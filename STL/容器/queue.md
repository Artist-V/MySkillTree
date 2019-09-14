## queue
* queue是队列容器，是一种“先进先出”的容器。
* queue是简单地装饰deque容器而成为另外的一种容器。


#### queue默认构造
* queue<T> queT;
* queue<int> queInt;            //一个存放int的queue容器。
* queue<float> queFloat;        //一个存放float的queue容器。
* queue<string> queString;     //一个存放string的queue容器。


#### queue插入删除
* queue.push(elem);   //往队尾添加元素
* queue.pop();        //从队头移除第一个元素


#### queue的拷贝构造与赋值
* queue(const queue &que);		         //拷贝构造函数
* queue& operator=(const queue &que);	//重载等号操作符


#### queue的数据存取
* queue.back();    //返回最后一个元素
* queue.front();   //返回第一个元素


#### queue的大小
* queue.empty();   //判断队列是否为空
* queue.size(); 	 //返回队列的大小


## priority_queue
* 最大值优先级队列、最小值优先级队列
* priority_queue<int> p1; //默认是 最大值优先级队列
* priority_queue<int, vector<int>, less<int> > p1;   //最大值优先级队列
* priority_queue<int, vector<int>, greater<int> > p2; //最小值优先级队列
