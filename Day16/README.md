# Operator Overloading

- By using **Operator Overloading** we are not creating a new operator , we are adding extra feature to the existing **operator**, So that is can work on user defined datatype.

>[!Note]   
> All the operator `+` , `-` , `/` , `*`,`()`, `[]` work for predefined datatype only, not user defined datatype.

- Only `=` can be used to for user defined function.

## Why use Operator Overloading ?

```c
struct st obj1, obj2, obj3;

obj3 = obj1 + obj2; /*invalid*/
```
- But, It work for predefined datatype.
```c
int a=10, b=20, c;
c = a+b;
```
- Similarly, for `char`, `float` and `double`.

The facility to give special meaning to an operator, without changing the existing meaning is referred to as **Operator Overloading**.

## How to Overload a Operator ?

- A operator can be overloaded by creating a special function called **Operator Function**, which describes the task.

**Syntax**

- As a **Member Function**

```c++
return_type classname :: operator op ( arg ...)
{
    /*Statement*/
}
```

- As a **Friend Function**

```c++
return_type opeartor op (arg &, ...);
```

## Assignment `=` operator

```c++
#include<iostream>
using namespace std;
class A
{
 int x,y;
 public:	
 	A():x(0),y(0){}
 	A(int a,int b):x(a),y(b){}
 	void get_data(){
 	 cout << x << " " << y << endl;
 	}
 	A  operator =(A t){
 	cout << "= operator" << endl;
 	 x=t.x;
 	 y=t.y;
 	 return *this;
 	}
};
int main() 
{  
  A obj1(10,20),obj2,obj3;
  obj3=obj2=obj1; /// obj2.opeartor=(obj1)
  obj2.get_data(); 
  obj3.get_data();
} 
```

## Binary `+` Operator

- As member function

```c++
#include <iostream>
using namespace std;

class A
{
    int x, y;

    public :
    A():x(0), y(0){
    }

    A(int a, int b) : x(a) , y(b) {}

    A operator + (A &obj)
    {
        A sum;

        sum.x = x + obj.x;
        sum.y = y + obj.y;

        return sum;
    }

    void get_data()
    {
        cout<< "x : "<<x << " y : " << y << endl;
    }
};

int main()
{
    A obj1(10,20), obj2(11,22), obj3;

    obj3 = obj1 + obj2; /*obj1.operator + (obj2) as member function*/

    obj3.get_data();
}
```

- As Friend Function

```c++
#include <iostream>
using namespace std;
class A
{
    int x,y;
    public :
    A():x(0), y(0) {}
    A(int a, int b): x(a), y(b) {}

    void get_data()
    {
        cout << "x : " << x << " y :" << y << endl;
    }

    friend A operator + (A & , A &);
};

A operator + (A &obj1, A &obj2)
{
    cout<< "+ Operator Friend Function"<<endl;
    A sum;
    
    sum.x = obj1.x + obj2.x;

    sum.y = obj1.y + obj2.y;

    return sum;
}

int main()
{
    A obj1(10,20), obj2(11,22), obj3;

    obj3 = obj1 + obj2; /*obj3 = operator + (obj1, obj2); As a friend functino */

    obj3.get_data();
}
```

- 5 Object Addition

- Using Member Function
```c++
int main()
{
    A obj1(10,20), obj2(11,22), obj3(12,24), obj4(13,12), obj5;

    obj5 = obj1 + obj2 + obj3 + obj4;
    /*
    obj5 = obj1.operator + (obj2) + obj3 + obj4;
    obj5 = sum + obj3 + obj4;
    obj5 = sum.operator + (obj3) + obj4;
    obj5 = sum + obj4;
    obj5 = sum.operator + (obj4);
    obj5 = sum;
    */

    obj5.get_data();
}
```
- Using Friend Function
```c++
int main()
{
    A obj1(10,20), obj2(11,22), obj3(12,24), obj4(13,12), obj5;

    obj5 = obj1 + obj2 + obj3 + obj4;
    /*
    obj5 = operator + (obj1,obj2) + obj3 + obj4;
    obj5 = sum + obj3 + obj4;
    obj5 = operator + (sum,obj3) + obj4;
    obj5 = sum + obj4;
    obj5 = operator + (sum,obj4);
    obj5 = sum;
    */

    obj5.get_data();
}
```

