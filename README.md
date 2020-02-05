## Algorithm & Data Structures Record

###  初等排序 Elmentery Sorting

- 插入排序 Insertion Sort

  ```c++
  //In ascending order, written in C++
  //Time complexity: O(n^2)
  void InsertionSort(dataType arr[], int len)
  {
      dataType key;
      
      for(int i = 1; i < len; i++) {
          key = arr[i];
          int j = i-1;
  		while (j >= 0 && key < arr[j]) {
              arr[j+1] = arr[j];
              j--;
          }
          arr[j+1] = key;
      }
  }
  ```

  

- 冒泡排序 Bubble Sort

  ```c++
  //In ascending order, written in C++
  //Time complexity: O(n^2)
  void swap(dataType *a, dataType *b)
  {
      dataType temp;
      
      temp = *a;
      *a = *b;
      *b = temp;
  }
  void BubbleSort(dataType arr[], int len)
  {
  	dataType key;
      bool flag = true;
  	
  	for (int i = 0; flag == true; i++) {
          flag = false;
          for (int j = 0; j < len-i-1; j++) {
              if (arr[j] > arr[j+1]) {
                  swap(&arr[j], &arr[j+1]);
                  flag = true;
              }
          }
      }
  }
  ```

  

- 选择排序 Selection Sort

  ```c++
  //In ascending order, written in C++
  //Time complexity: O(n^2)
  void SelectionSort(dataType arr[], int len)
  {
      for (int i = 0; i < len-1; i++) {
          int minIndex = i;
          
          for (int j = i+1; j < len; j++) {
              if (arr[j] < arr[minIndex]) {
                  minIndex = j;
              }
          } 
          //the definition of function 'swap()' is in BubbleSort
          swap(&arr[i], &arr[minIndex]);
      }
  }
  ```

  

- 希尔排序 Shell Sort

  ```c++
  //In ascending order, written in C++
  //Time complexity: O(n^1.25)
  void InsertionSort(dataType arr[], int len, int interval)
  {
      dataType key;
      
      for (int i = interval; i < len; i++) {
          key = arr[i];
          int j = i - interval;
          while (arr[j] > key && j >= 0) {
              arr[j+interval] = arr[j];
              j = j - interval;
          }
          arr[j+interval] = key;
      }
  }
  void ShellSort(dataType arr[], int len)
  {
      //generate the array of interval 'G={1, 4, 13, 40, 121, ...}'
      //this part is the most important
      //one of the recursive formula is: G[n+1] = 3*G[n] + 1
      //not the only one
      int cnt = 0;
      for (int g = 1; ; ) {
          if (g > len) {
              break;
          }
          G[cnt] = g;
          g = 3*G[cnt] + 1;
      }
      
      for (int i = len-1; i >= 0; i--) {
          InsertionSort(arr, len, G[i]);
      }
  }
  ```

  

### 栈 Stack

- C语言实现栈 Implement in C Language
- C++标准模板库中的栈 Implement with STL of C++ (__stack__)
- 表达式的转换 Expression conversion (__prefix, infix, suffix__)
- 表达式求值 Expression evaluation

### 队列 Queue

- C语言实现队列 Implement in C Language
- C++标准模板库中的队列 Implement with STL of C++ (__queue__)
- 循环队列 Circular Queue

### 链表 Linked List

- C语言实现链表 Implement in C Language
- C++标准模板库中的链表 Implement with STL of C++ (__vector__)
- 双向循环链表 Double Linked List

### 搜索 Searching

- 线性搜索 Linear Search (__including mark__)

- 二分搜索 Binary Search
- 散列表 Dictionary

### 递归与分治法 Recursion, Divide and Conquer

- 穷举搜索 Exhaustive Search



### 高等排序 Advanced Sorting

- 归并排序 Merge Sort

  ```c++
  //In ascending order, witten in C++
  //Time Complexity: O(nlogn)
  #define INF 99999999 //a flag
  void merge(dataType arr[], int left, int mid, int right)
  {
      int n1 = mid - left;
      int n2 = right - mid;
      int L[n1+1];
      int R[n2+1];
      
      //set the boundary
      L[n1] = R[n2] = INF;
      for (int i = 0; i < n1; i++) {
          //attention: not 'arr[i]'
          L[i] = arr[left+i];
      }
      for (int i = 0; i < n2; i++) {
          //attention: not 'arr[i]'
          R[i] = arr[mid+i];
      }
      
      int i = 0;
      int j = 0;
      //attention: not 'int k = 0'
      for (int k = left; k < right; k++) {
          if (L[i] <= R[j]) {
              arr[k] = L[i];
              i++;
          }
          else {
              arr[k] = R[j];
              j++;
          }
      }
  }
  void MergeSort(dataType arr[], int left, int right)
  {
      //two elements left at least
      if (left+1 < right) {
          int mid = (left+right)/2;
          MergeSort(arr, left, mid);
          MergeSort(arr, mid, right);
          merge(arr, left, mid, right);
      }
  }
  ```

  

