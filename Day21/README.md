# Inheritance 

Getting propertie from one class to another class old classes are called `Base`/`Parent` and new classes are called `Derived`/`child` 

**Syntax**

```c++
class Base
{
    /*Statement*/
}
class Derived : public / private / protected Base
{
    /*Statement*/
}
```

## Mode Of Inheritance (MOI)
1. Sizeof Base class depends only on Base class datamembers.
2. Sizeof Derived class depends on Base class datamember + Derived class data members.
3. Base class memeber functions/objects can access only base class members.
4. Derived class function/objects can access both base class member + Derived class member.
5. Base class all the members are inherited to derived class except private.
6. Base class privated member are not inherited to derived class.
7. MOI is applicable only for Base class member while inheriting to derived class.
8. By default, the MOI is private.
9. Eventhrough the Base class member are not inherited then also memory layout created for derived class object depends on base class + derived class data members.

## Case 1 : Sizeof Base and Derived Class

```c++
#include<iostream>
using namespace std;
class Base
{
  int x,y;
};
class Derived:public Base
{
 int m,n;
};
int main() 
{  
  cout << sizeof(Base) << endl;
  cout << sizeof(Derived) << endl;
}
```

**Output**

```sh
8
16
```

## Case 2 : Data memeber only in derived class

```c++
#include<iostream>
using namespace std;
class Base
{

};
class Derived:public Base
{
 int m,n;
};
int main() 
{  
  cout << sizeof(Base) << endl;
  cout << sizeof(Derived) << endl;
}
```

**Output**

```sh
1
8
```

## Case 3 : Data member only in base class

```c++
#include<iostream>
using namespace std;
class Base
{
 int x,y;
};
class Derived:public Base
{
 
};
int main() 
{  
  cout << sizeof(Base) << endl;
  cout << sizeof(Derived) << endl;
}
```

**Output**

```sh
8
8
```

## Case 4 : No Data members

```c++
#include<iostream>
using namespace std;
class Base
{
 
};
class Derived:public Base
{
 
};
int main() 
{  
  cout << sizeof(Base) << endl;
  cout << sizeof(Derived) << endl;
}
```


**Output**

```sh
1
1
```

## Case 5 : MOI is private by default

```c++
#include<iostream>
using namespace std;
class Base
{
 int x,y;

};
class Derived:Base       // MOI is private by default
{
 int m,n;
};
int main() 
{  
 
}
```

## Case 6 

- While inheritance MOI is applicable.
- MOI is public 
    - x is inherited as public.

```c++
#include<iostream>
using namespace std;
class Base
{
 public:
  int x;
};
class Derived:public Base
{
public:
 int y;

};
int main() 
{  
  Base b;
  Derived d;
  b.x=10;
  d.x=100;
  d.y=400;
  cout << d.x << " " << d.y << endl; 
}
```

## Case 7

```c++
#include<iostream>
using namespace std;
class Base
{
 public:
  int x;
};
class Derived:public Base
{
public:
 int x;

};
int main() 
{  
  Base b1,b2,b3;
  Derived d;
  b1.x=10;
  b2.x=100;
  b3.x=80;
  
  d.Base::x=100;
  d.x=400;
  cout << d.x << " " << d.Base::x << endl;
}
```

## Case 8

```c++
#include<iostream>
using namespace std;
class Base
{
 public: int x;
 protected:int y;
 private:int z
  public:
  	void set_base(){
  	 cin >> x >> y >> z;
  	}
  	void get_base(){
  	 cout << x << " " << y << " " << z << endl;
  	}
};
class Derived:public Base
{
  int m;
  public:
  	void set_derived(){
  	 cin >> m ;
  	 cin >> x;
  	 cin >> y;
  	 cin>>z;
  	 set_base();
  	}
  	void get_derived(){
  	 cout << m << endl;
  	}
};
int main() 
{  
   Base b;
 //  b.x=10;
 //  b.set_base();
  // b.y=20;
  // b.z=50;
   Derived d;
   d.Base::x=10;
   d.x=10;
   d.y=20;
   d.z=50;
    d.set_base();
    d.set_derived();
}
```

## Single Inheritance

### Case 1
```c++
#include<iostream>
using namespace std;
class Base
{
 public:
  int x;
};
class Derived:public Base
{
public:
 int y;
};
int main() 
{  
  Base b;
  Derived d;
  b.x=10;
  d.x=100;
  d.y=400;
  cout << d.x << " " << d.y << endl;
}
```

**Output**

```sh
100 400
```

### Case 2

```c++
#include<iostream>
using namespace std;
class Base
{
 public:
  int x;
};
class Derived:public Base
{
public:
 int x;

};
int main() 
{  
  Base b1,b2,b3;
  Derived d;
  b1.x=10;
  b2.x=100;
  b3.x=80;
  
  d.Base::x=100;
  d.x=400;
  cout << d.x << " " << d.Base::x << endl;
}
```
**Output**

```sh
400 100
```

### Case 3

