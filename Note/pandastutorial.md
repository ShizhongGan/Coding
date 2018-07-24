# 该笔记主要参照 [pandas0.23.2 document](https://pandas.pydata.org/pandas-docs/stable/tutorials.html)官方教程，进行系统学习归纳

## 基础篇 10分钟快速了解pandas

pandas 的基本数据结构是 **序列（series）**：某一个统计指标按照时间顺序排列而成的数列，多个指标的时间序列构成pandas的数据结构**DataFrame**
对比： numpy 是矩阵数组
优点： 1) 可以将不规则的多组序列数据直接转化为DataFrame,缺失值补全为NAN;2) 挺好用的...欢迎大家补充
```python
improt pandas as pd # 导入pandas库

# 将一个list 转化为一个序列
s = pd.Series([1,3,5,np.nan,6,8])

# 将一个矩阵数组转化为DataFrame
dates = pd.date_range('20130101', periods=6) #生成时间序列的时间戳(datetime index)
df = pd.DataFrame(np.random.randn(6,4), index=dates, columns=list('ABCD')) 
#numpy生成的6*4矩阵，时间戳为生成的dates，列表示指标，分别为A,B,C,D

# 字典（python基本数据结构之一，也是json文件格式）转化为DateFrame
df2 =pd.DataFrame({某个字典数据})
#自动补齐数据，字典key对应列指标，元素个数对应序列长度，时间戳为0-N的连续自然整数

# DataFrame数据的调用
df.head() #读取前几行
df.tail() #读取末尾几行
df.index  #行指标（时间戳）
df.columns # 读取列指标（序列名）
df.values  # 读取数据
df.describe() #描述数据的每个指标的基本统计特征
df.sort_index(axis=1, ascending=False) # 按照列指标降序排列 axis=0表示行
df.sort_values(by='B')  #按照某指标数值排列

# DataFrame Selection 数值调用，文档建议按照numpy方式读取
df['A'] # 按照指标名读取某一列
df[0:3] # 读取前三行
df['20130102':'20130104'] # 按时间戳读取某些行
df.loc['20130102':'20130104',['A','B']] # .loc是numpy的数据读取方法，可以按照标行列签进行数据读取
df.iloc[[1,2,4],0:2] # .iloc是numpy的数据读取方法，只按照数据的所在位置进行数据读取

# Boolean indexing 通过判断读取数据
df[df.A>0] # 通过某一列指标判断读取数据
df[df>0] # 通过整体判断，输出为df整体，不符合的显示为NAN
df[df.isin('NaN') # 判断是否有NAN值

# 缺失值
df.reindex(index=[],columns=[]) #更改index
df.dropna(how='any') # 删除含有NaN值的row 
df.fillna(value=5) #填充NAN的值为5
df.isna(df) # 判断是否存在nan

# 基本操作
# 通过函数对数据进行操作
df.apply(某个function) 对列数据累加 
df.apply(lambada x: x.max() - x.min()) 
# 统计直方图
s.value_counts() #序列操作
# 字符串操作
s.str.lower() #字符串全部变成小写

# 合并
```
                   A         B         C  D    F
2013-01-01  0.000000  0.000000 -1.509059  5  NaN
2013-01-02  1.212112 -0.173215  0.119209  5  1.0
2013-01-03 -0.861849 -2.104569 -0.494929  5  2.0
2013-01-04  0.721555 -0.706771 -1.039575  5  3.0
2013-01-05 -0.424972  0.567020  0.276232  5  4.0
2013-01-06 -0.673690  0.113648 -1.478427  5  5.0
