--- 
layout: post 
title: Standard JodaTimeFormats
category : [coding]
tags : [java]
--- 

A quick pass through google didn’t return any resource with a formatted table listing all the standard date-time formats from Joda time’s DateTimeFormat class. So here it is, localized into several locale to show the differences among regions.

<table class="table table-bordered">
  <tr>
    <th>
      METHOD NAME
    </th>
    <th>
      LOCALE
    </th>
    <th>
      INPUT DATE
    </th>
    <th>
      FORMATTED DATE
    </th>
  </tr>
  <tr>
    <td rowspan="4">
      mediumDate
    </td>
    <td>   
en_US
    </td>
    <td>
   2012-01-20T17:00:24.627
    </td>
    <td>
 Jan 20, 2012
    </td>
  </tr>
  <tr>
    <td>
   fr_FR
    </td>
    <td>
   2012-01-20T17:00:24.627
    </td>
    <td>
 20 janv. 2012
    </td>
  </tr>
  <tr>
    <td>
   de_DE
    </td>
    <td>
   2012-01-20T17:00:24.627
    </td>
    <td>
 20.01.2012
    </td>
  </tr>
  <tr>
    <td>
   el_GR
    </td>
    <td>
   2012-01-20T17:00:24.627
    </td>
    <td>
 20 Ιαν 2012
    </td>
  </tr>
  <tr>
    <td rowspan="4">
mediumTime
    </td>
    <td>
   en_US
    </td>
    <td>
   2012-01-20T17:00:24.627
    </td>
    <td>
 5:00:24 PM
    </td>
  </tr>
  <tr>
    <td>
   fr_FR
    </td>
    <td>
   2012-01-20T17:00:24.627
    </td>
    <td>
 17:00:24
    </td>
  </tr>
  <tr>
    <td>
   de_DE
    </td>
    <td>
   2012-01-20T17:00:24.627
    </td>
    <td>
 17:00:24
    </td>
  </tr>
  <tr>
    <td>
   el_GR
    </td>
    <td>
   2012-01-20T17:00:24.627
    </td>
    <td>
 5:00:24 μμ
    </td>
  </tr>
  <tr>
    <td rowspan="4">
longTime
    </td>
    <td>
     en_US
    </td>
    <td>
   2012-01-20T17:00:24.627
    </td>
    <td>
 5:00:24 PM PST
    </td>
  </tr>
  <tr>
    <td>
     fr_FR
    </td>
    <td>
   2012-01-20T17:00:24.627
    </td>
    <td>
 17:00:24 PST
    </td>
  </tr>
  <tr>
    <td>
     de_DE
    </td>
    <td>
   2012-01-20T17:00:24.627
    </td>
    <td>
 17:00:24 PST
    </td>
  </tr>
  <tr>
    <td>
     el_GR
    </td>
    <td>
   2012-01-20T17:00:24.627
    </td>
    <td>
 5:00:24 μμ PST
    </td>
  </tr>
  <tr>
    <td rowspan="4">
fullDateTime
    </td>
    <td>
 en_US
    </td>
    <td>
   2012-01-20T17:00:24.627
    </td>
    <td>
 Friday, January 20, 2012 5:00:24 PM PST
    </td>
  </tr>
  <tr>
    <td>
 fr_FR
    </td>
    <td>
   2012-01-20T17:00:24.627
    </td>
    <td>
 vendredi 20 janvier 2012 17 h 00 PST
    </td>
  </tr>
  <tr>
    <td>
 de_DE
    </td>
    <td>
   2012-01-20T17:00:24.627
    </td>
    <td>
 Freitag, 20. Januar 2012 17:00 Uhr PST
    </td>
  </tr>
  <tr>
    <td>
 el_GR 
    </td>
    <td>
  2012-01-20T17:00:24.627
    </td>
    <td>
 Παρασκευή, 20 Ιανουάριος 2012 5:00:24 μμ PST
    </td>
  </tr>
  <tr>
    <td rowspan="4">
fullTime
    </td>
    <td>
     en_US
    </td>
    <td>
   2012-01-20T17:00:24.627
    </td>
    <td>
 5:00:24 PM PST
    </td>
  </tr>
  <tr>
    <td>
     fr_FR
    </td>
    <td>
   2012-01-20T17:00:24.627
    </td>
    <td>
 17 h 00 PST
    </td>
  </tr>
  <tr>
    <td>
     de_DE
    </td>
    <td>
   2012-01-20T17:00:24.627
    </td>
    <td>
 17:00 Uhr PST
    </td>
  </tr>
  <tr>
    <td>
     el_GR
    </td>
    <td>
   2012-01-20T17:00:24.627
    </td>
    <td>
 5:00:24 μμ PST
    </td>
  </tr>
  <tr>
    <td rowspan="4">
fullDate
    </td>
    <td>
     en_US
    </td>
    <td>
   2012-01-20T17:00:24.627
    </td>
    <td>
 Friday, January 20, 2012
    </td>
  </tr>
  <tr>
    <td>
     fr_FR
    </td>
    <td>
   2012-01-20T17:00:24.627
    </td>
    <td>
 vendredi 20 janvier 2012
    </td>
  </tr>
  <tr>
    <td>
     de_DE
    </td>
    <td>
   2012-01-20T17:00:24.627
    </td>
    <td>
 Freitag, 20. Januar 2012
    </td>
  </tr>
  <tr>
    <td>
     el_GR
    </td>
    <td>
   2012-01-20T17:00:24.627
    </td>
    <td>
 Παρασκευή, 20 Ιανουάριος 2012
    </td>
  </tr>
  <tr>
    <td rowspan="4">
