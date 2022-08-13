* # C++标准库介绍（STL： Standard Template Library）

* ![image-20220306231732657](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220306231732657.png)

* ![image-20220306232027439](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220306232027439.png)

# 常用技巧   || Attentions

* while(cin>>m)

  判断是否有输入  直到停止

  （explanation:  最后输入EOF时返回为0）调试时**CTRL+C**

* 用vector<int> x当作标记

  x【0】x【1】是坐标（i，j） x【2】为visited【i】【j】，或者其他的需要传递参数

  可用在bfs（）     queue<vecotr<int>> x;

  dfs（）

* if else if 注意要打括号， 防止 在嵌套if -else 过程中 内层if-else 和外层if - else发生不必要连接；

* if(dfs(x,y) return true 与return dfs(x,y)区别

  在于前者若递归返回fasle 还可以进行其他操作  

  后者若进行完一次递归后 则完全返回  函数crashed。

  


## **库function** 

* 内联函数 sort（）

* vector<int> add(**vector<int> &A**,vector<int> &B);//**此时用引用会减少运行时间，otherwise 会要重复复制a[]进函数**

* sort(start,end,judege function);

  E.G

```c++
sort(nums.begin(),nums.end(),[](string &x,string &y){return x+y<y+x;});//一定要加引用，后续判断条件为x排在y前的情况条件
//or
sort(nums.begin(),nums.end(),compare);
bool compare(string &x.string &y){return x+y<y+x;}
```

* unique()

  ```c++
  iterator unique(iterator it_1,iterator it_2,bool Myfunc());//最后一个参数可以省
  //[it_1,it_2)的区间内。
  //删除区间内的重复元素 方法：将后面不重复的元素覆盖前面重复的元素
  //返回值为最后一个 不重复元素指针；
  //在vector，去重中用的很多
  ```

  

* max(a,b)||min(a,b) 

  两者a，b必须是同类型的数字 否则需要进行类型强制转换

* reverse（*ptr start,*ptr end)     #incldue<algorithm>

  与sort(*ptr start, *ptr end)有时会联合适用，（due to sort（）仅能从小到大）

* stringstream:

  相当于一个缓冲区  可以区分一长段字符串中的每个单词 （去除空格pop_back()即可）

  多次输入进ss：

  ss.clear(); //为了可以输入东西进去    去除EOF

  ss.str(""); //清空ss 如果不清空ss会很大，但是不会影响输入到其他的东西中去 只会影响 ss.sr() 会很大

  ```c++
  stringstream ss(s);//s是一长串
  string res="",temp;
  while(ss>>temp){
      res=temp+" "+res;//每次输入temp的仅有连续字符串 并没有空格“ ”；需要自己加
  }
  res.pop_back();'//去除最后的空格'
  ```

  - 用法① 格式转换

    

    ```c++
    stringstream s;
    int num = 1234;
    string out = "";
    s << num;
    s >> out;// out 为“1234”；
    ```

  - 用法② 读取格式不定的line

    getline函数

    ```c++
    //istream& getline (istream& is, string& str, char delim);
    string line ;
    getline(cin,line,'\n'); // 将cin中的直到/n的所有字符放入line中
    
    -------------------------------------------------------------------------
    //具体情况使用方法： (a, 1, 3, 100)格式的输入
    string line = ' s';  //开始需要非空
    vector<vector<int>> m;
    //存储矩阵
    while (getline(cin, line, '\n')) {
        istringstream iss(line);
        //多次定义stringstream会比较小号CPU的功耗，建议放在循环外部定义并
        //iss.clear();
        //iss << line; 或者 iss.str(line);
        vector<int> cur;
        for (int i; iss >> i;) {
            cur.emplace_back(i);
            if (iss.peek() == ',') iss.ignore();  //忽略输入中的逗号 
            //peek函数只是返回下一个字符，但是不读取他，意味着如果不ignore（）那么还会继续读取‘，’
        }
        m.emplace_back(cur);
    }
    //读取一行的方式还有
    //如果相隔符号为space时
    int i1, sum; // 统计每行的数字之和。
    while(true){
        iss >> i1;
        if(iss.fail())break;
        sum += i1;
    }
    ```

    

