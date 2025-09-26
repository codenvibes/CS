---
tags:
  - CAPT
  - OPERATING_SYSTEMS_FUNDAMENTALS
aliases:
---
## Introduction

Welcome to the beginning of our journey into the Linux operating system. In this section, we aim to introduce the fundamental concepts, history, significance of Linux in the modern computing landscape, and the core principles underpinning this powerful operating system.
<div>
<br>
</div>

### What is Linux?

Linux is a free and open-source operating system (OS) developed by Linus Torvalds in 1991 and continues to evolve. Since then, Linux has become a global phenomenon, powering everything from supercomputers to servers, mobile phones to personal computers. Known for its stability, security, and flexibility, Linux is a popular choice for both personal and professional use.
<div>
<br>
</div>

### The Philosophy of Linux

Linux embodies the spirit of collaboration and freedom. Its development reflects the following principles:

- **Freedom:** Linux gives users the freedom to control, modify, and redistribute their software. This fosters an environment of innovation and security.

- **Collaboration:** Thousands of developers worldwide contribute to Linux, keeping it sharp, secure, and responsive to user needs.

- **Transparency:** The open-source nature of Linux provides a level of transparency unmatched by proprietary systems.
<div>
<br>
</div>

### How Does Linux Work?

Linux is an operating system similar to Windows or macOS but differs in how it works and its free, open-source nature. At its core lies the Linux kernel, which is the central component of the system. The kernel is responsible for managing the computer's hardware, such as the CPU, memory, and peripherals, and allows all software applications to interact with the physical hardware.

The kernel acts as a bridge between software applications and the computer hardware. When a software application wants to do something hardware-related, like save a file or display something on the screen, it sends a request to the kernel. The kernel translates this request into instructions that the hardware can understand.

Linux supports multi-tasking and multi-user environments. This means multiple users can use the system simultaneously, and each can run multiple programs at the same time. This is especially useful in server environments where many people need to access the same system for different tasks.

The Linux file system is hierarchically organized, starting from the root directory (denoted as "/") and expanding into sub-directories. This organization makes it easy to manage and locate files.

Around the kernel, there are many software tools and libraries that add extra functionality. These can include graphical user interfaces (GUIs), system utilities, and application software. Users can mix and match these components to create a Linux distribution that meets their specific needs. Linux distributions package the kernel with a selection of software to provide a complete operating system ready for use. Popular Linux distributions include Ubuntu, Fedora, and CentOS.
<div>
<br>
</div>

### Linux Architecture

The Linux operating system is composed of several layers that manage the computer's resources and facilitate user interaction:

