# Inline Function And Structure in C++

## Inline Function 

A function Call is going to replace with function defination.   
Use keyword **inline**.
>[!Note]   
> It completely depends on the compiler that it will replace it or not.

**Syntax**  
```c++
inline return_type function_name(arguments) {
    /*Statements*/
}
```

**Example**
```c++
#include<iostream>
using namespace std;
inline void func(){
 cout << "hello world" << endl;
 cout << "welcome to  inline " << endl;
}
int main() 
{  
  func();
}
```

**inline.s** file
```c++
	.file	"inline.cpp"
	.text
	.section	.text._ZNKSt5ctypeIcE8do_widenEc,"axG",@progbits,_ZNKSt5ctypeIcE8do_widenEc,comdat
	.align 2
	.p2align 4,,15
	.weak	_ZNKSt5ctypeIcE8do_widenEc
	.type	_ZNKSt5ctypeIcE8do_widenEc, @function
_ZNKSt5ctypeIcE8do_widenEc:
.LFB1321:
	.cfi_startproc
	movl	%esi, %eax
	ret
	.cfi_endproc
.LFE1321:
	.size	_ZNKSt5ctypeIcE8do_widenEc, .-_ZNKSt5ctypeIcE8do_widenEc
	.section	.rodata._Z4funcv.str1.1,"aMS",@progbits,1
.LC0:
	.string	"hello world"
.LC1:
	.string	"welcome to  inline "
	.section	.text._Z4funcv,"axG",@progbits,_Z4funcv,comdat
	.p2align 4,,15
	.weak	_Z4funcv
	.type	_Z4funcv, @function

```
  
# Structure in C++

Structure is a **user defined datatype** to store different type of **data member** as well as **member function** in contigineous memory location.


```c++
struct Student {
    int id;
    char name[20];
    void fun()
    {
        /*Statements*/
    }
}; 
```

>[!Warning]   
> **Invalid Syntax**
> ```c++
> struct Student {
>    auto int a = 10;
>    extern int b = 20;
>};
> ```
> - Should not provide any **storage classs**.
> - Should not **initilize** any variable.

When **variable is created** then **memory is allocated**.

>[!Important]  
> **Access Variable** using ` . ` operator.   
> **Access Pointer** using ` -> ` operator.


>[!Note]   
>**Size** of `structure variable` depends on the **data member** only.   
>**Function** are not included.   
>If no data memeber are there   
>    - Then **default size** will be `1` , for the variable existance. 
>    - To access member functions.

By Default **access specifier** in structure is **public**.   
    - we can hide the data using keyword `private`.


```c++
#include<iostream>
using namespace std;
struct Family
{
```
**Data members / Attributes**
```c++
private:
 int cash,gold;
```
**Member functions / Methods**
```c++
 public:
 void set_data(){
  cout << "enter cash and gold" << endl;
  cin >> cash >>gold;
 }
 void get_data(){
  cout << cash << " " << gold << endl;
 }
};
```
**Non Member Function**
```c++
int main() 
{  
  Family f;
```
To access member function `.` operator is needed.
```c++
  f.set_data();
  f.get_data();
```
>[!Warning]  
>**private** data can't access directly
```c++
    f.cash=10; 
    f.gold=20;
    cout << f.cash << " "<< f.gold << endl;
}
```
### Size of a structure variable.

```c++
#include<stdio.h>
struct st
{
 int x;
 char ch;

};
int main()
{
 struct st s;
```
**Using sizeof()** from C
```c++
 printf("%ld\n",sizeof (struct st));
```
**sizeof object** in C++
```c++
 printf("%ld\n",sizeof s);
 
}
```
**Output**
```sh
8
8
```

## Size of a structure without Data member.

```c++
#include<stdio.h>
struct st
{
public:
 void print()
 {
	 printf("Hello");
 }
};
int main()
{
 struct st s;
 printf("%d\n",sizeof s);
}
```
**Output**
```sh
1
```
>[!Note]  
>The size of a structure variable will be `1`, to prove the existance of a variable and to access the member functions of that structure.