* stod(string str，*string::size_type size)

  return double型数据  //需要定义一个size变量 不用赋值

  ```
   double d;
      string::size_type size; //13     
      d = atof(str, &size);  //1234.56789
  ```

  利用 stringstream 也可以

* isdigit(char ch)

  判断当前字符是否是digit 

* isspace (char ch) 

* isalpha(char ch) judge if ch is a alpha(no matter A or a);

* atof( char* str);

  return float / doube型 

  如果是C++ 的string类型变量 需要调用函数  **.c_str()**  

  ```c++
  double d=atof(str.c_str());
  ```

  同理利用c_str() 也可以实现 ssprintf

  ```c++
  stringsream stream(str);
  stream>>d;
  cout<<d;
  ```

* swap（a,b) 两种运算方式

  ```c++
  // variable traditional version
  temp  =a;
  a = b ;
  b = temp;
  //bit calculation:
  a ^= b;
  b ^= a;
  a ^= b;
  ```

  

* to_sring(int val);

  从int 到string得转换自动.

* double ceil(double x)  向上取整

* double  floor (double x)向下取整

* memset()          #include<cstring>

  memset(st,false,sizeof st);

* accumulate()

  方法： iterator 的起点， 终点， 初值

  - 累加：

    ```c++
    int sum= accumulate(list, list+10, 0) ;
    //一般初值为0
    ```

    

  - 累乘：

    ```c++
     int  con_product  = accumulate(list, list + 3, 1, multiplies<int>());
    //一般初值为1
    ```

    

  - string 的合并

    ```c++
     string a_sum=accumulate(a.begin(), a.end(),string("out: "));
    ```

* 

## **数学上的trick**

最大数

```c++
int INF = (unsigned int) -1>>1; //不能(-1>>1)这样括，这样还是-1  因为括号内大小还是-1
```

gcb(int a,int b)

//求最大公约数

```c++
inline int gcd(int a,int b) {
	if(a%b==0) return b;
		else return gcd(b,a%b);
}
```

**重点在于转换 处理**

快速幂

```c++
void quick_pow(double x,int n){
    long long e=n;// in case of the overflw,when n<0,and n=-n will break up; 
    if(n<0) x = 1/x, e=-e;
    double ans;
    while(e){
        if(e&1) ans*=x;
        x*=x;
        e<<=1;
    }
    return ans;
}
```



## 模板

* 快排

  ```c++
  void qs(int a[],int l,int r){//如果是vector 记得用引用，要不然改变不了
      if(l>=r)return;
      int i=l-1,j=r+1,mid=a[l+r>>1];//一定要寄存mid 不能直接用下表 因为会改变去   a【l】
      while(i<j){
          do i++; while(a[i]<mid);//先do再while是为了防止在a[i]和a[j]都==mid时陷入死循环
          do j--;while(a[j]>mid);// 不是等号是为了防止在所有元素相同的时候 c
          if(i<j)swap(a[i],a[j]);//判断记得加
      }
      qs(a,l,j);//此处模板必须是这样， 如果是j-1, 因为最上处是取a【l】
      qs(a,j+1,r);
      //如果取得是a【r】/a[l+r+1>>1]则会发生死循环，此时应取qs(a,l,i-1);qs(a,i,r);
  }
  //结果中[l,j] 都小于等于mid;
  //[j+1,r] 大于等于mid；
  //所以 实际上分界点在于j+1 只排好了前j个数字。
  //所以在排前k个小的数字中 我们的边界判断为j+1 而非j
   if(j+1 > k) qs(arr, l, j, k);
   if(j+1 < k) qs(arr, j+1, r, k);
  //这个算法有一个最大的问题就是没有把对应第 j + 1小的数字放到对应位子上，只是保证了区间的有效性。
  
  void qs(int l, int r, vector<int> nums){
      int i = l,j = r, x = nums[l];
      while(i < j){
          while(i < j && x <= nums[j]) j--;
          //如果i先出发寻找大于6的数，会先经过1,2等小于6的数；这就会导致最后 i 和 j 相遇时j 不能找到 1. 2 因为i < j为判断条件 如下图
      	while(i < j && nums[i] <= x) i++;
          swap(nums[i], nums[j]);
      }
      swap(nums[l], nums[i]);
      qs(l, i-1, nums);
      qs(i+1, r, nums);
  }
  ```

  ![image-20220801165957580](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220801165957580.png)

