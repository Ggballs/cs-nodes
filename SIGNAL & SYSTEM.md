# SIGNAL & SYSTEM

4.22 10-12 西教402

前置：

X（t）=δ（t）信号  AX=u(t)； A^2 X=t * u(t); A^3=1/2 * t^2 * u(t)  (u(t)仅仅只是一个信号代称，表达输出的是信号而不是数值，可以理解为单位)

```matlab
n=40;                            %定义阶跃序列的长度
x=ones(1,n);                     %生成一个全1的向量x
xn=0:n-1;                        %定义绘图的横坐标变量
stem(xn,x);
%%u（t）信号
```



* causal system：

  根据当前及之前的输入来判定输出

* memoriless system

  仅仅根据当前的输入来判定输出 ----**all  memoriless sys are causal system

* 稳定性：

  有限的输入对应有限的输出

* 可逆性 invertible

  一个函数在不同输出下 可以反过来有 对应的不同输入 即为可逆

  特殊判断  如 C * δ（t - A) 信号

* time-invarient system 

  ①中括号内有前置时间系数  time-varient sys

  <img src="C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220420184628155.png" alt="image-20220420184628155" style="zoom:50%;" />![image-20220420185140305](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220420185140305.png)
  
  **y[f(n)-n0]==y[f(n-n0)];**
  
  <img src="C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220225104929208.png" alt="image-20220225104929208" style="zoom: 50%;" />
  
  <img src="C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220420185658377.png" alt="image-20220420185658377" style="zoom:50%;" />
  
  
  
  **线性时不变系统性质：**
  
  ![image-20220309081954576](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220309081954576.png)
  
  ### 信号一些基本性质
  
  ①系数变换与图像
  
  ​	一、连续性函数
  
  <img src="C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220309085403727.png" alt="image-20220309085403727" style="zoom:50%;" />
  
  ​	二、离散型函数
  
  ​	a<1  : 延展时  **会造成信号失真**   
  
  ​	a>1  进行压缩。
  
  ②周期函数：
  
  ​	**离散型的特殊性**
  
  ​	此时因为pi为无理数，所以实际上cos[n]并不是周期函数  cos[pi*n]才是周期函数。
  
  ​	<img src="C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220309085957691.png" alt="image-20220309085957691" style="zoom:50%;" />





# 离散化

<img src="C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220309083726548.png" alt="image-20220309083726548" style="zoom:80%;" />

<img src="C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220309083705074.png" alt="image-20220309083705074" style="zoom:67%;" />

<img src="C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220309083631229.png" alt="image-20220309083631229" style="zoom:67%;" />

<img src="C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220309083615648.png" alt="image-20220309083615648" style="zoom:67%;" />

# FeedBack

* ## Concept

  * Acyclic: all go out without a cycles;
  * cyclic: at least **one** cycle;

* ## Models

* <img src="C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220308210541300.png" alt="image-20220308210541300" style="zoom:50%;" />

  * ## 乘积式结构

  <img src="C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220302082503810.png" alt="image-20220302082503810" style="zoom:67%;" />

  

  Y/X =A/1-pA   == Y=e^pt u(t)  (if X=δ(t))

  Y/X=R/1-pR  == (1-R)Y

  ![image-20220302083522240](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220302083522240.png)

  ​	单系数反馈信号特点：  

  ​	**1/1-pR --> p^n * u[n];**

  ​	① converge（收敛）  p<1

  ​	② diverge（发散）  p>1

  ​	③ 绝对值单调（可以有正负不断变） （不会有相同的值）(如图5)

  ​	④如果多Delay的情况下  还是取Πp0p1....pn=p再做如上的判断 **p仅为y前的系数**（因δ（x）信号在n>1时已全部为0）

  ​	（如下图：） 

  <img src="C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220308185437475.png" alt="image-20220308185437475" style="zoom: 50%;" />



## 分式结构

<img src="C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220308185941357.png" alt="image-20220308185941357" style="zoom:50%;" />

