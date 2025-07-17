# Operator in C++

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

## Scope Resolution ::
