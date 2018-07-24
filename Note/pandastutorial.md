# 该笔记主要参照 [pandas0.23.2 document](https://pandas.pydata.org/pandas-docs/stable/tutorials.html)官方教程，进行系统学习归纳

## 基础篇 10分钟快速了解pandas

pandas 的基本数据结构是 **序列（series）**：某一个统计指标按照时间顺序排列而成的数列，多个指标的时间序列构成pandas的数据结构**DataFrame**

```python
improt pandas as pd # 导入pandas库
# 将一个list 转化为一个序列
s = pd.Series([1,3,5,np.nan,6,8])
s


```

