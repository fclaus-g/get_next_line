# get_next_line - 42 Project

## Introduction

**get_next_line** is a project at 42 that focuses on reading a line of input from a file descriptor, one line at a time, until the end of the file. The goal of this project is to strengthen your understanding of file I/O, buffer management, memory allocation, and dynamic memory handling.

You are tasked with implementing the function `get_next_line` which reads a single line from a given file descriptor (including standard input) and returns it as a string, handling multiple reads and buffering data efficiently.

## Prototype

```c
char *get_next_line(int fd);
```

- `fd`: The file descriptor to read from.
- Returns: The next line from the file descriptor, or `NULL` if there's no more data or an error occurs.

## Features

- Reads a line from a file descriptor, including the newline character (`\n`).
- Manages dynamic memory to store partial reads and accumulate the complete line.
- Works with any valid file descriptor, including files and standard input (stdin).
- Handles multiple file descriptors simultaneously (if bonus part is implemented).
  
## Usage

To use `get_next_line` in your project, follow these steps:

1. Clone the repository and navigate to the project directory:

   ```bash
   git clone https://github.com/fclaus-g/get_next_line.git
   cd get_next_line
   ```

2. Compile your program with `get_next_line` by linking it with your source files:

   ```bash
   gcc -Wall -Wextra -Werror get_next_line.c get_next_line_utils.c -D BUFFER_SIZE=42 your_file.c -o your_program
   ```

   Here, `BUFFER_SIZE` is a compile-time definition that controls how much data is read in each call to `read()`. You can adjust `BUFFER_SIZE` as needed.

3. Include the `get_next_line` header in your project:

   ```c
   #include "get_next_line.h"
   ```

4. Use the function in your program to read lines from a file descriptor:

   ```c
   int fd = open("yourfile.txt", O_RDONLY);
   char *line;

   while ((line = get_next_line(fd)) != NULL)
   {
       printf("%s", line);
       free(line);
   }
   close(fd);
   ```

## Project Files

- **get_next_line.c**: Contains the core logic for reading lines from a file descriptor.
- **get_next_line_utils.c**: Utility functions to assist with memory management and string manipulation.
- **get_next_line.h**: Header file with function prototypes and necessary includes.
- **Makefile**: Automates the compilation process for testing and development.

## Bonus (Optional)

The bonus part of the project includes:

- **Multiple file descriptors**: Your `get_next_line` function should be able to handle reading from multiple file descriptors simultaneously, returning the correct line for each one.
- **Memory management improvements**: Efficiently manage and free memory to prevent leaks and ensure optimal performance.

## Example

```c
#include "get_next_line.h"
#include <fcntl.h>

int main(void)
{
    int fd = open("example.txt", O_RDONLY);
    char *line;

    while ((line = get_next_line(fd)) != NULL)
    {
        printf("%s", line);
        free(line);
    }
    close(fd);
    return 0;
}
```

## License

This project is part of the 42 curriculum and is intended for educational purposes. Feel free to use it for learning, but be mindful of 42’s collaboration policies.
