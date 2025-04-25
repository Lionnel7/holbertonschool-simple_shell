![Logo](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTob-PjCKECdAeaKJ2385YR9AKZhyGR30ngAw&s)
![Header](https://raw.githubusercontent.com/Lionnel7/holbertonschool-simple_shell/refs/heads/Lionnel7/readme_header.jpg)

# Holberton School - Simple Shell Project

This program, made as a project for Holberton School, creates a basic command-line tool that allows users to interact with the operating system. It enables the execution of a limited set of built-in commands, as well as external programs, both interactively and in non-interactive modes.

This project provides a valuable learning experience in key shell programming concepts like understanding how commands are interpreted and processed, learning how to manage the execution of programs, understanding how the program responds to user input and system signals, and exploring how the program interacts with the operating system.

This basic shell replicates some core functionalities of a standard UNIX shell. It serves as a foundation for understanding the fundamental principles of how shell interpreters work and provides a starting point for exploring more advanced shell features.


## 📋 Project Requirements

Here’s a summarized version of the general requirements for this project:

- All your files will be compiled on Ubuntu 20.04 LTS using [gcc](https://gcc.gnu.org/install/)
- All your files should end with a new line
- Your code should use the [Betty](https://github.com/hs-hq/Betty) style
- Your shell should not have any memory leaks
- No more than 5 functions per file
- All your header files should be include guarded
- Use system calls only when you need to
## 🚀 Get Started

#### Prerequisites
- A UNIX-like operating system (Linux, macOS, etc.)
- GCC compiler

#### 1. Clone the repository
```
git clone https://github.com/Lionnel7/holbertonschool-simple_shell.git
```

#### 2. Navigate to the project directory
```
cd holbertonschool-simple_shell/
```

#### 3. Compile the program
```
gcc -Wall -Werror -Wextra -pedantic -std=gnu89 *.c -o hsh
```


## ‍💻 Usage

This simple shell can be used in two modes:

#### Interactive mode
Running the shell program with `./hsh` , it prints a prompt `simple_shell:~$` and waits for user's input to execute the command. To exit the shell `exit` must be typed.

Example:
```
root@DonGilles:~/holbertonschool-simple_shell# ./hsh
simple_shell:~$ ls -l
total 60
-rw-r--r-- 1 root root   158 Apr 23 11:56 AUTHORS
-rw-r--r-- 1 root root  5995 Apr 23 12:40 README.md
-rw-r--r-- 1 root root  1525 Apr 17 10:07 builtin_cmds.c
-rw-r--r-- 1 root root  1647 Apr 17 10:36 exec_cmd.c
-rwxr-xr-x 1 root root 21912 Apr 23 12:49 hsh
-rw-r--r-- 1 root root  2594 Apr 17 10:48 input_handlers.c
-rw-r--r-- 1 root root  2887 Apr 23 11:53 man_1_simple_shell
-rw-r--r-- 1 root root  1031 Apr 23 12:49 shell.c
-rw-r--r-- 1 root root  1188 Apr 23 11:58 shell.h
-rw-r--r-- 1 root root  2080 Apr 23 11:58 utils.c
simple_shell:~$ exit
root@DonGilles:~/holbertonschool-simple_shell#
```

#### Non-Interactive Mode
The shell reads commands from a file or pipe and commands are executed sequentially.

Examples:
```
root@DonGilles:~/holbertonschool-simple_shell# cat test.txt
echo HELLO FAM
 ls -la
root@DonGilles:~/holbertonschool-simple_shell# ./hsh < test.txt
HELLO FAM
total 60
drwxr-xr-x 1 root root   512 Apr 23 12:59 .
drwx------ 1 root root   512 Apr 23 12:59 ..
drwxr-xr-x 1 root root   512 Apr 23 12:17 .git
-rw-r--r-- 1 root root   158 Apr 23 11:56 AUTHORS
-rw-r--r-- 1 root root  5984 Apr 23 12:55 README.md
-rw-r--r-- 1 root root  1525 Apr 17 10:07 builtin_cmds.c
-rw-r--r-- 1 root root  1647 Apr 17 10:36 exec_cmd.c
-rwxr-xr-x 1 root root 21912 Apr 23 12:49 hsh
-rw-r--r-- 1 root root  2594 Apr 17 10:48 input_handlers.c
-rw-r--r-- 1 root root  2887 Apr 23 11:53 man_1_simple_shell
-rw-r--r-- 1 root root  1031 Apr 23 12:49 shell.c
-rw-r--r-- 1 root root  1188 Apr 23 11:58 shell.h
-rw-r--r-- 1 root root    24 Apr 23 12:59 test.txt
-rw-r--r-- 1 root root  2080 Apr 23 11:58 utils.c
root@DonGilles:~/holbertonschool-simple_shell#
```
## ⚙️ Built-in Commands

This shell supports the following built-in commands:

| Command | Description                |
| :-------- | :------------------------- |
| `exit` | Exits the shell. Optional usage: `exit <exit code>` |
| `env` | Prints the current environment variables. No options are allowed.|

## ⚠️ Error Handling

The shell implements basic error handling to provide informative messages to the user and appropriate exit codes.

#### Command not found
If an unknown command is entered, the shell displays a message indicating the command was not found with an exit code: `127`

```
./hsh: 1: cmd: not found
```
#### Permission denied
If the shell tries to execute a file that the user does not have permission to execute, it will display a permission denied error with an exit code: `126`

```
./hsh: 1: ./no_permissions: permission denied
```
#### Invalid command argument
If an unknown command option is entered, the shell displays a message indicating the invalid option with an exit code: `2`
```
ls: invalid option -- 'z'
Try 'ls --help' for more information.
```
#### EXIT Built-in command error
If a non number or negative number option is entered, the shell displays a message indicating the illegal number with an exit code: `2`
```
./hsh: 1: exit: Illegal number: -1
- or -
./hsh: 1: exit: Illegal number: arg
```
#### ENV Built-in command error
As the env built-in command is a limited version that not handles any options. If any option is entered, the shell displays a message indicating the invalid option with an exit code: `125`
```
env: invalid option -- '-l'
```

## 👉 Limitations
This simple shell has the following limitations:

- No other built-in commands except: exit and env
- No handling the commands separator ;
- No handling the && and || shell logical operators
- No handling variables replacement
- No handling comments (#)
- No handling complex error outputs
- File as input: this simple shell can take a file as a command line argument, but the feature is not entirely completed.
## 💻 Man Page

Command for execute the Man Page: 

```man ./man_1_simple_shell```

https://github.com/Lionnel7/holbertonschool-simple_shell/blob/Dan/man_1_simple_shell
## 🔁 Flowchart
![Flowchart](https://i.ibb.co/Hh9jGR3/Flowchart-Printf-1.png)

## 👥 Authors

Pierre Lionnel Obiang  [Github](https://github.com/Lionnel7)
Dan Florentin Ishimwe | [Github](https://github.com/danish872)
