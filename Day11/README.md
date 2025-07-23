# Friend Function
- **Friend Function** is a **non member function** where it can access **private** data of class.   

**Syntax** 
```c++
friend returntype function_name ( argument );
```

**Example**
```c++
#include<iostream>
using namespace std;
class A
{
    int x;
```    
```c++
    friend int main();
```
```c++
    void get();
public:
    void set(int);
};
void A::set(int data)
{
    x=data;
}
void A::get()
{
    cout<<x<<endl;
}

int main()
{
    A ob1;
    ob1.set(20);
    ob1.get();
}
```

- Even though `get()` is a **private** member function we can access it, because `main()` is a **friend** function.   

**Output**
```sh
20
```
## Friend Function conditions
1. Friend function can be friend to `N` number of classes.
2. A class can have `N` number of friend function.
3. Friend function will not have `this` pointer.

### Case 1 : Access private member with object & pointer.

```c++
#include<iostream>
using namespace std;
class A
{
	int x,y;
	friend void add(A);
	friend void sub(A*);
	public:
	void set(int d1,int d2)
	{
		x=d1;
		y=d2;
	}
};
```
Access private member with `object`.
```c++
void add(A t)
{
	cout<<t.x+t.y<<endl;
}
```
Access private member with `pointer`.
```c++
void sub(A *t1)
{
	cout<<(t1->x-t1->y)<<endl;
}
```
```c++
int main()
{
	A o1,o2;
	o1.set(10,20);
	o2.set(4,2);
	add(o1);
	sub(&o2);
}
```
**Output**
```sh
30
2
```

### Case 2 : Forward Declaration of a class. 

```c++
#include<iostream>
using namespace std;
```
**Forward Declaration**
```c++
class B;
```

```c++
class A
{
    int x;
    friend void add(A,B);
public:
    void set_A(int d1)
    {
        x=d1;
    }
};
class B
{
    int y;
    friend void add(A,B);
public:
    void set_B(int d2)
    {
        y=d2;
    }
};
```
```c++
void add(A ao,B bo)
{
    cout<<ao.x+bo.y<<endl;
}
```
```c++
int main()
{
    A aobj;
    B bobj;
    
    aobj.set_A(20);
    bobj.set_B(30);
    add(aobj,bobj);
}
```
**Output**
```sh
50
```

### Case 3 : Class as friend

**Friend class** is a class where one class all the member function can access, all the `private` member of `another` class.


```c++
#include<iostream>
using namespace std;
```
```c++
class B;
```
```c++
class A
{
	int x;
	void display();
	public:
	void set(int d1)
	{
		x=d1;
	}
	friend class B;
};
```
```c++
void A::display()
{
	cout<<x<<endl;
}
```
Access data member of `A` from object `t`.
```c++
class B
{
	public:
		void show(A t)
		{
			t.display();
		}
};
```
```c++
int main()
{
	A aobj;
	aobj.set(20);
	B bobj;
	bobj.show(aobj);
}
```

**Output**
```sh
20
```

### Case 4 : Only a Particular Function of a class as friend.

```c++
#include<iostream>
using namespace std;
class Emp;
class hr
{
public:
    void show_salary(Emp);
};
class Emp
{
    float sal;
public:
    void set(float f)
    {
       sal=f;
    }
```
```c++
    friend void hr::show_salary(Emp);
```
```c++
};
```
```c++
void hr::show_salary(Emp e)
{
    cout<<e.sal<<endl;
}
```
```c++
int main()
{
    hr h;
    Emp eo;
    eo.set(23457.67f);
    h.show_salary(eo);
}
```

**Output**
```sh
23457.67
```

## Difference between Member function & Friend Function

|Member Function|Friend Function|
|---|---|
|Member function belong to same class|Friend Function not belong to class|
|Will have `this` pointer|Will **not** have `this` pointer|
|Member function invoke through object|Friend function invoke without object.|
|Member function can access member of class without object|Friend function access member of the class with object|
