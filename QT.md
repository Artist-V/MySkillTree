# Qt
>Qt做过的一些实验和项目的索引

| Test1 | Test2 |
| :---: | :---: |
| [文本编辑器](https://github.com/Artist-V/qt/tree/master/qt_TextEditor) | [绘图编辑器](https://github.com/Artist-V/qt/tree/master/qt_painter) |

## 要记下的一些小知识点

# QString转数值

| 类型 | 方法 |
| :--: | :--: |
| int | toInt()  // `int tmp = str.toInt();` |
| char* | toStdString() + data()  // `char* tmp = str.toStdString().data;` |
| float | toFloat()  // `float tmp = str.toFloat();` |
| double | toDouble()  // `double tmp = str.toDouble();` |
| long | toLong()  // `long tmp = str.toLong();` |
| longlong | toLongLong()  // `longlong tmp = str.toLongLong();` 
| short | toShort()  // `short tmp = str.toShort();` |



# 数值转QString
>适用于：int,double,long,longlong等,默认十进制
QString::number()  // `int tmp = str.toInt();` 
