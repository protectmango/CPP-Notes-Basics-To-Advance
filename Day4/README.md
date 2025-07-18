# Call By " Value | Address | Reference "

Passing argument to a **function**.    
- [Call By Value](#call-by-value)
- [Call By Address](#call-by-address)
- [Call By Reference](#call-by-reference)
- [Reference vs Pointer](#reference-vs-pointer)
## Call By Value
**Variable passed** to the function at the time of calling is **not affected** by the changes/operation done within the function
```c++
#include<iostream>
using namespace std;
```
```c++
void swap_data( int a , int b )
{
    int t;
    t = a;
    a = b;
    b = t;

    cout << "Inside Swap() " <<endl;
    cout << "a : " << a << endl;
    cout << "b : " << b << endl;
}
```
```c++
int main()
{

    int a = 10 , b = 20;

    /*Call By Value*/
    swap_data( a, b);

    cout << "Inside Main()" <<endl;
    cout << "a : " << a << endl;
    cout << "b : " << b << endl;
   
}
```

**Output**
```sh
Inside Swap()
a : 20
b : 10
Inside Main()
a : 10
b : 20
```


## Call By Address 
Variable passed at the time of calling will be affected.   
- Must use `&` operator before variable name.
- Used `*` **Pointer** to receive the variable.   

>[!Note]  
> **8 byte** of memory is allocated to each pointer variable.   

```c++
#include <iostream>
using namespace std;
```
```c++
void swap_data( int *a , int *b )
{
    int t;
    t = *a;
    *a = *b;
    *b = t;

    cout << "Inside Swap() " <<endl;
    cout << "a : " << *a << endl;
    cout << "b : " << *b << endl;
}
```
```c++
int main()
{

    int a = 10 , b = 20;

    /*Call By Address*/
    swap_data( &a, &b);

    cout << "Inside Main()" <<endl;
    cout << "a : " << a << endl;
    cout << "b : " << b << endl;
   
}

```
**Output**
```sh
Inside Swap()
a : 20
b : 10 
Inside Main()
a : 20
b : 10
```

## Call By Reference 
Work on the **same variable memory** which is passed as attribute.    
>[!Warning]   
> We should not pass **constants** at function call.
> ```c++
>  fun(10);
> ```
**Advantage**  
- No extra **8 byte** memory is needed.
```c++
#include <iostream>
using namespace std;
```
```c++
void swap_data( int &a , int &b )
{
    int t;
    t = a;
    a = b;
    b = t;

    cout << "Inside Swap() " <<endl;
    cout << "a : " << a << endl;
    cout << "b : " << b << endl;
}
```
```c++
int main()
{

    int a = 10 , b = 20;

    /*Call By Reference*/
    swap_data( a, b);

    cout << "Inside Main()" <<endl;
    cout << "a : " << a << endl;
    cout << "b : " << b << endl;
   
}

```
**Output**
```sh
Inside Swap()
a : 20
b : 10 
Inside Main()
a : 20
b : 10
```
## Reference vs Pointer 

|Reference|Pointer|
|---|---|
|- Reference variable must be initilized.|- Pointer may or may not be initialized.|
|- Null Reference not possible.|- Null pointer possible.|
|- Reference variable cannot point to another variable.|- Pointer can point to any variable at any time.|
|- Will not get seperate memory.|- Seperate memory of 8 byte is assign to the variable.|
|- Reference variable get dereference implicitly.|- Pointer should be dereference explicitly.|
|- Reference to Reference not possible.|- Pointer to Pointer is possible.|