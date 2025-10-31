# Advanced LibFT - Extended C Library

## Overview

This is my personal extension of the **libft project from École 42**, developed during my studies to explore C programming concepts beyond the basic curriculum requirements. While the original libft project focuses on reimplementing basic C standard library functions, I decided to expand it with additional utility functions, data structures, and algorithms as a learning exercise.

## Architecture

The library is organized into modular components, each serving specific functionality:

### Main Components

#### 1. **Memory Management (`alloc/`, `mem/`)**

- **Custom Allocator**: Implements a buffer-based memory allocation system with `t_alloc` structure
  - `ft_alloc_init()`: Initialize custom allocator with buffer size
  - `ft_malloc()`: Allocate memory from custom buffer pools
  - `ft_reset()`: Reset allocator state for reuse
  - `ft_free()`: Free all allocated memory
- **Standard Memory Functions**: My implementations of standard memory operations
  - `ft_memcpy()`, `ft_memmove()`, `ft_memset()`, `ft_bzero()`
  - `ft_memchr()`, `ft_memchrset()`, `ft_memcmp()`, `ft_memdup()`
  - `ft_calloc()`, `ft_realloc()`

#### 2. **String Manipulation (`str/`)**

String handling functions:

- **Basic Operations**: `ft_strlen()`, `ft_strcpy()`, `ft_strcat()`, `ft_strcmp()`
- **Advanced String Functions**: `ft_strjoin()`, `ft_strtrim()`, `ft_substr()`
- **String Search**: `ft_strchr()`, `ft_strrchr()`, `ft_strnstr()`, `ft_strpbrk()`
- **String Transformation**: `ft_strmapi()`, `ft_striteri()`
- **Safe String Operations**: `ft_strlcpy()`, `ft_strlcat()`, `ft_strndup()`

#### 3. **Data Structures**

##### **Linked Lists (`lst/`)**

Singly linked lists with various operations:

- **Core Operations**: `ft_lstnew()`, `ft_lstadd_front()`, `ft_lstadd_back()`
- **List Traversal**: `ft_lstsize()`, `ft_lstlast()`, `ft_lstget()`, `ft_lstchr()`
- **Memory Management**: `ft_lstdelone()`, `ft_lstremove()`, `ft_lstclear()`
- **Functional Programming**: `ft_lstmap()`, `ft_lstiter()`, `ft_lstiter_inv()`
- **Advanced Features**: `ft_lstsort()`, `ft_lstsort_merge()`, `ft_lstis_sort()`
- **Custom Allocator Support**: `ft_lstnew_alloc()`

##### **Binary Search Trees (`bst/`)**

Binary Search Trees with various operations:

- **Node Operations**: `ft_bstnew()`, `ft_bstpush()`, `ft_bstchr()`
- **Tree Traversal**: `ft_bstiter_prefix()`, `ft_bstiter_infix()`, `ft_bstiter_suffix()`
- **Tree Analysis**: `ft_bstlevel_count()`
- **Memory Management**: `ft_bstclear()`

#### 4. **Input/Output Operations (`put/`, `gnl/`)**

- **File Descriptor Output**: `ft_putchar_fd()`, `ft_putstr_fd()`, `ft_putendl_fd()`
- **Numeric Output**: `ft_putnbr_fd()`, `ft_putnbr_base_fd()`
- **Get Next Line**: `ft_gnl()` - Efficient line reading from file descriptors
- **Advanced I/O**: `ft_read_line()` with buffer management

#### 5. **Printf Implementation (`printf/`)**

My implementation of printf (a separate 42 project that I integrated):

- **Core Functions**: `ft_printf()`, `ft_dprintf()`
- **Format Specifiers**: Support for `%c`, `%s`, `%p`, `%d`, `%i`, `%u`, `%x`, `%X`, `%%`
- **Format Flags**: `-`, `+`, ` `, `#`, `0`, precision and width specifiers
- **Modular Design**: Separate parsing, formatting, and output components

#### 6. **Conversion Functions (`convert/`)**

Data conversion functions:

- **String to Number**: `ft_atoi()`, `ft_atof()`, `ft_strtoi()`, `ft_strtof()`
- **Number to String**: `ft_itoa()`, `ft_nblen()`
- **String Parsing**: `ft_split()`, `ft_word()`, `ft_count_word()`

#### 7. **Character Classification (`is/`)**

Character type checking functions:

- `ft_isalpha()`, `ft_isdigit()`, `ft_isalnum()`, `ft_isascii()`
- `ft_isprint()`, `ft_isspace()`, `ft_isblank()`
- `ft_toupper()`, `ft_tolower()`

#### 8. **Process Management (`shell/`)**

System-level programming utilities:

- **Command Execution**: `ft_execve()`, `ft_which()`
- **Heredoc Support**: `ft_heredoc()`
- **Process Piping**: Support for command pipelines

#### 9. **Buffer Management (`buf/`)**

A simple buffer management system:

- **Buffer Operations**: `ft_buf_alloc()`, `ft_buf_realloc()`, `ft_buf_free()`
- **Buffer I/O**: `ft_buf_write()`

#### 10. **Mathematical Functions (`math/`, `utils/`)**

Mathematical utilities:

- **Exponential**: `ft_expf()` - Fast exponential approximation
- **Min/Max Functions**: Type-specific min/max for various data types
- **Absolute Values**: `ft_abs_*()` functions for different types

#### 11. **Random Number Generation (`utils/`)**

Pseudo-random number generation:

- **Seeding**: `ft_srand()`
- **Integer Random**: `ft_rand()`
- **Float Random**: `ft_randf()`, `ft_randf_norm()`

#### 12. **Utility Functions (`utils/`)**

Miscellaneous helpful functions:

- **Path Operations**: `ft_basename()`
- **Environment**: `ft_get_envp()`
- **Error Handling**: `ft_error()`, `ft_errloc()`
- **Data Manipulation**: `ft_swap_*()` functions
- **Argument Processing**: `ft_argv()`, `ft_split_argv()`

## Data Structures

### Custom Types

```c
typedef struct s_list {
    void *data;
    struct s_list *next;
} t_list;

typedef struct s_bst {
    struct s_bst *left;
    struct s_bst *right;
    void *data;
} t_bst;

typedef struct s_alloc {
    t_list *memory;
    t_list *current;
    size_t free_size;
    size_t buffer_size;
} t_alloc;
```

## Build System

The project includes a Makefile that:

- Compiles with strict warning flags (`-Wall -Wextra -Werror`)
- Creates a static library (`libft.a`)
- Supports standard targets: `all`, `clean`, `fclean`, `re`

## Usage

1. **Include the header**: `#include "libft.h"`
2. **Compile with the library**: `gcc your_program.c libft.a`
