+++
title = '数据结构与算法'
date = 2024-08-18T21:11:11+08:00
draft = false

+++

# 绪论

## **数据结构在学什么？**      

如何使用数据来表示生活中的问题.

## 数据结构的基本概念

![](数据元素和数据项.png)

**数据**：数据是{%label 信息的载体 green%}，是描述客观事物属性的数，字符及所有能输入到计算机中{%label 并被计算机程序识别和处理 green%}的符号的集合。数据是计算机程序加工的原料。

**数据元素**：是数据的{%label 基本单位 green%}，通常作为一个整体进行考虑和处理。一个数据元素可由若干{%label 数据项 green%}组成，数据项是构成数据元素的不可分割的最小单位。

![](数据对象.png)

**数据对象**:具有{%label 相同性质 green%}的数据元素的集合，是数据的一个子集。

**数据结构**:相互之间存在一种或多种{%label 特定关系 green%}的数据元素的集合。

**数据类型**：一个值的集合和定义在此集合上的一组操作的总称。

- 原子类型：其值不可再分的数据类型，如bool类型，int类型
- 结构类型：其值可以再分解为若干成分(分量)的数据类型

```cpp
struct Coordinate {
    int x;
    int y;
}
```

**抽象数据类型**(Abstract Data Type,ADT): 是抽象数据组织及与之相关的操作.

## 数据结构的三要素

### 逻辑结构

**集合**：各个元素同属于一个集合，并无其他关系

**线性结构**：数据元素之间是{%label 一对一的关系 green%}的关系。除了第一个元素，都有一个唯一的前驱。除了最后一个元素，所有的元素都有唯一后继。

**树形结构**：数据元素之间的{%label 一对多 green%}的关系。

**图结构**:数据元素之间是{%label 多对多的关系 green%}

### 数据的运算

结合逻辑结构，实际需求来定义基本运算。

### 物理结构(存储结构)

如何用计算机实现这种数据结构

- 顺序存储：把{%label 逻辑上相邻的元素存储在物理位置上也相邻的存储单元中 green%}，元素之间的关系由存储单元的邻接关系来体现。
- 链式存储：{%label 逻辑上相邻的元素在物理位置上可以不相邻 green%}，借助指数元素存储地址的指针来表示元素之间的逻辑关系。
- 索引存储：在存储元素信息的同时，还建立附加的索引表。索引表中的每项称为{%label 索引项 green%}，索引项的一般形式是{%label (关键字，地址) green%}
- 散列存储(Hash存储): 根据元素的关键字直接计算出该元素的存储地址。

>运算的定义是针对逻辑结构的，指出运算的功能。
>
>运算的实现是针对存储结构的，指出运算的具体操作步骤。



## 算法的基本概念

**算法**(Algorithm):对{%label 特定问题求解步骤的一种描述 green%},它是指令的有限序列,其中每条指令表示一个或多个操作.

**算法的特性**:

- 有穷性:一个算法必须总在执行有穷步之后结束,且每一步都可在又穷时间内完成.
- 确定性:算法中每条指令必须有确切的含义,对于{%label 相同的输入 green%}只能得到{%label 相同的输出 green%}.
- 可行性:算法中描述的操作都可以通过已经实现的{%label 基本运算执行有限次 green%}来实现.
- 输入:一个算法有{%label 零个或多个输入 green%},这些输入取自于某个特定的对象的集合.
- 输出:一个算法有{%label 一个或多个输出 green%},这些输出是与输入有着某种特定关系的量.

**"好"算法特质**

- 正确性:正确地解决问题
- 可读性:算法应该具有良好的可读性,以帮助人们理解.
- 健壮性:输入非法数据时,算法能够适当地做出反映或进行处理,而不会产生莫名奇妙的输出结果
- 高效率和低存储量需求:时间复杂度和空间复杂度低

## 算法的时间复杂度

>**同阶无穷大**
>
>$O(1)<O(log n)<O(n)<O(nlog n)<O(n^2)<O(n^3)<O(2^n)<O(n!)<O(n^n)$

>**小结论**
>
>1. 顺序执行的代码只会影响常数项,可以忽略.
>2. 只需挑循环中的**一个基本操作**分析它的执行次数与n的关系即可
>3. 如果有多层嵌套循环,只需关注最深层循环循环了几次

**最好/最坏/平均时间复杂度**

## 算法的空间复杂度

**算法原地工作**:无论问题规模怎么变,算法所需的内存空间都是固定的常量,算法的空间复杂度为$O(1)$

**递归算法**:通常为递归调用的深度

# 线性表

## 线性表的定义和基本操作

**线性表**:具有{%label 相同数据类型 green%}的n(n>=0)个{%label 数据元素 green%}的{%label 有限序列 green%},其中n为{%label 表长 green%},当n=0时线性表是一个{%label 空表 green%}.若用L命名线性表,则其一般表示为

$$L = (a_1,a_2,a_i,a_{i+1},...a_n)$$

>$a_i$是线性表中的"第i个"元素,线性表中的位序
>
>$a_1$是表头元素,$a_n$是表尾元素
>
>除第一个元素外,每个元素有且仅有一个直接前驱,除最后一个元素外,每个元素有且仅有一个直接后继.

**基本操作**

- InitList(&L):初始化表.构造一个空的线性表L,分配内存空间
- DestroyList(%L):销毁操作.销毁线性表,并释放线性表L所占用的内存空间
- ListInsert(&L,i,e):插入操作.在线性表的第i个位置插入指定元素e
- ListDelete(&L,i,&e):删除操作.删除表L中第i个位置的元素,并用e返回删除元素的值.
- LocateElement(L,e):按值查找操作.在表L中查找具有给定关键字值的元素.
- GetElem(L,i):按位查找操作,获取表L中第i个位置的元素的值.
- Lengeh(L):求表长.返回线性表L的长度,即L中数据元素的个数.
- PrintList(L):输出操作.按前后顺序输出线性表L的所有元素值.
- Empty(L):判空操作.若L为空表,则返回true,否则返回false

## 顺序表的定义

**顺序表**:用{%label 顺序存储 green%}的方式实现线性表.

**实现方式**

- 静态分配

```cpp
    #include <stdio.h>
    #define MaxSize 10 // 定义最大长度
    typedef struct
    {
      int data[MaxSize];
      int length;
    } SqList;
    
    // 基本操作：初始化一个顺序表
    void InitList(SqList &L)
    {
      for (int i = 0; i < MaxSize; i++)
      {
        L.data[i] = 0; // 将所有数据元素设置为默认初始值
      }
      L.length = 0; // 顺序表的初始长度为0
    }
    
    int main()
    {
      SqList L;    // 声明一个顺序表
      InitList(L); // 初始化
      // TODO
      return 0;
    }									//顺序表的类型定义(静态分配方式)
```

- 动态分配