- 快速排序 Quick Sort

  ```c++
  //In ascending order, written in C++
  //Time complexity: O(nlogn)
  void swap(dataType *a, dataType *b)
  {
      dataType temp;
      
      temp = *a;
      *a = *b;
      *b = temp;
  }
  int Partition(dataType arr, int start, int end)
  {
      //choose the last one to be the pivot
      int pivotValue = arr[end];
      int i = start-1;	//the rear index of smaller part
      
      for (int j = 0; j < end; j++) {
          if (arr[j] <= pivotValue) {
              i++;
              swap(&arr[j], &arr[i]);
          }
      }
      //place the pivot element between smaller part and bigger part
      swap(&arr[i+1], &arr[end]);
      
      return i+1;		//return the index of pivot
  }
  void QuickSort(dataType arr[], int start, int end)
  {
      if (start < end) {
          int pivotIndex = Partition(arr, start, end);
          QuickSort(arr, start, pivotIndex-1);
          QuickSort(arr, pivotIndex+1, end);
      }
  }
  ```

  

- 计数排序 Counting Sort

  ```c++
  //In ascending order, written C++
  //Time complexity: O()
  void CountingSort(int A[], int B[], int len, int maxNum)
  {
      //A[] is the array of original data (1 <= index <= len-1)
      //B[] is the array of sorted data (1 <= index <= maxNum)
      //Attention: A[0], B[0] were not used
      
      int C[maxNum+1];	// (0 <= index <= maxNum)
      
      //Initialize C[]
      for (int i = 0; i <= maxNum; i++) {
          C[i] = 0;
      }
      
      //Count 0~maxNum
      for (int i = 1; i <= len-1; i++) {
          C[A[i]]++;
      }
      
      for (int i = 1; i <= maxNum; i++) {
          C[i] = C[i] + C[i-1];
      }
      
      //The reason why iterate from len-1 to 1 is to 
      //make sure the algorithm is stable.
      for (int i = len-1; i >= 1; i--) {
          B[C[A[i]]] = A[i];
          C[A[i]]--;
      }
  }
  ```

  

### 树 Tree

