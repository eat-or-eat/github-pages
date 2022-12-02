##

#  一、文件操作

## 1.复制整个文件夹


```bash
# 指令
cp -r ./source_folder/ ./target_folder/

# 源文件夹里面内容
./source_folder/1.py
./source_folder/2.md
./source_folder/Dockefile

# 复制后目标文件夹多一个子文件夹
./target_folder/source_folder/*
```

##  2.压缩解压tar.gz

```bash
# 压缩文件夹
tar -zcvf name.tar.gz (--exclude=source_folder/XX --exclude=source_folder/XX2) source_folder/

-z是使用gzip来解压或者压缩文件
-c是释放文件，或者说叫解压文件
-v是报告文件详情信息，如果不加这一条的话，就不会一直滚动的信息条了，建议加上，如果出了错还是会更加直观的看出来是什么原因
-f是指定名字 后续跟的是要解压的文件名
--exclude后面的文件夹路径不以反斜杠结尾，不然无效去除
# 解压
tar -zxvf name.tar.gz -C ./target_folder/
-z是使用gzip来解压或者压缩文件
-x是释放文件，或者说叫解压文件
-v是报告文件详情信息，如果不加这一条的话，就不会一直滚动的信息条了，建议加上，如果出了错还是会更加直观的看出来是什么原因
-f是指定名字 后续跟的是要解压的文件名
-C是指定目录，后续跟的也就是目标目录
```

## 3.zip解压压缩

```bash
 # 压缩文件夹
 zip -r dir1.zip dir1/
 
 # 解压
 unzip unzip -d /target_path/ name.zip
```

# 二、磁盘占用查看

## 1.文件/文件夹占用查看

```bash
du -sh *

# 示例
280M    XX1
2.4M    XX2
1.4M    XX3
55M     XX4
34M     XX5
2.5G    XX6
```



## 2.系统磁盘占用查看

```bash
df -lh

# 示例
Filesystem                   Size  Used Avail Use% Mounted on
overlay                      3.6T  2.5T  965G  73% /
tmpfs                         64M     0   64M   0% /dev
tmpfs                         56G     0   56G   0% /sys/fs/cgroup
```







