##### 源码分析


+ get
  ```
  linkedList查找速度相对于arrayList是慢些，linkedList又是如何提高其查找速度的呢？
  通过源码发现， get(int) 是做了一些技巧在里面，linkedList的node节点有 prev,next属性，所以其内部是一个
  双向链表，基于此linkedList可以双向查找，get恰好利用了这个双向查找的特性，从最近的一端查询，提高查询速度.
      Node<E> node(int index) {
          // assert isElementIndex(index);
  
          if (index < (size >> 1)) {
              Node<E> x = first;
              for (int i = 0; i < index; i++)
                  x = x.next;
              return x;
          } else {
              Node<E> x = last;
              for (int i = size - 1; i > index; i--)
                  x = x.prev;
              return x;
          }
      }
  ``` 
+ set
  ```
   改也是先根据index找到Node，然后替换值。改不修改modCount。   
  ``` 
   
   
   
    