<img src="C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220308190003805.png" alt="image-20220308190003805" style="zoom: 50%;" />

<img src="C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220302085809241.png" alt="image-20220302085809241" style="zoom:67%;" />

**简化解法**

将R->1/z （**整个式子内全换**）再找到denominator的零根  之后就可以化为乘积的形式    再转换为加法

（z的根即为poles）

  ①R的最高次方决定pole的个数

​	② R3/1-R3  -> 1/Z3-1  Z3-1=0->  (Z-1)(Z2+Z+1); 一个实数根 2个虚数根

**1/1-pR的形式**



<img src="C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220302091602109.png" alt="image-20220302091602109" style="zoom: 50%;" /><img src="C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220309190617135.png" alt="image-20220309190617135" style="zoom:67%;" />

## 积分结构

​	A/1-pA = e^pt* u(t)

<img src="C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220308210001057.png" alt="image-20220308210001057" style="zoom:67%;" />

**A/1-pA的形式**

<img src="C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220308212207573.png" alt="image-20220308212207573" style="zoom:67%;" />

相对应的，一样可以把A->1/s并找到s的零次方根 ，即可找到对应系数

<img src="C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220302093443951.png" alt="image-20220302093443951" style="zoom:67%;" />

<img src="C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220308211901927.png" alt="image-20220308211901927" style="zoom:67%;" />

<img src="C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220311102820031.png" alt="image-20220311102820031" style="zoom:67%;" />

![image-20220327210740984](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220327210740984.png)

## 拉普拉斯定变换（s变换）：

<img src="C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220311104405170.png" alt="image-20220311104405170" style="zoom:33%;" />

* ### Basic

  <img src="C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220324165257814.png" alt="image-20220324165257814" style="zoom:50%;" />

  <img src="C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220324163849892.png" alt="image-20220324163849892" style="zoom: 67%;" /><img src="C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220324163857407.png" alt="image-20220324163857407" style="zoom:50%;" />

  即上面积分结构中的变换  把s-->1/A;

  

  ### negative part（left sided)

  <img src="C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220324165314330.png" alt="image-20220324165314330" style="zoom: 50%;" />u(-t):  only in the left side gemetrically; input(-5) x(t)=-e^5递增

  

  ![image-20220324164533894](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220324164533894.png)

  <img src="C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220324164632098.png" alt="image-20220324164632098" style="zoom: 67%;" />![image-20220414195546667](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220414195546667.png)

  

  ROC：与时域上 x（t）的值域正相关  

  ![image-20220415111100199](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220415111100199.png)

  ![image-20220415111502035](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220415111502035.png)

  ## characters:

  ![image-20220325110207899](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220325110207899.png)

  stable -> ROC includes jw axis  -> **rightest pole is still on the negtive constant axis**;

  <img src="C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220414194834453.png" alt="image-20220414194834453" style="zoom: 50%;" />

  

* ### sum 

![image-20220324164025468](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220324164025468.png)

![image-20220324164034717](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220324164034717.png)![image-20220324164040230](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220324164040230.png)

收敛域取交集  例如上图种 1/s+2 Re（s）>-2,  1/s+1 Re(s)>-1   所以最终R(s)>-1;

* ROC：与时域上 x（t）的值域正相关  

<img src="C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220311105659841.png" alt="image-20220311105659841" style="zoom:67%;" />

<img src="C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220311114704573.png" alt="image-20220311114704573" style="zoom:67%;" />





![image-20220316082149068](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220316082149068.png)

![image-20220415110309171](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220415110309171.png)

<img src="C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220311113735700.png" alt="image-20220311113735700" style="zoom:67%;" />

![image-20220415110532769](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220415110532769.png)

![image-20220420204837040](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220420204837040.png)

<img src="C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220316090834189.png" alt="image-20220316090834189" style="zoom:67%;" />

①求积分用1/s处理  即可得到从脉冲信号 转换到连续信号   ② 交换律可用

![image-20220414200239456](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220414200239456.png)

y(t) = H(s) x(t);如果经过变换的话

