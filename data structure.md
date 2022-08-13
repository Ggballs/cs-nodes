

![image-20211115184831202](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20211115184831202.png)

# 1.Stack and queue

```c
int isEmpty(Stack S);
Stack CreateStack();
void DisposeStack(Stack S);
void MakeEmpty(Stack S);
void Push(ElementType X,Stack S);
ElementType Top(Stack S);
void Pop (Stack S);

```

# 2.Tree

Each Node could have an arbitrary number of children

Node with ZERO child == **leaves**

Nodes with the same parent are **siblings**;

-------

**path:**

n1->nk ==a sequence of nodes n1,n2......nk;

length =k-1;

**depth:**

root's depth =0;

**height:**

the height of ni is the length of the longest path from ni to a leaf;

all leaves 的 height=0

height of the tree == height of the root;

**definition**:

```c
struct TreeNode{
    int Element;
    PtrtoNode firstChild;
    PtrtoNode NextSibling;
}
```

**ancestor<->descendant**

2 files in different directories could share the same name.

------------------------------------------------------

## Binary Tree

```C
struct node{
elementtype element;
node* Left;
node* Right;
}Treenode;
```

could not have more than 2children;

## Judgement on substructure 

```c++
bool recur(treenode* a,treenode* b){
    if(!b)return true;
    if(!a)return false;
    return a->val==b->val&&recur(a->left,b->left)&&recur(a->right,b->right);
}
bool check(treenode* a,treenode* b){
    if(!b)return false;
    return recur(a,b)||check(a->left,b)||check(a->right,b);
}
```

## judgement on symmetry

1. 递归的函数要干什么？

- 函数的作用是判断传入的两个树是否镜像。
- 输入：TreeNode left, TreeNode right
- 输出：是：true，不是：false

1. 递归停止的条件是什么？

- 左节点和右节点都为空 -> 倒底了都长得一样 ->true
- 左节点为空的时候右节点不为空，或反之 -> 长得不一样-> false
- 左右节点值不相等 -> 长得不一样 -> false

1. 从某层到下一层的关系是什么？

- 要想两棵树镜像，那么一棵树左边的左边要和二棵树右边的右边镜像，一棵树左边的右边要和二棵树右边的左边镜像
- 调用递归函数传入左左和右右
- 调用递归函数传入左右和右左
- 只有左左和右右镜像且左右和右左镜像的时候，我们才能说这两棵树是镜像的

1. 调用递归函数，我们想知道它的左右孩子是否镜像，传入的值是root的左孩子和右孩子。这之前记得判个root==null。

   

## Tree Traversals

visit each node exactly once.

```c
void preorder(Treendoe tree){
if(tree){
	vist(tree);
    for(each child C of TREENODE)
        preorder(C);
}
}
/*****preorder traversal: Root->children->descendant...**********/
void postorder(Treenode tree){
    if(tree){
        for(each child C of TREENODE)
            postorder(C);
        visit(tree);
    }
}
/**************************************************************************/
//interative version
vector<int> preorder(Node* root){
    stack<Node*> s;
    vector<int> ans;
    if(!root)return {};
    s.emplace(root);
    while(s.size()){
        Node* now = s.top();
        s.pop();
        if(now->right)s.emplace(now->right);//先压入右节点
        if(now->left)s.emplace(now->left);
        ans.emplace_back(now->val);
    }
    return ans;
}
//后续traversal that is first left then right,at last ,use reverse(ans.begin(),ans.end())
vector<int> inorderTraversal(Node* root){
    vector<int> ans;
    if(!root)return {};
    stack<Node*> s;
    Node* node = root;
    while(!s.empty()||node){
        while(node){
            s.emplace(node);
            node=node->left;
        }//找到对应最靠左的节点 并压入目前无法输出的节点
        if(s.size()){
            node=s.top();//如果此时刚打完左边节点  此时应该是中间节点
            ans.emplace_back(node->val);
            s.pop();//打表基本操作
            node=node->right;
            //找右节点打 如果为空会下一步直接跳过while，再到s.top（）即父节点上
        }
    }
}
```

- 先根遍历：若树非空，则先访问根结点，再按照从左到右的顺序遍历根结点的每一棵子树。**这个访问顺序与这棵树对应的二叉树的先序遍历顺序相同**。

- 后根遍历：若树非空，则按照从左到右的顺序遍历根结点的每一棵子树，之后再访问根结点。**其访问顺序与这棵树对应的二叉树的中序遍历顺序相同**。

