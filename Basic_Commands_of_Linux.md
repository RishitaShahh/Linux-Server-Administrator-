# Linux Shell Prompt and Basic Commands

The shell prompt in Linux typically follows this format:

```bash
[username@hostname current_location]$

```

- **`username`**: The current user logged in.
    - `root`: Superuser with full privileges.
    - Other names: Regular user.
- **`@`**: Separates the **username** and the **hostname**.
- **`hostname`**: The name of the system or server you're logged into.
- **`current_location (~)`**: The current directory. `~` indicates the user's home directory.
- **`$`**: Indicates a normal user prompt.
- **`#`**: Indicates the root user prompt (superuser).

### Example:

- **Root User**: `[root@localhost ~]#`
- **Normal User**: `[user@localhost ~]$`

# **Basic commands :**

## `ls` Command :

Lists

1. **`ls`**
    
    Lists the files and directories in the current directory.
    
2. **`ls [directory_name]`**
    
    Lists the files and directories in the specified directory.
    

### Common `ls` Options:

Here’s a table summarizing the **modes** (options) of the **`ls`** command:

| Modes  | **Description** |
| --- | --- |
| `ls -1` | Lists one file per line. |
| `ls -l` | Long format listing with detailed information like file permissions, owner, size, and modification date. |
| `ls -a` | Lists all files, including hidden files (those starting with a dot `.`). |
| `ls -lh` | Displays file sizes in a human-readable format (e.g., KB, MB). |
| `ls -t` | Sorts files by modification time, showing the newest files first. |
| `ls -r` | Reverses the order of the listing. |
| `ls -R` | Lists all files in the current directory and its subdirectories recursively. |
| `ls -d */` | Displays only directories in the current location. |
| `ls -lah` | Lists all files, including hidden ones, in long format with human-readable sizes. |
| `ls -S` | Sorts files by size, with the largest files first. |
| `ls -u` | Sorts files by last access time. |
| `ls -v` | Sorts files alphanumerically, as opposed to the default lexicographical order. |

---

## `pwd` Command :

**Print Working Directory**

The `pwd` command shows the full path of your current directory in Linux.

Usage:

- **`pwd`**: Prints the current directory path.
- **`pwd -L`**: Logical path (includes symlinks).
- **`pwd -P`**: Physical path (resolves symlinks).

---

## **`hostname` Command :**

**`hostname`**

Prints the current hostname of the system.

**`hostnamectl`**

Provides detailed information about the hostname and allows you to set it.

**`hostname -i`**: Shows the IP address of the hostname.

---

## **`man` Command:**

- Displays detailed **manual pages** for commands.
- Example: `man ls` shows the manual for the `ls` command.

---

## **`info` Command:**

- Provides more detailed **documentation** than `man`, including examples and structured content.
- Example: `info ls` gives detailed info on `ls`.

---

## **`help` Command:**

- Displays **basic help** for **bash built-in commands**.
- Example: `help cd` gives information on how to use `cd`.

---

 ****

## **`cd` Commands**:

1. **`cd [directory]`**
    
    Changes to the specified directory.
    
    Example:
    
    ```bash
    cd /home/user/Documents
    
    ```
    
- **Related Commands**:
    - `cd ..`: Moves up one directory level (to the parent directory).
    - `cd ~`: Changes to the user's home directory.
    - `cd -`: Returns to the previous working directory.
    - `cd /`**:** Changes the directory to the root (`/`) directory

---

## File Information Commands :

- **Commands**:
    - `file [file_name]`: Displays the file type.
    - `ls -lh`: Displays the size of files in a human-readable format.
    - `stat [file_name]`: Displays detailed information about a file.

---

## `touch`**Commands :**

- **Description**: Creates a new empty file or updates the timestamp of an existing file.

---

## `cat` **Commands :**

The `cat` command displays, combines, or creates files.

### Basic Commands for `cat`:

