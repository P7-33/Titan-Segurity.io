---
title: 'How to Open and Manipulate Large (100MB) CSV Files on a Mac'
date: 2019-11-05T05:39:00+01:00
draft: false
---

**How To Open & Manipulate Large (>100MB) CSV Files On A Mac**
--------------------------------------------------------------

Have you ever struggled to open and manipulate a large CSV file on a Mac? 100MB? 1 gigabyte or greater? Extremely large CSVs bring most spreadsheet utilities to a halt or the computer. I set out to figure out how to open and manipulate these files in a free and somewhat accessible way that was fast and didn’t risk crashes.

As a software engineer with a history of supporting marketing teams, I often encounter extremely large datasets including customer segment exports or analytics event logs that can be larger than a gigabyte. A good text editor can open these large CSVs but you lose spreadsheet capabilities like rearranging columns and filtering data.

In this post, I’ve outlined the different ways I’ve tried to manipulate large CSVs and their results. I’m using a 2018 Macbook Pro with a 2.6 GHz 6-core i7 and 16 GB of RAM. If you would like to skip the story and go straight to the best free solution, please [click here](https://www.alecdibble.com/blog/large-csvs-on-mac/#tldr).

### **Numbers & Excel**

Numbers honestly performed the worst. It has a hard row limit that seemed to be independent of file size. This made it useless for my task. Google Sheets worked for some files but would tend to crash or hang past a certain file size. Excel for Mac performed well but it is a paid solution so I did not consider it viable for many developers. Typically, opening large CSVs is a relatively rare occurrence unless your a data analyst, so I tried to find a free solution that would work well. Additionally, Excel’s file size limit appears to be 2 gigabytes, so it won’t work well for anything larger than that.

### **OpenRefine**

Google released a handy tool now called [OpenRefine](http://openrefine.org/) that enables lots of handy data manipulation operations. I was hoping this would be my answer to manipulating large CSVs. However, it definitely started getting really slow and crashing with files greater than a hundred megabytes. This is based on my memory from several months ago, I may test to get some better data around when it starts to crash.

### **CSV Explorer**

I found a great SaaS solution for the problem, called [CSV Explorer](https://www.csvexplorer.com/). They built a web tool to solve this exact problem. They have a free plan that has a limit of 5 million rows. If your data is column-heavy, this may be a great solution. The paid plans support up to 20 million rows. It’s a great solution if you don’t mind paying. Like I said earlier in the post, I desired a free solution so I kept researching.

### **MySQL Import Using Sequel Pro**

Many database management programs give you the ability to import a CSV file. I had [Sequel Pro](https://www.sequelpro.com/) installed so I decided to give this method an attempt. Sequel Pro is a free MySQL graphical management application for Macs. It has a great CSV import feature because it will help generate a table based on the CSV automatically. Here is a quick overview on how that works: 

1.  Select the database you want to import into (or create a new one) and then go to File -> Import…

[![](https://www.alecdibble.com/contents/data/2019/11/image1-300x277.png)](https://www.alecdibble.com/contents/data/2019/11/image1.png)

1.  Select the appropriate CSV files and make sure the import settings match your file’s needs.

[![](https://www.alecdibble.com/contents/data/2019/11/image2-300x170.png)](https://www.alecdibble.com/contents/data/2019/11/image2.png)

1.  It’s best practice to name the table the same name as the file. This is especially important if later importing a much larger file into the same table.

[![](https://www.alecdibble.com/contents/data/2019/11/image3-300x166.png)](https://www.alecdibble.com/contents/data/2019/11/image3.png)

Just like the other methods, the program crashed or froze when sufficiently large files were attempted. Specifically, my 1.32 GB CSV made Sequel Pro crash instantly.

### **MySQL Import Using Sequel Pro and the Command Line (Working Solution)**

Finally! I found a solution that works reliably for large CSVs. Additionally, you can do complex sorting, filtering, and transformation operations if you are proficient with SQL.

For the sake of this example, let’s assume we are working with a CSV file >1GB that is called _**very\_large\_nov\_2019.csv**_. 

First, you must create a CSV file contain only the first 10-20 lines of your large CSV file, we will call it _**very\_large\_nov\_2019\_abridged.csv**_. I prefer to use a text editor to open the large CSV and then copy and paste the first 10-20 lines into a new text editor window and saving that file with a .csv extension. 

Then, utilize the Sequel Pro import method described above. Make sure the table name matches the name of the original CSV file. In our example case, the table name should be _**very\_large\_nov\_2019**_.  Once the new table is created, go ahead and delete the rows in the table in preparation for the import of the large version of the CSV.

Use the following command to import your CSV file. I have enclosed data you must change in brackets (\[  \]). 

```
mysqlimport --ignore-lines=1 --fields-terminated-by=, --fields-optionally-enclosed-by='\\"' --verbose --local -u \[mysql username\] -p \[database name\] \[csv file path\]
```

The table name should match the CSV name. If you created the table using Sequel Pro, this should be easy to accomplish. If you need to use a table name that is different than the filename, you can create a symbolic link:

```
ln -s \[your csv file\] \[table name\].csv
```

To learn more about mysqlimport, it’s best to refer to the command on your system. You can read the man pages which are lengthy but thorough:

```
man mysqlimport
```

Or you can read the brief help output:

```
mysqlimport --help
```

If you have any questions about this article or would like to get help with your MySQL problems, feel free to contact me.

  
  
from Hacker News https://www.alecdibble.com/blog/large-csvs-on-mac/