- ![这里写图片描述](https://imgconvert.csdnimg.cn/aHR0cDovL2ltZy5ibG9nLmNzZG4ubmV0LzIwMTYxMDE1MTcyNDE3MDA4?x-oss-process=image/format,png)

- 根据这幅图：
  树的  先根遍历：A-B-E-F-G-C-H-D-I-J
  对应的二叉树的先序遍历：A-B-E-F-G-C-H-D-I-J

  二者是一致的。

  树的后根遍历：E-F-G-B-H-C-I-J-D-A
  对应的二叉树的后序遍历：G-F-E-H-J-I-D-C-B-A
  对应的二叉树的中序遍历：E-F-G-B-H-C-I-J-D-A(与树的后根遍历相一致)

## threaded tree

 如果一个结点的左孩子,为空，则指向它的前驱结点。 

如果一个结点右孩子为空，则指向它的后继。

8
12 11 20 17 1 15 8 5
12 20 17 11 15 8 5 1

## BST 二分查找树

左边的数据域<根节点<右边数据域

查找、插入、建树、删除。

1.查找

①root空，失败，返回

②x==root->data. return root;

③x< root->data  search root->left;

④x>......right;

```c
Treenode* search(Treenode* T,int x){
    if(T==NULL){
        printf("No result")
        return'
    }
    else{
        if(x>T->element) return search(T->right,x);
        else if(x==T->element)return T;
        else return search(T->right,x);
    }
}
```

2.插入

先查找一遍，如果返回为NULL，则可以插入，如果为applicable 则无需插入

```c
void  insert(node** T,int x){//node为地址的地址，
	if(T==NULL){
        *T=createnode(x);//将T位置赋值x；
        return ;
    } ;
    if((*T)->data>x) insert(&((*T)->left),x);
    else if(T->data==x) return ;
    else insert(&((*T)->right),x);
}
```

3.建立

```c
//已知含有data[n]的数组 ，放入查找树中；
node* createTree(int d[],int n){
    node* root=NULL;
    for(int i=0;i<n;i++){
        insert(&root,d[i]);
    }return root;
}
```

4.删除

分为①查找到对应树node的地址②找到前赴  与  后继 （b）（叶节点）③删除对应node

```c++
PtrtobtreeNode_int  findmin( PtrtobtreeNode_int T) {
	while (T->left_tr) {
		T = T->left_tr;
	}return T;
}
PtrtobtreeNode_int findmax(PtrtobtreeNode_int T) {
	while (T->right_tr)T = T->right_tr;
	return T;
}
//后继续按如此处理被用来做替代的节点，知道没有子节点为止。
```

## 平衡树（AVL）





## 堆 heap

完全平衡树，从上往下，从左往右

节点值比子值高



```
downadjust(low,high): 
{	while(存在孩子节点 j<=high){
		存储最大的孩子坐标
		if（heap[child]>heap[parent]) {swap（）；并将处理点i移至 j ，j=2*i）
		else break;
}}

upadjust(low,down){
	i=high;j=i/2; j为其父亲
	while(j>=low存在父节点){
		if(heap[i]>heap[j]){swap(),处理点i移至j，j=i/2;}
		else break;
	}
}
```

① 建立heap    自上而下的适应 

```c++
 for(int i=n/2;i>=1;i--)  
     downadjust(i,n);//对于n个节点的树来说，n/2以后的都是叶节点，故而从n/2开始，向前进行downadjust
```

②删除点， 

```c++
a[node]=a[n--];//n--为去除一个元素后的n值,先替换，再适应
downadjust(node,n);
```

③添加点

```c++
a[++n]=value;
upadjust(0,n);
```



## 并查集 （UFS）

Union  Find Set

①找根节点

```c++
void findrootr(int x){
    if(S[x]==x)return x;
    else return findroot(S[x]);
}//recursive version
void findrooti(int x){
    while(S[x]!=x){
        x=S[x];
    }return x;
}//iterative version

```

②合并2个union

```c++
void union(int data[]){
    int len = sizeof(data)/sizeof(int);
    for(int i =0; i<len-1;i++){
        if(findroot(data[i])!=findroot(data[i+1])){
            S[findroot(data[i+1])]=findroot(data[i]);
        }
    }
}
```

③路径缩短

```c++
void cutdistancei(int x){
    int s=findroot(x);
    while(S[x]!=x){
        int z=x;
        x=S[x];
        S[z]=s;
    }
}//iterative version
int  cutdistancer(int x){
    if(S[x]==x)return x;
    else{
        int F=cutdistance(x);
        S[x]=F;
        return F;
    }
}//recursive version

```

# 3.图

<img src="C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20211110161153511.png" alt="image-20211110161153511" style="zoom: 50%;" />

普通联通图 n-1边

强连通图，最少n条边，形成回路

非联通图

最多![image-20211110155844589](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20211110155844589.png)

极大连通子图   ：子图必须连通，且保留尽可能多的边

极大强连通子图   ：子图必须强连通，且保留尽可能多的边

<img src="C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20211110161235402.png" alt="image-20211110161235402" style="zoom:33%;" />

<img src="C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20211110161912133.png" alt="image-20211110161912133" style="zoom:33%;" />

每个边带着权值的图叫带权图，也称为网

## 邻接矩阵

无向图矩阵为对称矩阵

有向图不一定

```c++
typedef struct{
    char Vex[Maxvertex];//存放对应节点字母与数字的关系
    bool Edge[Maxvertex][Maxvertex];//int 型也行，bool能更小占存
    int vexnum,arcnum;
}Mgraph
```

无向图

度=遍历对应第i行的非0元素数量

有向图

求入度  遍历 对应第j列的非0元素的数量

求出度  遍历 对应第i行的非0元素的数量

度=入度+出度

### 权值矩阵

有权值时需要用无穷来表达2点之间没有连接

<img src="C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20211110164315366.png" alt="image-20211110164315366" style="zoom:67%;" />

### 求i到j点对应长n路径个数

A^n的元素A^n【i】【j】表示从i到j的长度为n的路径数目

![image-20211110164644106](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20211110164644106.png)

存放空间复杂度为O(n*n)

## 邻接表

```c++
//边、弧
typedef struct ArcNode{
	int ptrtovtx;//指向哪个节点
    struct ArcNode * next;//指向下一条Arc的指针
    int info;//边权值
}ArcNode;
//顶点 vertex
template<class vertextype>
typedef struct Vnode{
    vertextype nodedata;
    ArcNode *Arclist//第一条边/边的链表
}Vnode,Nodearray[MaxVertexNum];
//图
typedef struct {
    Nodearray vertexes;
    int vexnum,arcnum;
}Algraph;
```



找出被指向A点的arc需要遍历全部的边

## 图的基本操作



```c++
bool Adjacent(graph G,int x, int y);//判别是否存在边,<x.y>
Neighbors(graph G, int x);//列出x邻接的边   
void InsertVertex(graph G,int x);//插入顶点x
void DeleteVertex(graph G, int x);//删除 x
邻接矩阵 ：点x对应 列行全部变零  vertex结构体中加入bool变量，判别这个东西是否是一个空顶点而避免了数组元素的过多移动
邻接表 首先删除顶点的链表节点  后遍历全部的边 删除对应入边
void AddEdge(graph G,int x,int y);//
int firstNeighbor(graph G, int x)//找出第一个邻接点
int NextNeighbor(graph G,int x,int y);//找出y之后的下一个顶点x的邻接点，无则返回-1
Get_edge_value(G,x,y);
Set_edge_value(G,x,y);
```

)



