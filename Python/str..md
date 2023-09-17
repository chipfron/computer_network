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

`str.find(substring, start, end)`
```
sentence = "This is a sample sentence."
index = sentence.find("is")  # 在整个字符串中查找 "is"
print(index)  # 输出 2，因为 "is" 在位置 2 开始

index = sentence.find("is", 3)  # 从位置 3 开始查找 "is"
print(index)  # 输出 5，因为第二个 "is" 在位置 5 开始

index = sentence.find("notfound")  # 查找不存在的子字符串
print(index)  # 输出 -1，因为 "notfound" 未在字符串中找到
```
- 用于在给定的字符串中查找子字符串 `substring` 的第一个匹配，并返回匹配的索引位置。如果未找到匹配的子字符串，则返回 -1。
- `substring`：要查找的子字符串。
- `start`（可选）：搜索的起始位置，默认为 0，表示从字符串的开头开始搜索。
- `end`（可选）：搜索的结束位置，默认为字符串的末尾，表示在整个字符串中搜索。

`str.split(separator, maxsplit)` 
```
text = "apple,banana,grape,kiwi"  
  
# 使用逗号作为分隔符，默认情况下分割所有出现的逗号  
fruits = text.split(",")  
print(fruits)  # 输出: ['apple', 'banana', 'grape', 'kiwi']  
  
# 使用空格作为分隔符  
sentence = "This is a sample sentence."  
words = sentence.split(" ")  
print(words)  # 输出: ['This', 'is', 'a', 'sample', 'sentence.']  
  
# 使用最大分割次数，将字符串分割为2部分  
parts = sentence.split(" ", 2)  
print(parts)  # 输出: ['This', 'is', 'a sample sentence.']
```
- 用于将一个字符串分割成子字符串列表，根据指定的分隔符 `separator` 进行分割。它返回一个包含分割后的子字符串的列表。
- `separator`：分隔符，用于指定在哪里分割字符串。可以是一个字符或字符串。如果省略此参数，则默认使用空格作为分隔符。
- `maxsplit`（可选）：指定最大的分割次数。如果提供了此参数，字符串将被分割为最多 `maxsplit+1` 个部分。如果省略此参数或将其设置为 -1，则将字符串分割为尽可能多的部分。

`str.strip(characters)` 
```
text = "   Hello, World!   "

# 使用默认的空白字符删除开头和结尾的空格
stripped_text = text.strip()
print(stripped_text)  # 输出: "Hello, World!"

# 删除开头和结尾的逗号和空格
custom_stripped_text = text.strip(" ,")
print(custom_stripped_text)  # 输出: "Hello, World!"

# 删除开头和结尾的空白字符和感叹号
exclamation_stripped_text = text.strip(" !")
print(exclamation_stripped_text)  # 输出: "Hello, World"
```
- 用于删除字符串的开头和结尾处包含在 `characters` 参数中的字符（或字符集合）。它返回一个新的字符串，不影响原始字符串。