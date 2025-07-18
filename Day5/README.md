# Dynamic Memory Allocation in C++

>[!Note]
> Operator for allocating memory.   
- `new` operator → allocating memory.  
- `delete` operator → deleting/free memory.

>How memory is allocated by compiler?

- **Statically**  

    ```c++
    int a;
    char ch[10];
    float f[2];
    ```
    - **Compile Time** : memory decided  
        a  → `4`  byte.  
        ch → `10` byte.  
        f  → `8`  byte.  
    - **Load Time** : Load into `RAM` for execution.
    - **Run Time** : Memory reserved, Memory accessed.

>[!Important]  
> Problem with Statically allocated memory.  
- memory either `wasted/insufficient`.  
To Avoid this problem we alloct memory **Dynamically**.
- **Dynamically**  
    Using either `malloc()` or `calloc()`.

    ```c++
    int n;

    scan("%d", &n);

    int *p = malloc(sizeof( int ) * n );
    ```
    - **Compile Time** : memory decided for n → `4` byte.
    - **Load Time** : Program loaded to `RAM` for execution.
    - **Run Time**   
        - Memory Decided.
        - Memory Reserved.
        - Memory Accessed.

**Using malloc() in C++**  
Allocating memory using malloc(), calloc(), and free the memory using free().

```c++
#include <iostream>
```
> Must include 
```c++
#include <cstdlib>
```
```c++
using namespace std();
```
```c++ 
int main()
{
    int *p;

    p = (int * ) malloc(sizeof( p ));
    cout << "Data" << endl;
    cin >> *p;
    cout << "Data" << *p << endl;
    free(p);
}
```
> Where memory is allocted for p?   
- It is a **pointer**, memory is allocated in `stack section`.   
- But it is going to point to memory address which is in `heap section`.

## Dynamic Memory allocation using `new` operator.

**Syntax**
```c++
int *p;
p = new int;
```
**Advantages**  
- `sizeof()` operator **not required**.
- `typecasting` **not required**.
- `new` is **operator**.
- `return` exact pointer.
> In `C` **void *  pointer** is returned from `malloc()` and `calloc()`.   
>[!Note]  
> In `C++` `new` return **int * pointer**. 

## Initialization of Dynamically Allocated  Memory

```c++
int *p;
*p = new int(35);
```
**int(35)** here `(` `)` are used to **initilize** the memory.  
- **memory allocation** + **valid data storing**
```c++
cout << "*p : " << *p <<endl;
delete p;
```
**delete** to `free` the dynamically allocated memory.  

**Output**
```sh
*p : 35
```

## Dynamic Memory Allocation for array in C++

### Allocation
```c++
p = new int[5];
```
**int[5]** here `[` `]` are used to allocate `5` elements.

### Deallocation
```c++
delete []p;
```
**[ ] p** here `[` `]` are used previous to `p` to deallocate all element. 

>[!Note]
>| p = new int(5);|p = new int[5];|
>|---|---|
>|`4` byte allocated initialised with `5`.|`20` byte allocated initilised with `0`.|

### Initilisation of array in C++
```c++
int *p;
p = new int[5]{10, 20, 30, 40, 50};
```
`p[0]` : `10`  
`p[1]` : `20`  
`p[2]` : `30`  
`p[3]` : `40`  
`p[4]` : `50`  

## Dynamic Memory Allocation for 2D array in C++

### Allocation
```c++
int **p, i, j;
p = new int * [3]; /*No of rows*/

for (i=0; i< 3; i++)
{
    p[i] = new int[4]; /*No of column*/
}
```
**Scan** the data.
```c++
for (i=0; i< 3; i++)
{
    for(j=0; j< 4; j++)
    {
        cin >> p[i][j];
    }
}
```
**Print** the data.
```c++
for (i=0; i< 3; i++)
{
    for(j=0; j< 4; j++)
    {
        cout << p[i][j] <<endl;
    }
}
```

### Deallocation
```c++
for (i=0; i< 4; i++)
{
    delete []p[i];
}
delete []p; 
```