+ ## 广度优先

树的是layerordertraversal  

图里有可能出现点的二度重访问  ------>（可标记节点）

设置辅助队列

```c++
FristNeighbor(G,x);
NextNeighbor(G,x,y);
```

![image-20211122004212185](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20211122004212185.png)

```c++
void BFS(Mgraph G, int v) {
	queue<int> q;
	q.push(v);
	G.Vex[v] = 1;
	while (!q.empty()) {
		int now = q.front();
		cout << now << "|";
		q.pop();
		for (int i = 0; i < G.vexnum; i++) {
			//for(int i = FirstNeighbor(G,v);i>=0;i=NextNeighbor(G,v,w){}
			if (G.Vex[i] == 0) {
				q.push(i);
				G.Vex[i] = 1;
			}
		}
	}
}
```

广度优先生成树 对表不唯一 （因在表达出边时，边>=2时，顺序不唯一）对图唯一

+ ## 深度优先

树的深度优先是preorder

```c++
void preorder(tree *R){
	if(R) {visit(R);
    while(R的child存在){
        preorder(child);
        下一棵R的子树
    }
  }
}
```

也需设置visit[MaxVertexNum];

```c++
void DFS(Mgraph G, int v) {
		G.Vex[v] = 1;
		cout << now << "|";
		for (int i = 0; i < G.vexnum; i++) {
			//for(int i = FirstNeighbor(G,v);i>=0;i=NextNeighbor(G,v,w){
			if (G.Vex[i] == 0) {
				DFS(G, i);
				G.Vex[i] = 1;
			}
		}
	}
```

## 最短路径问题

![image-20211122010115602](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20211122010115602.png)

### Dijkstra算法

 

```c++
int final[Max],dist[Max],path[Max];
初始化 final[u]= true ;   else =false;
dist [u]=0; else =INFINITY;
path [all]=-1;
//找到目前final=false 且 dist最小的端点 u 把 final[u]=true;  
//更新u   
//对所有final == false 的vex 中 dist  若能更短，则更新 {path dist更新}
if(vis[v]=false&&G[u][v]!=INF&&d[v]>d[u]+G[u][v]) d[v]=d[u]+G[u][v];


//有负号值 时， 则不适用 dijkstra
```

### prim:

选一个点 然后并入最低weight的边所连接的点，然后看作一个整体 往外继续扩张

### kruskal:

每次选择一个最小weight的边，如果其2端有1端没有被连接，则并入。

## 最大流问题

   ford fulkerson

1.建立 一个capacity 图

2.找一条简单路径  并找到最小的x作为最大流于这条路上。

3.简单路径上的每个通路weight都 -x 并建立反向的x路径

repeat

till 没有通路

  Edmonds-Karp算法

将简单路径换成最短路径（ 看成无权图）

  dinic算法

blocking flow

level graph 从root最短走几步能到达的点就是第几级的点  同时删除掉同级别

之间的边 

①level graph： 把同level的边去掉  找到blocking way

② 建立反向blocking way 在residual gragh中

重新建立level graph  

# DP(动态规划)

​		dynamic programing

​		尽量不重复计算重复的问题

​		解决是否可行 或者最值问题

* 与recursion的区别：

  同： 有份分而治之  但区别在于dp的（子问题）有所联系， 

  不同：会有存储每个分支   

  ​			时间复杂度更小

  ```c++
  //体现记录性
  int a[n]={0};
  a[1]=1;
  for(int i = 2;i<n;i++){
      a[i]=a[i-1]+a[i-2]//避免重复运算
  }
  //优化存储空间减小  仅存储2个数字
  int a=0,b=1;
  for(int i = 0 ;i<n-1;i++){
      sum = a+b;
      b=sum
  }
  return sum;
  ```

* 与贪心的区别

  贪心的局部最优解不会储存  只会有一个值传下去（局部最优解）无法返回
  
