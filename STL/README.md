## STL

STL六大组件：容器、算法、迭代器、适配器、仿函数、空间适配器


### 容器
1. vector


##### vector
* vector插入数据的时间复杂度为O(1)
* push_back可能导致重新分配空间 ：空间溢出
* vector迭代器失效:
  * 序列式容器：删除当前iterator会使后面所有元素的迭代器都失效（连续分配的内存），不可以使用erase(it++)，erase方法可以返回下一个有效的iterator
  * 关联式容器：删除当前的iterator，仅仅会使得当前的迭代器失效，只要在erase时，递增当前iterator即可，用erase(it++)
