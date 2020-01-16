## Algorithm With Python 算法的python实现

[TOC]

### 1.Stack 栈

#### 介绍

栈允许进行插入和删除操作的一端称为栈顶(top)，另一端为栈底(bottom)；栈底固定，而栈顶浮动；栈中元素个数为零时称为空栈。插入一般称为进栈（PUSH），删除则称为退栈（POP）。

#### 基本功能

| 功能                     | 描述                            |
| ------------------------ | ------------------------------- |
| init                     | 新建list，设定长度极限limit     |
| push进栈                 | 未超limit，加入list, Ot(1)      |
| pop出栈                  | 栈若非空弹出顶部元素pop(),Ot(1) |
| peek查看堆栈顶部元素     | 若非空，返回list[-1]            |
| is_empty判断栈是否为空： | return not bool(self.stack)     |
| size栈的大小：           | return len(self.stack)          |

#### 应用

| 功能                   | 描述                                                         |
| ---------------------- | ------------------------------------------------------------ |
| balanced_parentheses() | 1_001有效括号字符串：左括号必须用相同类型的右括号闭合。左括号必须以正确的顺序闭合。注意空字符串可被认为是有效字符串。 |
| class MinStack         | 1_002 最小栈(LeerCode 115)                                   |

### 2.linked_list 列表

#### 介绍

链表(linked_list)是物理存储单元上非连续的、非顺序的存储结构，数据元素的逻辑顺序是通过链表的指针地址实现，每个元素包含两个结点，一个是存储元素的数据域 (内存空间)，另一个是指向下一个结点地址的指针域。根据指针的指向，链表能形成不同的结构，例如单链表，双向链表，循环链表等。

#### 基本功能

| 功能                          | 描述                                                         |
| ----------------------------- | ------------------------------------------------------------ |
| Node.init                     | self.data = data             self.next = None                |
| Linked_List.init              | self.head = head                                             |
| append(new_element)           | 向链表添加新的结点                                           |
| is_empty()                    | 判断链表是否为空                                             |
| insert(position, new_element) | 往链表中任意位置添加一个 new_element 元素。<br/>先判断要插入的位置是否在链表的索引范围内。 <br/>当插入的位置是头结点（即索引为 0）时，做特殊情况处理。<br/> 当要插入结点的位置不在 0 时，找到要插入的位置，插入新结点 |
| remove(position)              | 从链表中任意位置删除一个元素。<br/>先判断要删除的元素索引是否存在，如果不存在抛出错误<br/>接着判断当存在链表元素时才能执行删除操作。<br/>当要删除的是头结点时（即索引为 0），做特殊情况处理。<br/>其他情况时，通过循环找到要删除的结点。<br/>最后要做的就是把这个结点删除掉。 |
| get_length                    | 获取链表的长度                                               |
| print_list                    | 遍历链表，并将元素依次打印出来                               |
| reverse                       | 将链表反转                                                   |
| initlist(data_list)           | 将列表转换为链表                                             |
|                               |                                                              |

#### 应用

| 功能                         | 描述                             |
| ---------------------------- | -------------------------------- |
| swapNodes(a,b)               | 2-001交换2个阶段的位置           |
| isPalindrome(head: ListNode) | 2-002 回文链表 （leet-code234*） |

#### *leetcode234回文链表

具体代码参见leetcode页面

1. 方法1

   ①非空和一位检验

   ②将链表数据遍历--->存入listA

   ③i=1，j=len(listA)-1，当i<=j时，循环遍历确认是否arr[i] != arr[j]，是，返回False

   ④循环结束，返回True

2. 方法2

   ①非空和一位检验

   ②找出链表中点

   ```python
   start = ListNode(-1)
   start.next = head
   slow,fast = start,start
   while fast and fast.next:
   	slow,fast = slow.next, fast.next.next
   ```

   ③此时前半部链表比后半部链表相同或多一位，后半部链表反转

   反转参考：https://www.cnblogs.com/tianqizhi/p/9673894.html

   ```
   pHead = slow.next
   end = None
   while pHead:
       tmp = pHead.next
       pHead.next = end
       end = pHead
       pHead = tmp
   ```

   ④后半部反转后表与原表比对，有不相等的值，返回False，全部比对结束，返回True

### 3.Double_linked_list 双链表

#### 介绍

双向链表（Double_linked_list）也叫双链表，是链表的一种，它的每个数据结点中都有两个指针，分别指向直接后继和直接前驱。所以，从双向链表中的任意一个结点开始，都可以很方便地访问它的前驱结点和后继结点。

#### 基本功能

