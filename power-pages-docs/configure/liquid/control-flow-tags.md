---
title: Control flow tags
description: Learn about control flow tags available in liquid.
author: gitanjalisingh33msft

ms.topic: conceptual
ms.custom: 
ms.date: 01/09/2023
ms.subservice: 
ms.author: gisingh
ms.reviewer: ndoelman
contributors:
    - nickdoelman
    - GitanjaliSingh33msft
---

# Control flow tags

Control Flow tags determine which block of code should be executed and what content should be rendered based on given conditions. Conditions are built using the available [Liquid operators](liquid-operators.md), or just based on [the truth or falsehood of a given value](liquid-conditional-operators.md).  

## if

Executes a block of code if a given condition is met.

```
{% if user.fullname == 'Dave Bowman' %}

Hello, Dave.

{% endif %}
```

## unless

Like if, except it executes a block of code if a given condition is**not** met.

```
{% unless page.title == 'Home' %}

This is not the Home page.

{% endunless %}
```

## elsif/else

Adds more conditions to an if or unless block.

```
{% if user.fullname == 'Dave Bowman' %}

Hello, Dave.

{% elsif user.fullname == 'John Smith' %}

Hello, Mr. Smith.

{% else %}

Hello, stranger.

{% endif %}
```

## case/when

A switch statement to compare a variable to different values, and execute a different block of code for each value.

```
{% case user.fullname %}

{% when 'Dave Bowman' %}

Hello, Dave.

{% when 'John Smith' %}

Hello, Mr. Smith.

{% else %}

Hello, stranger.

{% endcase %}
```

### See also

- [Iteration tags](iteration-tags.md)
- [Variable tags](variable-tags.md)
- [Template tags](template-tags.md)
- [Dataverse table tags](dataverse-liquid-tags.md)

