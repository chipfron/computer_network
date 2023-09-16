```
random.seed(x)
```
- 设置完种子后，每次生成的随机数相同

```
random.random()
```
- 生成0-1的随机浮点数

```
random.randint(strat, stop)
```
- 生成某一区间的随机整数

```
random.randrange(strat, stop[, step])
```
- 生成一个在`start`与`stop`之间的随机整数，`step`是随机数之间的不长，`step`默认为 1 。
- `random.randrange(0, 10, 2)`只能生成0、2、4、6、8中的一个。

```
random.uniform(strat, stop)
```
- 生成随机浮点数

```
random.choice(seq)
random.choice(seq, k)
random.sample(seq, k)
```
- `random.choice(seq)`用于从序列中获取一个随机元素，并返回一个（列表，元组或字符串中的）随机项，其中参数 `seq` 是一个非空序列。
- `random.choice(seq, k)`=`random.sample(seq, k)`，表示随机生成`k`个元素。

```

```
