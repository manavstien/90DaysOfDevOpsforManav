# Day 02 – Linux Architecture, Processes, and systemd

## 1. Linux Architecture

Linux consists of three important components:

- **Kernel:** The core of Linux. It manages hardware resources such as CPU, RAM, storage and network devices. It also manages processes, memory, filesystems and networking.
- **User Space:** The environment where applications and utilities run, such as Bash, Java, browsers and other programs.
- **Init / systemd:** The first user-space process started by the kernel. On modern Linux systems, systemd typically runs as PID 1 and manages system initialization and services.

## 2. Kernel Responsibilities

The kernel performs five major functions:

1. **Process Management:** Creates and terminates processes, schedules CPU execution, manages process states and supports inter-process communication (IPC).
2. **Memory Management:** Allocates memory, provides virtual memory, isolates processes and manages memory pressure and swapping.
3. **Device Management:** Uses device drivers to communicate with hardware such as disks, USB devices and network interfaces.
4. **Filesystem Management:** Handles files, directories, permissions, metadata and different filesystem types.
5. **Networking:** Manages networking operations such as TCP/IP communication, routing and packet processing.

## 3. Processes and Process States

A process is an instance of a program currently executing.

Linux creates processes using mechanisms such as `fork()` and `exec()`. Every process has a Process ID (PID).

Important process states:

- **R – Running:** Executing or ready to execute.
- **S – Sleeping:** Waiting for an event that can interrupt the sleep.
- **D – Uninterruptible Sleep:** Usually waiting for certain I/O operations.
- **T – Stopped:** Execution has been stopped.
- **Z – Zombie:** Process has terminated, but its parent hasn't collected its exit status.
- **I – Idle:** Idle kernel thread.

Processes can communicate using IPC mechanisms such as pipes, signals, sockets and shared memory.

## 4. systemd and Daemons

systemd is a system and service manager commonly used by modern Linux distributions.

Its responsibilities include:

- Initializing the system during boot.
- Starting and stopping services.
- Managing service dependencies.
- Monitoring service status.
- Collecting system logs through the journal.

A **daemon** is a background process that provides services without requiring direct user interaction. Examples include SSH and web server daemons.

systemd manages services through unit files, commonly ending in `.service`.

Useful commands:

- `systemctl status nginx` – Check service status.
- `systemctl start nginx` – Start a service.
- `systemctl stop nginx` – Stop a service.
- `systemctl enable nginx` – Enable automatic startup at boot.
- `journalctl -u nginx` – View service logs.

## 5. Five Daily Linux Commands

| Command | Purpose |
|---|---|
| `ps aux` | List running processes |
| `top` | Monitor CPU and memory usage |
| `free -h` | Check RAM and swap usage |
| `systemctl status SERVICE` | Check service health |
| `journalctl -u SERVICE` | Inspect service logs |

## 6. My Practical Observations

While exploring my Ubuntu machine, I discovered:

- PID 1 is running systemd.
- My system is running systemd version 259.
- Jenkins is running as a Java 21 process.
- Jenkins was identified with PID 1804.
- The OpenSSH server package was not installed.
- I explored running services, process information and system logs.

## 7. Key Takeaway

Linux kernel manages the machine's resources, processes execute applications, and systemd manages system initialization and background services.

Understanding these components is essential for troubleshooting applications, monitoring resources and managing production servers as a DevOps engineer.
