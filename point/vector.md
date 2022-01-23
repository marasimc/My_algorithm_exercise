vector用法

```c++
#include <vector>
using namespace std;
```

## 创建vector

```c++
/*------- 方式1 -------*/
std::vector<double> values;
//（这是一个空的 vector 容器，因为容器中没有元素，所以没有为其分配空间。
//当添加第一个元素（比如使用 push_back() 函数）时，vector 会自动分配内存。）

values.reserve(20);
//设置了容器的内存分配，即至少可以容纳 20 个元素。
//注意，如果 vector 的容量在执行此语句之前，已经大于或等于 20 个元素，那么这条语句什么也不做；另外，调用 reserve() 不会影响已存储的元素，也不会生成任何元素，即 values 容器内此时仍然没有任何元素。
//还需注意的是，如果调用 reserve() 来增加容器容量，之前创建好的任何迭代器（例如开始迭代器和结束迭代器）都可能会失效，这是因为，为了增加容器的容量，vector<T> 容器的元素可能已经被复制或移到了新的内存地址。所以后续再使用这些迭代器时，最好重新生成一下。


/*------- 方式2 -------*/
std::vector<int> primes {2, 3, 5, 7, 11, 13, 17, 19};


/*------- 方式3 -------*/
std::vector<double> values(20);      //values 容器开始时就有 20 个元素，它们的默认初始值都为 0
std::vector<double> values(20, 1.0); //第二个参数指定了所有元素的初始值，因此这 20 个元素的值都是 1.0。


/*------- 方式4 -------*/
//通过存储元素类型相同的其它 vector 容器，也可以创建新的 vector 容器
std::vector<char>value1(5, 'c');
std::vector<char>value2(value1);

int array[]={1,2,3};
std::vector<int>values(array, array+2);//values 将保存{1,2}
std::vector<int>value1{1,2,3,4,5};
std::vector<int>value2(std::begin(value1),std::begin(value1)+3);//value2保存{1,2,3}
```

## vector容器包含的成员函数

| 函数成员         | 函数功能                                                     |
| ---------------- | ------------------------------------------------------------ |
| begin()          | 返回指向容器中第一个元素的迭代器。                           |
| end()            | 返回指向容器最后一个元素所在位置后一个位置的迭代器，通常和 begin() 结合使用。 |
| rbegin()         | 返回指向最后一个元素的迭代器。                               |
| rend()           | 返回指向第一个元素所在位置前一个位置的迭代器。               |
| cbegin()         | 和 begin() 功能相同，只不过在其基础上，增加了 const 属性，不能用于修改元素。 |
| cend()           | 和 end() 功能相同，只不过在其基础上，增加了 const 属性，不能用于修改元素。 |
| crbegin()        | 和 rbegin() 功能相同，只不过在其基础上，增加了 const 属性，不能用于修改元素。 |
| crend()          | 和 rend() 功能相同，只不过在其基础上，增加了 const 属性，不能用于修改元素。 |
| size()           | 返回实际元素个数。                                           |
| max_size()       | 返回元素个数的最大值。这通常是一个很大的值，一般是 232-1，所以我们很少会用到这个函数。 |
| resize()         | 改变实际元素的个数。                                         |
| capacity()       | 返回当前容量。                                               |
| empty()          | 判断容器中是否有元素，若无元素，则返回 true；反之，返回 false。 |
| reserve()        | 增加容器的容量。                                             |
| shrink _to_fit() | 将内存减少到等于当前元素实际所使用的大小。                   |
| operator[ ]      | 重载了 [ ] 运算符，可以向访问数组中元素那样，通过下标即可访问甚至修改 vector 容器中的元素。 |
| at()             | 使用经过边界检查的索引访问元素。                             |
| front()          | 返回第一个元素的引用。                                       |
| back()           | 返回最后一个元素的引用。                                     |
| data()           | 返回指向容器中第一个元素的指针。                             |
| assign()         | 用新元素替换原有内容。                                       |
| push_back()      | 在序列的尾部添加一个元素。                                   |
| pop_back()       | 移出序列尾部的元素。                                         |
| insert()         | 在指定的位置插入一个或多个元素。                             |
| erase()          | 移出一个元素或一段元素。                                     |
| clear()          | 移出所有的元素，容器大小变为 0。                             |
| swap()           | 交换两个容器的所有元素。                                     |
| emplace()        | 在指定的位置直接生成一个元素。                               |
| emplace_back()   | 在序列尾部生成一个元素。                                     |

