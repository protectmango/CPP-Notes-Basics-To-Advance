# Constant Member Functions

>[!Note]  
> - Constant function cannot modify data.
> - It is a member function where the data member are constant.

**Syntax**

```c++
returntype classname::function_name (arg) const;
```

>[!Note]  
> Here, **this** pointer act as a **const** pointer.

**Example**

```c++
#include<iostream>
using namespace std;
class Family
{
 int cash,gold;
 public:
 	void set_data(){
 	 cash = 10,gold = 20;
 	}
 	void get_data() const {
 	 cout << cash  << " "<< gold << endl;
 	}

};
int main() 
{  
  Family f;
  f.set_data();
  f.get_data();
}
```

**Output**

```sh
10 20
```

## If we try to modify the member in const function we get error

```c++
#include<iostream>
using namespace std;
class Family
{
 int cash,gold;
 public:
 	void set_data(){
 	 cash = 10,gold = 20;
 	}
 	void get_data() const {
```
trying to modify the data member in a const function.
```c++ 	
    cash=1000,gold=2000;
```
```c++
 	 cout << cash  << " "<< gold << endl;
 	}

};
int main() 
{  
  Family f;
  f.set_data();
  f.get_data();
 
}
```

**Error**

```sh
const.cpp:11:7: error: cannot assign to non-static data member within const member function 'get_data'
   11 |         cash=1000,gold=2000;
      |         ~~~~^
const.cpp:10:8: note: member function 'Family::get_data' is declared const here
   10 |         void get_data() const {
      |         ~~~~~^~~~~~~~~~~~~~~~
const.cpp:11:17: error: cannot assign to non-static data member within const member function 'get_data'
   11 |         cash=1000,gold=2000;
      |                   ~~~~^
const.cpp:10:8: note: member function 'Family::get_data' is declared const here
   10 |         void get_data() const {
      |         ~~~~~^~~~~~~~~~~~~~~~
2 errors generated.
```

# Mutable
## If we want to modify the data member in const function as a execption.

>[!Note]  
> - If object is const then **user** provided **constructor** is **mandatory**.  
> - Compier provided default constructor doesn't support these operations.

```c++
#include<iostream>
using namespace std;
class Family
{
 mutable int cash;
  int gold;
 public:
 	void set_data(){
 	 cash = 10,gold = 20;
 	}
 	void get_data() const {
```
**Valid** as this member is **mutable**.
```c++
cash=1000;
```
**Invalid** as this member is not **mutable**.
```c++
gold=2000;  //invalid
```
```c++
    cout << cash  << " "<< gold << endl;
 	}

};
int main() 
{  
  Family f;
  f.set_data();
  f.get_data();
  const int k=10; 
 
}
```
**Output**   
- For `cash = 1000;`
```sh
1000 20
```
**Error**
- For `gold = 2000`  
```sh
const2.cpp:13:8: error: cannot assign to non-static data member within const member function 'get_data'
   13 |          gold=2000;
      |          ~~~~^
const2.cpp:11:8: note: member function 'Family::get_data' is declared const here
   11 |         void get_data() const {
      |         ~~~~~^~~~~~~~~~~~~~~~
const2.cpp:20:16: error: default initialization of an object of const type 'const Family' without a user-provided default constructor
```

### Case : Constant Object

>[!Note]   
>If object is **constant** then user provided constructor is mandatory.
```c++
#include<iostream>
using namespace std;
class Family
{
 mutable int cash;
  int gold;
 public:
 	Family(){
 	 cout << "constructor " << endl;
 	 cash=10,gold=20;
 	}
 	void set_data(){      // Family *const this
 	 cash = 10,gold = 20;
 	}
 	void get_data() const {
 	 cash=1000;
 	 cout << cash  << " "<< gold << endl;
 	}

};
int main() 
{  
  const Family f1;
  f1.set_data(); // invalid  //Family::set_data(&f1);
  f1.get_data();
}
```

**Error**

```sh
const3.cpp:24:3: error: 'this' argument to member function 'set_data' has type 'const Family', but function is not marked const
   24 |   f1.set_data(); // invalid  //Family::set_data(&f1);
      |   ^~
const3.cpp:12:8: note: 'set_data' declared here
   12 |         void set_data(){      // Family *const this
      |              ^
1 error generated.
```