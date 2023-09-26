##### `random.seed(x)`
```
import random

# 设置种子
random.seed(123)

# 生成随机数序列
print(random.randint(1, 10))

# 再次设置种子
random.seed(456)

# 生成随机数序列
print(random.randint(1, 10))
```
- 设置完种子`x`后，每次生成的随机数相同。

##### `random.random()`
```
import random  
  
print(random.random())
```
- 生成0-1的随机浮点数，每次结果不同。

##### `random.randint(strat, stop)`
```
import random  
  
print(random.randint(1, 10))
```
- `start`：生成随机整数的起始位置
- `stop`：生成随机整数的终止位置
- `start`与`stop`必须是整数

##### `random.randrange(strat, stop[, step])`
```
import random  
  
print(random.randrange(1, 10)) # 生成1 ~ 9  
print(random.randrange(1, 10, 2)) # 生成1, 3, 5, 7, 9
```
- `start`：生成随机整数的起始位置
- `stop`：生成随机整数的终止位置（不包括）
- `step`：是随机整数之间的步长，`step`默认为 1 。
- `start`、`stop`与`step`必须是整数

##### `random.uniform(start, stop)`
```
random.uniform(strat, stop)
```
- `strat`：生成随机数的起始位置
- `stop`：生成随机数的终止位置

##### `random.choice(seq)`
```
random.choice(seq)
random.choice(seq, k)
random.sample(seq, k)
```
- `random.choice(seq)`用于从序列中获取一个随机元素，并返回一个（列表，元组或字符串中的）随机项，其中参数 `seq` 是一个非空序列。
- `random.choice(seq, k)`=`random.sample(seq, k)`，表示随机生成`k`个元素。

##### `random.shuffle(seq)`
```
import random

my_list = [1, 2, 3, 4, 5]
random.shuffle(my_list)
print(my_list) # 输出可能是[2, 5, 3, 4, 1]也可能是别的
```
- 函数是Python中的一个用于随机打乱列表顺序的函数。它接受一个可变序列作为参数，并在原地对该序列进行随机排序，即改变原始序列的顺序而不创建新的序列。