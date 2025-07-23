# Class & Object

**Class** is a collection of data member and member function.

To create a class we use keyword `class.`

**Syntax**
```c++
class Student{
    int rollno;
    void func(){

    }
};
```
|||
|---|---|
|**class**|`keyword`|
|**Student**|`tagname`|
|**int rollno;**|`attribute`| 
|**void func(){}**|`method`|
|||

## Reading an Printing data from member functions

```c++
#include<iostream>
using namespace std;
class Family
{
 int cash,gold;
```
**Member functions / Methods**
```c++
 void set_data(){
  cout << "set func " << endl;
  cin >> cash >> gold;
 }
 void get_data(){
 cout << "get func " << endl;
 cout << cash << " " << gold << endl;
 }
};
```
**Non member function**
```c++
int main()
{
  Family f1,f2;
  f1.set_data();
  f2.set_data();
  f1.get_data();
  f2.get_data();
}
```

**Input**
```sh
set func
10 20
set func
100 200
```
**Output**
```sh
get func
10 20
get func
100 200
```


## this pointer
For every **member function/ method** internally a pointer is created. ie. `this pointer` 

- this pointer type is class type.
- it is a const pointer.

```c++
#include<iostream>
using namespace std;
class Family
{
 int cash,gold;
 public:
```
**Member functions / Methods**
```c++

 void set_data(){
```
**this** pointer hold the address of the object which is used to call the member function. 
```c++
  cout << "set func:  "<< this << endl;
  cin >> this->cash >> this->gold;
 }
```
```c++
 void get_data(){
 cout << "get func : " << this << endl;
 cout << cash << " " << gold << endl;
 }
};
```
**Non member function**
```c++
int main()
{
  Family f1,f2;
  cout << "&f1 = " << &f1 << endl;
  cout << "&f2 = " << &f2 << endl;
```
**Syntactical representation**
```c++
  f1.set_data();
  f2.set_data();
  f1.get_data();
  f2.get_data();
}
```
**How it is actually called**
```c++
Family :: set_data( &f1 );
```
**How it is received**
```c++
void set_data( Family *const this){
    cin>> this->cash >> this->gold;
}
```

## How to pass arguments to member functions

```c++
#include<iostream>
using namespace std;
class Family
{
 int cash,gold;
 public:
```
**Member functions / Methods**
```c++
 void set_data(int a,int b){
  cout << "set func:  "<< this << endl;
   this-> cash = a, gold = b;
 }
 void get_data(){
 cout << "get func : " << this << endl;
 cout << this->cash << this->gold <<endl;
 }
};
```
**Non member Function**
```c++
int main()
{
  Family f1,f2;
  cout << "&f1 = " << &f1 << endl;
  cout << "&f2 = " << &f2 << endl;
  f1.set_data(10,20);
  f2.set_data(100,200);
  f1.get_data();
  f2.get_data();
}
```
**Output**
```sh
&f1 = 0x1000
&f2 = 0x2000
```
```sh
set func:  0x1000
set func:  0x2000
```
```sh
get func : 0x1000
10
20
get func : 0x2000
100
200
```
