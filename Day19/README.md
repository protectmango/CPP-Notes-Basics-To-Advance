# Templates

- Template is a format.
- It is used to created `generic function` or `generic classes`.
- Template are used to create function/class which work on different datatype.

**Template** types
- Function Template
    - working like generic and works on different 
datatype.

```c++
template <typename T>
T maximum(T a, T b) {
    return (a > b) ? a : b;
}
```

- Class Template 
    - working like generic class and works on different datatype.

```c++
template <class T>
class MyContainer {
public:
    T value;
    MyContainer(T val) : value(val) {}
};
```

## Case 1  
```c++
#include<iostream>
using namespace std;
template<class type>
class ARRAY
{
  type a[5];
  public:
  	ARRAY(){
  	 cout << "enter " << typeid(a).name()  << endl;
  	 for(int i=0;i<5;i++)
  	 cin >> a[i];
  	}
  	void get_data(){
  	 for(int i=0;i<5;i++)
  	 cout << a[i] << endl;
  	}
  	void reverse(){
  	type t;
   	 for(int i=0,j=4;i<j;i++,j--){
          t=a[i]; 	 
  	 	  a[i]=a[j];
  	 	  a[j]=t;
  	 }
  	}
};
int main() 
{  
   ARRAY <int>obj1; 
   ARRAY <float>obj2;
   ARRAY <char>obj3;
   obj1.reverse();
   obj1.get_data();
   obj2.reverse();
   obj2.get_data(); 
   obj3.reverse();
   obj3.get_data();   
}
```

## Case 2  

```c++
#include<iostream>
using namespace std;
template<class T1,class T2>
class A
{
 T1 x;
 T2 y;
 public:
 	A();
 	A(T1 ,T2);
 	void get_data();
};

template<class T1,class T2>
A<T1,T2>::A(){
 cout << "enter " << typeid(T1).name() << "  and " << typeid(T2).name()  << endl;
 cin >> x >> y;
}

template<class type1,class type2>
A<type1,type2>::A(type1 a,type2 b){
  x=a,y=b;
}

template<class T1,class T2>
void A<T1,T2>::get_data(){
 cout << x << " " << y << endl;
}

int main() 
{  
  A <int,char>obj1;
  A<double,int> obj2(10.4,12);
  A <char,float>obj3;
  A <string,int>obj4;
  obj1.get_data();
  obj2.get_data();
  obj3.get_data();
  obj4.get_data();
}
```

- To avoid function overloading we use templates.
- To create a function as generic then above the funtion must and should teplate arg created.

### Run time type identification

- use typeid() special operator function to find type of a variable at runtime.

```c++
#include<iostream>
using namespace std;
int main() 
{  
 auto x=10;
 auto k="hello";
 auto p={1,2,3,4,5};
 auto m=&x;
 cout << typeid(x).name() << endl;
 cout << typeid(k).name() << endl;
 cout << typeid(p).name() << endl;
 cout << typeid(m).name() << endl;
}
```
**Output**
```sh
i
PKc
St16initializer_listIiE
Pi
```

### Can I overload function templates?
- Yes

## Function Template

### Case 1 : Same type of data

```c++
#include<iostream>
using namespace std;
template<class Type>
Type sum(Type a,Type b)
{
 cout << "sum func: ";
 cout << typeid(a).name() << " ";
 cout << typeid(b).name() << endl;
 return a+b;
}

int main() 
{  
 cout << sum(10,20) << endl;
 cout << sum(10.2,23.4) << endl;
 cout << sum('0','1') << endl;
}
```

**Ouput**
```sh
sum func: i i
30
sum func: d d
33.6
sum func: c c
a
```

### Case 2 : Different type of data

```c++
#include<iostream>
using namespace std;
template<class type1,class type2,class type3=double>
type3 sum(type1 a,type2 b)
{
 cout << "sum func: ";
 cout << typeid(a).name() << " ";
 cout << typeid(b).name() << endl;
 return a+b;
}

int main() 
{  
 cout << sum(10,20.4) << endl;
 cout << sum(10.2,'a') << endl;
 cout << sum('0',12) << endl;
}
```

