---
layout: post
title: Lisp Part 3 - Evaluation
---

In the post on the basic form, we had an expression that was: (/ (- 10 2) (- 5 1)). But it would be useful to know how the result is evaulated. The "/" and "-" operators we used are actually functions. That means that each nested expression and the complete expression above are all function calls. The "Evaluation Rule" goes as follows: first, the arguments themselves are evaluated from left to right, and then these values are passed to the function. In this case, 10 and 2 evaluate to themselves as they are integers, and then they are passed to the "-" function which returns a value of 8. The same is done to 5 and 1 to return a value of 4. Finally, the values of 8 and 4 are sent to the "/" function that returns a value of 2. To be clear as to the relationship between operators and functions, most operators are functions, but not all are. Some special operators do not work according to the Evaluation Rule. One example of this is the quote operator.
```
> '(+ 1 1)
(+ 1 1)
```
The quote operator bypasses the Evaluation Rule of Common Lisp. Therefore, the arguments themselves are never evaluated and are never passed into the function. It basically does nothing and just returns what you typed. According to [PG](https://sep.yimg.com/ty/cdn/paulgraham/acl2.txt?t=1595850613&), CL does this to allow you to protect your expressions from evaluation.