* **做题思考方式**

  从集合角度思考： 

  状态标识 f【i】【j】 ---（区别于暴搜，时间复杂度大大降低，）

  * 集合 所有从（1，1）走到（i，j）的路线   （青蛙跳台  dp【i】）
  * 属性 Max// Min// 数量  ==（于摘花生中表示的是走到此步（i，j）时的花生最大MAX值）

  状态的计算转移

  * 转移：“来源”：如何到达的f【i】【j】

    ​						（于摘花生 中 为①最后一步从上面下来   ②从左边过来）

    ​						（若要计算2条路线时  ①左左 ② 上上③左上④上左）

  * 计算：计算式根据状态标识的  **属性**（max，min sum）

    ​				①**注意第一行第一列的特殊处理(仅在处理min（）时需要注意**

    ​				②**于2条路中注意边界问题  即若有坐标<=0 ||>n即continue**

    ​	（于摘花生中：所以计算式子即为 取二者最大值  +rid【i】【j】）



## category

* top down

  一般看到总共或者全部可能性  则用此方法

* bottom up

  



* 青蛙跳台   放入dp[]数组中保存，先初始化dp\[1\] 每次转移与dp\[n-1\]+dp\[n-2\];

  数字转换为字母多样性  只是添加了一个判断**前2个数字是否是合法的2位**

* 





# BFS

把visit() in BFS函数  以及 now 处理变化

设置遍历{

​		d[i]=INFINITY-1;//初始化路径长度

​		path[i]=-1;//i从哪个顶点过来的}

```c++
d[u]=0;//u为初始节点
in while
    int u = q.front();
	q.pop();
if(visited[i]==0){
	d[i]=d[u]+1;
    path[i]=u;
}
layerorder（）；
```

## 宏观定义与应用

最短距离（权值为1）和最小步数（带权值）问题

适用类型：求最小  

+ ## layerorder

```c++
bool st[m][n]={false};
void BFS(Mgraph G, int v) {
	queue<int> q;
	q.push(v);
	G.Vex[v] = 1;
	while (!q.empty()) {
		int now = q.front();
		cout << now << "|";
		q.pop();
		for (int i = 0; i < G.vexnum; i++) {
			//for(int i = FirstNeighbor(G,v);i>=0;i=NextNeighbor(G,v,w){
			if (G.Vex[i] == 0) {
				q.push(i);
				G.Vex[i] = 1;//tag this shit visited
			}
		}
	}
}
```

layer order每层均单行输出：

```c++
venctor<vector<int>> answer(){......
    vector<vector<int>> ans;
	while(!st.empty()){
    vector<int> temp;
    for(int size = st.size();size--;st.pop()){
        auto now->st.front();
        if(now->left)st.push(now->left);
        if(now->right)st.push(now->right);
        temp.push_back(now->val);//in a void functiono , cout<<now->val<<' ';
    }ans.push_back(temp);// if the function's return value is void,then just cout<<endl;
}return ans;
                             }
```



+ ## Flood fill

处理水塘问题 山峰问题  

随便选一个格子 注水   从一个格子中 开始BFS   依次遍历  覆盖水  直到所有的低洼的格子都被注水（分 四联通（共边） 八联通（共点）

功能：可以在线性时间复杂度内找到某个点的所有联通块



应用：池塘计数   八联通  <img src="C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20211124141939468.png" alt="image-20211124141939468" style="zoom:50%;" />

```c++
void bfs(int sx, int sy) {
	//int tt = 0, hh = 0;
	st[sx][sy] = true;
	q.push({ sx,sy });//q[0]={sx,sy};
	while (!q.empty()) {//while(hh<=tt)
		PII now = q.front();//PII now = q[hh++];
		q.pop();
		for (int i = now.x - 1; i <= now.x + 1; i++)
			for (int j = now.y - 1; j <= now.y + 1; j++) {
				if (i == now.x&&j == now.y)continue;
				if (i >= n || j >= m || i < 0 || j < 0)continue;
				if (st[i][j] )continue;
                	if(g[i][j]=='.')continue;
				q.push({ i,j });//q[++t]={i,j};
				st[i][j] = true;//visited;
			}
	}
}
```

+ ## 最短路径问题

```c++
把pre[][]加上了，只要标记了pre就行
    而且此时pre已经相当于标记了该点被走过  如果走过了就不会被再次标记，故而不会被长路径标记到， 只会标记最短路径  
    只用bfs一个起点就行
```

```c++
void bfs(int sx, int sy) {
    memset(pre[0], -1, sizeof pre);
	queue <PII> q;
	q.push({ sx,sy });
	pre[sx][sy] = { 0,0 };
	while (!q.empty()) {
		PII t = q.front();
		q.pop();
		int dx[4] = { 0,-1,0,1 }, dy[4] = { -1,0,1,0 };
		for (int i = 0; i < 4; i++) {
			int a = t.x + dx[i], b = t.y + dy[i];
			if (a >= n || a < 0 || b >= n || b < 0)continue;
			if (g[a][b])continue;
			if (!(pre[a][b].x == -1 && pre[a][b].y == -1))continue;
			pre[a][b] = t;
			q.push({ a,b });
		}
	}
}

```



+ ## 多源BFS最短距离

从每个起点出发，遍历所有的点，保留最小值 -----O(N^2)

把每个起点看成是  单源BFS起点的  距离为0  的一层节点   放入队列中

而后再一样的处理即可

但是记得 有个新数组distance[N] [N] 

每次bfs时  记得distance [a] [b] = distance[t.x] [t.y] + 1;（以及 pre

再push进queue中；  





+ ## 最小步数问题

魔板问题

利用哈希表来存放状态  unnodered_map STL

以及3个move（）  set（string state） get（）



## 双端队列BFS问题/ 优先队列BFS

双端广搜  不是”双向广搜“  其不同在还是 仅仅从一方向源头出发 ，只是利用的队列  不是单端队列 而是双端 队列  可以优化对于

电路板问题 

//注意一个小问题就是转义字符的使用 2*\==\

需要用到<deque> 用到队头  队尾输入的作用实现

不同于一般的bfs（入队时即为最小的步数选择）  此双端在出队时才是最小的步数选择

```c++
int bfs(){
    memset(dist[0],0x3f,sizeof dist);
    memset(st[0],false,sizeof st);
    deque <PII> q;
    st[0][0]=true;
    dist[0][0]=0;
    q.push_front({0,0});
    while(!q.empty()){
        PII t = q.front();
        q.pop_front();
        st[t.x][t.y]=true;
        int dx[4]={-1,-1,1,1},dy[4]={-1,1,1,-1};
        int ix[4]={-1,-1,0,0},iy[4]={-1,0,0,-1};
        char l[5]="\\/\\/";//转义符注意 
        for(int i = 0; i<4;i++){
            int a= t.x+dx[i],b=t.y+dy[i];
            int la=t.x+ix[i],lb=t.y+iy[i];
            if(a<0||a>r||b<0||b>c)continue;//点坐标与线坐标的上限判断有区别
            if(st[a][b])continue;
            if(la<0||lb<0||la>=r||lb>=c)continue
            int d = dist[t.x][t.y]+(gi[la][lb]!=l[i]);//保存距离变量

            if(d<dist[a][b]){//dijkstra 算法的一部分
                dist[a][b]=d;
                if(gi[la][lb]!=l[i]) q.push_back({a,b});
                else q.push_front({a,b});//先走 步数小的

            }
        }
    }return dist[r][c];
}
```

## 双向BFS

当图很大的时候  为了优化时间复杂度  而产生的  从终点和起点同时搜索

适用于最小步数问题  （大的时候）

```c++
while(!q1.empty()&& !q2.empty()){
	if(q1.size()>q2.size())	{
        //每次拓展队列小的那边 
    }
}
void extend(){
    取t=qa.front();
    多种变换遍历：
    	if(db[]中存在该变换)//说明a，b有交集了
            return da[t.x][t.y]+db[t.x][t.y]+1;
    	if(da[]存在)//说明之前处理过了，
            continue;
    	else{
            da[a][b]=da[t.x][t.y]+1;
            qa.push({a,b});
        }
            	
}
```



# DFS（暴搜）

* 与bfs相比

  速度快  （写的时候）

  不需要用define pair

  复杂度不可估计 但是更慢一些

  只能知道是否能够到达  不能找到最短路径

  层数比较多的时候容易爆栈

* dfs每层之间的return值可以与答案 不同 

  即处理过程中不一定ans处理值与return 值一样 可以二者并行

  ```c++
  int ans;
      int depth(TreeNode* root){
          if (root == NULL) return 0;
          int L = depth(root->left);
          int R = depth(root->right);
          ans = max(ans, L + R + 1);
          return max(L, R) + 1;
      }
  ```

  

* 最重要一点——**及时标记**  st【a】【b】=true//st【sx】【sy】=true；

  ①算一条线能走完的格子

  ②算可以走到的格子  

  ①②不同的，如何处理区别：

  ​	①必须回复现场  st【a】【b】以及cnt（可直接当作输入变量方便  或者全局变量 进行cnt++  --的变换）

  ​	②可以走到的  不用回复现场 直接ans++就行。（但是需要标记

  

  

  ---

  

* 回复现场

  是否是一连串点的集合  还是仅是否搜到一个点

  看下面的外部搜索与内部搜索

+ 内部搜索

  每个格子看作一个搜索单位 搜索到终点即可 无需回溯

+ 外部搜索

  将**整个棋盘的状态**看做一个搜索的单位，比如问是否存在一种棋子放置方式，能够使棋盘呈现如下图中右侧的状态？因此，在**对当前结点进行扩展时**，如果之前朝某个方向扩展过，则在继续扩展另一个方向时需要撤销上一步搜索对整个棋盘的影响，这个动作称为**回溯**。

  **注意每一层DFS时需要先判断是否满足终点条件再 标记格子  否则回溯不完全**

  <img src="C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20211210101956355.png" alt="image-20211210101956355" style="zoom:50%;" />

+ DFS剪枝

  1.优化搜索顺序  

  ​	优先搜索分支较少的节点

  2.排除等效冗余

  ​	12 = 21 可以排除21在已经搜索过12情况下

  ​	3.记忆化搜索（DP）//not import

  4.可行性   若已经不可行 则推出

  5.最优解剪枝  若已知道不可能最优  则退出
  
+ ----

  

```c++
void DFS(Mgraph G, int v) {
	G.Vex[v] = 1;
	cout << v << "|";
	for (int i = 0; i < G.vexnum; i++) {
		//for(int i = FirstNeighbor(G,v);i>=0;i=NextNeighbor(G,v,w){
		if (G.Vex[i] == 0) {
			DFS(G, i);
			G.Vex[i] = 1;
		}
	}
}
```

## 内部搜索

深搜  跟栈有关

判别是否可以到达  

（经典的 连通性问题）

```c++
 bool dfs(int sx,int sy){
     st[sx][sy]=true;//必须标记
     if(g[bx][by]=='#'||g[sx][sy]=='#')return false;
     if(sx==bx&&sy==by)return true;
     int dx[4]={0,-1,0,1},dy[4]={-1,0,1,0};
     for(int i = 0;i<4;i++){
         int a = sx+dx[i],b=sy+dy[i];
         if(a<0||a>=n||b<0||b>=n)continue;
         if(st[a][b])continue;
        
         if(dfs(a,b))return true;//注意这里不要直接return dfs(a,b)，要不然找到一个false的出口 也会直接弹出函数
     }return false;
 }
```

计算 路径长度

```c++
int dfs(int sx,int sy){
    int dis=1;
    st[sx][sy]=true;
    int dx[4]={0,-1,0,1},dy[4]={-1,0,1,0};
    for(int i=0;i<4;i++){
        int a = sx+dx[i],b=sy+dy[i];
        if(a<0||b<0||a>=r||b>=c)continue;
        if(st[a][b])continue;
        if(g[a][b]!='.')continue;
        dis+=dfs(a,b);
    }return dis;
}
```

## 外部搜索

是整体与整体间搜索问题



 有回溯时  记得恢复现场 （e.g:计算有多少中走法 （路径树）最优化路径问题）

于此同时 ，**在dfs开头的标记操作 需要在 判别找到终点操作之后**   防止 无法回复现场

```c++
void dfs{
	if(到达结束点)return;
	st[sx][sy]=true;//标记
	......
	st[sx][sy]=false;//去标记
}
```

```c++
  for (int i = 0; i < k; i ++ )
        if (sum[i] + w[u] <= m) // 可行性剪枝
        {
            sum[i] += w[u];
            dfs(u + 1, k);
            sum[i] -= w[u]; // 恢复现场
        }

    // 新开一辆车
    sum[k] = w[u];
    dfs(u + 1, k + 1);
    sum[k] = 0; // 恢复现场
```



## DFS剪枝

* ### 1.优化搜索顺序  

​	优先搜索分支较少的节点



* ### 2.排除等效冗余

​	12 = 21 可以排除21在已经搜索过12情况下

* ### 3.记忆化搜索（DP）

  

* ### 4.可行性   若已经不可行 则return                         //The most frequent algorithm  modifaction

  * 运算次数优化剪枝

    用lowb 算法可以优化至o（1）复杂度  核心思想时位运算与二进制

    

* ### 5.最优解剪枝  若已知道不可能最优  则退出

在每一次遍历dfs（）时，若此时已经超过最低cost，则直接推出遍历，进行下一次



其中 1.4 5 为最为常用之剪枝策略。

### Q1.小猫上山

顺序问题comes to the first;  选择分支较少的



剪枝优化中： 一般在dfs（）中进行

​	最优性剪枝 first

​	可行性剪枝

```c++
 for (int i = 0; i < k; i ++ )
        if (sum[i] + w[u] <= m) // 可行性剪枝
        {
            sum[i] += w[u];
            dfs(u + 1, k);
            sum[i] -= w[u]; // 恢复现场
        }

    // 新开一辆车
    sum[k] = w[u];
    dfs(u + 1, k + 1);
    sum[k] = 0; // 恢复现场
```



### Q2.数独

顺序：

​	选择可进行方案最少==可进行分支最少

​	（e.g:8,9优先于1，3，5）

剪枝：

​	最优化   无

​	可行性：不与九宫格中数字重复

位运算优化：

​	9宫格对应9位二进制数字（0-511）

​	以及行  列  均是

​	九宫 行 列 取&后 数字

​		核心  lowbit() 运算  O（1）只需要循环1次（取与运算） 不用n次

# 哈希表 

H（key）=Key%size.  = hash value

size =3  capacity =4

一般取质数为size



if any collision:

+ **散列及整数散列**

  将输入的数字作为最大数组的元素下标来对这个数的性质进行统计（出现个数，是否出现），空间换时间（在输入x为int型且数字最大值可控情况下，10w以内）

  -----------上述为引言

​		直接定址法：（上述就是）

​		H（key）=key；

​		除留余数法：

​		H（key）=key%mod；//把很大的数字转换为不超过mod的整数，作为下标

​		Tsize必须不小于mod，最好相等

​		mod最好是一个素数

​		key1与key2的H（key）相同冲突时：

+ **线性探查法**（Liner Porobing)

  key1已经把H(key)占了，检查下一个位置H(key)，知道找到空的位置

  如果超过表长就回到表头

+ **平方探查法**（Quadratic Probing）

情况如上时，检查H(key)±1^2  H(key)±2^2   ......

如果H(key)+k^2超过表长，就对Tsize取模，

如果H(key)-k^2<0（负数取模 -17mod 10=-7)

