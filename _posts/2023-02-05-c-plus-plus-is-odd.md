---
layout: post
title: C++ is Odd
excerpt: "C++ is odd, and in this post I go into the one of the reasons why."
categories: [Programming]
tags: [C++]
---

## Introduction
I've been meaning to learn C++ for a minute. Well, that and the piano, chess, speed typing, juggling, and hell even fire breathing. 

It is safe to say that, for some reason, I am spreading myself too thin trying to learn many subjects when I could be mastering one. But today, for some reason, C++ and its beautifully grotesque self interested me more than usual, and I learned some interesting things I'd like to share with you all in this short blog post.

## Operators in C++ 
C++ has six types of operators:
1. Arithmetic
2. Relational
3. Logical
4. Bitwise
5. Assignment
6. Ternary or Conditional

C++ and C itself can be written in any non-ASCII 7-bit character set that includes the [ISO 646:1983](https://en.wikipedia.org/wiki/ISO_646 "enwiki:ISO 646") code set. Despite that, C++ includes a few operators `{, }, [, ], #, \, ^, |, ~` that are not included within ISO 646's character set. To counter this, C++ provides a few *odd* alternatives that can be used in their place.

## C++'s *odd* operators 

| Primary   | Alternative  |
| -------- | ----------- |
| && | and|
| &= | and_eq|
| & |bitand |
| \| |bitor |
| ~ |compl |
| ! |not |
| != |not_eq |
| \|\| |or |
| \|= |or_eq |
| ^ |xor |
| ^= |xor_eq |
| { |\<\% |
| } |\%\> |
| \[ |\<\: |
| \] |\:\> |
| \# |\%\: |
| \#\# |\%\:\%\: |

### C Compatibility
The same phrases are defined as macros in the include file iso646.h of the C computer language. Both the C++ version of iso646.h and ciso646 do not define anything because these are built into C++.

## Example 
```cpp
%:include <iostream>

struct A <%
    A(int bitand a) : a(a) {}
    int bitand a;
%>;

int main(int argc, char**argv)
<%
    if(argc not_eq 2) <% return 1;%>

    int n = std::atoi(argv<:1:>);
    A a(n);

    auto func = <:bitand:>(A a)<%
        std::cout << a.a << std::endl;
    %>;

    func(a);
    return 0;
%>
```
> This code compiles and prints a provided integer as an arg.

### Extra
34 control codes (characters like **NUL** and **DEL**) and 82 non-control characters make up the invariant character set.
  
Here are the 82 non-control characters: `!"%&'()*+,-./0123456789:;<=>?ABCDEFGHIJKLMNOPQRSTUVWXYZ_abcdefghijklmnopqrstuvwxyz`

You may have noticed that these `{}[]` characters are absent. Alternative operators were introduced in C and eventually C++ for this reason.

For international variations, the invariant leaves 12 characters. Here is how the French-Canadian version utilized its 12 more characters on a global scale: `#$àâçêîôéùèû` 

Why **&** needs a different operator when it is in the invariant is a little puzzling. It seems that certain international variations replaced other characters, including **!**, in addition to the 12 characters allowed. I was unable to locate a specific variant substituting **&**, but as C++ supports the **!** character with the not keyword, I assume that **&** is supported because there is a variant not utilizing it.