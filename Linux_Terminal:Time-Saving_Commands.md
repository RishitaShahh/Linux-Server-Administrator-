# Linux Terminal: Time-Saving Commands




## **Introduction**
Linux is a powerful and flexible operating system that provides numerous shortcuts and commands to enhance productivity. This document covers essential commands and techniques to improve efficiency when working with the Linux terminal.

---

### **1. Autocompletion with Tab**
When navigating directories, use the **Tab** key to autocomplete paths. This speeds up navigation and reduces errors.

Example:
```bash
cd /home/rishita/tutorials
```
Press **Tab** after typing part of the directory name to complete it automatically.

---

### **2. Switching to the Last Working Directory**
Use the following command to switch back to the last visited directory:
```bash
cd -
```
Example:
```bash
cd /etc/nginx
cd -   # Switches back to the previous directory
```

---

### **3. Running Multiple Commands in One Line**
- Use `;` to execute multiple commands sequentially:
  ```bash
  command1; command2; command3
  ```
  Example:
  ```bash
  whoami; pwd;
  ```
- Use `&&` to run the second command only if the first one is successful:
  ```bash
  command1 && command2
  ```

---

### **4. Reading Large Files Efficiently**
Avoid using `cat` for large files; instead, use `less` for better navigation:
```bash
less largefile.csv
```
- `less` allows searching, scrolling, and navigating efficiently.

---

### **5. Empty a File Without Deleting It**
To empty a file while retaining it:
```bash
> filename
```
Example:
```bash
> testfile
```

---

### **6. Live Monitoring for Specific Text in a File**
Monitor logs in real-time for specific keywords:
```bash
tail -f filename | grep "error"
```
Example (with sudo for system logs):
```bash
sudo tail -f /var/log/syslog | grep "error"
```

---

### **7. Recording Command Execution**
Use `script` to record all executed commands:
```bash
script
```
Perform tasks, then press **Ctrl + D** to stop recording.

Useful for:
- Recording training sessions
- Documenting system processes

---

### **8. Using the Terminal as a Calculator**
Run `bc` for calculations:
```bash
bc -l
```

---

### **9. Terminal Navigation Shortcuts**
- **Ctrl + A** → Move cursor to the start of the line
- **Ctrl + E** → Move cursor to the end of the line

---

### **10. Clearing the Terminal and Redoing Commands**
- **Ctrl + U** → Clears the terminal input
- **Ctrl + Y** → Redo last deleted input

---

### **11. Searching Previously Used Commands**
- **Ctrl + R** → Reverse search through command history

---

### **12. Clearing the Screen**
- **Ctrl + L** → Clears the terminal screen

---

### **13. Deleting Characters Efficiently**
- **Ctrl + D** → Deletes one character at a time (opposite of Backspace)

---

### **14. Switching to the Home Directory**
- Use `cd ~` to return to the home directory:
  ```bash
  cd ~
  ```

---

### **15. Viewing Command History**
- Use `history` to view frequently used commands:
  ```bash
  history
  ```
This helps in reusing commands and tracking system activities.

---