(H(key)-k^2)%Tsize)%Tsize  till找到大于0小于Tsize位置

+ **链地址法（拉链法）**

  不同，不计算新的hash值

  把所有H（key）相同的key1，key2连接为一条单链表

  建立链表数组Link[mod]

  link[h]存放H(key)=h的单链表

  rehashing：

  容量超过70%时，将原来的size变成两倍，并取最近的一个大于他的质数。

  重新hash一边

+ **字符串hash初步**

  key不是整数时，如(X,Y)二维形式时，可以做映射H(P)=x*Range+y;（0<X,Y<Range;）

  故而不会冲突，有唯一的点

  Tsize=大于Range^2d的最小质数（最好）
  
  

-------------------------------------------------

​	（目前只讨论唯一映射，更深入的后续补充）

​	A-Z为26个字母  字符长度为len

​	则Tsize=26^len  最大下标为26^len -1(对应ZZZZ)(len=4时)（保存了所有字符串）

​	----equal to 26 进制用10进制表示----

```c
int hashFunc(char S[],int len){//字符串S[]
    int id=0;
    for(int i=0;i<len;i++){
        id=id*26+(s[i]-'A');//s[i]字母与'A'距离
    }return id;
}
```

​	出现小写字母，增大到52进制

​	出现数字，增大到62进制

