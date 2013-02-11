--- 
layout: post 
title: Standard JodaTimeFormats
--- 

A quick pass through google didn’t return any resource with a formatted table listing all the standard date-time formats from Joda time’s DateTimeFormat class. So here it is, localized into several locale to show the differences among regions.

METHOD NAME  LOCALE  INPUT DATE	   FORMATTED DATE
mediumDate   en_US   2012-01-20T17:00:24.627 Jan 20, 2012
mediumDate   fr_FR   2012-01-20T17:00:24.627 20 janv. 2012
mediumDate   de_DE   2012-01-20T17:00:24.627 20.01.2012
mediumDate   el_GR   2012-01-20T17:00:24.627 20 Ιαν 2012
mediumTime   en_US   2012-01-20T17:00:24.627 5:00:24 PM
mediumTime   fr_FR   2012-01-20T17:00:24.627 17:00:24
mediumTime   de_DE   2012-01-20T17:00:24.627 17:00:24
mediumTime   el_GR   2012-01-20T17:00:24.627 5:00:24 μμ
longTime     en_US   2012-01-20T17:00:24.627 5:00:24 PM PST
longTime     fr_FR   2012-01-20T17:00:24.627 17:00:24 PST
longTime     de_DE   2012-01-20T17:00:24.627 17:00:24 PST
longTime     el_GR   2012-01-20T17:00:24.627 5:00:24 μμ PST
fullDateTime en_US   2012-01-20T17:00:24.627 Friday, January 20, 2012 5:00:24 PM PST
fullDateTime fr_FR   2012-01-20T17:00:24.627 vendredi 20 janvier 2012 17 h 00 PST
fullDateTime de_DE   2012-01-20T17:00:24.627 Freitag, 20. Januar 2012 17:00 Uhr PST
fullDateTime el_GR   2012-01-20T17:00:24.627 Παρασκευή, 20 Ιανουάριος 2012 5:00:24 μμ PST
fullTime     en_US   2012-01-20T17:00:24.627 5:00:24 PM PST
fullTime     fr_FR   2012-01-20T17:00:24.627 17 h 00 PST
fullTime     de_DE   2012-01-20T17:00:24.627 17:00 Uhr PST
fullTime     el_GR   2012-01-20T17:00:24.627 5:00:24 μμ PST
fullDate     en_US   2012-01-20T17:00:24.627 Friday, January 20, 2012
fullDate     fr_FR   2012-01-20T17:00:24.627 vendredi 20 janvier 2012
fullDate     de_DE   2012-01-20T17:00:24.627 Freitag, 20. Januar 2012
fullDate     el_GR   2012-01-20T17:00:24.627 Παρασκευή, 20 Ιανουάριος 2012
shortTime    en_US   2012-01-20T17:00:24.627 5:00 PM
shortTime    fr_FR   2012-01-20T17:00:24.627 17:00
shortTime    de_DE   2012-01-20T17:00:24.627 17:00
shortTime    el_GR   2012-01-20T17:00:24.627 5:00 μμ
mediumDateTime	     en_US		     2012-01-20T17:00:24.627	Jan 20, 2012 5:00:24 PM
mediumDateTime	     fr_FR		     2012-01-20T17:00:24.627	20 janv. 2012 17:00:24
mediumDateTime	     de_DE		     2012-01-20T17:00:24.627	20.01.2012 17:00:24
mediumDateTime	     el_GR		     2012-01-20T17:00:24.627	20 Ιαν 2012 5:00:24 μμ
longDate	     en_US		     2012-01-20T17:00:24.627	January 20, 2012
longDate	     fr_FR		     2012-01-20T17:00:24.627	20 janvier 2012
longDate	     de_DE		     2012-01-20T17:00:24.627	20. Januar 2012
longDate	     el_GR		     2012-01-20T17:00:24.627	20 Ιανουάριος 2012
longDateTime	     en_US		     2012-01-20T17:00:24.627	January 20, 2012 5:00:24 PM PST
longDateTime	     fr_FR		     2012-01-20T17:00:24.627	20 janvier 2012 17:00:24 PST
longDateTime	     de_DE		     2012-01-20T17:00:24.627	20. Januar 2012 17:00:24 PST
longDateTime	     el_GR		     2012-01-20T17:00:24.627	20 Ιανουάριος 2012 5:00:24 μμ PST
shortDate	     en_US		     2012-01-20T17:00:24.627	1/20/12
shortDate	     fr_FR		     2012-01-20T17:00:24.627	20/01/12
shortDate	     de_DE		     2012-01-20T17:00:24.627	20.01.12
shortDate	     el_GR		     2012-01-20T17:00:24.627	20/1/2012
shortDateTime	     en_US		     2012-01-20T17:00:24.627	1/20/12 5:00 PM
shortDateTime	     fr_FR		     2012-01-20T17:00:24.627	20/01/12 17:00
shortDateTime	     de_DE		     2012-01-20T17:00:24.627	20.01.12 17:00
shortDateTime	     el_GR		     2012-01-20T17:00:24.627	20/1/2012 5:00 μμ