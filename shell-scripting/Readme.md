
**1. Understanding Shell Scripting**
- **Purpose**: Writing a series of commands in a file (script) to automate manual activities on Linux systems.
- **Use Cases**:
  - Automating file creation.
  - Automating system health checks.
  - Printing large sequences of numbers.
  - Repeating CLI activities without manual input.
  - Creating thousands of files quickly using `touch`.
- **Benefits**:
  - Reduces manual effort.
  - Monitoring and alerting.
  - Enables scalability in infrastructure management.
  - Ensures consistency in task execution.
---

**2. Basic Commands for Shell Scripting**

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

**3. File Editing with Vim**
- **Opening Files**: `vi filename.sh`
- **Insert Mode**: Press `Esc` → `i`
- **Saving and Exiting**:
  - Save & quit: `Esc` → `:wq`
  - Quit without saving: `:q!`
- **Best Practice**:
  - Use `touch` for mass automation.
  - Use Vim for manual content editing.

---

**4. Shebang (#!)**
- **Definition**: First line in a script, e.g., `#!/bin/bash`
- **Purpose**: Specifies which shell interpreter executes the script.
- **Common Choices**:
  - `#!/bin/bash` – Recommended, supports advanced Bash features.
  - `#!/bin/sh` – May point to `bash` or `dash` depending on the system (affects compatibility).
- **Tip**: Always specify `#!/bin/bash` for predictable results across different systems.

---

**5. Writing a Simple Script**
**Example Script**:
```bash
#!/bin/bash
echo "My name is Jai"
```
- **Notes**:
  - Use `echo` to print output to the terminal (similar to `print` in Java/Python).
  - Comment lines with `#` for clarity and documentation.
---

**6. Executing Shell Scripts**
- **Methods**:
  - `sh script.sh` – Executes with `sh` interpreter.
  - `./script.sh` – Direct execution (requires execute permission).
- **Permissions**:
  - Set with `chmod`:
    - `chmod 777 file` → Read/Write/Execute for all.
    - Numeric values: `4` (read), `2` (write), `1` (execute).

**Permission Examples**:
- `chmod 755 script.sh` → Full for owner, read/execute for others.
- `chmod 444 file` → Read-only for everyone.

---

**7. Directory Navigation & Management**
- **Current Directory**: `pwd`
- **Change Directory**: `cd <path>` or `cd ..` to go back.
- **Create Directory**: `mkdir folder_name`

---

**8. Example Automation Script**
```bash
#!/bin/bash

#Create folder
mkdir demofolder

#Enter folder
cd demofloder

#Create files
touch first_file
touch second_file

Run: `./script.sh` after giving execute permissions.
```
---

**9. Shell Scripting for DevOps**
- **Why Important**:
  - Automates infrastructure tasks.
  - Useful for environments with limited tooling.
  - Provides custom, repeatable solutions.
- **Example Use Case**:  
  - Managing 10,000+ Linux VMs.
  - Automating CPU & memory checks.
  - Sending alerts on anomalies.

---

**10. Monitoring Node Health**
| Command | Purpose                                |
|---------|----------------------------------------|
| `nproc` | Show number of CPU cores               |
| `free`  | Display memory usage                   |
| `top`   | Real-time CPU and memory usage display |

---

**11. Advanced Topics**
- **Signal Trapping**:
  - Handle termination signals (e.g., Ctrl+C) gracefully.
- **Cron Jobs**:
  - Schedule recurring tasks.
- **Custom Monitoring**:
  - Scripts for tailored system checks and reporting.

---

**12. Best Practices**
1. Always start scripts with a shebang (`#!/bin/bash`).
2. Use comments to document intent and logic.
3. Set only necessary permissions (avoid `777` in production).
4. Test scripts in non-production environments before deployment.
5. Use descriptive file and variable names for maintainability.

---

**Learning Areas**:
- Integrating shell scripts with **cron** for automation.
- Using shell scripts in **CI/CD pipelines**.
- Secure script writing and permission management.
- Cross-shell and cross-platform script compatibility.


