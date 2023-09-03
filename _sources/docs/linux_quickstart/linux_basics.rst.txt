============================
Minimal Unix skills to have
============================
:Authors:
    Luis Belmar Letelier <luis.belmar-letelier@mazars.fr>
:Version: 2021

:Training reviewer:
    Luis Belmar-Letelier <lbelmarletelier@zettafox.com>

General
=======
Shell programming allows you to perform tasks (manipulating files, creating
directories, executing programs, printing text, etc.) by typing commands from
the keyboard into the command line interface.

- Please watch this: https://www.youtube.com/watch?v=7uwW20odwEk
- And this https://www.youtube.com/watch?v=gd7BXuUQ91w&pp=ygUPdW5peCA4MCBjb21hbmRz

Unix System Concept
===================
- All is file (directories, input devices too)
- All is process
- Using 'Tab' is good (to use word completion instead of typing the whole command)

File system
===========
The filesytem appears as one rooted tree of directories. Instead of addressing
separate volumes such as disk partitions and removable media as separate trees
(which is the case in  Windows: partitions C: and D: for the primary drive, E:
for DVD, F:for USB stick, etc.) such volumes can be **mounted on a directory**
(mountin point), causing the volume's file system tree to appear as that
directory in the larger tree. The root of the entire tree is denoted `.`::

  $ tree
  .
  ├── example_dir
  │   └── tot.txt
  ├── out.pdf
  ├── practice_data2.rst
  ├── practice_data.rst
  ├── symbols.py
  ├── tasks.pdf
  ├── Tools_bash.rst
  ├── Tool_vim.rst
  └── train.rst

Example of output from the **tree** command : 8 files and 1 directory
(example_dir) are attached to the working directory. One file (tot.txt) is
attached to the sub-level directory example_dir.

Shell(s) and Environment Variables
===================================
**$bash** will create a child bash process

List of basic environment variables (convention: write their names with capital letters,
and add a $ sign in front of them)::

  $USER: name of logges in user
  $UID: numeric user ID
  $HOME: user's home directory
  $PWD: current working directory
  $SHELL: name of the shell
  $$: process id (= PID)
  $PPID: if of the parent process
  $?: exit code of the last command
  $PATH: environment variable specifying a set of directories where executable programs are located.

To display information about the current shell process, you can use the command
**ps**, please refer to exercise 15 to give it a try.

In order to create an environment variable that will be recognized by child
processes, you will need to export it first with **export**.

Use **env** command without any options to display all current shell
environment variables.

Terminal Glossary
====================
Most unix commands have a variety of options that can be executed in the
command with flags, such as `ls -l -a` that can be written `ls -la`.

=================================================  ===================================================
Command                                            Purpose
=================================================  ===================================================
**df**                                             display free disk space
**ls**                                             list information about files in current directory
**pwd**                                            print name of current/working directory
**tree**                                           lists contents of directories in a tree-like format
**cd**                                             change directory: e.g `cd ~/Images`
**cp**                                             copy a file from one place to another: e.g. `cp /tmp/f1.h /tmp/a/f1.h`
**mv**                                             move or rename a file: e.g. `mv /tmp/a/f1.h /tmp/b/c/`
**rm**                                             remove files, use `rm -r` to remove directories
**rmdir**                                          remove directories (they need to be empty)
**mkdir**                                          make directories: `mkdir -p /tmp/a/b/c`
**man**                                            help manual (ex: man df)
**cat**                                            concatenate files and print on the standard output
**touch**                                          create/change time stamp of file
**head**                                           output the first part of a file
**tail**                                           ouput the last part of a file
**more**                                           more is a filter for paging through text one screenful at a time e.g.
                                                   `cat file_with_much_data.txt | more`
**less**                                           like more but you can then navigate in the content
**grep**                                           print lines that match patterns, input can be a file or stream from a pipe
**|** (pipe)                                       pass the ouput of the first command as input of the
                                                   second command
**<**                                              (redirect) a command use to redirect data into a file.
**>**                                              redirect output from a command to a file
**>>**                                             append output from a command to existing file
**{,}** (brace expansion)                          used to generate saving typing time
                                                   ex: `mv a.{txt,doc}` is expanded as `mv a.txt a.doc`
**nano**                                           a text editor. NEVER USE THIS go vim e.g. `vim code.py`
=================================================  ===================================================

========= =========================================================================
`sudo`    super user do. many commands need administrator-like privileges,
          otherwise they won’t work. apt-get is a command that needs to be run
          with sudo to allow files to be written to protected directories.
          You’ll see sudo as the first word in a lot of commands - this will
          give the command the necessary access. You’ll be asked for
          a password the first time you use sudo.

`apt-get` the command used for installing, removing, and finding software for
          Debian Linux systems. e.g `sudo apt-get install tree`
          install `tree` and all needed dependeneies.

`find`    look for files in the filesystem. Ex: find ~/Documents -name
          particular.txt -type f will look for the file with the name
          particular.txt in the Documents directory.

`chmod`   change mode. Used for file permissions.

`htop`    display the processes currently alive on the CPU, type `q` to exit.
          If `htop` not present on your linux use `top`

`scp`     secure copy. copy a file from one computer to another over a network.
          e.g. `scp /tmp/f1.h akd6.zettafox.com:/tmp/`
          work both direction you can `scp akd6.zettafox.com:/tmp/ ~/Images/`
`ssh`     secure shell. access another computer on the network and use the
          terminal commands to make changes and control it.
          e.g. `ssh akd6.zettafox.com`
`CTRL C`  means “interrupt”, i.e., stop what you're doing, this kill the process
`Ctrl d`  means end of file, used to terminate a remote or a sub-terminal and come back to the precedent one.
========= =========================================================================

Basic Commandes
================

Text streams: `cat`, `tail`, `head`, `more`, `less`, `touch`
--------------------------------------------------------------

`cat`
~~~~~~
Concatenate files::

    $ cat file1.txt file2.txt > file12.txt

`head` and `tail`
~~~~~~~~~~~~~~~~~~~
Get first `N` lines of data in a files or stream::

  $ head -2 data.txt
  a a
  b b
  $

Get end of data in a files or stream::

  $ cat data.txt
  a a
  b b
  ...
  y y
  z z
  $ tail -2 data.txt
  y y
  z z
  $

Concatenate files keeping only header from first file::

  $ cat data1.txt data2.txt
  head1, head2
  a, a
  b, b
  c, c
  head1, head2
  x, x
  y, y

  $ head -1 data1.txt > concat.txt;
  $ tail -n +2 -q data1.txt data2.txt >> concat.txt
  $ cat concat.txt
  head1, head2
  a, a
  b, b
  c, c
  x, x
  y, y

  # Same result with one command
  $ cat <(head -1 data1.txt) <(tail -n +2 -q data1.txt data2.txt) > concat.txt
  $

`more` and `less`
~~~~~~~~~~~~~~~~~~~
- `more`: is a filter for paging through text one screenful at a time e.g.::

    cat file_with_much_data.txt | more

- `less`: is like more but you can then navigate in the content::

    cat file_with_much_data.txt | less

So they return the output of a file or stream page per page (for `more`) or as a
scrolable stream (for `less`).

Note that all vim/unix shortcuts work e.g. end of stream with `G` search with
`\/` search backward git `?`.

`touch`
~~~~~~~
Create an empty file::

    $ touch /tmp/myfile.txt
    $ ls -la /tmp/myfile.txt
    -rw-rw-r-- 1 luis luis 0 janv. 17 21:31 /tmp/myfile.txt
    $

