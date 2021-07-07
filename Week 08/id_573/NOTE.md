# NOTE

### 动态规划概念
````
动态规划(dynamic programming)是运筹学的一个分支，是求解决策过程(decision process)最优化的数学方法。20世纪50年代初美国数学家R.E.Bellman等人在研究多阶段决策过程(multistep decision process)的优化问题时，提出了著名的最优化原理(principle of optimality)，把多阶段过程转化为一系列单阶段问题，利用各阶段之间的关系，逐个求解，创立了解决这类过程优化问题的新方法——动态规划。
````
  
### 动态规划分类

```
动态规划一般可分为线性动规，区域动规，树形动规，背包动规四类。
举例：
    线性动规：拦截导弹，合唱队形，挖地雷，建学校，剑客决斗等；
    区域动规：石子合并， 加分二叉树，统计单词个数，炮兵布阵等；
    树形动规：贪吃的九头龙，二分查找树，聚会的欢乐，数字三角形等；
    背包问题：01背包问题，完全背包问题，分组背包问题，二维背包，装箱问题，挤牛奶（同济ACM第1132题）等；

应用实例：
    最短路径问题 ，项目管理，网络流优化等；
```


#### 动态规划问题实例

```
解决动态规划类问题，分为两步：1.确定状态，2.根据状态列状态转移方程
  确定该状态上可以执行的操作，然后是该状态和前一个状态或者前多个状态有什么关联，通常该状态下可执行的操作必定是关联到我们之前的几个状态。
  
1、数字三角形

2、背包问题两讲
  这里解决了两张背包问题，一个是确定最多可以装的下多少的背包盛放物品问题，还有一个是背包中放置的物品具有价值，要来确定其价值为多少。解决方法都是通过动态规划来解决。

3、公共子序列，公共子串问题
  公共子串
  给出两个字符串，找到最长公共子串，并返回其长度
  
  状态，字符串的每一位对应另一个字符串的每一个位置，因此通过一个二维数组来表示这每一个状态位，然后是找状态转移方程，转移方程即为其前一个位置的前一个的比对的结果累计当前的结果，如果相同则加1，否则为0

4、打劫房屋
  问题描述
  假设你是一个专业的窃贼，准备沿着一条街打劫房屋。每个房子都存放着特定金额的钱。你面临的唯一约束条件是：相邻的房子装着相互联系的防盗系统，且 当相邻的两个房子同一天被打劫时，该系统会自动报警。
  给定一个非负整数列表，表示每个房子中存放的钱， 算一算，如果今晚去打劫，你最多可以得到多少钱 在不触动报警装置的情况下。

5、编辑距离
  题目描述
  给出两个单词word1和word2，计算出将word1 转换为word2的最少操作次数。
  
  你总共三种操作方法：
  
  插入一个字符
  
  删除一个字符
  
  替换一个字符
  
  三种操作，因此我们在一个状态上面可以进行三种状态的变化，确定每一个状态，通过第二个字符串和第一个字符串的每一个位置的对应作为一个状态，处在该状态上，我们可以进行的操作，改，进行改操作，那么与之关联的前一个状态是其前一个字符对应另一个字符串的当前对应的前一个字符，增，则是说当前字符串的当前位对应到前一个字符串的前一个位置，删，则为当前字符串的当前位对应前一个字符串的前一个位置。为了增加一个增的位置，需要我们在其前面，所以我们在两个字符串的开始处设置一增加的位置。

6、N皇后问题
  n皇后问题是将n个皇后放置在n*n的棋盘上，皇后彼此之间不能相互攻击。
  给定一个整数n，返回所有不同的n皇后问题的解决方案。
  对于n皇后的问题，下一个皇后的布局位置将与之前的所有王后布局有关，因此通过动态规划，没安置一个皇后就作为一个状态，然后判断之前的已经安放的所有皇后的状态，确定是否可以按这一个皇后，通过递归的方式实现。

```

