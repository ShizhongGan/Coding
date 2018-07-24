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
df = pd.DataFrame(np.random.randn(6,4), index=dates, columns=list('ABCD')) #numpy生成的6*4矩阵，时间戳为生成的dates，列表示指标，分别为A,B,C,D
# 字典（python基本数据结构之一，也是json文件格式）转化为DateFrame
df2 =pd.DataFrame({某个字典数据}) #自动补齐数据，字典key对应列指标，元素个数对应序列长度，时间戳为0-N的连续自然整数
# DataFrame数据的调用
df.head() #读取前几行
df.tail() #读取末尾几行
df.index 
df.c

```

