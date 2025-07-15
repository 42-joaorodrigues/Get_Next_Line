# Get Next Line

![42 Badge](https://img.shields.io/badge/42-Get_Next_Line-brightgreen)
![C Badge](https://img.shields.io/badge/Language-C-blue)
![Status Badge](https://img.shields.io/badge/Status-Completed-success)

## Project Details

For full project requirements, see the [Subject File](./subject.md).

## Multiple Implementations

This repository contains **two distinct implementations** of the `get_next_line` project:

- **Buffer-based version** (`get_next_line_buffer/`):
  - Uses a static buffer to manage reading and returning lines efficiently.
  - Simpler memory management, suitable for most use cases.

- **Linked list-based version** (`get_next_line_linkedlist/`):
  - Uses a linked list to store file chunks, allowing for flexible and robust line assembly.
  - Handles very large or fragmented lines more gracefully.

Each version includes its own set of mandatory and bonus files. You can explore and test both to compare their approaches and performance.

## What I Learned

Through this project at 42 School, I developed essential programming skills and knowledge:

- **Static variables in C** – Learned how to use static variables to maintain state between function calls
- **File descriptor management** – Gained experience reading from files and standard input using file descriptors
- **Efficient buffer handling** – Implemented logic to read as little as possible per call, optimizing memory and performance
- **Dynamic memory allocation** – Practiced safe allocation and freeing of memory to avoid leaks
- **String and buffer manipulation** – Handled partial reads, line splitting, and buffer concatenation
- **Linked list data structures** – Built a version using linked lists for advanced memory management
- **Robust error handling** – Managed edge cases such as EOF, errors, and invalid input
- **Modular programming** – Structured code into reusable functions and clear interfaces
- **Defensive programming** – Validated inputs and handled unexpected scenarios gracefully

This project reinforced my attention to detail, problem-solving abilities, and low-level programming skills that are transferable to any software development role.

## About the Project

Get Next Line is a C function that reads and returns a line from a file descriptor, including the newline character if present. It is designed to:

- Read files or standard input one line at a time
- Work with any buffer size (set via `-D BUFFER_SIZE`)
- Handle multiple file descriptors (bonus)
- Avoid memory leaks and undefined behavior

## Implementation Details

Each implementation consists of the following main files:

- `get_next_line.c` – Main function implementation
- `get_next_line_utils.c` – Helper functions for string and buffer operations
- `get_next_line.h` – Function prototypes and macros
- `get_next_line_bonus.c`, `get_next_line_bonus.h`, `get_next_line_utils_bonus.c` – Bonus: support for multiple file descriptors

### Key Features

- Uses a static variable to retain buffer state between calls (buffer version)
- Uses a linked list to store file chunks (linked list version)
- Returns each line including the `\n` character (if present)
- Handles end-of-file and error conditions gracefully
- Bonus: manages independent buffers for multiple file descriptors

## Usage

Choose the implementation you want to use:

1. **Buffer-based version**
   - Source files: `get_next_line_buffer/`
   - To use: Copy the files from this directory into your project or compile them directly with your C compiler.

2. **Linked list-based version**
   - Source files: `get_next_line_linkedlist/`
   - To use: Copy the files from this directory into your project or compile them directly with your C compiler.

### Example Compilation

To compile either implementation, you will need to provide your own `main.c` file. Here is a minimal example:

```c
#include "get_next_line.h"
#include <fcntl.h>
#include <stdio.h>

int main(void)
{
    int fd = open("file.txt", O_RDONLY);
    char *line;
    while ((line = get_next_line(fd)))
    {
        printf("%s", line);
        free(line);
    }
    close(fd);
    return 0;
}
```

### Compilation Commands

```bash
# Compile the buffer-based version
cc -Wall -Wextra -Werror -D BUFFER_SIZE=42 get_next_line_buffer/get_next_line.c get_next_line_buffer/get_next_line_utils.c main.c -Iget_next_line_buffer -o gnl_buffer

# Compile the linked list-based version
cc -Wall -Wextra -Werror -D BUFFER_SIZE=42 get_next_line_linkedlist/get_next_line.c get_next_line_linkedlist/get_next_line_utils.c main.c -Iget_next_line_linkedlist -o gnl_linkedlist

# For bonus (multi-fd) support, add the _bonus files instead
cc -Wall -Wextra -Werror -D BUFFER_SIZE=42 get_next_line_buffer/get_next_line_bonus.c get_next_line_buffer/get_next_line_utils_bonus.c main.c -Iget_next_line_buffer -o gnl_buffer_bonus
cc -Wall -Wextra -Werror -D BUFFER_SIZE=42 get_next_line_linkedlist/get_next_line_bonus.c get_next_line_linkedlist/get_next_line_utils_bonus.c main.c -Iget_next_line_linkedlist -o gnl_linkedlist_bonus
```

You can then run the resulting executable. Make sure to provide your own `main.c` or use the example above.

## Technical Challenges Overcome

- **Managing partial reads** – Ensured lines are returned as soon as a newline is encountered, not after reading the whole file
- **Buffer edge cases** – Handled cases where lines are longer or shorter than the buffer size
- **Memory safety** – Prevented leaks and double frees by careful allocation and cleanup
- **Multi-fd support** – Implemented logic to track state for each file descriptor independently (bonus)
- **Linked list management** – Designed and debugged a custom linked list for dynamic file chunk storage (linked list version)

---

*This project was completed as part of the 42 School curriculum, demonstrating my proficiency in C programming, file I/O, and robust software engineering practices.*

---

## License

This project is licensed under the [MIT License](./LICENSE).
