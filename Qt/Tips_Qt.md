## 要记下的一些小知识点
1. QString和数值的转换
2. 随机数

# QString和数值的转换

1. QString转数值

| 类型 | 方法 |
| :--: | :--: |
| int | toInt()  // `int tmp = str.toInt();` |
| char* | toStdString() + data()  // `char* tmp = str.toStdString().data;` |
| float | toFloat()  // `float tmp = str.toFloat();` |
| double | toDouble()  // `double tmp = str.toDouble();` |
| long | toLong()  // `long tmp = str.toLong();` |
| longlong | toLongLong()  // `longlong tmp = str.toLongLong();`
| short | toShort()  // `short tmp = str.toShort();` |



2. 数值转QString
>适用于：int,double,long,longlong等,默认十进制
QString::number()  // `int tmp = str.toInt();`


# Qt-正则表达式
>在Qt中想要使用正则表达式来检验输入的字符

`QRegExp类`：QRegExp类使用正则表达式提供模式匹配

`QRegExpValidator类`：QRegExpValidator类用于根据正则表达式检查字符串

头文件：# include < QRegExp >

使用方法：定义QRegExp类对象，指定正则表达式。然后在控件中,比如`QLineEdit`调用`setValidator`函数，指定该模式匹配

`void QLineEdit::setValidator(const QValidator *v)`：设置QLineEdit只接受成功验证了模式匹配的数

示例：
```
  QRegExp re("^[A-Za-z0-9_]{1,9}$");
  ui->name_lineEdit->setValidator(new QRegExpValidator(re,this));
```

### 随机数
* 头文件<Qtime>
* 