```cpp
#include <stdio.h>
#include <stdlib.h>

#define InitSize 10           // 默认的最大长度
typedef struct SeqList
{
  int *data;                  // 指示动态分配数组的指针
  int MaxSize;                // 顺序表的最大容量
  int length;                 // 顺序表的当前长度
};

void InitList(SeqList &L)
{
  L.data = (int *)malloc(InitSize * sizeof(int));     // 分配内存
  L.MaxSize = InitSize;                               // 初始化最大容量
  L.length = 0;                                       // 初始化当前长度
}

// 增加动态数组的长度
void IncreaseSize(SeqList &L, int len)
{
  int *p = L.data;                                    // 保存原数组指针
  L.data = (int *)malloc((L.MaxSize + len) * sizeof(int)); // 分配新的内存
  for (int i = 0; i < L.length; i++)
    L.data[i] = p[i];                                 // 将原数组元素拷贝到新数组
  L.MaxSize = L.MaxSize + len;
  free(p);                                            // 释放原数组的内存
}
```

**顺序表的特点**

- 随机访问:即可以在O(1)时间内找到第i个元素
- 存储密度高,每个节点只存储数据元素
- 拓展容量不方便(即便采用动态分配的方式实现,拓展长度的时间复杂度也比较高)
- 插入,删除操作不方便,需要移动大量元素.

## 顺序表的插入删除

**插入**

```cpp
// 基本操作：在L的位序i处插入元素e
void ListInsert(SqList &L, int i, int e)
{
  for(int j = L.length; j >= i; j--){   // 将第i个元素及之后的元素后移
    L.data[j] = L.data[j - 1];
  }
  L.data[i - 1] = e;                    // 在位序i处放入e
  L.length++;                           // 顺序表长度加1
}

// 增加健壮性后
bool ListInsert(SqList &L, int i, int e)
{
  if (i < 1 || i > L.length + 1)
    return false;
  if (L.length >= MaxSize)
    return false;
  for (int j = L.length; j >= i; j--)
  {
    L.data[j] = L.data[j - 1];
  }
  L.data[i - 1] = e;
  L.length++;
}
```

>时间复杂度分析:
>
>- 最好情况:新元素插入到表尾,不需要移动元素.i=n+1,循环0次,时间复杂度为O(1)
>- 最坏情况:新元素插入到表头,所有元素都需要移动,i=1,循环n次,时间复杂度为O(n);
>- 平均情况:假设新元素插入到任何一个位置的概率相同,即i=1,2,3,length+1的概率都是$p=\frac{1}{n+1}$,时间复杂度为O(n)

**删除**

```cpp
bool ListDelete(SqList &L,int i,int &e){
    if(i<1||i>L.length)			// 判断i的范围是否有效
        return false;
    e=L.data[i-1]				// 将被删除的元素赋值给e
    for(int j=i;j<L.length;j++){
        L.data[j-1]=L.data[j];
    }
    L.length--;
    return true;
}
int main(){
    SqList L;		//声明一个顺序表
    InitList(L);    // 初始化顺序表
    // 此处省略一些代码,插入几个元素
    int e = -1;		// 用变量e把删除的元素带回来
    if(ListDelete(L,3,e))
        printf("已删除第3个元素,删除元素值为=%d\n",e);
    else
        printf("位序i不合法,删除失败\n");
    return 0;
}
```

>时间复杂度分析:
>
>- 最好情况:删除表尾的元素,不需要移动元素.i=n+1,循环0次,时间复杂度为O(1)
>- 最坏情况:删除表头的元素,所有元素都需要移动,i=1,循环n次,时间复杂度为O(n);
>- 平均情况:删除任何一个位置的概率相同,即i=1,2,3,length+1的概率都是$p=\frac{1}{n+1}$,时间复杂度为O(n)

## 顺序表的查找

**按位查找**

`GetElem(L,i)`:按位查找操作.获取表L中第i个位置的元素的值.

```cpp
// 静态方式
#define MaxSize 10  // 定义最大长度
typedef struct SqList{
    ElemType data[MaxSize];
        int length;
};
ElemType GetElem(SqList L, int i){
    return L.data[i-1]
}
// 动态方式
#define InitSize 10
typedef struct SeqList{
    ElemType *data;
    int MaxSize;
    int length;
};
ElemType GetElem(SeqList L, int i){
    return L.data[i-1]			// 和访问普通数组的方法一样
}
```

>**时间复杂度**:O(1)

**按值查找**

`LocateElem(L,e)`:按值查找操作.在表L中查找具有给定关键字值的元素.

```cpp
#define InitSize 10   // 顺序表的初始长度
typedef struct{
    ElemType *data;	  // 指示动态分配数组的指针
    int MaxSize;	  // 顺序表的最大容量
    int length;		  // 顺序表的当前长度
}SeqList;

// 在顺序表L中查找第一个元素值等于e的元素,并返回其位序
int LocateElem(SeqList L, ElemType e){
    for(int i=0;i<L.length;i++){
        if(L.data[i]==e)
            return i+1;
    }
    return 0;
}
// 注意:结构类型的比较不能用==比较
// 需要依次对比各个分量来判断两个结构体是否相等
```

>时间复杂度分析:
>
>最好情况:O(1)
>
>最坏情况:O(n)
>
>平均情况:O(n)



## 单链表的定义

**单链表**:每个结点除了存放数据元素外,还要存储指向下一个节点的指针.

- 优点：不要求大片连续空间，改容量方便。
- 缺点：不可随机存储，要耗费一定空间存放指针。

```cpp
#include <stdio.h>
#include <stdlib.h>
struct LNode
{                     // 定义单链表结点类型
  ElemType data;      // 每个结点存放一个数据元素
  struct LNode *next; // 指针指向下一个结点
};
// 增加一个新结点
struct LNode *p = (struct LNode *)malloc(sizeof(struct LNode));
```

---

**使用typedef关键字来简化代码**

```cpp
#include <stdio.h>
#include <stdlib.h>

struct LNode{
  ElemType data;
  struct LNode *next;
}LNode, *LinkList;
```

要表示一个单链表时,只需声明一个{%label 头指针 green%}L,指向单链表的第一个结点

```cpp
LNode *L;			//声明一个指向单链表第一个结点的指针
// 或者也可以使用如下方式
LinkList L;			//声明一个指向单链表第一个结点的指针
```

LNode *L和LinkList L本质是一样的,不过前者更强调单独的一个结点,而后者更强调这是一个单链表整体.

**不带头结点的单链表**

```cpp
typedef struct LNode{			//定义单链表结点类型
    ElemType data;				//每个结点存放一个数据元素
    struct LNode *next;			//指针指向下一个结点
}LNode, *LinkList;				//将struct LNode 取别名为LNode,将struct LNode *取别名为LinkList
// 初始化一个空的单链表
bool InitList(LinkList &L){
    L = NULL;			//空表,暂时还没有任何结点
    return true;
}
// 判断单链表是否为空
bool Empty(LinkList L){
    return (L==NULL);
}

// 测试一下
void test {
    LinkList L;			//声明一个指向单链表的指针
    // 初始化一个空表
    InitList(L);
    // ... 后续代码
}
```

**带头结点的单链表**:推荐!!

```cpp
typedef struct LNode{				//定义单链表结点类型
    ElemType data;					//每个结点存放一个数据元素
    struct LNode *next;				//指针指向下一个结点
}LNode, *LinkList;
// 初始化一个单链表(带头结点)
bool InitList(LinkList &L){
    L = (LNode *)malloc(sizeof(LNode));		//分配一个头结点
    if(L == NULL)						// 内存不足,分配失败
        return false;
    L->next = NULL;						//头结点之后暂时还没有结点
    return true;
}
void test(){
    LinkList L;							//声明一个指向单链表的指针
    // 初始化一个空表
    InitList(L);
    //... 后续代码
}
```

