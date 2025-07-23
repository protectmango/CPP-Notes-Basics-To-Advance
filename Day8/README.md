# Data Types
**New Data type** in C++, which are not in C.
- [**wchar_t**](#wchar_t)
- [**bool**](#bool)
- [**string**](#string)

## wchar_t
- **wchar_t** is used to print wide range of character.
- **wchar_t** store **unicode** char | universal char **[`international language`]**.
- **Size of wchar_t** depend on `compiler` and `operating system`.
    - 16 bit → 2 byte.
    - 32/64 bit → 4 byte.
    ```c++
        wchar_t ch;
        cout<<sizeof(ch)<<endl;
    ```
    **Output**
    ```sh
    4
    ```
- **wchar_t** represent with **L**, here **L** mean `string constant`/ `literal character`.
- To scan and print
    - `wcin` to scan data.
    - `wcout` to print data.
- By default cout will give **ascii** value.
- **wchar_t** will support `signed`/`unsigned` depend on compiler.

```c++
wchar_t ch;
count << sizeof (ch) << endl;
```
**Output**
```sh
4
```
>[!Note]  
>**Default** value of **wchar_t** variable is `0`.
- ### To scan and print 
    ```c++
    wchar_t ch;
    wcin >> ch;
    cout << ch << endl;
    wcout << ch << end;
    ```

    **Input**
    ```sh
    a
    ```
    **Output**   
    - **cout** << ch << endl;  
    ```sh
    97
    ```
    - **wcout** << ch << endl;
    ```sh
    a
    ```

- ### Initialization of wchar_t
    ```c++
    wchar_t ch[] = L"Vector";
    wcout << ch << endl;
    ```
    >[!Note]  
    > **L"Vector"** ,   
    > here `L` is mandatory  

- ### To print a special character
    ```c++ 
    #include<iostream>
    using namespace std;
    int main()
    {
    wchar_t ch[2]={0x0c85,0x0270A};
    setlocale(LC_ALL,"");
    wcout<<ch[0]<<" "<<ch[1]<<endl;
    }
    ```
    **Output**
    ```sh
    ಅ ✊
    ```

## bool
- to store logical value `0/1`.
- **size** of bool is **1 byte**.
- bool data type will not support any qualifier.
    - signed / unsigned / long / short not **supported**.
- bool means boolean expression.
```c++
bool x = 10;
```
Binary in x is `0000 0001`. Not `0000 1010`.
- ### Why size of bool is 1 byte not 1 bit ?
In any programming language to store `0` or `1` memory formation is done in **byte** format, not in bit format. As assigning memory in byte is faster and easier.
```c++
cout << sizeof(x) << endl;
```
**Output**
```sh
1
```

- **Default** value is `0`.
```c++
cout << x << endl;
```
**Output**
```sh
0
```

### **Case 1**
```c++
#include<iostream>
using namespace std;
int main()
{
bool b=256;
bool c=0;
cout<< sizeof(b) <<" "<< b <<endl;
cout<< sizeof(c) <<" "<< c <<endl;
}
```
**Ouput**
```sh
1 1
1 0
```

### **Case 2**
```c++
#include<iostream>
using namespace std;
int main()
{
bool b="true";
bool c="false";
cout<<sizeof(b)<<" "<<b<<endl;
cout<<sizeof(c)<<" "<<c<<endl;
}
```
**Ouput**
```sh
1 1
1 1
```
### **Case 3**
```c++
#include<iostream>
using namespace std;
int main()
{
bool b=True;
bool c=False;
cout<<sizeof(b)<<" "<<b<<endl;
cout<<sizeof(c)<<" "<<c<<endl;
}
```
**Error**
```sh
data8.cpp:5:8: error: use of undeclared identifier 'True'; did you mean 'true'?
    5 | bool b=True;
      |        ^~~~
      |        true
data8.cpp:6:8: error: use of undeclared identifier 'False'; did you mean 'false'?
    6 | bool c=False;
      |        ^~~~~
      |        false
2 errors generated.
```
### WAP to check a number is even or odd
```c++
#include<iostream>
using namespace std;
bool fun(int n)
{
	if (n%2==0)
		return 1;
	else
		return 0;
}
int main()
{
	bool res;
	res=fun(20);
	cout<<res<<endl;
}}
```
## String 
**It is a class.**
- collection of char / set of char.
- ending with `\0`.
- size of string depend on compiler.
- according to compiler string is a **class**.

- ### Size of string
```c++
#include<iostream>
using namespace std;
int main()
{
	string s;
	cout<<sizeof(s)<<endl;
}
```
**Output** on Ubuntu OS
```sh
32
```
**Output** on Mac OS
```sh
24
```

### Case 1
```c++
#include<iostream>
using namespace std;
int main()
{
    string s="hello vector";
    cout<<sizeof(s)<<endl;
    cout<<s<<endl;
}
```
**Output** on Ubuntu OS
```sh
32
hello vector
```
**Output** on Mac OS
```sh
24
hello vector
```

### How to find the size and length of the string ?

```c++
#include<iostream>
using namespace std;
int main()
{
    string s="hello vector";
    cout<<s.size()<<endl;
    cout<<s.length()<<endl;
    cout<<s<<endl;
}
```
**Output**
```sh
12
12
hello vector
```

### Concate two strings

```c++
#include<iostream>
using namespace std;
int main()
{
	string s="hello",s1="vector";
	cout<<s1+s<<endl;
}
```
**Output**
```sh
hellovector
```
### Copy two strings
```c++
#include<iostream>
using namespace std;
int main()
{
	string s="hello",s1;
    s1 = s;
	cout<<s1<<endl;
}
```
**Output**
```sh
hello
```

### Comparing two strings
```c++
#include<iostream>
using namespace std;
int main()
{
	string s1="hello",s2= "HELLO";
    bool res;
    res = s1==s2;
	cout<< res <<endl;
}
```