![image-20220414201248547](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220414201248547.png)



![image-20220414201711438](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220414201711438.png)

![image-20220414201545412](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220414201545412.png)

## **z变换**

* ### Standard form



对于R（Delay） 函数比较常用   离散式的变换

<img src="C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220316081410165.png" alt="image-20220316081410165" style="zoom: 67%;" />

<img src="C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220316081722745.png" alt="image-20220316081722745" style="zoom:67%;" />



![image-20220415110710870](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220415110710870.png)![image-20220415110919264](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220415110919264.png)

![image-20220415111626490](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220415111626490.png)

![image-20220415111809600](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220415111809600.png)

（能如此化简得条件是|α|<|z| 即收敛域  一个圆  外部）

![image-20220324201518736](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220324201518736.png)

![image-20220325110614085](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220325110614085.png)

右边信号 -> stable -> ROC includes |z| = 1; -> poles are inside unit circle



* ### Calculation

<img src="C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220316082219757.png" alt="image-20220316082219757" style="zoom:67%;" />

<img src="C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220316084437196.png" alt="image-20220316084437196" style="zoom:67%;" />

如果在化简时未能化成标准形式 则可以如此**再操作一下**化成标准形式

**里式*z  外式 /z （相当于延时）**

或者转换为R模式  一个数字一个数字的看

![image-20220324202849547](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220324202849547.png)

<img src="C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220324203556402.png" alt="image-20220324203556402" style="zoom:33%;" />

于S域里的  x轴边界 相当于 这里的unit circle （单位圆）

* ### 小总结

![image-20220316090041115](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220316090041115.png)



## 卷积

* ### Basic

  离散：

  ![image-20220325102245263](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220325102245263.png)

  将x[k]（x[n]）不动 ， h[n-k]为x[k]相反 并一个个右移 与x[k]相乘相加。

  

  连续

  ![image-20220325102723738](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220325102723738.png)

  ![image-20220325103344226](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220325103344226.png)

* ### Calculation

  ![image-20220325104552312](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220325104552312.png)![image-20220325104555854](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220325104555854.png)

  ![  yyyhhhh](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220325104440883.png)

  

  ![image-20220331204504656](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220331204504656.png)

  满足t>c  c>0所以此时积分范围为0-c.

  ![image-20220414200956786](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220414200956786.png)![image-20220401192208226](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220401192208226.png)

  ![image-20220325113221154](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220325113221154.png)

  

  ![image-20220325113544038](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220325113544038.png)

  ![image-20220401193441186](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220401193441186.png)

  ![image-20220401192922227](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220401192922227.png)
  
  ![image-20220401193232826](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220401193232826.png)
  
  ![image-20220401193554241](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220401193554241.png)
  
  
  
  根据ht 判断系统的稳定性
  
  
  
  ![image-20220325113959409](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220325113959409.png)
  
  ![image-20220325114124648](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220325114124648.png)
  
  
  
  ![image-20220325114149373](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220325114149373.png)
  
  此时只是将1/(2+2j) 换成了1/（模长×角度）的形式
  
  

## Control

**concept**: system with feedback

![image-20220408103446022](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220408103446022.png)

![image-20220408103504379](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220408103504379.png)

![image-20220408105544236](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220408105544236.png)

![image-20220414212650579](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220414212650579.png)

# Fourier series

## 1.basic rules



下述3个式子为基本的

![image-20220502172651488](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220502172651488.png)

![image-20220502174632556](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220502174632556.png)

最后一个式子可以通过cos 和sin 的基恩转化为e的形式， 再加上计算w0 计算出来

<img src="C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220605132556347.png" alt="image-20220605132556347" style="zoom:50%;" />



先欧拉展开：cos 1/2 加  sin 1/2j 正-负

时域上连续 频域上离散：

傅里叶基数展开ak是代表不同的谐波的分量

xt为real信号：性质——————

- x(t) = x*(t)  

- ak* = a-k

- H（ejw) = H*(e-jw);

  ![image-20220605132029975](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220605132029975.png)

example:

