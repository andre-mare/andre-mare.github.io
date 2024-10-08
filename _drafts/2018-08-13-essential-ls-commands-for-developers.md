---
layout: post
title: "Essential ls commands for developers"
author: andre
categories: [ bash ]
tags: [bash, ls, terminal]
image: /assets/images/feature-images/feature-image-bash.jpg
description: This post provides a quick reference to the ls commands that I use on macOS. 
---

- Table of Contents
{:toc .large-only}

The Linux operating system contains a number of basic commands to help you navigate the file system. Probably one of the very first commands you will learn and use is the `ls` command. The `ls` command is used to list directory contents.

There are a number of different options and operands that can be used with the `ls` command. Depending on the options and operands, the output and display of contents of a directory will vary.

## Frequently Used Commands
The following is a set of all the frequently used `ls` commands in Linux.
```bash
ls          # List the contents of the current directory.
ls /bin     # List the contents of the bin directory under the root directory '/'.
ls dir1/    # List the contents of the dir1 directory under the current directory.

ls -a       # List contents including those that are hidden. 
ls -A       # List contents including those that are hidden, except for the . and .. 

ls -l       # List contents in a long format with a total sum for all the file sizes one first line.
ls -lh      # List contents in long form, but use unit suffixes: Byte, Kilobyte, Megabyte, etc.. to reduce digits.

ls -F       # List contents and display '/' for directory, '*' for executables, '@' for symbolic link, '=' for socket

ls -r       # List contents in reverse order.
ls -R       # List contents and subdirectories recursively.

ls -t       # List contents sorted by time modified (most recent modified first).
ls -i       # List contents and the file's file serial number (inode number).

ls -ltr     # List contents in long format with most recent time modification last.

ls -lSh     # List contents with file size in order with size suffixes.

ls -F /bin  # List contents of 'bin' directory and display '/' for directory, '*' for executables, '@' for symbolic link, '=' for socket
```


## Examples:
The following is a list of the most basic `ls` command options and operands that are frequently used.


### Example 1. List Current Directory Contents
The `ls` command without any options or operands will list the contents of the current directory.
**Command:**
```bash
$ ls
```

### Example 2. List Directory Contents
To list the contents of any directory anywhere on the filesystem agnostic from the current directory, you need to specify the absolute path of the directory as an operand for the `ls` command. The absolute path is the complete path starting from the root directory (/). 

The `ls` command with the directory name called '/bin' as the operand, displays the content of the 'bin' directory. The '/bin' directory is a standard sub-directory of the root directory and contains the essential binary files for booting and shells like bash.
**Command:**
```bash
$ ls /bin
```

### Example 3. List Sub-directory Contents
To list the contents of the a sub-directory of the current working directory, you need to specify the relative path of the directory as an operand of for the `ls` command.

The `ls` command with the directory name called 'dir1/' as the operand, displays the content of a sub-directory called 'dir1' from the current directory. If the sub-directory is not found within the current directory, the `ls` command will display an error saying "No such file or directory".
**Command:**
```bash
$ ls dir1/
```
 
### Example 4. List Hidden Content
In Linux operating systems, any file or directory that starts with a dot '.' character, will be treated as hidden. The `ls` command does not display hidden files or directories unless the -a flag / option is used.
**Command:**
```bash
$ ls -a
```

### Example 5. List Hidden Content, Except . and ..
The behavior of the flag/option '-A' where the 'A' is capitalized, is the same as using the flag/option '-a' with a lower case 'a', except that the current directory '.' and parent directory '..' is not listed.
**Command:**
```bash
$ ls -A
```

### Example 6. List Content In Detail
The `ls` command by default only displays the name of the files and directories. To display more detailed information about the file and directory content, the '-l' option is used with the `ls` command. This will list the content in the long format. The command displays the permission, user, group, size, timestamp and name of all the entries that match the listing criteria. A total sum for all the file sizes is output on a line before the long listing.
**Command:**
```bash
$ ls -l
```

### Example 7. List Content and File Size in Units
The ls command with the option '-l' displays detailed information about the files and directories including the size. The '-h' option used with the '-l' option, use unit suffixes: Byte, Kilobyte, Megabyte, Gigabyte, Terabyte and Petabyte in order to reduce the number of digits to three or less using base 2 for sizes.
**Command:**
```bash
$ ls -lh
```

### Example 8. List Directory Content Types
The ls command by default only list the names of files and directories and it can be very difficult to differentiate between the different types of files and directories. The '-F' option displays a slash (`/') immediately after each pathname that is a directory, an asterisk (`*') after each that is executable, an at sign (`@') after each symbolic link, an equals sign (`=') after each socket, a percent sign (`%') after each whiteout, and a vertical bar (`|') after each that is a FIFO.
**Command:**
```bash
$ ls -F
```

### Example 9. List Content In Reverse Order
The ls command by default list the content of the directory in lexicographical order (generalization of alphabetical order). It is possible to reverse the lexicographical order by making use of the '-r' option as part of the command. If the '-r' option is used with other options like '-t' or '-S', it will reverse the order of the sort to get reverse lexicographical order or the oldest entries first or largest files last.
**Command:**
```bash
$ ls -r
```

### Example 10. List Content Including Sub-Directories
The ls command by default only list the content of the current directory. Any subdirectories within the current directory will be listed, but their content will not be listed. The '-R' option will recursively list the sub-directories encountered.
**Command:**
```bash
$ ls -R
```

### Example 11. Sort Contents By Date/Time.
To sort the content of a directory based on modified time, the '-t- option is added to the ls command. This will sort the output by time modified (most recently modified first) before sorting the content by lexicographical order.
**Command:**
```bash
$ ls -t
```

### Example 12. List inode Information
An inode is a data structure that describes a filesystem object such as a file or directory. Each inode stores the attributes and disk block locations of the file or directory. Attributes include metadata like times of last change, access, modification as well as owner and permission data. To list the inode number of a directory, the '-i' option is added to the command. 
**Command:**
```bash
$ ls -i
```

### Example 13. List Detail Content Sorted By Time In Reverse
By combining a number of options, it is possible to list the content of a directory in detail (long format) and sort the entries by modification date (latest first) in reverse order (latest modification last).
**Command:**
```bash
$ ls -ltr
```

### Example 14. List Detail Content Sorted By Size (B, K, M, etc.)
To list the content of a directory in detail and sort it according to size, more than one option should be used as part of the ls command. The '-l' option will list the content in detail, the '-S' option will sort according to size and the '-h' option will use unit suffixes for bytes, kilobytes, etc..
**Command:**
```bash
$ ls -lSh
```

### Example 15. List Content Types in Directory
The different options and operands can be combined in a single command to perform various tasks. The '-F' option will indicate the type of entry (directory, executable, pipe, etc..) of the bin directory located under the root directory.
**Command:**
```bash
$ ls -F /bin
```

## Finally
Congratulations! You have successfully worked through the 15 `ls` command examples in Linux. Follow me on any of the different social media platforms and feel free to leave comments.