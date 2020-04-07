---
title: 'Calculate the day of the week for any date in your head'
date: 2020-01-01T06:55:00+01:00
draft: false
---

Doomsday Algorithm
==================

The Doomsday Algorithm gives the day of the week for any date (and you can do it in your head)
----------------------------------------------------------------------------------------------

Added 1994-02-22, Updated 2019-02-28 with examples for 2019

Overview
--------

The Doomsday Algorithm is presented in the following sections.

*   [February 28 or 29](http://rudy.ca/doomsday.html#feb2829): Doomsday is the last day of February
*   [Even Months](http://rudy.ca/doomsday.html#even): April, June, August, October, and December (months 4, 6, 8, 10, and 12)
*   [Odd Months](http://rudy.ca/doomsday.html#odd): March, May, July, September, and November (months 3, 5, 7, 9, and 11)
*   [2018 Calendar](http://rudy.ca/doomsday.html#calendar): the current year calendar, highlighting the Doomsday in each month
*   [Other Years](http://rudy.ca/doomsday.html#years): how to apply the Doomsday Algorithm to other years in the 1900s and 2000s
*   [Other Centuries](http://rudy.ca/doomsday.html#centuries): extending the Doomsday Algorithm to other centuries
*   [The Hand](http://rudy.ca/doomsday.html#hand): Dr. Conway's shortcut method
*   [Origins](http://rudy.ca/doomsday.html#origins): the creation of the Doomsday Algorithm by Dr. John Horton Conway
*   [Links](http://rudy.ca/doomsday.html#links): Doomsday Algorithm resources on the Web for additional information

Have fun!

February 28 or 29
-----------------

To use the Doomsday Algorithm in any year, we first need to know the Doomsday for that year.

**Doomsday is February 28 or 29**. In other words, Doomsday is always the last day of February.  
In normal years, Doomsday is February 28, and in leap years, Doomsday is February 29.

In 2019, which is not a leap year, the last day of February is  
**Thursday** the 28th.

Once we know Doomsday, it's pretty easy to get the day of the week for any day in February.  
This is done by adding and subtracting, using multiples of 7, and you should be comfortable doing this in your head,  
otherwise the rest of the algorithm will give you trouble! Luckily, most people, through practice or whatever,  
are good at mentally picturing a month if they have something to anchor it on, and Doomsday is this anchor.  
For February, it's always the 28th in normal years, and the 29th in leap years.

**Example**: what is this year's Valentine's Day, February 14th?  
**Answer**: Doomsday 2019 is  
Thursday the 28th of February. So one week earlier, the 21st is also  
Thursday. Another week earlier is  
Thursday the 14th. So Valentine's Day 2019 is  
Thursday.

**Example**: what is this year's Groundhog day, February 2nd?  
**Answer**: Doomsday 2019 is  
Thursday the 28th of February... then subtracting 7 for each week going backwards, we have  
Thursday the 21st...  
Thursday the 14th...  
Thursday the 7th...  
and then we have to go five days back, to get from the 7th to the 2nd.

If going back five days in your head is difficult—and it often is, especially looking back over a weekend—there's a  
little trick we can use here.  
Going two days forward gives the _same day of the week_ as five days back. So if February 7th is  
Thursday, then two days forward is  
Saturday the 9th, which is the same day of the week as  
Saturday the 2nd. So Groundhog day in 2019 is  
Saturday. Remember, all we're after is the day of the week, so "-5" is the same as "+2" but "+2" is usually easier to do.

If it helps, you can review the above two examples using this calendar for February 2019 —

```
 **2.Feb(28th/non-leap)**  
 Su Mo Tu We Th Fr Sa   
 1 2   
 3 4 5 6 7 8 9   
 10 11 12 13 14 15 16   
 17 18 19 20 21 22 23   
 24 25 26 27 **28** 
```

[Return to top](http://rudy.ca/doomsday.html#content)

Even Months
-----------

Okay, the last day of February is Doomsday. Once we know what day of the week Doomsday is, we immediately know the day of the week of  
certain other days in the year. There are actually 52 (or 53) other days which are all on the same day of the week as "the" Doomsday at the  
end of February, but there's a special one each month which we will now learn.

Each month has a special day which we remember, because it is on the same day of the week as the Doomsday which is at the end of February.  
We call these the Doomsdays for their months. Just keep in mind that the entire year is determined by the Doomsday at the end of February,  
and that all the other Doomsdays within the year are on the same day of the week.

Let's begin with the even months. These are months 2, 4, 6, 8, 10, and 12, i.e. February, April, June, August, October, and December.  
Actually, we never do February this way, because it's special, and we've already covered it.

**For even months** (not including February), **the Nth of that month is a Doomsday**.  
In other words, it's the same day of the week as the last day in February.  
This is a delightful coincidence, and it's _so_ easy to remember:

*   April 4th is a Doomsday
*   June 6th is a Doomsday
*   August 8th is a Doomsday
*   October 10th is a Doomsday
*   December 12th is a Doomsday

Neat, eh? Now we can simply work our way around any even month based on its Doomsday.

**Example**: what is this year's Christmas Day, December 25th?  
**Answer**: Doomsday 2019 is  
Thursday. Then December (even month) 12th is the Doomsday for December, so it's also  
Thursday. Two weeks later, December 26th is also  
Thursday, so Christmas, the day before, is  
Wednesday December 25th. Easy! In fact, after you do the Doomsday algorithm often enough, you just start remembering things  
like **Christmas is always the day before Doomsday**.

**Example**: what is this year's Halloween, October 31st?  
**Answer**: Doomsday 2019 is  
Thursday. So October (even) 10th is  
Thursday. Then three weeks (21 days) later is  
Thursday, October 31st. Easy! In fact, after you do the Doomsday algorithm often enough, you just start remembering things  
like **Halloween is always Doomsday**.

**Example**: what is this year's Canadian Thanksgiving Day, the second Monday in October?  
**Answer**: Doomsday 2019 is  
Thursday. So October (even) 10th is  
Thursday. A week earlier is Thursday October 3rd, and two days before that is Tuesday the 1st.  
So that means the first Monday of October is the 7th, and  
the second Monday in October, Canadian Thanksgiving (also Columbus Day in the US), is  
Monday, October 14th in 2019.

[Return to top](http://rudy.ca/doomsday.html#content)

Odd Months
----------

Now let's do the odd months—months 1, 3, 5, 7, 9, and 11, i.e. January, March, May, July, September, and November.  
Skip January and March for a moment, and concentrate on 5, 7, 9, and 11.

Consider the following mnemonic phrase:

> **I work 9-5 at the 7-11**

"Nine to five" is a common working day (9 a.m. to 5 p.m.) while [7-Eleven](http://www.7-eleven.com/) is a chain of convenience stores.  
This mnemonic phrase should help you remember:

*   for the 9th month, Doomsday is the 5th
*   for the 5th month, Doomsday is the 9th
*   for the 7th month, Doomsday is the 11th
*   for the 11th month, Doomsday is the 7th

This gives us Doomsday for May, July, September, and November. Now we just work our way around again within each month,  
using the Doomsday for that month.

**Example**: what day is this year's July 4th?  
**Answer**: Doomsday 2019 is  
Thursday, so the Doomsday for July (7th month) is the 11th, also a  
Thursday. So one week earlier, July 4th is also  
Thursday. In fact, after you do the Doomsday algorithm often enough, you just start remembering things like  
**July 4th is always Doomsday**.

**Example**: what is this year's Labour Day, the first Monday of September?  
**Answer**: Doomsday 2019 is  
Thursday. September (9th month) 5th is  
Thursday. To o back to Monday, we go back 3 days.  
  
So Labour Day in 2019, the first Monday of September, is September 2nd.

Now March.

Doomsday, the last day of February, is often also called the "0th" of March. You might have to think about that for a moment,  
until you realize that the next day is the 1st of March. So if the "0th" of March is Doomsday, then the **7th of March**,  
exactly one week after the last day of February, no matter whether it's the 28th or 29th, is also Doomsday.

**Example**: what day is this year's St. Patrick's Day, March 17th?  
**Answer**: Doomsday 2019 is  
Thursday, which we know is the "0th" of March.  
So a week later, March 7th is  
Thursday. March 14th is  
Thursday. Now we go three days forward, to get to Sunday, March 17th.

An alternate, simpler method for March is to use [Pi Day](https://en.wikipedia.org/wiki/Pi_Day), which is March 14th,  
i.e. 3/14 using month/day numbers. **Pi Day is always Doomsday**.

Finally, we have to be able to do January.

The easiest way to calculate January's Doomsday was described to me by reader **Bob Goddard**:

> It's January 3rd three years out of four, the non-leap years. It's January 4th only in the fourth year,  
> the years divisible by 4.

This is _so_ much simpler than what I had before (which involved January 31st and "January 32nd").

**Example**: what is this year's New Year's Day (January 1st)?  
**Answer**: Doomsday 2019 is  
Thursday, and since 2019 is not a leap year, January 3rd is  
Thursday. Go back 2 days, and January 1st is Tuesday. Simple, eh? Thanks, Bob.

Another way to calculate January's Doomsday was sent to me by reader **Roman Weil**.  
It's actually due to his son Sandy Weil, who is the Director of Football Analytics for the Baltimore Ravens:

> A January trick: Instead of associating January with the new year, associate it with the old. That is, think of Jan 2019  
> as being part of 2018. In that case, Pi Days in January are 1/2 and 1/23. So in 2019, 1/2 and 1/23 are Wednesdays, which is the Pi Day of 2018.  
> You will find, if you are like me, that when you think about January, it's more often about 'next January' than about 'last January,'  
> so putting January at the end of the current year will solve most of your January issues.

Sandy here refers to "Pi Days" which is another name for Doomsdays—this is further discussed in  
[Origins](http://rudy.ca/doomsday.html#origins). The mnemonic part of Sandy's trick is that 1/2 and 1/23 sound  
like "one two" and "one two three."

[Return to top](http://rudy.ca/doomsday.html#content)

2019 Calendar
-------------

If you've worked your way through the rules but have trouble remembering them, it may help to see the Doomsdays in calendar form.  
Here's the Doomsday Calendar for 2019 with all the Doomsdays highlighted:

### Doomsday Calendar for 2019

```
 ** 1.Jan(3rd/nonleap) ** ** 2.Feb(28th/nonleap)**  
 Su Mo Tu We Th Fr Sa Su Mo Tu We Th Fr Sa  
 1 2 **3** 4 5 1 2  
 6 7 8 9 10 11 12 3 4 5 6 7 8 9  
 13 14 15 16 17 18 19 10 11 12 13 14 15 16  
 20 21 22 23 24 25 26 17 18 19 20 21 22 23  
 27 28 29 30 31 24 25 26 27 **28**   
   
 ** 3.Mar(7th) ** **4.Apr(4th)**   
 Su Mo Tu We Th Fr Sa Su Mo Tu We Th Fr Sa  
 1 2 1 2 3 **4** 5 6  
 3 4 5 6 **7** 8 9 7 8 9 10 11 12 13  
 10 11 12 13 14 15 16 14 15 16 17 18 19 20  
 17 18 19 20 21 22 23 21 22 23 24 25 26 27  
 24 25 26 27 28 29 30 28 29 30  
 31  
   
 ** 5.May(9th) ** **6.Jun(6th)**   
 Su Mo Tu We Th Fr Sa Su Mo Tu We Th Fr Sa  
 1 2 3 4 1  
 5 6 7 8 **9** 10 11 2 3 4 5 **6** 7 8  
 12 13 14 15 16 17 18 9 10 11 12 13 14 15  
 19 20 21 22 23 24 25 16 17 18 19 20 21 22  
 26 27 28 29 30 31 23 24 25 26 27 28 29  
 30  
   
 ** 7.Jul(11th) ** **8.Aug(8th)**   
 Su Mo Tu We Th Fr Sa Su Mo Tu We Th Fr Sa  
 1 2 3 4 5 6 1 2 3  
 7 8 9 10 **11** 12 13 4 5 6 7 **8** 9 10  
 14 15 16 17 18 19 20 11 12 13 14 15 16 17   
 21 22 23 24 25 26 27 18 19 20 21 22 23 24  
 28 29 30 31 25 26 27 28 29 30 31  
   
 ** 9.Sep(5th) ** **10.Oct(10th)**   
 Su Mo Tu We Th Fr Sa Su Mo Tu We Th Fr Sa  
 1 2 3 4 **5** 6 7 1 2 3 4 5  
 8 9 10 11 12 13 14 6 7 8 9 **10** 11 12   
 15 16 17 18 19 20 21 13 14 15 16 17 18 19  
 22 23 24 25 26 27 28 20 21 22 23 24 25 26  
 29 30 27 28 29 30 31  
   
 ** 11.Nov(7th) ** **12.Dec(12th)**   
 Su Mo Tu We Th Fr Sa Su Mo Tu We Th Fr Sa  
 1 2 1 2 3 4 5 6 7  
 3 4 5 6 **7** 8 9 8 9 10 11 **12** 13 14  
 10 11 12 13 14 15 16 15 16 17 18 19 20 21  
 17 18 19 20 21 22 23 22 23 24 25 26 27 28  
 24 25 26 27 28 29 30 29 30 31
```

### Previous Doomsday Calendars

Here are links to single-page versions of the Doomsday Calendar (the first two are actually GIFs; sorry 'bout that) suitable for printing:

[Return to top](http://rudy.ca/doomsday.html#content)

Other Years
-----------

Okay, we can do 2019. What about other years? If Doomsday is  
Thursday this year, what was it last year, in  
2018?

Well, you could go look it up in a calendar, but let me tell you it was a  
Wednesday. Doomsday advances by one day each year because 365 divided by 7 leaves 1 remainder.  
Doomsday advances two days each leap year, and we'll come back to more on that in a moment.

Let's work a couple of examples for last year,  
2018, when Doomsday was  
Wednesday.

**Example**: what day was New Year's Eve last year?  
**Answer**: Start with Doomsday for last year -- Doomsday 2018 was  
Wednesday. December (even) 12th was  
Wednesday, and so was the 26th. Five days later, December 31st, was  
Monday. Or, if you're starting to get the hang of this, instead of  
"Wednesday + 5 = Monday," you'll think  
"Wednesday - 2 = Monday," which seems just a wee bit easier. Remember, all we're looking for is the day of the week.  
So New Year's Eve last year, 2018, was Monday.

**Example**: what day of the week was New Year's Eve,  
2017?  
**Answer**: Since we were just doing examples for last year, let's try New Year's Eve,  
2017 by going backwards from January 1st, 2018.  
Now, Doomsday 2018 was  
Wednesday, and since  
2018 was not a leap year, that means that **January 3rd,  
2018** was  
Wednesday. So then January 1st, 2018 was 2 days earlier, i.e.  
Monday. Finally, this means that the day before, New Year's Eve, December 31st,  
2017, was Sunday.

The Doomsday Algorithm is often used with people's birthdays. In order to do the Doomsday algorithm for  
**any year in the 1900's**, when most of us were born, we need to memorize the fact that  
**Doomsday for 1900 is Wednesday**. Then we do a calculation based on the number of years since 1900.

First, look at the following chart of Doomsdays:

```
 ** Sun Mon Tue Wed Thu Fri Sat**  
 1900 1901 1902 1903  
 ---- **1904** 1905 1906 1907 ---- **1908**  
 1909 1910 1911 ---- **1912** 1913 1914  
 1915 ---- **1916** 1917 1918 1919 ----  
 **1920** 1921 1922 1923 ---- **1924** 1925  
 1926 1927 ---- **1928** 1929 1930 1931  
 ---- **1932** 1933 1934 1935 ---- **1936**  
 1937 1938 1939 ---- **1940** 1941 1942  
 1943 ---- **1944** 1945 1946 1947 ----  
 **1948** 1949 1950 1951 ---- **1952** 1953  
 1954 1955 ---- **1956** 1957 1958 1959  
 ---- **1960** 1961 1962 1963 ---- **1964**  
 1965 1966 1967 ---- **1968** 1969 1970  
 1971 ---- **1972** 1973 1974 1975 ----  
 **1976** 1977 1978 1979 ---- **1980** 1981  
 1982 1983 ---- **1984** 1985 1986 1987  
 ---- **1988** 1989 1990 1991 ---- **1992**  
 1993 1994 1995 ---- **1996** 1997 1998  
 1999 ---- **2000** ...
```

Notice that Doomsday 1900 is Wednesday. This is the anchor for all the years in the 1900's.  
(Notice also that 1900 is _not_ a leap year, so Doomsday 1900 is February 28th.)  
How do we remember 1900=Wednesday? Dr. Conway (see [Origins](http://rudy.ca/doomsday.html#origins)) suggests the mnemonic "We-in-dis-day",  
indicative of the fact that most of us were born in the 1900's.

Now every twelve years, Doomsday advances by one. Check for yourself.  
In the chart above, pick a year and look ahead twelve years—down two rows and over one day. This leads to the following rule...

For any year 19YY, using the YY part of the year, calculate:

1.  the number of 12's in the YY part of the year
2.  the remainder of step 1
3.  the number of 4's in the remainder of step 1

Feel free to throw out multiples of 7 along the way if you find this easy to do.

Now we need to add the result of our calculation to 1900=Wednesday to get the Doomsday for that year.  
We do by this treating Wednesday as day 4. Quite easy to remember, since that's Wednesday's day of the week in the normal  
Sunday-to-Saturday calendar.

**Example**: what is Doomsday 1929?  
**Answer**:

1.  29 divided by 12 is **2**
2.  ... remainder **5**
3.  5 divided by 4 is **1**

Adding these up, we get 5+2+1=**8**, and we can throw out a 7 to get **1**.  
Finally, this 1 has to be added to 1900=Wednesday, so Doomsday for 1929 is Thursday.

**Example**: what is Doomsday 1999?  
**Answer**:

1.  99 divided by 12 is **8**
2.  ... remainder **3**
3.  and of course 3 divided by 4 is **0**

Adding these up, we get 8+3+0=**11** i.e. **4**.  
This has to be added to 1900=Wednesday, so Doomsday for 1999 is Sunday.

We should now be able to do **any day in the 1900's in our head**. Let's do a couple more examples...

**Example**: what day of the week was November 27, 1982?  
**Answer**: 82 / 12 = **6**  
... remainder **10**  
... 10 / 4 = **2**  
... 6 + 10 + 2 = 18 which is 4 days to be added to Wednesday (for 1900)  
... so Doomsday 1982 was **Sunday**  
... November(11) 7th was Sunday, 28th was Sunday  
... November 27th 1982 was Saturday; that was the day the Doomsday Algorithm was featured on Quirks and Quarks  
(see [Origins](http://rudy.ca/doomsday.html#origins)).

**Example**: what day of the week was July 20, 1969? (the date of the first landing of humans on the Moon)  
**Answer**: 69 / 12 = **5**  
... remainder **9**  
... 9 / 4 = **2**  
... 5 + 9 + 2 = 16 which is 2 days to be added to Wednesday (for 1900)  
... so Doomsday 1969 was **Friday**  
... July(7) 11th is Friday, 18th is Friday  
... July 20th 1969 was Sunday

### Increased Speed

Dr. Sidney Graham sent me the following:

> Do you know Conway's method for "increased speed"? Basically, the trick is to memorize the list:
> 
> > 6, 11.5, 17, 23, 28, 34, ...., 84, 90, 95.5
> 
> These are the years in a century that have the same doomsday as the century year, i.e. Doomsday1900 = Doomsday1906 = Doomsday1917 etc.
> 
> The "11.5" refers to the fact that  
> Doomsday1911 = Doomsday1900 - 1 and  
> Doomsday1912 = Doomsday1900 + 1.

This list of years can be seen in the above table in the column under 1900. Here's that column again, all by itself:

```
 Sun Mon Tue Wed Thu Fri Sat  
 1900  
 06  
 11 -- 12  
 17  
 23  
 28  
 34  
 39 -- 40  
 45  
 51  
 56  
 62  
 67 -- 68  
 73  
 79  
 84  
 90  
 95 -- 96
```

Obviously, if you can memorize this list, you can increase the speed of your calculations.  
For some of us, that's a big _IF_; it reminds me of a comment someone made when first shown the entire Doomsday Algorithm:

> Find the day of the week for any year in history in your head? Maybe, but only if one of the  
> steps included in my head is telling myself "Remember where you put the printout of that page."

In any case, let's have a couple of examples:

**Example**: what day of the week was August 13, 1971  
**Answer: "67.5" means 1968 = Doomsday + 1**  
... thus 1971 is Doomsday + 4 = Sunday  
... August(8) 8th is Doomsday  
... August 13th 1971 was a Friday

**Example**: what day of the week was December 24, 1973?  
**Answer: 73 = Doomsday**  
... thus 1973 is Wednesday  
... December(12) 12th is Doomsday  
... December 24th 1973 was a Monday

[Return to top](http://rudy.ca/doomsday.html#content)

Other Centuries
---------------

Previously, we learned that Doomsday for 1900 was Wednesday. What is Doomsday for other centuries?

Let's start with the 21st century, i.e. the 2000's.

### The 2000's

Well, it turns out the 2000's are real easy. Recall the chart we were looking at earlier.  
Here it is again, extended into the 2000's a few years...

```
 ** Sun Mon Tue Wed Thu Fri Sat**  
 1999 ---- **2000** 2001 2002 2003 ----  
 **2004** 2005 2006 2007 ---- **2008** 2009  
 2010 2011 ---- **2012** 2013 2014 2015  
 ---- **2016** 2017 2018 2019 ...
```

Notice that **Doomsday for 2000 is Tuesday, i.e. "2000=Tue"**.  
This is the mnemonic that helps us anchor the other years in this century.

Remember the formula we learned for the 1900's, where we got the multiples of 12, kept the remainder,  
and added the number of 4's in the remainder? That still works, we just apply it to this century with  
Tuesday as the Doomsday for the 2000's.

Let's work through a couple of examples.

**Example**: what day of the week is May 29, 2017?  
(That would have been [John F. Kennedy](http://en.wikipedia.org/wiki/John_F._Kennedy)'s 100th birthday, had he lived.)  
**Answer**: 17 / 12 = **1**  
... remainder **5**  
... 5 / 4 is **1**  
... 1 + 5 + 1 = 7 which is 7=0 days to be added to Tuesday (for the 2000's)  
... Doomsday 2017 is **Tuesday** (which the chart above confirms)  
... May(5) 9th is Tuesday, 23rd is Tuesday  
... May 29th, 2017 is Monday.

**Example**: what day of the week is July 20, 2069? (That will be the 100th anniversary of the Apollo 11 moon landing.)  
**Answer**: 69 / 12 = **5**  
... remainder **9**  
... 9 / 4 is **2**  
... 5 + 9 + 2 = 16 which is 2 days to be added to Tuesday (for the 2000's)  
... Doomsday 2069 is **Thursday**  
... July(7) 11th is Thursday  
... July 18th is Thursday, so July 20th, 2069 is Saturday.

### Other Centuries

Let's construct another chart of years, extending backwards and forwards from the previous chart,  
except we want it to cover a bigger range of years. Let's show only those rows with a century year:

```
 ** Sun Mon Tue Wed Thu Fri Sat**  
 1599 **1600** 1601 1602 1603  
 **1700** 1701 1702 1703 1704 1705  
 1796 1797 1798 1799 **1800** 1801  
 1897 1898 1899 **1900** 1901 1902 1903  
 1999 **2000** 2001 2002 2003  
 **2100** 2101 2102 2103 2104 2105  
 2196 2197 2198 2199 **2200** 2201  
 2297 2298 2299 **2300** 2301 2302 2303  
 2399 **2400** 2401 2402 2403  
 **2500** 2501 2502 2503 2504 2505
```

Examine this chart carefully, until you convince yourself that it is behaving exactly as you would expect for  
leap century years and non-leap century years. Remember the rule for determining a leap year:

*   if it's divisible by 4, it is a leap year,
    *   unless it's divisible by 100, then it's **not** a leap year,
        *   unless it's divisible by 400, then it **is** a leap year

Each normal year advances Doomsday by one day. Each leap year advances Doomsday by two days. Now look at the century years again:

```
 **Sun Mon Tue Wed Thu Fri Sat**  
 1700 1600  
 2100 2000 1900 1800  
 2500 2400 2300 2200
```

What's the best way to memorize century Doomsdays? I'm not sure. Here's what I use.  
Notice that century Doomsdays fall only on "Sun-Tue-Wed-Fri".  
I say this as "Son to wed Friday", thinking of my own (_second_) son and how pleased I would be if he were indeed getting married this Friday  
(my first son got married on a Saturday in 2003).

Combine "Sun-Tue-Wed-Fri" with Dr. Conway's "We-in-dis-day" for 1900=Wednesday and "2000=Tuesday", and I can reconstruct the chart mentally.  
The tricky part is that the years go right to left in each row, but 2000=Tue and 1900=Wed help with this.  
The easy part is that if you can get just that one row, with 2000=Tue and 1900=Wed in it, then the other years have the  
**same Doomsday, plus or minus 400 years**.

**Example**: what day of the week is Canada's 300th birthday, July 1st, 2167?  
**Answer**: 67 / 12 = **5**  
... remainder **7**  
... 7 / 4 = **1**  
... 5 + 7 + 1 = **13** i.e. **6**  
... 6 + **2100=Sunday** = Saturday  
... July(7) 11th is a Saturday, so July 1st, 2167, is Wednesday.

[Return to top](http://rudy.ca/doomsday.html#content)

The Hand
--------

Dr. Conway now teaches the Doomsday algorithm, complete with Century adjustment, using a very simple visual aid—your hand.

```
 \_\_\_\_\_  
 \_\_\_\_/ \_\_\_)\_\_\_\_ <-- 1  
 \_\_\_\_\_\_\_) <-- 2  
 \_\_\_\_\_\_\_\_) <-- 3  
 \_\_\_\_ \_\_\_\_\_\_\_) <-- 4  
 \\\_\_\_\_\_\_\_\_) <-- 5
```

> 1 -- Doomsday Difference  
> 2 -- Century Day  
> 3 -- number of DOZENS  
> 4 -- remainder  
> 5 -- number of 4s in remainder

The **Doomsday Difference** is the difference between the required date and a nearby Doomsday,  
recorded as so many days "on" (i.e. to be added) or "off" (subtracted) from that Doomsday.

Recall a couple of the examples we've covered:

*   July 4th is always Doomsday, i.e. the Doomsday Difference is 0
    
*   Christmas, December 25th, is always "1 off" Doomsday
    

Be careful with the Doomsday Difference for dates in January and February. (Thanks to Bob Goddard for pointing this out.)  
In a leap year, we must subtract 1 from the Doomsday Difference for January and February dates:

*   Valentine's Day, February 14, is always "1 off" Doomsday in leap years, when Doomsday is February 29th;  
    in ordinary years, the Doomsday Difference for Valentine's Day is 0
    
*   Groundhog Day, February 2, is only "1 on" Doomsday in leap years, when Doomsday is February 29th;  
    in ordinary years, the Doomsday Difference for Groundhog Day is "2 on"
    
*   New Year's Day, January 1, is always "3 off" Doomsday in leap years, when Doomsday is the 4th of January;  
    in ordinary years, the Doomsday Difference for New Year's Day is "2 off"
    

### Examples using the hand

Here, in his own description, is how Dr. Conway would calculate the day of the week for Pearl Harbor Day, December 7th, 1941.

> The various numbers to be attached to the hand are (reading from the thumb):
> 
> *   "2 on" (for Dec 7)
> *   "Wednesday" (for 1900)
> *   "3 dozen" (getting us to 1936)
> *   "5 remainder" (number of years after 1936)
> *   "and 1" (since one of those 5 years was a leap year).
> 
> Don't start adding these up until you've formed them all, and then proceed as far as possible by cancelling first 14s, then 7s.  
> To make sure we haven't forgotten them, let's say:
> 
> > " 2, Wed, 3, 5, 1 "
> 
> (touching the appropriate digits as we do so), and then cancel that 2+5=7 (and folding down the thumb and ring finger) to get
> 
> > "Wed, 3 and 1 " = Wed + 4 = Sun
> 
> I also advise use of my mnemonic names for weekdays, namely:
> 
> > NUNday, ONEday, TWOSday, tWEBLESday, FOURSday, FIVEday, SIXurday, SE'ENday
> 
> which can be pronounced so that they both sound like numbers and weekdays, and so help you do the addition, for example
> 
> > " TREBLES, 3 and 1 = SEVENday " (Sunday)
> 
> in the above case.

The nice part about Dr. Conway's Hand is that we do the calculations **in the same order we usually say the date -- month/day,  
then century/year.** For example, for August 4, 1997, we do August 4, then 19, then 97.

**Example**: what day is August 4, 1997?  
**Answer**:

```
 \_\_\_\_\_  
 \_\_\_\_/ \_\_\_)\_\_\_\_ <-- **4 off** (Aug 4)  
 \_\_\_\_\_\_\_) <-- **Wed** (for 1900)  
 \_\_\_\_\_\_\_\_) <-- **8** DOZENS  
 \_\_\_\_ \_\_\_\_\_\_\_) <-- remainder **1**  
 \\\_\_\_\_\_\_\_\_) <-- and **0**
```

which is "4 off, tWEBLESday, 8, 1" or -4+3+8+1 which is 1, so August 4, 1997 is a Monday.

Finally, one last warning: Watch out for Gregorian versus Julian dates. The Doomsday algorithm described up to this point covers  
only Gregorian dates.

**Example**: what day was September 14, 1752?  
**Answer**:

```
 \_\_\_\_\_  
 \_\_\_\_/ \_\_\_)\_\_\_\_ <-- **2 on** (Sep 14)  
 \_\_\_\_\_\_\_) <-- **Sun** (for 1700)  
 \_\_\_\_\_\_\_\_) <-- **4** DOZENS  
 \_\_\_\_ \_\_\_\_\_\_\_) <-- remainder **4**  
 \\\_\_\_\_\_\_\_\_) <-- and **1**
```

which is "2, Sun, 4, 4, 1" and we can throw out the 2, a 4 and the 1 to get **4 on Sunday**, so September 14, 1752 was a Thursday.

That was a trick question, sort of. September 14, 1752 was the first day of the Gregorian calendar in England and its colonies.  
(The Gregorian calendar was originally adopted in parts of Europe in 1583). So September 1752 actually looked like this:

```
Sun Mon Tue Wed Thu Fri Sat  
 1 2 14 15 16  
 17 18 19 20 21 22 23  
 24 25 26 27 28 29 30
```

Neat, eh?

[Return to top](http://rudy.ca/doomsday.html#content)

Origins
-------

The Doomsday algorithm was created by **John Horton Conway**, an eminent mathematician, perhaps best  
known as the inventor of the [Game of Life](http://en.wikipedia.org/wiki/Conway's_Game_of_Life).

I first heard about the Doomsday algorithm on November 27, 1982, on a **CBC Radio** program  
called [Quirks and Quarks](http://www.cbc.ca/quirks/). Dr. Conway was interviewed by **Jay Ingram**,  
who later worked at Discovery Canada and has recently  
[released a new book  
called The End of Memory](http://www.cbc.ca/news/canada/british-columbia/jay-ingram-explores-alzheimer-s-disease-in-new-book-1.2976547). Anyhow, back in those days Quirks and Quarks occasionally made typed transcripts available,  
and I sent away for one.

Dr. Conway had just published a book that year (co-authored by Elwyn R. Berlekamp and Richard K. Guy) called  
[Winning Ways For Your Mathematical Plays](http://amazon.com/exec/obidos/ASIN/0120911027/r937-20),  
Volume 2: Games in Particular, Academic Press, London, 1982, ISBN 01-12-091102-7. The Doomsday algorithm is on pages 795-797,  
and the rest of the book is mainly about games, with substantial emphasis on their mathematical underpinnings.

In the original version of the Doomsday algorithm, the odd months were a bit harder to remember than "I work from 9-5 at the 7-11."  
You had to remember if the odd month was a long month or a short month. The 3rd, 5th, and 7th months are "long" because March, May, and  
July have 31 days, while the 9th and 11th months are "short" because September and November have only 30 days.  
You could remember "30 days hath September... and November" (but be careful because this old rhyme includes  
April and June which are even months). Anyway, **for long odd months, Doomsday is the (N+4)th, while for short odd months,  
Doomsday is the (N-4)th.** The mnemonic was long=add, short=subtract. Thus:

*   March (3rd month, long) 3+4=**7**th is Doomsday
*   May (5th month, long) 5+4=**9**th is Doomsday
*   July (7th month, long) 7+4=**11**th is Doomsday
*   September (9th month, short) 9-4=**5**th is Doomsday
*   November (11th month, short) 11-4=**7**th is Doomsday

I'd agree that it's easier to remember "I work from 9-5 at the 7-11" together with "March 0th=7th".

### Additional background

For more on the development of the Doomsday Algorithm,  
see [Doomsday Timeline](http://doomsdayrule.blogspot.ca/2011/01/doomsday-timeline.html).

[The Second Doomsday Lesson](http://blog.tanyakhovanova.com/?p=232) describes a 2010 meeting with Dr. Conway in which he explains the "Hand"  
method on the back of a napkin (picture included).

### Pi Days

I recently received the following email from reader **Roman Weil**, currently teaching at Princeton.

> I've been teaching Doomsday Rule for about fifteen years because I can show students the first day of class what my exam questions  
> are like-working backwards. If Thanksgiving Thursday is November 27 in a Leap Year, what is the day of the week of Feb. 28 that year?
> 
> Students can think they have mastered the rule and still not answer the question. I can show them up front that directionally correct  
> doesn't cut it; thorough mastery is needed. Doomsday is a good way to get them there on the first day.
> 
> Students invariable ask why the name. When I taught at Princeton five years ago, I asked my old college roommate to get to John Conway  
> and ask. To my surprise it took 3, not 2, degrees of separation to get to him. He said he wanted the name to end in "-day" and "Dooms"  
> popped into his head.
> 
> About a decade ago, one of my adult students said his family had used the rule for years and called it Pi Day, because 3.14 is a one, too.  
> From then, I call it Pi Day, because it's easier to explain the etymology.

Thanks so much, Roman. Delighted to have this background.

In case it wasn't obvious, "Pi day" refers to March 14th because 3.14 are the first significant digits of π.  
And of course March 14th is always a Doomsday.

Note: Roman also included a January trick by his son Sandy Weil which is mentioned in [Odd Months](http://rudy.ca/doomsday.html#odd).

[Return to top](http://rudy.ca/doomsday.html#content)

Links
-----

The following web sites are about or include descriptions of Dr. Conway's Doomsday algorithm.

*   [Doomsday Rule](http://en.wikipedia.org/wiki/Doomsday_rule) — the Wikipedia entry; very comprehensive.
    
*   [What Day Is Doomsday? How to Mentally Calculate the Day of the Week for Any Date](https://www.scientificamerican.com/article/calendar-algorithm/),  
    October 2011 article in [Scientific American](http://www.scientificamerican.com/).
    
*   [First Sunday Doomsday Algorithm](http://firstsundaydoomsday.blogspot.ca/) explains a modification to the Doomsday algorithm using the "first Sunday of the month" and the "Odd+11" rule.
    
*   If you're into heavy math, see [Methods for Accelerating Conway's Doomsday Algorithm (part 1)](http://arxiv.org/ftp/arxiv/papers/1006/1006.3913.pdf) PDF
    
*   [Simon Cassidy](http://www.angelfire.com/dc2/calendrics/CALNDR-L/98/FEB/13sc1.html) comments on the "Hand" in the context of  
    the Dee-Cecil calendar.
    
*   [C.07.2 Can I calculate the date of Easter?](http://www.faqs.org/faqs/astronomy/faq/part3/index.html) explains Conway's algorithm  
    for Easter, and gives another explanation of his Doomsday algorithm;  
    includes the remark "Note to non-US readers: 'Seven-Eleven' is the name  
    of a ubiquitous chain of convenience stores." Reader **Richard Ezell**  
    wrote to me in 2004 to report that this explanation may not really be necessary,  
    as he had seen four 7-11 stores in a seven block stretch in Bangkok, Thailand.
    
*   [AST 309-TIME; What is the day of the week, given any date?](http://quasar.as.utexas.edu/BillInfo/doomsday.html)  
    contains notes by William H. Jefferys for a school course on time,  
    with another explanation of the Doomsday algorithm  
    (examples are from 1997).
    
*   [The Doomsday Rule for Fortnights](http://jimvb.home.mindspring.com/doom14.html), by Jim Blowers, gives calculations  
    for Doomsday based on 14-day periods.
    
*   Kate Larson's [Mathematical poem to calculate the "day of the week"  
    for any day of any year](http://web.archive.org/web/20061018103244/http://www.cs.wustl.edu/~ksl2/mathpoem.html) is a beautiful, whimsical poem,  
    attributed to Dr. Conway, which describes the algorithm completely,  
    including both Gregorian and Julian century adjustments.  
    (Note: link goes to [archive.org](http://web.archive.org/), as the original has dropped off the Web.)
    

For more information about Dr. Conway, see:

*   [John Horton Conway: the world's most charismatic mathematician](http://www.theguardian.com/science/2015/jul/23/john-horton-conway-the-most-charismatic-mathematician-in-the-world). "John Horton Conway is  
    a cross between Archimedes, Mick Jagger and Salvador Dalí. For many years, he worried that his  
    obsession with playing silly games was ruining his career — until he realised that it could lead  
    to extraordinary discoveries." Story by Siobhan Roberts, author of Genius at Play, The Curious  
    Mind of John Horton Conway published by Bloomsbury, 2015.
    
*   [Inside the mind of 'mathemagician' John Horton Conway](http://www.thestar.com/news/insight/2015/08/23/inside-the-mind-of-mathemagician-john-horton-conway.html). In this Toronto Star excerpt from her biography, Genius at Play,  
    author Siobhan Roberts introduces readers to a distinguished scholar who claims never to have worked a day in his life.
    
*   [Interview with John Horton Conway](http://www.ams.org/notices/201305/rnoti-p567.pdf) (PDF). Edited version of an interview  
    with John Horton Conway conducted in July 2011 at the first International Mathematical  
    Summer School for Students at Jacobs University, Bremen, Germany
    
*   [Not Just Fun and Games](http://www.sciam.com/article.cfm?id=not-just-fun-and-games)  
    April 1999 Scientific American profile of John H. Conway.  
    (**Note:** this article is now available online only if you purchase the digital edition.)
    
*   Charles Seife's  
    [Mathemagician](http://www.cloud9.net/~cgseife/conway.html) -- an  
    amusing article about John Horton Conway.
    
*   [John  
    Conway's Game of Life](http://www.tech.org/~stuart/life/life.html) by Stephen Stuart -- an interactive  
    version that you can play via your web browser.
    

### Interesting calendar links

For links to other calendar sites, see my [Calendar Links](http://rudy.ca/callinks.html) page; CAUTION, this page of links has not been updated since 2003!

* * *

[![KaBoL logo](http://rudy.ca/candy.gif)](https://cms.math.ca/Kabol/)  
The Doomsday Algorithm was "latest link in the braid" for the week of  
[April 6-12, 1999](http://cms.math.ca/cgi/kabol/browse.pl?Number=154).

"This page will teach you a simple algorithm to calculate  
mentally the day of the week corresponding to any given date.  
Give it a try, it's quite rewarding! The page features clear  
instructions, examples, and mnemonic tricks."

**KaBoL** is a "cool math site of the week" service to the  
mathematics community provided by the  
[Canadian Mathematical Society](http://cms.math.ca/).

[Return to top](http://rudy.ca/doomsday.html#content)

  
  
from Hacker News https://ift.tt/1iGXZiV