<img src="C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220605132303087.png" alt="image-20220605132303087" style="zoom:50%;" />

<img src="C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220502181658548.png" alt="image-20220502181658548" style="zoom:50%;" />



## 2.calculative rules

求导时

![image-20220502180006842](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220502180006842.png)



所以求导时的系数为 求导前ak * k j w

如果求积分 则为ak /k j w

**跟拉普拉斯一样**

![image-20220605133257045](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220605133257045.png)

应用在次，锯齿信号为方波信号的积分形式，所以/jkw就行

## 3.neccesary conditions 

<img src="C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220502184004618.png" alt="image-20220502184004618" style="zoom:50%;" />

任意一个周期内，他是绝对可积的

![image-20220502184353027](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220502184353027.png)

最大最小值的个数为有限个

## 4.正交分解

![image-20220502184848020](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220502184848020.png)![image-20220502184855594](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220502184855594.png)

做一个点乘

![image-20220605134731233](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220605134731233.png)

证明出谐波之间是正交的状态

是否正交的判断：

将2个信号求乘积 的 在某一个周期积分 看是否为0；

- real 信号

  （共轭等于本身）直接相乘 取一个是周期的积分 查看是或否等于0

- imaginary 信号

  取共轭，相乘，取一个周期的积分查看是否 = 0；

找出规律，给出的信号T必须是该信号的周七的整数倍才能正交

## 5.非周期信号展开

周期T 趋近于无穷

①如果为有限的区间内有值，则拓展为周期信号  周期逐渐趋近无穷

![image-20220605145708534](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220605145708534.png)

![image-20220605145801969](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220605145801969.png)

|x(t)|^2 =  x(t) 乘 x* (t)

x*(t) = 右边式子其中的改为X *（jw）e^(-jwt);



![image-20220605150503837](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220605150503837.png)

替换的前提是ROC包含jw轴（绝对可积）收敛

![image-20220605150602781](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220605150602781.png)

图形比对：

![image-20220605213626613](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220605213626613.png)



时域上越宽  频域上越窄

频域上X（0） 对应的点，求时域上的面积即可，关系到高度

时域上x（0）![image-20220605214607802](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220605214607802.png)

对应的是红色三角形的面积 **/ 2 pi**

![image-20220605214727078](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220605214727078.png)



## 6.对偶性

![image-20220605220102395](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220605220102395.png)

如果有T0 的偏移， 那么还可以将2边的T0 都换成w0

看出来形状是成对出现的  频域（时域）上是矩形，那么时域（频域）上都会是 波形图

<img src="C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220605222504447.png" alt="image-20220605222504447" style="zoom:50%;" />

![image-20220605223128954](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220605223128954.png)

![image-20220605223231789](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220605223231789.png)

![image-20220605224355167](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220605224355167.png)

周期信号的傅里叶展开和傅里叶变换

## 7.卷积

![image-20220605235834437](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220605235834437.png)

![image-20220606024233508](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220606024233508.png)

分析相移：

利用H(jw)来分析  转换成e的形式，

<img src="C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220606001149066.png" alt="image-20220606001149066" style="zoom:67%;" />

如图是H（jw） = jw的例子

u（t）的h（t）



![image-20220606002054364](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220606002054364.png)



![image-20220606002713540](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220606002713540.png)

***判断是否为casual  h（t） 应该 = 0 当 t  < 0 时***

![image-20220606003622126](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220606003622126.png)

调制

![image-20220606003420231](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220606003420231.png)

利用性质的简便计算

<img src="C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220606152903900.png" alt="image-20220606152903900" style="zoom:50%;" />

三角波可以转换为矩形创的宽度来进行卷积

<img src="C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220606152939433.png" alt="image-20220606152939433" style="zoom:50%;" />

## 8.能量计算

![image-20220606003839900](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220606003839900.png)

## 9.filter

![image-20220606005411890](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220606005411890.png)

用公式看向量的比值与1比较

![image-20220606004945195](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220606004945195.png)

# 离散傅里叶变换



