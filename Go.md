# Go

# chap 1

- No variables that  is never used in a func

  - to avoid this , use _, to represent the useless one

- strings.Join 

  (slice, gap variable);

  
  
  
  
  

# if

Like `for`, the `if` statement can start with a short statement to execute before the condition.

```go
if v := math.Pow(x, n); v < lim {
		return v
	}
```

Variables declared inside an `if` short statement are also available inside any of the `else` blocks.

# for

```go
pow := []int {1, 2, 3, 4}
for i,v := range pow{
	//i denotes to index
	//v denotes to value
	//if any of these is useless in this scope ,just use _ to replace it, in case of collapse
}
//range pow[1 : 3] 也行
```



# struct

```go
type Vertex struct {
	X int
	Y int
}
	fmt.Println(Vertex{1, 2})
//pointer of the struct
v := Vertex{1, 2}
	p := &v
	p.X = 1e9
	fmt.Println(v)

var (
	v1 = Vertex{1, 2}  // has type Vertex
	v2 = Vertex{X: 1}  // Y:0 is implicit
	v3 = Vertex{}      // X:0 and Y:0
	p  = &Vertex{1, 2} // has type *Vertex
)

func main() {
	fmt.Println(v1, p, v2, v3)
}
// result : {1 2} &{1 2} {1 0} {0 0}

```

# slice

①dynamically-sized array

```go
	primes := [6]int{2, 3, 5, 7, 11, 13}

	var s []int = primes[1:4]
	fmt.Println(s)
```

②**not store any data**

```go
a := names[0:2]
b := names[1:3]
fmt.Println(a, b)
b[0] = "XXX"
fmt.Println(a, b)
fmt.Println(names)
/*result :[John Paul George Ringo]
[John Paul] [Paul George]
[John XXX] [XXX George]
[John XXX George Ringo]*/
//改变slice 里的东西 那么array里也会跟着改变

```

③parameters

- length: number of elements it contains
- capacity: number of elements in the underlying array (**counting from the 1st element from slice**)

use len(s) cap(s) to get the data

④空slice nil

⑤make

```go
b := make([]int, 0, 5) // len(b)=0, cap(b)=5
b := make([]int) // 最原始的初始化
b := make([]int,5) // len = 5, cap = 5	
b = b[:cap(b)] // len(b)=5, cap(b)=5
b = b[1:]      // len(b)=4, cap(b)=4
```

⑥ 多维slice

```go
board := [][]string{
		[]string{"_", "_", "_"},
		[]string{"_", "_", "_"},
		[]string{"_", "_", "_"},
	}
```

## append

```go
func append(s []T, vs ...T) []T
	s = append(s, 2, 3, 4)

```

# map

```go
var m map[string]Vertex
func main(){
	m = make(map[string]Vertex)
	m["Bell Labs"] = Vertex{
		40.68433, -74.39967,
	}
	fmt.Println(m["Bell Labs"])
}
// literals 
var m = map[string]Vertex{
	"Bell Labs": Vertex{
		40.68433, -74.39967,
	},
	"Google": Vertex{
		37.42202, -122.08408,
	},
}
var m = map[string]Vertex{
	"Bell Labs": {40.68433, -74.39967},
	"Google":    {37.42202, -122.08408},
}

```

获取和改变

```go
delete(m, key)
elem, ok := m[key]
//elem is the value of m[key] if ok is true else elem = 0
//ok is (key is in the map m ?) 
```

# func

```go
//func 可作为变量进行赋值， 传参
func compute(fn func(float64, float64) float64) float64 {
	return fn(3, 4)
}

func main() {
	hypot := func(x, y float64) float64 {
		return math.Sqrt(x*x + y*y)
	}
	fmt.Println(hypot(5, 12))

	fmt.Println(compute(hypot))
	fmt.Println(compute(math.Pow))
}
//func 也可用于匿名函数
func adder() func(int) int {
	sum := 0
	return func(x int) int {
		sum += x
		return sum
	}
}

func main() {
	pos, neg := adder(), adder()
	for i := 0; i < 10; i++ {
		fmt.Println(
			pos(i),
			neg(-2*i),
		)
	}
}
/*0 0
1 -2
3 -6
6 -12
10 -20
15 -30
21 -42
28 -56
36 -72
45 -90
*/
```

