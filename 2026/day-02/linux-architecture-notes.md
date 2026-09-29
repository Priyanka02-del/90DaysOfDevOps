Linux Architecture, Processes, and systemd

1) The core components of Linux (kernel, user space, init/systemd)

The core concepts of Linux:

A] Kernel: The kernel is the core part of the Linux operating system. It acts as a bridge between the computer's physical hardware and its software applications. The kernel is the interface between hardware and software. It correctly processes commands entered by the user. The user transmits commands to the kernel through the shell. The kernel executes these commands and sends the results back to the user.
The Core Responsibilities of Kernel are as follows:
Device Management: Controls hardware devices through device drivers. 
Memory Management: Allocates and manages system memory.
Process Management: Schedules processes and controls execution.
Handling system requests.


B] Shell: It is the command-line interface that interprets and executes user commands. The user instructs the operating system by entering commands.
The shell provides a user interface that receives commands, processes them and presents the results to the user.

Some shell names used according to operating systems are as follows:
➜ Linux and Unix-like Operating Systems:
Bash (Bourne Again Shell)
Zsh (Z Shell)
Fish (Friendly Interactive Shell)
Ksh (Korn Shell)
Csh (C Shell)
➜ macOS Operating System:
Bash (Bourne Again Shell)
Zsh (Z Shell)
➜ Windows Operating System:
Command Prompt (cmd.exe)
PowerShell

C] System Libraries: System libraries provide predefined functions that allow application programs and system utilities to access kernel features without interacting with the kernel directly. They form the foundation for software development by offering reusable, standardized interfaces for system operations.

Examples:
GNU C Library (glibc): Provides core system calls and built-in functions required for executing C programs
libm (Math Library): Offers mathematical functions such as trigonometry, logarithms, and exponentiation

D] System Utilities: They are built-in tools used for system management, configuration and maintenance. For example, process management (ps, top, kill), disk and file system (df, du), networking (ip, ping).

E] Init/Systemd: SystemD is an init system and service manager used by many modern Linux distributions. The “init” part means it’s the first process that runs when your computer boots up (hence the name from “initialization”). The service manager part means it controls which services (like network managers, web servers, etc.) are running and how they interact.

G] User space: 
Kernel Mode (Ring 0): This is the most privileged mode. When the CPU is executing kernel code, it has direct, unrestricted access to all hardware components, including the CPU, physical memory, and I/O devices. The kernel is the most trusted and powerful component of the system.

User Mode (Ring 3): This is the unprivileged mode where all user applications run. Code executed here has limited access to system resources and cannot directly manipulate hardware. All user programs and their libraries operate within this mode.

In embedded systems, the operating system consists of two distinct spaces: user space and kernel space. User space is where applications and processes run, while kernel space is where the operating system’s core functions, device drivers, and hardware interactions take place. The primary role of the C library is to bridge the gap between these two spaces, facilitating communication and ensuring efficient interactions.
Understanding User Space and Kernel Space.

2) How processes are created and managed

A process is simply a running instance of a program. When you execute any command, Linux loads the program into memory and creates a process to execute it.

Every process has:

-A unique Process ID (PID)

-Memory allocation

-CPU usage

-Execution state

-Parent process

Linux uses processes to perform all tasks, from system operations to user applications.

Linux processes can run in two modes.

-Foreground Process
Runs directly in the terminal and occupies it until completion. Example: running a command manually.

-Background Process
Runs independently without blocking the terminal. Useful for long-running tasks such as servers, scripts, or updates.

Background processing allows multitasking and efficient system use.

Two more states of process: 

-Zombie Process
A process that has completed execution but still appears in the process table because its parent has not collected its status.

-Orphan Process
A process whose parent has terminated. Linux automatically assigns such processes to the init/system process to maintain stability.

Process Management:

Process management is used daily in:

Managing web servers

Running databases

Handling system services

Monitoring application performance

Automating scripts and background jobs

Maintaining production servers

Without proper process management, systems can become slow, unstable, or unresponsive.

3) What systemd does and why it matters?

SystemD is an init system and service manager used by many modern Linux distributions. The “init” part means it’s the first process that runs when your computer boots up (hence the name from “initialization”). The service manager part means it controls which services (like network managers, web servers, etc.) are running and how they interact.

Importance of systemd

-Acts as PID 1: Runs as the very first user-space process started by the kernel, responsible for launching and supervising all other processes.
-Manages Services: Starts, stops, and restarts background daemons and programs using the systemctl utility.
-Parallel Startup: Boots the computer faster by launching independent services simultaneously instead of one after another.
-Tracks Dependencies: Understands which programs need other services to run first and sets up systems in the correct order.
-Monitors Health: Keeps watch over active processes and automatically restarts services if they crash.
-Handles Logging: Collects and indexes system event logs through systemd-journald, queryable via journalctl.

4) Explain **process states** (running, sleeping, zombie, etc.)

Running - The process is actively using CPU

Sleeping - Waiting for input or resource

Stopped - Paused manually or by system

Zombie - Completed but still listed in process table

Terminated: The process is fully finished, resources are cleaned up.

5) List **5 commands** you would use daily

PWD
CD
LS
Clear
Top