## 单链表的插入删除

**带头结点**

ListInsert(&L,i,e):插入操作，在表L中第i个位置插入指定元素e

需要找到第i-1个结点，将新结点插入其中

```cpp
// 定义一个单链表
typedef struct LNode{
    ElemType data;
    struct LNode *next;
}LNode, *LinkList;
// 在第i个位置插入元素e(带头结点)
bool ListInsert(LinkList &L, int i, ElemType e){
    if(i<1)
        return false;
    LNode *p;			//指针p指向当前扫描到的结点
    int j=0;			//当前p指向的是第几个结点
    p = L;				//L指向头结点，头结点是第0个结点(不存数据)
    while(p!=NULL && j<i-1){
        //循环找到第i-1个结点
        p=p->next;
        j++:
    }
    if(p==NULL)			//i值不合法
        return false;
    LNode *s = (LNode *)malloc(sizeof(LNode));
    s->data=e;
    s->next=p->next;
    p->next=s;		//将结点s连到p之后
    return true;     //插入成功
}
```

>**时间复杂度分析**
>
>最好情况：在表头插入，O(1)
>
>最坏情况/平均情况: O(n)

**不带头结点**

```cpp
// 定义一个单链表
typedef struct LNode{
    ElemType data;
    struct LNode *next;
}LNode, *LinkList;

//按位序插入(不带头结点)
bool ListInsert(LinkList &L,int i, ElemType e){
    if(i<1)
        return false;
    if(i==1){
        // 插入第一个结点的操作与其他结点的不同
        LNode *s = (LNode *)malloc(sizeof(LNode));
        s->data = e;
        s->next = L;
        L = s;     // 头指针指向新结点
        return true;
    }
    LNode *p;		//指针p指向当前扫描到的结点
    int j=1;		//当前p指向的是第几个结点
    p = L;			//p指向第1个结点(注意：不是头结点)
    while(p!=NULL && j<i-1){
        //循环找到第i-1个结点
        p=p->next;
        j++;
    }
    if(p==NULL)			//i值不合法
        return false;
    LNode *s = (LNode *)malloc(sizeof(LNode));
    s->data = e;
    s->next = p->next;
    p->next = s;
    return true;		//插入成功
}

```

**指定结点的后插操作**

```cpp
// 后插操作：在结点p之后出入元素e
// 时间复杂度,O(1)
bool InsertNextNode (LNode *p, ElemType e){
    if(p==NULL)
        return false;
    LNode *s = (LNode *)malloc(sizeof(LNode));
    if(s==NULL)		//内存分配失败
        return false;
    s->data = e;		//用结点s存放数据元素e
    s->next = p->next;
    p->next = s;		//将结点s连到p之后
    return true;
}
```

**指定结点的前插操作**

```cpp
// 前插操作：在p结点之前插入元素e
// 传入头指针，遍历整个链表，找到p结点的前驱节点，在其之后插入e
// 时间复杂度O(n)
//bool InsertPriorNode(LinkList L, LNode *p, ElemType e)
    
// 第二种方式，先在p结点之后插入新结点，再将p的元素赋值给新结点，将e赋值给p结点
bool InsertPriorNode(LNode *p,ElemType e){
    if(p==NULL)
        return false;
    LNode *s = (LNode *)malloc(sizeof(LNode));
    if(s==NULL)			//内存分配失败
        return false;
    s->next = p->next;
    p->next = s;		//新结点s连到p之后
    s->data=p->data;	//将p中元素复制到s中
    p->data=e;			//将p中元素覆盖为e
    return true;		//前插成功
}
```

**按位序删除**(带头结点)

```cpp
bool ListDelete(LinkList &L,int i,ElemType &e){
    if(i<1)
        return false;
    LNode *p;		//指针p指向当前扫描到的结点
    int j=0;		//当前p指向的是第几个结点
    p = L;			//L指向头结点,头结点是第0个结点(不存数据)
    while(p!=NULL & j<i-1){
        p=p->next;
        j++;
    }
    if(p==NULL)		//i值不合法
        return false;
    if(p->next==NULL)	//第i-1结点之后已无其他结点
        return false;
    LNode *q = p->next;	//令q指向被删除的结点
    e = q->data;		//用e返回元素的值
    p->next=q->next;	//将*q结点从链中断开
    free(q);			//释放结点的存储空间
    return true;		//删除成功
}
```

>最好情况:O(1)
>
>最坏情况/平均情况:O(n)

**指定结点的删除**

```cpp
// 删除指定的结点p
bool DeleteNode(LNode *p){
    if(p==NULL)
        return false;
    LNode *q = p->next;		//令q指向*p的后继节点
    p->data=p->next->data;	//和后继节点交换数据域
    p->next=q->next;		//将*q结点从链中断开
    free(q);				//释放后继结点的存储空间
    return true;
}
// 如果*p是最后一个节点的话,不能ci'a'y
```

## 单链表的查找

**按位查找**

GetElem(L,i):按位查找，获取表L中第i个位置的元素.

```cpp
//按位查找，返回第i个元素(带头结点)
LNode *GetElem(LinkList L,int i){
    if(i<0)
        return NULL;
    LNode *p;		//指针p指向当前扫描到的结点
    int j=0;		//当前p指向的是第几个结点
    p = L;			//L指向头结点，头结点是第0个结点，不存数据
    while(p!==NULL && j<i){
        p=p->next;
        j++;
    }
    return p;
}
```

>最好情况:O(1)
>
>最差情况/平均情况:O(n)

**按值查找**

LocateElem(L,e):按值查找，再表L中查找具有给定关键字值的元素

```cpp
//按值查找，找到数据域==e的结点
LNode *LocateElem(LinkList L,ElemType e){
    LNode *p = L->next;
    //从第1个结点开始查找数据域为e的结点
    while(p!==NULL && p->data != e)
        p = p->next;
    return p;		//找到后返回该结点指针，否则返回NULL
}
```

>最好情况:O(1)
>
>最差情况/平均情况:O(n)

**求表的长度**

```cpp
//求表的长度
int Length(LinkList L){
    int len = 0;		//统计表长
    LNode *p = L;
    while(p->next != NULL){
        p = p->next;
        len++;
    }
    return len;
}
```

>时间复杂度:O(n)

## 单链表的建立

**尾插法**

```cpp
#include <stdio.h>
#include <stdlib.h>
typedef struct LNode{
    int data;
    struct LNode *next;
}LNode,*LinkList;
LinkList LinkList_TailInsert(LinkList &L){
    int x;					//设置ElemType为整形
    L = (LinkList)malloc(sizeof(LNode)); //建立头结点
    LNode *s,*r = L;		//r为表尾指针
    scanf("%d",&x);			//输入结点的值
    while(x!=9999){
        //输入9999表示结束
        s = (LNode *)malloc(sizeof(LNode));
        s->data=x;
        r->next=s;
        r=s;			//r指向新的表尾结点
        scanf("%d",&x);
    }
    r->next=NULL;
    return L;
}
```