```c++
#include<iostream>
using namespace std;
class Base
{
 public: int x;
 protected:int y;
 private:int z;
  public:
  	void set_base(){
  	 cin >> x >> y >> z;
  	}
  	void get_base(){
  	 cout << x << " " << y << " " << z << endl;
  	}
};
class Derived:private Base
{
  int m;
  public:
  	void set_derived(){
  	 cin >> m ;
  	 cin >> x;
  	 cin >> y;
  	 cin>>z;
  	 set_base();
  	}
  	void get_derived(){
  	 cout << m << endl;
  	}
};
int main() 
{  
  Base b;
  // b.x=10;
  // b.set_base();
  // b.y=20;
  // b.z=50;
  Derived d;
  d.x=10;
  d.y=20;
  d.z=50;
  d.set_base();
  d.set_derived();
}
```
**Error**

```sh
single3.cpp:24:10: error: 'z' is a private member of 'Base'
   24 |          cin>>z;
      |               ^
single3.cpp:7:14: note: declared private here
    7 |  private:int z;
      |              ^
single3.cpp:39:6: error: 'x' is a private member of 'Base'
   39 |    d.x=10;
      |      ^
single3.cpp:16:15: note: constrained by private inheritance here
   16 | class Derived:private Base
      |               ^~~~~~~~~~~~
single3.cpp:5:14: note: member is declared here
    5 |  public: int x;
      |              ^
single3.cpp:40:6: error: 'y' is a private member of 'Base'
   40 |    d.y=20;
      |      ^
single3.cpp:16:15: note: constrained by private inheritance here
   16 | class Derived:private Base
      |               ^~~~~~~~~~~~
single3.cpp:6:16: note: member is declared here
    6 |  protected:int y;
      |                ^
single3.cpp:41:6: error: 'z' is a private member of 'Base'
   41 |    d.z=50;
      |      ^
single3.cpp:7:14: note: declared private here
    7 |  private:int z;
      |              ^
single3.cpp:42:7: error: 'set_base' is a private member of 'Base'
   42 |     d.set_base();
      |       ^
single3.cpp:16:15: note: constrained by private inheritance here
   16 | class Derived:private Base
      |               ^~~~~~~~~~~~
single3.cpp:9:9: note: member is declared here
    9 |         void set_base(){
      |              ^
5 errors generated.
```

### Case 4

```c++
#include<iostream>
using namespace std;
class Base
{
  int x,y;
  public:
  	Base(){
  	 cout << "Base  constructor " << endl;
  	 x=10,y=20;
  	}
  	~Base()
  	{
  	 cout << "Base destructor " << endl;
  	}
};
class Derived:public Base
{
 int m,n;
 public:
 Derived(){
 cout << "Derived constructr " << endl;
  m=30,n=40;
 }
	~Derived(){
	cout << "Derived destructor" << endl;
	}
};
int main() 
{  
   Derived d; 
}
```

**Output**

```sh
Base  constructor
Derived constructr
Derived destructor
Base destructor
```

### Case 5

```c++
#include<iostream>
using namespace std;
class Base
{
   int x,y;
  public:
  	Base(){
  	 cout << "Base  constructor " << endl;
  	 x=10,y=20;
  	}
  		Base(int a,int b):x(a),y(b){
  		 cout << "Base parametrized" << endl;
  		}
  	~Base()
  	{
  	 cout << "Base destructor " << endl;
  	}
};
class Derived:public Base
{
 int m,n;
 public:
 Derived(){
 cout << "Derived constructr " << endl;
  m=30,n=40;
 } 
 Derived(int a,int b,int c,int d):Base(a,b){ // this
 cout << "derived parametrized" << endl;
 }
	~Derived(){
	cout << "Derived destructor" << endl;
	}
};
int main() 
{  
   Derived d(101,201,301,401);  //Derived(&d)
}
```

**Output**

```sh
Base parametrized
derived parametrized
Derived destructor
Base destructor
```

## Multilevel Inheritance

```c++
#include<iostream>
using namespace std;
class Base
{
   int x;
  public:
  	Base(){
  	 cout << "Base  constructor " << endl;
  	 x=10;
  	}
  	Base(int a):x(a){
  		 cout << "Base parametrized" << endl;
  	}
  	~Base()
  	{
  	 cout << "Base destructor " << endl;
  	}
};
class Derived1:public Base
{
 int n;
 public:
 Derived1(){
 cout << "Derived1 constructr " << endl;
 n=40;
 } 
 Derived1(int a,int b):Base(a),n(b){ // this
 cout << "derived1 parametrized" << endl;
 }
	~Derived1(){
	cout << "Derived1 destructor" << endl;
	}
};
class Derived2:public Derived1
{
 int m;
 public:
 Derived2(){
 cout << "Derived2 constructr " << endl;
  m=30;
 } 
 Derived2(int a,int b,int c):Derived1(a,b),m(c){ // this
 cout << "derived2 parametrized" << endl;
 }
	~Derived2(){
	cout << "Derived2 destructor" << endl;
	}
};
int main() 
{  
   Derived2 d(101,201,301);  //Derived(&d)
}
```
**Output**

