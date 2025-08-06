# Standard Template library
- It collection of templated function templated class.

**Components**
1. Container
2. Algorithms → Functions
3. Iterator → Smart Pointer

## Container
- It's a variable/object of templated lcass.
- Implemented using template.
- Storing the data.
- The way of Represention.

### 3 - Type of Containers
- Sequence Container
    - Vector
    - List
    - Deque
- Associative Container
    - Set
    - Multiset
    - Map
    - Multimap
- Derived Container
    - Stack
    - Queue

## Vector

- A `vector` is a dynamic array that can grow or shrink in size as needed. It stores elements in contiguous memory, allowing for fast random access.

- It is a templated class.
- It is having only one end.
- Insertion/Deletion of data if faster at slower at first/middle.
- It supports `indexing`.
- Randomly can access data.
- It is dynamic array
    - Automatic memory created while storing the dynamic memory de-allocated automatically while deleting the data.

- Header: ```#include <vector>```

- Key Operations:

  - `push_back()`: Adds an element to the end of the vector.

  - `pop_back()`: Removes the last element from the vector.

  - `size()`: Returns the number of elements in the vector.

  - `at()`: Accesses an element at a specific index with bounds checking.

  - `[]` (Subscript Operator): Accesses an element at a specific index without bounds checking (faster).


- The provided program demonstrates various vector operations:

  - Initialization: A vector named v is created.

  - push_back(): A for loop adds five integer elements to the vector.

  - size(): The program prints the current number of elements.

  - Iteration: The program uses a for loop with the v.at(i) function to print each element.

  - pop_back(): The pop_back() function is called, which removes the last element (50) from the vector.

  - front() and back(): These member functions access the first and last elements of the vector respectively.

  - insert(): The v.insert(v.begin()+2, 25) statement inserts the value 25 at the third position in the vector.

  - erase(): The v.erase(v.begin()+4) statement removes the element at the fifth position.



### Case 1 

```c++
#include<iostream>
#include<vector>
using namespace std;
int main() 
{  
   vector<int> v1;
   cout << v1.size() << endl;
   v1.push_back(10);
   v1.push_back(5);
    v1.push_back(40);
   v1.push_back(57);
    v1.push_back(20);
   v1.push_back(34);
    v1.push_back(54);
   v1.push_back(53);
 
   for(int i=0;i<v1.size();i++)
   cout << v1[i] << endl;
}
```

### Case 2

```c++
#include<iostream>
#include<vector>
using namespace std;
int main() 
{  
  vector<int>v1(5); // 5 ele created
  cout << "No.of ele: " << v1.size() << endl;
  v1.push_back(20);
  v1.push_back(45);
  v1.insert(v1.begin(),89);
  v1.insert(v1.begin()+3,50);
  v1.insert(v1.end(),43);
  v1.insert(v1.end()-3,23);
  
  vector<int>::iterator it;
  for(it=v1.begin();it!=v1.end();it++)
   cout << *it << endl;
}
```

### Case 3

```c++
#include<iostream>
#include<vector>
using namespace std;
int main() 
{  
  vector<int>v1(5,40); // all 5 eles iniiialized with 40
  cout << "No.of ele: " << v1.size() << endl;
  v1.push_back(20);
  v1.push_back(45);
  v1.insert(v1.begin(),89);
  v1.insert(v1.begin()+3,50);
  v1.insert(v1.end(),43);
  v1.insert(v1.end()-3,23);
  
  ////////// method-1 
  vector<int>::iterator it;
  for(it=v1.begin();it!=v1.end();it++)
   cout << *it << endl;
  //////////// method-2
  for(int i=0;i<v1.size();i++)
  cout << v1[i] << endl;
  
  ///////// method-3 advanced
  for(auto i:v1)
  cout << i << endl;
}
```

### Case 4

