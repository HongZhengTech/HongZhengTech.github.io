---
title: 常用数据结构介绍
categories: 数据结构
---
# 常用数据结构介绍

# 0 概述

数据结构描述了计算机中存储、组织数据的方式。许多大型系统的编写经验显示，程序设计的困难程度与最终成果的质量与表现，取决于是否选择了最适合的数据结构。

数据结构种类非常多，而且每个种类下的细分种类也很多。这里主要介绍8种最常用的数据结构。

# 1 数组

![Untitled](%E5%B8%B8%E7%94%A8%E6%95%B0%E6%8D%AE%E7%BB%93%E6%9E%84%E4%BB%8B%E7%BB%8D%20e93a376e1ea9478aac2e8f9a727ee3c5/Untitled.png)

数组可以说是最基本最常见的数据结构。数组一般用来存储相同类型的数据，可通过数组名和下标进行数据的访问和更新。数组中元素的存储是按照先后顺序进行的，同时在内存中也是按照这个顺序进行连续存放。数组相邻元素之间的内存地址的间隔一般就是数组数据类型的大小。

数组包括一维数组和多维数组。

# 2 链表

![Untitled](%E5%B8%B8%E7%94%A8%E6%95%B0%E6%8D%AE%E7%BB%93%E6%9E%84%E4%BB%8B%E7%BB%8D%20e93a376e1ea9478aac2e8f9a727ee3c5/Untitled%201.png)

链表相较于数组，除了数据域，还增加了指针域用于构建链式的存储数据。链表中每一个节点都包含此节点的数据和指向下一节点地址的指针。由于是通过指针进行下一个数据元素的查找和访问，使得链表的自由度更高。

这表现在对节点进行增加和删除时，只需要对上一节点的指针地址进行修改，而无需变动其它的节点。不过事物皆有两极，指针带来高自由度的同时，自然会牺牲数据查找的效率和多余空间的使用。

链表包括单向链表、双向链表、循环链表。跳表也是链表的一种形式。

```tsx
/**
 * 单向链表的增删查
 */

class LinkedNode {
    constructor(public data: number, public next: LinkedNode | null = null) { }
}

class LinkedList {
    private head: LinkedNode | null = null;

    public insert(data: number) {
        const node = new LinkedNode(data);
        if (!this.head) {
            this.head = node;
        } else {
            let current = this.head;
            while (current.next) {
                current = current.next;
            }
            current.next = node;
        }
    }

    public delete(data: number) {
        if (!this.head) {
            return;
        }
        if (this.head.data === data) {
            this.head = this.head.next;
            return;
        }
        let current = this.head;
        while (current.next) {
            if (current.next.data === data) {
                current.next = current.next.next;
                return;
            }
            current = current.next;
        }
    }

    public search(data: number): boolean {
        if (!this.head) {
            return false;
        }
        let current: LinkedNode | null = this.head;
        while (current) {
            if (current.data === data) {
                return true;
            }
            current = current.next;
        }
        return false;
    }
}

// test case
const list = new LinkedList();
list.insert(1);
list.insert(2);
list.insert(3);
list.insert(4);
list.insert(5);
list.delete(3);
console.log(list.search(3)); // false
console.log(list.search(4)); // true
```

## 2.1 链表与数组的比对

|  | 数组 | 链表 |
| --- | --- | --- |
| 内存地址 | 连续。 | 不连续。 |
| 增删效率 | 低。为了保持存储的连续性，需要移动对应元素后面所有元素的位置。 | 高。只需要修改对应元素的指针指向。 |
| 查询效率 | 高。由于数据存储的连续性和数据类型一致性，可通过index直接定位到对应元素。 | 低。需要按顺序从链表头节点开始顺着指向往后找。 |

# 3 栈

