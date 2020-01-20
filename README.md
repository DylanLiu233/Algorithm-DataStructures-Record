## Algorithm & Data Structures Record

###  Elmentery Sorting

- Insertion Sort

  ```c++
  //In asceding order, written in C++
  void InsertionSort(dataType arr[], int len)
  {
      dataType key;
      
      for(int i = 0; i < len; i++) {
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

- Shell Sort

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