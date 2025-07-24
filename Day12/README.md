# Constructor

- Special member function.
- For **initialization** of data.
- Called **automatically** by compiler when object get created.
- Doesn't have any return type.

### Question : Does Constructor have `this` pointer ?
Yes, it have this pointer.
### Question : How many time constructor will execute to that object in it life time ?
Only **1 time**, at the time if initilization of **object**.
### Question : Is Constructor constructing a object ?
Yes
### When object gets created Successfully ?
1. memory allocation  
2. memory initilization   
When both the steps complete successfully without any error, object gets created successfully.


## Type of Constructor
- **Default Constructor**
- **Parameterized Constructor**
- **Copy Constructor**

### Default Constructor
The constructor doesn't have any argument. *(No formal argument.)*

```c++
#include<iostream>
using namespace std;
class Family
{
 int cash,gold;
 ```
```c++
 public:
  Family(){
    cout << "default constructor  " << endl;
    cash=10,gold=20;
  }
 ```
```c++
 void set_data(){
 cin >> cash >> gold;
 }
 void get_data(){
 	cout << cash << " " << gold << endl;
 }
};
```
```c++
int main() 
{  
  Family f1;  
  f1.get_data();
}
```

**Output**
```sh
default constructor
10 20
```
### If user not provide any constructor then what will happen ?
**Compiler** will by default provide **default constructor**.


### Parameterized Constructor
Constructor having argument. *(at least one argument)* 
```c++
#include<iostream>
using namespace std;
class Family
{
 int cash,gold;
 public:
  Family(){
    cout << "default constructor  " << endl;
    cash=10,gold=20;
  }
```
```c++

  Family(int a,int b){
   cout << "parametrized constructor "<< endl;
   cash = a,gold = b;
  }
```
```c++ 
 void set_data(){
 cin >> cash >> gold;
 }
 void get_data(){
 	cout << cash << " " << gold << endl;
 }
};
int main() 
{  
  Family f1,f2(100,200);  
  f1.get_data();
  f2.get_data();
}
```
**How f2(100, 200) is called**
```c++
Family :: Family(&f2 , 100, 200);
```

**Output**
```sh
default constructor
parameterized constructor
10 20
100 200
```

### Copy Constructor

Copy one object data to another object at the time of creating an object. *(at the time of initialization)*

>[!Note]  
> - Copy Constructor must collect the argument with **reference** type only.   
> - If Copy Constructor is not called with **reference** , then copy constructor will call **recursively**. 

## Case : Copy Constructor must colled the argument with reference 

**Invalid**
```c++
#include<iostream>
using namespace std;
class Family
{
 int cash,gold;
 public:
  Family(){
    cout << "default constructor  " << endl;
    cin >> cash >> gold;
  }
 ```
 Without `&`
 ```c++ 
 Family(Family t){
   cout << "copy constructor " << endl;
   this->cash = t.cash;
   this->gold = t.gold;
  }
 void get_data(){
 	cout << cash << " " << gold << endl;
 }
};
```
Non Member function
```c++
Family test(Family t){
  cout << "test func executed" << endl;
  return t;
 }
```
```c++
int main() 
{  
  Family f1,f2(f1);
  test(f1);
}
```
**Error**
```sh
copy.cpp:11:16: error: copy constructor must pass its first argument by reference
   11 |  Family(Family t){
      |                ^
      |                const &
1 error generated.
```

**Valid Code**
```c++
#include<iostream>
using namespace std;
class Family
{
 int cash,gold;
 public:
  Family(){
    cout << "default constructor  " << endl;
    cin >> cash >> gold;
  }
 Family(Family& t){
   cout << "copy constructor " << endl;
   this->cash = t.cash;
   this->gold = t.gold;
  }
 void get_data(){
 	cout << cash << " " << gold << endl;
 }
};
```
Non Member function
```c++
Family test(Family t){
  cout << "test func executed" << endl;
  return t;
 }
```
```c++
int main() 
{  
  Family f1,f2(f1);
  test(f1);
}
```
- First `f1` will call `default constructor`.
- `f2(f1)` will call `copy constructor`.
- `test(f1)` passes the data to `t` as now also it will call `copy constructor`.
- `return t` will also create another copy, call `copy constructor`.

**Output**

```sh
default constructor
10 20
copy constructor
copy constructor
test func executed
copy constructor
```
### Case 1 : If user provide a constructor explicitly, Compiler doesn't provide default constructor.

```c++
#include<iostream>
using namespace std;
class Family
{
 int cash,gold;
 public:
 Family(Family& t){
   cout << "copy constructor " << endl;
   this->cash = t.cash;
   this->gold = t.gold;
  }
 void get_data(){
 	cout << cash << " " << gold << endl;
 }
};
int main() 
{  
  Family f1,f2(f1);
  f1.get_data();
  f2.get_data();
}
```
**Error**
```sh
copy1.cpp:18:10: error: no matching constructor for initialization of 'Family'
   18 |   Family f1,f2(f1);
      |          ^
copy1.cpp:7:2: note: candidate constructor not viable: requires single argument 't', but no arguments were provided
    7 |  Family(Family& t){
      |  ^      ~~~~~~~~~
1 error generated.
```

## Case 2 : Compiler provide Copy Constructor by default. If user doesn't provide.

```c++
#include<iostream>
using namespace std;
class Family
{
 int cash,gold;
 public:
 Family(){
  cout << "default " << endl;
  cash=10,gold=20;
 }
 void get_data(){
 	cout << cash << " " << gold << endl;
 }
};
int main() 
{  
  Family f1,f2(f1);
  f1.get_data();
  f2.get_data();
}
```
**Output**
```sh
default
10 20
10 20
```

## Case 3: More than one argument will lead to Parameterized Connstructor.

```c++
#include<iostream>
using namespace std;
class Family
{
	int cash,gold;
	public:	 
Family(int a=1,int b=2){
	cout << "parametrized " << endl;
	cash = a,gold= b;
}
void get_data(){
 	cout << cash << " " << gold << endl;
}
};
int main() 
{  
  Family f1,f2(100,200);
  f1.get_data();
  f2.get_data();
}
```

## Member Initilization of Class

```c++
#include<iostream>
using namespace std;
```
```c++
class Family
{
	int cash,gold;
	public:
	Family();
	Family(int,int);
	Family(Family &);
	void get_data();
};
```
```c++
int main() 
{  
	Family f1,f2(100,200),f3(f2);
	f1.get_data();
	f2.get_data();
    f3.get_data();
}
```
**Default Constructor**
```c++
Family::Family():cash(10),gold(20){
	cout << "Default constructor " << endl;
}
```
**Parametrized Constructor**
```c++
Family::Family(int a,int b):cash(a),gold(b){
	cout << "Parametrized constructor" << endl;
}
```
**Copy Constructor**
```c++
Family::Family(Family &t):cash(t.cash),gold(t.gold){
	cout << "Copy constructor " << endl;
}
```
```c++
void Family::get_data(){
	cout << cash << " " << gold << endl;
}
```

**Output**

```sh
Default constructor
Parametrized constructor
Copy constructor
10 20
100 200
100 200
```