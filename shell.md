# shell cheatsheet

## Commands and Files

### Files

1. `/proc/cpuinfo` - Contains info on the CPUs in the system. 

### Commands

1. `ln -s source target` - When a file exists in the `source` location and you want a shortcut/symbolic link to appear in a new location `target` that points to `source`, use this command.

## Cookbook

### Find and remove files recursively

To remove all files with a JPG extension in a given folder path, recursively:

`find /folderpath -name '*.jpg' -exec rm {} \;`

### Create multi-line file from shell

This will create a file `greetings.txt` with two lines in it, the first being `line 1` and the second being `line 2`:

```bash
cat <<EOT > greetings.txt
line 1
line 2
EOT
```

Alternately, you can append multiple lines to an existing file:

```bash
cat <<EOT >> newhosts
127.0.0.1 localhost
10.0.0.1 localhost
EOT
```

### Exporting variables using text file

Let's say you have a file called `.secrets` with the following variable settings:

```bash
DB_NAME=dbname
DB_USER=root
DB_PASS=fakepassword
DB_HOST=databaseserver.com
```

You can do `source .secrets` to get those variables available in the shell:

```bash
$ echo $DB_HOST
databaseserver.com
```

But then if you run a program like `python` those variables will not be available in the environment local to that program:

```
$ python
>>> import os
>>> os.getenv('DB_HOST')
```

