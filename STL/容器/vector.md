## vector
* vector底层是`动态数组`
* vector插入数据的时间复杂度为O(1)，随机存取【支持 operator[] 和 at() 】
* vector在尾部添加或移除元素非常快速，但是在中部或头部插入元素或移除元素比较费时
* push_back可能导致重新分配空间 ：空间溢出
* vector迭代器失效:
  * 序列式容器：删除当前iterator会使后面所有元素的迭代器都失效（连续分配的内存），不可以使用erase(it++)，erase方法可以返回下一个有效的iterator
  * 关联式容器：删除当前的iterator，仅仅会使得当前的迭代器失效，只要在erase时，递增当前iterator即可，用erase(it++)


#### vecotr默认构造
```
vector<T> vecT;

vector<int> vecInt;        	  //一个存放int的vector容器。
vector<float> vecFloat;     	//一个存放float的vector容器。
vector<string> vecString;   	//一个存放string的vector容器。
  				                    //尖括号内还可以设置指针类型或自定义类型。
Class CA{};
vector<CA*> vecpCA;	  	//用于存放CA对象的指针的vector容器。
vector<CA> vecCA;     	//用于存放CA对象的vector容器。
```
由于容器元素的存放是按值复制的方式进行的，所以此时CA必须提供`CA的拷贝构造函数`，以保证CA对象间拷贝正常。


#### vecotr带参构造
```
vector(beg,end);    //构造函数将[beg, end)区间中的元素拷贝给本身。注意该区间是左闭右开的区间。
vector(n,elem);     //构造函数将n个elem拷贝给本身。
                    //vector<int> vecIntD(3, 9); //此代码运行后，容器vecIntB就存放3个元素，每个元素的值是9。
vector(const vector &vec);  //拷贝构造函数
```


#### vector的赋值
```
vector.assign(beg,end);    //将[beg, end)区间中的数据拷贝赋值给本身。注意该区间是左闭右开的区间。
vector.assign(n,elem);     //将n个elem拷贝赋值给本身。
vector& operator=(const vector  &vec);	//重载等号操作符
vector.swap(vec);          // 将vec与本身的元素互换。
```

#### vector的大小
```
vector.size();	            //返回容器中元素的个数
vector.empty();	            //判断容器是否为空
vector.resize(num);         //重新指定容器的长度为num，若容器变长，则以默认值填充新位置。如果容器变短，则末尾超出容器长度的元素被删除。
vector.resize(num, elem);   //重新指定容器的长度为num，若容器变长，则以elem值填充新位置。如果容器变短，则末尾超出容器长度的元素被删除。
```

#### vector末尾的添加移除操作
```
vector.push_back(int num);  //尾部添加
vector.pop_back();          //尾部删除
```

#### vector的数据存取
```
vector.at(int index);  	//返回索引idx所指的数据，如果idx越界，抛出out_of_range异常。
vector[int index];    	//返回索引idx所指的数据，越界时，运行直接报错
int &front();             //返回第一个元素
const int &front() const; //返回第一个元素
int &back();              //返回最后一个元素
const int &back() const;  //返回最后一个元素
```

#### vector插入
```
vector.insert(pos,elem);      //在pos位置插入一个elem元素的拷贝，返回新数据的位置。
vector.insert(pos,n,elem);    //在pos位置插入n个elem数据，无返回值。  
vector.insert(pos,beg,end);   //在pos位置插入[beg,end)区间的数据，无返回值
```

#### vector的删除
```
vector.clear();	      //移除容器的所有数据(大小size = 0,容量capacity不变 )
vec.erase(beg,end);   //删除[beg,end)区间的数据，返回下一个数据的位置。
vec.erase(pos);       //删除pos位置的数据，返回下一个数据的位置。
```
```
假设 vecInt 包含1,3,2,3,3,3,4,3,5,3，删除容器中等于3的元素
for(vector<int>::iterator it=vecInt.begin(); it!=vecInt.end(); /*这里不需写 ++it*/ )
{
   if(*it == 3)
   {
        it  =  vecInt.erase(it);       //以迭代器为参数，删除元素3，并把数据删除后的下一个元素位置返回给迭代器。
        //此时，不执行  ++it；  
   }
   else
   {
        ++it;
   }
}
```


#### vector为什么扩容以1.5倍或者2倍
1. 为什么是成倍增长，而不是每次增长一个固定大小的容量呢？
  * 成倍增长的重新分配内存次数=时间复杂度=O(logm(N))
  * 每次增长一个固定大小的时间复杂度=O(n^2)
  * 成倍方式扩容时间复杂度比较低
2. 为什么是以 2 倍或者 1.5 倍增长，而不是以 3 倍或者 4 倍等增长呢？
  * 每次扩展的新尺寸必然刚好大于之前分配的总和
