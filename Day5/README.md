# Dynamic Memory Allocation is C++

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
It is a **pointer**, memory is allocated in `stack section`.   
But it is going to point to memory address which is in `heap section`.