![](https://storage.hackviser.com/file/hackviser-prod/trainings/sections/images/68a4d2f6-4913-4850-b2cd-ec08a7918b4c/linux-layers-a4d3a0334.webp)

1. **Hardware Layer**: This is the physical foundation of the system, composed of the computer's processor (CPU), memory (RAM), storage (hard disks), and peripherals such as keyboards, mice, and printers.

2. **Kernel Layer**: The kernel is the heart of Linux and is vital to the operating system. It acts as an intermediary between software and hardware. The kernel manages tasks such as memory allocation, process scheduling (deciding when and what tasks the CPU should execute), and handling input/output requests from software. This layer ensures that different programs and users running on the system do not interfere with each other and have the necessary resources to operate.

3. **Shell Layer**: The shell is the user interface for accessing the services of the kernel. It is commonly a command-line interface (CLI) where users type commands, but graphical shells also exist. The shell allows users to interact with the kernel to run programs, manage files, and request other services by typing commands or using a graphical interface.

4. **System Utility Layer**: This layer contains various tools and applications necessary for performing tasks on the computer. System utilities can range from file management tools to software installers, network configuration tools, and more. They serve as a bridge between the user's commands (entered in the shell or through a graphical interface) and the kernel's handling of those commands.

In summary, Linux architecture organizes the interaction between the computer's hardware and user activities from physical components to software applications through a well-defined management and control layer.
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## Linux Distributions

Linux is not a single operating system but a family of open-source operating systems built around the Linux kernel. These variants are known as "distributions" or "distros." Each distribution offers a different flavor of Linux tailored for various types of users, devices, and purposes. This section explores the concept of Linux distributions, their importance, and examples of popular distros.
<div>
<br>
</div>

### What are Linux Distributions?

A Linux distribution is a complete operating system built around the Linux kernel. It includes the kernel, a wide array of software applications, libraries, and optionally a graphical user interface (GUI). Distros are developed by various organizations, communities, and even individuals, focusing on different needs such as usability, stability, security, or customization.
<div>
<br>
</div>

### Why Are There Different Distributions?

The diversity of Linux distributions stems from the philosophy of freedom and flexibility. Different users have different needs, ranging from personal computers to servers, from beginners to experts, and from lightweight systems for older hardware to feature-rich environments for modern machines. Distributions meet these varied requirements by offering specialized software packages, user interfaces, and management tools.
<div>
<br>
</div>

### Core Components of a Distribution

While each distribution offers unique features and software, they all share several core components:

- **Linux Kernel**: The heart of the operating system, managing hardware resources.
- **System Libraries**: Essential for running applications, providing standard ways to interact with the kernel.
- **Software Applications**: Ranging from system utilities to end-user applications.
- **Package Manager**: A tool for installing, updating, and managing software applications and components.
- **Bootloader**: Software that manages the boot process of the computer after power is turned on.
- **Graphical User Interface (GUI)**: Optional, but most distros offer a GUI for ease of use, such as GNOME, KDE, or XFCE.
<div>
<br>
</div>

### Popular Linux Distributions

#### Ubuntu

- **Target Audience**: Beginner and regular desktop users.
- **Features**: User-friendly, strong focus on ease of installation and usability. Extensive documentation and community support.
- **Use Cases**: Desktops, servers, and cloud environments.

#### Fedora

- **Target Audience**: Developers and system administrators.
- **Features**: Cutting-edge technology, close alignment with the Linux community, strong emphasis on free software.
- **Use Cases**: Development, servers, and workstations.

#### CentOS

- **Target Audience**: Servers and enterprise users.
- **Features**: Stability and long-term support, binary compatibility with RHEL (Red Hat Enterprise Linux).
- **Use Cases**: Servers, enterprise environments.

#### Debian

- **Target Audience**: Advanced users and environments focusing on stability.
- **Features**: Large package repository, strict free software guidelines, stability.
- **Use Cases**: Servers, desktops, embedded systems.

#### Arch Linux

- **Target Audience**: Experienced users and enthusiasts.
- **Features**: Rolling release model, user-centric approach focusing on customization and minimalism.
- **Use Cases**: Desktops, development, personal servers.

#### Kali Linux

- **Target Audience**: Security professionals and ethical hackers.
- **Features**: Preloaded with a wide range of tools for penetration testing, security research, computer forensics, and reverse engineering.
- **Use Cases**: Security research, penetration testing, and ethical hacking.
<div>
<br>
</div>

### Choosing the Right Distribution

Choosing the right distribution depends on your specific needs, level of expertise, and preferences. Consider the following factors:

- **Purpose**: Desktop use, server, development, etc.
- **Ease of Use**: Is it beginner-friendly or requires Linux expertise?
- **Support and Community**: Access to documentation, forums, and community support.
- **Hardware Compatibility**: Supports your hardware, especially for older or specialized equipment.
- **Software Availability**: Availability of the software packages you need.

In conclusion, Linux distributions offer a wide range of choices for users of all levels and purposes. By understanding the unique features and target audiences of each distro, you can select the one that best meets your needs.
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## Linux Shell

The Linux shell is a unique program that acts as a bridge between the user and the services of the operating system. It takes commands entered in a human-readable format, such as text typed on a keyboard or stored in a file, and translates them into a form that the operating system's kernel can process. The shell functions essentially as a command-language interpreter, executing these instructions. It becomes active automatically when users log into their accounts or start a terminal session.

In Linux, there are two main types of shells: **Command Line** and **Graphical Interface**.
<div>
<br>
</div>

### Command Line

The command-line shell is accessible to users through a text-based interface. Users can enter commands into a specific application known in Linux as the Terminal. Commands like `cat`, `ls`, and others are written into this interface, processed, and executed. The results of these commands are displayed directly in the terminal window.

A terminal on Linux looks like this:

![](https://storage.hackviser.com/file/hackviser-prod/trainings/sections/images/68a4d2f6-4913-4850-b2cd-ec08a7918b4c/terminal-example-2fe48b7c6.webp)

In the given screenshot, the

`ls`

command is executed with the

`-l`

option. This command lists all files in the current directory in a long format.

Using the command line can be challenging at first because remembering commands might be difficult. However, its power lies in its flexibility and strength; users can compile scripts and execute them simultaneously, making it easy to automate repetitive tasks. In the Linux context, these scripts are often referred to as shell scripts.
<div>
<br>
</div>

### Graphical Interface

The graphical interface offers a user-friendly way to interact with programs. It allows users to perform actions like opening, closing, moving, and resizing windows without needing to type commands. Operating systems like Windows or Ubuntu provide a graphical interface to simplify user interaction with the system.

A graphical interface on a typical Linux system looks like this:

![](https://storage.hackviser.com/file/hackviser-prod/trainings/sections/images/68a4d2f6-4913-4850-b2cd-ec08a7918b4c/gui-example-50294f77d.webp)

Linux operating systems offer various shells, each with unique features and command syntax:

- **BASH (Bourne Again SHell)**: The most widely used Linux shell, serving as the default shell on Linux and macOS. BASH is known for its comprehensive scripting capabilities and extensive support.
    
- **CSH (C Shell)**: The syntax and usage of C Shell are similar to the C programming language, making it appealing for users familiar with C.
    
- **KSH (Korn Shell)**: The Korn Shell, which forms the basis for the POSIX Shell standard features, combines elements from BASH and CSH, offering powerful scripting abilities and command-line editing features.
    
- **ZSH (Z Shell)**: ZSH incorporates features from BASH, KSH, and TCSH, offering robust auto-completion functions, customizable prompts, and numerous plugins and themes through frameworks like Oh My Zsh.
    
- **Fish (Friendly Interactive SHell)**: Known for its user-friendly interface, Fish provides features like syntax highlighting, auto-suggestions, and tab completions without requiring additional configuration.
    

While all these shells perform the basic task of command interpretation, they vary in the specific commands they support, built-in functionalities, and scripting capabilities, allowing users to choose the shell that best fits their preferences and needs.
<div>
<br>
</div>

### What is a Terminal?

The terminal application serves as a gateway for users to interact with the shell, providing a text-based interface where commands can be entered and their outputs viewed. It is a critical tool for executing commands directly and is also used to run larger scripts designed to automate and perform repetitive and complex tasks.

To open the terminal, you can usually find it by typing 'terminal' into the search box in the graphical interface and launching it by double-clicking the result.

![](https://storage.hackviser.com/file/hackviser-prod/trainings/sections/images/68a4d2f6-4913-4850-b2cd-ec08a7918b4c/terminal-searchbox-2440dfcad.webp)
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## Navigating Directories
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## File and Directory Operations
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## Methods of Finding Files and Directories in Linux
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## Text Editing
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## Filters
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## Package Management
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## User Management
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## Group Management
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## Permissions
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## Process Management
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## Network Management
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## Exam
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## References

https://app.hackviser.com/academy/trainings/linux-fundamentals
