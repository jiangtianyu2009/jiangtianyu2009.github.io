---
layout:      post
title:       JavaScript Get Element by Value
category:    JavaScript
description: Code Snippet of how to get element by value in JavaScript.
---

Sometimes we need to scroll to one element on page, we use `elem.scrollIntoView()`, as you see, it requires a element object. But for some reason, when you do not have a unique id or class name or whatever, only have a unique value, you can try this way.

<script src="https://gist.github.com/jiangtianyu2009/e49af8189b8544b1539fa3f248d22e7b.js"></script>

In this example, you get a element like `<td class="level">[FAIL]</td>`, here the `level` will appear in every row of the table, cannot used to determine the location, but the value `[FAIL]` or `[PASS]` only appear once in the whole page.
