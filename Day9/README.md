# Function Overloading

**Overloading** refer to the capability of using a single a name for several different task.

**Defination**  
Defining multiple function with the same name is called **function overloading**.    
These function must differ in their  
- number
- order
- types of argument  

at compile time it will check for   
1. No of argument.
2. Order of argument.
3. Type of argument.

**Example**
```c++
sum(int, int);
sum(int, float);
sum(float, int);
```

### Case 1 : Differ in argument
```c++
#include<iostream>
using namespace std;
void sum(int x,int y)
{
    cout<<"sum of int "<< x+y <<endl;
}
void sum(float x,float y)
{
    cout<<"sum of float "<< x+y <<endl;
}
int main()
{
sum(20,30);
sum(23.4f,34.5f);
}
```
**Output**
```sh
sum of int 50
sum of float 57.9
```
### Case 2 : Order of argument
```c++
#include<iostream>
using namespace std;
void sum(int x,float y)
{
    cout<<"sum of int+float "<<x+y<<endl;
}
void sum(float x,int y)
{
    cout<<"sum of float+int "<<x+y<<endl;
}
int main()
{
sum(20,30.4f);
sum(23.4f,34);
}
```
**Output**
```sh
sum of int+float 50.4
sum of float+int 57.4
```
### Case 3 : Number of argument
```c++
#include<iostream>
using namespace std;
void sum(int x,int y)
{
    cout<<"sum of 2 int "<<x+y<<endl;
}
void sum(int x,int y,int z)
{
    cout<<"sum of 3 int "<<x+y+z<<endl;
}
int main()
{
    sum(20,30);
    sum(23,34,12);
}
```
**Output**
```sh
sum of 2 int 50
sum of 3 int 69
```
### Case 4 : Character are treated as int as default by the compiler
```c++
#include<iostream>
using namespace std;
int  sum(int x,int y)
{
    cout<<"int block"<<endl;
return x+y;
}
int sum(float x,float y)
{
    cout<<"float block"<<endl;
return x+y;
}
int main()
{
    cout<<sum(20,30)<<endl;
    cout<<sum(23.3f,34.5f)<<endl;
    cout<<sum('a','b')<<endl;
}
```

**Output**
- ```c++
    cout<<sum(20,30)<<endl; 
    ```
    ```sh
    int block
    50
    ```
- ```c++
    cout<<sum(23.3f,34.5f)<<endl; 
    ```
    ```sh
    float block
    57
    ```
- ```c++
    cout<<sum('a','b')<<endl; 
    ```
    ```sh
    int block
    195
    ```

## Ambiquity in Function Overloading.

### **Case 1** : Default argument
```c++
#include<iostream>
using namespace std;
void fun(int a,int b=0)
{
    cout<<a<<endl;
}
void fun(int a)
{
    cout<<a<<endl;
}
int main()
{
    fun(200);//Error bcz of default argument
}
```
**Error**
```sh
amb.cpp:13:1: error: call to 'fun' is ambiguous
   13 | fun(200);
      | ^~~
amb.cpp:3:6: note: candidate function
    3 | void fun(int a,int b=0)
      |      ^
amb.cpp:7:6: note: candidate function
    7 | void fun(int a)
      |      ^
1 error generated.
```
### **Case 2** : Automatic type conversion
```c++
#include<iostream>
using namespace std;
void fun(float a)
{
    cout<<a<<endl;
}
void fun(double a)
{
    cout<<a<<endl;
}
int main()
{
    fun(200);
}
```
**Error**
```sh
amb1.cpp:14:1: error: call to 'fun' is ambiguous
   14 | fun(200);
      | ^~~
amb1.cpp:4:6: note: candidate function
    4 | void fun(float a)
      |      ^
amb1.cpp:8:6: note: candidate function
    8 | void fun(double a)
      |      ^
1 error generated.
```
###  **Case 3** : Ambiquity between Variable and Reference
```c++
#include<iostream>
using namespace std;
void fun(int a)
{
    cout<<a<<endl;
}
void fun(int &a)
{
    cout<< a <<endl;
}
int main()
{
    int b=20;
    fun(b);
}
```
**Error**
```sh
amb2.cpp:14:1: error: call to 'fun' is ambiguous
   14 | fun(b);
      | ^~~
amb2.cpp:3:6: note: candidate function
    3 | void fun(int a)
      |      ^
amb2.cpp:7:6: note: candidate function
    7 | void fun(int &a)
      |      ^
1 error generated.
```
## Name Mangling
C++ allows multiple functions to share the same name as long as their parameter lists differ (function overloading).  
**Name mangling** encodes the parameter types into the function's internal name, allowing the **linker** to distinguish between overloaded functions.

# Default Arguments
**Default Argument** is a **function parameter**, that provide some **default value** to it, if **user** is **not** providing any argument, the function should take **default value**.

**Example**
```c++
#include<iostream>
using namespace std;
int sum(int x,int y=60)
{
    cout<<x+y<<endl;
}
int main()
{
    sum(10,20);
    sum(100);
}
```
**Output**
```sh
30
160
```

### Case 1 : Too few arguments
```c++
#include<iostream>
using namespace std;
int sum(int x,int y)
{
    cout<<x+y<<endl;
}
int main()
{
    sum(100);
}
```
**Error** : Too few argument
```sh
default.cpp:9:1: error: no matching function for call to 'sum'
    9 | sum(100);
      | ^~~
default.cpp:3:5: note: candidate function not viable: requires 2 arguments, but 1 was provided
    3 | int sum(int x,int y)
      |     ^   ~~~~~~~~~~~
1 warning and 1 error generated.
```
### Case 2 : Always provide default to right most arguemnt
```c++
#include<iostream>
using namespace std;
int sum(int x=0,int y)
{
cout<<x+y<<endl;
}
int main()
{
    sum(100);
}

```
**Error** 
```sh
def2.cpp:3:21: error: missing default argument on parameter 'y'
    3 | int sum(int x=0,int y)
      |                     ^
def2.cpp:9:1: error: no matching function for call to 'sum'
    9 | sum(100);
      | ^~~
def2.cpp:3:5: note: candidate function not viable: requires 2 arguments, but 1 was provided
    3 | int sum(int x=0,int y)
      |     ^   ~~~~~~~~~~~~~
2 errors generated.
```
**Correct Approch**
```c++
#include<iostream>
using namespace std;
int sum(int,int=90);
int main()
{
    sum(10,20);
    sum(100);
}
int sum(int x,int y)
{
    cout<<x+y<<endl;
}
```
**Output**
```sh
30
190
```
