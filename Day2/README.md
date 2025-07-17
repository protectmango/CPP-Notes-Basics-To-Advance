# Operator in C++

[Printing Hex, Oct, Dec, in C++](#printing-hex-octal-decimal-in-c).  
[Reading Hex, Oct, Dec, in C++](#reading-hex-oct-dec-in-c).  
[Read ASCII of a character in C++](#read-ascii-of-a-character).  
[Print float values](#how-to-print-float-value)
[Using printf() in C++](#using-printf-in-a-c-programm)
[Scope Resolution](#scope-resolution--)

```c++
#include<iostream>
using namespace std;
int main()
{
 int x;
 cout << "enter x value" << endl;
 cin >> x;
 cout << " x value: " << x << endl;
}
```
Insertion  : `<<`   
Extraction : `>>`.  

**Input**
```sh
enter x value
10
```
**Ouput**
```sh
x value: 10
```

## Printing Hex, Octal, Decimal in C++

```c++
#include<iostream>
using namespace std;
int main()
{
 int x;
 cout << showbase << uppercase << showpos;
 cout << "enter x value" << endl;
 cin >> x;
 cout << "Decimal value: " << x << endl;
 cout << "Octal value: " << oct << x << endl;
 cout << "Hexadecimal : " << hex << x <<  endl;
}
```

**Input**
```sh
enter x value
10
```
**Ouput**
```sh
Decimal value: +10
Octal value: 012
Hexadecimal: 0XA
```

**showbase** to show the base (hex, oct, dec)  
**showpos** to show +ve or -ve.   

>To disable these flag

```c++
cout << noshowbase << nouppercase << noshowpos; /*deactivated*/
```

## Reading Hex, Oct, Dec in C++

```c++
#include<iostream>
using namespace std;

int main()
{
    /*Hexadecimal*/
    int x;
    cin>>hex>>x;

    /*Octal*/
    int y;
    cin>>oct>>y;

    /*Decimal*/
    int x;
    cin>>x;
}
```

## Read ASCII of a character

```c++
#include<iostream>
using namespace std;
int main()
{
 char ch;
 cout << "enter char" << endl;
 cin >> ch;
 cout << "charcater: " << ch << endl;
 cout << "ASCII: " << (int)ch << endl;
}
```

**Input**
```sh
enter char
a
```
**Ouput**
```sh
character: a
ASCII: 97
```

## How to print `float` value

```c++
#include<iostream>
using namespace std;
int main()
{
    float f;
    cout << "enter float" << endl;
    cin >> f;
    cout << "float : "<< f << endl; /*%g*/
    cout << "fixed : " << fixed << f << endl; /*%f after.6digits*/
    cout << "scientific : " << scientific  << f << endl; /*%e exponetial*/
}
```

**Input**
```sh
enter float
23.5
```

**Output**
```sh
float : 23.5
fixed : 23.500000
scienctific : 2.350000e+01
``` 

>To deactivate these flag
>   ```c++
>   cout<<defaultfloat<<f<<endl;
>   ```

## Using `printf()` in a `c++` programm.

>must include `<cstdio>` to use `printf()` and `scanf()`

```c++
#include<iostream>
#include<cstdio>
using namespace std;
int main()
{
 int x;
 printf("enter x\n");
 scanf("%d",&x);
 printf("%d %#o %#x \n",x,x,x);
}
```

## Scope Resolution : :

To access **local** and **global** variable with same name in **main()**.

```c++
#include<iostream>
using namespace std;
int x=100;
int main()
{
 int x=10;
 cout << "local x :" << x << endl;
 cout << "global x : " << ::x << endl;
}
```
**Output**
```sh
local x : 10
global x : 100
```

>[!CAUTION]  
>**Invalid Code**
>```cpp
>#include<iostream>
>using namespace std;
>int main()
>{
> int x=10;
> cout << "local x :" << x << endl;
>
> /* invalid ,x not declared */
> cout << "global x : " << ::x << endl; 
>}
>```
>**Error**
>```sh
>error: no member named 'x' in the global namespace; did you mean simply 'x'?
>    7 |  cout << "global x : " << ::x << endl; // invalid ,x not declared
>```


>[!WARNING]   
>**: :** It will always refer to global variable which is outside the main()
>```c++
>#include<iostream>
>using namespace std;
>int x=100;
>int main()
>{
> int x=10;
> {
>  int x=1000;
>  cout << "local x :" << x << endl;
>  cout << "global x : " << ::x << endl;
> }
>
>}
>```
>**Output**
>```sh
>local x : 1000
>global x : 100
>```