* 二分：

  ```c++
  int bisearch(vector<int> num,int target){
  	int l=0,r=nums.size()-1;
      while(l<r){
          long long mid=l+(r-l)/2;//else +1; sometimes +1ll when longlong
          if(check(mid))r=mid;//else l=mid;
          else l=mid+1;//else r=mid-1; 
          
      }
      return l;
  }
  ```

* 归并

  ```c++
  void merge(int a[],int l,int r){
      if(l>=r)return;
      int mid=l+r>>1;
      //先递归 再归并
      merge(a,l,mid);
      merge(a,mid+1,r);
      int k=0,i=l,j=mid+1,temp[l+r];
      while(i<=mid&&j<=r){
          if(a[i]>a[j])temp[k++]=a[j++];
          else temp[k++]=a[i++];
      }
      while(i<=mid)temp[k++]=a[i++];
      while(j<=r)temp[k++]=a[j++];
      for(int i=l,k=0;i<=r;)q[i++]=temp[k++];
  }
  ```

* 

# vector：

```c++
#include<vector>

using namespace std;
```

向量，“变长数组”：长度根据需要自动变化的数组，

以“邻接表”的方式存储图，

vector变量也可以直接使用等于号来进行比较

**常用于在单词中字母freq比较的时候**



## 1.定义

```c++
vector<typename> name;  //typename==int /double /struct (basic type)//vector/set /queue/stack(STL type)
//e.g:
vector<int> scores;//存放成绩
vector<*struct root> Forest;//森林的定义
vector<string>  a = {"00"};//直接赋值
////*////////////////////////////////
//two- dimentional vecotr defination
 　　
    //二维vector初始化
2     vector< vector<int> > vt;
//初始化一个 二维vector
3     vector<vector<int> > vect(vt);
//使用另一个 二维 vector 初始化当前二维vector
4     vector< vector<int> > vec(row,vector<int>(column));
//初始化一个 二维的vector 行row,列column,且值为0
5     vector<vector<int> > visited(row,vector<int>(column,6));
//初始化一个 二维vector 行row,列column ,且 值为data=6 自定义data;
6     vector<vector<int> > vecto(row,vector<int>(vt[0].begin()+1,vt[0].begin()+3));
////初始化一个 二维vector 行row,第二个参数为一维vector;
```

## 2.访问

（1）下标法

```c++
vector <typename> vi;	
```

vi[0]、vi[i];

适用函数   vi.size();//取到地址最大值+1的地址

vi.size()-1为可访问的地址最大值

（2）迭代器访问

```c++
vector<typename> vi::iterator it;//it类似于指针，::指的是仅属于在vi当中的变量；
for(int i=0;i<5;i++){
    vi.push_back(i);//0-4共5个数push 进vector容器中 0.1.2.3.4
}

```

```c++
vector<int>::iterator it = scores.begin();
       i=0;
       while(it<scores.end ) {
      printf("%d",*it);
      it++;
   }
```

**需要访问时，才定义iterator，否则会出现错误，因为每次push_back()；begin（）对应的地址都会发生改变**

即，需要在push_back()完成后，才能定义iterator访问；

## 3.函数

typename x;

vector<typename>::iterator it=...;

begin(): 指向第一个元素   的iterator

end（）：指向最后一个元素**再往后**一个地址。



--------

push_front():**无这个函数** == insert(vector.begin(),val);

**emplace_back()**比push_back（）更快

//少了一次复制再构造变量的过程，但是问题在无法将常量（无法确定类型）emplace_back();

assign(int length,size_type item);//直接覆盖length 个 item

assign(iterator begin ,iterator end)  //直接覆盖 [begin,end) 的区间内元素

push_back(x);//在vector后添加元素x；

pop_back();//删除尾元素；

size();//返回unsigned 值

clear(）;//清空所有O(N)

insert(it，x);//向任意it处插入x；O(N)

insert(it,n,x);

insert(it,it_begin,it_end);

erase(it); erase(first,last) 

swap(vector<int>  a) 与a 向量交换； **用于全局vector变量与局部变量vector的赋值**

//删除it处元素；first-last 元素

**自创find()**  找到对应元素下标

```c++
cout<<find(nums.begin(),nums.end(),val)-nums.begin();
```

sort（）：sort（vector.begin(),vector.end());

