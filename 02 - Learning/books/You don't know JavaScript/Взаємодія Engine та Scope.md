---
title: Взаємодія Engine та Scope
created: 2024-06-13 15:45
last modified: Thursday 13th June 2024 15:45:53
aliases: 
tags:
  - book/you-dont-know-js/scope-and-closures
---
# Взаємодія Engine та Scope

Базуючись на [[LHS та RHS]] та [[Дві дії для оголошення змінних]]


```js
function `foo`(a) {
	console.log( a ); // 2
}

`foo`( a );
```

Давайте уявимо виконання ось цього шматку коду як розмову

Вони буде вигдати проблизно так:

```diff
+ Engine: Hey Scope, I have an RHS reference for `foo` . Ever heard of it?
- Scope: Why yes, I have. Compiler declared it just a second ago. He's a function. Here you go.
+ Engine: Great, thanks! OK, I'm executing `foo` .
+ Engine: Hey, Scope, I've got an LHS reference for `a` , ever heard of it?
- Scope: Why yes, I have. Compiler declared it as a formal parameter to `foo` just recently. Here you go.
+ Engine: Helpful as always, Scope. Thanks again. Now, time to assign `2` to `a`.
+ Engine: Hey, Scope, sorry to bother you again. I need an RHS look-up for `console`. Ever heard of it?
- Scope: No problem, Engine, this is what I do all day. Yes, I've got `console` . He's builtin. Here ya go.
+ Engine: Perfect. Looking up `log(..)`. OK, great, it's a function.
+ Engine: Yo, Scope. Can you help me out with an RHS reference to `a`. I think I remember it, but just want to double-check.
- Scope: You're right, Engine. Same guy, hasn't changed. Here ya go.
+ Engine: Cool. Passing the value of `a` , which is `2` , into `log(..)`
```

