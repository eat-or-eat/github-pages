## 
> [官方文档](https://pandas.pydata.org/docs/)

# 一、增加

# 二、删除

## 1.删除某列为nan的行

作用：通常获得的一份dataframe中有些列有nan值，是统计中不需要的或者多余的，可直接去掉

```python
column_name = '列的名字'
df=df[~(df[column_name].isnull())] 
```

# 三、查看（找）

## 1.统计某列的各个值的数量

```python
column_name = '列的名字'
df.value_counts(column_name)
```



# 四、改动

