## 栈


##### 堆和栈
* 堆和栈都是一种数据项按序排列的数据结构
* 栈：具有后进先出的性质
* 堆：（倒过来的树）经过排序的树形数据结构，每个结点都有一个值
  * 特点：根结点的值最小（最大)，根结点的两个子树也是一个堆
  * 常用来实现优先队列

>内存分配的堆区和栈区：
>栈：由操作系统自动分配释放，存放函数的参数值，局部变量等值
>堆：一般由程序员分配释放，若程序员不释放，在程序结束之后可能由OS回收


```
template <class T>
class Stack
{
private:
  T *element;
  int top;
  int capacity;

public:
  Stack(int capacity = 10)
  {
    element = new T[length];
    this->top = -1;
    this->capacity = capacity;
  }
  ~Stack()
  {
    this->top = -1;
    delete[] element;
  }
  bool isEmpty()
  {
    if(top == -1)
    {
      return true;
    }
    return false;
  }
  T top()
  {
    if(top == -1)
    {
      return -1;
    }
    return element[top];
  }
  bool pop()
  {
    if(isEmpty())
    {
      return false;
    }
    top--;
    return true;
  }
  bool push(T num)
  {
    if(top == capacity-1)
    {
      retur false;
    }
    top++;
    element[top] = num;
    return true;
  }
};
```
