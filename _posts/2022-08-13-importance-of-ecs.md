---
layout: post
title: Metatables, and how they work.
excerpt_separator: <!--more-->
---

I\'m active in several development help communities and have noticed that one of the most common struggles amongst new scripters is metatables. While initially they can be an odd concept to wrap your head around, they are actually quite simple.

### Basics
You can think of a blank metatable like a blank piece of data, an object, or an instance, with no functionality. By default, our metatable has no functionality, and will act exactly the same way a normal table would. The magic here is that we can customize our metatable to do just about anything we want!

### ✨Metamethods✨

To add the fun custom functionality to our metatable, we use a fun special property called a ✨*metamethod*✨. With metamethods, we can customize our metatable and let it do anything we want!

For example, we could use the `__call` metamethod to let us call our metatable as if it were a function. Or... we could use the `__add` metamethod to add metatables as if they were numbers.

>"The possibilities are endless", - The Metatable Man.

\
Luau has __19__ built-in metamethods, all of which can be used to let our metatable do different things.
>* `__index`
* `__newindex`
* `__call`
* `__concat`
* `__unm`
* `__add`
* `__sub`
* `__mul`
* `__div`
* `__mod`
* `__pow`
* `__tostring`
* `__metatable`
* `__eq`
* `__lt`
* `__le`
* `__mode`
* `__iter`
* `__len`

These are probably somewhat confusing. Do not worry! You should get a better understanding as we go on.

### Getting Started

You might (or might not) be familiar with `getmetatable` & `setmetatable`. These functions are the gateway to accessing metatables. With some slight intuition, we can assume that we use these functions to, well, get the metatable, and set the metatable.

#### setmetatable
We use `setmetatable` to cast our metatable onto a regular table. It\'s important to understand that our functionality is not applied to the metatable, but rather applied onto a regular table.

`setmetatable` function takes two arguments, both tables. The first argument is the table we would like to apply our MT to, and the second argument is a dictionary where we define our metamethods. Take a look at this example...

```lua
local tbl = {}
setmetatable(tbl, {
	__index = function(self, key)
		print(key .. " doesn't exist!")
	end
})

print(tbl.foo) -- "foo doesn't exist!"
```