# bash-script


# 🐚 **Bash Scripting – Questions with Answers & Explanations**

---

### **1. What is a Bash script?**

* **Answer:** A text file with a series of commands interpreted by the Bash shell.
* **Explanation:** Used to automate tasks in Unix/Linux.

---

### **2. How do you make a Bash script executable?**

* **Answer:** `chmod +x script.sh`
* **Explanation:** Grants execute permission.

---

### **3. What is `#!/bin/bash` at the top of a script?**

* **Answer:** It's the shebang line that tells the system to run the script with Bash.
* **Explanation:** Ensures correct interpreter.

---

### **4. How do you run a Bash script?**

* **Answer:** `./script.sh` or `bash script.sh`
* **Explanation:** `./` runs as a program, `bash` runs using the shell explicitly.

---

### **5. What is `$0`, `$1`, `$2` in Bash?**

* **Answer:** `$0` is the script name, `$1`, `$2`, etc., are arguments.
* **Explanation:** Used for parameter handling.

---

### **6. How do you read user input in Bash?**

* **Answer:** `read varname`
* **Explanation:** Captures input from the keyboard.

---

### **7. What is `if` statement syntax in Bash?**

* **Answer:**

  ```bash
  if [ condition ]; then
    # code
  fi
  ```
* **Explanation:** Used for conditional logic.

---

### **8. How do you write a loop in Bash?**

* **Answer (for loop):**

  ```bash
  for i in 1 2 3; do echo $i; done
  ```

---

### **9. How to define and use a function?**

* **Answer:**

  ```bash
  myfunc() { echo "Hello"; }
  myfunc
  ```

---

### **10. What is `exit 0` used for?**

* **Answer:** Exits the script with a success status.
* **Explanation:** `0` means success; other codes signal errors.

---

### **11. How do you comment in Bash?**

* **Answer:** Use `#` before the comment.
* **Explanation:** Ignored during execution.

---

### **12. What is `&&` and `||` in Bash?**

* **Answer:** `&&` runs next command only if previous succeeded, `||` runs if failed.
* **Explanation:** Used for conditional chaining.

---

### **13. What is `"$@"` and `"$*"`?**

* **Answer:** Both refer to all script arguments. `"$@"` treats them individually, `"$*"` as one string.
* **Explanation:** Useful for looping over inputs.

---

### **14. How do you check if a file exists?**

* **Answer:** `[ -f filename ]`
* **Explanation:** Returns true if it's a regular file.

---

### **15. How do you check if a directory exists?**

* **Answer:** `[ -d dirname ]`

---

### **16. What does `set -e` do?**

* **Answer:** Exits script on any error.
* **Explanation:** Safer execution in automation.

---

### **17. What is `trap` in Bash?**

* **Answer:** Used to catch signals (e.g., `SIGINT`) and perform cleanup.
* **Example:** `trap "echo Exiting; exit" INT`

---

### **18. How do you capture command output in a variable?**

* **Answer:** `var=$(ls)`
* **Explanation:** Uses command substitution.

---

### **19. What is `source` or `.` command used for?**

* **Answer:** Runs a script in the current shell.
* **Example:** `. script.sh` or `source script.sh`

---

### **20. Difference between `==` and `-eq`?**

* **Answer:** `==` is for strings, `-eq` is for integers.

---

### **21. How do you append to a file in Bash?**

* **Answer:** `echo "text" >> file.txt`

---

### **22. How to redirect both stdout and stderr to a file?**

* **Answer:** `command > file 2>&1`

---

### **23. How to check the exit status of a command?**

* **Answer:** Use `$?`
* **Example:**

  ```bash
  ls /tmp
  echo $?
  ```

---

### **24. How do you loop through files in a directory?**

* **Answer:**

  ```bash
  for file in *; do echo "$file"; done
  ```

---

### **25. What does `shift` do?**

* **Answer:** Shifts positional parameters to the left.
* **Explanation:** Useful for processing arguments.

---

### **26. Write a script to check if a service is running.**