```c++
//去除重复元素 在一些debug中有大用处
sort(vec.begin(), vec.end());//必须先sort 因为unique 只去除连续的相同元素
vec.erase(unique(vec.begin(),vec.end()),vec.end());
vec.resize(unique(vec.begin(),vec.end())-vec.begin())//unique 返回去重后的最后一个iteratior
//两种方法都可以
//define sorting function immediately
            sort(edges.begin(), edges.end(), [](const auto& a, const auto& b) {return a.len < b.len;});

```

自创 map（） 省事省心版

```c++
//e.g: for char in小写
vector<int> hash(26,0);
hash[ch-'a']++;//使用
```

resize() 可以在main（）函数里重新将全局vector变量大小定义

## 优化

①双指针

**删改** 都是O（N）的复杂度

所以如果需要在一串字符串中删除特定的东西

需要 O（N^2）

更优解为双指针 +resize（）；



push_back(0 )在预内存不足时 会重申请空间  导致时间复杂度上升

可以使用reserve（）来预先申请空间  **只改变capacity 不改变size**；

如在三数之和的题目里

```c++
vector<vector<int>> ret;
int n =nums.size();
ret.reserve(n>256 ? n:256);
//可以避免冲申请空间
```

 （与resize（）的区别在 resize size和capacity都改变到n值）



②list优化

使用情景： 使用insert函数很多的时候

而在实际上复杂度还可能更大，因为在vector中 insert如果size超过了capacity 就会再申请2倍capacity的内存再一个一个复制过去。

所以复杂度为O(N^2 +t * n) 其中t 为复制的次数

而利用list 就可以很好的避免这个问题  且insert的效率更高

```c++
list<int> que;
vector<int> ans;
list<int>:: iterator it = que.begin();
//如果想找到第n个位置 距离开头
while(n--){
    it++;
}
que.insert(it,val);
//最后的复制
ans.assign(que.begin(),que.end());
```



# set:

## 定义:

内部自动有序，不含重复元素的容器

如果考试中需要去掉重复元素，可以使用。



```c++
#include<set>
using spacename std;
set<typename> name;
set<typename>:: iterator it;//迭代器
name.insert(value);
```

## 访问

**迭代器只有vector string 能用*(it+i)来访问，也不支持it <st.end();可以写为!=st.end();**

set的迭代器访问

```c++
set<int> st;
st.insert(0);
st.insert(1);
for(set<int>::iterator it=st.begin();it!=st.end();it++){
    printf("%d",*it);
}
```



## 函数

```c++
#include<set>
set<typename> s;
set<typename>::iterator first,last;
typename value;
```

**insert(value)**//插入value  O(logN)

**erase(value)**;/

**erase(first,last)**//删除value  //删除first->last的

**erase(iterator)**

**count()** //返回元素个数

**find(value);**//返回value的迭代器；找不到返回end()； O（logN)

**size()**;返回元素个数 O(1);

**clear();**删除全部

**auto pr=s.equal_range(tepe_T item);** 

//返回一个pair值 first指向第一个>=item 的iterator  second指向第一个>item的iterator

**lower_bound(key_value)** ，返回第一个大于等于key_value的定位器

**upper_bound(key_value)，**返回最后一个大于等于key_value的定位器

# String

## 定义

```c++
#include<string>
string str="abcd";
string::iterator it=str.begin();
```

## 访问

```c++
cout<<str;//abcd
cout<<str[0];//a
cout<<*(it+1);//b
```

### 函数

1.+=

```c++
string str1="ab",str2="bc";
string str0=str1+str2;//str=abcd;
str1+=str2;//str1=abcd;

```

2.compare  ==/!==</...

```c++
str1<str2  //比较的每个字母是字典序，小写>大写 a>D;
```

3.length()/size() 返回存放字符数；

**返回值类型为unsigned int **如果要把其与其他类型数据比较 （利用max。min函数时）

则需要强制类型转换 e.g:max((int)str.size(),a)   (a为int型)。

4.str1.insert(int n,string str2);//在str1[n]处插入str2；

​    str1.(it,it1,it2);在str1的it处插入it1-it2包含的字符；

5.erase() //O(N)的复杂度

pop_back()

str.erase(begin,end) 删除[begin,end)  省略end则为INF;

