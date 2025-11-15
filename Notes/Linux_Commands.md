# Linux Commands Notes
# 11/14/2025


## nano
**Purpose:** Edit text files from the command line.
**Example:** nano myfile.txt

## grep (grep --help, man grep)
**Purpose:** to filter text, displaying only the lines that contain a match for a given pattern. Allows for quick extraction relevant information from files of any text-based data.
**Example:** to search for the word "error" in a file named logfile.txt, the command would be: grep "error" logfile.txt
**Options:** -i: Ignore case-sensitive during the search, -v: invert the match and shows all lines that do not containt the word, -n: displays all matching lines with their correspdonding line numbers. 
