# Linux Commands Notes
# 11/14/2025


## nano
**Purpose:** Edit text files from the command line.
**Example:** nano myfile.txt

## grep (grep --help, man grep)
**Purpose:** to filter text, displaying only the lines that contain a match for a given pattern. Allows for quick extraction relevant information from files of any text-based data.
**Example:** to search for the word "error" in a file named logfile.txt, the command would be: grep "error" logfile.txt
**Options:** -i: Ignore case-sensitive during the search, -v: invert the match and shows all lines that do not containt the word, -n: displays all matching lines with their correspdonding line numbers. 


-R (grep -R "pattern" /path/to/directory): The option that enables recursive searching and follows symbolic links
"pattern": The text or regular expression you are searching for. Enclosed in double quotes if it contains spaces or special chars
/path/to/directory: The starting directory for the recursive search. If you want to search the current directory, you can use "."
**Example:** Searching for a specific word in the current directory and its subdirectories: grep -R "example_word" . (the . is part of the command)
**Example:** Searching for a pattern in a specific direcory and its subdirectories: grep -R "error_code" /var/log
**Example:** Combining with other options: Case-insensitive search: grep -Ri "search_term" /home/user/documents

-h