- 有根树的表示（左孩子-右兄弟表示法）Rooted Tree (**Left-Child Right-Sibling Respresentation**)

  ```c++
  //左孩子-右兄弟表示法的结点结构：
  typedef struct {
      dataType parent;
      dataType leftChild;
      dataType sibling;
} Node;
  如果采用数组存储，那么dataType就是int类型，表示结点在数组中的下标。
  如果采用链式存储，那么dataType是结点的指针类型，用于保存结点的地址。
  parent指向该结点的父结点，leftChild指向该结点最左边的子结点，
  sibling指向该结点右边第一个兄弟结点。
  若无则用NULL或NIL表示。
  ```
  
  ```c++
  //树的创建
  一般来说，倘若使用数组存储一棵树，创建树时一般要使用以下格式:
  结点编号id 子结点数目k 子结点列表c1,c2, ... ,ck
  ...
  结点编号id 子结点数目k 子结点列表c1,c2, ... ,ck
  
  创建树(数组存储)的步骤：
  1、读取结点个数信息，初始化树的每一个结点，将parent, leftChild, sibling置为NIL。
  2、读取每一个结点的信息，对于每一个结点，更新Tree[id].leftChild = c1，
  	接着更新Tree[c1...ck].parent = id，同时更新Tree[c1].sibling = c2,
  	Tree[c2].sibling = c3, ... , Tree[ck-1].sibling = ck以此类推
  3、最后，遍历数组，parent == NIL的结点就是根结点
  ```
  
  ```c++
  //结点的深度（从根到结点的层数）
  考虑结点的结构就可以知道，只要使用结点的parent信息向上遍历直到根结点，
  就可以求得结点的深度。(根结点的高度定义为0)
      
  //结点的子结点列表
  首先获取结点的第一个子结点leftChild，接着从第一个子结点开始，遍历sibling，直到NIL，
  按照此顺序保存或输出就是子结点的列表。
  ```
  
  ```c++
  //written in C++
  #include <iostream>
  #define NIL -1
  #define MAXN 100000
  
  typedef struct {
      int parent;
      int leftChild;
      int sibling;
  } Node, Tree;
  
  void readTree(Tree T[], int n)
  {
      int id, k, c;
      int p = NIL;
      int left
      
      for (int i = 0; i < n; i++) {
          cin >> id >> k;
          for (int j = 0; j < k; j++) {
              cin >> c;
              
              int leftSibling;
              //最左边的那个结点
              if (j == 0) {
                  T[id].leftChild = c;
                  leftSibling = c;
              } else {	//更新左边结点的右兄弟c
                  T[leftSibling].sibling = c;
                  leftSibling = c;
              }
              //更新结点c的父结点
              T[c].parent = id;
          }
      }
  }
  
  void getDepth(Tree T[], int depth[], int n)
  {
      //注意：根结点的深度定义为0
      for (int i = 0; i < n; i++) {
          int id = i;
          int d = 0;
          while (T[id].parent != NIL) {
              cnt++;
              id = T[p].parent;
          }
          depth[i] = d;
      }
  }
  
  void printTree(Tree T[], int depth[], int n)
  {
      for (int i = 0; i < n; i++) {
          cout << "Node: " << i << ": ";
          cout << "parent = " << T[i].parent << ", ";
          cout << "depth = " << depth[i] << ", ";
          if (T[i].parent == NIL) {
              cout << "root";
          } else if (T[i].left == NIL) {
              cout << "leaf";
          } else {
              cout << "internal node";
          }
          
          cout << ", [";
          int id = T[i].leftChild;
          for (int j = 0; id != NIL; j++) {
              if (j > 0) {
                  cout << ", ";
              }
              cout << id;
              id = T[id].sibling;
          }
          cout << "]\n";
      }
  }
  
  int main(void)
  {
      int n;
      Tree T[MAXN];
      int depth[MAXN];
      
      cin >> n;
      for (int i = 0; i < n; i++) {
          T[i].parent = T[i].leftChild = T[i].sibling = NIL;
      }
  	readTree(T, n);
      getDepth(T, depth, n);
      printTree(T, depth, n);
  }
  
  /*
  输入样例：
  13
  0 3 1 4 10
  1 2 2 3
  2 0
  3 0
  4 3 5 6 7
  5 0
  6 0
  7 2 8 9
  8 0
  9 0
  10 2 11 12
  11 0
  12 0
  
  输出样例：
  node 0: parent = -1, depth = 0, root, [1, 4, 10]
  node 1: parent = 0, depth = 1, internal node, [2, 3]
  node 2: parent = 1, depth = 2, leaf, []
  node 3: parent = 1, depth = 2, leaf, []
  node 4: parent = 0, depth = 1, internal node, [5, 6, 7]
  node 5: parent = 4, depth = 2, leaf, []
  node 6: parent = 4, depth = 2, leaf, []
  node 7: parent = 4, depth = 2, internal node, [8, 9]
  node 8: parent = 7, depth = 3, leaf, []
  node 9: parent = 7, depth = 3, leaf, []
  node 10: parent = 0, depth = 1, internal node, [11, 12]
  node 11: parent = 10, depth = 2, leaf, []
  node 12: parent = 10, depth = 2, leaf, []
  
  */
  ```
  
  
  
- 二叉树的表示 Binary Tree

- 二叉树的遍历 

- 二叉树的重建 

### 二叉查找树 Binary Search Tree

- 二叉查找树的插入
- 二叉查找树的搜索
- 二叉查找树的删除
- map和set的使用

### 堆 Heap

- 完全二叉树
- 最大/小堆
- 优先级队列
- priority_queue

### 动态规划 Dynamic Programming

- 斐波那契数列求解 Finonacci Number
- 最长公共子序列 LCS(**Longest Common Subsequence**)

- 矩阵链乘法 

### 图 Graph

- 图的表示
- 深度优先搜索 DFS(**Depth First Search**)
- 广度优先搜索 BFS(**Breadth First Search**)
- 连通分量 Connected Components

### 加权图

- 最小生成树 MST(**Minimum Spanning Tree**)
- 单源最短路 Single Source Shortest Path

### 高级数据结构

- 并查集 Union-Find Set
- 范围搜索

### 高等图算法

- 所有点对间最短路径
- 拓扑排序
- 关节点（割点）
- 树的直径
- 最小生成树

### 计算几何学

- 

### 动态规划法

- 