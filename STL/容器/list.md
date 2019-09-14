## list
* list是一个双向链表容器，可高效地进行插入删除元素。
* list不可以随机存取元素，所以不支持at()函数与[]操作符。It++(ok) it+5(err)


#### list的默认构造
* list<T> lstT;
* list<int> lstInt;            //定义一个存放int的list容器。
* list<float> lstFloat;        //定义一个存放float的list容器。
* list<string> lstString;      //定义一个存放string的list容器。


#### list带参构造
* list(beg,end);          //构造函数将[beg, end)区间中的元素拷贝给本身。注意该区间是左闭右开的区间。
* list(n,elem);           //构造函数将n个elem拷贝给本身。
* list(const list &lst);  //拷贝构造函数。


#### list插入和删除
* list.push_back(int num);	    //在容器尾部加入一个元素
* list.pop_back();              //删除容器中最后一个元素
* list.push_front(int num);     //在容器开头插入一个元素
* list.pop_front();             //从容器开头移除第一个元素


#### list数据存取
* list.front();   //返回第一个元素。
* list.back();    //返回最后一个元素。


#### list与迭代器
* list.begin();        //返回容器中第一个元素的迭代器。
* list.end();          //返回容器中最后一个元素之后的迭代器。
* list.rbegin();       //返回容器中倒数第一个元素的迭代器。
* list.rend();         //返回容器中倒数最后一个元素的后面的迭代器。


#### list赋值
* list.assign(beg,end);    //将[beg, end)区间中的数据拷贝赋值给本身。注意该区间是左闭右开的区间。
* list.assign(n,elem);     //将n个elem拷贝赋值给本身。
* list& operator=(const list &lst);	//重载等号操作符
* list.swap(lst);          // 将lst与本身的元素互换。


#### list大小
* list.size();	           //返回容器中元素的个数
* list.empty();	           //判断容器是否为空
* list.resize(num);        //重新指定容器的长度为num，若容器变长，则以默认值填充新位置。如果容器变短，则末尾超出容器长度的元素被删除。
* list.resize(num, elem);  //重新指定容器的长度为num，若容器变长，则以elem值填充新位置。如果容器变短，则末尾超出容器长度的元素被删除。


#### list插入
* list.insert(pos,elem);      //在pos位置插入一个elem元素的拷贝，返回新数据的位置。
* list.insert(pos,n,elem);    //在pos位置插入n个elem数据，无返回值。
* list.insert(pos,beg,end);   //在pos位置插入[beg,end)区间的数据，无返回值。


#### list删除
* list.clear();	          	//移除容器的所有数据
* list.erase(/*迭代器*/beg,/*迭代器*/end);      //删除[beg,end)区间的数据，返回下一个数据的位置。
* list.erase(/*迭代器*/pos);          //删除pos位置的数据，返回下一个数据的位置。
* lst.remove(int elem);     //删除容器中所有与elem值匹配的元素。


#### list反序排列
* lst.reverse();     //反转链表，比如lst包含1,3,5元素，运行此方法后，lst就包含5,3,1元素。
