# Pandas

- iloc可以连续切片

``` python
# 下标，行标
df.index  # axis=0

df.columns  # 列，, axis = 1

df.values  # 查看数值

df.describe()

# 排序
df.sort_index(axis=0, ascending=False)  # 递增
df.sort_values(by="B")

df['A']  df.A  # 查看A列

# 切片看行
df[0:3]  df["20130101":"20130103"]  # iloc可以连续切片

# loc
df.loc[dates[0]]  # 第一行数据
df.loc[dates[0],'B']
df.loc[:,['A','B']]
df.loc['20130102':'20130104',['A','B']]

# iloc
df.iloc[3]  # 第三行
df.iloc[3:5,0:2]  # 连续切片
df.iloc[[1,2,4],[0,2]]

df.iat[1,1]  # 索引标量值更快

# 布尔型索引
df[df.A > 0]  # 所有A列大于0的行
df2[df2 > 0]  # 留下大于0的，前提是可以比较的数值

# isin函数
df2[df2['E'].isin(['two','one'])]
```

### 缺失数据

``` python
# 丢弃缺失数据
df1.dropna(how='any')
# 填补缺失数据
df1.fillna(5)
# 查看
df1.isnull(df1)
```

### 计算数据

``` python
df.mean()  # 每一列的均值
df.mean(1)  # 每一行的均值

# apply()  ?
```

