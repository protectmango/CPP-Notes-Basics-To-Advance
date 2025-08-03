# Exception Handling

- **Error is program**
    - Compile Time Error
    - Runtime Error

- A exception is an event which occurs during the exception of a program that interrupt the normal flow of the program's instructions.

- Exception, which occurs at runtime, due to unusual conditions.

- This mechanism uses these keywords
    - `try`
    - `throw`
    - `catch`

- A `try block` will throw an exception using `throw` keyword.

```c++
try
{
    throw exception_occured;
}
```

- A try block will throw an exception using throw keyword.

- Catch block will be handle the exception condition which is sent by throw.

```c++
try{
    throw exception_occured;
}
catch (data-type argument)
{
    /*Statements*/
}
```

- Some exception where try blcok may produce various types of exceptions.

- Can write catch blcok which can handle all type of exception.

```c++
catct(...) /*Catch All*/
{

}
```

### Program : Divided by zero

```c++
#include <iostream>
using namespace std;
int main()
{
    int x, y,z;

    cout << "Enter x = " endl;
    cin >> x;

label :  
        cout << "Enter y = "<<endl;
        cin>>y;

        try 
        {
            if(y==0)
                throw "divided by 0";
            else
                z = x/y;
        }
        catch (const char *p)
        {
            cout << p << endl;
            goto label;
        }

    cout << "z = " << z << endl;
}
```

- Using external function

```c++
#include <iostream>
using namespace std;
int divide(int a, int b)
{
    cout<< "Divide function"<< endl;
    if(b==0)
        throw "divided by 0";
    else
        return a/b;
}
int main()
{
    int x, y,z;

    cout << "Enter x = " endl;
    cin >> x;

label :  
        cout << "Enter y = "<<endl;
        cin>>y;

        try 
        {
            z = divide(x,y);            
        }
        catch (const char *p)
        {
            cout << p << endl;
            goto label;
        }

    cout << "z = " << z << endl;
}
```

## How to catch exception using a contructor ?

```c++
#include<iostream>

using namespace std;

class A
{
    public :
            A()
            {
                throw (10);
            }
};

int main()
{
    try
    {
        A obj;
    }
    catch (int x)
    {
        /*Statements*/
    }
}
```
## Unhandled Exceptions

### Case 1 : Catch not Availble

```c++
#include<iostream>
using namespace std;
/* unhandled exception ex:1 */
int main() 
{  
  throw 12;
}
```

### Case 2 : Proper Catch Statement no avaible 

```c++
#include<iostream>
using namespace std;
/* unhandled exception ex:2 */
int main() 
{  
  try
  {
  //throw "hello";
   throw 12;
  }
  catch(const char *s)
  {
  cout << "exception : " << s << endl;
  }
}
```

### Case 3 : set_terminate()

```c++
#include<iostream>
using namespace std;
void emergency(){
  cout << "Exception unhandled "<< endl;
  cout << "Please all of u be alert" << endl;
  cout << "Assemble in Assembly point" << endl;
  //exit(0);
}
int main() 
{  
  set_terminate(emergency);
   try
   {
     //throw 12;   
     throw 12.4;
   }
   catch(int a){
    cout << "exception int: "<< a << endl;
   }

 
}
```

**Output**
```sh
Exception unhandled
Please all of u be alert
Assemble in Assembly point
libc++abi: terminate_handler unexpectedly returned
[1]    24405 abort      ./a.out
```

### Case 4 :  Dynamic Memory Allocation

```c++
#include<iostream>
using namespace std;
int main() 
{  
  int *p;
  unsigned int n;
  cin >> n;
  try
  {
  p=new int [n];
  cout << "memory allocated" << endl;
  }
  catch(exception &e){
  cout << e.what() << endl;
  }
}
```

**Output**

- Memory Allocated

```sh
5
memory allocated
```

- Memory Not Allocated 

```sh
9999999999
bad allocation
```

### Case 5 : Proper Catch Handling 

```c++
#include<iostream>
using namespace std;
int main() 
{  
 try
 {
  throw 12.3;
 // throw 12;
 
 }	
 catch(int a){
  cout << "int ex: " << endl;
 }
 catch(double d){
 cout << "double ex: " << d << endl;
 }
 catch(char *s){
 cout << "char * " << s << endl;
 }
 catch(...){
  cout << "default" << endl;
 }
}
```

### Case 6 :  Default Catch 

```c++
#include<iostream>
 using namespace std;
int main() 
{  
  try
  {
   throw "12.4";
  }
  catch(...)
  {
   cout << "default" << endl;
  }
 
}
```

### Case 7 : Constructor Exceptions

```c++
#include<iostream>
using namespace std;
class A
{
 int x,y;
 public:
 	A(){
 	cout << "constructor " << endl;
 	throw 100;
 	x=10;
 	y=20;
 	}
	void get_data(){
	cout << x << " " << y << endl;
	}
	~A(){
	cout << "Destructor  "<< endl;
	}

};
int main() 
{
  try
  {  
  A obj;
  obj.get_data(); 
  }
  catch(int a){
   cout << "object not created" << endl;
   cout << "constructor failed due to value: " << a << endl;
  }  
}
```

**Output**

```sh
constructor
object not created
constructor failed due to value: 100
```

### Case 8 :  Nested Blocks

- If we rethrow an exception it must be catch by another catch block.

```c++
#include<iostream>
using namespace std;
void test2(){
 cout << "test2 func" << endl;
 throw "n/w issue";
}
void test1(){
  try
  {
   test2();  
  }
  catch(const char *s){
   cout << "in test1 : " << s << endl;
   throw;
  }
}
int main() 
{  
   try
   {
     test1();   
   }
   catch(const char *s){
    cout << "in main: " << s << endl;
   }
}
```

**Output**

```sh
test2 func
in test1 : n/w issue
in main: n/w issue
```

### Case 9 : Unwind

- Here the stack of test2() and test3() will be automatically destroyed.

```c++
#include<iostream>
using namespace std;
void test3(){
   cout <<"test3 func" << endl;
   throw "Be happy";
}
void test2(){
   test3();
   cout << "test2 func" << endl;
}
void test1(){
   test2();
   cout << "test1 func "<< endl;
}
int main() 
{  
  try
  {
    test1();  
  }
  catch(const char *s){
  cout << "in main:" << s << endl;
  }
  cout << "main func" << endl;
 
}
```

**Output**


```sh
test3 func
in main:Be happy
main func
```