```c++
#include<iostream>
#include<vector>
using namespace std;
int main() 
{  
  vector<int>v1(5,40); // all 5 eles iniiialized with 40
  cout << "No.of ele: " << v1.size() << endl;
  v1.push_back(20);
  v1.push_back(45);
  v1.insert(v1.begin(),89);
  v1.insert(v1.begin()+3,50);
  v1.insert(v1.end(),43);
  v1.insert(v1.end()-3,23);
  
#if 0
  ////////// method-1 
  vector<int>::iterator it;
  for(it=v1.begin();it!=v1.end();it++){
    *it=*it+100;
   cout << *it << endl;
  }
  vector<int>::const_iterator it2;
  for(it2=v1.begin();it2!=v1.end();it2++){
    *it2=*it2+100;
   cout << *it2 << endl;
  }
#endif
  vector<int>::reverse_iterator it3;
  for(it3=v1.rbegin();it3!=v1.rend();it3++){
   cout << *it3 << endl;
  }
}
```

### Case 5

```c++
#include<iostream>
#include<vector>
using namespace std;
int main() 
{  
  vector<int>v1(5,40); // all 5 eles iniiialized with 40
  cout << "No.of ele: " << v1.size() << endl;
  v1.push_back(20);
  v1.push_back(45);
  v1.insert(v1.begin(),89);
  v1.insert(v1.begin()+3,50);
  v1.insert(v1.end(),43);
  v1.insert(v1.end()-3,23);
  
 // v1.clear(); // clear the ele
 // v1.pop_back(); //delete last ele 
   // v1.erase(v1.begin()); // first ele
   // v1.erase(v1.begin()+5); // 6th  ele
   // v1.erase(v1.end()); //  invalid
    //v1.erase(v1.end()-1); // last ele
   //v1.erase(v1.end()-3); // 3rd ele from last
   v1.erase(v1.begin()+3,v1.end()-3); // last ele
 
   
  vector<int>::iterator it;
  for(it=v1.begin();it!=v1.end();it++){
      cout << *it << endl;
  }
}
```

## List

- A list is a doubly linked list that allows for constant-time insertion and deletion of elements at any position. However, it does not support fast random access.

- Header: ```#include <list>```

- Key Operations:

  - push_front(): Adds an element to the beginning of the list.

  - push_back(): Adds an element to the end.

  - pop_front(): Removes the first element.

  - pop_back(): Removes the last element.

  - sort(): Sorts the elements in the list.

  - reverse(): Reverses the order of elements.

- Program Analysis
  - The program for list showcases its key features:

- Initialization: An empty list called l1 is created.

  - push_back() and push_front(): Elements are added to both the front and back of the list.

  - begin() and end(): An iterator it is used to traverse the list from the beginning to the end. The program uses *it to print the value at each position.

  - pop_back() and pop_front(): The first and last elements are removed.

  - sort(): The l1.sort() function sorts the remaining elements in ascending order.

  - reverse(): The l1.reverse() function reverses the sorted list.

  - remove(): The l1.remove(30) function removes all occurrences of the value 30 from the list.

```c++
#include<iostream>
#include<list>
using namespace std;
struct st
{
 int rollno;
 char name[20];
 float marks;
 st(){
      cin >> rollno >> name >> marks;
 }
};
int main() 
{  
   list<struct st> v1;
    struct st s1,s2,s3,s4,s5;
   list<struct st>::iterator it;
   v1.push_back(s1);
   v1.push_back(s2);
   v1.push_back(s3);
   it=v1.end();
   advance(it,-2);
   v1.insert(it,s5);
   v1.push_back(s4);
   
  for(it=v1.begin();it!=v1.end();it++){
      cout << it->rollno << " "<< it->name <<" " << it->marks <<  endl;
  }
}
```

## Deque

### Case 1

