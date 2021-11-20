---
layout: post
title: Lisp Experiments 2
---

In the previous post, we saw that the `cons` function takes two arguments (which can either be: an element and a list, two elements, or two lists) and joins them together to make another list - true or dotted depending on how the expression is terminated. We also saw that the `list` function takes any number of arguments and makes them into a true list.

But, there are some more functions to help us. The `car` function will take a list as an argument and return the first value in the list. 

```
> (car '(1 2 3))
1
```

Pretty simple to get the hang of as `car` can take no more than a single argument and that argument must be a list. The function works for dotted lists too:

```
> (car '(a b . c))
A
```

The function `cdr` again takes in a single list argument and returns the same list without the first value.

```
> (cdr '(1 2 3 4 5))
(2 3 4 5)
> (cdr '(s a e n c h a . i))
(A E N C H A . I)
```

When you have a simple dotted pair, the first value is called the `car` value and the second is called the `cdr` value. So, they are named after the functions that retrieve them:

```
> (car (cons 1 2))
1
> (cdr (cons 1 2))
2
```

In Chapter 12 of the book _Practical Common Lisp_, it says "Lists are built by linking together cons cells in a chain. The elements of the list are held in the CARs of the cons cells while the links to subsequent cons cells are held in the CDRs. The last cell in the chain has a CDR of NIL, which...represents the empty list as well as the boolean value false." The following code will help to illustrate this:

```
> (cons 1 (cons 2 (cons 3 (cons 4 (cons 5 nil)))))
(1 2 3 4 5)
> (list 1 2 3 4 5)
(1 2 3 4 5)
```

So `car` and `cdr` are antagonistic. `car` returns ONLY the first value and `cdr` returns EVERYTHING BUT the first value. Using these two functions, we can return any value in a set of lists. Take a look at the following few lines:

```
> (defparameter fighterlist (list 'saenchai 'manachai 'buakaw 'dekkers))
FIGHTERLIST
> (car fighterlist) 
SAENCHAI
> (cadr fighterlist)
MANACHAI
> (caddr fighterlist)
BUAKAW
> (cadddr fighterlist)
DEKKERS
> (cdr fighterlist) 
(MANACHAI BUAKAW DEKKERS)
> (cddr fighterlist) 
(BUAKAW DEKKERS)
> (cdddr fighterlist)
(DEKKERS)
```

From these, we can nontice a few patterns. If you want a single, non-list value, your car/cdr chain should start with an "a", e.g. `cadr` or `caddr`. If you want a list, your chain should start with a "d", e.g. `cdar` etc.

It gets slightly more complicated when nesting gets involved:

```
> (car (list (list 1 2) (list 3 4))) 
(1 2)
> (cdr (list (list 1 2) (list 3 4))) 
((3 4))
> (caar (list (list 1 2) (list 3 4))) 
1
> (cadr (list (list 1 2) (list 3 4))) 
(3 4)
> (cddr (list (list 1 2) (list 3 4))) 
NIL
> (cdar (list (list 1 2) (list 3 4)))
(2)
```

We can also use `first` and `rest` as synonyms for `car` and `cdr` when working with the `list` function. Like with `car`, `first` returns single values and like `cdr`, `rest` returns lists, even if the rest of the original list is only one value.

```
> (defparameter listexample (list 1 2 3 4 5))
LISTEXAMPLE
> (first listexample)
1
> (rest listexample)
(2 3 4 5)
```

Next, we'll learn a few more quick functions and then move on.