```sh
Base parametrized
derived1 parametrized
derived2 parametrized
Derived2 destructor
Derived1 destructor
Base destructor
```


**Invalid** in Multilevel Inheritance

```c++
class Derived2:public Derived1
{
 int m;
 public:
 Derived2(){
 cout << "Derived2 constructr " << endl;
  m=30;
 } 
 Derived2(int a,int b,int c):Base(a){ // invalid
 cout << "derived2 parametrized" << endl;
 }
	~Derived2():~Derived1(){
	cout << "Derived2 destructor" << endl;
	}
};
```

**Error**

```sh
multlllll.cpp:46:14: error: expected '(' or '{'
   46 |         ~Derived2():~Derived1(){
      |                     ^
multlllll.cpp:43:30: error: type 'Base' is not a direct or virtual base of 'Derived2'
   43 |  Derived2(int a,int b,int c):Base(a){ // invalid
      |                              ^~~~
2 errors generated.
```


## Multipath Inheritance

```c++
#include<iostream>
using namespace std;
class A
{
public:
	int x;
	A(){
	cout << "constructor A"<< endl;
	x=10;
	}
	~A(){
		cout<< "Destructor A" << endl;
	}
};
class B:virtual public A
{
public:
	int y;
	B(){
	cout << "constructor B"<< endl;
	y=20;
	}
	~B(){
		cout<< "Destructor B" << endl;
	}

};
class C:virtual public A
{
public:
	int z;
	C(){
	cout << "constructor C"<< endl;
	z=30;
	}
	~C(){
		cout<< "Destructor C " << endl;
	}

};
class D:public B,public C
{
public:
	int m;
	D(){
	cout << "constructor D"<< endl;
	m=40;
	}
	~D(){
		cout<< "Destructor D" << endl;
	}
	void get_data(){
	cout << x << endl;
	//cout << B::x << endl;
	//cout << C::x << endl;
	cout << y << endl;
	cout << z << endl;
	cout << m  << endl;
	
	}
};
int main(){
 
  D obj;
  obj.get_data();
  cout << sizeof(A) << endl;
	cout << sizeof(B) << endl;
	cout << sizeof(C) << endl;
	cout << sizeof(D) << endl;
}
```


# Virtual Class and Virtual Function

## Function Overriding
```c++
//function overriding
#include<iostream>
using namespace std;
class Base
{
public:
  void test(){
  cout << "test in Base" << endl;
  }
};
class Derived:public Base
{
public:
  void test(){
  cout << "test in Derived" << endl;
  }
};
int main() 
{  
    Derived d;
    d.Base::test();
    d.test();
 
 
}
```

## Upcasting 

- Base class pointer holding derived class object address is valid.

### Case 1

```c++
#include<iostream>
using namespace std;
class Base
{
public:
  void test(){
  cout << "test in Base" << endl;
  }
};
class Derived:public Base
{
public:
  void test(){
  cout << "test in Derived" << endl;
  }
};
int main() 
{  
  Base *bptr;
  Derived d;
  bptr=&d; 
 
}
//upcasting
```

### Case 2

```c++

//function overriding
#include<iostream>
using namespace std;
class Base
{
public:
  virtual void test(){
  cout << "test in Base" << endl;
  }
};
class Derived:public Base
{
public:
  void test(){
  cout << "test in Derived" << endl;
  }
};
int main() 
{  
 Base b;
  Base *bptr;
  Derived d;
  d.test();
  bptr=&b; 
  bptr->test(); //pending ;
}

//upcasting:
```


## Downcasting

- Derived class pointer cab't hold derived class object address 

```c++

//function overriding
#include<iostream>
using namespace std;
class Base
{
public:
  void test(){
  cout << "test in Base" << endl;
  }
};
class Derived:public Base
{
public:
  void test(){
  cout << "test in Derived" << endl;
  }
};
int main() 
{  
  Derived *dptr;
  Base b;
  dptr=&b;
}
//downcasting
```

## Vector Table

```c++
#include<iostream>
using namespace std;
class A
{
 int x;
 public:
 	virtual void test1(){
 	  cout << "test1 in A" << endl;
 	}
 	virtual void test2(){
 	  cout << "test2 in A" << endl;
 	}
    void test3(){
 	  cout << "test3 in A" << endl;
 	}

};
class B:public A
{
public:
 	void test1(){
 	  cout << "test1 in B" << endl;
 	}
 	void test3(){
 	  cout << "test3 in B" << endl;
 	}

};
class C:public A
{
public:
 	void test2(){
 	  cout << "test2 in C" << endl;
 	}
    void test3(){
 	  cout << "test3 in C" << endl;
 	}

};
int main() 
{  
    A *ptr;
    A a;
    ptr=&a;
    ptr->test1();
    ptr->test2();
    ptr->test3(); 
    B b;
    ptr=&b;
    ptr->test1();
    ptr->test2();
    ptr->test3(); 
  
    ptr=&c;
    ptr->test1();
    ptr->test2();
    ptr->test3(); 
 
}
```