shortTime
    </td>
    <td>
    en_US
    </td>
    <td>
   2012-01-20T17:00:24.627
    </td>
    <td>
 5:00 PM
    </td>
  </tr>
  <tr>
    <td>
    fr_FR
    </td>
    <td>
   2012-01-20T17:00:24.627
    </td>
    <td>
 17:00
    </td>
  </tr>
  <tr>
    <td>
    de_DE
    </td>
    <td>
   2012-01-20T17:00:24.627
    </td>
    <td>
 17:00
    </td>
  </tr>
  <tr>
    <td>
    el_GR
    </td>
    <td>
   2012-01-20T17:00:24.627
    </td>
    <td>
 5:00 μμ
    </td>
  </tr>
  <tr>
    <td rowspan="4">
mediumDateTime
    </td>
    <td>
	     en_US
    </td>
    <td>
		     2012-01-20T17:00:24.627
    </td>
    <td>
	Jan 20, 2012 5:00:24 PM
    </td>
  </tr>
  <tr>
    <td>
	     fr_FR
    </td>
    <td>
		     2012-01-20T17:00:24.627
    </td>
    <td>
	20 janv. 2012 17:00:24
    </td>
  </tr>
  <tr>
    <td>
	     de_DE
    </td>
    <td>
		     2012-01-20T17:00:24.627
    </td>
    <td>
	20.01.2012 17:00:24
    </td>
  </tr>
  <tr>
    <td>
	     el_GR
    </td>
    <td>
		     2012-01-20T17:00:24.627
    </td>
    <td>
	20 Ιαν 2012 5:00:24 μμ
    </td>
  </tr>
  <tr>
    <td rowspan="4">
longDate
    </td>
    <td>
	     en_US
    </td>
    <td>
		     2012-01-20T17:00:24.627
    </td>
    <td>
	January 20, 2012
    </td>
  </tr>
  <tr>
    <td>
	     fr_FR
    </td>
    <td>
		     2012-01-20T17:00:24.627
    </td>
    <td>
	20 janvier 2012
    </td>
  </tr>
  <tr>
    <td>
	     de_DE
    </td>
    <td>
		     2012-01-20T17:00:24.627
    </td>
    <td>
	20. Januar 2012
    </td>
  </tr>
  <tr>
    <td>
	     el_GR
    </td>
    <td>
		     2012-01-20T17:00:24.627
    </td>
    <td>
	20 Ιανουάριος 2012
    </td>
  </tr>
  <tr>
    <td rowspan="4">
longDateTime
    </td>
    <td>
	     en_US
    </td>
    <td>
		     2012-01-20T17:00:24.627
    </td>
    <td>
	January 20, 2012 5:00:24 PM PST
    </td>
  </tr>
  <tr>
    <td>
	     fr_FR
    </td>
    <td>
		     2012-01-20T17:00:24.627
    </td>
    <td>
	20 janvier 2012 17:00:24 PST
    </td>
  </tr>
  <tr>
    <td>
	     de_DE
    </td>
    <td>
		     2012-01-20T17:00:24.627
    </td>
    <td>
	20. Januar 2012 17:00:24 PST
    </td>
  </tr>
  <tr>
    <td>
	     el_GR
    </td>
    <td>
		     2012-01-20T17:00:24.627
    </td>
    <td>
	20 Ιανουάριος 2012 5:00:24 μμ PST
    </td>
  </tr>
  <tr>
    <td rowspan="4">
shortDate
    </td>
    <td>
	     en_US
    </td>
    <td>
		     2012-01-20T17:00:24.627
    </td>
    <td>
	1/20/12
    </td>
  </tr>
  <tr>
    <td>
	     fr_FR
    </td>
    <td>
		     2012-01-20T17:00:24.627
    </td>
    <td>
	20/01/12
    </td>
  </tr>
  <tr>
    <td>
	     de_DE
    </td>
    <td>
		     2012-01-20T17:00:24.627
    </td>
    <td>
	20.01.12
    </td>
  </tr>
  <tr>
    <td>
	     el_GR
    </td>
    <td>
		     2012-01-20T17:00:24.627
    </td>
    <td>
	20/1/2012
    </td>
  </tr>
  <tr>
    <td rowspan="4">
shortDateTime
    </td>
    <td>
	     en_US
    </td>
    <td>
		     2012-01-20T17:00:24.627
    </td>
    <td>
	1/20/12 5:00 PM
    </td>
  </tr>
  <tr>
    <td>
	     fr_FR
    </td>
    <td>
		     2012-01-20T17:00:24.627
    </td>
    <td>
	20/01/12 17:00
    </td>
  </tr>
  <tr>
    <td>
	     de_DE
    </td>
    <td>
		     2012-01-20T17:00:24.627
    </td>
    <td>
	20.01.12 17:00
    </td>
  </tr>
  <tr>
    <td>
	     el_GR
    </td>
    <td>
		     2012-01-20T17:00:24.627
    </td>
    <td>
	20/1/2012 5:00 μμ
    </td>
  </tr>
</table>