* **Answer:**

  ```bash
  service_name=nginx
  if systemctl is-active --quiet $service_name; then
    echo "$service_name is running"
  else
    echo "$service_name is NOT running"
  fi
  ```

---

### **27. How do you read a file line by line in Bash?**

* **Answer:**

  ```bash
  while read line; do
    echo "$line"
  done < file.txt
  ```

---

### **28. Write a script to backup a directory.**

* **Answer:**

  ```bash
  tar -czf backup_$(date +%F).tar.gz /path/to/dir
  ```

---

### **29. How do you perform arithmetic in Bash?**

* **Answer:** Use `(( ))` or `let`
* **Example:** `((sum = 5 + 3))`

---

### **30. Write a script to find the largest file in a directory.**

* **Answer:**

  ```bash
  find . -type f -exec du -h {} + | sort -rh | head -n 1
  ```

---

### **31. What is `xargs` used for?**

* **Answer:** Converts input into arguments for a command.
* **Example:** `cat files.txt | xargs rm`

---

### **32. How can you create a menu-driven script in Bash?**

* **Answer:** Use `select` loop.

  ```bash
  select opt in "Start" "Stop" "Exit"; do
    case $opt in
      Start) echo "Starting";;
      Stop) echo "Stopping";;
      Exit) break;;
    esac
  done
  ```

---

### **33. Script to delete logs older than 7 days?**

* **Answer:**

  ```bash
  find /var/log -name "*.log" -mtime +7 -exec rm -f {} \;
  ```

---

### **34. How do you handle JSON in Bash?**

* **Answer:** Use `jq` tool.
* **Example:** `cat file.json | jq '.key'`

---

### **35. Write a script to monitor disk usage and send alert if > 80%.**

* **Answer:**

  ```bash
  usage=$(df / | awk 'NR==2 {print $5}' | sed 's/%//')
  if [ "$usage" -gt 80 ]; then
    echo "Disk usage above 80%"
  fi
  ```

---

### **36. What is here document (heredoc)?**

* **Answer:**

  ```bash
  cat <<EOF
  Hello World
  EOF
  ```

---

### **37. How to use `getopts` for option parsing?**

* **Answer:**

  ```bash
  while getopts ":u:p:" opt; do
    case $opt in
      u) user=$OPTARG ;;
      p) pass=$OPTARG ;;
    esac
  done
  ```

---

### **38. Script to rename all `.txt` files to `.bak`:**

* **Answer:**

  ```bash
  for f in *.txt; do mv "$f" "${f%.txt}.bak"; done
  ```

---

### **39. How do you validate if a variable is an integer?**

* **Answer:**

  ```bash
  [[ "$var" =~ ^[0-9]+$ ]] && echo "Integer"
  ```

---

### **40. What is the use of `eval` in Bash?**

* **Answer:** Executes a string as a command.
* **Caution:** Can be dangerous if not sanitized.

---

### **41. What is subshell in Bash?**

* **Answer:** A separate shell instance within `()`.
* **Example:** `(cd /tmp && ls)`

---

### **42. Difference between `"` and `'` in Bash?**

* **Answer:** `"` allows variable expansion; `'` does not.

---

### **43. How do you debug a Bash script?**

* **Answer:** Run with `bash -x script.sh`
* **Explanation:** Shows command tracing.

---

### **44. What is array in Bash?**

* **Answer:**

  ```bash
  arr=(one two three)
  echo "${arr[1]}"
  ```

---

### **45. How to count number of lines in a file?**

* **Answer:** `wc -l file.txt`

---

### **46. How to send an email from Bash script?**

* **Answer:** Use `mailx`, `sendmail`, or `ssmtp`.
* **Example:** `echo "Body" | mail -s "Subject" user@example.com`

---

### **47. What is the purpose of `/dev/null`?**

* **Answer:** A null device — discard output.
* **Example:** `command > /dev/null 2>&1`

---

### **48. Script to find and kill a process by name:**

* **Answer:**

  ```bash
  pkill -f "process_name"
  ```

---

### **49. How to parse CSV in Bash?**