## Unary `-` Operator

```c++
#include<iostream>
using namespace std;
class A
{
    int x, y;
    public :
    A():x(0), y(0) {}

    A(int a,int b):x(a),y(b) {}

    A operator - ();

    void get_data();
};

A A::operator - ()
{
    cout << "- Operator function" << endl;
    A temp;

    temp.x = -x;
    temp.y = -y;
    return temp;
}

void A:: get_data()
{
    cout << "x : " << x << " y : "<<y << endl;
}

int main()
{
    A obj1(10,20), obj2;
    obj2 = -obj1;

    /* obj2 = obj1.operator -(); */
    obj2.get_data();
}
```
- As Friend Function

```c++
#include<iostream>
using namespace std;

class A
{
    int x, y;
    public : 
            A():x(0), y(0) {}

            A(int a, int b): x(a), y(b) {}

            friend A operator - (A &);
};

A operator - (A &obj)
{
    cout << "Operator function"<< endl;

    A temp;

    temp.x = -obj.x;
    temp.y = -obj.y;

    return temp;
}

int main()
{
    A obj1(10,20), obj2;
    obj2= -obj1;    /*operator -(obj1)*/
    obj2.get_data();
}
```

## Unary `++` Operator

```c++
#include<iostream>
using namespace std;

class A
{
    int x, y;
    public :
    A():x(0), y(0) {}

    A(int a, int b): x(0), y(0) {}

    A operator ++ (); // per - fix

    A operator ++ (int); // post - fix

    void get_data();
}

A A::operator ++ ()
{
    cout<<"Prefix operator function"<< endl;
    
    A temp;
    temp.x = ++x;
    temp.y = ++y;

    return temp;
}

A A::operator ++ (int)
{
    cout<<"Postfix operator function"<<endl;

    A temp;
    temp.x = x++;
    temp.y = y++;

    return temp;
}

void A::get_data()
{
    cout<<"x : "<< x << " y : "<<y << endl;
}

int main()
{
    A obj1(10,20), obj2;

    obj2= ++obj1; /* obj2 = obj1.operator ++() */

    cout << "obj1 data"<< endl;
    obj1.get_data();
    
    cout<<"obj2 data"<< endl;
    obj2.get_data();

    obj2 = obj1++; /*obj2 = obj1.operator ++(int);*/

     cout << "obj1 data"<< endl;
    obj1.get_data();
    
    cout<<"obj2 data"<< endl;
    obj2.get_data();
}
```
### List of operator that can be overloaded
|Operation Name|Operator|
|---|---|
|Binary Arithmetic|+, -, /, *, %|
|Unary Arithmetic|+, -, ++, --|
|Assignment|=, +=, *=, /=, -=, %=, &=, ^=|
|Bitwise|`&`, OR, `!` , `>>` , `<<`, `~`, `^`|
|Dereferencing|->|
|Dynamic memory| new , delete|
|Subscript|[]|
|Function Call|()|
|Logical|&&, ||, !|
|Relational|>, <, ==, !=, <= , >=|
|Others|>>=, <<=|

### Operator can be overloaded by member function only

|Operation Name|Operator|
|---|---|
|Assignment|=|
|Function Call|()|
|Subscript|[]|
|Arrow|->|

#### Assignment Operator `=`

```c++
#include<iostream>
using namespace std;

class A
{
    int x,y;
    public :
    A():x(0),y(0) {}

    void operator = (A &obj)
    {
        cout <<"Assignment Operator"<< endl;
        x = obj.x;
        y = obj.y;
    }

    void get_data()
    {
        cout<<"x : "<< x<< "y = "<<y<< endl;
    }
};

int main()
{
    A obj1(10,20), obj2;

    obj2= obj1; /*obj2.operator = (obj1)*/
    obj2.get_data();
}
```
>[!Note]  
> Using friend funciton then give a **Error** because void operator = (A &, A &) must be a non static member function.

##### Why `=` operator can't be overloaded with friend function ?

- When we don't define the member function for `=` operator, then compiler will supply the default assignment overloaded function, and if we define the friend function then it becomes ambiquity for compiler.

