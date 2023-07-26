# COMP1521 Notes


### Two's Complement
Two's complement is a way of representing signed integers in binary. It is the most common way of representing signed integers in computers.

To convert a positive number to two's complement, we simply convert it to binary. For example, to convert 5 to two's complement, we convert 5 to binary, which is ```101```.

To convert a negative number to two's complement, we first convert it to binary, then invert all the bits, then add 1. For example, to convert -5 to two's complement, we first convert 5 to binary, which is ```101```. Then we invert all the bits, which is ```010```. Then we add 1, which is ```011```. Hence, -5 in two's complement is ```011```.

For a more intuitive understanding of this representation, refer to this [blog post](https://www.ralismark.xyz/posts/twos-complement).

<br>

### Floating Point
**Exponential Representation - IEEE 754**
Floats are stored using a representation that is quite similar to scientific notation.

Consider the float ```10.6875```. This can be represented as ```1.06875``` in base 10 scientific notation. 

The IEEE 754 standard uses base 2 (binary) or base 10 (decimal), but we will only be looking at base 2.

```10.6875``` in base 2 scientific notation is ```1.0101011 x 2^11```. 

A bit of terminology: The number before the ```x``` is `1.0101011` called the **mantissa**. The **exponent** is the power of 2 that the mantissa is multiplied by. In this case, the exponent is `11`.

Although we could also represent this as ```10.101011 x 2^10```, by convention, $1 \leq \text{mantissa} \lt 2$. This is called **normalisation**. This is done to ensure that the first bit of the mantissa is always 1. Hence, the first bit of the mantissa does not need to be stored, and therefore we can store more significant digits in the mantissa.


![Alt text](img/float.png)


Important to remember
- Do not use `==` and `!=` with floating point numbers, as this may cause unexpected behavior due to floating point error. Instead, calculate whether the difference between the two numbers is less than a certain threshold.


<br>



### Unicode and UTF-8
**Unicode** is a standard that assigns a unique number to every character in every language. It is a superset of ASCII, which only contains characters in the English language.

**UTF-8** is a way of encoding Unicode characters into bytes. UTF-8 is a variable length encoding, which means that each character can be represented by a different number of bytes. UTF-8 is backwards compatible with ASCII, which means that ASCII characters can be represented by a single byte in UTF-8.

**UTF-8 Layout**
![UTF-8](img/utf8.png)

Explanation of the layout:
- A single UTF-8 character can be anywhere from 1 to 4 bytes long.
- If the first bit is 0, then the character is a single byte character. This also means it is an ASCII character.
- If the first bit is 1, then the character is a multi-byte character.
- The number of bytes in a multi-byte character is determined by the number of leading 1s in the first byte. For example, if the first byte is `1110xxxx`, then the character is 3 bytes long.



<br>

### Processes
A process is an instance of a running program. It has its own memory space, which means that it cannot access the memory of other processes. A process also has its own stack, heap, and registers.

Environment for process running on Unix systems:
- `argc` - number of command line arguments
- `argv` - array of command line arguments
- `envp` - array of environment variables
  - Values of environment variables are set by the shell and are passed to the process. They are stored in the form `key=value`. 
  - For example, `PATH=/usr/bin:/bin` is an environment variable that tells the shell where to find the executable files for the commands `ls` and `cat`.
- `uid` - user identifier
  - Used to determine the permissions of the process. For example, if the user ID is 0, then the process has admin permissions. 
  - Must be an integer (POSIX standard)
- Streams (`stdin`, `stdout`, ``stderr``)
  - `stdin` is the standard input stream. It is used to read input from the user.
  - `stdout` is the standard output stream. It is used to print output to the user.
  - `stderr` is the standard error stream. It is used to print error messages to the user.
- Return status
  - An integer that is returned to the shell when the process exits. A return status of 0 indicates that the process exited successfully. A return status of 1 indicates that the process exited with an error.



**Process Creation**
In the past, processes were created using the `fork` and `exec` system calls. `fork` creates a copy of the current process, and `exec` replaces the current process with a new process.

Nowadays, we use `posix_spawn` to create processes. `posix_spawn` is a wrapper around `fork` and `exec`. It is more efficient than using `fork` and `exec` separately, as it avoids unnecessary copying of memory. It also is less prone to subtle bugs - more on this later!


`posix_spawn` takes in 6 arguments:
```c
#include <spawn.h>
int posix_spawn(
pid_t *pid, 
const char *path,
const posix_spawn_file_actions_t *file_actions,
const posix_spawnattr_t *attrp,
char *const argv[], 
char *const envp[]);
```

- `pid` is a pointer to a variable that will store the process ID of the new process.
- `path` is the path to the executable file of the new process.
- `file_actions` is a pointer to a `posix_spawn_file_actions_t` struct. This struct is used to specify what to do with the standard streams of the new process. For example, we can use this struct to redirect the standard streams to files.
  - Can be set to `NULL` if we do not want to do anything with the standard streams.
- `attrp` is a pointer to a `posix_spawnattr_t` struct. This struct is used to specify the attributes of the new process. For example, we can use this struct to set the user ID of the new process.
  - Can be set to `NULL` if we do not want to set any attributes.
- `argv` is an array of strings that will be passed to the new process as command line arguments.
- `envp` is an array of strings that will be passed to the new process as environment variables.