* **Answer:**

  ```bash
  while IFS=, read -r col1 col2; do
    echo "$col1 - $col2"
  done < file.csv
  ```

---

### **50. Explain `while true; do ... done` loop.**

* **Answer:** Infinite loop, used for daemons, polling, or watchers.
* **Break out with:** `break` or `trap`

---

### **51. How do you check if a variable is empty?**

* **Answer:**

  ```bash
  if [ -z "$var" ]; then echo "Empty"; fi
  ```
* **Explanation:** `-z` checks for zero-length string.

---

### **52. How do you check if a variable is set (non-null)?**

* **Answer:**

  ```bash
  if [ -n "$var" ]; then echo "Not empty"; fi
  ```

---

### **53. Difference between `exec` and running a command normally?**

* **Answer:** `exec` replaces the current shell with the command.
* **Example:** `exec ls` replaces the script with `ls`.

---

### **54. What is the purpose of `sleep` command in scripts?**

* **Answer:** Pauses execution for given seconds.
* **Example:** `sleep 5`

---

### **55. How to add a timestamp to a log in a loop?**

* **Answer:**

  ```bash
  echo "$(date): log entry" >> log.txt
  ```

---

### **56. Script to monitor memory usage?**

* **Answer:**

  ```bash
  free -m | awk 'NR==2 {print "Memory Used: "$3"MB"}'
  ```

---

### **57. How to extract a substring from a variable?**

* **Answer:**

  ```bash
  str="abcdef"
  echo "${str:2:3}"  # cde
  ```

---

### **58. How to find all `.sh` files recursively?**

* **Answer:**

  ```bash
  find . -type f -name "*.sh"
  ```

---

### **59. What does `IFS` do?**

* **Answer:** Internal Field Separator — controls how Bash splits strings.
* **Example:**

  ```bash
  IFS=',' read -r name age <<< "John,25"
  ```

---

### **60. Script to convert all filenames to lowercase**

* **Answer:**

  ```bash
  for f in *; do
    mv "$f" "$(echo $f | tr '[:upper:]' '[:lower:]')"
  done
  ```

---

### **61. How do you generate a random number in Bash?**

* **Answer:** Use `$RANDOM`

  ```bash
  echo $((RANDOM % 100))
  ```

---

### **62. How to create a temporary file securely?**

* **Answer:**

  ```bash
  tempfile=$(mktemp)
  ```

---

### **63. Script to monitor CPU usage over time**

* **Answer:**

  ```bash
  while true; do
    top -bn1 | grep "Cpu(s)"
    sleep 5
  done
  ```

---

### **64. What is `select` used for in scripts?**

* **Answer:** Creates a numbered menu for user selection.

---

### **65. Difference between `cron` and `at`?**

* **Answer:** `cron` schedules recurring jobs; `at` runs one-time tasks.

---

### **66. Script to send alert if a port is closed**

* **Answer:**

  ```bash
  port=22
  if ! nc -z localhost $port; then
    echo "Port $port is closed!"
  fi
  ```

---

### **67. What does `2>&1` do in redirection?**

* **Answer:** Redirects stderr (`2`) to stdout (`1`).

---

### **68. What is the purpose of `set -x`?**

* **Answer:** Enables debugging by printing each command before execution.

---

### **69. What is Bash’s `readonly` used for?**

* **Answer:** Makes a variable immutable.

  ```bash
  readonly NAME="admin"
  ```

---

### **70. Script to check internet connection**

* **Answer:**

  ```bash
  ping -c1 google.com &> /dev/null && echo "Connected" || echo "Disconnected"
  ```

---

### **71. How to find duplicate lines in a file using Bash?**

* **Answer:**

  ```bash
  sort file.txt | uniq -d
  ```

---

### **72. How to list all environment variables?**

* **Answer:** `printenv` or `env`

---

### **73. How to get the current shell?**

* **Answer:** `echo $SHELL`

---

### **74. How to delete a specific line in a file using Bash?**

* **Answer:** Using `sed`:

  ```bash
  sed -i '5d' file.txt
  ```

---

### **75. How do you measure script execution time?**

