## 容器
0. string：字符串类型
1. vector：动态数组，序列式容器
2. list：双向链表，序列式容器
3. deque：双端数组，序列式容器
4. set / multiset：集合，`红黑树`，关联式容器
5. map / multimap：`红黑树`，关联式容器
6. stack：堆栈
7. queue：队列容器

* 序列式容器：每个元素都有固定的位置，取决于插入顺序
* 关联式容器：元素位置取决于特定的排序

***

##### string
* string 和 char* 的比较
1. string 是一个类， char* 是指向字符类型的指针
2. string 封装了char*
3. string 不用考虑内存释放和越界问题，string 管理 char* 所分配的内存
4. string 提供了一系列字符串操作函数

* string 的 字符串操作函数：
1. find：查找
2. copy：拷贝
3. erase：删除
4. replace：替换
5. insert：插入


##### vector
* vector插入数据的时间复杂度为O(1)
* push_back可能导致重新分配空间 ：空间溢出
* vector迭代器失效:
  * 序列式容器：删除当前iterator会使后面所有元素的迭代器都失效（连续分配的内存），不可以使用erase(it++)，erase方法可以返回下一个有效的iterator
  * 关联式容器：删除当前的iterator，仅仅会使得当前的迭代器失效，只要在erase时，递增当前iterator即可，用erase(it++)
