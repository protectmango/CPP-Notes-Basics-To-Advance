# Data Types
**New Data type** in C++, which are not in C.
- **wchar_t**
- **bool**
- **string**

## wchar_t
- **wchar_t** is used to print wide range of character.
- **wchar_t** store **unicode** char | universal char **[`international language`]**.
- **Size of wchar_t** depend on `compiler` and `operating system`.
    - 16 bit → 2 byte.
    - 32/64 bit → 4 byte.
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