Update access date and modification date of an existing file::

  $ touch -t 201801010000 /tmp/myfile.txt
  $ ls -la /tmp/myfile.txt
  -rw-rw-r-- 1 luis luis 0 janv.  1  2018 /tmp/myfile.txt
  $

Available options:

- -d: add specific last access time (string format)
- -t: add specific last access time (.ss format)

`csplit`
~~~~~~~~~
csplit - split a file into sections determined by context lines::

  $ cat file.txt
  annee, text
  2020, a
  2020, b
  2020, c
  annee, text
  2019, x
  2019, y
  2019, z
  $ ls -A
  file.txt
  $

split on `^annee`::

  $ cat file.txt |csplit - /^annee/ {*}

  $ wc -l *
  8 file.txt
  0 xx00
  4 xx01
  4 xx02
  $

`-z` to avoid empty first file::

  $ rm xx*
  $ cat file.txt |csplit -z - /^annee/ {*}

  $ wc -l *
    8 file.txt
    4 xx00
    4 xx01
  $

`-b "_%02d.csv"` to change the ouput files pattern::

  $ rm -f xx*
  $ cat file.txt |csplit -b "_%02d.csv" -z - /^annee/ {*}

  $ wc -l *
    8 file.txt
    4 xx_00.csv
    4 xx_01.csv
  $
  $ cat xx_01.csv
  annee, text
  2019, x
  2019, y
  2019, z
  $

Process management: `ps`, `top`, `htop`
----------------------------------------
`ps`
~~~~~~
Displays the currently-running processes::

      PID TTY          TIME CMD
      4322 pts/1    00:00:00 bash
      4954 pts/1    00:00:00 ps

`top`
~~~~~
Task manager program::

  $ top
  PID UTIL.     PR  NI    VIRT    RES    SHR S  %CPU %MEM    TEMPS+ COM.
  3567 viphone   20   0 3911616 1,473g 146240 S  27,6 19,6  27:35.15 firefox
  1790 viphone   20   0  225620  61884  40776 S   1,7  0,8   1:33.15 Xorg
  1979 viphone   20   0 1824208 157912  67248 S   1,0  2,0   1:17.00 gnome-shel
  3440 viphone   20   0  703484  59596  35728 S   1,0  0
  $

`htop`
~~~~~~
Interactive task manager program::

  PID UTIL.     PR  NI    VIRT    RES    SHR S  %CPU %MEM    TEMPS+ COM.
  3567 viphone   20   0 3911616 1,473g 146240 S  27,6 19,6  27:35.15 firefox
  1790 viphone   20   0  225620  61884  40776 S   1,7  0,8   1:33.15 Xorg
  1979 viphone   20   0 1824208 157912  67248 S   1,0  2,0   1:17.00 gnome-shel
  3440 viphone   20   0  703484  59596  35728 S   1,0  0
  F1 Help  F2 Setup  F3 Search  F4 Filter  F5 Tree  F6 SortBy  F7 Nice


Files and Directories manipulation: `ls`, `tree`, `du`, `ncdu`, `df`
-----------------------------------------------------------------------
`ls`
~~~~~~
Lists files of a directory::

    $ ls fox_dojo/sphinx/source
    akd_db_edit.rst                 Python_email_check.rst
    akd-db-edit-trainingII.rst      Python_machine_learning.rst   ...

`tree`
~~~~~~
Show the tree of the subdirectories from a specific directory::

  $ mkdir -p unix/{a,b,c}
  $ mkdir -p unix/b/bb/bbb
  $ touch unix/b/bb/f5.txt
  $ touch unix/{a,b,c}/f1.txt

  $ tree unix/
  unix/
  ├── a
  │   └── f1.txt
  ├── b
  │   ├── bb
  │   │   ├── bbb
  │   │   └── f5.txt
  │   └── f1.txt
  └── c
      └── f1.txt

  $ tree /tmp/unix/
  /tmp/unix/
  ├── a
  │   └── f1.txt
  ├── b
  │   ├── bb
  │   │   ├── bbb
  │   │   └── f5.txt
  │   └── f1.txt
  └── c
      └── f1.txt

  $ tree -d -L 2 /tmp/unix/
  /tmp/unix/
  ├── a
  ├── b
  │   └── bb
  └── c

  $ tree -ah /tmp/unix/
  /tmp/unix/
  ├── [4.0K]  a
  │   └── [   0]  f1.txt
  ├── [4.0K]  b
  │   ├── [4.0K]  bb
  │   │   ├── [4.0K]  bbb
  │   │   └── [   0]  f5.txt
  │   └── [   0]  f1.txt
  └── [4.0K]  c
      └── [   0]  f1.txt
  $


`du`
~~~~
Estimate file space usage::

  $ du -sh .
  570M	.
  $

`ncdu`
~~~~~~
NCurses Disk Usage, navigable version of `du`::

    $ ncdu .

`df`
~~~~
Report file system disk space usage::

  $ df -h
  Sys. de fichiers            Taille Utilisé Dispo Uti% Monté sur
  udev                          7,6G       0  7,6G   0% /dev
  tmpfs                         1,6G    2,9M  1,6G   1% /run
  /dev/mapper/ubuntu--vg-root   453G    353G   77G  83% /
  tmpfs                         7,6G    355M  7,3G   5% /dev/shm
  tmpfs                         5,0M    4,0K  5,0M   1% /run/lock
  tmpfs                         7,6G       0  7,6G   0% /sys/fs/cgroup
  /dev/sda1                     704M    150M  503M  23% /boot
  tmpfs                         1,6G    100K  1,6G   1% /run/user/1000
  $


software management with `sudo`, `apt-get` and `dpkg`
--------------------------------------------------------
`apt-get`
~~~~~~~~~
Manage packages and libraries (install, uninstall, upgrade, ...)::

    $ apt-get install tree

`dpkg`
~~~~~~
Manage Debian packages `.dpgk` packages::

    $ dpkg -r elvis.dpkg

Access list of packages known by the system and their state::

    $ dpkg -l

See all files coming from one package::

    $ dpkg -L vagrant

Find the package from which the file comes from with `dpkg -S`::

    $ which pdfjam
    /usr/bin/pdfjam
    $ dpkg -S /usr/bin/pdfjam
    texlive-extra-utils: /usr/bin/pdfjam
    $

Find all packages installed.
Can be useful to save current state of your machine.::

    $ dpkg --get-selections > current_state.txt

Restore state::

    $ dpkg --set-selections < current_state.txt

`sudo`
~~~~~~
sudo allows a permitted user to execute a command as the superuser or another
user::

    $ sudo apt-get install gparted

Network: `curl`, `rsync`, `scp`, `ssh`
------------------------------------------

`Curl`
~~~~~~
http://stackoverflow.com/questions/15995919/curl-how-to-send-cookies-via-command-line


For urls with special characters use double quotes

`rsync`
~~~~~~~~
Powerfull tool to synchronize folders. For exemple to restore from a backup
folder all files keeping .git hardlinks, removing sources file and deleting
destinations files not in source::

  rsync -aH --delete --remove-source-files /bkp/luis/ /home/luis/

Streams filters and transformation: `sort`, `tr`, `awk`, `grep` and `sed`
===========================================================================
`sort`
-------
Let's sort some data::

  $ cat /tmp/data.txt
  BBB;4
  aaa;7
  zzz;4
  eee;8
  123;11
  9;9
  73234;0
  $ cat /tmp/data.txt | sort
  123;11
  73234;0
  9;9
  aaa;7
  BBB;4
  eee;8
  zzz;4