**头插法**

```cpp
LinkList_HeadInsert(LinkList &L){
    LNode *s;
    int x;
    L=(LinkList)malloc(sizeof(LNode));		//创建头结点
    L->next = NULL;						//初始为空链表
    scanf("%d",&x);						//输入结点的值
    while(x!=9999){
        //输入9999表示结束
        s = (LNode *)malloc(sizeof(LNode));	//创建新结点
        s->data=x;
        s->next=L->next;
        L-next=s;	//将新结点插入表中，L为头指针
        scanf("%d",&x);
    }
    return L;
}
```

## 双链表

```cpp
typedef struct DNode{
    ElemType data;
    struct DNode *prior,*next;	//前驱和后继指针
}DNode, *DLinkList;

```

```cpp
//初始化双链表(带头结点)
bool InitDLinkList(DLinkList &L){
    L = (DNode *)malloc(sizeof(DNode));	//分配一个头结点
    if(L==NULL)		//内存不足,分配失败
        return false;
    L->prior = NULL;		//头结点的prior永远指向NULL
    L->next = NULL;			//头结点之后暂时还没有结点
    return true;
}
```

```cpp
//在p结点之后插入s结点
bool InsertNextDNode(DNeode *p, DNode *s){
    if(p==NULL||s==NULL)		//非法参数
        return false;
    s->next=p->next;
    if(p->next!=NULL)		//如果p结点还有后继节点
        p->next-prior=s;
    s->prior=p;
    p->next=s;
    return true;
}
```

```cpp
//删除p的后继节点q
bool DeleteNextDNode(DNode *p){
    if(p==NULL) return false;
    DNode *q = p->next;	//找到p的后继结点q
    if(q==NULL) return false;	//p没有后继
    p->next=q->next;
    if(p->next!=NULL)`		//q有后继结点
        q->next->prior=p;
    free(q);		//释放结点空间
    return true;
}
```

```cpp
//双链表的遍历
//后向遍历
while(p!=NULL){
    p=p->next;
}
//前向遍历
while(p!=NULL){
    p=p->prior;
}
//前向遍历(跳过头结点)
while(p->prior!=NULL){
    p=p->prior;
}
// 时间复杂度:O(n)
```

## 循环链表

**循环单链表**

```cpp
typedef struct LNode{
    ElemType data;
    struct LNode *next;
}LNode, *LinkList;
//初始化一个循环单链表
bool InitList(LinkList &L){
    L = (LNode *)malloc(sizeof(LNode));//分配一个头结点
    if(L==NULL)
        return false;
    L->next=L;		//头结点的next指向头结点
    return true;
}
//判断循环单链表是否为空
bool Empty(LinkList L){
    if(L->next=L)
        return true;
    else
        return false;
}
//判断p结点是否为循环单链表的表尾结点
bool isTail(LinkList L,LNode *p){
    if(p->next==L)
        return true;
    else
        return false;
}
```

**循环双链表**

```cpp
//初始化空的循环双链表
bool InitDLinkList(DLinkList &L){
    L = (DNode *)malloc(siezeof(DNode));//分配一个头结点
    if(L==NULL)
        return false;
    L->prior=L;
    L->next=L;
    return true;
}
//判断循环双链表是否为空
bool Empty(DLinkList L){
    if(L->next==L)
        return true;
    else
        return false;
}
// 判断p结点是否是循环双链表的表尾结点
bool isTail(DLinkList L,DNode *p){
    if(p->next=L)
        return true;
    else
        return false;
}
```

## 静态链表

**单链表**：各个节点在内存中星罗棋布，散落天涯

**静态链表**：分配一整片连续的内存空间，各个结点集中安置

```cpp
#define MaxSize 10  // 静态链表的最大长度
struct Node{
    ElemType data;
    int next;		//下一个元素的数组下标
};
typedef struct {
    int data;
    int next;
}SLinkList[MaxSize];

void testSLinkList(){
    struct Node x;
    printf("sizeX=%d\n",sizeof(x));
 	
    struct Node a[MaxiSize];
    printf("sizeA=%d\n",sizeof(a));
    
    SLinkList b;
    printf("sizeB=%d\n",sizeof(b));
}
//输出结果
// sizeX=8
// sizeA=80
// sizeB=80
```

>查找:O(n)

## 顺序表VS链表

|            | 顺序表                                                       | 链表                                                         |
| ---------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| 逻辑结构   | 线性结构                                                     | 线性结构                                                     |
| 物理结构   | 顺序存储,支持随机存取,存储密度高;大片连续空间分配不方便,改变容量不方便 | 链式存储,离散的空间分配方便,改变容量方便;不可随机存储,存储密度低 |
| 数据的运算 | 静态自动回收,动态手动free                                    | 遍历free                                                     |
| 适用情况   | 表长可以估计,经常进行查询                                    | 表长难以估计,需要经常增删改查                                |

# 栈和队列

## 栈的基本概念

**栈**(Stack)是只允许在一端进行插入或删除操作的线性表

**栈顶**:允许进行插入和删除的一端

**栈底**:不允许进行插入和删除的一端

**空栈**:没有元素的栈

特点:后进先出(Last in First Out,LIFO)

**常考题型**:n个不同元素进栈,出栈元素不同的排列的个数为$\frac{1}{n+1}C_{2n}^n$,上述公式称为卡特兰数,可采用数学归纳法证明.

## 栈的顺序存储实现

```cpp
#define MaxSize 10
typedef struct{
    ElemType data[MaxSize];
    int top;			//栈顶指针
}SqStack;

//初始化栈
void InitStack(SqStack &S){
    S.top=-1;			//初始化栈顶指针
}

//判断栈空
bool StackEmpty(SqStack S){
    return S.top==-1;		
}

//新元素入栈
bool Push(SqStack &S, ElemType x){
    if(S.top===MaxSize-1)
        //栈满,报错
        return false;
    //一下两行可以简写为
    //S.data[++S.top]=x;
    S.top++;
    S.data[S.top]=x;	//新元素入栈
    return true;
}
// 出栈操作
bool Pop(SqStack &S,ElemType &x){
    if(S.top==-1)
        return false;
    x=S.data[S.top--];	//栈顶元素先出栈,再将指针-1
    return true;
}
//读取栈顶元素
bool Pop(SqStack &S,ElemType &x){
    if(S.top==-1)
        return false;
    x=S.data[S.top];
    return true;
}

void testStack(){
    SqStack S;		//声明一个顺序栈(分配空间)
    // 后续操作
}
//栈满条件:S,top = MaxSize
```

**共享栈**:两个栈共享同一片空间

```cpp
#define MaxSize 10
typedef struct{
    ElemType data[MaxSize];
    int top0;
    int top1;
}ShStack;
//初始化栈
void InitStack(ShStack &S){
    S.top0=-1;
    S.top1=MaxSize;
}
//栈满的条件:top0+1=top1
```

## 栈的链式存储

**定义**

```cpp
//链栈的定义
typedef struct Linknode{
    ElemType data;
    struct Linknode *next;
}*LiStack;