![image-20220606021653826](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220606021653826.png)

![image-20220606021914935](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220606021914935.png)

通过简单的向量比值判断  高通/低通

如果对于DT的信号，是实数real信号

- x*(t) = x(t);
- ak * = a-k
- H(e  jo) = H*(e -jo);

下main的cos 的变换也是利用了这一性质  相移就是H（ejo）的相

![image-20220606022817237](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220606022817237.png)

![image-20220606123457499](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220606123457499.png)

在单位⚪上的z变换

<img src="C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220606023054454.png" alt="image-20220606023054454" style="zoom:50%;" />

0 对应 low pi 对应high freq

![image-20220606025228343](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220606025228343.png)

![image-20220606024959130](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220606024959130.png)



## 1.展开

O = 2 pi / N

![image-20220606124253905](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220606124253905.png)

<img src="C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220606025840840.png" alt="image-20220606025840840" style="zoom:80%;" />

相当于把⚪做N等分

所以离散的信号的展开对应的项是有限的

![image-20220606124458106](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220606124458106.png)

![image-20220606140530003](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220606140530003.png)

![image-20220606133416714](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220606133416714.png)

![image-20220606134213207](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220606134213207.png)



跟CT最大的区别是ak止呕有限的N个

同样a0具有特殊性， 求x[n] 在一个周期内的和就行 再 / N

![image-20220606134701774](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220606134701774.png)

利用正交性和向量的线性代数计算求

![image-20220606134813107](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220606134813107.png)

## 2.展开例子

①方波信号

![image-20220606140038631](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220606140038631.png)

![image-20220606140049584](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220606140049584.png)

## 3.非周期的DT信号

![image-20220606141425583](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220606141425583.png)

同样的推理方式，先周期化，再将N 趋近于无穷

此时也可以利用跟z变换的相似性，来判断傅里叶变换的运算性质

![image-20220606141754719](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220606141754719.png)

## 4.运算方法

![image-20220606142509655](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220606142509655.png)

可以将一个e 和j 提出来 造成内部有可以组成cos 或 sin 的形式组合

# sum

![image-20220606143329245](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220606143329245.png)

![image-20220606145547552](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220606145547552.png)

![image-20220606152358422](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220606152358422.png)

## 1.频域上采样

**在原信号上用xt * pt（卷积）**

![image-20220606170459984](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220606170459984.png)

![image-20220606170727617](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220606170727617.png)
$$
 P（jw) = Σ 2 pi / T σ（w - kw0)
$$
最后Z = P * X 即为结果

所以得出结论：

**再时域上的周期话  =  频域上的周期采样**

![image-20220606171132662](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220606171132662.png)

## 2.时域上的采样

![image-20220606172014305](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220606172014305.png)

![image-20220606172334483](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220606172334483.png)

相当于在频域上的卷积

得到结果为原信号的周期话后的信号



![image-20220606172527848](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220606172527848.png)

## 3.DT的频域上的采样

也是时域上的周期话

与周期信号进行一个卷积

## 4.DT时域上的采样

## 5.对偶性

DTFS

![image-20220606173445099](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220606173445099.png)

![image-20220606173454245](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220606173454245.png)

![image-20220606174143114](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220606174143114.png)

连续时间周期信号   对应离散频域

离散信号 对应 周期频域

## 6.能量普

![image-20220606174607794](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220606174607794.png)

![image-20220606174616595](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220606174616595.png)

# 运算

## 1.CTFS



![image-20220502172651488](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220502172651488.png)

![image-20220502174632556](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220502174632556.png)

![image-20220608132633580](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220608132633580.png)

### 1.0搭积木+时移：

![image-20220606193303859](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220606193303859.png)

如果此时搭积木中存在时移：根据性质

![image-20220606193616853](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220606193616853.png)

![image-20220606213618636](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220606213618636.png)

需要前面呈上 ejwk * t0

### 1.05 讨论ak中k特殊取值时

![image-20220606194245127](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220606194245127.png)

### 1.1求导时ak

求导时

