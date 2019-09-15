## pair
* pair译为对组，可以将两个值视为一个单元。
* pair<T1,T2>存放的两个值的类型，可以不一样，如T1为int，T2为float。T1,T2也可以是自定义类型

```
pair.first    //是pair里面的第一个值，是T1类型
pair.second   //是pair里面的第二个值，是T2类型

//////
set<int> setInt;  //往setInt容器插入元素1,3,5,7,9

pair< set<int>::iterator , set<int>::iterator > pairIt = setInt.equal_range(5); //返回容器中与5相等的上下限的两个迭代器。上限是闭区间，下限是开区间，如[beg,end)。
set<int>::iterator itBeg = pairIt.first;  //5
set<int>::iterator itEnd = pairIt.second; //7
//此时 *itBeg==5  而  *itEnd == 7

```
