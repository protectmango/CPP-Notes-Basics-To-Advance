# Pure Virtual Function

- A virutal function that is declared but not defined in a base class is referred to as a pure **virtual function**.

```c++
virtual <return type> <function name> (arg) = 0;
```

## Abstract Class

- If a class contain at least one pure virtual function is called as **abstract class**.

- If a virtual function declared as **pure**, it must be redefined in each derived class else compilation of the program is unsuccessful.

>[!Note]  
>A class having pure virtual function  cannot be used to instantiate object of its own.

```c++
#include<iostream>
using namespace std;
class RBI // Abstract class
{
public:
	virtual void min_bal()=0; // pure virtual 
	
};
class SBI:public RBI
{
public:
	void min_bal(){
	cout << "min bal SBI 5000 "<< endl;
	}
};
class Axis:public RBI
{
	void min_bal(){
	cout << "min bal Axis 7000" << endl;
	}
	void minimum_bal(){
	cout << "min bal SBI 5000 "<< endl;
	}
};

int main() 
{
 //RBI r; // invalid ,abstrcat type
  RBI *ptr;  
  SBI s; 
 
  Axis a;
  ptr=&a;
  ptr->min_bal();
}
```
**Output**

```sh
min bal Axis 7000
```

## Virtual Destructor

- only Base class should have virtual destructor.

```c++
#include<iostream>
using namespace std;
class A
{
  char *s1;
  public:
  	A(){
  	s1=new char[20];
  	cout << "constructor A"<< endl;
  	}
	virtual ~A(){
	delete []s1;
	cout << "Destructor A" << endl;
	}
};

class B:public A
{
  char *s2;
  public:
  	B(){
  	s2=new char[20];
  	cout << "constructor B"<< endl;
  	}
	~B(){
	delete []s2;
	cout << "Destructor B" << endl;
	}
};

class C:public B
{
  char *s3;
  public:
  	C(){
  	s3=new char[20];
  	cout << "constructor C"<< endl;
  	}
	~C(){
	delete []s3;
	cout << "Destructor C" << endl;
	}
};
```
### Case 1
```c++
int main() 
{  
   C obj;
}
```
**Output**

```sh
constructor A
constructor B
constructor C
Destructor C
Destructor B
Destructor A
```

### Case 2
```c++
int main(){
  C *ptr;
  ptr=new C;
}
```
**Output**
```sh
constructor A
constructor B
constructor C
```

### Case 3
```c++
int main(){
  C *ptr;
  ptr=new C;
  delete ptr;
}
```
**Output**

```sh
constructor A
constructor B
constructor C
Destructor C
Destructor B
Destructor A
```


### Case 4
```c++
int main(){
  A *ptr;
  ptr=new C;
}
```

**Output**

```sh
constructor A
constructor B
constructor C
```

### Case 5
```c++
int main(){
  A *ptr;
  ptr=new C;
  delete ptr;
}
```
**Output**

```sh
constructor A
constructor B
constructor C
Destructor C
Destructor B
Destructor A
```

### Case 6
```c++
int main(){  // in class A, If destructor is virtual
  A *ptr;
  ptr=new C;
  delete ptr;
}
```
**Output**
```sh
constructor A
constructor B
constructor C
Destructor C
Destructor B
Destructor A
```

## Virtual Pure Base

```c++
#include<iostream>
using namespace std;
class Base
{
  public:
  	virtual void test(){
  	cout << "test func Base "<< endl;
  	}
};
class Derived:public Base
{
int x,y;
   void test(){
		cout << "test func Derived" << endl;   
    cin >>x >>y;
   }
};
```
### Case 1
```c++
int main(){
  Base *ptr;
  Derived d;
  ptr=&d;
  ptr->test();
}
```
**Output**

```c++
test func Derived
10 20
```

### Case 2
```c++
int main() 
{  
   Derived d;
   d.test();
}
```

**Error**

```c++
vpub.cpp:34:6: error: 'test' is a private member of 'Derived'
   34 |    d.test();
      |      ^
vpub.cpp:13:9: note: implicitly declared private here
   13 |    void test(){
      |         ^
1 error generated.
```