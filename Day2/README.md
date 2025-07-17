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