erase(str.end()-1)

str.erase(first,last);

6.clear();清空所有

7.substr(int start,int len)

```c++
str0.substr(0,2);//ab  到n-1c
```

**substr(0)即省略了len  此时len为infinite**

8.**find(string )//返回第一次出现的位子，若无则返回 string :: npos**（本身值为-1，但是是unsigned 故可认为是最大值）

9.replace（）

```c++
str0.replace(pos,len,str);//str0[pos]处开始，len的长度内替换为str；
str0.replace(it1,it2,str);
```

10.append（） 加上某个char string sub_string 的方法

​	加sub_string :  str.append(string0, begin,length);   //begin ， length均为int型的变量

# MAP

翻译为映射

映射如int型array就是int到int的映射，array[0]=25//0->25的映射

double型array就是int->double的映射

可适用于 hashtable的适用

* find()

  return 迭代器值 

  ```c++
  map<char,int>::iterator it=m.find('a');
  cout<<it->first<<' '<<it->second;
  ```

  ## 判断的话可以

  ```c++
  if(hash.find(s[i])==hash.end());
  ```

* count(item) //return 1/0 if the item exsists or not;

* 当需要给map中元素排序时  先转换为vector

* ```
          vector<pair<int, int>> vec(map.begin(), map.end());
  ```

## 用处：

作为排序使用

因为map是以key值为reference 进行排序存储， 利用红黑树

unordered_map<string, map<int, set<string>> cusinetofood

此时就可以利用map对int的排序 和set 对string 的排序进行对事物的取出

```c++
*(cusinetofood["japan"].begin() -> second.rbegin());
//取出japan的map中 int 值最高， 且string字典序最小的值
```

## trick

- insert

  insert为了保证key值得唯一性， 当key值存在时，不会完成insert

  所以最好使用数组形式得插入

  ```c++
  hash[key] = value;
  ```

- 在key值对应得数组为空时

  记得要删除， 否则会出现某些不符合题目逻辑得错误

  

#  QUEUE

## 定义

```c++
queue<typename>  name;
queue<int> q1;
```

## 访问

本身是限制为先进先出的数据结构，所以只能通过q1.front();来访问队首，q2.back();来访问队尾；

### 函数

1.push(typename x);

2.front(),back(),

3.pop();即删除

4.empty();//检测是否为空，true为空，false为非空

5.size（）//返回个数

# Deque

## 定义：

```c++
deque<int> k(int nSize,const int &t);
```

## 函数

push_front();

push_back();

pop_front();

pop_back();

erase(iterator first,last); 删除 [first,last)的元素

insert(iterator it,const T x);

insert(it , n, x);

insert (it,  it_begin,it_end);//再it前插入[it_begin,it_end);

assign(int n,const T x);



# Priority_queue

## 1.定义

```c++
priority<int, vector<int>,less<int>> q;// equal to priority<int> q;  4 3 2 1 0 	// 递减 - 对应<
priority<int,vector<int>,greater<int>> q;//							 0 1 2 3 4	// 递增 - 对应>
//pair<int int>
//lesser<PII> (2,1)  (1,3)  (1,2)  so the vital items need to be in the first place.
//普通函数法
        priority_queue<ListNode*, vector<ListNode*>, decltype(&cmp)> q(cmp);

//重载需要bool oper
/**************************************************************/
auto cmp = [](const pair<string, int>& a, const pair<string, int>& b) {
            return a.second == b.second ? a.first < b.first : a.second > b.second;
        };
        priority_queue<pair<string, int>, vector<pair<string, int>>, decltype(cmp)> que(cmp);

///////////////////仿函数法
class Comp{
        public:
        bool operator()(const PII &n1,const PII &n2)const
        {
                if(n1.first == n2.first)
                        return n1.second < n2.second;
                return n1.first > n2.first;
        }n
};
 priority_queue<PII,vector<PII>,Comp> prio_freq;
////////////////////lambda表达式
auto cmp = []( Node & a,  Node &b){return ...};
priority_queue<Node, vector<Node>, decltype(cmp) > q(cmp);








//函数指针
bool cmpFun (const Node &a, const Node &b){
    return ....
}
bool (*p)(const Node a&, const Node b&) = cmpFun;
priority_queue<Node, vector<Node> , decltype(*p)> q(*p);
priority_queue<Node, vector<Node> , decltype(*cmpFun)> q(*c);
```

