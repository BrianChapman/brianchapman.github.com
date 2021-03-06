---
layout: post
title: "Getting Started with AspectJ, Eclipse, and Maven"
description: ""
category: [tutorial]
tags: [aspectj, java]
published: true
---
{% include JB/setup %}

AspectJ is the de-facto library for using aspect oriented programming (AOP) in Java. I had a difficult time finding a good introduction to AspectJ, including setting it up with Maven and Eclipse, thus the reason for this post. 

Maven
-----

There are two plugins that allow use of AspectJ with Maven: [aspectj-maven-plugin \(Codehaus\)](http://mojo.codehaus.org/aspectj-maven-plugin/) and [maven-aspectj-plugin (Apache)](http://maven.apache.org/maven-1.x/plugins/aspectj/). We are going to focus on the aspectj-maven-plugin.

For those who like to get their hands dirty will want to checkout my [AspectJ sandbox](https://github.com/BrianChapman/sandbox/tree/master/aspectj), which has examples of AspectJ usage with Maven.

To get started, you need to add a dependency and a plugin to your pom
    
      <properties>
        <aspectj.version>1.6.11</aspectj.version>
		<maven.compiler.version>1.6</maven.compiler.version>
      </properties>
    
      <dependencies>
        <dependency>
          <groupId>org.aspectj</groupId>
          <artifactId>aspectjrt</artifactId>
          <version>${aspectj.version}</version>
        </dependency>
        </dependencies>
    
      <build>
    
        <pluginManagement>
          <plugins>
            <plugin>
              <groupId>org.codehaus.mojo</groupId>
              <artifactId>aspectj-maven-plugin</artifactId>
              <version>1.4</version>
              <configuration>
                <complianceLevel>${maven.compiler.target}</complianceLevel>
                <source>${maven.compiler.source}</source>
                <target>${maven.compiler.target}</target>
				<outxml>true</outxml>
				<verbose>true</verbose>
				<showWeaveInfo>true</showWeaveInfo>
              </configuration>
              <executions>
                <execution>
                  <goals>
                    <goal>compile</goal>       <!-- use this goal to weave all your main classes -->
                    <goal>test-compile</goal> <!-- use this goal to weave all your test classes -->
                  </goals>
                </execution>
              </executions>
            </plugin>
    
            <plugin>
              <groupId>org.apache.maven.plugins</groupId>
              <artifactId>maven-compiler-plugin</artifactId>
              <version>2.3.2</version>
              <configuration>
                <source>${maven.compiler.version}</source>
                <target>${maven.compiler.version}</target>
              </configuration>
            </plugin>
          </plugins>
        </pluginManagement>
    
        <plugins>
          <plugin>
            <groupId>org.apache.maven.plugins</groupId>
            <artifactId>maven-compiler-plugin</artifactId>
          </plugin>
		  <plugin>
		    <groupId>org.codehaus.mojo</groupId>
			<artifactId>aspectj-maven-plugin</artifactId>
		  </plugin>
        </plugins>
    
      </build>
    </project>

Some things to note. You must supply a compiler version if you plan to use features added in AspectJ 5. Otherwise the plugin will assume a version less than 1.5. This is particularly important if you plan on using annotations or generics.

The aspectj-maven-plugin will run your classes through the adj compiler and apply any matching advice. If a bit of advice does not get applied, Xlint will warn you of these errors. 

Eclipse
-------

Eclipse [AspectJ Development Tools (AJDT)](http://www.eclipse.org/ajdt/) provides AspectJ integration with Eclipse. It can be installed by adding the appropriate update site to your Eclipse install manager.

Since m2e version 1.0, plugins that are bound to the maven lifecycle must either have a connector installed or have an explicit lifecycle mapping ([more information)](http://wiki.eclipse.org/M2E_plugin_execution_not_covered). Fortunately, the AspectJ has adding [http://dist.springsource.org/release/AJDT/configurator/](http://dist.springsource.org/release/AJDT/configurator/) to your Eclipse install manager.

I recommend reviewing [this video](http://eclipse.org/ajdt/demos/HelloWorldAspectJ.html) on the features of AJDT.

Writing your first Aspect
-------------------------

AspectJ has two modes for creating aspects: 1) using the 'aspect' keyword and 2) using Annotations. I'll show you both here. This example is adapted from my [sandbox](https://github.com/BrianChapman/sandbox/tree/master/aspectj).

The class we would like to add aspects to is a hypothetical Bank.

    public interface Bank {
    
    public void transfer(Account accountFrom, Account accountTo, Money amount);
    
    public void register(Account account, Money initialAmount);
    
    public Money balance(Account account);
    
    }

We want to accomplish 3 things:

 1. apply an overdraft protection to the account if there are insufficient funds, 
 1. record the transaction in an audit log, and 
 1. record any balance inquiries in the audit log. These three items should be sufficient to demonstrate the basic functionality of picking out JoinPoints and applying before, after, and after returning advice.

I'll first show you what I call the traditional method using the 'aspect' keyword.

    public aspect TransactionAspect {
    
      pointcut transfer() : execution(* com.rts.sandbox.aspectj.Bank.transfer(..));
    
      before(Account from, Account to, Money amount, SecureBank bank): transfer() && args(from, to, amount) 
	    && this(bank) {
		
        Money fromBalance = bank.balance(from);
        if (MoneyMath.with(fromBalance).lessThan(amount)) {
          Money amountToTransfer = MoneyMath.with(amount).subtract(fromBalance).result();
          bank.transfer(bank.getOverdraftAccount(), from, amountToTransfer);
        }
    
      }
    
      after(Account from, Account to, Money amount, SecureBank bank) : transfer() && args(from, to, amount) 
	    && this(bank) {
		
        recordTransaction("Transfer from account " + from.name() + " to account " + to.name() + " of amount "
          + amount.formatted() + " succeeded. ");
        System.out.println("   Account Balance: " + from.name() + ", " + bank.balance(from).formatted());
        System.out.println("   Account Balance: " + to.name() + ", " + bank.balance(to).formatted());
      }
    
      after(Account account) returning(Money balance): 
	    execution(* com.rts.sandbox.aspectj.Bank.balance(Account)) && args(account) {
		
        recordTransaction(account.name() + " inquired about their balance of " + balance.formatted() + ".");
      }
    
      after() : execution(* com.rts.sandbox.aspectj.Bank.balance(java.util.List)) {
        recordTransaction("Inquiry about many accounts just happened.");
      }
       
      private void recordTransaction(String message) {
        System.out.println(new Date().toString() + " " + message);
      }
    }

Notice that there are several new keywords introduced. 

    public aspect TransactionAspect {
	
this tells AspectJ that this is an aspect. It is very much the same as declaring a class or interface.

    pointcut transfer() : execution(* com.rts.sandbox.aspectj.Bank.transfer(..));
	
The pointcut keyword indicates that we want to define a named pointcut. Pointcuts are expressions that pick out branches in execution such as method calls, exception handling, field access, etc. This expression will match everytime the Bank class's transfer method is executed with any combination of arguments (the '..' indicates a wildcard for the arguments).

Note that there are other types pointcuts such as 'call' which will inject at the point a call is made, not where the matching method executes. 

    before(Account from, Account to, Money amount, SecureBank bank): transfer() && args(from, to, amount) 
	    && this(bank) {
		...
	}
		
This statement is called 'advice'. Specifically it is 'before advice' because the code block will be injected before the pointcut. In this case we provide a named pointcut 'transfer()' which matches against the transfer method. Therefore this advice will be injected before any code within the transfer method executes. Note that the pointcut is an 'execution' pointcut. This is perfect because we want to check for overdraft protection before a transfer is made. 

Other points of interest here are the arguments in the 'before()' clause. These arguments must match the names in the predicated provided. In this example there is the 'args(from, to, amount)' predicate, which tells AspectJ that you want to have these arguments available in the code block, and the 'this(bank)' predicate which indicates that you want access to the object that the method is located in. In this case it will be an instance of the Bank class.

    after(Account from, Account to, Money amount, SecureBank bank) : transfer() && args(from, to, amount) 
        && this(bank) {
        ...
    }
	
This statement is an 'after advice' which will be injected after the code in the pointcut executes. As in the before advice, the arguments and containing object are supplied to the code block.

    after(Account account) returning(Money balance): 
        execution(* com.rts.sandbox.aspectj.Bank.balance(Account)) && args(account) {
	  ...    
    }
	
This type of after advice is called 'after returning advice' and will be executed after the code in the pointcut executes just like before, but this time the returning value is supplied. This is denoted with the 'returning(Money balance)' keyword. The return value's type and variable name is supplied here.

You can also define pointcuts and advice using Java 5 Annotations. There are some advantages to doing this over the traditional approach as the resulting class is a valid java class and can be used and unit tested like a java class. 

    @Aspect
    public class TransactionsAspect {
    
      @Pointcut("execution(* com.rts.sandbox.aspectj.Bank.transfer(..))")
        public void transfer() {
      }
    
      @Before("transfer() && args(from, to, amount) && this(bank)")
      public void overdraftProtection(Account from, Account to, Money amount, SecureBank bank) {
        Money fromBalance = bank.balance(from);
        if (MoneyMath.with(fromBalance).lessThan(amount)) {
          Money amountToTransfer = MoneyMath.with(amount).subtract(fromBalance).result();
          bank.transfer(bank.getOverdraftAccount(), from, amountToTransfer);
        }
      }
    
      @After("transfer() && args(from, to, amount) && this(bank)")
      public void recordTransaction(Account from, Account to, Money amount, Bank bank) {
        recordTransaction("Transfer from account " + from.name() + " to account " + to.name() + " of amount "
          + amount.formatted() + " succeeded. ");
        System.out.println("   Account Balance: " + from.name() + ", " + bank.balance(from).formatted());
        System.out.println("   Account Balance: " + to.name() + ", " + bank.balance(to).formatted());
      }
    
      @AfterReturning(pointcut = "execution(* com.rts.sandbox.aspectj.Bank.balance(Account)) && args(account)",
        returning = "balance")
      public void recordBalanceInquiry(Account account, Money balance) {
        recordTransaction(account.name() + " inquired about their balance of " + balance.formatted() + ".");
      }
    
      @After("execution(* com.rts.sandbox.aspectj.Bank.balance(java.util.List))")
      public void recordBalanceInquiry() {
        recordTransaction("Inquiry about many accounts just happened.");
      }
    
      private void recordTransaction(String message) {
        System.out.println(new Date().toString() + " " + message);
      }
    }

Note that the pointcut's name is defined by the method name. The pointcut's name 'transfer()' is used in the before and after advice.

Arguments taken from predicates (such as the 'args()' and 'this() predicates) must have names that match the arguments to the method. For example, the 'this(bank)' predicate defines a variable 'bank' which will be made available to the method. The method must have an argument called 'bank' which has a matching type from the pointcut (Bank in this case).

This is only a cursory review of the capabilities of AspectJ. For the complete documentation, see the [programming guide](http://www.eclipse.org/aspectj/doc/released/progguide/index.html) and the [Supplemental Documentation](http://www.eclipse.org/aspectj/doc/released/adk15notebook/index.html) for AspectJ 5 features (annotations, generics, and a few others)
