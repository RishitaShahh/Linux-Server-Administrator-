# **Wildcards - Globbing Patterns**

Wildcards are special characters that allow pattern matching for filenames and directories in Linux. They help automate tasks by reducing the need to type out exact filenames. Wildcards are widely used with commands such as `ls`, `cp`, `mv`, and `rm` to efficiently work with multiple files.

---

## **Common Wildcards and Their Functions**

| Wildcard | Function |
|----------|----------|
| `*` | Matches any number of characters, including none. |
| `?` | Matches exactly one character. |
| `[]` | Matches a single character from a specified set. |
| `{}` | Expands to multiple specified patterns. |
| `-` | Defines a range within square brackets. |
| `!` | Excludes specified characters inside brackets. |
| `**` | Matches files and directories recursively (when `globstar` is enabled). |
| `~` | Represents the home directory of the user. |

---

## **Explaining Wildcards with Examples**

### **1. Asterisk `*` (Matches Multiple Characters)**
- `*.txt` → Matches all `.txt` files (e.g., `notes.txt`, `logfile.txt`).
- `file*` → Matches any file starting with `file` (e.g., `file1`, `file_new`).

### **2. Question Mark `?` (Matches a Single Character)**
- `file?.txt` → Matches `file1.txt`, `fileA.txt` (but not `file12.txt`).
- `?.jpg` → Matches `1.jpg`, `a.jpg`, but not `12.jpg`.

### **3. Square Brackets `[]` (Matches One Character from a Set)**
- `file[1-3].txt` → Matches `file1.txt`, `file2.txt`, `file3.txt`.
- `file[a-c].txt` → Matches `filea.txt`, `fileb.txt`, `filec.txt`.
- `file[!1-3].txt` → Matches any `fileX.txt` where X is not `1`, `2`, or `3`.

### **4. Curly Braces `{}` (Expands to Multiple Options)**
- `file{1,2,3}.txt` → Matches `file1.txt`, `file2.txt`, `file3.txt`.
- `backup-{Jan,Feb,Mar}.zip` → Matches `backup-Jan.zip`, `backup-Feb.zip`, `backup-Mar.zip`.

### **5. Hyphen `-` (Specifies a Range within `[]` Brackets)**
- `file[0-9].txt` → Matches `file0.txt` to `file9.txt`.
- `file[a-z].txt` → Matches `filea.txt` to `filez.txt`.

### **6. Exclamation Mark `!` (Negates a Pattern Inside `[]`)**
- `file[!a-c].txt` → Matches files except `filea.txt`, `fileb.txt`, `filec.txt`.
- `file[!0-9].log` → Matches logs not starting with numbers.

### **7. Double Asterisk `**` (Recursive Matching)**
- `**/*.txt` → Matches all `.txt` files in current and subdirectories.
- `**/config.json` → Finds `config.json` files in all nested folders.

🔹 **Enable recursive matching:**
```bash
shopt -s globstar
```

### **8. Tilde `~` (Represents Home Directory)**
- `cd ~` → Navigates to the home directory.
- `ls ~/Downloads` → Lists files in the `Downloads` directory.

---

## **Practical Examples Using Wildcards**

| Command | Purpose |
|---------|---------|
| `ls *.log` | Lists all `.log` files. |
| `rm file?.txt` | Deletes files like `file1.txt`, `fileA.txt`. |
| `cp image[1-5].jpg ~/Pictures/` | Copies `image1.jpg` to `image5.jpg` to `Pictures`. |
| `mv report{1,2,3}.doc ~/Documents/` | Moves `report1.doc`, `report2.doc`, `report3.doc` to `Documents`. |
| `ls [!a-z]*` | Lists files **not** starting with lowercase letters. |
| `find . -name "*.bak"` | Finds all backup (`.bak`) files in current and subdirectories. |

---

## **Additional Notes**

🔹 **Escaping Wildcards:** If you want to treat wildcard characters as regular characters (not as patterns), prefix them with a backslash (`\`).
```bash
ls file\*
```

🔹 **Character Classes:** You can use predefined character classes within brackets:
- `[[:digit:]]` → Any number (`0-9`).
- `[[:alpha:]]` → Any letter (`A-Z` or `a-z`).
- `[[:lower:]]` → Any lowercase letter.
- `[[:upper:]]` → Any uppercase letter.
- `[[:space:]]` → Any whitespace character.

**Example:**
```bash
ls file[[:digit:]].txt
```
Matches `file0.txt` to `file9.txt`.

---

## **Caution When Using Wildcards with `rm`**

Wildcards can be dangerous with `rm` as they may delete unintended files. Always verify before executing deletion commands.

**Safe Practice:**
```bash
ls *.log
```
🔹 Preview the files before deleting them.

**Use Interactive Mode:**
```bash
rm -i *.txt
```
🔹 Asks for confirmation before deleting each file.

---

### **Conclusion**
Mastering wildcards in Linux allows you to work with multiple files efficiently. Whether you are listing, copying, moving, or deleting files, wildcards save time and effort. Understanding how they work ensures accuracy and prevents accidental file manipulations.

