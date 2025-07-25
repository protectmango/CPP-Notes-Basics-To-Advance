# Referance Variable in C++

It is used to provide a **duplicate name** to **existing variable.**

[Rules for Reference Variable](#rules).   
[Reference to Pointer](#reference-to-a-pointer).   
[To check optimised code](#to-check-the-optimized-code).  
[Reference to an array](#reference-to-an-array).   
[Function Return type is reference](#function-return-type-is-reference)

**Syntax**  
```c++
datatype &newname = existing name
```
>[!Important]   
>## **Rules**  
>1. **reference value**  must be initilized.   
>    - **Invalid**    
>    ```c++
>        int &rv;   /*invalid*/
>    ```
>2. No seperate memory is created for **reference variable.**
>3. **Reference variable** cannot refer to another variable.
>4. `NULL` reference is not possible.
>       - **Invalid**   
>       ```c++
>       int &rv = 0;
>       ```
>       - To make is **Valid**
>       ```c++
>       const int &rv = 0;
>       ```   
>5. **Reference variable** can dereference automatically.     
> It is working like **pointer** internally.
>6. No **alias** for constant variable/data. 
>       - **Invalid**   
>       ```c++
>       int &rv = 500;  /*invalid*/
>       ```
>7. **Reference** to **reference** not possible.
>       - **Invalid**   
>       ```c++
>       datatype &&new_name;
>       ```
>       **Example**
>       ```c++
>       int &&rv;        
>       ```
>       **Reference variable** doesn't have seperate memory;    


## Internal working of reference.
**Syntax** 
```c++
datatype &new_name = existing_name
```

### With respect to User
```c++
int x = 10;
int &rv = x;
cout<<rv;
```

### With respect to Compiler
```c++
int x = 10;
int &rv;
    
    rv = &x;
    cout << *rv;
```

## To Check the optimized Code
**Command**
```sh
c++ file.cpp -fdump-tree-gimple
```
Check the output using **ls.**

## Reference to a Pointer
```c++
#include <iostream>
using namespace std;

int main()
{
  int num = 10;
    int* ptr = &num;  // Pointer to 'num'
    int* &refToPtr = ptr;  // Reference to the pointer 'ptr'

    cout << "Original num: " << num << endl;  // 10
    cout << "Pointer value: " << *ptr << endl;  // 10
    cout << "Reference to pointer value: " << *refToPtr << endl;  // 10

    // Modify the value through the reference
    *refToPtr = 20;
    cout << "After modification:" << endl;
    cout << "num: " << num << endl;  // 20
    cout << "*ptr: " << *ptr << endl;  // 20
}
```
**Output**
```sh
Original num: 10
Pointer value: 10
Reference to pointer value: 10
After modification:
num: 20
*ptr: 20
```

>[!Note]
>**Pointer** to **reference** is not possible.   
>**Invalid**
>  ```c++
>   int &*p;    /*invalid*/
>   ```

## Reference to an array
Provide **duplicate** name to an **array**.  
**Syntax**
```c++
datatype (&new_name)[size] = existing_name;
int (&p)[5];
```
> [!WARNING]  
> Array of reference is not possible.   
>**Example**  
>```c++
>int &a[5];
>```


## Function return type is **reference**

```c++
#include<iostream>
using namespace std;
```
**Syntax**
```c++
int& func(){
 static int k=100;
 cout  <<"k value : " <<  k << endl;
 return k;
}
```
```c++
int main() 
{  
  int a=10;
  func()=a;
  func();

}
```
Store value of `a` into `k` **memory location.**
```c++
func()=a;
```
**Ouput**
```sh
k value : 100
```
When we call the function again.
```c++
func();
```
**Output**
```sh
k value : 10
```
>[!Warning]  
> **Invalid**
> ```c++
> #include <iostream>
> using namespace std;
> ```
> ```c++
> int& func(){
> ```
> The memory of the k will be destroyed after execution of function.   
> In main function
> ```c++
> func()=a; /*Will generate error*/
> ```
> >int k=100;
> ```c++
> cout  <<"k value : " <<  k << endl;
> return k;
>}
>```
>```c++
> int main() 
> {  
>  int a=10;
>  func()=a;
>  func();
>}
>```
> **Error**
>```sh
>error: expression is not assignable
>   12 |            func()=a;
>      |            ~~~~~~^
>1 error generated.
>```