| 功能              | 描述                                                         |
| ----------------- | ------------------------------------------------------------ |
| Node.init         | self.data = data             self.next = None      self.prev = None |
| DLinked_List.init | self.head = head      #head =None                            |
| is_empty()        | 判断链表是否为空                                             |
| travel()          | 遍历列表                                                     |
| add(item)         | 头部插入元素                                                 |
| append(item)      | 尾部插入元素                                                 |
| search(item)      | 查找元素是否存在                                             |
| insert(pos, item) | 在指定位置添加节点                                           |
| remove(item)      | 删除元素                                                     |
|                   |                                                              |

### 4.queue 队列

#### 介绍

队列 (queue) 是一种特殊的线性表，特殊之处在于它只允许在表的前端（front）进行删除操作，而在表的后端（rear）进行插入操作，和栈一样，队列是一种操作受限制的线性表。进行插入操作的端称为队尾，进行删除操作的端称为队头。

队列有两种实现形式，分为两种：**数组**和**链表**。

#### 基本功能

| 功能              | 描述                                          |
| ----------------- | --------------------------------------------- |
| Node.init         | self.data = data             self.next = None |
| DLinked_List.init | self.head = head      self.rear = None        |
| is_empty()        | 判断队列是否为空                              |
| enqueue(elem)     | 入队                                          |
| dequeue()         | 出队                                          |
| peek()            | 返回队头部元素                                |
| print_queue()     | 打印队列                                      |

### 5.tree 树

树 (tree) 是一种非常高效的非线性存储结构。树，可以很形象的理解，有根，有叶子，对应在数据结构中就是根节点、叶子节点，同一层的叶子叫兄弟节点，邻近不同层的叫父子节点，非常好理解。

其他概念解释

- **二叉树**，就是每个节点都至多有二个子节点的树。
- **满二叉树**，就是除了叶子节点外，每个节点都有左右两个子节点，这种二叉树叫做满二叉树。
- **完全二叉树**，就是叶子节点都在最底下两层，最后一层叶子节都靠左排列，并且除了最后一层，其他层的节点个数都要达到最大，这种二叉树叫做完全二叉树。

#### 基本功能

| 功能             | 描述                                                         |
| ---------------- | ------------------------------------------------------------ |
| Node.init        | self.item = item             self.left = None  # 表示左子节点         self.right = None  # 表示右子节点 |
| Tree.init        | self.root = Node('root')                                     |
| add(item)        | 添加子节点到树里面                                           |
| get_parent(item) | 找到 item 的父节点                                           |
| delete(item)     | 从二叉树中删除一个子节点*                                    |
| inorder(node)    | 中序遍历                                                     |
| postorder(node)  | 后续遍历                                                     |
| preorder(node)   | 先续遍历                                                     |

*删除二叉树

```shell
先获取待删除节点 item 的父节点（以下简称 item）。
    如果父节点不为空，判断 item 的左右子树是否存在：
        当左子树为空时，进一步判断 item 是父节点的左孩子，还是右孩子；
            如果是左孩子，将父节点的左指针指向 item 的右子树，反之将父节点的右指针指向 item 的右子树。
        当右子树为空时，进一步判断 item 是父节点的左孩子，还是右孩子；
            如果是左孩子，将父节点的左指针指向 item 的左子树，反之将父节点的右指针指向 item 的左子树。
        当左右子树均不为空时，寻找右子树中的最左叶子节点 x，将 x 替代要删除的节点。
    删除成功，返回 True。
    删除失败, 返回 False。
```

#### 应用

