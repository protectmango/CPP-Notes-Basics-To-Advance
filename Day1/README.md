# Day 1 : Intro to C++

[What is a Object ?](#what-is-a-object-).   
[Concept in OOPS](#concept-in-object-oriented-programming).   
[Basic Syntax](#basic-code-syntax-in-c).   
[How to compile c++ code ?](#how-to-compile-c-code).  


>[!Note]  
>##  C++ → ` c + 1 `  
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
        /*---Statement---*/
    }
    void display()
    {
        /*---Statement---*/
    }

};

int main()
{
    /*Object Declaration*/
    struct Student S;

}
```

## Concept in Object Oriented Programming
- **Inheritance**
    - Acquring properties from one to another.
    - **Advantage**
        - Code Re-usability
        - Extensiblity
- **Encapsulation**
    - Writing the data and function together.

    ```c++
    class Family{
        int gold;
        int cash;
        void Person1();
    };
    ```
- **Abstraction**
    - Hide the data and restricting the access. Using **Access Specifer.**

    - **Access Specifier**
        - Private
        - Protected
        - Public

    ```c++
    class Student{
        private :
                    /*Private Member*/
        protected : 
                    /*Protected Member*/
        public : 
                    /*Public Member*/

    };
    ```
- **Polymorphism**
    > **Poly** → **Many**   
    > **Morphoism** → **Creation**

    - Advantages   
        - Flexibility   
        - Single Entity exist more than one form

    - Compile Time 
        - Function Overloading
        - Operator Overloading
    
    - Run Time 
        - Virtual Function


    **Function Binding** : Resolving a function call with its proper function defination.  
    - Static/Early Binding     
        If function binding happen at **compile time** called **compile time function binding**  also known as **static binding / early binding**
    - Dynamic/Late Binding   
        If function binding happen at **runtime** called **runtime binding*** also known as **dynamic/late binding**


> [!IMPORTANT]  
>Statement which are `valid in c` but are `invalid in c++`.   
>   **Case : 1**
>    ```c++
>   int x;
>   char *p= &x;    /*invalid in c++*/
>   ```
>  **C++** is has **strict type checking**.   
>   
>  **Valid Code**
>   ```c++
>   int x;
>   char *p = (char *)&x;
>   ```
>   **Case : 2**
>   ```c++
>   const int x=10;
>   int *p;
>   p = &x; /*invalide in c++*/
>   *p = 30;
>   ```
>   
>   **Valid Code**
>   ```c++
>   const int x = 10;    
>   const int *p = &x;
>   ```

## Basic Code Syntax in C++

**Headerfile**
```c++
    #include<iostream>
```
**namespace**
```c++
    using namespace std;
```
**main()**
```c++
int main()
{
    cout<< "Hello Brother" << endl;
    cout<< "Basic Syntax For C++"<<endl;
    int x;
    cin>>x;
    cout<< "x value : "<< x <<endl;
}
```
- **cout** object of `ostream` class.
- **cin** object of `istream` class.
- **<<**  insertion operator
- **>>**  extraction operator
- **endl** for new line

`cout` → `"x value : "` → `x` → `endl`;

## How to compile c++ code

```sh
g++ filename.cpp
```
**or**
```sh
c++ filename.cpp
```