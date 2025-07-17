# Referance Variable in C++

It is used to provide a **duplicate name** to **existing variable.**

**Syntax**  
```c++
datatype &newname = existing name
```
>[!Important]   
>**Rules**  
>1. **reference value**  must be initilized.   
>    - **Invalid**    
>    ```c++
>        int &rv;   /*invalid*/
>    ```
>2. No seperate memory is created for **reference variable.**
>3. **Reference variable** cannot refer to another variable.
>4. `NULL` reference is not possible.
>       - **Invalid**   
>       ```c++
>       int &rv = 0;
>       ```
>       - To make is **Valid**
>       ```c++
>       const int &rv = 0;
>       ```   
>5. **Reference variable** can dereference automatically.
> > [!Note]      
> > It is working like **pointer** internally.
>6. No **alias** for constant variable/data. 
>       - **Invalid**   
>       ```c++
>       int &rv = 500;  /*invalid*/
>       ```
>7. **Reference** to **reference** not possible.
>       - **Invalid**   
>       ```c++
>       datatype &&new_name;
>       ```
>       **Example**
>       ```c++
>       int &&rv;        
>       ```
> > [!Note]   
> >**Reference variable** doesn't have seperate memory;    