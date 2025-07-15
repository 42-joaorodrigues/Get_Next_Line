# Get Next Line

## 📘 Project Overview

**Get Next Line** is a foundational C project from the 42 curriculum. Its goal is to implement a function that reads and returns a line from a file descriptor, introducing the use of static variables and careful memory management.

> **Disclaimer:**  
> This document is an unofficial summary written for educational and documentation purposes.  
> It is not affiliated with or endorsed by 42 or its partners.  
> All 42 students are responsible for adhering to the academic integrity policy.  
> You may **not** publish or share any part of the official subject PDF, evaluation scripts, or Moulinette content.

---

## Contents

- [Goals](#goals)
- [General Requirements](#general-requirements)
- [Mandatory Part](#mandatory-part)
- [Bonus Part](#bonus-part)
- [Submission Guidelines](#submission-guidelines)
- [Testing](#testing)
- [Final Note](#final-note)

---

## Goals

- Implement a function that reads a line from a file descriptor.
- Learn and apply the concept of static variables in C.
- Practice robust memory management and error handling.
- Gain experience with file I/O and buffer management.

---

## General Requirements

- Written in **C**, following the **42 Norm**.
- No memory leaks or undefined behavior.
- All heap-allocated memory must be properly freed.
- No use of global variables.
- Only allowed standard functions: `read`, `malloc`, `free`.
- Forbidden: `lseek()`, your own `libft`, and global variables.
- All files must compile with `-Wall -Wextra -Werror`.
- Must work with and without the `-D BUFFER_SIZE` flag.
- Submit only necessary and used files.

### Makefile

Must include rules:
- `$(NAME)`, `all`, `clean`, `fclean`, `re`
- `bonus` rule if implementing bonus functions

---

## Mandatory Part

You must implement the following:

### Function Prototype

```c
char *get_next_line(int fd);
```

- **Files to turn in:**  
  `get_next_line.c`, `get_next_line_utils.c`, `get_next_line.h`
- **Parameters:**  
  `fd` — The file descriptor to read from.
- **Return value:**  
  - The line read (including the `\n` if present).
  - `NULL` if there is nothing else to read or an error occurred.
- **External functions:**  
  `read`, `malloc`, `free`

### Requirements

- Repeated calls to `get_next_line()` should read the file one line at a time.
- The returned line should include the terminating `\n` character, except at EOF if the file does not end with `\n`.
- Must work with both files and standard input.
- The header file must contain at least the prototype for `get_next_line()`.
- All helper functions should be in `get_next_line_utils.c`.
- Use a buffer size defined by `BUFFER_SIZE` (set via `-D BUFFER_SIZE=n`).
- Do **not** read the whole file at once; read as little as possible per call.
- Undefined behavior if the file changes between calls or when reading binary files.

---

## Bonus Part

If the mandatory part is complete and perfect, you may implement the bonus:

### Bonus Requirements

- Use only **one static variable** in your implementation.
- Support reading from **multiple file descriptors** at the same time, maintaining separate reading states for each.
- Bonus files must be named:
  - `get_next_line_bonus.c`
  - `get_next_line_bonus.h`
  - `get_next_line_utils_bonus.c`
- Add a `bonus` rule to your Makefile.

---

## Submission Guidelines

- Submit your work to your assigned Git repository.
- Only the contents of the repository will be evaluated.
- File and function names must be correct.
- Evaluation includes peer reviews and possible automated testing via **Deepthought**.
- If a norm or runtime error is found during evaluation, grading is stopped immediately.

---

## Testing

Writing your own test suite is **highly recommended**.  
Tests help during:
- Debugging
- Evaluation defense
- Collaborating with peers

Consider:
- Varying buffer sizes and line lengths.
- Using file descriptors for files, pipes, and standard input.

---

## Final Note

This project introduces static variables and advanced file I/O in C.  
A strong understanding of memory management, buffer handling, and file descriptors is essential for success in this and future 42 projects.

---

