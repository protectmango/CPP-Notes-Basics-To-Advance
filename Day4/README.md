# Call By " Value | Address | Reference "

Passing argument to a **function**.    
- [Call By Value](#call-by-value)
- Call By Address
- Call By Reference

## Call By Value
**Variable passed** to the function at the time of calling is **not affected** by the changes/operation done within the function
```c++
#include<iostream>
using namespace std;

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

int main()
{

    int a = 10 , b = 20;

    /*Call By Reference*/
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