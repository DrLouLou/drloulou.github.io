---
layout: post
title: Lisp Experiments 1
---

Enough talking - we should probably start fiddling around with things.

A list, the primary data sctructure in Lisp - what is it? And what is it not? Examples will help.

To start, we cannot simply do what's in the code block below, else we return an error. 
```
> (1 2)
caught ERROR: illegal function call
```
This is because there is no joining of the values taking place. We may return a list looking like that, but we aren't allowed to simply state things that easily. To join two values and create "single-linked" lists, use the `cons` function and plug in two arguments. It looks like this:

```
> (cons 1 2)
(1 . 2)
```
Letters also work:

```
> (cons 'a 'b) 
(A . B)
```
But, remembering from an earlier post, if we want to have letters evaluate to themselves, we have to have the "'" (quote) operator. If we don't, CL will assume we are referring to variables:

```
> (cons a b)
The variable A is unbound.
```

So far, our arguments have been either numbers (which evaluate to themselves and so do not need the quote operator) or letters (which do not evaluate to themselves in the absence of the quote). But we can also have lists as arguments. Lists are like letters in that they need the quote operator if we want them to be returned as they have been inputted:

```
> (cons 'a '(b c d))
(A B C D)
> (cons 1 '(2 3 4))
(1 2 3 4)
```

You can also provide `nil` as the second argument:

```
> (cons 1 nil)
(1)
```

You can also chain `cons` functions together:

```
> (cons 'a (cons 'b '(c d))) 
(A B C D)
> (cons 'a (cons 'b (cons 'c nil)))
(A B C)
```

Notice how there were dots between the returned values in the first few examples but not in the recent ones? Compare these two similar looking examples which return different looking values:

```
> (cons 'a (cons 'b (cons 'c nil)))
(A B C)
> (cons 'a (cons 'b 'c))
(A B . C)
```

The former is a "true list" as it it terminated by nil. The latter is a "dotted list" because it contains... a dot. Both these notations mean the same thing, but most functions prefer true notation and will throw an error if they are given dotted lists. 

You may be wondering about the examples from earlier which were not terminated with the nil value, for example:

```
> (cons 'a '(b c d))
(A B C D)
```

*CHECK*: The second argument provided is already a list, meaning the nil at the end is implicit.

As you can probably guess, chaining the `cons` function becomes impractical very quickly. That's why you can also do this:

```
> (list 1 2 3 4 5)
(1 2 3 4 5)
> (list '(a b c))
((A B C))
> (list 1 2 3 nil)
(1 2 3 NIL)
```

`list` does the work for you. You don't need to wrap the subsequent arguments in parenthesises and you don't need to get terminate the expression with `nil`. If you do, the `nil` will be interpreted literally. Also, in the second example just now, we used the quote operator so we could have the sequence of letter arguments evaluate to themselves. But then I told you to not wrap the arguments in parenthesises as `list` already does this. So far, I don't know of a way around this other than just using the quote operator on each individual argument:

```
> (list 'a 'b 'c))
(A B C)
```

You can nest like this too:

```
> (list (list 'a 'b) (list 'c 'd))
((A B) (C D))
```

Once you've got a handle on predicting what lists will look like from the code, you can play around with some more list functions which I will cover next post.
