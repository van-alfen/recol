
# RECOL

This package dynamically **RE**sizes **COL**umns in Stata's data browser.



## Installation and updates

To install:

```stata
ssc install recol
```

To update:

```stata
ado update recol, update
```

To uninstall:

```stata
ssc uninstall recol
```



## Syntax

**recol** [*varlist*] [, *options*]



## Options

- **maxwidth**(#)
	- The maximum allowable column width, in characters, for each *var* in *varlist*. When **maxwidth** is not specified, a default value of 50 is used.

- **userows**(#)
	- To achieve faster execution, **recol** only examines the first 100 rows and uses the content of those rows to infer the appropriate width of the column. The **userows** option indicates how many rows to use instead.

- **full**
	- To achieve faster execution, **recol** only examines the first 100 rows and uses the content of those rows to infer the appropriate width of the column. The **full** option causes the program to examine all rows to infer the appropriate width of the column. This may be useful if there are many missing values at the beginning of the data, but the program will slow down with larger datasets. If **full** and **userows** are both specified, **full** is used and **userows** is ignored.

- **compress**
	- Some users frequently pair the **compress** command with **recol**. Use this option to **compress** the data at the end.



## Description

**recol** examines your variable names and the content of your variables in order to determine the appropriate display widths for your columns in the data browser. It works with both string and numeric variables.

For example, suppose you have a rather long variable name (*your_long_variable_name*) which gets truncated by Stata when displaying your data in the Browser (*your_long_v~e*). Rather than manually clicking and dragging to resize the column every time, **recol** widens your columns automatically to display the full variable names.

A common issue with string variables is excessively long content. This can result in jumpy horizontal scrolling from columns that are too wide. **recol** reduces these column widths to a predefined max width, resulting in easier data browsing.



## Examples

Dynamically resize all columns in the data.

```stata
recol
```

Dynamically resize a subset of columns with a max width of 25 characters

```stata
recol var1 var2 var3, max(25)
```

Dynamically resize a single column, using the first 2,000 observations to determine width

```stata
recol var1, userows(2000)
```

Dynamically resize a single column, using the full set of observations to determine width

```stata
recol var1, full
```

Dynamically resize all columns and then compress the data.

```stata
recol, c
```