## 示例

```c++
#include <iostream>
#include <vector>
using namespace std;
int main()
{
    //初始化一个空vector容量
    vector<char>value;
    
    //向value容器中的尾部依次添加 S、T、L 字符
    value.push_back('S');
    value.push_back('T');
    value.push_back('L');
    
    //排序
    sort(value.begin(),value.end());
    
    //调用 size() 成员函数容器中的元素个数
    printf("元素个数为：%d\n", value.size());
    
    //使用迭代器遍历容器
    for (auto i = value.begin(); i < value.end(); i++) {
        cout << *i << " ";
    }
    cout << endl;
    
    //向容器开头插入字符
    value.insert(value.begin(), 'C');
    cout << "首个元素为：" << value.at(0) << endl;
    
    return 0;
}
```

## 遍历vector容器

```c++
#include <vector>
 #include <iostream>

class Test
{
public:
    int a;
    int b;
    int c;
    Test()
    {
         a = 0;
         b = 0;
         c = 0; 
     }
}

int main()
{
     vector<Test> vecTest;
    for(int i = 0; i < 5; i++)
    {
         Test temp;
         a=i;
         b=i+1;
         c=i+2;
         vecTest.push_back(temp);
    }  
    std::cout.setf(ios::left);
    std::cout.width(6);

    //一、通过数组下标遍历
    for(int i = 0; i < vecTest.size(); i++)
    {
        std::cout << vecTest[i].a << vecTest[i].b << vecTest[i].c <<std::endl;
     }
  
    //二、通过迭代器遍历
    for(vector<Test>::iterator iter = vecTest.begin();iter != vecTest.end();iter++)
    {
        std::cout << iter->a << iter->b << iter->c <<std::endl;
    }  

    //三、C++11标准，auto关键字遍历
    for(auto iter = vecTest.begin(); iter != vecTest.end(); iter++)
    {
        std::cout << iter->a << iter->b << iter->c <<std::endl;
    }
   
    for(auto i : vecTest)
    {
         std::cout << iter->a << iter->b << iter->c <<std::endl;
    }
}
```

# 删除某一元素

```c++
#include<vector>
#include<iostream>
int main()
{
    vector<int> myvector;
    for(int i=0;i<20;i++)
        {
            myvector.push_back(i);
        }
    myvector.erase(myvector.begin()+2);//删除第三个元素
    myvecotr.erase(myvector.begin(),myvector.bengin()+3);//删除前3个元素,[ .. ),第四个元素没有删除
    for(auto it=myvector.begin();it!=myvecotr.begin()+5;)
        {
            myvector.erase(it);
        }
    for(auto it=myvector.begin();it!=myvcetor.end();it++)
        cout<<*it<<endl;
    //元素显示第二种方式,直接用索引来做
    //for(unsigned int i=0;i<myvector.size();i++)
    //cout<<' '<<myvector[i]
}
```

# 去重

```c++
include <iostream>
#include <algorithm>
#include <vector>

using namespace std;

int main()
{
    int myints[] = {1,2,3,1,1};
    int len = sizeof(myints)/sizeof(int);
    vector<int> vec(myints, myints + len);
    
    sort(vec.begin(), vec.end());
    vec.erase(unique(vec.begin(), vec.end()), vec.end());
    
    for(int x : vec)
        cout << x << ",";
    return 0;
}
```