**Output**

```sh
sum func: i d
30.4
sum func: d c
107.2
sum func: c i
60
```

### Case 3 : Multiple Template Functions

```c++
#include<iostream>
using namespace std;
template<typename type>
double area(type r)
{
 cout << "area of circle" << endl;
 return 3.14*r*r;
}

template<class type>
type area(type l,type b)
{
cout << "area of rectangle" << endl;
 return l*b;
}

int main() 
{  
  cout << area(2) << endl;
  cout << area(2.3) << endl;
  cout << area(2,3) << endl;
  cout << area(2.3,4.5) << endl;
}
```

**Output**

```sh
area of circle
12.56
area of circle
16.6106
area of rectangle
6
area of rectangle
10.35
```


# Type Conversion

- Converting one datatype to another datatype including userdefined datatypes.

- 3 types of Conversion
    - Basic to Class
    - Class to Basic
    - Class to Class

## Basic to Class

```c++
obj = a
```
- `obj` → Target
- `a` → Source

- Userdefined datatype can be modified.
- Predefined datatype can't be modified.

- The conversion logic need to implement in the **userdefined class**.
- Conversion login implemented in target side, then take **proper constructor**.

- Here, Constructor used to convert one datatype to another , it is called **Conversion Constructor**.

```c++
#include<iostream>
using namespace std;
class Time
{
  int hr,mint;
  public:
   Time():hr(0),mint(0){}
   Time(int n){
    cout << "conversion constructor" << endl;
    hr = n/60;
    mint=n%60;
   }
   void getTime(){
   cout << "Time:" ;
   cout << hr  << " Hours " << mint << " Minutes" << endl;
   }
  
};
int main() 
{  
  Time t;
  t.getTime();
   int n;
   cout << "Enter Total minutes :"  << endl;
   cin >> n;
  t=n;               //    t=n
  					 //    Time temp(n)
  					 //    t=temp
  t.getTime();
}
```

## Class to Basic

```c++
a = obj
```

- `a` → Target
- `obj` → Source

- Target is predefined datatype, can't be modified.
- Source is User defined datatype can be modified.

- Conversion login need to implement in source side.
- If source side conversion logic implemented then **proper conversion** function is needed.

**Syntax** of Conversion function

```c++
operator type() {}
```
1. It is a special Function.
2. It doesn't have any return type but it will return value.
3. It doesn't have any arguments.
4. It must be member function.

```c++
#include<iostream>
using namespace std;
class Time
{
  int hr,mint;
  public:
  	Time(){
  	 cout << "Enter hr and mint" << endl;
  	 cin >> hr >> mint;
  	}
  	operator int(){
  	 cout << "conversion func" << endl;
  	 return hr*60+mint;
  	} 	

};
int main() 
{  
  Time t;
  int n;
  n=t;      ///          n=t.operator int();
  cout << "Total minutes: " << n << endl;
 
}
```

## Class to Class

```c++
obj1 = obj2
```
- `obj1` → Target
- `obj2` → Source

- Both are user defined ,So can implement the conversion logic,on both target side and source side. 
- if target, proper constructor.
- if source, proper conversion function.


```c++
#include<iostream>
using namespace std;
class B
{
 int m,n;
 public:
 	B():m(0),n(0){}
 	void getB(){
 	cout << m << " " << n << endl;
 	}
 	B(int a,int b){
 	 m = a, n = b;
 	}
};
class A
{
 int x,y;
 public:
 	A():x(10),y(20){}
 	operator B(){
 	cout << "conversion" << endl;
 	 return B(x,y);
 	}
};

int main() 
{  
  A a1;
  B b1;
  b1.getB();
  b1=a1;               // b1=a1.operator B();
  b1.getB();
}
```