Sort it as numerical (`9` is smaller than `121`) with `sort -n`::

  $ cat /tmp/data.txt | sort -n
  aaa;7
  BBB;4
  eee;8
  zzz;4
  9;9
  123;11
  73234;0

Sort on the second part after the `;`::

  $ cat /tmp/data.txt | sort -t ';' -k 2
  73234;0
  123;11
  BBB;4
  zzz;4
  aaa;7
  eee;8
  9;9
  $ cat /tmp/data.txt | sort -t ';' -k 2 -n -r
  123;11
  9;9
  eee;8
  aaa;7
  zzz;4
  BBB;4
  73234;0
  $


`tr`
-----
**tr** to 'translate' a character e.g. spaces by TABs::

  $ echo 'a b c d' | tr ' ' '\t'
  a	b	c	d
  $

If we give two lists of same size `tr` replace list_1[i] by list_2[i] for all i e.g. translate `c` by `Z` and ` ` (space) by `=`::

  $ echo 'a b c d' | tr 'c ' 'Z='
  a=b=Z=d
  $

grep
----
This command line allows to find files containing a specific string of character.::

    grep -option string directory/file

Available options:

:-v: show the line that doesn't contain the string
:-c: count the number of lines containing the string
:-n: each line containing the string is numbered
:-x: list all the files containing the string
:-r: recursive to grep in all the subdirectory

To get shell variables that refer to 'luis'::

  $ env |grep luis
  LOGNAME=luis
  ARDUINO_DIR=/home/luis/arduino-1.8.10
  HOME=/home/luis
  USERNAME=luis
  VIRTUAL_ENV=/home/luis/venvs/venv
  NVM_DIR=/home/luis/.nvm
  npm_config_prefix=/home/luis/.node_modules
  USER=luis
  LD_LIBRARY_PATH=/home/luis/akd/lib:/usr/lib/jvm/java-7-openjdk-amd64/jre/lib/amd64/server
  PYENV_ROOT=/home/luis/.pyenv
  PATH=/home/luis/venvs/venv/bin:/home/luis/.node_modules/bin:/home/luis/.pyenv/plugins/pyenv-virtualenv/shims:/home/luis/.pyenv/shims:/home/luis/.pyenv/bin:/home/luis/.yarn/bin:/home/luis/.local/bin:/home/luis/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin
  $

To get shell variables that refer to 'luis'::

  $ env |grep luis| grep -v home
  | grep -v home
  LOGNAME=luis
  USERNAME=luis
  USER=luis
  $

To get the ones that has ardui OR PYENV::

  $ env |grep -E 'ardui|PYENV'
  PYENV_SHELL=bash
  PYENV_VIRTUALENV_INIT=1
  ARDUINO_DIR=/home/luis/arduino-1.8.10
  PYENV_ROOT=/home/luis/.pyenv
  $


`awk`
-------
Powerfull to manipulate streams as column::

  $ cat /tmp/d.csv
  animal,mysize,weight,adult,age,length
  0,cat,S,8,False,3,30.0
  1,dog,S,10,False,4,46.66666666666667
  2,cat,M,11,False,5,63.333333333333336
  3,fish,M,1,False,6,80.0
  4,dog,M,20,False,7,96.66666666666667
  5,cat,L,12,True,8,113.33333333333334
  6,cat,L,12,True,9,130.0

  $ cat /tmp/d.csv | awk -F',' '{print $3 ";" $1 ";" $4}'
  weight;animal;adult
  S;0;8
  S;1;10
  M;2;11
  M;3;1
  M;4;20
  L;5;12
  L;6;12
  $

We can give to `awk` a list of possibles separators (e.g. `,` and `=`)::

  $ cat /tmp/ddd.csv
  animal,mysize,length
  0,cat,S,l=30.0
  1,dog,S,l=46.66666666666667
  2,cat,M,l=63.333333333333336
  3,fish,M,l=80.0
  $
  $ cat /tmp/ddd.csv | awk -F'[,=]' '{print $2 " length is\t" $5}'
  mysize length is
  cat length is	30.0
  dog length is	46.66666666666667
  cat length is	63.333333333333336
  fish length is	80.0

