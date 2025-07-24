# Static 
>[!Note]  
> - In **C++** `static` is only allowed inside class.
> - Memory allocated in `data` section.
> - Default value is `zero`.

```c++
#include<iostream>
using namespace std;
class A
{
  int x,y;
  static int c;
};
```
```c++
int main() 
{  
  A obj;
  
  cout << sizeof(obj) << endl;
  cout << sizeof(A) << endl;
}
```

**Output**
- sizeof(obj) is `8`.
- sizeof(A) is `8`.

But there are 3 `int` member. `static` `int` `c`  is allocated memory in `data` section.
```sh
8
8
```

## Case : If only static data member, then what will be the size.

```c++
#include<iostream>
using namespace std;
class A
{
  static int c;
};
int main() 
{  
  A obj;
 
  cout << sizeof(obj) << endl;
  cout << sizeof(A) << endl;
}
```

**Output**

```sh
1
1
```

- **1 byte** memory, so the varible can exist.
- The size of a **class/object** depend only on **non-static** member of a class.*(static member should not be considered.)*
- `static` member belong to **class**.

>[!Note]  
> - To access `static` member **object** is `not` **mandatory**.

- To access static member we can use

```c++
classname :: variablename
```
```c++
class A {
    static int c ;
};

int A :: c;
```

**Example**

```c++
#include<iostream>
 using namespace std;
 class Handbook
 {
   string name,mbl;
   public:
```
**Declaration** 
-  Here ,`c` works as a global variable for `class A`.
```c++
   static int c; /*declaration*/
   	Handbook(){
   	 cout << "enter name and mobile num" << endl;
   	 cin >> name >> mbl;
   	 c++;
   	 cout << "user account created" << endl;
   	}
   	~Handbook(){
   	 c--;
   	 cout << "user account deleted " << endl;
   	}
};
```
**Defination**
```c++
int Handbook::c; 
```
```c++
int main() 
{  
  Handbook h1,h2,h3;
  {
   Handbook h4,h5;
```
Using class name.
```c++
   cout << " Total count: " << Handbook::c << endl; 
```
Using class object.
```c++
  }
  cout << " Total count: " << h2.c << endl; 
}
```

**Output**

```sh
enter name and mobile num
ravi 8989
user account created
```
```sh
enter name and mobile num
sahil 8923
user account created
```
```sh
enter name and mobile num
bushan 9897
user account created
```
```sh
enter name and mobile num
shiva 7800
user account created
```
```sh
enter name and mobile num
tomar 7999
user account created
```
```sh
 Total count: 5
```
```sh
user account deleted
user account deleted
```
```sh
 Total count: 3
```
```sh
user account deleted
user account deleted
user account deleted
```


# Singleton Class
- A class having only `1` **object**.

```c++
#include<iostream>
using namespace std;
class A
{
  int x,y;
  
  	A(){
  	cout << "constructor " << endl;
  	}
  	~A(){
  	 cout << "Destructor  "<< endl;
  	}
  	public:
```
should be `static`
```c++
    static void create_object(){
	  A obj;
	}
};
```
```c++
int main() 
{  
  A::create_object();
}
```

## Static function can only access static members

### Example with singleton class

```c++
#include<iostream>
using namespace std;
class A
{
  int x,y;
  static int c;
  public:
  	A(){
  	 cout << "constructor  "<<endl;
  	 x=10,y=20;
  	}
  	~A(){
  	 cout << "destructor  "<<endl;
  	}
    static void get_data(){
```
- `static` member function **can't** access other member which are not `static`
```c++
    cout << x << " " << y << endl; /*invalid*/
```
```c++
    cout << "c value: " << c << endl;
    }
};
int A::c=1000;
int main() 
{  
   A obj1;
   obj1.get_data();
```
**Or**
```c++
  A::get_data();  
}
```

**Output**
- Comment line  `cout << x << " " << y << endl;` or remove
```sh
constructor
c value: 1000
destructor
```

## Explanation of the Singleton Pattern Implementation
- This C++ program demonstrates the Singleton design pattern
- Which ensures a class has only one instance and provides a global point of access to it.

**Class**
```c++
class Singleton {
    int x;  // Private data member
    
    // Private static pointer to hold the single instance
    static Singleton* single;  // Declaration
    
    // Private constructor
    Singleton() {
        cout << "Constructor " << endl;
    }
    
    // Private destructor
    ~Singleton() {
        cout << "Destructor " << endl;
    }
    
public:
    // Static method to create/access the single instance
    static Singleton* create_object() {
        if(single == nullptr)
            single = new Singleton;  // Create instance if none exists
        return single;
    }
    
    // Static method to destroy the instance
    static void destory_object() {
        if(single != nullptr) {
            delete single;
            single = nullptr;
        }
    }
};

// Definition of the static member variable
Singleton* Singleton::single = nullptr;
```
**main()**
```c++
int main() {  
    Singleton *ptr1; 
    ptr1 = Singleton::create_object();  // Creates instance
    ptr1 = Singleton::create_object();  // Returns existing instance
    ptr1 = Singleton::create_object();  // Returns existing instance
    
    Singleton::destory_object();  // Destroys instance
    Singleton::destory_object();  // Does nothing (already destroyed)
    Singleton::destory_object();  // Does nothing (already destroyed)
}
```

**Output**

```sh
Constructor 
Destructor
```