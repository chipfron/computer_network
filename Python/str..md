`str.startswith(prefix[, start[, end]])`
```
text = "Hello, world!"

# 检查字符串是否以特定前缀开始
result = text.startswith("Hello")
print(result)  # 输出 True

# 可以指定起始和结束位置
result = text.startswith("world", 7)
print(result)  # 输出 True，从索引 7 开始检查
  
# 检查多个前缀
result = text.startswith(("Hello", "Hi", "Hey"))
print(result)  # 输出 True，因为 "Hello" 在字符串开头
  
# 检查多个前缀，指定起始和结束位置
result = text.startswith(("world", "universe"), 7, 12)
print(result)  # 输出 True，因为 "world" 在索引 7 到 11 的范围内
```
- 用于检查字符串是否以指定的前缀开始。它返回一个布尔值，如果字符串以指定的前缀开头，则返回 True，否则返回 False。
- `prefix`：要检查的前缀，可以是一个字符串或一个元组（tuple）包含多个前缀。
- `start`（可选）：开始搜索的起始位置，默认为 0，即整个字符串。
- `end`（可选）：结束搜索的位置，默认为字符串的末尾。

`str.endswith(suffix[, start[, end]])`
```
text = "Hello, world!"

# 检查字符串是否以特定后缀结束
result = text.endswith("world!")
print(result)  # 输出 True

# 可以指定起始和结束位置
result = text.endswith("Hello", 0, 5)
print(result)  # 输出 True，从索引 0 到 4 的范围内检查

# 检查多个后缀
result = text.endswith(("world!", "universe!"))
print(result)  # 输出 True，因为 "world!" 在字符串末尾

# 检查多个后缀，指定起始和结束位置
result = text.endswith(("Hello", "Hi", "Hey"), 0, 5)
print(result)  # 输出 True，因为 "Hello" 在索引 0 到 4 的范围内
```
- 用于检查字符串是否以指定的后缀结束。它返回一个布尔值，如果字符串以指定的后缀结束，则返回 True，否则返回 False。
- `suffix`：要检查的后缀，可以是一个字符串或一个元组（tuple）包含多个后缀。
- `start`（可选）：开始搜索的起始位置，默认为 0，即整个字符串。
- `end`（可选）：结束搜索的位置，默认为字符串的末尾。