```

## 队列的基本概念

**队列**(Queue):先进先出(First in first out,FIFO)

**重要术语**:队头,队尾,空队列

## 队列的顺序实现

```cpp
//循环队列
#define MaxSize 10
typedef struct{
    ElemType data[MaxSize];		//用静态数组存放队列元素
    int front,rear		//队头指针和队尾指针
}SqQueue;

//初始化队列
void InitQueue(SqQueue &Q){
    //初始时,队头,队尾指针指向0
    Q.rear=Q.front=0;
}
//判断队列是否为空
bool QueueEmpty(SqQueue Q){
    if(Q.rear==Q.front)
        return true;
    else
        return false;
}
//入队
bool EnQueue(SqQueue &Q,ElemType x){
    if((Q.rear+1)%MaxSize==Q.front)
        return false;
    Q.data[Q.rear]=x;
    Q.rear=(Q.rear+1)%MaxSize;  //队尾指针加1取模运算
    return true;
}
//出队(删除一个队头元素,并用x返回)
bool DeQueue(SqQueue, &Q,ElemType &x){
    if(Q.rear==Q.front)
        return false; //队空
    x=Q.data[Q.front];
    Q.front=(Q.front+1)%MaxSize;	//指针后移
    retrun true;
}
//获取队头元素的值,用x返回
bool GetHead(SqQueue Q,ElemType &x){
    if(Q.rear==Q.front)
        return false;
    x=Q.data[Q.front];
    return true;
}

void testQueue(){
    SqQueue Q;
}

```

**判断队列已满/已空的方法**

- 方法1
  - 已满:rear+1==front
  - 已空:rear==front
- 方法2:设计size来表示当前队列的长度
  - 已满:size==MaxSize
  - 已空:size==0
- 方法3:用tag来表示队列的上一次操作,每次删除成功,令tag=0;插入成功令tag=1;
  - 已满:rear==front&&tag=1
  - 已空:rear==front&&tag=0

## 队列的链式实现

```cpp
//队列的链式实现
typedef struct LinkNode{   //链式队列结点
    ElemType data;
    struct LinkNode *next;
}LinkNode;
typedef struct{				//链式队列
    LinkNode *front,*rear;	//队列的队头和队尾指针
}LinkQueue;

//初始化队列(带头结点)
void InitQueue(LinkQueue &Q){
    //初始时,front,rear 都指向头结点
    Q.front=Q.rear=(LinkNode *)malloc(sizeof(LinkNode));
    Q.front->next=NULL;
}
//判断队列是否为空
bool IsEmpty(LinkQueue Q){
    if(Q.front==Q.rear)
        return true;
    else
        return false;
}
//新元素入队
void EnQueue(LinkQueue &Q,ElemType x){
	LinkNode *s=(LinkNode *)malloc(sizeof(LinkNode));
    s->data=x;
    s->next=NULL;
    Q.rear->next=s;			//新结点插入到rear之后
    Q.rear=s;				//修改表尾指针
}
void testLinkQueue(){
    LinkQueue Q;		//声明一个队列
    InitQueue(Q);		//初始化队列
}
//队列元素出队
bool DeQueue(LinkQueue &Q,ElemType &x){
    if(Q.front==Q.rear)
        return false;		//空队
    LinkNode *p=Q.front->next;
    x=p->data;			//用变量x返回队头元素
    Q.front->next=p->next;	//修改头结点的next指针
    if(Q.rear==p)			//此次是最后一个结点出队
        Q.rear=Q.front;		//修改rear指针
    free(p);				//释放结点空间
    return true;
}
```

## 双端队列

![](双端队列.png)

## 栈的应用--括号匹配

 ```cpp
 #define MaxSize 10  //定义栈中元素的最大个数
 typedef struct{
     char data[MaxSize];		//静态数组存放栈中元素
     int top;				//栈顶指针
 }SqStack;
 //初始化栈
 void InitStack(SqStack &S);
 //判断栈是否为空
 bool StackEmpty(SqStack S);
 //新元素入栈
 bool Push(SqStack &S,char x);
 //栈顶元素出栈,用x返回
 bool Pop(SqStack &S,char &x);
 
 bool bracketCheck(char str[],int length){
     SqStack S;
     InitStack(S);		//初始化一个栈
     for(int i=0;i<length;i++){
         if(str[i]=='('||str[i]=='['||str[i]=='{'){
             Push(S,str[i]);//扫描到左括号,入栈
         }else{
             if(StackEmpty(S))//扫描到右括号且目前栈空
                 return false; //匹配失败
             cahr topElem;
             Pop(S,topElem);	//栈顶元素出栈
             if(str[i]==')'&&topElem!='(')
                 return false;
             if(str[i]==']'&&topElem!='[')
                 return false;
             if(str[i]=='}'&&topElem!='{')
                 return false;
         }
     }
     return StackEmpty(S); //检索全部括号后,栈空说明匹配成功
 }
 ```

## 栈的应用--表达式求值

**三种算术表达式**

- 前缀表达式(波兰表达式)**

>**右优先原则**
>
>只要右边的运算符能先计算,就优先算右边的
>
>从右往左扫描
>
>扫描到操作数则压入栈,继续扫描
>
>扫描到运算符,则弹出两个栈顶元素,执行相应的运算,运算结果压回栈顶,继续扫描(注意:先出栈的是**左操作数**

- 中缀表达式
- 后缀表达式(逆波兰表达式)

>**左优先原则**
>
>只要左边的运算符能先计算,就优先算左边的
>
>从左往右扫描
>
>扫描到操作数则压入栈,继续扫描
>
>扫描到运算符,则弹出两个栈顶元素,执行相应的运算,运算结果压回栈顶,继续扫描(注意:先出栈的是**右操作数**

**中缀表达式转后缀表达式**

初始化一个栈,用于保存{%label 暂时还蹦年确定运算顺序的运算符 green%}

从左到右处理各个元素,直到末尾.可能遇到三种情况:

1. 遇到{%label 操作数 green%}.直接加入后缀表达式.
2. 遇到{%label 界限符 green%}.遇到"("直接入栈;遇到")"则依次弹出栈内运算符并加入后缀表达式,直到弹出"("位置.注意:"("不加入后缀表达式
3. 遇到{%label 运算符 green%}.依次弹出栈中优先级高于或等于当前运算符的所有运算符,并加入后缀表达式,若碰到"("或栈空则停止.之后再把当前运算符入栈.
4. 按上述方法处理完所有字符后,将栈中剩余运算符依次弹出,并加入后缀表达式.

## 栈的应用--递归

**函数调用背后的过程**

函数调用时,需要用一个栈存储:

1. 调用返回地址
2. 实参
3. 局部变量

适合用"递归"算法解决:可以把原始问题转换为{%label 属性相同 green%},但{%label 规模较小的问题 green%}

## 队列的应用--树的层次遍历

## 队列的应用--图的广度优先遍历

## 队列在操作系统中的应用

FCFS(First Come First Service,先来先服务)



## 特殊矩阵的压缩存储

**一维数组的存储结构**

各个数组元素大小相同，且在物理上连续存放，已知起始地址即可得到其他地址

**二维数组的存储结构**

- 行优先存储
- 列优先存储

**普通矩阵的存储**

使用二维数组

**对称矩阵的压缩存储**

只存储主对角线+下/上三角区域

**三角矩阵的压缩存储**

按照行优先原则将绿色区元素存入一维数组中。并在最后一个位置存储常量c

**三对角矩阵的压缩存储**

按行优先(或列优先)原则，只存储带状部分

**稀疏矩阵的压缩矩阵**

- 顺序存储--三元组<行，列，值>
- 十字链表法



# 串

## 串的定义和基本操作

**串**，即字符串(String)是由零个或多个字符组成的有限序列。

**空串**：长度为0的串

**子串**：串中任意各连续的字符组成的子序列。

**主串**：包含子串的串

**子串在主串中的位置**：子串的第一个字符在主串中的位置

---

**串的基本操作**

- StrAssign(&T,chars):赋值操作。把串T赋值为chars
- StrCopt(&T,S):复制操作。由串S复制得到串T
- StrEmpty(S):判空操作。若S为空串，则返回true,否则，返回false
- StrLength(S):求串长。返回串S的元素个数。
- ClearString(&S):清空操作。将S清为空串
- DestroyString(&S):销毁串，将串S的存储空间回收
- Concat(&T,S1,S2):串连接。用T返回S1和S2连接成的新串
- SubString(&Sub,S,pos,len):求子串，用Sub返回串S的第pos个字符起长度为len的子串
- Index(S,T):定位操作。若主串S中存在与串T值相同的子串，则返回它在主串S中第一次出现的位置，否则返回0
- StrCompare(S,T):若S>T,则返回值>0,若S=T,则返回值=0,若S<T，则返回值<0

**字符集编码**

英文字符-ASCII字符集

中英文--Unicode字符集

基于同一字符集，可以有多种编码方案。如UTF-8,UTF-16

**拓展：乱码问题**

## 串的存储结构

**顺序存储**

```cpp
#define MAXLEN 255
typedef struct{
    char ch[MAXLEN];
    int length;
}SString;