We can use more than one caracter as separator for `awk` (Note this is not true for `tr` and `cut`::

  $ cat /tmp/dd.csv
  animal|#|mysize|#|weight|#|adult|#|age|#|length
  3|#|fish|#|M|#|1|#|False|#|6|#|80.0
  4|#|dog|#|M|#|20|#|False|#|7|#|96.66666666666667
  5|#|cat|#|L|#|12|#|True|#|8|#|113.33333333333334
  6|#|cat|#|L|#|12|#|True|#|9|#|130.0
  $

`|` and `\` are specials caracters for `awk` so we have to escape `|` as
`\\|`::

  $ cat /tmp/dd.csv | awk -F'\\|#\\|' '{print $5,$1,$7}'
  age animal
  False 3 80.0
  False 4 96.66666666666667
  True 5 113.33333333333334
  True 6 130.0
  $

To set the output separator once for all we use `-v OFS=\;`::

  $ cat /tmp/dd.csv | awk -F'\\|#\\|' -v OFS=\; '{print $5,$1,$7}'
  age;animal;
  False;3;80.0
  False;4;96.66666666666667
  True;5;113.33333333333334
  True;6;130.0
  $


Use Regular Expressions with `grep` and `sed`
-----------------------------------------------
Start by creating following directory and files::

  $  mkdir -p lpi103-7 && cd lpi103-7 && {
     echo -e "1 apple\n2 pear\n3 banana" > text1
     echo -e "9\tplum\n3\tbanana\n10\tapple" > text2
     echo "This is a sentence. " !#:* !#:1->text3
     split -l 2 text1
     split -b 17 text2 y;
     cp text1 text1.bkp
     mkdir -p backup
     cp text1 backup/text1.bkp.2
     }

`grep`
~~~~~~~~

get lines from text 1 with at least 2 p's::

   $ grep "pp\+" text1 # at least two p's
   1 apple

get lines from text1 that start with p, end with e, and have optinally a letter 'l' in between::

   $ grep "pl\?e" text1 # pe with optional l between
   1 apple
   2 pear

get lines that optionally start with 'pl' (instead of just 'l')::

   $ grep "\(pl\)\?" text1 # same but with optional pl
   1 apple
   2 pear
   3 banana

get words that contain zero or more characters between p and r:::

   $ grep "p.*r" text1 # p, some string then r
   2 pear

get words that start with 'a' and that are followed by 2 other characters:::

   $ grep "a.." text1 # a followed by two other letters
   1 apple
   3 banana

 Find at least one 'an'::

   $ grep "\(an\)\+" text1 # find at least 1 an
   3 banana

 Find at least two an's::

   $ grep "an\(an\)\+" text1 # find at least 2 an's
   3 banana

 Find p or 3::

   $ grep "[3p]" text1 # find p or 3

 Get all lines containing word 'banana' from all 4 texts, associated with text number::

   $ grep -n banana text[1-4]
   text1:3:3 banana
   text2:2:3   banana

 get all lines starting with 1 or 2 digits, followed by a blank::

   $ oursearch='^[[:digit:]][[:digit:]]*[[:blank:]]'
   $ grep "$oursearch" text[1-3]
   text1:1 apple
   text1:2 pear
   text1:3 banana
   text2:9 plum
   text2:3 banana
   text2:10    apple

   $ ## same thing using sed:
   $ cat text[1-3] | sed -ne "/$oursearch/p"
   1 apple
   2 pear
   3 banana
   9   plum
   3   banana
   10  apple

`sed`
~~~~~~
To change inplace ugly by beautiful in a file::

  $ sed -i 's/ugly/beautiful/g' ./sue.txt

Create the following text1 and text2 files::

  $ echo -e "1 apple\n2 pear\n3 banana" > text1
  $ echo -e "9\tapple\n3\tpear\n10\tbanana">text2

To delete 2nd line, and replace all 'a' with 'A'::

   $ sed '2d;s/a/A/g' text1
   1 Apple
   3 bAnAnA

To specifiy you only want to modify the 2 last lines:
(2 solutions below)::

   $ sed -e '2,${' -e 's/a/A/g' -e '}' text1
   1 apple
   2 peAr
   3 bAnAnA

   $ sed -e '/pear/,/bana/{' -e 's/a/A/g' -e '}' text1
   1 apple
   2 peAr
   3 bAnAnA

Sed to transform this::

   $ cat text6
   1 apple
   2 pear
   3 banana
   9       apple
   3       pear
   10      banana
   1 apple
   2 pear
   3 banana
   9       apple
   3       pear
   10      banana

into this:
(i.e. add line numbers)::

   1  1 apple
   2  2 pear
   3  3 banana
   4  9       apple
   5  3       pear
   (...)

   $ cat text1 text2 text1 text2 > text6
   $ ht=$(echo -en "\t")
   $ sed '=' text6|sed "N
   > s/^/      /
   > s/^.*\(......\)\n/\1$ht/"

To humanize kbytes from a stream with ``numfmt --to=iec``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Imagine you receive a file with two columns integer and filepath::

  $ cat /tmp/files.txt |sort -n| tail -3
  144876 /usr/lib/firefox/libxul.so
  146412 /usr/lib/slack/slack
  163612 /usr/lib/jvm/java-11-openjdk-amd64/jmods/java.base.jmod

Use numfmt to format in human readable the k integers::

  $ cat /tmp/files.txt |sort -n|tail -3| numfmt --from-unit=1000 --to=iec
  139M /usr/lib/firefox/libxul.so
  140M /usr/lib/slack/slack
  157M /usr/lib/jvm/java-11-openjdk-amd64/jmods/java.base.jmod
  $

.. note::

  This file could have been created by someoen else on some other server with e.g.::

  $ find /usr/lib -type f -printf '%k %p\n' > /tmp/files.txt

Pipelines and redirect stream allow composition `|`,  `>`,  `...`
===================================================================
When using `>` to redirect. if no number is specified, 1 is default (i.e. std
output) recall:

- 1 std output
- 2 = std error
- 3 = std input

Type following commands to create required directory and spaces::

   mkdir -p lpi103-4 && cd lpi103-4 && {
   echo -e "1 apple\n2 pear\n3 banana" > text1
   echo -e "9\tplum\n3\tbanana\n10\tapple" > text2
   echo "This is a sentence. " !#:* !#:1->text3
   split -l 2 text1
   split -b 17 text2 y
   ls; }

   $ ls x* z*
   ls: cannot access z*: No such file or directory
   xaa
   xab

Redirect std error of command to output.txt, i.e. only output will appear on
terminal::

   $ ls x* z* 2>output.txt
   xaa xab

   $ ls x* z* 2>&1 # the & sign tells &1 is the REPOSITORY where stdout is
   ls: cannot access 'z*': No such file or directory
   xaa  xab

   $ ls x* z* 2>1 # no & sign means we are writing ON stdout
   xaa  xab


Redirect std error to location of stdout and then redirect stdout to
output.txt::

  $ mkdir -p /tmp/streams/{a,c}; cd /tmp/stream
  /tmp/streams$

  /tmp/streams$ ls a b c  1> /tmp/out
  ls: impossible d'accéder à 'b': Aucun fichier ou dossier de ce type
  $ cat /tmp/out
  a:

  c:

`2>` redirect error stream::

  $ ls a b c  2> /tmp/out
  a:

  c:
  $ cat /tmp/out
  ls: impossible d'accéder à 'b': Aucun fichier ou dossier de ce type

`&>` redirect both streams::

  $ ls a b c  &> /tmp/out
  $ cat /tmp/out
  ls: impossible d'accéder à 'b': Aucun fichier ou dossier de ce type
  a:

  c:
  $

Redirect streams on real life situation
------------------------------------------
The `>` redirect is in fact `1>` **1** stand for standard output::

    $ sshfs -h > /tmp/log_file.txt

To redirect both error output and standard output stream to a file use `&>`::

    $ sshfs -h &> /tmp/log_file.txt

To joint error and output stream to stdout use `2>&1` (so we can pipe)::

    $ sshfs -h 2>&1 | grep xzy

Makefile
=========

- Make is a build automation tool that automatically builds executable programs and
  libraries from source code by reading a file called ``Makefiles``.
- ``Makefile`` specify how to derive the target program and manage a build process Make
  is widely used in Unix ecosystems.
- Besides building programs, Make can be used to manage any project where some files
  must be updated automatically from others whenever the others change.

A simple makefile consists of “rules” with the following shape::

  target <target_name> : <prerequisites>
          recipe

- Gnu documentation: https://www.gnu.org/software/make/manual/html_node/File-Name-Functions.html

Makefile exemple
-----------------
``Makefile`` that call ``mmdc`` on every file with ``.mmd`` (mermaid) extention to
create a ``png`` file:

.. code::

   $ echo Makefile
   MMD_TARGETS:= $(patsubst %.mmd,%.png,$(wildcard *.mmd))
   png: $(MMD_TARGETS)

   %.png: %.mmd
    mkdir -p _build
    @mmdc -i $< -o _build/$@ -s 4
    @echo _build/$@

The above ``Makefile`` do the following:

- put in ``$(MMD_TARGETS)`` variable as many ``.png`` files there are ``*.mmd`` files
- the job ``png:`` request that all this ``.png`` files exist
- make looks for a rule to convert  ``.mmd`` into ``.png``, it found it ``%.png: %.mmd``
  and execute it, after having created a ``_build`` folder

.. code:: bash

  $ tree
  ├── itasm.mmd
  ├── itasm_workflow.mmd
  └── Makefile
  $ make png
  ...
  $
  $ tree
  ├── _build
  │   ├── itasm.png
  │   └── itasm_workflow.png
  ├── itasm.mmd
  ├── itasm_workflow.mmd
  └── Makefile


Unix workworse: `find` + looping
==================================

`find`
-------
The find command line is very powerful for managing your files, you can
obviously find specific files according to defined conditions but you can also launch
automatic process on found files or directories

:`-name`: search by the name of the file
:`-type`: search by the type (d=directory, c=character, f=file)
:`-size`: search by the block size (1 block=512octets)
:`-atime`: search by the last read acces date
:`-mtime`: search by the last modification date
:`-ctime`: search by the creation date

Logical operations for options:

- `-a` : corresponds to the logical AND & the default
- `-o` : correspondts to the logical OR |

Example of find command :

.. code:: bash

    find . -name "*.rst" -mtime -1

This find command line will look for all rst files that have been modified today.

Find files older than `2013-11-10`::

  find . ! -newermt "2013-11-10" | grep Shang | grep -vE 'mario|teau|Musi'
  find . -newermt "2012-12-01" ! -newermt "2013-03-01" | grep txt

Exec action on `find` results::

  (venv-dev) fox@akd6:~/.../hedonique$ find . -name "*rules" -exec ls -alt {} \;

  -rw-r--r-- 1 fox fox 1506 May  8 21:54 ./us2/us_attr25.rules
  -rw-r--r-- 1 fox fox 941 May  8 23:20 ./both2/both_attr25.rules
  -rw-r--r-- 1 fox fox 1718 May  8 14:23 ./both2/both_attr25_res_antoine.rules
  -rw-r--r-- 1 fox fox 116029 May  7 22:06 ./fr/Rules_BOTH_ddsearch_0.5_43_Ingredients.rules
  -rw-r--r-- 1 fox fox 116029 May  7 22:06 ./fr/Rules_BOTH_ddsearch_23_Ingredients.rules
  -rw-r--r-- 1 fox fox 1069 May  9 00:19 ./fr/fr_attr25.rules
  -rw-r--r-- 1 fox fox 2945 May  7 16:38 ./trash/both/Luis_selected_Rules_23.rules
  -rw-r--r-- 1 fox fox 43871 May  7 15:51 ./trash/both/Rules_BOTH_ddsearch_23_Ingredients.rules
  -rw-r--r-- 1 fox fox 1853 May  7 15:53 ./trash/both/high_lift_selected_Rules_BOTH_ddsearch_24_Ingredients.rules

exclude a folder from search e.g. `.venv`::

  find . -path ./.venv -prune -o -name '__init__.py'

find python files on all sub-folders at the exception of './test/'::

  find . -name '*.py' -not -path '*/test

count json file larger than 8 Ko (8 * 1024 bytes) ::

  $ find . -size +8k -name '*.json' -printf '%k %p\n' | sort -rn | wc -l
  7435

find more recent files using a `-printf FORMAT`::

  $ find ./main -name '*.pptx' -type f -printf "%T+ %p\n"| sort
  2018-07-20+17:14:19.1060106780 ./main/cv_luis_en.pptx
  2018-07-25+17:14:19.5884579030 ./main/180721_nissan_credential_v2.1.pptx
  2018-09-13+11:08:31.8518450230 ./main/bb.pptx
  2018-09-21+18:40:21.5746639250 ./main/a.pptx
  2018-09-21+18:41:25.5506795890 ./main/orange.pptx
  2018-09-30+17:40:54.6810545310 ./main/panorama_outils_audit.pptx
  2018-10-02+10:54:24.6840314980 ./main/zettafox_audit.pptx
  (venv) luis@spinoza:~/projets/sujets$

Not bad, but if we want to remove the msec like `.6840314980` we can use `awk
-F'SEPARATOR'` to split columns with '.'::

  $ find ./main -name '*.pptx' -type f -printf "%T+ %p\n"|\
          awk -F'\\.' '{print $1 " " $3}'|\
          sort -n
  2018-07-20+17:14:19 /main/cv_luis_en
  2018-07-25+17:14:19 /main/180721_nissan_credential_v2
  2018-09-13+11:08:31 /main/bb
  2018-09-21+18:40:21 /main/a
  2018-09-21+18:41:25 /main/orange
  2018-09-30+17:40:54 /main/panorama_outils_audit
  2018-10-02+10:54:24 /main/zettafox_audit
  $

Note: to escape the dot we use backslash to escape backslash we need a second
backslash.

make it a bash function (in `~.bashrc`)::

  function last_pptx() {
    find ./$1 -name '*.pptx' -type f -printf "%T+ %p\n"|\
          awk -F'\\.' '{print $1 " " $3}'|\
          sort -n
  }

Date in conroled format::

  $ date +%F_%Hh%Mm%Ss
  2018-11-16_10h55m35s
  $
  $ date +%F+%H:%M:%S
  2018-11-16+10:56:51
  $

To get only folders excluding some of them `2018`, `S1` and `S2`::

  find . \( -path './2018*' -o -path "./S*" \) -prune\
           -o -type d -print
  ./git_wc
  ./budget
  ./budget/mail_0625
  ./budget/achats
  ./rh
  ...

`\(` and `\)` group the -path XZY -o -path TUV, `-o` is the logical OR

Note this specific case can be done with `tree`::

  $ tree -d -L 2 -I 'S1|2018' -fi
  ./git_wc
  ./budget
  ./budget/mail_0625
  ./budget/achats
  ./rh
  ...

:Note: more about the find cmd: https://www.booleanworld.com/guide-linux-find-command/
:Note: for a very good case on find: https://unix.stackexchange.com/a/102203/254303

rename f.txt to f.cob massively
---------------------------------
::

  $ export my_mv(i) {echo $i; mv $i ${i%.txt}.cob ;done}
  $ find . -name 'copy_*.txt' |while read i ;do my_mv($i) ;done

`while read i; do echo $i; done` < /tmp/out
--------------------------------------------
Real life will be more like::

  find . -size +50M -name '*.csv' | while read i ;do DO_STUFF_WITH_$i ;done

If we want to get sorted python files by number of lines::

  $ count_lines() { printf '%s#lines:%s %s\n' `wc -l<"$1"`{,} $1 ;}

  $ find . -name '*.py' | while read i ;do count_lines $i; done | sort -n | awk -F'#' '{print $2}'
  lines:0 ./lpm/__init__.py
  lines:0 ./tests/__init__.py
  lines:16 ./setup.py
  lines:34 ./lpm/feature.py
  lines:55 ./lpm/data/geodata.py
  lines:55 ./tests/utils_test.py
  lines:114 ./lpm/reador1.py

To flush right numbers replace `%s` by `%4s`::

  $ count_lines() { printf '%s#lines:%4s %s\n' `wc -l<"$1"`{,} $1 ;}

  $ find . -name '*.py' | while read i ;do count_lines $i; done | sort -n | awk -F'#' '{print $2}'
  lines:   0 ./lpm/__init__.py
  lines:   0 ./tests/__init__.py
  lines:  16 ./setup.py
  lines:  34 ./lpm/feature.py
  lines:  55 ./lpm/data/geodata.py
  lines:  55 ./tests/utils_test.py
  lines: 114 ./lpm/reador1.py
  $

Top Pattern: call a function from while find loop::

  $ stuff() { printf 'name: %s::%s\n' $1 `wc -l $1` ;}
  $
  $ find . -size +50M -name '*.csv' | while read i ;do stuff $i; done
  name: ./data/05082019/AllReponses2019_bis.csv::1449447
  name: ./data/05082019/AllReponses2019_bis.csv::
  name: ./data/05082019/AllResponse2019.csv::1449447
  name: ./data/05082019/AllResponse2019.csv::
  name: ./data/RespondentsTestZeta.csv::1048576
  name: ./data/RespondentsTestZeta.csv::
  $

Notice the use of printf::

  printf 'name: %s::%s\n' $1 `wc -l $1`
  printf 'string %s with %s slots' string1  string2  # because two %s in string

like in old Python::

  >>> "{} {}".format(a, b)   #  with old Python
  >>> f"{a} {b}"             #  with modern Python with


avantage of **while read i** over **for i in**
----------------------------------------------
Let's play with files with spaces in name::

  $ touch "bonjour les amis.odt"
  $ ls
  fdssdf.odt
  blockchain.odt
  bonjour les amis.odt
  hello.odt
  $

spaces in filename are messy with ``for i in``::

  $ for i in `ls *.odt`; do printf "$i \n"; done
  fdssdf.odt
  blockchain.odt
  bonjour                   # bad
  les                       # bad
  amis.odt                  # bad
  hello.odt
  $

It is better to use while::

  $ ls *.odt | while read i ;do echo $i ; done
  fdssdf.odt
  blockchain.odt
  bonjour les amis.odt
  hello.odt
  $

Looping with `xargs` `for i in ` and `while read i`
---------------------------------------------------

`cut printf and xargs`
~~~~~~~~~~~~~~~~~~~~~~~~
(Using Output as Arguments)

Get all Exited docker container id and and use the ids to remove them::

  $ docker ps -a
  71207dc9ca37  smizy/apache-drill:1.16.0-alpine    "entrypoint.sh drill…"     Exited (143) 2 months ago  drillbit-1
  239cf7fba4d1  mongo:latest                        "docker-entrypoint.s…"     Exited (0) 2 months ago    mongodb
  47a51cc4a814  smizy/zookeeper:3.4-alpine          "entrypoint.sh -serv…"     Exited (143) 2 months ago  zookeeper-1
  $
  $ docker ps -a | grep Exit | cut -d' ' -f1
  71207dc9ca37
  239cf7fba4d1
  47a51cc4a814
  $ docker ps -a | grep Exit | cut -d' ' -f1 | xargs docker rm

  $ in case it's more complexe the pattern with `while read` is better
  $ docker ps -a | grep Exit | cut -d' ' -f1 |while read i; do docker rm "$i"; done

Get all workers configured on a Celery server::

  $ grep "\-Q" /etc/supervisor/conf.d/*
  /etc/supervisor/conf.d/anablue_lazy_table_injection_fr_preprod.conf:command=/opt/anablue_worker_fr_preprod/bin/celery --app=anablue_api.app.celery worker -Ofair --autoscale=4,1 --loglevel INFO -Q lazy_table_injection -n lazytable@%%h
  /etc/supervisor/conf.d/anablue_worker_big_jobs_fr_preprod.conf:command=/opt/anablue_worker_fr_preprod/bin/celery --app=anablue_api.app.celery worker -Ofair --autoscale=2,1 --loglevel INFO -Q big_jobs_few_tasks -n bigjobs@%%h
  /etc/supervisor/conf.d/anablue_worker_small_jobs_fr_preprod.conf:command=/opt/anablue_worker_fr_preprod/bin/celery --app=anablue_api.app.celery worker -Ofair --autoscale=10,1 --loglevel INFO -Q default,small_jobs_many_tasks --beat -n smalljobs@%%h
  $

`cut -f5-` from 5th column to the last::

  $ grep "\-Q" /etc/supervisor/conf.d/*| cut -f5- -d ' '
  --autoscale=4,1 --loglevel INFO -Q lazy_table_injection -n lazytable@%%h
  --autoscale=2,1 --loglevel INFO -Q big_jobs_few_tasks -n bigjobs@%%h
  --autoscale=10,1 --loglevel INFO -Q default,small_jobs_many_tasks --beat -n smalljobs@%%h
  $

`printf "%-18s %s", var1, var2` to align left formated output::

  $ grep "\-Q" /etc/supervisor/conf.d/*| cut -f5- -d ' '| awk '{printf "%-18s %s\n", $1, $5}'
  --autoscale=4,1    lazy_table_injection
  --autoscale=2,1    big_jobs_few_tasks
  --autoscale=10,1   default,small_jobs_many_tasks
  $




Use case: size a folder and diet csv to csv.gz
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Main tools `du` and `find`::

  $ du -sh .
  245M    .
  $ du -sh .git
  116M    .git
  $

  $ find ./ -size +1M -name '*.csv' | xargs ls -lh

The best tools for this `find`::

  $ find .git -type f -printf '%k %p\n' | sort -n | tail

Think to use ncdu::

  $ ncdu

Get how much Mb we have with csv > 1M::

  $ find ./ -size +1M -name '*.csv' | xargs ls -l |
         awk '{print $5}{s+=$5}END{print s/1024/1024}'
  ...
  1576810
  99.9094
  $

find large csv gited, gzip them, git update::

  $ find ./ -size +1M -name '*.csv' -exec pigz -f -k {} \;
  $ find ./ -size +1M -name '*.csv' -exec git rm {} \;
  $ find ./ -size +1M -name '*.csv.gz' -exec git add {} \;
  $ git commit -am 'replace .csv bigger than 1M by csv.gz'

The above is good to lower the working copy size but did not lower the `.git`
size for that you need to change history::

  $ du -sh .git
  143M  .git
  $

`while read`
~~~~~~~~~~~~~~
`while read` is more solid in case you have spaces or new lines on strings you
manipulate.
It's our favorit pattern.

Look for iterrow in a pandas code repo::

  $ git grep iterro
  pkg/aaa/files/credit_stock.py:        for index, row in input_df.iterrows():
  pkg/aaa/files/mca_currencies.py:        for index, row in params_df.iterrows():
  pkg/aaa/s_invest/m01/utils.py:    for index, move in movements.iterrows():
  pkg/aaa/s_invest/m01/utils.py:                for row_index, element in inner_df.iterrows():
  $

  $ ## get list of file that contains `iterrow`:
  $ git grep iterro | cut -d ':' -f1 |sort |uniq
  pkg/aaa/files/credit_stock.py
  pkg/aaa/files/mca_currencies.py
  pkg/aaa/s_invest/m01/utils.py

  $ ## loop on it to `git blame` and get the commiter::
  $ git grep iterro | cut -d ':' -f1 |sort |uniq | \
    while read i; do echo '  =>' $i; git blame $i |grep  iterrow;done

  ==> pkg/aaa/files/credit_stock.py
  9d61b36014 (Daniel   2020-12-01 15:21:28 +0100 132)         for index, row in input_df.iterrows():
  ==> pkg/aaa/files/mca_currencies.py
  7772df4160 (Daniel 2020-11-23 14:47:35 +0100 64)         for index, row in params_df.iterrows():
  ==> pkg/aaa/s_invest/m01/utils.py
  bddb79e579 pkg/invest/modules/m01/utils.py (Arkadiusz Klein     2019-06-10 15:04:58 +0200 116)     for index, move in movements.iterrows():
  180dea3a72 pkg/aaa/s_invest/m01/utils.py   (Arek                2020-04-23 09:51:47 +0200 169)                 for row_index, element in inner_df.iterrows():
  $

Practical work: Identifying perfect duplicates inside raw data files
-----------------------------------------------------------------------
.. code:: bash

  $ ls *.csv.gz
  customer.csv.gz  LIGNEREMISE_TRANSACTION.csv.gz  LIGNE_TRANSFERT.csv.gz  PIECE_TRANSACTION.csv.gz  STORE.csv.gz
  ITEM.csv.gz      LIGNE_TRANSACTION.csv.gz        PAIEMENT.csv.gz         PIECE_TRANSFERT.csv.gz

.. code:: bash

  $ ls *.csv.gz | while read i;
  do
  zcat "$i" |sort |uniq -c |sort -nr |awk '($1 > 1) {print $0}' > "$i"."DUPLICATES"
  done

  $ ls *.DUPLICATES
  -rw-rw-r-- 1 fox fox    0 oct.   3 16:58 customer.csv.gz.DUPLICATES
  -rw-rw-r-- 1 fox fox    0 oct.   3 16:58 ITEM.csv.gz.DUPLICATES
  -rw-rw-r-- 1 fox fox 210K oct.   3 16:58 LIGNEREMISE_TRANSACTION.csv.gz.DUPLICATES
  -rw-rw-r-- 1 fox fox 401K oct.   3 16:58 LIGNE_TRANSACTION.csv.gz.DUPLICATES
  -rw-rw-r-- 1 fox fox  61K oct.   3 16:58 LIGNE_TRANSFERT.csv.gz.DUPLICATES
  -rw-rw-r-- 1 fox fox  27K oct.   3 16:59 PAIEMENT.csv.gz.DUPLICATES
  -rw-rw-r-- 1 fox fox    0 oct.   3 16:59 PIECE_TRANSACTION.csv.gz.DUPLICATES
  -rw-rw-r-- 1 fox fox    0 oct.   3 16:59 PIECE_TRANSFERT.csv.gz.DUPLICATES
  -rw-rw-r-- 1 fox fox    0 oct.   3 16:59 STORE.csv.gz.DUPLICATES

If you have files with 0 Ko, you don't have DUPLICATES inside your file.

If you don't have 0 Ko, you do have DUPLICATES.

You also want to know later how many duplicates in total you have in your file.

With those \*.DUPLICATES files, just SUM the first column

.. code:: bash

        $ ls *.DUPLICATES |while read i;
        do
        awk '{SUM+=$1} END {print FILENAME "\t" SUM-NR}' "$i";
        done

        customer.csv.gz.DUPLICATES
        ITEM.csv.gz.DUPLICATES
        LIGNEREMISE_TRANSACTION.csv.gz.DUPLICATES	6999
        LIGNE_TRANSACTION.csv.gz.DUPLICATES	10359
        LIGNE_TRANSFERT.csv.gz.DUPLICATES	2678
        PAIEMENT.csv.gz.DUPLICATES	789
        PIECE_TRANSACTION.csv.gz.DUPLICATES
        PIECE_TRANSFERT.csv.gz.DUPLICATES
        STORE.csv.gz.DUPLICATES

CAUTION

beware that for files without duplicates, this will add a tab "\t" character
just after the filename in the output


Unix Tools to process `pdf`, `xlsx` and  `images`
====================================================

pdf manipulation
-----------------
Install texlive-extra-utils::

  $ sudo apt-get install texlive-extra-utils
  $ pdfjoin a.pdf b.pdf c.pdf -o out.pdf

xlsx to csv
-------------
Sometimes, you may be facing a large xlsx file (e.g. 500 M), so it
will not open with libreoffice on your laptop.
So you will need to analyze it on akd6, but there is no graphic interface,
so you will need to convert it to csv.

a way to do it is to use ssconvert (comes with gnumeric pkg)::

  $ sudo apt-get install gnumeric

  $ ssconvert file_a.xlsx file_a.csv

If the xlsx file has several tabs, proceed that way::

  $ ssconvert -S 'file_a.xlsx' 'file_a.csv'

there will be as many csvs (each numbered) created as there are
tabs in the xlsx file


Images manipulation with imagemagic
------------------------------------

Use mogrify and identify to play with images
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
``apt-get install imagemagick``::

  identify kn01.jpeg
  mogrify -resize 200x3000 kn01.jpeg

http://debian-facile.org/doc:media:imagemagick

Add 5 px purple border to images
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
::

  convert -bordercolor purple -border 5 image_in.png image_out.png

`montage` Command is designed to produce an array of thumbnail images
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
::

  $ montage -geometry 640x+0+0 i*.png out.png

- here 640 is the size of each image

Use `-tile` to shape the montage::

  $ montage -tile 2x5 -geometry 640x+0+0 i*.png out.png



Mount scp remote connexion with ``sshfs``
=========================================
install::

  $ sudo apt-get install sshfs

mount::

  $ mkdir /home/luis/mysftp
  $ sshfs log_r_audit@sftp2.mazars.fr: /home/luis/mysftp


Data Compression
=================
first let's create a file with fake data::

  $ fallocate -l 90M data.csv
  $ ll data.csv
  -rw-rw-r-- 1 luis luis 90M sept.  1 20:12 data.csv
  $

Parallel Implementation of GZip (This is the recomended to use, let's go ``.csv.gz``)

compress::

  $ pigz data.csv
  $ ls data.csv*
  data.csv.gz
  $

de-compress::

  $ pigz -d data.csv.gz
  $ ls data.csv*
  data.csv

7zip very slow to compress, fast to uncompress::

  $ p7zip data.csv
  $ ls -l data.*
  -rw-rw-r-- 1 luis luis 101K sept.  1 20:12 data.img.gz
  $


Powerfull terminals: `Terminator`, `screen` and `tmux`
========================================================
Terminator
-----------
Provide **split window** a much better pattern than multiples tabs.

Install it::

  $ sudo apt-get install terminator


:Ctrl-Maj x: Toogle fullscreen
:Ctrl-Maj e: add panel to the right
:Ctrl-Maj o: add panel at the bottom
:Ctrl-Maj w: remove panel
:Alt+<Arrow>: Move focus

Multiplexes a physical terminal with  ``tmux`` and ``screen``
--------------------------------------------------------------

(TO BE DONE)


Locate duplicate files with `jdupes`
--------------------------------------
Locate the all duplicates files bigger than 10M::

  $ sudo apt-get install jdupes
  $ time jdupes -S -X size-:10M -r ~/ -M > ~/jdupes_10M.txt

Vacume `/var/log/journal`
--------------------------
Removes the oldest archived journal files until the disk space they use falls below the specified size::

  $ du -sh /var/log/journal/
  1.4G	/var/log/journal/
  $ sudo journalctl --vacuum-size=200M
  ...
  Vacuuming done, freed 1.2G of archived journals from /var/log/journal/4334...8c87.
  $ du -sh /var/log/journal/
  233M	/var/log/journal/

Exercises
===========
As always, your code should be committed in a separate file in the
fox_dojo directory of your training repository.

We will use the directory sphinx/source for our Unix exercises.

.. code:: python

    cd sphinx/

Exercices :

- 1. Find all files containing "Python" in their name in knowledge_data_advisory/sphinx/source.
- 2. Find python files that have been created within the last 5 days.
- 3. Find the three biggest .rst files in fox_dojo and return their 5 first lines.
- 4. Find the .rst files containing the word "Vim".
- 5. Show all the file names and their size in present directory.
- 6. Print all the line of a file withe the lines number.
- 7. Print only the first word of each line of a file.
- 8. Print all the name of the student and their average results.

.. code:: python

    BOBY                  18 5
    ZELYNOU               6 11
    ANTIN             8 4
    BOB              16 8 15
    IZEL              16 18 12

- 9. Print all the lines containing the character "to" in your file (or other character).
- 10. List the files containing the string "Vim" in fox_dojo/sphinx/source
- 11. Count the number of occurence of this string in this directory
- 12. List all the files that doesn't contains this string.
- 13. Show columns 3 to last on any file.
- 14. Print all the .rst and their size, sorted by decreasing size order, in .csv format
- 15. Print the sum of the sizes of the .rst files in your folder
- 16. Go to fox_dojo git folder and open pactiv.log
      You will see something like this :

.. code:: python

    ^[[32mlabor_mix-nameko-prod-2    |^[[0m Data v23 made in 1.057941198348999 seconds
    ^[[32mlabor_mix-nameko-prod-2    |^[[0m Data v23 made in 0.8878018856048584 seconds
    ^[[32mlabor_mix-nameko-prod-2    |^[[0m Data v24_FG made in 1.0906145572662354 seconds
    ^[[32mlabor_mix-nameko-prod-2    |^[[0m Data v24_FG made in 2.0634255409240723 seconds
    ^[[32mlabor_mix-nameko-prod-2    |^[[0m Data v25_Overtimehourspercent made in 1.0764472484588623 seconds
    ^[[32mlabor_mix-nameko-prod-2    |^[[0m Data v25_Overtimehourspercent made in 1.0128099918365479 seconds
    ^[[32mlabor_mix-nameko-prod-2    |^[[0m Data v25_Overtimehourspercent made in 1.4184410572052002 seconds
    ^[[32mlabor_mix-nameko-prod-2    |^[[0m Data v31 made in 1.245509147644043 seconds
    ^[[32mlabor_mix-nameko-prod-2    |^[[0m Data v31 made in 1.0590665340423584 seconds
    ^[[32mlabor_mix-nameko-prod-2    |^[[0m Data v32 made in 0.49026966094970703 seconds
    ^[[32mlabor_mix-nameko-prod-2    |^[[0m Data v32 made in 0.4227783679962158 seconds
    ^[[32mlabor_mix-nameko-prod-2    |^[[0m Data v32 made in 0.5403151512145996 seconds


Create a file sort.txt which list all "Data vN" and the average time each of them are made.


Shell process question:

- 17. Display the following information for the current shell:
  pid, ppid and cmd

Sorting text, and removing duplicates::

  Create the following text1 and text2 files:
  echo -e "1 apple\n2 pear\n3 banana" > text1
  echo -e "9\tapple\n3\tpear\n10\tbanana">text2

- 18. Concatenate, align and sort the rows by their first character,
  character-wise (not numeric wise, i.e. it should only consider the 1st (left)
  character of 2 digit numbers if there are any)

- 19. Concatenate, align and sort the rows by both their first character
  numeric-wise (2 digit numbers will be fully considered) and by their 2nd
  character character-wise (in this case it's a letter so it's easier than in
  the last question).
  Then, remove duplicates.

- 20. Concatenate, align and sort the rows by their second character,
  character-wise, then remove ducplicates using uniq.

Cut, paste:

- 21. Remove the tabs from each line in text2 using cut

- 22. Paste text1 and text2

More on find::

  Create the following files:
  echo -e "c1,c2\n1,2\n2,3" > data1.csv
  echo -e "c1,c2\n1,2\n2,3\n3,3" > data2.csv
  echo -e "not a csv," > not_a_csv

- 23. Transform csv files into tsv files with a find & while read command (do not forget to rename the '.csv' files into '.tsv')

- 24. Get the number of lines of each new .tsv file

Solutions of the Exercises:

- 1. Find all files containing "Python" in their name in
  fox_dojo/sphinx/source

.. code:: bash

        $ find . -name "*Python*"

- 2. Find python files that have been created within the last 5 days

.. code:: bash

        $ find . -name "*.py" -mtime -5

- 3. Find the 3 biggest .rst files in fox_dojo and return their 5 first lines

.. code:: bash

       $ find . -name "*.rst" -exec du -s {} \; | sort -hr | head -3 | while read i; do head -5 $i; done

- 4.  Find the .rst files containing the word "Vim"

.. code:: bash

       $ grep -rl "Vim" --include="*rst" # or
       $ find . -name "*.rst" | grep -rl "vim"

- 5. Select all files in current working directory and size

.. code:: bash

       $ ls -s #gives the size in blocks

- 6. Display all lines of a file with line number

.. code:: bash

       $ cat -b README.rst

- 7. Print only the first word of each line of a file

.. code:: bash

       $ awk '{print $1}' README.rst

- 8. Print the name of all students and their average results

.. code:: bash

       $ awk '{tot=0; for (i=1; i<=NF; i++) tot += $i; print $1, ':', tot/(NF-1); }' student_data.rst


- 9. Print all lines containing the character "to" in your file

.. code:: bash

       $ grep -n 'to' README.rst

- 10. List all the files containing the string 'Vim' in
  fox_dojo/sphinx/source

.. code:: bash

       $ # do, when in the right directory:
       $ grep -l Vim *.*

- 11. Count number of occurence of 'Vim' in this directory

.. code:: bash

       $ grep -o Vim *.* | wc -l

- 12. List all the files that do not contain this string

.. code:: bash

       $ grep -vrl Vim *.*

- 13. Show column 3 to to last on any file

.. code:: bash

       $ awk '{for (i=3; i<=NF; i++) print $i}' any_file

- 14. Print all the .rst and their size, sorted by decreasing size order, in .csv format

.. code:: bash

       $ find . -name "*.rst" -printf '%k %p\n' | sort -n | awk '{print $1 ";" $2}'
       # BEGIN{print"Size;Path"} in awk adds the header

- 15. Print the sum of the sizes of the .rst files in your folder

.. code:: bash

       $ find . -name "*.rst" -printf '%k %p\n' | awk '{s+=$1}END{print s}'

- 16. List all "Data vN" and the average time each
  of them are made

.. code:: bash

       $ grep -r 'seconds' pactiv.log | awk '{print $4, $7}' | awk 'NF==2 {sum[$1] += $2;
         N[$1]++} END {for (key in sum) {avg = sum[key]/N[key]; printf "%s%f\n", key,
         avg;}}'

- 17. Display the following information for the current shell:
  pid, ppid and cmd

.. code:: bash

       $ ps -p $$ -o "pid ppid cmd"

  notes: ps displays info about a process, -p tells that we want to know
  about the current shell process, $$ is en environment variable that
  contains the PID of the current process, -o says that we want to tell
  which process infomation we want, which we ask between quotes right
  after that parameter: "pid ppid and cmd".

- 18. Concatenate, align and sort the rows by their first character,
  character-wise (not numeric wise, i.e. it should only consider the 1st (left)
  character of 2 digit numbers if there are any)

.. code:: bash

     $ cat text1 | tr ' ' '\t' | sort - text2

  Why: the **tr** part will translate spaces in text1 with tabs (\t), which
  will allow the concatenation to be aligned with text2 when we add it in the
  next pipe.
  The sort is by default character-wise in the first character. Note: because
  it is character-wise, '10' will appear on top, as sort does not see it as an
  entire numeric value, but only sorts by the 1st left character which is 1.

- 19. Concatenate, align and sort the rows by both their first character
  numeric-wise (2 digit numbers will be fully considered) and by their 2nd
  character character-wise (in this case it's a letter so it's easier than in
  the last question).
  Then, remove duplicates.

.. code:: bash

    $ cat text1|tr ' ' '\t'| sort -u -k1n -k2 - text2

  Why: regarding the alignment, same as last question.
  Regarding the sorting, -k1n says that you sort by 1st character
  numeric-wise, and -k2 says you sort by 2nd character character-wise.
  -u is what allows you to eliminate duplicates.

- 20. Concatenate, align and sort the rows by their second character,
  character-wise, then remove ducplicates using uniq.

.. code:: bash

     $ cat text1|tr ' ' '\t'| sort -k2 - text2|uniq -f1


- 23.

.. code:: bash

     $ find . -name "*.csv"| while read i; sed -i 's/,/\t/g' $i; do mv "$i" "$(echo "$i" | sed s/csv/tsv/)"; done

An alternative more bashy solution:

.. code:: bash

     $ find . -name "*.csv"| while read i; sed -i 's/,/\t/g' $i; do mv "$i" "${i%.*}.tsv"; done


- 24.

.. code:: bash

     $ find . -name "*.tsv" | while read i;do wc -l $i; done

  Why: regarding alignment and sort: same as before. **uniq** allows you to
  remove consecutive identical lines. -f1 tells you keep the first duplicate
  line and remove the second one.

- 21. Remove the tabs from each line in text2 using cut

.. code:: bash

     $ cut -c 1- --output-delimiter="" text2 > text2_without_tabs

- 22. Paste text1 and text2

.. code:: bash

     $ paste -s text1 text2

  Why: the -s option (for *--serial*) tells *paste* to paste files one at a
  time. The default behaviour is a parallel pasting which would result in mixed
  texts.