# 4.贪心

局部偏优解（最优解） contributes to 全局最优解

先猜做法 后证明 

## 4.1区间分组问题

* ### 找到最多的互补交集的区间数目

  证明  ans>=cnt && abs<=cnt  --> ans ==cnt;

  ①证明>= ：因为找到的答案为最大值

  ②证明<= ：因为如果存在> 情况，则说明cnt不是最完备的cnt

  步骤：

  1.将诶个区间按右端点从小到大排序

  2.寻找不接壤的区

  ```c++
  struct Range{
      int l,r;
      bool operator < (const Range &w)const
      {
          return r<w.r;
      }
  }range[n];
  int end=-2e7;
  int nct=0;
  for(int i=0;i<n;i++){
      if(end<range[i].r){
          cnt++;
          end=range[i].r;
      }
  }
  return cnt;
  ```

* ### 区间分组

  找到组内彼此没有交集  要求找到最小数目

  1.先排序  按照左端点从小到达排序

  2..判断是否能放到现有组中

  ​	l[i]>Max_r (组的最大右端点)    

  ​						存在可放入组   将其放进去 并跟新 Max_R of this group

  ​						不存在    新开  后更新Max_R; 

  ```c++
  struct Range{
  int l,r;
      bool operator <(const Range &w)const//const at last  means  no changes on the privious haing item.
      {
          return l<w.l;
      }
  }
  //利用来进行最大R的存储和处理
  priority_queue<int,vector<int>,lesser<int>> heap;
  
  
  ```

