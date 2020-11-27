---
layout: post
title: Lisp Part 1 - The Basic Form
---

LISP (usually referred to as "Lisp") is actually an acronym - LISt Processor. It was developed by [John McCarthy]([http://www-formal.stanford.edu/jmc/recursive.pdf](http://www-formal.stanford.edu/jmc/recursive.pdf)) (not the MMA referee) in 1960 for the IBM 704 computer. A list is one of the most basic data structures you can have. This gives a clue as to how Lisp is unique. Every expression in Lisp is a list. In other words, the language treats code like data.  Another unique thing about Lisp is that it's written in itself. But more on that later. The best way to learn Lisp, like basicallly any other language, is to start writing it as soon as possible. 

Every Lisp system includes an interactive "toplevel" where you enter your expressions. Toplevel is signified with a ">". Many things count as an expression in Lisp. For example, when entering an integer:
`> 1 
1
>`

The system returns and prints the value of the integer, then prompts you again.

I'm not sure if a single integer techincally counts as an "expression" (perhaps only bracketed code counts as an expression as we will see), but we can try something more complicated.

`> (+ 1 1)
2
>`

Here, we have an example of an in-built operator in the "+" sign, which is adding 1 and 1 together to equal two. Ordinarily, we would place in the plus sign in the middle of the values being added, but Lisp orders things differently and for good reason. After all, the fact that we usually put the plus in between the values is nothing more than historical accident. Putting the operator first (known as "prefix notation"), we can chain together values or "arguments" without repeating the operator each time:

`> (+ 1 2 3 4 5)
15
>`

As the chain of arguments  could continue indefinitely, we need to delimit the end of the expression with brackets. With the operator being before the arguments, you can also only provide a single argument.

`> (+ 1)
1
>`

You can also nest expressions in the same way.

`> (/ (- 10 2) (- 5 1))
2
>`

What came was the basic form of expression - it's as simple as that. Every Lisp expression is either an atom (e.g. 2) or a list which is anywhere from zero to a practically infinite amount of expressions enclosed in brackets.
