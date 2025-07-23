# Namespace

>[!Important] 
>- Namespace is a declarative region used to localize global identifier name to avoid name collision.
>- Namespase create a memory in which various program element can be placed.
>- Element declared in one namespace are seperate from elelment declared in another.
>- Element can be variable, function, classes and template.

### namespace using scope
- **normal method**
    ```c++
    #include<iostream>
    int main()
    {
        int cout=10;
        std::cout<<"Hello"<<std::endl;
        std::cout<<cout<<std::endl;
    } 
    ```
    - Here `std :: cout` and `cout` are different.  
    
    **Output**
    ```sh
    Hello
    10
    ```
- **declarative method**
    ```c++
    #include<iostream>
    using std::cout;
    int main()
    {
        cout<<"it's good"<<std::endl;
        int a;
        std::cin>>a;
        cout<<a<<std::endl;
    }
    ``` 
    - Here we declared `cout` which belong from `std`.

### Case 1 : Multiple declarations of namespace
```c++
#include<iostream>
using namespace std;
namespace A
{
	int a=10;
	void fun()
	{
	cout<<"inside A block"<<endl;
	}
}
namespace B
{
	int a=50;
	void fun()
	{
	cout<<"inside B block"<<endl;
	}

}
int main()
{
    using namespace A;
    using namespace A;
    cout<<a<<endl;
    fun();
}
``` 
**Output**
```sh
10
inside A block
```

## Case 2 : Ambiquity 
```c++
#include<iostream>
using namespace std;
namespace A
{
	int a=10;
	void fun()
	{
	cout<<"inside A block"<<endl;
	}
}
namespace B
{
	int a=50;
	void fun()
	{
	cout<<"inside B block"<<endl;
	}

}
using namespace B;
using namespace A;
int main()
{
    cout<<a;
    fun();
}
```
**Error**
```sh
error: reference to 'a' is ambiguous
   24 | cout<<a;
      |       ^
note: candidate found by name lookup is 'B::a'
   13 |         int a=50;
      |             ^
note: candidate found by name lookup is 'A::a'
    5 |         int a=10;
      |             ^
error: call to 'fun' is ambiguous
   25 | fun();
      | ^~~
note: candidate function
    6 |         void fun()
      |              ^
note: candidate function
   14 |         void fun()
      |              ^
2 errors generated.
```

## Alias name for namespace

**Syntax**
```c++
namespace new_name = old_name;
```
**Example**
```c++
#include<iostream>
using namespace std;
```
```c++
namespace v24be8
{
int x=50;
namespace v24be7
{
int y=30;
} 
}
```
```c++
namespace n= v24be8;
namespace n1= v24be8::v24be7;
using n1::y;
int main()
{
cout<<y<<endl;
}
```
**Output**
```sh
30
```

## Anonymous namespace
```c++
#include <iostream>
using namespace std;

namespace 
{
    int x = 10;
}

int main()
{
    cout << ::x << endl;
}
```
`::x` to access x we directly use `::`.