```c++
struct cmp{

    bool operator ()(const Node& a, const Node& b)
    {
        return a.value < b.value;//将value的值由大到小排列，形成Node的大根堆
    }
};
priority_queue<Node, vector<Node>, cmp>q;
```



## 2.用法

①emplace（）添加//push（）也可以

②pop（）弹出最顶上的那个元素 。

③ top（） 访问顶端元素

④size（） 大小

```c++
    priority_queue<PII, vector<PII>, greater<PII>> pq;

    for(auto [num, f]: freq) {//vector<int,int> freq;
        pq.emplace(f, num);//f in the first place to merge the order
        if(pq.size() > k) {
            pq.pop();//that's why use the greater priority.
        }
    }
// find the top k frequncy in the array.


priority_queue<Node,vector<Node>,cmp> q;
priority_queue<Node> q ;
Struct Node{
    int val
    Node():{};
    Node(int _x,int _y,int _val):x(_x),y(_y),val(_val);
   	bool operator <()
}
//if without reset of the operator  ,use cmp;
bool cmp(Node w1,Node w2){
    return w1.val>w2.val;//按照升序排列 （小顶堆） 返回1的在后面
}
```



# STACK

## 定义

```c+
stack<typename> name;
stack<int> s1;
```

## 访问

后进先出的数据结构

s1.top();来访问

1.push(typename x);弹入一个

2.pop()弹出，删除

3.top（）；访问最上面的值，不会删除

4.empty();//true为空，false 为非空

5.size();//返回stack中的元素个数

# list

## 构造：

构造函数：

list() 构造空的list
list (size_type n, const value_type& val = value_type()) 构造的list中包含n个值为val的元素
list (const list& x) 拷贝构造函数
list (InputIterator ﬁrst, InputIterator last) 用[ﬁrst, last)区间中的元素构造list

## 迭代器：

begin() 返回第一个元素的迭代器
end() 返回最后一个元素下一个位置的迭代器
rbegin() 返回第一个元素的reverse_iterator,即end位置
rend() 返回最后一个元素下一个位置的reverse_iterator,即begin位置
cbegin() (C++11) 返回第一个元素的cosnt_iterator
cend() (C++11) 返回最后一个元素下一个位置的const_iterator
crbegin() (C++11) 即crend()位置
crend() (C++11) 即crbegin()位置
 capacity：

bool empty() const 检测list是否为空，是返回true，否则返回false
size_t size() const 返回list中有效节点的个数

## 函数：

void push_front (const value_type& val)  在list首元素前插入值为 val的元素
		void pop_front() 删除list中第一个元素
		void push_back (const value_type& val)   在list尾部插入值为val的元素
		void pop_back() 删除list中最后一个元素
iterator insert (iterator position, const value_type& val)    在list position 位置中插 入值为val的元素
void insert (iterator position, size_type n, const value_type& val)    在list position位置插入n 个值为val的元素
void insert (iterator position, InputIterator ﬁrst, InputIterator last)    在list position位置插入 [ﬁrst, last)区间中元素
iterator erase (iterator position)    删除list position位置的 元素
iterator erase (iterator ﬁrst, iterator last)   删除list中[ﬁrst, last)区 间中的元素
void swap (list& x)   交换两个list中的元素
void resize (size_type n, value_type val = value_type())   将list中有效元素个数改变 到n个，多出的元素用val 填充
void clear() 清空list中的有效元素


# 类

## 初步定义

```c++
class Stock//define a class
{
private:
    std::string company;
    long shares;
    double share_value;
    double total_value;
    void set_tot();
public:
    void acquire (const std string&co,long n,double pr);
}
```

private的变量只能通过public的函数或者友元函数/友元类的函数（**friend**关键字于**private**中声明时)

因此可以说public 函数是程序和私有成员的桥梁。

当把成员函数放在private部分时，就不能通过程序直接调用该函数，但亦如同上段所说，公有部分函数可以调用他们（如同不写在.h文件中的在.c文件中的函数与外界文件之间的关系）

通常，会用**private**里的函数处理  **不属于公有接口的**实现细节

后续还有关键词 **protected**在后续13章会说到。

### 定义函数

