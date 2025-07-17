# Day 1 : Intro to C++

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


>[!Important].  
>Statement which are `valid in c` but are `invalid in c++`
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