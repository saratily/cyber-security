### Week 3: Terminal-and-Bash

| command       |    Sample      | Description |
|:---------------|:---------------|:---------------------------------------------|
| pwd           | pwd  | current working directory (print working directory). |
| ls            | ls  | List directories and files in the current directory. |
|               |  ls -l | all files under current directory with their details |
|               |  ls -a | list hidden files also |
|               |  ls -t | list files according to their modification date (descending)|
|               |  ls -h | human readable format |
|               |  ls -S | list files according to their size (largest first) |
|               | ls --help |
| cd            | cd <relative dir>  | Navigate into a directory (change directory). |
| cd            | cd /<absolute dir>  | |
| mkdir         | mkdir <dir>  | Make a directory. |
| touch         | touch <file>  | Create an empty file. |
| cp            | cp ~/original.txt backup/  | creates a copy of the file |
| mv            | mv original.txt file1.txt  | Rename a file |
|             | mv ~/original.txt backup/  | Move file to another location |
|clear          | clear  | Clear the terminal screen. |
| rm            | rm <filename> | Remove a file.|
|               | rm -rf <dir> | Remove a directory recursively.|
| rmdir         | rmdir <dir>  | Remove a directory - dir should be empty.|
| cat           | cat file1.txt  | Display file content|
|               | cat file1.txt file2.txt file2.txt  > file.txt | Concatenation multiple files|
|               | cat -n log.txt | -n argument - add line number to each line |
| head          | head <file>  | Displays the top 10 lines of a file. (by default 10 lines |
|               | head -n <file>  | Displays the top n lines of a file. |
| tail          | tail <file>  | Displays the bottom 10 lines of a file. |
|               | tail -n <file> |    |
| more          | more <file>  | View file page by page Space bar -> next page. |
| less          | less <file>  | more flexible than more. 
|               |   | scroll forward and backward one line at a time
|               |   | also supports horizontal scrolling. |
| man           | man <cmd>  | brief description about cmd, and its options |
|               | man ls     |   | 
| find          | find <location> -type <type> -name <filename/dir>  | runs for searching file names or dir |
|               | -iname | for name insensetive |
|command &>/dev/null|      |  |
| grep          | grep <options> <word> <file>  | <options> |
|               | grep -il Sallystealer *       | -i = case insensetive |
|               |                               | -l = list file name  |
|               |                               | -r recursively, by default, not recursive |
|               |                               | <word> - search string |
|               |                               | <file> can use wildcard for file name, e.g. *, or *.txt |
| wc            |  wc  | lines or words inside of files. |
|               | wc -l |  line count | 
|               | wc -w |  word count | 
|\|  pipe       |   |  to combine multiple cmd |
| sed           | sed s/<old_value>/ /<new_value>/  | make substitute to a file |
|               |         | reads and edit text line by line - to match files |
| awk           | awk -F(delimiter) '{print $(field_number)}' <file> | isolate data points from a complex log file |
|               | awk '{print $3, $1}' <file> | delimiter - By default awk separate fields by space , could be comma, or semi-colon ; |
| nano/vi/vim/emac          | nano file.txt  | text editors  |
| script        | nano diskcleanup.sh  | edit script |
|               | #!/bin/bash | add shbang |
|               | chmod +x diskcleanup.sh | change file permissions to execute |
|               | ./diskcleanup.sh | execute file |
|               | ./diskcleanup.sh arg1 | script by passing arguments (e.g. IP lookup) | 
| xde-open      |   | to open image file from cmd line |

=========================================================================

grep -R "Megan,Patel" epscript/