![image-20220502180006842](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220502180006842.png)



所以求导时的系数为 求导前ak * k j w

求积分时注意：仅仅当在一个区间内  原函数的积分为0时才成立，如果不为0，那么就会是非周期的

如果求积分 则为ak /k j w

**跟拉普拉斯一样**

### 1.2.离散周期对偶

在时域频域两个域中，如果信号在一个域是周期的，那么在另一个域一定是离散的

（逆否命题）或者说如果信号在一个域是不是离散的，那么在另一个域一定是非周期的



### 1.3.特殊利用的例子

![image-20220606221242441](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220606221242441.png)

![image-20220605223128954](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220605223128954.png)

![image-20220608094938278](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220608094938278.png)

![image-20220612014955024](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220612014955024.png)

周期的方波信号 Δ = 矩形框的宽度



## 2.CTFT

![image-20220607235625870](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220607235625870.png)

|x(t)|^2 =  x(t) 乘 x* (t)

x*(t) = 右边式子其中的改为X *（jw）e^(-jwt);

![image-20220608094648844](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220608094648844.png)

①X（jw）为real 那么 x（t） real and even

② X（jw） imag 那么x（t） real and odd

③ 

基本的，在时域相乘等于在频域相卷积

### 2.0 卷积

![image-20220606024233508](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220606024233508.png)

![image-20220605235834437](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220605235834437.png)

![image-20220606003622126](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220606003622126.png)

![image-20220606002713540](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220606002713540.png)

### 2.0 对偶性

![image-20220605220102395](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220605220102395.png)

![image-20220605223231789](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220605223231789.png)

![image-20220605224355167](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220605224355167.png)

内部的常数T 换成W

### 2.1 能量

![image-20220606003839900](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220606003839900.png)

### 2.2 周期的信号

![image-20220611145532133](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220611145532133.png)

如果X（jw） 为一系列的离散冲击的化

![image-20220609172154231](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220609172154231.png)

![image-20220609172017177](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220609172017177.png)