* 区间覆盖

  找到能覆盖区间的多组数据  找到最小区间数

  1.按照左端点排序

  2.依次枚举区间  在所有能交集start的区间中选择 Right最大的区间   

  ​				将start 更新为此时的Max_Right

  ```c++
  sort(range,range+n);
  int res=0;
  for(int i=0;i<n;i++){
      int j=i;r=-2e9;
      while(j<n&&range[j].l<=st){
          r=max(r,range[j].r);
      }
      if(r<st)return -1;
      res++;
      if(r>=ed)break;
      i=j-1;//为了下次执行++时变成j;细节处理
      st=r;//更新最右端点
  }
  return res;
  ```

## 4.2H树

* 合并果子

  

### 二分查找

主要为了区分和处理二分最容易模糊的边界问题 特此写一分段的小结

* 前提

  ①有序 ②数组

* 有能区分前后2段的明显条件    如果不能则提前处理创造条件。（e.g 剑指offer:找出转折元素）

### 快速幂

求 a^b

b=13=2^3+2^2+1（二进制1101）

a^b=a^13=a^8 * a^4 * a^1

枚举 b的二进制每一位，如果i位上数字为1，则总数可以乘对应a^(2i)

```c
int quickexpo(int b,int e){
	int result=1,flag=0,n=b;
    while(e){
        if(e%2==0)n*=n;
        result*=n;
        e/=2;
    }return result;
}
```

### 斐波那契数列

```c++

int fib(int n){
	if(n<=1)return n;
    else{
        int a=0,b=1,c;
        while(n>1){
            c=a+b;//注意 若有最大数限制，则记得用mod约除
            a=b;
            b=c;
            n--;
        }
    }
    return c;
}
//iteractive version
int fiv(int n){
    if(n<1)return n;
    else return fib(n-1)+fib(n-2);
}
//recursive version
```



### 公约数

```c++
int gcb(int a,int b){
	if(a%b==0)return b;
    else return gcb(b,a%b);
}
```

### lowbit运算

用O（1）复杂度返回运算次序

```c++
    return x&(-x);
```

用位运算来判断0-n是否available

```c++
  for (int i = state; i; i -= lowbit(i)) {//每次从最低位开始check
        int t = map[lowbit(i)];			//map是转换n与2^n的一个map
        draw(x, y, t, true);            //填数字
```

```c++
int map[1<<9];
for(int i=0;i<9;i++)map[1<<i]=i;//map定义
```



# 5.排序

对于一个排列好的a[n]

找出对应k组含2个数字，相加和为M，用2pointers->i and j;

分析原理：

i从left ，j从right开始

a[j]+a[i]>M,则对于a[j+n]也会不满足条件-> j--

a[j]+a[i]<M，则对于a[i-n]也不会满足条件->i++

满足后： 那么i对应j就只有这唯一的j，故而  -> j--;i++;

