## Algorithm & Data Structures Record

###  Elmentery Sorting

- Insertion Sort

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

  

- Bubble Sort

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
  void InsertionSort(dataType arr[], int len)
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

  

- Selection Sort

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

  

- Shell Sort

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

  

### Stack

- Implement in C Language
- Implement with STL of C++ (__stack__)
- Expression conversion (__prefix, infix, suffix__)
- Expression evaluation

### Queue

- Implement in C Language
- Implement with STL of C++ (__queue__)
- Circular Queue

### Linked List

- Implement in C Language
- Implement with STL of C++ (__vector__)
- Double Linked List

### Searching

- Linear Search (__including mark__)

- Binary Search
- Dictionary

### Recursion, Divide and Conquer

- Exhaustive Search



### Advanced Sorting

- Merge Sort

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

  

- Quick Sort

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

  

- Counting Sort

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

  