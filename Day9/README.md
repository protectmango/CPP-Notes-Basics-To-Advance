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