```c++
void Stock::acquire(const std string&co,long n,double pr){
    ...
}//define the fuction in the class
```

这种方式意味着我们可以定义不同class底下同名的function，例如 void Buffer::acquire();

```c++
Stock sally;//define a object in Stock class.
```

### 内联函数

通常将短小的函数在其定义前增添 **inline**关键字（可在上一行）依次减少编译器的栈的空间，

在private中的函数经常被内联定义，

内联函数**inline**一般不加在**声明**时，而是在**定义**时。

```c++
inline
    void Stock::set_tot(){
    total_value=share_value*shares;
}
```

一般为了简便而把内联函数定义在头文件（.h）里

## 构造函数与析构函数

一般放置于 **public** 部分

```c++
Stock(const string & str="Error",long n=0,double pr = 0.0);
//constructor prototype with some default arguments
//str -> company | n -> shares | pr -> share_value;
```

定义：**参数名不能与类型中成员变量名相同** 否则就会有shres=shares;这样的语句出现。

一般会在 **成员变量名**前加上前缀 “class_"  或者加后缀    

"_"

```c++
Stock::Stock(const string & str="Error",long n;double pr ){
    company=str;
    if(n<0){
        std::cerr<<"Error"<<endl;
        shares=0;
    }
    else{
        shares=n;
    }
    share_value=pr;
    set_tot();
}
```

使用构造函数：

```c++
Stock gov("茅台",2005.62,50);
Stock gov= Stock("茅台",2005.62,50);
Stock * ptr = new Stock("茅台",2005.62, 50);
Stock none;//则使用默认值 0，0
```

只能有一个默认构造函数于一个类当中，有2种初始化默认值的方式

但是切勿 同时与上述的方法使用

// **但是可以同时拥有多个构造函数**

```c++

Stock(){
    company="Error";
    share_value=0.0;
    shares=0;
    set_tot();
}
//但是当上述带参数的构造函数 把最开始的"="Error""去掉时，则可以同时使用2个构造函数，因为此时只有现在这个Stock（）为默认构造函数。
```

析构函数：

```c++
~Stock();//一般没有形参 
```

```c++
Stock ~Stock(){
	cout<<"bye"<<company<<"!"<<endl
}
```

在类过期的时候使用。

## this 指针

```c++
const Stock & compare(const Stock & stk1)const;
```

①const & 表示返回一个最大的Stock class的变量，而不能被后续改变。

②const 表示显示访问的stk1 不会被改变

③const 表示隐式访问的this 不会被改变。

## operator 重载



```c++
Stock operator+(const Stock & stk1) const;
```

```c++
//重载时一般右自带的 class or  struct 值可以使用 而运算符后面的值为新进入的交互值 类似函数中的引用变量
Stock Stock::operator+(const Stock &stk1)const
{
	Stock k;
        ...
        return  k;
}
//重载于类当中
struct range
{
    int l, r;
    bool operator <(const range &w)const
    {
        return r<w.r;
    }
}
//重载于struct 当中  一般使用 sort 和 priority_queue等自带排序算法模板时 都是重载<符号
	//greater queue 时重载>符号
//重载时注意  priority_queue满足 比较return value ==1 的是由优先级小
							
			//在sort 时重载 <符号（for升序）return 1 时放在前面（优先级高）

```

因为此时+操作做完之后新造了一个Stock 变量，所以不能使用Stock &来作为返回值，因为这个Stock 变量一返回玩就销毁了（出作用域）

## Template

```c++
template<Array atype = int,int size = 50>
class Array{
    public:
    atype sto[size];
}
Array<int,100> a1; //define a array in int format
```



# 引用

```c++
int k=1;
int& k0=k;
int* ptrk = &k;
cout<<k<<","<<k0<<endl;//result:"1,1"
k0++;
cout<<k<<","<<k0<<endl;//result:"2,2"
cout<<&k<<","<<&k0<<enl;//result:"0x0065fd48,0x0065fd48"
```

此时k0扮演的角色与*ptrk相同，可在函数中调整对应引用值的value。

如果突然将引用变量 被赋值于另一个同类型变量：e.g:

```c++
int q=0;
k0=q;//k0=k=0;
```

也就是说只有在初始化的时候才能设置引用，而不能后天 通过赋值 而改变引用。此时的赋值只是简单的value的给予。

