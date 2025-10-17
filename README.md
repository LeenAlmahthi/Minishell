# # 🐚 MINISHELL

> *Empowering Seamless Command, Unleashing Innovation Daily*

[![Last Commit](https://img.shields.io/github/last-commit/LeenAlmanthI/Minishell)](https://github.com/LeenAlmanthI/Minishell)
[![Language](https://img.shields.io/badge/language-C-blue.svg)](https://en.wikipedia.org/wiki/C_(programming_language))
[![42 School](https://img.shields.io/badge/42-School-000000?logo=42)](https://42.fr/)

A lightweight, customizable UNIX shell implementation created as part of the 42 School curriculum. Minishell provides a minimal yet powerful environment for command execution, environment management, and process control, all while emphasizing security and flexibility.

---

## 📋 Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Getting Started](#getting-started)
  - [Prerequisites](#prerequisites)
  - [Installation](#installation)
- [Usage](#usage)
  - [Built-in Commands](#built-in-commands)
  - [Examples](#examples)
- [Testing](#testing)
- [Technical Implementation](#technical-implementation)
- [Project Structure](#project-structure)
- [Contributing](#contributing)
- [Resources](#resources)
- [License](#license)
- [Authors](#authors)

---

## 🎯 Overview

Minishell is a lightweight shell designed for developers to build and experiment with core command-line functionalities. It provides a minimal yet powerful environment for command execution, environment management, and process control, all while emphasizing security and flexibility.

### Why Minishell?

This project aims to create a simplified shell environment that developers can extend and adapt. By building a shell from scratch, you gain deep understanding of:

- How shells parse and execute commands
- Process creation and management in UNIX systems
- Signal handling and job control
- Environment variable manipulation
- Pipeline and redirection mechanics

---

## ✨ Features

### 🔧 Command Parsing & Execution
Handles user input, pipelines, heredocs, and process management seamlessly. Supports complex command chains with proper error handling.

### 🌍 Environment & Variable Expansion
Supports dynamic content substitution and environment variable management. Includes support for `$VAR` expansion and special parameters like `$?`.

### 🔒 Security-Aware Architecture
Incorporates security zone metadata to ensure safe file and command handling. Prevents common shell vulnerabilities and validates user input.

### 📡 Signal & Process Control
Manages signals like SIGINT, SIGQUIT for a stable interactive experience. Implements proper signal handling for both interactive and non-interactive modes.

### 📁 Built-in Commands & Environment Management
Implements essential shell commands with robust internal handling:
- `echo` with `-n` option
- `cd` with relative and absolute paths
- `pwd` for current directory
- `export` for environment variables
- `unset` for variable removal
- `env` for environment display
- `exit` with exit status

---

## 🚀 Getting Started

### Prerequisites

This project requires the following:

- **Programming Language**: C
- **Compiler**: GCC or Clang
- **Operating System**: Linux or macOS
- **Libraries**: 
  - `readline` (for command-line editing)
  - Standard C library

### Installation

Follow these steps to build and install Minishell:

1. **Clone the repository:**
   ```bash
   git clone https://github.com/LeenAlmanthI/Minishell.git
   ```

2. **Navigate to the project directory:**
   ```bash
   cd Minishell
   ```

3. **Build the project:**
   ```bash
   make
   ```

4. **Clean build files (optional):**
   ```bash
   make clean    # Remove object files
   make fclean   # Remove object files and executable
   make re       # Rebuild everything
   ```

---

## 💻 Usage

### Running Minishell

Start the shell with:

```bash
./minishell
```

Once running, you'll see a prompt where you can enter commands just like in bash or zsh.

### Built-in Commands

Minishell supports the following built-in commands:

| Command | Description | Example |
|---------|-------------|---------|
| `echo` | Display text (supports `-n` flag) | `echo -n "Hello"` |
| `cd` | Change directory | `cd /home/user` |
| `pwd` | Print working directory | `pwd` |
| `export` | Set environment variables | `export PATH=/usr/bin` |
| `unset` | Remove environment variables | `unset PATH` |
| `env` | Display environment variables | `env` |
| `exit` | Exit the shell | `exit 0` |

### Examples

```bash
# Simple command execution
minishell$ ls -la

# Pipelines
minishell$ cat file.txt | grep "pattern" | wc -l

# Redirections
minishell$ echo "Hello World" > output.txt
minishell$ cat < input.txt

# Heredoc
minishell$ cat << EOF
> Line 1
> Line 2
> EOF

# Environment variables
minishell$ export MY_VAR="Hello"
minishell$ echo $MY_VAR

# Exit status
minishell$ ls nonexistent
minishell$ echo $?
```

---

## 🧪 Testing

Minishell uses a custom testing framework to ensure reliability.

### Running Tests

Execute the test suite with:

```bash
make test
```

### Test Coverage

The test suite covers:
- ✅ Command parsing and execution
- ✅ Pipeline functionality
- ✅ Redirections (input, output, append)
- ✅ Heredoc implementation
- ✅ Environment variable expansion
- ✅ Built-in commands
- ✅ Signal handling
- ✅ Error conditions and edge cases
- ✅ Memory leak detection

---

## 🔍 Technical Implementation

### Architecture Overview

```
┌─────────────────────────────────────────────────────┐
│                   User Input                        │
└──────────────────┬──────────────────────────────────┘
                   │
                   ▼
┌─────────────────────────────────────────────────────┐
│              Lexer & Tokenizer                      │
│  (Breaks input into tokens: commands, operators)    │
└──────────────────┬──────────────────────────────────┘
                   │
                   ▼
┌─────────────────────────────────────────────────────┐
│                  Parser                             │
│  (Builds command structure and validates syntax)    │
└──────────────────┬──────────────────────────────────┘
                   │
                   ▼
┌─────────────────────────────────────────────────────┐
│                Expander                             │
│  (Handles variable expansion and quotes)            │
└──────────────────┬──────────────────────────────────┘
                   │
                   ▼
┌─────────────────────────────────────────────────────┐
│                Executor                             │
│  (Executes commands, manages processes)             │
└─────────────────────────────────────────────────────┘
```

### Key Components

- **Lexer**: Tokenizes input into meaningful units
- **Parser**: Builds abstract syntax tree from tokens
- **Expander**: Handles variable and wildcard expansion
- **Executor**: Manages process creation and execution
- **Signal Handler**: Handles SIGINT, SIGQUIT appropriately

---

## 📁 Project Structure

```
Minishell/
├── src/
│   ├── parsing/        # Lexer and parser implementation
│   ├── execution/      # Command execution logic
│   ├── builtins/       # Built-in command implementations
│   ├── expansion/      # Variable expansion
│   ├── signals/        # Signal handling
│   └── utils/          # Helper functions
├── include/            # Header files
├── libft/              # Custom C library (if used)
├── tests/              # Test files
├── Makefile            # Build configuration
└── README.md           # This file
```

---

## 🤝 Contributing

Contributions are welcome! If you'd like to improve Minishell:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/improvement`)
3. Commit your changes (`git commit -am 'Add new feature'`)
4. Push to the branch (`git push origin feature/improvement`)
5. Open a Pull Request

Please ensure your code follows the 42 School norm and includes appropriate tests.

---

## 📚 Resources

Helpful resources for understanding shell implementation:

- [GNU Bash Manual](https://www.gnu.org/software/bash/manual/)
- [POSIX Shell Command Language](https://pubs.opengroup.org/onlinepubs/9699919799/utilities/V3_chap02.html)
- [Advanced Programming in the UNIX Environment](https://stevens.netmeister.org/631/)
- [Writing Your Own Shell](https://www.cs.purdue.edu/homes/grr/SystemsProgrammingBook/Book/Chapter5-WritingYourOwnShell.pdf)

---

## 📄 License

This project is part of the 42 School curriculum and follows their academic policies.

---

## 👥 Authors

- **Leen Almanthi** - [GitHub Profile](https://github.com/LeenAlmanthI)
- *Add collaborators here*

---

## 🎓 42 School Project

This project is part of the 42 School common core curriculum. It aims to deepen understanding of:
- Process creation and management
- File descriptors and I/O redirection
- Signal handling
- Memory management
- System calls

**Grade**: *[Insert your grade here]*

---

<div align="center">

**⭐ If you found this project helpful, please consider giving it a star! ⭐**

Made with ❤️ at [42 School](https://42.fr/)

</div>
