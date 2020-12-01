---
layout: post
title: Lisp Part 2 - Information and Types
---

![3 programming language paradigms]({{ site.baseurl }}/images/3Paradigms.png "3 Paradigms")

Lisp is a functional programming language. A functional  language, as opposed to a procedural or a object oriented language,  is one in which data has no independent existence from the code: it exists only as long as it is flowing through the functions - hence functional programming language. Data can be stored in Lisp through "Special variables" (often in other languages known as global variables), and it can simultaneously remain a functional language, but it wouldn't then be a *pure* functional language. Despite all this, Common Lisp is multi-paradigmatic, meaning it does have the capacity for object oriented programming through the [Common Lisp Object System]([https://courses.cs.northwestern.edu/325/readings/clos.php](https://courses.cs.northwestern.edu/325/readings/clos.php)) extension, although there does seem to be some disagreement as to how [fundamental it is to the language]([https://news.ycombinator.com/item?id=19165448](https://news.ycombinator.com/item?id=19165448))). It is also capable of procedural programming too. It may even be that Lisp is [no longer seen]([https://news.ycombinator.com/item?id=154005](https://news.ycombinator.com/item?id=154005)) by many as a functional language nowadays as it has such a broad variety of applications, although I suspect that the AI researchers, for whom the language was originally made for, still think of it as such.

There are many data types in Lisp. Here is a helpful simplification of [this data type table]([http://www.math-cs.gordon.edu/courses/cps323/LISP/lisp.html#:~:text=When attempting to evaluate a,as the logical value true.):

Common Lisp Type Name	                  Printed form example(s)
--------------------------------------------------------------------------------------
Atom

  Symbol	                              x, this-is-a-symbol, *so-is-this*, 1+, nil, ()
  Integer                               123
  Ratio	                                4/5
  Bit	                                  0, 1 (printed only, cannot be read)
  String	                              "This is a string"
  Array                                 #2a((1 2 3) (4 5 6))
  
List
  
  True List	                            (1 2 3), (), nil
  Dotted List	                          (1 . 2),   (1 2 (3 . 4))
 
In addition to these types, you will also commonly hear of [symbolic expressions](https://en.wikipedia.org/wiki/S-expression), or s-expressions for short. Note that almost everything in Lisp is an s-expression as an s-expression is defined as simply either an atom or a list. Considering that lists themselves are made of atoms or other lists (creating a nested hierarchy) and that atoms are s-expressions, lists are also known as parenthesised s-expressions.

Many of the data types in the table are straightforward and exist in other languages, but there are others which aren't included in the table that don't. Symbols (which are not case-sensitive as they are all turned into uppercase) and integers are both examples of atoms. As a result, symbols and integers are both examples of s-expressions.

Lists are objects enclosed with parenthesises. As you will see, almost every expression in Lisp is parenthesised, hence the name LISt Processing. in PG's book, ANSI Common Lisp, he says:

"We are now in a position to appreciate one of the most remarkable
features of Lisp.  Lisp programs are expressed as lists.  If the
arguments of flexibility and elegance did not convince you that
Lisp notation is a valuable tool, this point should.  It means that
Lisp programs can generate Lisp code.  Lisp programmers can (and
often do) write programs to write their programs for them."

Empty lists can also be represented in Common Lisp, either by empty parenthesises, (), or by nil. This is notable as it is the only s-expression that is both an atom and list.

The dotted list is another form of list that consists of two s-expressions separated by a single dot (also known as a conse). Although dotted lists like this are rarely used in practice, they are valuable in modelling how the Lisp represents the lists internally. For example, on the first line of code below, we have a true list, and on the second is the same list but in dotted form:

```
(show me a list)
(show . (me . (a . (list . nil))))
(show . (me . (a . list)))
```
Note that the third line would be incorrect.

Next post, we will look at evaluation and operators more closely...


  

  
