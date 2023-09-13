---
weight: 1
title: Find and Replace String Content and Renaming Files and Directories
date: 2023-09-14T01:27:04+08:00
lastmod: 2023-09-14T01:27:04+08:00
draft: false
author: venven
authorLink: https://www.datacareph.com
description: A Utility Command to Find and Replace String Content and Renaming Files and Directories
images:
  - posts/src/default.png
featuredimage: posts/src/default.png
resources:
  - name: featured-image
    src: featured-image.png
tags:
  - find
  - utilities
  - grep
  - sed
  - command
  - terminal
categories:
  - Linux
lightgallery: false
toc:
  enable: true
twemoji: false
math:
  enable: false
---
In the realm of command-line #utilities, the combination of #find, #grep, and #sed is a powerful trio that empowers users to perform intricate operations on files and directories within a Linux environment. This article will provide an in-depth exploration of this #terminal #command and how it can be harnessed to find, search, and replace content in a directory, as well as rename files and directories.
## Finding and Replacing Content in Files
The `-type f` in an option for `find` command. It specifies that we're only interested in files, not directories.

To find files containing a specific string, you can use the following command:
```sh
find /path/to/directory -type f -exec grep -l 'string-to-find' {} \;
```
-OR-
```sh
find /path/to/directory -type f -exec grep -l 'string-to-find' {} +
```
- **`-l`**: This option tells `grep` to only display the names of files that contain a match, not the actual lines with the match.
- **`-exec`**: This is another option for the `find` command. It allows you to execute a command on the files or directories that match the search criteria.
Note: What we have here is we replace `\;` to `+` if you are executing it on the large file.

Both of these commands achieve the same result:
```sh
grep -r "text string to search" /path/to/directory
```
- `-r` - Recursively search through directories.

#### Creating Backup Copies

If you wish to create backup copies of the files found, you can use this command:
```sh
find /path/to/directory -type f ! -name '*.bak' -exec grep -l 'string-to-find' {} \; | xargs -I {} cp {} {}.bak
```
This command first locates files containing the target string, then creates a backup copy of each file.

## Searching and Replacing Content
Find all files in the current directory and its sub-directories containing the string `string-to-find` in their contents and replace it with `string-to-replace`. You can also add flag e.g. `! -name '*.bak' ` to exclude those file ending with `.bak`

To search for and replace content within files, you can use this command:
```sh
find /path/to/directory -type f -exec grep -l 'string-to-find' {} \; -and -exec sed -i 's/string-to-find/string-to-replace/g' {} \;

```

## Renaming Files and Directories

#### Finding Files or Directories by Name

To locate files or directories with a specific name, you can use the following command:
```sh
find /path/to/directory -name '*filename-to-find*'
```
This command searches for files or directories containing the specified string in their names.

### Files and Directories: Find or Find and Replace
To rename files and directories, you can use the following command:

```sh
find /path/to/directory -depth -name '*filename-to-find*' -execdir bash -c 'for f; do mv -v "$f" "${f//filename-to-find/filename-to-replace}"; done' _ {} \;
```

This bash command will find all files and directories containing the string `filename-to-find` in the name and rename them to replace `filename-to-find` with `filename-to-replace`.

## Combining both commands
Finally, we come up with one command on the go, by copying and pasting. Just make sure to replace `PATH_TARGET`, `STRING_TO_FIND`, `STRING_TO_REPLACE` as the writer of this article is not responsible for any loss. You have been warned. And always run this command on the test environment, though this command is already tested.

```bash
PATH_TARGET="./path/to/directory" \
&& STRING_TO_FIND="string-to-find" \
&& STRING_TO_REPLACE="string-to-replace" \
&& echo "Step 1: Finding and replacing file contents. Working.." \
&& find $PATH_TARGET -type f -exec grep -l $STRING_TO_FIND {} \; -and -exec sed -i "s/$STRING_TO_FIND/$STRING_TO_REPLACE/g" {} \; \
&& echo "Step 2: We are now renaming files and directories. Working.." \
&& find $PATH_TARGET -depth -name "*$STRING_TO_FIND*" -execdir bash -c 'for f; do mv -v "$f" "${f//'"$STRING_TO_FIND"'/'"$STRING_TO_REPLACE"'}"; done' _ {} \;
```

#### Interesting utility. Deleting files that has .bak file extension
This command searches in the specified directory for files with names ending with `.bak`. For each file found, it deletes the file and provides a message for each deletion.
```sh
find /path/to/directory -name '*.bak' -exec rm -v {} \;
```

## Conclusion
This utility command, combining `find`, `grep`, and `sed`, serves as a versatile tool for manipulating files and directories within a Linux environment. By providing a structured approach to finding, searching, and replacing content, as well as renaming files and directories, it empowers users with a powerful set of capabilities. Incorporating this command into your workflow can significantly enhance your efficiency and productivity in handling large datasets or file structures.