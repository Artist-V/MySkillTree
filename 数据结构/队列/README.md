## 队列
* 队列的插入和删除操作分别在线性表的两端进行
* 允许入队的一端称为队尾，允许出队的一端成为队头

###### 顺序队列/顺序循环队列
1. 队列空：front == rear == 0
2. 入队：rear++;
3. 出队：front++;
4. 当入队/出队元素超过数组容量时，rear下标越界，数据溢出  ====== 假溢出
5. 顺序队列的缺点：假溢出，入队/出队需要同时改变两个下标

1. front = (front+1) % length; rear = (rear+1) % length;
2. 队列空条件：front == rear;
3. 队列满条件：front == (rear+1) % length;

```
class Queue
{
private:
  T *element;
  int length;
  int front,rear;

public:
  Queue();
  ~Queue();
  bool empty();
  void push(T num);
  T pop();
};


template <class T>
Queue<T>::Queue()
{
  length = 10;
  element = new T[length];
  front = rear = 0;
}

template <class T>
Queue<T>::~Queue()
{
  delete[] element;
  front = rear = 0;
}

template <class T>
bool Queue<T>::empty()
{
  return front == rear;
}

template <class T>
void Queue<T>::push(T num)
{
  if(front == (rear+1) & length) // 队列满
  {
    T *tmp = element;
    elemtn = new T[length * 2];
    int j = 0;
    for(int i = 0; i != rear; i=(i+1)%length)
    {
      element[j++] = tmp[i];
    }
    front = 0;
    reat = j;
    length *= 2;
  }
  element[rear] = num;
  rear = (rear+1) % length;
}

template <class T>
T Queue<T>::pop()
{
  T x = element[front];
  front = (front+1)%length;
  return x;
}

```

###### 链式队列
