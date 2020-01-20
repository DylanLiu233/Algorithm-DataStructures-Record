## Algorithm & Data Structures Record

###  Elmentery Sorting

- Insertion Sort

  ```c++
  //In asceding order, written in C++
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
  //In asceding order, written in C++
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
  //In asceding order, written in C++
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
  //In asceding order, written in C++
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
- 