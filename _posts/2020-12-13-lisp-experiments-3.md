---
layout: post
title: Lisp Experiments 3
---

There are a few more quick list functions to learn.

The `append` function takes any number of list arguments and returns a new list with all of the list arguments.

```
> (append (list 1 2) (list 3 4) (list 5 6))
(1 2 3 4 5 6)
> (append (list 1 2 3 (list 4 5) 6 7) (cons 8 (cons 9 (cons 10 nil))) (cons 11 12))
(1 2 3 (4 5) 6 7 8 9 10 11 . 12)
```

The `member` function takes two arguments, the second of which must be a list, and checks whether the first argument is contained within the list. If so, the function returns the remainder of the list (including the first argument), starting from matching value if the value appears more than once. If not, NIL is returned.

```
> (member 2 (list 1 2 3 4 5))
(2 3 4 5)
> (member 3 (list 1 2 3 4 5 3))
(3 4 5 3)
> (member (list 1 2 3) (list 1 2 3 4 5))
NIL
```
Judging from the third example, I think the first argument is not allowed to be a list.

Finally, `reverse` takes a list and reverses the top elements.

```
> (reverse (list 1 2 3 4 5))
(5 4 3 2 1)
> (reverse (list 1 2 3 (list 4 5)))
((4 5) 3 2 1)
```

As you can see, only the immediate elements in the first list are reversed. To reverse elements "lower down", you have to write more `reverse` statements:

```
> (reverse (list 1 2 3 (reverse (list 4 5))))
((5 4) 3 2 1)
```

Next post, we'll take a look at variables.
