# Everything you need to know about pointers in C


Table of contents

    Definition of a pointer
    Starting off
    Interlude: Declaration syntax
    Assignment and pointers
    Dereferencing
    Interlude: Arrays
    Pointer arithmetic (or: why 1 == 4)
    Indexing
    Interlude: Structures and unions
    Multiple indirection
    Pointers and const
    Function pointers
    Strings (and why there is no such thing)


## Definition of a pointer

A pointer is a memory address.
(Mmm, short paragraphs.)


## Starting off

Say you declare a variable named foo.
```c
    int foo;
```
This variable occupies some memory. On current mainstream Intel processors, it occupies four bytes of memory (because an int is four bytes wide).

Now let's declare another variable.
```c
    int *foo_ptr = &foo;
```
foo_ptr is declared as a pointer to int. We have initialized it to point to foo.

As I said, foo occupies some memory. Its location in memory is called its address. &foo is the address of foo (which is why & is called the “address-of operator”).

Think of every variable as a box. foo is a box that is sizeof(int) bytes in size. The location of this box is its address. When you access the address, you actually access the contents of the box it points to.

This is true of all variables, regardless of type. In fact, grammatically speaking, there is no such thing as a “pointer variable”: all variables are the same. There are, however, variables with different types. foo's type is int. foo_ptr's type is int *. (Thus, “pointer variable” really means “variable of a pointer type”.)

The point of that is that the pointer is not the variable! The pointer to foo is the contents of foo_ptr. You could put a different pointer in the foo_ptr box, and the box would still be foo_ptr. But it would no longer point to foo.

The box named foo_ptr (an int *) is a pointer to a box named foo (an int).

The pointer has a type, too, by the way. Its type is int. Thus it is an “int pointer” (a pointer to int). An int **'s type is int * (it points to a pointer to int). The use of pointers to pointers is called multiple indirection. More on that in a bit.

int * |     | int
------|-----|----
foo_ptr| ->&foo -> | foo
-------|-----------|----
       |           | sizeof(int)