![https://ask.qcloudimg.com/http-save/yehe-5359587/f1uyb7t5l4.gif](https://ask.qcloudimg.com/http-save/yehe-5359587/f1uyb7t5l4.gif)

栈是一种比较简单的数据结构，常用一句话描述其特性，后进先出。栈本身是一个线性表，但是在这个表中只有一个口子允许数据的进出。

栈的常用操作包括入栈push和出栈pop，对应于数据的压入和压出。还有访问栈顶数据、判断栈是否为空和判断栈的大小等。由于栈后进先出的特性，常可以作为数据操作的临时容器，对数据的顺序进行调控，与其它数据结构相结合可获得许多灵活的处理。

# 4 队列

![https://ask.qcloudimg.com/http-save/yehe-5359587/uj2ybsqwq7.gif](https://ask.qcloudimg.com/http-save/yehe-5359587/uj2ybsqwq7.gif)

队列是栈的兄弟结构，与栈的后进先出相对应，队列是一种先进先出的数据结构。顾名思义，队列的数据存储是如同排队一般，先存入的数据先被压出。常与栈一同配合，可发挥最大的实力。

队列包括单向队列和双向队列。

# 5 树

![Untitled](%E5%B8%B8%E7%94%A8%E6%95%B0%E6%8D%AE%E7%BB%93%E6%9E%84%E4%BB%8B%E7%BB%8D%20e93a376e1ea9478aac2e8f9a727ee3c5/Untitled%202.png)

![Untitled](%E5%B8%B8%E7%94%A8%E6%95%B0%E6%8D%AE%E7%BB%93%E6%9E%84%E4%BB%8B%E7%BB%8D%20e93a376e1ea9478aac2e8f9a727ee3c5/Untitled%203.png)

树作为一种树状的数据结构，其数据节点之间的关系也如大树一样，将有限个节点根据不同层次关系进行排列，从而形成数据与数据之间的父子关系。常见的数的表示形式更接近“倒挂的树”，因为它将根朝上，叶朝下。

树的数据存储在结点中，每个结点有零个或者多个子结点。没有父结点的结点在最顶端，成为根节点；没有非根结点有且只有一个父节点；每个非根节点又可以分为多个不相交的子树。

这意味着树是具备层次关系的，父子关系清晰，家庭血缘关系明朗；这也是树与图之间最主要的区别。

树可看作是链表的高配版。树的实现就是对链表的指针域进行了扩充，增加了多个地址指向子结点。同时将“链表”竖起来，从而凸显了结点之间的层次关系，更便于分析和理解。

树可以衍生出许多的结构，若将指针域设置为双指针，那么即可形成最常见的二叉树，即每个结点最多有两个子树的树结构。二叉树根据结点的排列和数量还可进一度划分为完全二叉树、满二叉树、平衡二叉树、红黑树等。

树的应用场景较多，在操作系统文件系统的存储中用到了树的数据结构。

## 5.2 树的分类

### 完全二叉树

除了最后一层结点，其它层的结点数都达到了最大值；同时最后一层的结点都是按照从左到右依次排布。

### 满二叉树

除了最后一层，其它层的结点都有两个子结点。

### 二叉排序树

对于其上的每个节点，若它的左子树不空，则左子树上所有结点的值均小于它的根结点的值；若它的右子树不空，则右子树上所有结点的值均大于它的根结点的值；它的左、右子树也分别为二叉排序树。

### 平衡二叉树

平衡二叉树又被称为AVL树，它是一棵二叉排序树，且具有以下性质：它是一棵空树或它的左右两个子树的高度差的绝对值不超过1，并且左右两个子树都是一棵平衡二叉树。

```tsx
/**
 * 二叉树的增删查
 */
class TreeNode {
    constructor(
        public val: number,
        public left: TreeNode | null = null,
        public right: TreeNode | null = null
    ) { }
}

class BST {
    private root: TreeNode | null = null;
    constructor() { }
    public insert(val: number): void {
        const node = new TreeNode(val);
        if (this.root === null) {
            this.root = node;
        } else {
            this.insertNode(this.root, node);
        }
    }
    private insertNode(root: TreeNode, node: TreeNode): void {
        if (root.val > node.val) {
            if (root.left === null) {
                root.left = node;
            } else {
                this.insertNode(root.left, node);
            }
        } else {
            if (root.right === null) {
                root.right = node;
            } else {
                this.insertNode(root.right, node);
            }
        }
    }
    public inOrderTraverse(): number[] {
        const result: number[] = [];
        this.inOrderTraverseNode(this.root, result);
        return result;
    }
    private inOrderTraverseNode(root: TreeNode | null, result: number[]): void {
        if (root !== null) {
            this.inOrderTraverseNode(root.left, result);
            result.push(root.val);
            this.inOrderTraverseNode(root.right, result);
        }
    }
    public preOrderTraverse(): number[] {
        const result: number[] = [];
        this.preOrderTraverseNode(this.root, result);
        return result;
    }
    private preOrderTraverseNode(root: TreeNode | null, result: number[]): void {
        if (root !== null) {
            result.push(root.val);
            this.preOrderTraverseNode(root.left, result);
            this.preOrderTraverseNode(root.right, result);
        }
    }
    public postOrderTraverse(): number[] {
        const result: number[] = [];
        this.postOrderTraverseNode(this.root, result);
        return result;
    }
    private postOrderTraverseNode(root: TreeNode | null, result: number[]): void {
        if (root !== null) {
            this.postOrderTraverseNode(root.left, result);
            this.postOrderTraverseNode(root.right, result);
            result.push(root.val);
        }
    }
    public search(val: number): boolean {
        return this.searchNode(this.root, val);
    }
    private searchNode(root: TreeNode | null, val: number): boolean {
        if (root === null) {
            return false;
        }
        if (root.val > val) {
            return this.searchNode(root.left, val);
        } else if (root.val < val) {
            return this.searchNode(root.right, val);
        } else {
            return true;
        }
    }
    public remove(val: number): void {
        this.root = this.removeNode(this.root, val);
    }
    private removeNode(root: TreeNode | null, val: number): TreeNode | null {
        if (root === null) {
            return null;
        }
        if (root.val > val) {
            root.left = this.removeNode(root.left, val);
            return root;
        } else if (root.val < val) {
            root.right = this.removeNode(root.right, val);
            return root;
        } else {
            if (root.left === null && root.right === null) {
                root = null;
                return root;
            }
            if (root.left === null) {
                root = root.right;
                return root;
            } else if (root.right === null) {
                root = root.left;
                return root;
            }
            const aux = this.findMinNode(root.right);
            root.val = aux.val;
            root.right = this.removeNode(root.right, aux.val);
            return root;
        }
    }
    private findMinNode(root: TreeNode): TreeNode {
        while (root.left !== null) {
            root = root.left;
        }
        return root;
    }
}

// test case
const bst = new BST();
bst.insert(11);
bst.insert(7);
bst.insert(15);
bst.insert(5);
bst.insert(3);
bst.insert(9);
bst.insert(8);
bst.insert(10);
bst.insert(13);
console.log(bst.inOrderTraverse()); // [3, 5, 7, 8, 9, 10, 11, 13, 15]
console.log(bst.preOrderTraverse()); // [11, 7, 5, 3, 9, 8, 10, 15, 13]
console.log(bst.postOrderTraverse()); // [3, 5, 8, 10, 9, 7, 13, 15, 11]
console.log(bst.search(1)); // false
console.log(bst.search(8)); // true
bst.remove(15);
console.log(bst.inOrderTraverse()); // [3, 5, 7, 8, 9, 10, 11, 13]
```

# 6 堆

![Untitled](%E5%B8%B8%E7%94%A8%E6%95%B0%E6%8D%AE%E7%BB%93%E6%9E%84%E4%BB%8B%E7%BB%8D%20e93a376e1ea9478aac2e8f9a727ee3c5/Untitled%204.png)

了解完二叉树，再来理解堆就不是什么难事了。堆通常是一个可以被看做一棵树的数组对象。堆的具体实现一般不通过指针域，而是通过构建一个一维数组与二叉树的父子结点进行对应，因此堆总是一颗完全二叉树。

对于任意一个父节点的序号n来说（这里n从0算），它的子节点的序号一定是2n+1，2n+2，因此可以直接用数组来表示一个堆。

不仅如此，堆还有一个性质：堆中某个节点的值总是不大于或不小于其父节点的值。将根节点最大的堆叫做最大堆或大根堆，根节点最小的堆叫做最小堆或小根堆。

堆常用来实现优先队列，在面试中经常考的问题都是与排序有关，比如堆排序、topK问题等。由于堆的根节点是序列中最大或者最小值，因而可以在建堆以及重建堆的过程中，筛选出数据序列中的极值，从而达到排序或者挑选topK值的目的。****

```tsx
/**
 * 大根堆的维护
 */
class MaxHeap {
    private data: number[] = [];
    private count: number = 0;

    constructor() { }

    public size(): number {
        return this.count;
    }

    public isEmpty(): boolean {
        return this.count === 0;
    }

    public insert(item: number): void {
        this.data[this.count + 1] = item;
        this.count++;
        this.shiftUp(this.count);
    }

    private shiftUp(k: number): void {
        while (k > 1 && this.data[Math.floor(k / 2)] < this.data[k]) {
            this.swap(k, Math.floor(k / 2));
            k = Math.floor(k / 2);
        }
    }

    private swap(i: number, j: number): void {
        const temp = this.data[i];
        this.data[i] = this.data[j];
        this.data[j] = temp;
    }

    public extractMax(): number {
        if (this.count > 0) {
            const ret = this.data[1];
            this.swap(1, this.count);
            this.count--;
            this.shiftDown(1);
            return ret;
        }
        return -1;
    }

    private shiftDown(k: number): void {
        while (2 * k <= this.count) {
            let j = 2 * k;
            if (j + 1 <= this.count && this.data[j + 1] > this.data[j]) {
                j++;
            }
            if (this.data[k] >= this.data[j]) {
                break;
            }
            this.swap(k, j);
            k = j;
        }
    }
}

// test case
const maxHeap = new MaxHeap();
maxHeap.insert(1);
maxHeap.insert(2);
maxHeap.insert(3);
maxHeap.insert(4);
maxHeap.insert(5);
maxHeap.insert(6);
maxHeap.insert(7);
maxHeap.insert(8);
maxHeap.insert(9);

while (!maxHeap.isEmpty()) {
    console.log(maxHeap.extractMax());
} // 9 8 7 6 5 4 3 2 1
```

# 7 图

![Untitled](%E5%B8%B8%E7%94%A8%E6%95%B0%E6%8D%AE%E7%BB%93%E6%9E%84%E4%BB%8B%E7%BB%8D%20e93a376e1ea9478aac2e8f9a727ee3c5/Untitled%205.png)

图结构一般包括顶点和边，顶点通常用圆圈来表示，边就是这些圆圈之间的连线。边还可以根据顶点之间的关系设置不同的权重，默认权重相同皆为1。此外根据边的方向性，还可将图分为有向图和无向图。

## 7.1 图的表示方法

### 邻接矩阵

![Untitled](%E5%B8%B8%E7%94%A8%E6%95%B0%E6%8D%AE%E7%BB%93%E6%9E%84%E4%BB%8B%E7%BB%8D%20e93a376e1ea9478aac2e8f9a727ee3c5/Untitled%206.png)

![Untitled](%E5%B8%B8%E7%94%A8%E6%95%B0%E6%8D%AE%E7%BB%93%E6%9E%84%E4%BB%8B%E7%BB%8D%20e93a376e1ea9478aac2e8f9a727ee3c5/Untitled%207.png)

用二维数组来存储节点间的关系。

### 邻接表

![Untitled](%E5%B8%B8%E7%94%A8%E6%95%B0%E6%8D%AE%E7%BB%93%E6%9E%84%E4%BB%8B%E7%BB%8D%20e93a376e1ea9478aac2e8f9a727ee3c5/Untitled%208.png)

在邻接表中，每一个顶点都对应着一条链表，链表中存储的是顶点能够达到的相邻顶点。存储的顺序可以按照顶点的编号顺序进行。比如上图中对于顶点B来说，其通过有向边可以到达顶点A和顶点E，那么其对应的邻接表中的顺序即B->A->E，其它顶点亦如此。

### 逆邻接表

![Untitled](%E5%B8%B8%E7%94%A8%E6%95%B0%E6%8D%AE%E7%BB%93%E6%9E%84%E4%BB%8B%E7%BB%8D%20e93a376e1ea9478aac2e8f9a727ee3c5/Untitled%209.png)

通过邻接表可以获得从某个顶点出发能够到达的顶点，从而省去了对不相连顶点的存储空间。然而，这还不够。对于有向图而言，图中有效信息除了从顶点“指出去”的信息，还包括从别的顶点“指进来”的信息。这里的“指出去”和“指进来”可以用出度和入度来表示。

> *入度：有向图的某个顶点作为终点的次数和。
出度：有向图的某个顶点作为起点的次数和。*
> 

由此看出，在对有向图进行表示时，邻接表只能求出图的出度，而无法求出入度。这个问题很好解决，那就是增加一个表用来存储能够到达某个顶点的相邻顶点。这个表称作逆邻接表。

逆邻接表与邻接表结构类似，只不过图的顶点链接着能够到达该顶点的相邻顶点。也就是说，邻接表时顺着图中的箭头寻找相邻顶点，而逆邻接表时逆着图中的箭头寻找相邻顶点。

邻接表和逆邻接表的共同使用下，就能够把一个完整的有向图结构进行表示。可以发现，邻接表和逆邻接表实际上有一部分数据时重合的，因此可以将两个表合二为一，从而得到了所谓的十字链表。

### 十字链表

![Untitled](%E5%B8%B8%E7%94%A8%E6%95%B0%E6%8D%AE%E7%BB%93%E6%9E%84%E4%BB%8B%E7%BB%8D%20e93a376e1ea9478aac2e8f9a727ee3c5/Untitled%2010.png)

十字链表似乎很简单，只需要通过相同的顶点分别链向以该顶点为终点和起点的相邻顶点即可。

但这并不是最优的表示方式。虽然这样的方式共用了中间的顶点存储空间，但是邻接表和逆邻接表的链表节点中重复出现的顶点并没有得到重复利用，反而是进行了再次存储。因此，上图的表示方式还可以进行进一步优化。

十字链表优化后，可通过扩展的顶点结构和边结构来进行正逆邻接表的存储：（下面的弧头可看作是边的箭头那端，弧尾可看作是边的圆点那端）

> data：用于存储该顶点中的数据；
firstin指针：用于连接以当前顶点为弧头的其他顶点构成的链表，即从别的顶点指进来的顶点；
firstout指针：用于连接以当前顶点为弧尾的其他顶点构成的链表，即从该顶点指出去的顶点；
> 

边结构通过存储两个顶点来确定一条边，同时通过分别代表这两个顶点的指针来与相邻顶点进行链接：

> tailvex：用于存储作为弧尾的顶点的编号；
headvex：用于存储作为弧头的顶点的编号；
headlink 指针：用于链接下一个存储作为弧头的顶点的节点；
taillink 指针：用于链接下一个存储作为弧尾的顶点的节点；
> 

![Untitled](%E5%B8%B8%E7%94%A8%E6%95%B0%E6%8D%AE%E7%BB%93%E6%9E%84%E4%BB%8B%E7%BB%8D%20e93a376e1ea9478aac2e8f9a727ee3c5/Untitled%2011.png)

以上图为例子，对于顶点A而言，其作为起点能够到达顶点E。因此在邻接表中顶点A要通过边`AE`（即边04）指向顶点E，顶点A的`firstout`指针需要指向边04的`tailvex`。同时，从B出发能够到达A，所以在逆邻接表中顶点A要通过边`AB`（即边10）指向B，顶点A的`firstin`指针需要指向边10的弧头，即`headlink`指针。依次类推。

十字链表采用了一种看起来比较繁乱的方式对边的方向性进行了表示，能够在尽可能降低存储空间的情况下增加指针保留顶点之间的方向性。具体的操作可能一时间不好弄懂，建议多看几次上图，弄清指针指向的意义，明白正向和逆向邻接表的表示。

# 8 散列表

![Untitled](%E5%B8%B8%E7%94%A8%E6%95%B0%E6%8D%AE%E7%BB%93%E6%9E%84%E4%BB%8B%E7%BB%8D%20e93a376e1ea9478aac2e8f9a727ee3c5/Untitled%2012.png)

散列表也叫哈希表，是一种通过键值对直接访问数据的机构。在初中，我们就学过一种能够将一个x值通过一个函数获得对应的一个y值的操作，叫做映射。散列表的实现原理正是映射的原理，通过设定的一个关键字和一个映射函数，就可以直接获得访问数据的地址，实现O(1)的数据访问效率。在映射的过程中，事先设定的函数就是一个映射表，也可以称作散列函数或者哈希函数。

散列表的实现最关键的就是散列函数的定义和选择。一般常用的有以下几种散列函数：

> 直接寻址法：取关键字或关键字的某个线性函数值为散列地址。
数字分析法：通过对数据的分析，发现数据中冲突较少的部分，并构造散列地址。例如同学们的学号，通常同一届学生的学号，其中前面的部分差别不太大，所以用后面的部分来构造散列地址。
平方取中法：当无法确定关键字里哪几位的分布相对比较均匀时，可以先求出关键字的平方值，然后按需要取平方值的中间几位作为散列地址。这是因为：计算平方之后的中间几位和关键字中的每一位都相关，所以不同的关键字会以较高的概率产生不同的散列地址。
取随机数法：使用一个随机函数，取关键字的随机值作为散列地址，这种方式通常用于关键字长度不同的场合。
除留取余法：取关键字被某个不大于散列表的表长 n 的数 m 除后所得的余数 p 为散列地址。这种方式也可以在用过其他方法后再使用。该函数对 m 的选择很重要，一般取素数或者直接用 n。
> 

确定好散列函数之后，通过某个`key`值的确会得到一个唯一的`value`地址。但是却会出现一些特殊情况。即通过不同的`key`值可能会访问到同一个地址，这个现象称之为冲突。

冲突在发生之后，当在对不同的`key`值进行操作时会使得造成相同地址的数据发生覆盖或者丢失，是非常危险的。所以在设计散列表往往还需要采用冲突解决的办法。

常用的冲突处理方式有很多，常用的包括以下几种：

> 开放地址法（也叫开放寻址法）：实际上就是当需要存储值时，对Key哈希之后，发现这个地址已经有值了，这时该怎么办？不能放在这个地址，不然之前的映射会被覆盖。这时对计算出来的地址进行一个探测再哈希，比如往后移动一个地址，如果没人占用，就用这个地址。如果超过最大长度，则可以对总长度取余。这里移动的地址是产生冲突时的增列序量。
再哈希法：在产生冲突之后，使用关键字的其他部分继续计算地址，如果还是有冲突，则继续使用其他部分再计算地址。这种方式的缺点是时间增加了。
链地址法：链地址法其实就是对Key通过哈希之后落在同一个地址上的值，做一个链表。其实在很多高级语言的实现当中，也是使用这种方式处理冲突的。
公共溢出区：这种方式是建立一个公共溢出区，当地址存在冲突时，把新的地址放在公共溢出区里。
> 

目前比较常用的冲突解决方法是链地址法，一般可以通过数组和链表的结合达到冲突数据缓存的目的。

```tsx
/**
 * 采用除留取余法作为散列函数，开放地址法作为冲突解决方法，实现散列表
 */
class HashTable {
    table: any[] = [];

    loseloseHashCode(key: string) {
        let hash = 0;
        for (let i = 0; i < key.length; i++) {
            hash += key.charCodeAt(i);
        }
        return hash % 37;
    }

    hashCode(key: string) {
        return this.loseloseHashCode(key);
    }

    put(key: string, value: any) {
        let position = this.hashCode(key);
        if (this.table[position] === undefined) {
            this.table[position] = new ValuePair(key, value);
        } else {
            let index = ++position;
            while (this.table[index] !== undefined) {
                index++;
            }
            this.table[index] = new ValuePair(key, value);
        }
    }

    get(key: string) {
        let position = this.hashCode(key);
        if (this.table[position] !== undefined) {
            if (this.table[position].key === key) {
                return this.table[position].value;
            } else {
                let index = ++position;
                while (this.table[index] === undefined || this.table[index].key !== key) {
                    index++;
                }
                if (this.table[index].key === key) {
                    return this.table[index].value;
                }
            }
        }
        return undefined;
    }

    remove(key: string) {
        let position = this.hashCode(key);
        if (this.table[position] !== undefined) {
            if (this.table[position].key === key) {
                this.table[position] = undefined;
            } else {
                let index = ++position;
                while (this.table[index] === undefined || this.table[index].key !== key) {
                    index++;
                }
                if (this.table[index].key === key) {
                    this.table[index] = undefined;
                }
            }
        }
        return undefined;
    }
}

class ValuePair {
    key: string;
    value: any;
    constructor(key: string, value: any) {
        this.key = key;
        this.value = value;
    }
    toString() {
        return '[' + this.key + ' - ' + this.value + ']';
    }
}

// test case
let hash = new HashTable();
hash.put('Gandalf', 'Foo')
hash.put('John', 'Bar')
hash.put('Tyrion', 'Baz')
hash.put('Aaron', 'Bax')
hash.put('Donnie', 'Qux')
hash.put('Ana', 'Quux')
hash.put('Jonathan', 'Quuz')
hash.put('Jamie', 'Corge')
hash.put('Sue', 'Grault')
hash.put('Mindy', 'Garply')
hash.put('Paul', 'Waldo')
hash.put('Patrick', 'Fred')
hash.put('Peter', 'Plugh')
hash.put('Bill', 'Thud')

console.log(hash.get('Ana')) // Quux
console.log(hash.get('Gandalf')) // Foo
console.log(hash.get('Loiane')) // undefined

hash.remove('Gandalf')

console.log(hash.get('Gandalf')) // undefined
```

# Ref

[图解！24张图彻底弄懂九大常见数据结构！ - 腾讯云开发者社区-腾讯云](https://cloud.tencent.com/developer/article/1634155)