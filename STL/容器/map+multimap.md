## map / multimap
* map是标准的关联式容器，一个map是一个键值对序列，即(key,value)对。它提供基于key的快速检索能力。
* map中集合中的元素按一定的顺序排列。元素插入过程是按排序规则插入，所以不能指定插入位置。
* map的具体实现采用`红黑树变体的平衡二叉树`的数据结构。在插入操作和删除操作上比vector快。
* map可以直接存取key所对应的value，支持[]操作符，如map[key]=value。
* multimap与map的区别：
  * map支持唯一键值，每个键只能出现一次
  * multimap中相同键可以出现多次。multimap不支持[]操作符。


#### map / multimap 的默认构造
* map<T1,T2> mapTT;
* multimap<T1,T2>  multimapTT;        //默认按照升序排列
* map<T1,T2,less<T1>> mapLess;        //按键升序的方式排列元素，若没有指定则默认T1
* map<T1,T2,greater<T1>> mapGreater;  //按键降序的方式排列元素，若没有指定则默认T1
其中T1,T2还可以用各种指针类型或自定义类型


#### map与迭代器
* 往容器插入元素，返回pair<iterator,bool>：
  * `map.insert(...);`  
* 在map中插入元素的三种方式：
  * 假设  `map<int, string> mapA;`
* 一、通过pair的方式插入对象
  * `mapA.insert(pair<int, string>(3, "小张"));``
* 二、通过pair的方式插入对象
  * `mapA.insert(make_pair(2, "小红"));`
* 三、通过value_type的方式插入对象
  * `mapA.insert(map<int, string>::value_type(1, "小李"));`
* 四、通过数组的方式插入值
  * `mapA[5] = "小王";`

* 前三种方法，采用的是insert()方法，返回值是pair<itrator,bool>
* 第四种数组插入方法，有一个性能问题：
  * 若在map中存在该键值，则修改这个键值的value
  * 若在map中没有该剑指，则将对组插入到map中


#### map 取操作或插入操作
`string strName = mapA[2];   //取操作或插入操作`
* 当map中存在2这个键值时，是取操作
* 当map中不存在2这个键值时，会自动插入一个实例，键值为2，value值为初始化值
```
map.begin();    //返回容器中 第一个数据 的迭代器
map.end();      //返回容器中 最后一个数据之后 的迭代器
map.rbegin();   //返回容器中 倒数第一个元素 的迭代器
map.rend();     //返回容器中 倒数最后一个元素之后 的迭代器
```


#### map的拷贝构造和赋值
```
map(const map &mp);		          //拷贝构造函数
map& operator=(const map &mp);	//重载等号操作符
map.swap(mp);				            //交换两个集合容器
```



#### map的大小
```
map.size();	  //返回容器中元素的数目
map.empty();  //判断容器是否为空
```


#### map的删除
```
map.clear();		        //删除所有元素
map.erase(pos);	        //删除pos迭代器所指的元素，返回下一个元素的迭代器。
map.erase(beg,end);	    //删除区间[beg,end)的所有元素	，返回下一个元素的迭代器。
map.erase(keyElem);     //删除容器中key为keyElem的对组。
```


#### map的查找
```
map.find(key);        //查找键key是否存在，若存在，返回该键的元素的迭代器；若不存在，返回map.end()
map.count(keyElem);   //返回容器中key为keyElem的对组个数。对map来说，要么是0，要么是1
multimap(keyElem);    //返回容器中key为keyElem的对组个数。对multimap来说，值可能大于1

map.lower_bound(keyElem);    //返回第一个key >= keyElem元素的迭代器
map.upper_bound(keyElem);	   //返回第一个key > keyElem元素的迭代器
map.equal_range(keyElem);		 //返回容器中 key == keyElem 的上下限的两个迭代器。上限是闭区间，下限是开区间，如[beg,end)。
                             //以上函数返回两个迭代器，而这两个迭代器被封装在pair中。
```