```
### Trie
Trie 树优于哈希表的另一个理由是，随着哈希表大小增加，会出现大量的冲突，时间复杂度可能增加到 O(n)O(n)，其中 nn 是插入的键的数量。与哈希表相比，Trie 树在存储多个具有相同前缀的键时可以使用较少的空间。此时 Trie 树只需要 O(m)O(m) 的时间复杂度，其中 mm 为键长。而在平衡树中查找键值需要 O(m \log n)O(mlogn) 时间复杂度。

### 作用
Trie (发音为 "try") 或前缀树是一种树数据结构，用于检索字符串数据集中的键。这一高效的数据结构有多种应用：
    
    1. 自动补全
    2. 拼写检查
    3. IP 路由 (最长前缀匹配)
    4. T9 (九宫格) 打字预测
    5. 单词游戏
    6. 还有其他的数据结构，如平衡树和哈希表，使我们能够在字符串数据集中搜索单词。为什么我们还需要 Trie 树呢？尽管哈希表可以在 O(1)O(1) 时间内寻找键值，却无法高效的完成以下操作：
        找到具有同一前缀的全部键值。
        按词典序枚举字符串的数据集。


### Trie 树的结点结构

    Trie 树是一个有根的树，其结点具有以下字段：
    
````
    1、最多 RR 个指向子结点的链接，其中每个链接对应字母表数据集中的一个字母。本文中假定 RR 为 26，小写拉丁字母的数量。
    2、布尔字段，以指定节点是对应键的结尾还是只是键前缀。
````
    
### Trie 树中最常见的两个操作是键的插入和查找。
    
    向 Trie 树中插入键
    我们通过搜索 Trie 树来插入一个键。我们从根开始搜索它对应于第一个键字符的链接。有两种情况：
    
    链接存在。沿着链接移动到树的下一个子层。算法继续搜索下一个键字符。
    链接不存在。创建一个新的节点，并将它与父节点的链接相连，该链接与当前的键字符相匹配。
    重复以上步骤，直到到达键的最后一个字符，然后将当前节点标记为结束节点，算法完成。
    
### 复杂度分析
  
    时间复杂度：O(m)O(m)，其中 mm 为键长。在算法的每次迭代中，我们要么检查要么创建一个节点，直到到达键尾。只需要 mm 次操作。
    空间复杂度：O(m)O(m)。最坏的情况下，新插入的键和 Trie 树中已有的键没有公共前缀。此时需要添加 mm 个结点，使用 O(m)O(m) 空间。
  
#### 在 Trie 树中查找键
    每个键在 trie 中表示为从根到内部节点或叶的路径。我们用第一个键字符从根开始，。检查当前节点中与键字符对应的链接。有两种情况：
  
    存在链接。我们移动到该链接后面路径中的下一个节点，并继续搜索下一个键字符。
    不存在链接。若已无键字符，且当前结点标记为 isEnd，则返回 true。否则有两种可能，均返回 false :
    还有键字符剩余，但无法跟随 Trie 树的键路径，找不到键。
    没有键字符剩余，但当前结点没有标记为 isEnd。也就是说，待查找键只是Trie树中另一个键的前缀。
  
#### 查找 Trie 树中的键前缀
    该方法与在 Trie 树中搜索键时使用的方法非常相似。我们从根遍历 Trie 树，直到键前缀中没有字符，或者无法用当前的键字符继续 Trie 中的路径。与上面提到的“搜索键”算法唯一的区别是，到达键前缀的末尾时，总是返回 true。我们不需要考虑当前 Trie 节点是否用 “isend” 标记，因为我们搜索的是键的前缀，而不是整个键。
  
  
### DFS\BFS

    DFS即深度优先搜索，俗称不撞南墙不回头，实现方式是用栈来保存选择，然后每次取栈顶元素，并且依据栈顶元素遍历，将符合条件的元素压栈，然后如此往复。

    BFS即广度优先搜索，特征是层次遍历，利用队列来实现。每次取队列队首元素，遍历所有节点，将所有符合条件的元素入队。循环往复。

    不管是DFS还是BFS，都需要一个状态标记来表示元素已经被选取，避免出现重复选择以及死循环。

    从上面的分析，我们可以知道DFS是很适合去做连通性搜索测试，并且如果不需要找到最短路径的话，可以直接退出，不需要存储大量路径信息（C语言也可以用递归来做）；而BFS则是很适合去搜索==最短路径==，因为其会进行层次遍历，在任何一层发现了目标，那都是最短的路径上发现的。但是BFS会要求记录每一层的信息，会导致信息记录量大。（而且C语言没有队列，需要额外实现）

    但是很明显，我们这道题就是需要用到BFS。也即根据beginWord来搜索所有与其相差仅为1个词语的单词，将其放入队列中，然后后循环搜索。不过要注意的是，存粹的BFS会超时，所以需要双端BFS，也就是从beginWord和endWord两端搜索。


### 双端BFS


依据名字，我们要从两端都搜索，也就需要两个队列来保存各自的搜索信息。我们记为begin_word_queue和end_word_queue，并且记为A和B。双端搜索的规则如下：

1、每次选取A和B中最少元素的来进行出队操作。如果size相等，取A中元素。

2、每次遍历到符合要求的元素，则进行入队操作，A搜索到的记为1， B搜索到的记为2。但是赋值方式为：
    
    
    int selected_flag; //0 means A; 1 means B
    int flag = 0;
    flag |= selected_flag;
    
3、当flag为3的时候代表A、B同时访问了一个节点，退出。

4、记录访问层次的次数，返回此次数。层次次数初始值为1
    
   
    
为什么这么做呢？因为BFS是层次遍历，也就是金字塔型遍历，越往后，搜索到的节点越多，信息越庞大，导致搜索时间越长。==但是结束点又只有一个，所以数据量大就会超时==。

### 算法分类

十种常见排序算法可以分为两大类：

    比较类排序：通过比较来决定元素间的相对次序，由于其时间复杂度不能突破O(nlogn)，因此也称为非线性时间比较类排序。
    非比较类排序：不通过比较来决定元素间的相对次序，它可以突破基于比较排序的时间下界，以线性时间运行，因此也称为线性时间非比较类排序。 
    
    
  #### 概念
  
    稳定：如果a原本在b前面，而a=b，排序之后a仍然在b的前面。
    不稳定：如果a原本在b的前面，而a=b，排序之后 a 可能会出现在 b 的后面。
    时间复杂度：对排序数据的总的操作次数。反映当n变化时，操作次数呈现什么规律。
    空间复杂度：是指算法在计算机
    内执行时所需存储空间的度量，它也是数据规模n的函数。
    
    
#### 1、冒泡排序（Bubble Sort）

    冒泡排序是一种简单的排序算法。它重复地走访过要排序的数列，一次比较两个元素，如果它们的顺序错误就把它们交换过来。走访数列的工作是重复地进行直到没有再需要交换，也就是说该数列已经排序完成。这个算法的名字由来是因为越小的元素会经由交换慢慢“浮”到数列的顶端。 

##### 1.1 算法描述

    比较相邻的元素。如果第一个比第二个大，就交换它们两个；
    对每一对相邻元素作同样的工作，从开始第一对到结尾的最后一对，这样在最后的元素应该会是最大的数；
    针对所有的元素重复以上的步骤，除了最后一个；
    重复步骤1~3，直到排序完成。

```
function bubbleSort(arr) {
    var len = arr.length;
    for (var i = 0; i < len - 1; i++) {
        for (var j = 0; j < len - 1 - i; j++) {
            if (arr[j] > arr[j+1]) {        // 相邻元素两两对比
                var temp = arr[j+1];        // 元素交换
                arr[j+1] = arr[j];
                arr[j] = temp;
            }
        }
    }
    return arr;
}
```

##### 2、选择排序（Selection Sort）
    选择排序(Selection-sort)是一种简单直观的排序算法。它的工作原理：首先在未排序序列中找到最小（大）元素，存放到排序序列的起始位置，然后，再从剩余未排序元素中继续寻找最小（大）元素，然后放到已排序序列的末尾。以此类推，直到所有元素均排序完毕。 

#####  算法描述

    n个记录的直接选择排序可经过n-1趟直接选择排序得到有序结果。具体算法描述如下：

    初始状态：无序区为R[1..n]，有序区为空；
    第i趟排序(i=1,2,3…n-1)开始时，当前有序区和无序区分别为R[1..i-1]和R(i..n）。该趟排序从当前无序区中-选出关键字最小的记录 R[k]，将它与无序区的第1个记录R交换，使R[1..i]和R[i+1..n)分别变为记录个数增加1个的新有序区和记录个数减少1个的新无序区；
    n-1趟结束，数组有序化了。
    

```
function selectionSort(arr) {
    var len = arr.length;
    var minIndex, temp;
    for (var i = 0; i < len - 1; i++) {
        minIndex = i;
        for (var j = i + 1; j < len; j++) {
            if (arr[j] < arr[minIndex]) {     // 寻找最小的数
                minIndex = j;                 // 将最小数的索引保存
            }
        }
        temp = arr[i];
        arr[i] = arr[minIndex];
        arr[minIndex] = temp;
    }
    return arr;
} 
```
##### 分析

````
表现最稳定的排序算法之一，因为无论什么数据进去都是O(n2)的时间复杂度，所以用到它的时候，数据规模越小越好。唯一的好处可能就是不占用额外的内存空间了吧。理论上讲，选择排序可能也是平时排序一般人想到的最多的排序方法了吧。
````


#### 寻找旋转排序数组中的最小值 

#### 思路：
    
    旋转排序数组 numsnums 可以被拆分为 2 个排序数组 nums1nums1 , nums2nums2 ，并且 nums1任一元素 >= nums2任一元素；因此，考虑二分法寻找此两数组的分界点 nums[i]nums[i] (即第 2 个数组的首个元素)。
    设置 leftleft, rightright 指针在 numsnums 数组两端，midmid 为每次二分的中点：
    当 nums[mid] > nums[right]时，midmid 一定在第 1 个排序数组中，ii 一定满足 mid < i <= right，因此执行 left = mid + 1；
    当 nums[mid] < nums[right] 时，midmid 一定在第 2 个排序数组中，ii 一定满足 left < i <= mid，因此执行 right = mid；
    当 nums[mid] == nums[right] 时，是此题对比 153题 的难点（原因是此题中数组的元素可重复，难以判断分界点 ii 指针区间）；
    例如 [1, 0, 1, 1, 1][1,0,1,1,1] 和 [1, 1, 1, 0, 1][1,1,1,0,1] ，在 left = 0, right = 4, mid = 2 时，无法判断 midmid 在哪个排序数组中。
    我们采用 right = right - 1 解决此问题，证明：
    此操作不会使数组越界：因为迭代条件保证了 right > left >= 0；
    此操作不会使最小值丢失：假设 nums[right]nums[right] 是最小值，有两种情况：
    若 nums[right]nums[right] 是唯一最小值：那就不可能满足判断条件 nums[mid] == nums[right]，因为 mid < right（left != right 且 mid = (left + right) // 2 向下取整）；
    若 nums[right]nums[right] 不是唯一最小值，由于 mid < right 而 nums[mid] == nums[right]，即还有最小值存在于 [left, right - 1][left,right−1] 区间，因此不会丢失最小值。
    
    以上是理论分析，可以代入以下数组辅助思考：
        [1, 2, 3][1,2,3]
        [1, 1, 0, 1][1,1,0,1]
        [1, 0, 1, 1, 1][1,0,1,1,1]
        [1, 1, 1, 1][1,1,1,1]
    时间复杂度 O(logN)O(logN)，在特例情况下会退化到 O(N)O(N)（例如 [1, 1, 1, 1][1,1,1,1]）。

  
    旋转排序数组nums可以被拆分为2个排序数组nums1, nums2，并且nums1中所有元素比nums2大（因为nums中没有重复值）；
    因此，考虑二分法寻找值nums[i]，满足nums[i] < nums[i-1] and nums[i] < nums[i+1]
    设置left, right指针在nums数组两端，mid为中点：
        当nums[mid] > nums[right]时，一定满足mid < i <= right，因此left = mid + 1；
        当nums[mid] < nums[right]时，一定满足left< i <= mid，因此right = mid；
        当nums[mid] == nums[right]时，说明数组长度len(num) == 1（因为计算mid向下取整）；当left = right也满足，但本题left == right时跳出循环。