```c

void twopoints(int a[],const int len,int M){
    int i=0,j=len-1,k=0;
    while(i<j){
        if(a[i]+a[j]>M)j--;
        else if(a[i]+a[j]<M)i++;
        else {
           printf("%d %d|",a[i],a[j]);
           j--;
           i++;
        }
    }
    
}
```

<img src="C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20211214220303116.png" alt="image-20211214220303116" style="zoom: 67%;" />

### MERGE 归并

分为两步，一部是赋值，另一部是分开2部分，这2部分排序好后，再将他们赋值合并。

1.递归实现

防止求mid overflows  ->  mid = left+(right-left)/2;//保守写法

```c
void merge_recur(int a[],int l1,int r1,int l2,int r2){
    int temp[maxn],i=l1,j=l2,index=0;//index 为新建临时数组的下标
    while(i<=r1&&j<=r2){
        if(a[i]>a[j])temp[index++]=a[j++];
        else temp[index++]=a[i++];
    }
    while(i<=r1)temp[index++]=a[i++];
    while(j<=r2)temp[index++]=a[j++];//解决剩余没存完的

    for(int i=l1;i<=r2;i++){
        a[i]=temp[i-l1];//排好序的temp赋值到a  
    }

}//deployee the value in the array;

void mergesort_recur(int a[],int left,int right){
    if(right<=left)return;
    else {
        int mid=left+(right-left)/2;
        mergesort_recur(a,left,mid);
        mergesort_recur(a,mid+1,right);//分为左右2组分而治之排序
        merge_recur(a,left,mid,mid+1,right);
    }
    
}
```

### 快速排序

left right 2个pointers

temp=a[i];

right 右边都是≥temp，left左边都是<temp；

因为i是从0递增的，有temp保存a[i]，所以相当于a[i]的位置空了出来，可以随意处理，此时初始化left， right；

left=i；right=n；

因left位置为空，先处理right，慢慢左移，找出比temp小的元素a[k]后，把a[k]值赋在left 位置，然后left++



而后同样处理left；

直到left==right;

```c++
void quicksort(vector<int>& nums,int left,int right){
    if(left>=right)return ;
    int i=left-1,j=right+1,int mid = nums[i+j>>1];
    while(i<j){
        do i++;while(mid>=nums[i]);
        do j--;while(mid<=nums[j]);
        if(i<j)swap(nums[i],nums[j]);
    }
    quicksort(nums,left,j);
    quicksor(nums,j+1,right);
   
}
```



### 堆排序

①每个数组通过层序排列 转化为一个堆（heap）：

性质：1.parent大于children 2.从左往右排，不落空

即：从最底下的层开始，即（size-1)该级别的siblings中最大的一个跟parent swap，后i--转换到往左or往上一个层级继续交换size/2-1次



②执行堆排序

将root与最后一个数字对调，->将原root值去除到heap之外

后因此时coot非最大值，故而需要movedown，重新建立堆

repeat；s

# 递归

![image-20211210111037404](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20211210111037404.png)

# 基本数学方法

+ # 质数

  ```c++
  int gcd (int a,int b){
      return b?gcd(b,a%b):a;
  }//欧几里得算法 找到最大公约数
  ```

  适用条件是a，b均为正整数即可，若a<b 则再第一层递归即将a b 交换过来了 (因 a%b=a)

  

# 其他高效技巧与算法

## 打表

①	**在程序中一次性计算处所有需要的结果**

以空间换时间，如求Fibonacci第n项，如果查q次就得O（qN），我们可以第一次查的时候先把N项打完，而后每次即提取就行了，即O（q+N）；

②	**在程序B中分一次或多次计算处所有结果，手工把结果写在程序A的数组中，在A中可直接使用这些结果。**

如果在网上答题时，如皇后问题，算法不够好，超时，可以现在本地程序中计算处所有N皇后的方案数，然后把结果直接写在数组当中，就可以根据题目输入的n来输出结果

③**对于不会做的题目，先用暴力程序计算小范围的结果，找规律，发现数学归纳**



## 递推（one by one）

# summary on tests

1.For a sequentially stored linear list of length N, the time complexities for query and insertion are O(1) and O(N), respectively.

译文：对于长度为N的顺序存储线性列表，查询和插入的时间复杂度分别为O(1)和O(N)。

T

顺序存储的线性表支持随机存取，所以查询的时间是常数时间，但插入需要把后面每一个元素的位置都进行调整，所以是线性时间。
可是课本P27-28说：顺序表按值查找算法的平均时间复杂度为O(n)，顺序表插入算法的平均时间复杂度为O(n)

*****************************************************************************************************************************************************************

2.If the most commonly used operations are to visit a random position and to insert and delete the last element in a linear list, then sequential storage works the fastest. (2分)   T

译文：如果最常用的操作是访问一个随机位置以及插入和删除线性列表中的最后一个元素，那么顺序存储的速度最快。

T 

频繁地对最后一个元素查删，顺序表完全可以胜任。

*******************

3.Given a binary search tree with 20 integer keys which include 10, 11, and 12, if 10 and 12 are on the same level, then 11 must be their common ancestor. (2分)

T 

but once if change "ancestor" into "parent"  ,it'll be wrong;

<img src="C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20211214220303116.png" alt="image-20211214220303116" style="zoom: 67%;" />![image-20211115184831202](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20211115184831202.png)

---------------------------

![image-20220104225842780](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220104225842780.png)

边数+1等于节点数 Nn   Nn-N(with children)=N(leaf)