# method

类似于class里的function

只要有type 就能做method 的前置参数

```go
type Vertex struct {
	X, Y float64
}
func (v Vertex) Abs() float64 {
	return math.Sqrt(v.X*v.X + v.Y*v.Y)
}
// v.Abs() could be application

func Abs(v Vertex) float64 {
	return math.Sqrt(v.X*v.X + v.Y*v.Y)
}
//Abs(v) could be application

//pointer receivers 此时可以通过函数改变参数的value
//second reason : avoid copy the value , more efficient
func (v *Vertex) Scale(f float64) {
	v.X = v.X * f
	v.Y = v.Y * f
}
var v Vertex
v.Scale(5)  // OK for convenience, equivalent to (&v).Scale(5)
p := &v
p.Scale(10) // OK
```

# Interfaces

C++可以用虚基类表示， 

go中的interface 更接近oop中的 方法签名的集合，这些方法可以被**任一**类型通过方法实现 

因此interface 只是对象行为的声明 非定义 **仅仅表示方法签名（函数模型**

- 方法签名

  由方法名， 输入参数， 返回值 三部分组成

如果你使用的类型 实现了 一个interface 中的 **所有**方法签名， 那么golang就默认你实现了这个interface

- 实现interface

  **不一定需要只有interface里的函数  ，只要包含就行**

  **类似class 但是不那么严格  不必要里面的所有（变量类型 函数）均相同   只需要函数签名一致即可，  类似一个军队 ，不用所有人都长得一样，只要能打仗的就是军人**

  比如我们有一个interface shape

  ```go
  type shape interface{
  	Area() float64
  	Parameter() float64
  }
  ```

  利用一个struct 实现interface

  ```go
  type Rect struct {
  	width float64
      height float64
  }
  func (r Rect) Area() float64 {
      return r.width * r.height
  }
  func (r Rect) Parameter float64 {
      return 2 *(r.width + r.height)
  }
  //cuz Rec has Area() and Parameter() func so it achieve interface Shape successfully
  func main() {
      var s Shape
      s = Rect{5.0, 4.0}
      r := Rect{5.0, 4.0}
      //s == r
      //s的 %T 为 main.Rect value 是{5 4} 可以成功调用area 和 Parameter
  }
  ```

  

```go
type I interface {
	M()
}
func (t *T) M() {
	fmt.Println(t.S)
}

type F float64

func (f F) M() {
	fmt.Println(f)
}
```

different type for different method

## empty interface

```go
func describe(i interface{}) {
	fmt.Printf("(%v, %T)\n", i, i)
}
//mustn't be nil 
```

## Type assertion

判断这个interface 中是否含有这个type 

为了保险起见  最好是按照assertion 的形式来进行 interface 作为右值的 赋值动作

```go
t := i.(T)
t, ok := i.(T)

package main

import "fmt"

func main() {
	var i interface{} = "hello"

	s := i.(string)
	fmt.Println(s)

	s, ok := i.(string)
	fmt.Println(s, ok)

	f, ok := i.(float64)
	fmt.Println(f, ok) // f = 0, ok = false

	f = i.(float64) // panic
	fmt.Println(f)
}

```

## 重构

```go
func (p Person) String() string {
	return fmt.Sprintf("%v (%v years)", p.Name, p.Age)
}
//重构 Stringer
/*type Stringer interface {
    String() string
}*/
```

# error

is a interface

error != nil 说明有error else 无

# gopath

①src里存放开发的代码

代码的package需要和目录相同

```go
// $GOPATH/src/mymath/sqrt.go 原始碼如下：
package mymath

func Sqrt(x float64) float64 {
    z := 0.0
    for i := 0; i < 1000; i++ {
        z -= (z*z - x) / (2 * x)
    }
    return z
}
```

②编译应用

- 进入对应套件的目录 执行 go install

- 或者进入任何目录下执行go install $yourpkg

  

![image-20220805214054647](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220805214054647.png)

# mod

- init 
- tidy
- download

函数的private or public

首字母

- 小写 只能在当前package使用
- 大写 可以在外卖呢