To get these variables available in your shell AND available in any programs you run from the shell (without using `sudo`), you have to use the [export](https://linuxconfig.org/learning-linux-commands-export) function along with a command to get the variable names from the `.secrets` file:

```bash
source .secrets && export $(cut -d= -f1 .secrets)
```

Then, when you go in to the python prompt again you'll be able to access the variables:

```
$ python
>>> import os
>>> os.getenv('DB_HOST')
'databaseserver.com'
```

### GNU coreutils - the swiss army knife of the shell

You can do a lot of calculations on text in files, and the text input and output of programs, without writing a script, using the GNU coreutils. Some useful ones:

1. `wc` - Does a Word Count, in some interpretations.
2. `cut` - Cuts a text string based on delimiters or specific character indexes.
3. `head` - Gets the first lines of a file, based on offset from the start or end of the file.
4. `sed` - Stream Editor, you can use regular expressions on lines of text.

#### To get the number of lines in a file `1929/032620-99999-1929.op` (a weather station's data for 1929):

```bash
wc --lines 1929/032620-99999-1929.op
```

With output:

```
92 1929/032620-99999-1929.op
```

#### To get the number of files in a folder `1929`:

```bash
ls -1 1929 | wc --lines
```

With output:

```
21
```

Where running:

```bash
ls -1 1929
```

Would have output:

```
030050-99999-1929.op
030750-99999-1929.op
030910-99999-1929.op
031590-99999-1929.op
032620-99999-1929.op
033110-99999-1929.op
033790-99999-1929.op
033960-99999-1929.op
034970-99999-1929.op
036010-99999-1929.op
037770-99999-1929.op
037950-99999-1929.op
038040-99999-1929.op
038110-99999-1929.op
038560-99999-1929.op
038640-99999-1929.op
038940-99999-1929.op
039530-99999-1929.op
039730-99999-1929.op
039800-99999-1929.op
990061-99999-1929.op
```

#### To get the line counts for each one of the files:

```bash
wc --lines 1929/*.op
```

With output:

```
    91 1929/030050-99999-1929.op
    92 1929/030750-99999-1929.op
    76 1929/030910-99999-1929.op
    91 1929/031590-99999-1929.op
    92 1929/032620-99999-1929.op
    90 1929/033110-99999-1929.op
   148 1929/033790-99999-1929.op
    92 1929/033960-99999-1929.op
   153 1929/034970-99999-1929.op
    91 1929/036010-99999-1929.op
   150 1929/037770-99999-1929.op
   149 1929/037950-99999-1929.op
    91 1929/038040-99999-1929.op
    92 1929/038110-99999-1929.op
    92 1929/038560-99999-1929.op
    89 1929/038640-99999-1929.op
    89 1929/038940-99999-1929.op
    90 1929/039530-99999-1929.op
    89 1929/039730-99999-1929.op
    90 1929/039800-99999-1929.op
    44 1929/990061-99999-1929.op
  2081 total
```

#### To get rid of this last line:

```bash
wc --lines 1929/*.op | head --lines=-1
```

With output:

```
    91 1929/030050-99999-1929.op
    92 1929/030750-99999-1929.op
    76 1929/030910-99999-1929.op
    91 1929/031590-99999-1929.op
    92 1929/032620-99999-1929.op
    90 1929/033110-99999-1929.op
   148 1929/033790-99999-1929.op
    92 1929/033960-99999-1929.op
   153 1929/034970-99999-1929.op
    91 1929/036010-99999-1929.op
   150 1929/037770-99999-1929.op
   149 1929/037950-99999-1929.op
    91 1929/038040-99999-1929.op
    92 1929/038110-99999-1929.op
    92 1929/038560-99999-1929.op
    89 1929/038640-99999-1929.op
    89 1929/038940-99999-1929.op
    90 1929/039530-99999-1929.op
    89 1929/039730-99999-1929.op
    90 1929/039800-99999-1929.op
    44 1929/990061-99999-1929.op
```
#### To get rid of the leading spaces:

```bash
wc --lines 1929/*.op | head --lines=-1 | sed 's/[ \t]*//'
```

With output:

```
91 1929/030050-99999-1929.op
92 1929/030750-99999-1929.op
76 1929/030910-99999-1929.op
91 1929/031590-99999-1929.op
92 1929/032620-99999-1929.op
90 1929/033110-99999-1929.op
148 1929/033790-99999-1929.op
92 1929/033960-99999-1929.op
153 1929/034970-99999-1929.op
91 1929/036010-99999-1929.op
150 1929/037770-99999-1929.op
149 1929/037950-99999-1929.op
91 1929/038040-99999-1929.op
92 1929/038110-99999-1929.op
92 1929/038560-99999-1929.op
89 1929/038640-99999-1929.op
89 1929/038940-99999-1929.op
90 1929/039530-99999-1929.op
89 1929/039730-99999-1929.op
90 1929/039800-99999-1929.op
44 1929/990061-99999-1929.op
```

#### To get just the numbers representing the counts of lines:

```bash
wc --lines 1929/*.op | head --lines=-1 | sed 's/[ \t]*//' | cut --delimiter=" " --fields=1
```

With output:

```
91
92
76
91
92
90
148
92
153
91
150
149
91
92
92
89
89
90
89
90
44
```

#### To get the minimum number of lines per file, maximum, median, and mean, you can rely on a small bit of R script. Create a file `summary.r` with the following contents:

```rscript
#! /usr/bin/env Rscript
d<-scan("stdin", quiet=TRUE)
summary(d)
```

Make this script executable with:

```bash
chmod +x ./summary.r
```

Install R if you don't have it already, then run:

```bash
wc --lines 1929/*.op | head --lines=-1 | sed 's/[ \t]*//' | cut --delimiter=" " --fields=1 | ./summary.r
```

With output:

```
   Min. 1st Qu.  Median    Mean 3rd Qu.    Max.
   44.0    90.0    91.0    99.1    92.0   153.0
```

#### To get these statistics for every year folder, from 1929 to 2017:

```bash
for year in {1929..2017}
do
    echo $year
    wc --lines $year/*.op | head --lines=-1 | sed 's/[ \t]*//' | cut --delimiter=" " --fields=1 | ./summary.r
done
```

With output in this [summary.txt](https://github.com/tothebeat/noaa-gsod-data-munging/blob/master/summary.txt) of the noaa-gsod-data-munging repo that this contributed to.

## References:

1. [How to append multiple lines to a file](https://unix.stackexchange.com/a/77278/107124)
2. [How to Install R on Ubuntu 16.04](https://www.digitalocean.com/community/tutorials/how-to-install-r-on-ubuntu-16-04-2)
3. [`cut` examples](https://en.wikipedia.org/wiki/Cut_(Unix)#Examples)
4. [Creating the `summary.r` Rscript](https://unix.stackexchange.com/a/13775/107124)
5. [Input/Output redirection in the shell](https://robots.thoughtbot.com/input-output-redirection-in-the-shell)
6. [noaa-gsod-data-munging](https://github.com/tothebeat/noaa-gsod-data-munging)
7. [StackOverflow - How to export variables from a file?](https://unix.stackexchange.com/a/79065/107124)
8. [Learning Linux Commands: export](https://linuxconfig.org/learning-linux-commands-export)
9. [8 commands to check cpu information on Linux](http://www.binarytides.com/linux-cpu-information/)
