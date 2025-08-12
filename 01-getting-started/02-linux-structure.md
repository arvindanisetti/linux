# Core components of a Linux Machine

```plaintext
+----------------------------------------------------+
| User Applications (Vim, Docker, Apache, etc.)     |
+----------------------------------------------------+
| Shell (Bash, Zsh, Fish, etc.)                     |  <-- Part of the OS
+----------------------------------------------------+
| System Libraries (glibc, libc, OpenSSL, etc.)     |  <-- Part of the OS
+----------------------------------------------------+
| System Utilities (ls, grep, systemctl, etc.)      |  <-- Part of the OS
+----------------------------------------------------+
| Linux Kernel (Process, Memory, FS, Network)       |  <-- Core of the OS
+----------------------------------------------------+
| Hardware (CPU, RAM, Disk, Network, Peripherals)   |
+----------------------------------------------------+

(a) Hardware Layer

🔹 The physical components of the computer (CPU, RAM, disk, network interfaces, etc.).
🔹 The OS interacts with hardware using device drivers.

(b) Kernel (Core of Linux OS)

🔹 The Linux Kernel is responsible for directly managing system resources, including:

    Process Management – Schedules processes and handles multitasking.

    Memory Management – Allocates and deallocates RAM efficiently.

    Device Drivers – Acts as an interface between software and hardware.

    File System Management – Manages how data is stored and retrieved.

    Network Management – Handles communication between systems.

(c) Shell (Command Line Interface - CLI)

🔹 A command interpreter that allows users to interact with the kernel.
🔹 Examples: Bash, Zsh, Fish, Dash, Ksh.
🔹 Converts user commands into system calls for the kernel.

(d) User Applications

🔹 End-user programs like web browsers, text editors, DevOps tools, etc.
🔹 Applications interact with the OS using system calls via the shell or GUI.

(e) System Libraries

🔹 Provide the APIs and runtime support for applications and utilities.
🔹 Examples: glibc (GNU C Library), libm, OpenSSL, which provide critical functionalities like standard input/output, math operations, cryptography, and networking.
🔹 Act as a bridge between user applications and the kernel system calls, simplifying development.
🔹 Libraries enable portability of applications across different Linux distributions.

(f) System Utilities

🔹 These are basic command-line tools and programs that facilitate system management and user tasks.
🔹 System utilities often come from the GNU coreutils or other essential packages.
🔹 They are crucial for Linux administration, scripting, and automation.
    
    File operations: ls, cp, mv, rm

    Text processing: grep, awk, sed

    Process management: ps, top, systemctl

    Networking: ping, ip, netstat
