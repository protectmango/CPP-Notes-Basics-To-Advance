# Day 1 : Intro to C++

##  C++ → ` c + 1 `  
>**C Concepts** + ` EXTRA `   

**C Concepts**

- Datatype
- Operator
- Control Statements
- Array
- Pointer
- Functions
- Recursion
- Preprocessor
- File
- Command Line Argument
- Dynamic Memory Allocation

>**Extra** : Support Object Oriented Programming. 

- Provide duplicate name to existing variable.
- Use operator to allocate dynamic memory.
- Impleement 'n' no of function using same name.
- Write function defination in structure.
- Access local and global variable same time of same name.
- Creating blocks for global variable.

## What is a Object ?

>[!NOTE]   
>*Understanding purpose only*   
>**Object** is a **variable**

Creating N no of variable to complete the task is called **Object Oriented Programming**.  

>**C :**  Functional Oriented.  
>`printf(), scanf(), fscanf(), fprintf()`  

>**C++ :** Object Oriented.
>`cin, cout, fin, fout` 

## Object : Function + Data
>**Function** : Procedure/Method/Code   
>**Data** : attribute/fields

```c
struct Student{
    int rollno;
    char name[20];
    float marks;
    void scan()
    {

    }
    void display()
    {

    }

};

int main()
{
    /*Object Declaration*/
    struct Student S;

}
```