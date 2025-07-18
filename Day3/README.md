# Referance Variable in C++

It is used to provide a **duplicate name** to **existing variable.**

[Rules for Reference Variable](#rules).   
[Reference to Pointer](#reference-to-pointer).   
[To check optimised code](#to-check-the-optimized-code).  
[Reference to an array](#reference-to-an-array).   
[Function Return typpe is reference](#function-return-type-is-reference)

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


## Reference to Pointer
Providing duplicate name to a pointer.   
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
