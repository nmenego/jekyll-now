---
layout: post
title: Java DOTALL Ignoring Newline
tags: java
---

This is quite an embarrassing thing to discover after years of writing Java. I recently was writing some code that checks for a string having a certain format. This string may or may not include a new line character. Today I learned that `.*` does not automatically cover line breaks in string. If you use `String.matches()` then `\\R` option can be used to cover this use case.