```c++
#include<iostream>
#include<deque>
using namespace std;
int main() 
{  
  deque<int>v1(5,40); // all 5 eles iniiialized with 40
  cout << "No.of ele: " << v1.size() << endl;
  v1.push_back(20);
  v1.push_back(45);
  v1.insert(v1.begin(),89);
  v1.insert(v1.begin()+3,50);
  v1.insert(v1.end(),43);
  v1.insert(v1.end()-3,23);
  
 // v1.clear(); // clear the ele
 // v1.pop_back(); //delete last ele 
   // v1.erase(v1.begin()); // first ele
   // v1.erase(v1.begin()+5); // 6th  ele
   // v1.erase(v1.end()); //  invalid
    //v1.erase(v1.end()-1); // last ele
   //v1.erase(v1.end()-3); // 3rd ele from last
   v1.erase(v1.begin()+3,v1.end()-3); // last ele
   v1.push_front(200);
   v1.pop_front();
   
  deque<int>::iterator it;
  for(it=v1.begin();it!=v1.end();it++){
      cout << *it << endl;
  }
}
```

### Case 2

```c++
#include<iostream>
#include<deque>
using namespace std;
struct st
{
 int rollno;
 char name[20];
 float marks;
};
int main() 
{  
   deque<struct st> v1;
    struct st s1,s2;
    cin >> s1.rollno >> s1.name >> s1.marks;
    cin >> s2.rollno >> s2.name >> s2.marks;
   
   v1.push_back(s1);
   v1.push_back(s2);
  deque<struct st>::iterator it;
  for(it=v1.begin();it!=v1.end();it++){
      cout << (*it).rollno << " "<< (*it).name <<" " << (*it).marks <<  endl;
      cout << it->rollno << " "<< it->name <<" " << it->marks <<  endl;
  }
}
```


## Set
- Set is collection or unique element. (duplicate not allowed)

### Case 1

```c++
#include<iostream>
#include<set>
using namespace std;
int main() 
{  
  set<int>v1;
  v1.insert(10);
  v1.insert(23);
  v1.insert(13);
  v1.insert(3);
  v1.insert(23);
  v1.insert(10);
  v1.insert(5);
  
  set<int>::iterator it;
  for(it=v1.begin();it!=v1.end();it++)
  cout << *it << endl;
}
```

### Case 2

```c++
#include<iostream>
#include<set>
using namespace std;
int main() 
{  
  set<int,greater<int> >v1;
  v1.insert(10);
  v1.insert(23);
  v1.insert(13);
  v1.insert(3);
  v1.insert(23);
  v1.insert(10);
  v1.insert(5);
  
  set<int>::iterator it;
  for(it=v1.begin();it!=v1.end();it++)
  cout << *it << endl;
}
```


## Multiset
- Collection of element. (duplicate all)

### Case 1

```c++
#include<iostream>
#include<set>
using namespace std;
int main() 
{  
  multiset<int>v1;
  v1.insert(10);
  v1.insert(23);
  v1.insert(13);
  v1.insert(3);
  v1.insert(23);
  v1.insert(10);
  v1.insert(5);
  
  set<int>::iterator it;
  for(it=v1.begin();it!=v1.end();it++)
  cout << *it << endl;
}
```

## Map
- It is collection of key & value relation pair (duplicate key not allowed)
- A map is an associative container that stores elements in a sorted key-value pair. Each key must be unique, and it provides very fast access to its elements.

```c++
#include<iostream>
#include<map>
using namespace std;
int main() 
{  
    multimap<string,string> m1;
    m1.insert(pair<string,string>("Num","10"));
    m1.insert(pair<string,string>("age","30"));
    m1.insert(pair<string,string>("name","c++"));
    m1.insert(pair<string,string>("city","Banaglore"));
    m1.insert(pair<string,string>("Num","30"));
    m1.insert(pair<string,string>("age","40"));        

   map<string,string>::iterator it;
   for(it=m1.begin();it!=m1.end();it++)
   cout << it->first << " " << it->second << endl;
}
```

## Multimap
- Duplicate key allowed.

