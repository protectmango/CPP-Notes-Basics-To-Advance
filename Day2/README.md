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