typedef struct{
    char *ch;	//按串长分配存储区,ch指向串的基地址
    int length;	//串的长度
}HString;//动态数组实现(堆分配存储)

HString S;
S.ch = (char *)malloc(MAXLEN *sizeof(char));
S.length = 0;
```

**链式存储**

```cpp
typedef struct StringNode{
    char ch;
    struct StringNode *next;
}StringNode, *String;

typedef struct StringNode{
    char ch[4];	//每个结点存多个字符
    struct StringNode *next;
}StringNode, *String;
```

```cpp
#define MAXLEN 255
typedef struct{
    char ch[MAXLEN];
    int length;
}SString;

//求子串
bool SubString(SString &Sub, SString S,int pos,int len){
    //子串范围越界
    if(pos+len-1>S.length)
        return false;
    for(int i=pos;i<pos+len;i++){
        Sub.ch[i-pos+1] = S.ch[i];
    }
    Sub.length = len;
    return true;
}
```

## 朴素模式匹配算法

被找的是主串，要找的目标是模式串

**字符串模式匹配**：在主串中找到与模式串相同的子串，并返回其所在位置

找到主串所有与模式串长度相等的子串与模式串进行匹配

```cpp
int Index(SString S,SString T){
    int i=1,j=1;
    while(i<=S.length && j<=T.length){
        if(S.ch[i]==T.ch[i]){
            i++;
            j++; //继续比较后续字符
        }else{
            i=i-j+2;
            j=1;	//指针后退重新开始匹配
        }
        if(j>T.length)
            return i-T.length;
        else
            return 0;
    }
}
```

## KMP匹配算法

**改进思路**:主串指针不回溯,只有{%label 模式串指针回溯 green%}

![](KPM算法.png)

```cpp
int Index_KMP(SString S,SString T,int next[]){
    int i=1,j=1;
    while(i<=S.length&&j<T.length){
        if(j==0||S.ch[i]==T.ch[j]){
            i++;
            j++;	//继续比较后继字符
        }else{
            j=next[j];//模式串向右移动
        }
    }
    if(j>T.length)
        return i-T.length;	//匹配成功
    else
        return 0;
}
```

**求next数组**

**串的前缀**:包含第一个字符,且不包含最后一个字符的子串

**串的后缀**:包含最后一个字符,且不包含第一个字符的子串

当第j个字符匹配失败，由前1~j-1个字符组成的串记为S，则{%label next[j]=S的最长相等前后缀长度+1 green%}，可推导出next[2]=1

特别地,next[1]=0

```cpp
//求模式串T的next数组
void get_next(SString T,int next[]){
    int i=1,j=0;
    next[1]=0;
    while(i<T.length){
        if(j==0||T.ch[i]=T.ch[j]){
            i++;
            j++;
            //若pi=pj，则next[j+1]=next[j]+1
            next[i]=j;
        }else{
            //否则令j=next[j],循环继续
            j=next[j];
        }
    }
}

//KMP算法
int Index_KMP(SString S,SString T){
    int i=1,j=1;
    int next[T.length+1];
    get_next(T,next);	//求模式串的next数组
    while(i<=S.length&&j<=T.length){
        if(j==0||S.ch[i]==T.ch[j]){
            i++;
            j++;			//继续比较向后的字符
        }else{
            j=next[j];		//模式串向右移动
        }
    }
    if(j>T.length)
        return i-T.length;	//匹配成功
    else
        return 0;
}
```

# 树

## 树的定义和基本术语

>除了根节点外，任何一个结点都有且仅有一个前驱

**术语**：祖先结点，子孙结点，双亲结点(父节点),子结点，兄弟结点，堂兄弟结点

**路径**：只能从上往下，经过了几条边，长度就是几

**属性**

- 结点的层次(深度):从上往下数
- 结点的高度：从下往上数
- 树的高度(深度):总共多少层
- 结点的度：有几个孩子(分支)
- 树的度：各结点的度的最大值

**有序树VS无序树**

- 有序树：从逻辑上看，树中结点的各子树从左至右是有次序的，不能互换
- 无序树：从逻辑上看，数中结点的各子树从左至右是无次序的，可以互换

**森林**：m课互不相交的树的集合

## 树的性质

- 树的结点数=总度数+1(即所有子孙结点+根节点)
- 度为m的树，m叉树的区别

| 度为m的树                     | m叉树                        |
| ----------------------------- | ---------------------------- |
| 任意结点的度<=m,(最多m个孩子) | 任意结点的度<=m(最多m个孩子) |
| 至少有一个结点度=m(有m个孩子) | 允许所有结点的度都<m         |
| 一定是非空数，至少有m+1个结点 | 可以是空树                   |

- 度为m的树第i层至多有$m^{i-1}$个结点

![](树的比较.png)

- 高度为h的m叉树至多有$\frac{m^h-1}{m-1}$个结点
- 高度为h的m叉树至少有h个结点
- 高度为h，度为m的树至少有h+m-1个结点

- 具有n个结点的m叉树的最小高度为$\lceil log_m(n(m-1)+1)\rceil$

## 二叉树的定义和基本概念

**特点**：

- 每个结点至多只有两棵子树
- 左右子树不能颠倒(二叉树是有序树)

**特殊二叉树**

- 满二叉树：一棵高度为h,且含有$2^h-1$个结点的二叉树
  - 只有最后一层有叶子结点
  - 不存在度为1的结点
  - 按层序从1开始编号，结点i的左孩子为2i，右孩子为2i+1;结点i的父节点为\[i/2\](如果有的话)
- 完全二叉树：当且仅当其每个结点都与高度为h的满二叉树中编号为1-n的结点一一对应时，称为完全二叉树。
  - 只有最后两层可能有叶子节点
  - 最多只有一个度为1的结点
  - 按层序从1开始编号，结点i的左孩子为2i，右孩子为2i+1;结点i的父节点为$\lfloor i的父节点 \rfloor$(如果有的话)
  - i<=[n/2]为分支节点，i>[n/2]为叶子节点
- 二叉排序树
  - 左子树上所有结点的关键字均小于根节点的关键字
  - 右子树上所有结点的关键字均大于根节点的关键字
  - 左右子树又各是一棵二叉排序树
- 平衡二叉树：树上任一结点的左子树和右子树的深度之差不超过1

## 二叉树的性质

**常考性质**

- 设非空二叉树中度为0,1,2的结点个数分别为$n_0,n_1,n_2$,则$n_0=n_2+1$
  - 假设树中结点总数为n，则
    - $n=n_0+n_1+n_2$
    - $n=n_1+2n_2+1$结点数等于总度数+1
- 二叉树第i层最多有$2^{i-1}$个结点
- 高度为h的二叉树至多有$2^h-1$个结点

**完全二叉树常考性质**

- 具有n个结点的完全二叉树高度h为$\lceil log_2(n+1)\rceil 或\lfloor log_2n\rfloor+1$

![](完全二叉树性质.png)

- 对于完全二叉树，可以由结点数n推出度为0,1,2的结点个数为$n_0,n_1,n_2$

![](完全二叉树的性质2.png)

## 二叉树的存储结构

**完全二叉树顺序存储**

```cpp
#define MaxSize 100
struct TreeNode{
    ElemType value;	//结点中的数据元素
    bool isEmpty;	//结点是否为空
};
//定义一个长度为MaxSize的数组t，按照从上至下，从左至右的顺序依次存储完全二叉树中的各个结点