1. **Create a file and add content**:
    - **Command**: `cat > file.txt`
    - **Description**: Creates a new file and lets you type content directly into it. To finish:
        - Press `Ctrl + D` to save and exit.
        - Press `Ctrl + C` to exit without saving.
2. **Append to a file**:
    - **Command**: `cat >> file.txt`
    - **Description**: Adds new content to the end of an existing file.
3. **View a file**:
    - **Command**: `cat file.txt`
    - **Description**: Displays the contents of the file on the screen.
4. **Merge files**:
    - **Command**: `cat file1.txt file2.txt > merged.txt`
    - **Description**: Merges multiple files into one. The content from `file1.txt` and `file2.txt` will be combined into `merged.txt`.

### Advanced Usage:

1. **Add multiple lines until EOF**:
    - **Command**: `cat << EOF >> file.txt`
    - **Description**: Allows you to write multiple lines to a file until `EOF` is typed on a new line.

### **Common Options**

| Option | Description |
| --- | --- |
| `-n` | Numbers all output lines. |
| `-b` | Numbers non-blank lines only. |
| `-E` | Shows `$` at the end of each line. |
| `-s` | Suppresses repeated empty lines. |
| `-T` | Displays tabs as `^I`. |
| `-v` | Displays non-printing characters. |

### **Paginated Display:**

1. **Use less or more to read:**
    
    ```bash
    cat messages | less
    
    ```
    
    - Displays content page by page.
    - Alternative: Use `less messages` or `more messages` directly.
    

---

## `mkdir` **Commands :**

The `mkdir` command in Linux is used to create directories (folders).

### Syntax:

`mkdir [OPTIONS] DIRECTORY_NAME`

### Options:

1. **Create a Single Directory:**
    - Use `mkdir folder_name` to create a directory named `folder_name`.
2. **Create Multiple Directories:**
    - Use `mkdir dir1 dir2 dir3` to create multiple directories at once (e.g., `dir1`, `dir2`, `dir3`).
3. **Create Parent Directories (Nested):**
    - Use `mkdir -p parent/child/grandchild` to create nested directories. The `p` option ensures all parent directories are created if they don't exist.
4. **Set Permissions While Creating:**
    - Use `mkdir -m 755 folder_name` to create a directory with specific permissions, such as `755`.
5. **Display Messages While Creating Directories:**
    - Use `mkdir -v folder_name` to show a confirmation message as the directory is created.

---

### `rm` **Commands :**

 Table summarizing the `rm` command and its common options:

| **Command** | **Description** | **Example** |
| --- | --- | --- |
| `rm file.txt` | Deletes a **single file**. | `rm example.txt` |
| `rm file1.txt file2.txt` | Deletes **multiple files**. | `rm report1.txt report2.txt` |
| `rm *` | Deletes **all files in the current directory.** | `rm *` |
| `rmdir folder_name` | Deletes an **empty directory**. | `rmdir empty_folder` |
| `rm -r folder_name` | **Recursively** deletes a directory and its contents. | `rm -r my_folder` |
| `rm -f file.txt` | **Forcefully** deletes a file without confirmation. | `rm -f error.log` |
| `rm -rf folder_name` | Forcefully deletes a directory and all its contents. | `rm -rf backup_folder` |
| `rm -v file.txt` | **Verbose mode** - shows what is being deleted. | `rm -v temp.txt` |
| `rm -i file.txt` | **Interactive mode** - asks for confirmation before deleting. | `rm -i data.csv` |
| `rm *.txt` | Deletes all `.txt` files in the current directory. | `rm *.txt` |
| `rm --help` | Displays help information for the `rm` command. | `rm --help` |

---

## **Process Management Commands**

- **Commands**:
    - `Ctrl + C`: Stops a running process.
    - `Ctrl + Z`: Suspends a process.
    - `ctrl + l`: Clears the terminal screen.
    - `clear`: Performs the same action as `ctrl + l`.
