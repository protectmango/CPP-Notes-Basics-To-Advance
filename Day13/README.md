# Deep Copy & Shallow Copy

|**Shallow Copy**|**Deep Copy**|
|---|---|
|- Copy one object data to another object with the help of **compiler** provided **copy constructor** or **assignment operator**.| - Copy one object data to another object with the help of **user** provided **copy constructor**.|
|- In shallow, both object are pointing to **same** memory location ,where the object holding pointer to dynamically allocated memory.|- In deep copy, both object are pointing to **different** memory location ,where the object holding pointer to dynamically allocated memory.|
|- If modify one object then it will effect to another object|- It won't effect another object at it has its own memory.|

## Shallow Copy

```c++
#include<iostream>
#include<cstring>
using namespace std;
```
```c++
class Shallow
{
  char *s;
```
We need to manually provide default constructor, as it will not be provided by the compiler as we have defined a parameterized constructor.
```c++
public:
  	Shallow(){}
```
This is a parameterized Constructor.
```c++
    Shallow(const char *p){
  	 s=new char[strlen(p)+1];
  	 strcpy(s,p);
  	}
	void get_string(){
	cout << s << endl;
	}
	void modify()
	{
	  s[0]='S';
	}
};
```
```c++
int main() 
{  
  Shallow s1("vector"),s2(s1);
  s1.get_string();
  s2.get_string();
  s1.modify();  
  s1.get_string();
  s2.get_string();
}
```

**Output**
```sh
vector
vector
Sector
Sector
```
>[!Note]   
>When copy constructor is called it work using reference, So it will copy the same address which is allocated to the first object.

## Deep Copy

```c++
#include<iostream>
#include<cstring>
using namespace std;
class Deep
{
  char *s;
  public:
  	Deep(){}
```
**Parameterized Constructor**
```c++
Deep(const char *p){
  	 s=new char[strlen(p)+1];
  	 strcpy(s,p);
  	}
```
**Copy Constructor** created by user.   
- To implement deep copy and allocated seperate memory.
```c++
Deep(Deep &t){
  	 s=new char[strlen(t.s)+1];
  	 strcpy(s,t.s);
  	}
	void get_string(){
	cout << s << endl;
	}
	void modify()
	{
	  s[0]='S';
	}
};
```
```c++
int main() 
{  
  Deep s1("vector"),s2(s1);
  s1.get_string();
  s2.get_string();
  s1.modify();  
  s1.get_string();
  s2.get_string();
}
```

# Destructor

- It is also a special member function.
- Automatically calls when object life completed.
- Main purpose is to destroy an object.
- De-initializing an object.
- Having same name as class name but prefix with `~` symbol.

- Destructor executed in **reverse** direction of constructor.
- if user not provided then compiler by default will provide destructor.

>[!Note]  
> **Constructor** & **Destructor** doesn't invoke for pointer.*(Only for objects)*

```c++
#include<iostream>
using namespace std;
class A
{
  public:
```
**Constructor**
```c++
    A(){
  	 cout << "constructor - "<< this  << endl;
  	}
```
**Destructor**
```c++
  	~A(){
  	 cout << "destructor - " << this << endl;
  	}
};
int main() 
{  
   A obj1,obj2,obj3; 
}
```

**Output**
```sh
constructor - 0x1000
constructor - 0x2000
constructor - 0x3000
```
```sh
destructor - 0x3000
destructor - 0x2000
destructor - 0x1000
```

|**Constructor**|**Destructor**|
|---|---|
|- It's creating an object.|- It's destroying an object.|
|- It's having same name as class name.|- It's having same name as class name but prefix with `~` symbol.|
|- Used for initilization purpose.|- Used for de-initialization.|
|- Constructor can't be virtual.|- Destructor can be virtual.|
|- Constructor does have arguments.|- Doesn't have arguments.|
|- Constructor can be overloaded.|- Destructor can't be overloaded.|
|- Constructor executed in forward direction.|- Destructor executed in reverse direction of constructor.|


## What are the member by default provided to a class by compiler ?

class A {

    1. Default Constructor.
    2. Copy Constructor.
    3. Assignment Operator Function.
    4. Destructor.
}

## Desturctor for DMA object

### Case 1

```c++
#include<iostream>
#include<cstring>
using namespace std;
class A
{
 char *s;
  public:
  	A(){
  	cout << "constructor " << endl;
  	s=new char[20];
  	strcpy(s,"hello");
  	}
  	~A(){
  	 cout << "destructor " << endl;
  	 delete [] s;
  	} 
};
int main() 
{  
   A obj1;   
}
```

**Output**
```sh
constructor
destructor
```

### Case 2

```c++
#include<iostream>
#include<cstring>
using namespace std;
class A
{
 char *s;
  public:
  	A(){
  	cout << "constructor " << endl;
  	s=new char[20];
  	strcpy(s,"hello");
  	}
  	~A(){
  	 cout << "destructor " << endl;
  	 delete [] s;
  	} 
};

int main(){
    A *ptr;
    ptr=new A;
    delete ptr; // object destroy ,so destructor will call
}
```
**Output**
```sh
constructor
destructor
```