![这里写图片描述](https://img-blog.csdn.net/20170829093743699?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvRWluc3RlbGx1bmc=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

### 特殊例子

![image-20220608094955722](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220608094955722.png)

![image-20220608130537718](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220608130537718.png)

![image-20220608130547288](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220608130547288.png)

![image-20220612022714337](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220612022714337.png)

任意周期的信号



## 3.DTFS

![image-20220606133416714](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220606133416714.png)

![image-20220606134213207](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220606134213207.png)



跟CT最大的区别是ak止呕有限的N个

同样a0具有特殊性， 求x[n] 在一个周期内的和就行 再 / N

![image-20220608015446965](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220608015446965.png)

### 3.1对偶性

![image-20220606173445099](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220606173445099.png)

![image-20220606173454245](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220606173454245.png)

### 例子

![image-20220608132756239](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220608132756239.png)

## 4.DTFT

![image-20220612183153890](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220612183153890.png)卷积公式

![image-20220608132558251](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220608132558251.png)

![image-20220606141425583](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220606141425583.png)

![image-20220609001904276](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220609001904276.png)

### 例子

![image-20220608134514377](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220608134514377.png)

![image-20220608132809086](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220608132809086.png)

![image-20220608132842879](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220608132842879.png)

![image-20220612020809069](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220612020809069.png)







![image-20220606142509655](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220606142509655.png)

可以将一个e 和j 提出来 造成内部有可以组成cos 或 sin 的形式组合



# sampling

## 1sampling（频域上卷积）

### 1.0xt ->xd[n]-> xp(t)





<img src="C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220609173516308.png" alt="image-20220609173516308" style="zoom:40%;" /><img src="C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220609173617030.png" alt="image-20220609173617030" style="zoom:67%;" />

![image-20220610012635094](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220610012635094.png)

![image-20220611140742442](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220611140742442.png)

![image-20220609174442667](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220609174442667.png)[]()

如果换成一个连续信号xp(t)

是： 将周期的连续信号进行一个采样得到的 / 将离散且周期的信号进行一个脉冲处理

傅里叶变换之后的是Xp（jw）

发现仅仅是横轴发生了变化

![image-20220609190353208](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220609190353208.png)



![image-20220610012755500](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220610012755500.png)

### 1.1xp（t） -> x(t)



![image-20220609190853444](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220609190853444.png)

此时我们发现，第一个三角形顶点对应的横坐标为 ws

而一个周期内有值区间为[-wm,wm];  此时wm = ws / 2;

我们发现在ws - wm >= wm 时 才不会发生值重叠 

即ws > 2wm

通过一个低通滤波器就行了

![image-20220609191142952](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220609191142952.png)

## 2混叠现象

![image-20220610005220527](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220610005220527.png)

1次谐波 f = 10k Hz

8 次   80k

![image-20220610005304918](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220610005304918.png)

80 kHz 时  88 - 80 = 8 kHz;

输出不能超过fs / 2 否则反转

### 2.0抗混叠处理

<img src="C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220610005933516.png" alt="image-20220610005933516" style="zoom:50%;" />



<img src="C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220610010006729.png" alt="image-20220610010006729" style="zoom:50%;" />

先滤掉可能发生混叠的高频部分

## 3.interpolation （时域上卷积）

不同interpolation 的方法区别在 不同的ht

![image-20220610010632914](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220610010632914.png)

## 4.CT -> DT -> CT

![image-20220610012254780](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220610012254780.png)

![image-20220610014625282](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220610014625282.png)



离散时间内的大Ω， =  连续时间小w * 采样的周期T

## 5.离散时间采样

![image-20220611135324138](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220611135324138.png)

在时域上是相乘  p的周期为Np

<img src="C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220611143218161.png" alt="image-20220611143218161" style="zoom: 67%;" /><img src="C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220611143309690.png" alt="image-20220611143309690" style="zoom: 67%;" />



![image-20220611223430384](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220611223430384.png)

![image-20220611224224075](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220611224224075.png)


$$
T= 3
$$
![image-20220611224448448](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220611224448448.png)

T倍放宽了信号，如果是Xb的化

**时域上越宽  频域上越窄**

## 作业

![image-20220610012635094](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220610012635094.png)

<img src="C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220609173617030.png" alt="image-20220609173617030" style="zoom:67%;" />

![image-20220611140742442](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220611140742442.png)

![image-20220609174442667](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220609174442667.png)[]()

<img src="C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220612175227858.png" alt="image-20220612175227858" style="zoom:50%;" />

![image-20220610014625282](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220610014625282.png)



缺少对离散时间采样的笔记



# Modulation

![image-20220612010316751](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220612010316751.png)

cos的傅里叶转换幅度为pi

Y的幅度为1/2

（因为卷积中还有一步要/2pi）

中间幅度为1/2 左右两边为1/4

（因为卷积中还有一步要/2pi）

最后过一个低通滤波器后再*2

![image-20220612014415812](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220612014415812.png)

![image-20220612023014167](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220612023014167.png)

对应任意的周期T的调制信号，最后出来的信号为Y

## 离散信号调制

![image-20220612015547738](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220612015547738.png)

区别在于离散时间的频域周期为2 * pi

![image-20220612020431598](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220612020431598.png)



如果此时换成调制信号为cos[wc * n]

![image-20220612020558219](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220612020558219.png)



任意信号调制

![image-20220612021529638](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220612021529638.png)

要求 wc > 2 wm   2 pi / N > 2 * wm --->  wm < pi / N;





















































# Matlab

* ## ②特殊变量


​	

<img src="C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220304102230234.png" alt="image-20220304102230234" style="zoom:80%;" />

```matlab
a=complex(real,imag);%%生成复数
angle(x)%%x为复数 返回角度  
```

* ## ④矩阵输入

  ![image-20220304102907458](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220304102907458.png)

  分行符为  ’；’分号 或直接回车。

  ②语句生成：

  ```matlab 
  a=[1:2:10%%from 1 to 10 等差2  -> 1 3 5 7 9
  a=10:20%%10 11.....20  
  a=linspace(1,10,10) %% 1 2 3 4 5 6 7 8 9 10 (n1,n2,n)从n1->n2 数据数量为n
  a=logspace(1,3,3)%% 相当于从10^1 to 10^3 数量为3. ->10 100 1000
  ```
  
  

![ ](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220304103310387.png)

​		③load数据  不含文本  仅为逗号与space隔开

* ## ⑤矩阵运算

```matlab
.'%%不含共轭处理转置
'%%含共轭处理的转置
```

​		

<img src="C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220304104559072.png" alt="image-20220304104559072" style="zoom:50%;" />

带点的为元素级别的运算

```matlab
inv(A)%%求逆  inverse
det(A)%%求行列式 
A(m,n);
A(:,n);
A(m,:);
A(m1:m2,n1:n2);%子矩阵
A(:)%%长列失量
[m.n]=size(A);
rank(A);%%秩
-------------------
find(condition);
sort(tuple);
```

* ## ⑥脚本&函数

  ```matlab
  %%function"
  while(condition)
  	...
  	...
  end
  [s,m]%输出s，m
  function[out,out....]=filename(in1,in2......);
  
  for i=1:1:10%%起始值：步长：终止
  	...
  	%%  break;  跳出
  end
  
  if condition
  	....
  elseif condition
  	...
  else 
  end
  ```

  <img src="C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220304113503504.png" alt="image-20220304113503504" style="zoom:50%;" />

* ## ⑦画图

  ![image-20220304110602408](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220304110602408.png)

  <img src="C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220304110612319.png" alt="image-20220304110612319" style="zoom: 67%;" />

  ```matlab
  plot(x,y);%% for continuous function 
  legend('string1','string2'....);
  subplot(m n k);%% m行  n列  k为子图编号
  			%%subplot(2,5 5+i);
  stem(x,y);%%火柴图 discrete 若输出信号时不能省略x，否则回出现移动 （默认从1开始画图）
  
  ```

  ![image-20220304112057875](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220304112057875.png)

  x重新赋值问题 与zeros函数的使用

  ![image-20220304112253096](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220304112253096.png)

  时移信号x2的表达 （nx2只是画一个范围 包含特征即可 如此时只要包含到-2即可）

## 基本信号

①时移信号

```matlab
t=0:0.5:10;
%%x=u(t-2);
x=zeros(1,length(t));
x(5:end)=1;
```




## lab2



```matlab
%%延时型
filter (b,a,x);%%产生滤波信号  即输出y[n]

%%积分型
lism(b,a,x,t);%%对于x输入的积分响应 不一定是δ or u 函数，更具有普遍性
impulse(b,a,t)%%对于时域在t上的冲击响应 x=δ(t)
step(b,a,t)%%时域在t上的节约响应 x=u(t)
```

![image-20220318101044583](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220318101044583.png)

![image-20220318101055478](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220318101055478.png)

积分计算

![image-20220318101110889](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220318101110889.png)

```matlab
a=[1,2];
b=1;
t=0:0.5:10;
step(b,a,t);
x=(5:end)=1;
y=lsim(b,a,x,t);//产生h(t) 
%%%%%%%%%%%%%%%%%%%%%%%%%%%%
impulse (b,a,t);
```

```
a=[1,2];
b=1;
x=
```

## lab3

* roots

  求方程的根；

  ```matlab
  a = [1 2 3];
  zp = roots(a);%%求 s^2+2*s+3 = 0  的根
  
  
  %%如果涉及底边2个多项式相乘 用卷积；
  a1=[1 2 10];
  a2=[1 2];
  a = conv(a1,a2);
  ap=roots(a);
  
  %%可能设计到虚数  注意打印的时候
  plot(real(zp),imag(zp),'o');
  ```

* pzplot

  pole-zero diagram for LTI ;

  b-> denominators vector;

  a>nominator vectro;

  ```matlab
  pzplot(b,a,1);
  %%直接画出来节点
  ```

  