* **Answer:**

  ```bash
  start=$(date +%s)
  # commands
  end=$(date +%s)
  echo "Time taken: $((end - start))s"
  ```

---

### **76. What is the difference between `$*` and `$@` without quotes?**

* **Answer:** Both expand all arguments, but behave differently when quoted.

---

### **77. What is the difference between `[` and `[[` in Bash?**

* **Answer:** `[[` is more flexible and supports regex, `[` is POSIX-compliant.

---

### **78. Write a script to simulate a progress bar**

* **Answer:**

  ```bash
  for i in {1..10}; do
    echo -ne "$i%\r"
    sleep 1
  done
  ```

---

### **79. How to rename multiple files with a pattern?**

* **Answer:**

  ```bash
  for file in *.log; do mv "$file" "${file%.log}.bak"; done
  ```

---

### **80. Script to remove trailing spaces in a file**

* **Answer:**

  ```bash
  sed -i 's/[ \t]*$//' file.txt
  ```

---

### **81. How do you handle errors in Bash?**

* **Answer:**

  ```bash
  command || { echo "Failed"; exit 1; }
  ```

---

### **82. How do you detect the OS in Bash?**

* **Answer:**

  ```bash
  unameOut="$(uname -s)"
  echo $unameOut
  ```

---

### **83. How do you count how many times a string appears in a file?**

* **Answer:**

  ```bash
  grep -o "pattern" file.txt | wc -l
  ```

---

### **84. What is a shebang and why is it important?**

* **Answer:** `#!/bin/bash` tells the system which interpreter to use.

---

### **85. Script to restart a service if it fails**

* **Answer:**

  ```bash
  service=nginx
  if ! systemctl is-active --quiet $service; then
    systemctl restart $service
  fi
  ```

---

### **86. What is `basename` used for?**

* **Answer:** Strips path and shows filename.

  ```bash
  basename /path/to/file.txt
  ```

---

### **87. How to send a Slack alert from Bash?**

* **Answer:** Use `curl` with Slack webhook:

  ```bash
  curl -X POST -H 'Content-type: application/json' --data '{"text":"Alert"}' https://hooks.slack.com/services/...
  ```

---

### **88. How do you increment a variable in Bash?**

* **Answer:**

  ```bash
  count=0
  ((count++))
  ```

---

### **89. What is the use of `wait` in Bash?**

* **Answer:** Waits for background processes to finish.

---

### **90. Script to count files by extension**

* **Answer:**

  ```bash
  for ext in txt log sh; do
    echo "$ext: $(ls *.$ext 2>/dev/null | wc -l)"
  done
  ```

---

### **91. What is the purpose of `/etc/profile` vs `~/.bashrc`?**

* **Answer:** `/etc/profile` is system-wide; `~/.bashrc` is user-specific and used for interactive sessions.

---

### **92. Script to check if user exists**

* **Answer:**

  ```bash
  id "$1" &>/dev/null && echo "User exists" || echo "No such user"
  ```

---

### **93. How do you define global vs local variables in Bash functions?**

* **Answer:**

  ```bash
  local var="only inside function"
  ```

---

### **94. How to generate a password in Bash?**

* **Answer:**

  ```bash
  tr -dc A-Za-z0-9 </dev/urandom | head -c 12
  ```

---

### **95. Script to validate IP address format**

* **Answer:**

  ```bash
  [[ $ip =~ ^[0-9]+\.[0-9]+\.[0-9]+\.[0-9]+$ ]] && echo "Valid" || echo "Invalid"
  ```

---

### **96. How do you reverse the lines in a file?**

* **Answer:** `tac file.txt`

---

### **97. What is the purpose of `$LINENO`?**

* **Answer:** Returns the current line number in the script.

---

### **98. How to get the size of a file?**

* **Answer:** `stat -c%s filename`

---

### **99. How to remove duplicates from a file?**

* **Answer:** `sort file.txt | uniq > newfile.txt`

---

### **100. Script to rotate logs manually**

* **Answer:**

  ```bash
  mv logfile.log logfile.log.1
  touch logfile.log
  ```

---
