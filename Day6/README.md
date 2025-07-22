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
```arm
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
>Size of structure variable depends on the datamember only.   
>Function are not included.   
>If no data memeber are there   
>    - Then **default size** will be `1` , for the variable existance. 
>    - To access member functions.

By Default **access specifier** in structure is **public**.   
    - we can hide the data using keyword `private`.