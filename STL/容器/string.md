## string
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


***

#### string构造函数
```
string();  //默认构造函数
string(const string &str); //拷贝构造函数
string(const char* s); //用字符串s初始化
string(int n, char c); // 用n个字符c初始化
```

#### string存取
```
const char & operator[](int n) const;
const char & at(int n) const;
char &operator[](int n);
char &cat(int n);
```
1. operator[]和at()的区别：at()在越界时会抛出异常，[]在刚好越界时会返回(char)0，再越界时编译器出错


#### string 到 const char*的转换
```
const char * c_str const
```

#### 把string 拷贝到char * 指向的内存空间
`int copy(char* s, int n, int pos=0 ) const;` 把串中以pos开始的字符n个字符拷贝到以s为起始位置的字符数组中，返回实际拷贝的数目。【s所指向的空间要足够大，不然会越界；该函数不会在复制内容的末尾附加空字符。】

#### string的长度
```
int length() const; //返回当前字符串的长度，不包括'\0'
bool empty() const; //当前字符串是否为空
```

#### string的赋值
```
string &operator=(const string &s);   //把字符串s赋给当前的字符串
string &assign(const char *s);        //把字符串s赋给当前的字符串

string &assign(const string &s);      //把字符串s赋给当前字符串
string &assign(int n,char c);         //用n个字符c赋给当前字符串
string &assign(const char *s, int start); //把字符串s/*前n个字符*/从start开始的字符串赋给当前的字符串
string &assign(const string &s,int start, int n);  //把字符串s中从start开始的n个字符赋给当前字符串
```

#### 字符串连接
```
string &operator+=(const string &str);  //把字符串str连接到当前字符串结尾
string &operator+=(const char *c_str);  //把字符串c_str连接到当前字符串结尾
string &append(const char *s);          //把字符串s连接到当前字符串结尾
string &append(const char *s,int n);    //把字符串s的/*前n个字符*/从pos开始的字符串连接到当前字符串结尾
string &append(const string &str);      //同operator+=()
string &append(const string &s,int pos, int n);//把字符串s中从pos开始的n个字符连接到当前字符串结尾
string &append(int n, char c);          //在当前字符串结尾添加n个字符c
```


#### string的比较
```
int compare(const string &s) const;  //与字符串s比较
int compare(const char *s) const;   //与字符串s比较
```
compare函数在 > 时返回 1，< 时返回 -1，== 时返回 0。比较区分大小写，比较时参考字典顺序，排越前面的越小。大写的A比小写的a小。


#### string 子串
```
string substr(int pos=0, int n=npos) const;    //返回由pos开始的n个字符组成的子字符串
```

#### string的查找
```
int find(char c,int pos=0) const;             //从pos开始查找字符c在当前字符串的位置
int find(const char *s, int pos=0) const;     //从pos开始查找字符串s在当前字符串的位置
int find(const string &s, int pos=0) const;   //从pos开始查找字符串s在当前字符串中的位置

int rfind(char c, int pos=npos) const;        //从pos开始从后向前查找字符c在当前字符串中的位置
int rfind(const char *s, int pos=npos) const;
int rfind(const string &s, int pos=npos) const;
```
find函数如果查找不到，就返回-1
rfind是反向查找的意思，如果查找不到， 返回-1

#### string的替换
```
string &replace(int pos, int n, const char *s);     //删除从pos开始的n个字符，然后在pos处插入串s
string &replace(int pos, int n, const string &s);   //删除从pos开始的n个字符，然后在pos处插入串s
void swap(string &s2);                              //交换当前字符串与s2的值
```

#### string的插入
```
string &insert(int pos, const char *s);   //在pos位置插入字符串s
string &insert(int pos, const string &s); //在pos位置插入字符串s
string &insert(int pos, int n, char c);   //在pos位置 插入n个字符c
```

#### string的删除
```
string &erase(int pos=0, int n=npos);  //删除pos开始的n个字符，返回修改后的字符串
```
