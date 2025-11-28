# Linux Commands Notes
# 11/14/2025


## nano
**Purpose:** Edit text files from the command line.
**Example:** nano myfile.txt

## du (du --help, man du)
**Purpose:** short for disk usage, is a linux command which helps you identify what files/directories are consuming how much space.
**Flags:** -a: will list all files and directories, instead of just directories only, -h: will list the file sizes in human readable format (B,MB,KB,GB), -c using this flag will print the total size at the end just in case you want to find the size of directory you were enumerating, -d<number>: to specify the depth-ness of a directory you want to view the results for (eg. -d 1 = show only top-level folders), --time: show the last modification timestamp for each entry 
**Example:** typing the command: du <directory>  **Explanation:** You'll see output like 3409  ./Documents    9182 ./Downloads, The folders in their respective folders are listed with the size they occupy on the disk. The size whos may be in B, MB, KB, GB. The files inside a folder are not shown, only the folders are listed by running du/<directory> command. By default, sizes are shown in KB. It recursively wlaks through deeper directories unless you control it with flags. **List every file inside /home with its size** du -a /home/ **Filter results using grep** du -a /home/ | grep user (Shows any item containing "user" in its name), **Show directory sizes in readable units** du -h /var/log **Show sizes up to depth 2** du -h -d 2 /etc **Show modification timestamps with depth 1** du --time -d 1

## grep (grep --help, man grep)
**Purpose:** to filter text, displaying only the lines that contain a match for a given pattern. Allows for quick extraction relevant information from files of any text-based data.
**Example:** to search for the word "error" in a file named logfile.txt, the command would be: grep "error" logfile.txt
**Flags:** -i: Ignore case-sensitive during the search, -v: invert the match and shows all lines that do not containt the word, -n: displays all matching lines with their correspdonding line numbers. 


-R (grep -R "pattern" /path/to/directory): The option that enables recursive searching and follows symbolic links
"pattern": The text or regular expression you are searching for. Enclosed in double quotes if it contains spaces or special chars
/path/to/directory: The starting directory for the recursive search. If you want to search the current directory, you can use "."
**Example:** Searching for a specific word in the current directory and its subdirectories: grep -R "example_word" . (the . is part of the command)
**Example:** Searching for a pattern in a specific direcory and its subdirectories: grep -R "error_code" /var/log
**Example:** Combining with other options: Case-insensitive search: grep -Ri "search_term" /home/user/documents

-h

