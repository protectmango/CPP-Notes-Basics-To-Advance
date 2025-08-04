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