| 功能                   | 描述                                                         |
| ---------------------- | ------------------------------------------------------------ |
| sortedArrayToBST(list) | 5-001[将有序数组转换为二叉搜索树](https://leetcode-cn.com/problems/convert-sorted-array-to-binary-search-tree/)(leet-code108) |
| maxDepth(root)         | 5-002二叉树的最大深度(leet-code104)                          |
| isSymmetric(root)      | 5-003对称二叉树leet-code101                                  |

### 6.TrieNode字典树

字典树，又称单词查找树，Trie  树，是一种树形结构，是一种哈希树的变种。典型应用是用于统计，排序和保存大量的字符串（但不仅限于字符串），所以经常被搜索引擎系统用于文本词频统计。它的优点是：利用字符串的公共前缀来减少查询时间，最大限度地减少无谓的字符串比较，查询效率比哈希树高。

#### 字典树的主要性质

它有 3 个基本性质：

1. 根节点不包含字符，除根节点外每一个节点都只包含一个字符；
2. 从根节点到某一节点，路径上经过的字符连接起来，为该节点对应的字符串；
3. 每个节点的所有子节点包含的字符都不相同。

#### 基本功能

| 功能               | 描述                                                |
| ------------------ | --------------------------------------------------- |
| TrieNode.init      | self.nodes = dict()            self.is_leaf = False |
| insert(word)       | 插入一个字到字典树中                                |
| insert_many(words) | 插入一列表的字到字典树中（循环insert()）            |
| search(word)       | 在字典树里面查询一个字                              |

### 7.heap 堆

堆 (heap) 是一种经过排序的完全二叉树，其中任一非叶子节点的值均不大于（或不小于）其左孩子和右孩子节点的值。

其他概念解释

- **最大堆** 根结点的键值是所有堆结点键值中最大者。
- **最小堆** 根结点的键值是所有堆结点键值中最小者。

#### 基本功能

| 功能                     | 描述                                                         |
| ------------------------ | ------------------------------------------------------------ |
| heap.init                | self.data_list = []                                          |
| get_parent_index( index) | 返回父节点的下标，使用二进制位移>>                           |
| swap( index_a, index_b)  | 交换数组中的两个元素                                         |
| insert(data)             | 插入元素并堆化# 先把元素放在最后，然后从后往前依次堆化，以大顶堆为例，如果插入元素比父节点大，则交换，直到最后 |
| removeMax()              | 删除堆顶元素，然后将最后一个元素放在堆顶，再从上往下依次堆化 |
| heapify(index)           | 从上往下堆化，从index 开始堆化操作 (大顶堆)==@.@==           |

### 8.Graph 图

- **无向图** 图是若干个顶点(Vertices)和边(Edges)相互连接组成的。边仅由两个顶点连接，并且没有方向的图称为无向图。

- **有向图** 在有向图中，边是单向的：每条边连接的两个顶点都是一个有序对，它们的邻接性是单向的。我们开发过程中碰到的很多场景都是有向图：比如任务调度的依赖关系，社交网络的任务关系等等都是天然的有向图。

- **度** 一个顶点的度是指与该顶点相关联的边的条数，顶点 v 的度记作 d(v)。

  表示图通常有四种方法：数组表示法、邻接表、十字链表和邻接多重表。邻接表是图的一种链式存储结构，十字链表是有向图的另一种链式存储结构，邻接多重表是无向图的另一种链式存储结构。

  #### 基本功能

  **待添加**

### 9.并查集

待添加







### 10.线性代数

资源：[沉浸式线性代数](http://immersivemath.com/ila/index.html)。[麻省理工公开课:线性代数_全三集](http://open.163.com/special/opencourse/daishu.html)。[3Blue1Brown](https://space.bilibili.com/88461692?from=search&seid=9898388095015449432)。孟岩的《理解矩阵》    

- **标量** 一个标量就是一个单独的数，一般用小写的变量名称表示。
- **向量** 一个向量就是一列数，这些数是有序排列的。用过次序中的索引，我们可以确定每个单独的数。通常会赋予向量粗体的小写名称。
- **矩阵** 一个矩阵是二维数组，其中的每一个元素被两个索引而非一个所确定。我们通常会赋予矩阵粗体的大写变量名称，比如 A。
- **张量** 几何代数中定义的张量是基于向量和矩阵的推广，通俗一点理解的话，我们可以将标量视为零阶张量，矢量视为一阶张量，那么矩阵就是二阶张量。一般地，一个数组中的元素分布在若干维坐标的规则网格中，我们将其称之为张量。使用粗体 A 来表示张量“A”

### 11.search搜索

#### ①顺序搜索

**算法原理**

**思路：**从数据结构线性表的一端开始，顺序扫描，依次将扫描到的结点关键字与给定值 k 相比较，若相等则表示查找成功；若扫描结束仍没有找到关键字等于 k 的结点，表示查找失败。

**适用性：**顺序搜索适合于存储结构为顺序存储或链接存储的线性表。

**复杂度分析**

最坏复杂度: 从一个线性表依次查找对应项，需要做 n 次查找，在最后一项才查找到对应项或者查找失败（仍然未查找到对应项），时间复杂度为 O(n)。

最好复杂度: 从一个线性表依次查找对应项，第一项就查找到对应项,时间复杂度为 O(1)。

平均复杂度: 假设每个数据元素的概率相等（1/n),1/n(1+2+3+...+n)=(n+1)/2，所以时间复杂度为 O(n)。

#### ②二分搜索Binary Search

二分搜索也称折半搜索（Binary Search），它是一种效率较高的搜索方法。但是，二分搜索要求线性表必须采用顺序存储结构，而且表中元素按关键字有序排列。

**适用性：** 二分查找的前提是有序表存储，如果是无序的则先要进行排序操作。对于静态查找表，一次排序后不再变化，折半查找能得到不错的效率。但对于需要频繁执行插入或删除操作的数据集来说，维护有序的排序会带来不小的工作量，那就不建议使用。——《大话数据结构》

**基本思想：** 用给定值 k 先与中间结点的关键字比较，中间结点把线性表分成两个子表，若相等则查找成功；若不相等，再根据 k 与该中间结点关键字的比较结果确定下一步查找哪个子表，这样递归进行，直到查找到或查找结束发现表中没有这样的结点。

**最坏复杂度:**上述分析可以得到时间复杂度为 O(logn)。

**最好复杂度：**第一次折半就查找到中间元素,时间复杂度为 O(1)。

**平均复杂度:**时间复杂度为 O(logn)

**拓展**：叁分搜索：在二分搜索的基础上，将区间分为三个区间做判断，因此存在 5 个条件判断

#### ③差值搜索

**算法原理**

**适用性：** 对于表长较大，而关键字分布又比较均匀的查找表来说，插值搜索算法的平均性能比折半搜索要好的多。反之，数组中如果分布非常不均匀，那么插值搜索未必是很合适的选择。

**基本思想：** 基于二分搜索算法，只是在取"中点"的时候把比例参数 1/2 修改为自适应参数，可以提高搜索效率。当然，差值搜索也属于有序搜索。

二分搜索：查找点计算如下：mid=(left+right)/2, 即 mid=left+1/2*(right-left)

差值搜索：将查找的点改进为如下： mid=left+(key-a[left])/(a[right]-a[left])*(right-left)，也就是将上述的比例参数 1/2 改进为自适应的，根据关键字在整个有序表中所处的位置，让 mid 值的变化更靠近关键字 key，这样也就间接地减少了比较次数。

**复杂度分析**

**最坏复杂度:**时间复杂度为 O(logn)，最坏的情况就是二分搜索的情况，时间复杂度和二分搜索的时间复杂度相同。

**最好复杂度：**时间复杂度为 O(1)。

**平均复杂度:**时间复杂度为 O(loglogn)

#### ④跳跃搜索Jump search

**算法原理**

**适用性：** 跳跃搜索的前提是有序表存储。相比于二分搜索，跳跃搜索仅遍历一次，而二分搜索最多需要 O(logn)，如果向后跳跃比向前跳跃花费更多时间，考虑要搜索的元素是最小元素或小于最小的，我们一般选用跳跃搜索。

**基本思想：** 基于二分搜索算法，采用固定间隔进行跳跃，直到找到一个符合目标元素的区间，然后在该区间使用线性搜索，找到目标元素的确切位置。

**复杂度分析**

**最坏复杂度:**时间复杂度为 O(n^(1/2))

**最好复杂度：**时间复杂度为 O(n^(1/2))

**平均复杂度:**时间复杂度为 O(n^(1/2))

#### ⑤快速搜索quick search

快速选择是一种选择算法，用于查找无序列表中的第 k 个最小元素，它与快速排序算法有关。

**适用性：** 用于查找无序列表中的第 k 个最小元素或最大元素。

**基本思想：** 基于二分搜索算法，采用固定间隔进行跳跃，直到找到一个符合目标元素的区间，然后在该区间使用线性搜索，找到目标元素的确切位置。

**最坏复杂度:**时间复杂度为 O(n^2)。

**最好复杂度：**时间复杂度为 O(n)。

**平均复杂度:**时间复杂度为 O(n)。

#### ⑥哈希搜索

哈希表就是一种以键-值(key-indexed) 存储数据的结构，只要输入待查找的键即  key，即可查找到其对应的值。哈希表是一个在时间和空间上做出权衡的经典例子。如果没有内存限制，那么可以直接将键作为数组的索引。那么所有的查找时间复杂度为  O(1)；如果没有时间限制，那么我们可以使用无序数组并进行顺序查找，这样只需要很少的内存。哈希表使用了适度的时间和空间来在这两个极端之间找到了平衡。只需要调整哈希函数算法即可在时间和空间上做出取舍。

**适用性：** 一个简单无序数组即可实现索引关系。

**基本思想：** 哈希的思路很简单，如果所有的键都是整数，那么就可以使用一个简单的无序数组来实现：将键作为索引，值即为其对应的值，这样就可以快速访问任意键的值。这是对于简单的键的情况，我们将其扩展到可以处理更加复杂的类型的键。

**最坏复杂度:**时间复杂度为 O(1),对于无冲突的哈希表而言。

**最好复杂度：**时间复杂度为 O(1),对于无冲突的哈希表而言。

**平均复杂度:**时间复杂度为 O(1),对于无冲突的哈希表而言。





### 哈希            

### 哈希表            

### 混沌机            

### 数学上几个基本问题            

### 斐波那契数列问题            

- 

- 

- 

   

### 常见的排序算法介绍            

### 正则表达式的使用            

### 数论基础            

### 双重哈希            

### 摘要算法            

### 算术分析方法            

### 最大公约数问题            

### 常见的搜索算法介绍            

### 字符串的基本概念            

### 常见的字符串处理算法            