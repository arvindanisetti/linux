# Shell Scripting – Comprehensive Guide 
---
## **1. Understanding Shell Scripting**
- **Purpose**: Writing a series of commands in a file (script) to automate manual activities on Linux systems.
- **Use Cases**:
  - Automating file creation.
  - Printing large sequences of numbers.
  - Repeating CLI activities without manual input.
- **Benefits**:
  - Reduces manual effort.
  - Enables scalability in infrastructure management.
  - Ensures consistency in task execution.
---

## **2. Automation in DevOps**
- **Importance**: Key driver for efficiency in modern infrastructure operations.
- **Examples**:
  - Creating thousands of files quickly using `touch`.
  - Automating system health checks.
- **Role in DevOps**:
  - Infrastructure maintenance.
  - Code management (e.g., Git operations).
  - Configuration automation.
  - Monitoring and alerting.

---

## **3. Basic Commands for Shell Scripting**

| Command   | Usage Description             | Example                                    |
|-----------|-------------------------------|--------------------------------------------|
| `ls`      | List files/directories        | `ls -ltr` for detailed view sorted by time |
| `touch`   | Create empty file(s)          | `touch first_shell_script.sh`              |
| `man`     | View command manual/help      | `man ls`                                   |
| `vi`      | Edit files interactively      | `vi script.sh`                             |
| `cat`     | Display file content          | `cat script.sh`                            |
| `pwd`     | Show current directory        | `pwd`                                      |
| `mkdir`   | Create a new directory        | `mkdir my_folder`                          |
| `cd`      | Change directory              | `cd my_folder`, `cd ..`                    |
| `history` | View previously used commands | `history`                                  |
| `chmod`   | Change file permissions       | `chmod 755 script.sh`                      |

---

## **4. File Editing with Vim**
- **Opening Files**: `vi filename.sh`
- **Insert Mode**: Press `Esc` → `i`
- **Saving and Exiting**:
  - Save & quit: `Esc` → `:wq`
  - Quit without saving: `:q!`
- **Best Practice**:
  - Use `touch` for mass automation.
  - Use Vim for manual content editing.

---

## **5. Shebang (#!)**
- **Definition**: First line in a script, e.g., `#!/bin/bash`
- **Purpose**: Specifies which shell interpreter executes the script.
- **Common Choices**:
  - `#!/bin/bash` – Recommended, supports advanced Bash features.
  - `#!/bin/sh` – May point to `bash` or `dash` depending on the system (affects compatibility).
- **Tip**: Always specify `#!/bin/bash` for predictable results across different systems.

---

## **6. Writing a Simple Script**
**Example Script**:
```bash
#!/bin/bash
echo "My name is Abhishek"
```
- **Notes**:
  - Use `echo` to print output to the terminal (similar to `print` in Java/Python).
  - Comment lines with `#` for clarity and documentation.


