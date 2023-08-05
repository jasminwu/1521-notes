# COMP1521 Notes

## Introduction
This document explains some key concepts taught in COMP1521. 

It is not a replacement for the lectures, but rather a supplement to them. It is recommended that you attend/watch the lectures first, then read these notes to get a better understanding of the content.

These notes are not comprehensive, and do not cover all the course content. It mostly consists of concepts that I personally found difficult to understand, or believed required further explanation.

If you would like a more complete set of notes, refer to the lecture slides on the [course webpage](https://cgi.cse.unsw.edu.au/~cs1521).

If you find any errors in these notes, please let me know by creating an issue on the [GitHub repository](https://github.com/jasminwu/1521-notes).


<br>

## Table of Contents
- [COMP1521 Notes](#comp1521-notes)
  - [Introduction](#introduction)
  - [Table of Contents](#table-of-contents)
  - [Two's Complement](#twos-complement)
  - [Floating Point](#floating-point)
    - [Exponential Representation - IEEE 754](#exponential-representation---ieee-754)
    - [Exponent Bias](#exponent-bias)
    - [Single Precision vs Double Precision](#single-precision-vs-double-precision)
    - [Bits in a Float](#bits-in-a-float)
  - [Unicode and UTF-8](#unicode-and-utf-8)
    - [Definitions](#definitions)
    - [UTF-8 Layout](#utf-8-layout)
    - [Tips for the Exam](#tips-for-the-exam)
  - [Processes](#processes)
    - [Process Creation](#process-creation)
    - [Process Execution State](#process-execution-state)
    - [Process ID](#process-id)
    - [Process Hierarchy](#process-hierarchy)
    - [Multi-tasking](#multi-tasking)
    - [Process related functions / syscalls](#process-related-functions--syscalls)
    - [Environment Variable Functions](#environment-variable-functions)
    - [Environment Variables and `posix_spawn`](#environment-variables-and-posix_spawn)
    - [Using `exec` family functions](#using-exec-family-functions)
    - [Pipes](#pipes)
  - [Concurrency, Parallelism, Threads](#concurrency-parallelism-threads)
    - [Concurrency vs Parallelism](#concurrency-vs-parallelism)
    - [Threads](#threads)
    - [Mutual Exclusion](#mutual-exclusion)
    - [Atomics](#atomics)
    - [Lifetimes](#lifetimes)
    - [Lifetimes in the context of concurrent programming](#lifetimes-in-the-context-of-concurrent-programming)
    - [Barriers](#barriers)
  - [Virtual Memory](#virtual-memory)
    - [Loading Pages from Memory](#loading-pages-from-memory)
    - [Caching](#caching)