//初始化设置各节点为空
TreeNode t[MaxSize];
for(int i=0;i<MaxSize;i++){
    t[i].isEmpty=true;
}
//可以空缺t[0]来使数组下标与二叉树序号一一对应
```

几个重要常考的基本操作

- i的左孩子  --2i
- i的右孩子  --2i+1
- i的父节点  --$\lfloor i/2 \rfloor$
- i所在的层次 ---$\lceil log_2(n+1) \rceil 或 \lfloor log_2n \rfloor +1$

若完全二叉树中共有n个结点，则

- 判断i是否有左孩子 --2i<=n？
- 判断i是否有右孩子 --2i+1<=n?
- 判断i是否是叶子/分支结点? --i>$\lfloor n/2 \rfloor$

>普通二叉树一定要把树的结点编号和完全二叉树对应起来

**二叉树的链式存储**

```cpp
//二叉树的结点(链式存储)
struct ElemType{
    int value;
}
typedef struct BiTNode{
    ElemType data;
    struct BiTNode *lchild, *rchild;
}BiTNode,*BiTree;

//定义一棵空树
BiTree root = NULL;
```

>n个结点的二叉链表共有n+1个空链域
>
>因为n个结点总共有2n个指针域，除了根节点外，每个结点头上都有一个指针，所以有效指针为n-1个，故空指针为n+1个

如果实际需求需要经常查找父节点的话，可以定义一个指向父节点的指针(三叉链表)

```cpp
typedef struct BiTNode{
    ElemType data;
    struct BiTNode *lchild,*rchild;
    struct BiTNode *parent;
}BiTNode,*BiTree;
```

## 二叉树的先中后序遍历

**二叉树的递归特性**

- 要么是个空二叉树
- 要么就是“根节点+左子树+右子树"
  - 先序遍历:根左右(NLR)：第一次路过访问
  - 中序遍历:左根右(LNR)：第二次路过访问
  - 后序遍历:左右根(LRN)：第三次路过访问

## 二叉树的层次遍历

**算法思想**

- 初始化一个辅助队列
- 根节点入队
- 若队列非空，则队头结点出队，访问该结点，并将其左右孩子插入队尾
- 重复第三条直至队列为空

## 由遍历序列来构造二叉树

必须有中序遍历，再加一个前序/后序遍历



## 线索二叉树

**找到p结点的中序遍历序列前驱**

- 从根节点触发，重新进行一次中序遍历，指针q记录当前访问的结点，指针pre记录上一个被访问的结点
  - 当q==p时，pre为前驱
  - 当pre=q时，q为后继 

![](线索二叉树.png)

```cpp
//二叉树的结点(链式存储)
typedef struct BiTNode{
    ElemType data;
    struct BiTNode *lchild,*rchild;
}BiTNode,*BiTree;

//线索二叉树结点
typedef struct ThreadNode{
    ElemType data;
    struct ThreadNode *lchild,*rchild;
    int ltag,rtag;	//左右线索标志
}ThreadNode, *ThreadTree;
//tag==0,表示指向孩子
//tag==1,表示指向线索

