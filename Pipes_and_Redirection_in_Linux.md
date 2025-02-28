# **Pipes & Redirection in Linux**

## **Introduction**
Linux provides powerful features for handling command-line input and output using **pipes** (`|`) and **redirection** (`>`, `>>`, `<`, `2>`, `&>`). These tools help streamline workflows by chaining commands together or managing data efficiently.

---

## **1. Pipes (`|`)**
Pipes allow the output of one command to be used as input for another, enabling efficient command chaining.

### **Examples**

1. **List files and filter `.txt` files:**
    ```bash
    ls | grep ".txt"
    ```
    - `ls` lists files in the directory.
    - `grep ".txt"` filters files containing `.txt`.

2. **Count lines containing "error" in a file:**
    ```bash
    cat file.txt | grep "error" | wc -l
    ```
    - `cat file.txt` displays the file content.
    - `grep "error"` extracts lines with "error".
    - `wc -l` counts the number of matching lines.

3. **Display currently running processes and filter `bash` processes:**
    ```bash
    ps aux | grep "bash"
    ```
    - `ps aux` lists all running processes.
    - `grep "bash"` filters processes related to `bash`.

---

## **2. Redirection**
Redirection allows capturing command output and directing it to files or using files as input.

### **Output Redirection (`>` and `>>`)**

1. **Save command output to a file (overwrite existing content):**
    ```bash
    echo "Hello, World!" > greeting.txt
    ```
    - Overwrites `greeting.txt` with "Hello, World!".

2. **Append output to a file (without overwriting):**
    ```bash
    echo "Goodbye!" >> greeting.txt
    ```
    - Adds "Goodbye!" to `greeting.txt` without deleting existing content.

### **Input Redirection (`<`)**

1. **Use a file as input for a command:**
    ```bash
    sort < file.txt
    ```
    - Sorts the contents of `file.txt` and displays the sorted output.

### **Error Redirection (`2>`, `&>` and `/dev/null`)**

1. **Redirect errors to a file:**
    ```bash
    ls non_existent_folder 2> error.log
    ```
    - Saves error messages to `error.log` if the folder doesn't exist.

2. **Redirect both output and errors to a file:**
    ```bash
    command &> output.log
    ```
    - Saves both standard output and error messages to `output.log`.

3. **Discard errors by redirecting them to `/dev/null`:**
    ```bash
    command 2> /dev/null
    ```
    - Suppresses error messages by sending them to `/dev/null` (a special device that discards data).

4. **Redirect only standard output to a file:**
    ```bash
    command > output.log 2> error.log
    ```
    - Saves standard output in `output.log`.
    - Saves errors in `error.log`.

---

## **3. Combining Pipes & Redirection**
Pipes and redirection can be used together for advanced workflows.

1. **Sort and save unique lines from a file:**
    ```bash
    sort < file.txt | uniq > sorted_unique.txt
    ```
    - Sorts `file.txt`, removes duplicates using `uniq`, and saves output to `sorted_unique.txt`.

2. **Count occurrences of a word and save results:**
    ```bash
    grep -o "error" file.txt | wc -l > error_count.txt
    ```
    - Counts occurrences of "error" and saves the result in `error_count.txt`.

3. **Monitor system logs and filter warnings:**
    ```bash
    tail -f /var/log/syslog | grep "WARNING" > warnings.log
    ```
    - Continuously monitors system logs for warnings and saves them to `warnings.log`.

---

## **4. Summary Table**

| Symbol | Description | Example |
|--------|-------------|-------------|
| `|` | Pipe - Pass output to another command | `ls | grep ".txt"` |
| `>` | Redirect output (overwrite) | `echo "Hello" > file.txt` |
| `>>` | Append output to file | `echo "Hello" >> file.txt` |
| `<` | Use file as input | `sort < file.txt` |
| `2>` | Redirect errors | `ls invalid_dir 2> errors.log` |
| `&>` | Redirect both output and errors | `command &> output.log` |
| `2> /dev/null` | Discard errors | `command 2> /dev/null` |

---

## **Conclusion**
Pipes and redirection are essential tools in Linux for handling command-line output efficiently. Mastering these techniques will improve workflow automation and command execution. 

---

