# COMP1521 Notes

## Introduction
This document explains some key concepts taught in COMP1521. 

It is not a replacement for the lectures, but rather a supplement to them. It is recommended that you attend/watch the lectures first, then read these notes to get a better understanding of the content.

These notes are not comprehensive, and do not cover all the course content. It mostly consists of concepts that I personally found difficult to understand, or believed required further explanation.

If you would like a more complete set of notes, refer to the lecture slides on the [course webpage](https://cgi.cse.unsw.edu.au/~cs1521).

If you find any errors in these notes, please let me know by creating an issue on the [GitHub repository](https://github.com/jasminwu/1521-notes).


<br>

## Table of Contents
- [COMP1521 Notes](notes.md/#comp1521-notes)
  - [Introduction](notes.md/#introduction)
  - [Table of Contents](notes.md/#table-of-contents)
  - [Two's Complement](notes.md/#twos-complement)
  - [Floating Point](notes.md/#floating-point)
    - [Exponential Representation - IEEE 754](notes.md/#exponential-representation---ieee-754)
    - [Exponent Bias](notes.md/#exponent-bias)
    - [Single Precision vs Double Precision](notes.md/#single-precision-vs-double-precision)
    - [Bits in a Float](notes.md/#bits-in-a-float)
  - [Unicode and UTF-8](notes.md/#unicode-and-utf-8)
    - [Definitions](notes.md/#definitions)
    - [UTF-8 Layout](notes.md/#utf-8-layout)
    - [Tips for the Exam](notes.md/#tips-for-the-exam)
  - [Processes](notes.md/#processes)
    - [Process Creation](notes.md/#process-creation)
    - [Process Execution State](notes.md/#process-execution-state)
    - [Process ID](notes.md/#process-id)
    - [Process Hierarchy](notes.md/#process-hierarchy)
    - [Multi-tasking](notes.md/#multi-tasking)
    - [Process related functions / syscalls](notes.md/#process-related-functions--syscalls)
    - [Environment Variable Functions](notes.md/#environment-variable-functions)
    - [Environment Variables and `posix_spawn`](notes.md/#environment-variables-and-posix_spawn)
    - [Using `exec` family functions](notes.md/#using-exec-family-functions)
    - [Pipes](notes.md/#pipes)
  - [Concurrency, Parallelism, Threads](notes.md/#concurrency-parallelism-threads)
    - [Concurrency vs Parallelism](notes.md/#concurrency-vs-parallelism)
    - [Threads](notes.md/#threads)
    - [Mutual Exclusion](notes.md/#mutual-exclusion)
    - [Atomics](notes.md/#atomics)
    - [Lifetimes](notes.md/#lifetimes)
    - [Lifetimes in the context of concurrent programming](notes.md/#lifetimes-in-the-context-of-concurrent-programming)
    - [Barriers](notes.md/#barriers)
  - [Virtual Memory](notes.md/#virtual-memory)
    - [Loading Pages from Memory](notes.md/#loading-pages-from-memory)
    - [Caching](notes.md/#caching)