```

## 二叉树的线索化

```cpp
//中序遍历
void InOrder(BiTree T){
    if(T!=NULL){
        InOrder(T->lchild);	//递归遍历左子树
        visit(T);
        InOrder(T->rchild);	//递归遍历右子树
    }
}
//访问结点q
void visit(BiTNode *q){
    if(p==q)
        final = pre;//找到p的前驱
    else
        pre=q;	//移动pre访问当前结点
}
//辅助全局变量，用于查找结点p的前驱
BiTNode *p;		//p指向目标结点
BiTNode *pre=NULL; //指向当前访问结点的前驱
BiTNode *final=NULL;//用于记录最终结果   
```

```cpp
//线索二叉树结点
typedef struct ThreadNode{
    ElemType data;
    struct ThreadNode *lchild,*rchild;
    int ltag,rtag;	//左右线索标志
}ThreadNode, *ThreadTree;
//中序遍历二叉树,一边遍历一边线索化
void InThread(ThreadTree T){
    if(T!=NULL){
        InThread(T->lchild);//中序遍历左子树
        visit(T);			//访问根节点
        InThread(T->rchild);//中序遍历右子树
    }
}
void visit(ThreadNode *q){
    if(q->lchild==NULL){
        //左子树为空,建立前驱线索
        q->lchild=pre;
        q->ltag=1;
    }
    if(pre!=NULL&&pre->child==NULL){
        pre->rchild=1;	//建立前驱节点的后继线索
        pre->rtag=1;
    }
    pre=q;
}
//全局变量pre,指向当前访问结点的前驱
ThreadNode *pre=NULL;
```

## 在线索二叉树中寻找前驱后继

![](中序线索二叉树前驱.png)

|        | 中序线索二叉树 | 先序线索二叉树 | 后序线索二叉树 |
| ------ | -------------- | -------------- | -------------- |
| 找前驱 | √              | ×              | √              |
| 找后继 | √              | √              | ×              |

## 树的存储结构

**双亲表示法**(顺序存储)

```cpp
#define MAX_TREE_SIZE 100		//树中最多结点数
typedef struct{
    ElemType data;				//数据元素
    int parent;					//双亲位置域
}PTNode;
typedef struct{
    PTNode nodes[MAX_TREE_SIZE];	//双亲表示
    int n;							//结点数
}
```

**孩子表示法**(顺序+链式存储)

```cpp
struct CTNode{
    int child;		//孩子结点在数组中的位置
    struct CTNode *next;		//下一个孩子
};
typedef struct {
    ElemType data;
    struct CTNode *firstChild;		//第一个孩子
}CTBox;
typedef struct{
    CTBox nodes[MAX_TREE_SIZE];
    int n,r;	//结点数和根的位置
}CTree;
```

**孩子兄弟表示法**(链式存储)

![](树与二叉树的转化.png)

![](树转二叉树.png)

**森林和二叉树的转化**

![](森林转二叉树.png)

![](二叉树转森林.png)



## 树和森林的遍历

**树的先根遍历**:深度优先遍历

```cpp
//树的先根遍历
void PreOrder(TreeNode *R){
    if(R!==NULL){
        visit(R);	//访问根节点
        while(R还有下一个子树T)
            PreOrder(T);	//先根遍历下一棵子树
    }
}
```

>树的先根遍历序列与这棵树对应的二叉树的先序序列相同

**树的后根遍历**:深度优先遍历

![](后根遍历.png)

**树的层次遍历**(队列实现):广度优先遍历

- 若树为空,则根节点入队
- 若队列非空,队头元素出队并访问,同时将该元素的孩子依次入队
- 重复2直到队列为空

**森林的先序遍历**

- 若森林为非空,则按照如下规则进行遍历
- 访问森林中第一棵树的根节点
- 先序遍历第一棵树中根节点的子树森林
- 先序遍历剩余的树构成的森林

**森林的中序遍历**





## 哈夫曼树

**概念**

- 结点的权:有某种显示含义的数值(如:表示结点的重要性等)
- 结点的带权路径长度:从树的跟结点到该结点的路径长度(经过的边数)与该节点上权值的乘积
- 树的带权路径长度:树中所有叶子节点的带权路径长度之和(WPL,Weight Path Length)
  - $\sum\limits _{i=1}^n w_il_i$

在含由n个带权叶节点的二叉树中,其中{%label 带权路径长度(WPL)最小的二叉树 green%}称为{%label 哈夫曼树 red%},也称为最优二叉树

**哈夫曼树的构造**

给定n个权值分别为$w_1,w_2,...w_n$的结点,构造哈夫曼树的算法描述如下:

- 将这n个结点分别作为n棵仅含一个结点的二叉树,构成森林F
- 构造一个新结点,从F中选取两棵根节点权值最小的树作为新结点的左右子树,并且将新结点的权值置为左右子树根结点的权值之和
- 从F中删除刚才选出的两棵树,同时将新得到的树加入F中
- 重复2,3步骤,直到F中只剩下一棵树为止.

**哈夫曼树的性质**

- 每个初始节点最终都成为叶节点,且权值越小的结点到根节点的路径长度越大
- 哈夫曼树的节点总数为2n-1(初始n个结点,每次两两合并产生一个新的结点,合并n-1次,故产生n-1个新结点)
- 哈夫曼树中不存在度为1的结点
- 哈夫曼树不唯一

**哈夫曼编码**

固定长度编码:每个字符用相等长度的二进制位表示

![](哈夫曼编码.png)

可变长度编码:允许对不同字符用不等长的二进制位表示

若没有一个编码时另一个编码的前缀,则称这样的编码为{%label 前缀编码 green%}

![](哈夫曼编码2.png)

## 并查集

# 图

## 图的基本概念

**定义**:图G是由顶点集V和边集E组成，记为G=(V,E)，其中V(G)表示图G中顶点的有限非空集合；E(G)表示图G中各顶点之间的关系(边)集合。用$|V|$表示图G中顶点的个数，也成为图G的阶．用$|E|$表示图G中边的条数.

若E是无向边(简称为边)的有限集合时,则图G为无向图.边是顶点的无序对.

- 顶点v的度是指依附于该点的边的条数
- 顶点v到顶点w有路径存在,则称v和w是联通的
- 若图G中任意两个顶点之间是联通的,则称G为{%label 连通图 green%},否则为非连通图
- 有n个顶点的连通图G至少有n-1条边.有n个顶点的非连通图F最多有$C_{n-2}^2$条边.
- 无向图中的{%label 极大连通子图 green%}称为{%label 连通分量 green%}
- 连通图的{%label 生成树 green%}是包含图中全部顶点的一个极小的连通子图.
- 在非连通图中,连通分量的生成树构成了非连通图的{%label 生成森林 green%}
- 无向完全图:无向图中任意两个顶点之间都存在边

若E是有向边(也称为弧)的有限集合时,则图G为有向图．弧是顶点的有序对，记为$<v,w>$,其中v称为{%label 弧尾 green%},w称为{%label 弧头 green%}.$<v,w>$称为从顶点v到顶点w的弧.

- 入度是指以顶点v为终点的有向边的数目,记为ID(v)
- 出度是指以顶点v为起点的有向边的数目,记为OD(v)
- 顶点v的度等于其入度和出度之和.
- 在具有n个顶点,e条弧的有向图中,$\sum_{i=1}^n ID(v_i)= \sum_{i=1}^n OD(v_i)=e$
- 若<v,w>和<w,v>均存在,则这两个顶点是强连通的.
- 若图G中任意两个顶点都是强连通的,则称为强连通图.
- 含由n个顶点的强连通图至少有n条边(形成回路).
- 有向图中的{%label 极大强连通子图 green%}称为有向图的强连通分量.
- 有向完全图:有向图中任意两个顶点之间都存在方向相反的两条弧.

**简单图**:

- 不存在重复边
- 不存在顶点到自身的边

**多重图**:

- 图G中某两个结点之间的边数多于一条,又允许顶点通过同一条边和自己关联,则G为多重图.

**路径**:顶点$v_p$到顶点$v_q$之间的一条路径是指顶点序列,$v_p,v_{i_1},v_{i_2},v_{i_3},...v_q$

**回路**(环):第一个顶点和最后一个顶点相同的路径

**简单路径**:在路径序列中,顶点不重复出现的路径

**简单回来**:除第一个和最后一个顶点外,其余顶点不重复出现的回路称为简单回路.

**路径长度**:路径上边的数目

**点到点的距离**:从顶点u出发到顶点v的最短路径若存在,则称此路径的长度为从u到v的距离.若不存在,则记该距离为无穷.$\infty$

**子图**:设有两个图G=(V,E)和$G^{'}=(V^{'},E^{'})$,若$V^{'}$是V的子集,且$E^{'}$是E的子集,则称$G^{'}$是G的子图.

**生成子图**:若有满足$V(G^{'})=V(G)$的子图$G^{'}$,则称其为生成子图.

**边的权**:在一个图中,每条边都可以标注上具有某种含义的数值,该数值称为该边的权值.

**带权图/网**:边上带有权值的图称为带权图,也称为网.

**带权路径长度**:当图是带权图时,一条路径上所有边的权值之和,称为该路径的带权路径长度.

## 邻接矩阵法

邻接矩阵

## 十字链表，邻接多重表

## 图的基本操作

## 图的广度优先遍历
