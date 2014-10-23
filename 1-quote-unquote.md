1-引用和反引用
==============

[引用]()  
[反引用]()  
[转义]()  

__一个Elixir程序可以被它自己的数据结构所表示。__本章将学习这样的数据结构看起来啥样，以及如何去构建它们。
这些概念是之后学习宏和元编程的基础。

## 1.1-引用
组成Elixir程序的基石，是三个元素的元组。
举个例子，方法调用```sum(1,2,3)```可以被表示为：
```elixir
{:sum, [], [1,2,3]}
```

你可以使用宏```quote```把所有语句转换成该形式：
```elixir
iex> quote do: sum(1,2,3)
{:sum, [], [1,2,3]}
```

第一个元素是函数的名字，第二个是一个键值列表，包含了一些元数据，第三个元素是参数列表。

运算符也可以被这样表示：
```elixir
iex> quote do: 1 + 2
{:+, [context: Elixir, import: Kernel], [1,2]}
```

甚至一个图（其实本质上就是调用了```%{}```）也可以：
```elixir
iex> quote do: %{ 1 => 2}
{:%{}, [], [{1,2}]}
```





