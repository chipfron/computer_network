- Lambda 表达式是一种匿名函数，允许在代码中定义简单的函数或函数对象而无需为其分配一个名称。Lambda 表达式通常用于函数式编程，特别是在编程语言中支持函数作为一等公民（first-class citizens）的情况下，例如 Python、Java 等。
- Lambda 表达式的一般语法通常包括以下元素：
- `lambda 参数列表: 表达式`
```
# 使用lambda表达式定义一个简单的加法函数
add = lambda x, y: x + y

# 调用lambda函数
result = add(3, 5)
print(result)  # 输出 8
```

- 在一些编程语言中，包括Python，Lambda表达式可以包含条件判断语句（if语句）。这使得Lambda表达式更加灵活，可以根据条件来执行不同的操作。Lambda表达式的条件语法通常如下：
- `lambda 参数列表: 返回值1 if 条件 else 返回值2`
```
# 使用Lambda表达式带有if条件判断
is_even = lambda x: "Even" if x % 2 == 0 else "Odd"

print(is_even(4))  # 输出 "Even"
print(is_even(7))  # 输出 "Odd"
```
