### Zsh Tiered Command Cheat Sheet (macOS)
Beginner -> Intermediate -> Expert. Focused on interactive use while taking courses. Assumes zsh on macOS.

BEGINNER – Everyday Navigation & Basics

Navigation & Files

- pwd  
  Show current directory.

- ls  
  List files in current directory.

- ls -l  
  Long listing (permissions, size, dates).

- ls -a  
  Show hidden files (starting with .).

- cd DIR  
  Change directory (e.g., cd Documents).

- cd ..  
  Go up one directory.

- cd ~  
  Go to your home directory.

- mkdir DIR  
  Create a directory (e.g., mkdir projects).

- touch FILE  
  Create an empty file or update its timestamp (e.g., touch notes.txt).

- cp SRC DST  
  Copy files (e.g., cp file.txt backup.txt).

- mv SRC DST  
  Move or rename files (e.g., mv old.txt new.txt).

- rm FILE  
  Remove file (no trash!).

- open .  
  Open current directory in Finder (macOS).

- open FILE  
  Open file with default macOS app (e.g., open report.pdf).

Inspecting Files & Output

- cat FILE  
  Show entire file contents (cat notes.txt).

- less FILE  
  View file page by page (q to quit).

- head FILE  
  Show first 10 lines.

- tail FILE  
  Show last 10 lines.

- tail -f FILE  
  Follow file as it grows (logs).

- wc -l FILE  
  Count lines in a file.

Help & Basic Info

- command --help  
  Quick help for many commands (ls --help).

- man command  
  Manual page (full documentation, e.g., man grep).

- which command  
  Show path to command being run (which python).

- echo TEXT  
  Print text or variable value (echo $SHELL).

- clear  
  Clear terminal screen.

- CTRL + C  
  Cancel current running command.

INTERMEDIATE – Productivity, History, Globbing

History & Reuse

- history  
  Show recent commands (history | tail).

- !n  
  Re-run command number n from history (e.g., !125).

- !!  
  Re-run previous command.

- sudo !!  
  Re-run last command with sudo.

- !string  
  Re-run last command starting with string (e.g., !grep).

- CTRL + R  
  Reverse search history; type to filter, press Enter to run.

Redirection & Pipes

- cmd > file  
  Send output to file (overwrite), e.g., ls > listing.txt.

- cmd >> file  
  Append output to file, e.g., echo "line" >> notes.txt.

- cmd1 | cmd2  
  Pipe output of cmd1 into cmd2, e.g., ls | grep .txt.

- cmd < file  
  Use file as input, e.g., sort < names.txt.

Search & Filtering

- grep PATTERN FILE  
  Search for text in files, e.g., grep error server.log.

- grep -i  
  Case-insensitive search, e.g., grep -i warning server.log.

- grep -r PATTERN DIR  
  Recursive search, e.g., grep -r TODO src.

- find DIR -name PATTERN  
  Find files by name, e.g., find . -name "*.py".

- sort  
  Sort lines, e.g., sort names.txt.

- uniq  
  Remove duplicate neighboring lines, e.g., sort names.txt | uniq.

Globbing (File Patterns) – zsh Superpowers

- *.txt  
  All .txt files (ls *.txt).

- **/*.py  
  All .py files in all subdirectories (ls **/*.py).

- */  
  Only directories in the current folder (ls -d */).

- *( .om[1,10] )  
  10 most recently modified files (requires extended globbing).

Aliases & Basic Customization

- alias  
  List aliases.

- Example aliases:  
  alias ll='ls -lh'  
  alias gs='git status'

- unalias NAME  
  Remove alias (unalias ll).

- Edit zsh config:  
  nano ~/.zshrc

- Reload config:  
  source ~/.zshrc

EXPERT – Scripting, Functions, Advanced zsh

Variables & Substitution

- Set variable:  
  PROJECT=aws-course

- Use variable:  
  echo $PROJECT

- Use default if unset:  
  echo ${PORT:-8000}

- Remove shortest match from end:  
  file=${path%/*}     (directory portion)

- Remove shortest match from start:  
  name=${path#*/}     (drop leading directory)

Command Substitution & Arithmetic

- Command substitution:  
  FILES=$(ls *.txt)

- Arithmetic evaluation:  
  echo $((2 * 3 + 4))

Process & Job Control

- ps aux | grep python  
  Show processes and filter for python.

- kill PID  
  Terminate process by ID (kill 12345).

- kill -9 PID  
  Force kill (last resort).

- fg %n  
  Bring job n to foreground (fg %1).

- bg %n  
  Resume job n in background (bg %1).

zsh-Specific Niceties

- Auto cd into directories:  
  set -o AUTO_CD

- Directory stack:  
  setopt AUTO_PUSHD  
  dirs -v         (show directory stack)  
  pushd src       (push and cd to src)  
  popd            (go back)

- Initialize advanced completion (often in ~/.zshrc):  
  autoload -Uz compinit  
  compinit

- Use zsh globbing with printing:  
  print -l **/*.py
