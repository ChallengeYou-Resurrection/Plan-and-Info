# Code Style

Please follow this code style when contributing to C++ projects 


1. [Naming Conventions](#naming)
    1. [Files and Folders](#files)
    2. [Variables and Constants](#variables)
    3. [Misc](#misc)
2. [Functions and Scopes](#functions)
3. [Classes](#classes)
4. [Includes](#includes)
5. [Constants](#constants)
6. [Pointers](#pointers)
    1. [Non-Owning](#ptr-nonown)
    2. [Owning](ptr-own)

## Naming Conventions <div id = "naming">
### Files and Folders<div id = "files">
| Type        | Convention   |
|-------------|--------------|
| File name   | `PascalCase` |
| Folder name | `PascalCase` |

### Variables and Constants <div id = "naming">
| Type            | Convention             |
|-----------------|------------------------|
| Local variables | `camelCase`            |
| Class variables | `m_camelCase`          |
| Local Pointers  | `pCamelCase`           |
| Class Pointers  | `m_pCamelCase`         |
| Constants       | `SCREAMING_SNAKE_CASE` |

### Misc <div id = "misc">
| Type           | Convention                                 |
|----------------|--------------------------------------------|
| Function names | `camelCase(int camelCase, int camelAgain)` |
| Class names    | `PascalCase`                               |
    
## Functions and Scopes <div id = "functions">
* Pass primitives by either reference or value
* Pass object types (>8 bytes) by reference or const reference 
The indentation style for scopes can be seen here:
```C++
//New line bracket for functions
bool functionName(int arg1, const std::string& arg2)
{
    //Same line bracket for block statements
    if (arg1 > 5) {
        std::cout << arg2 << "\n";
        return true;
    }
    return false;
}
    
void swapStrings(std::string& str1, std::string& str2)
{
    auto temp = str1;
    str1 = str2;
    str2 = str1;
}

void Foo::setID(int newId)
{
    m_id = newId;
}
```

## Classes <div id = "classes">

```C++
class Foo
{
    public:
        Foo();

        void foo();
        void bar();

    protected:
        void barFoo();

    private:
        void fooBar();

        int m_number;
        Object* m_pPointer;
};
```

* Public functions and members at top, protected in middle, private at bottom
* Notice a space between the final class member/function and the next accessor

For initilzation lists, use a new line like so

```C++
Foo::Foo(int x, int y)
:   m_x (x)
,   m_y (y) { }
```

## Includes <div id = "includes">
The order in which files should be included is the following:
    
    1. Standard ibrary includes
    2. Third-party libraries
    3. Other
    4. Forward declarations
    
For example:

```C++
#include <vector>
#include <unordered_map>

#include <SFML/Graphics.hpp>

#include "Foo.h"
```

## Constants <div id = "constants">
* Do not use C-Style "defines" for constants.
* Use constexpr, it is compile-time determined just like #define is
* Functions can be marked as "constexpr" as well. 
    
## Pointers <div id = "pointers">
### Non-Owning <div id = "ptr-nonown>
Try to avoid using pointers as they are often completely unnecessary, as in a reference is usually appropriate instead. However, they are often fine as class members.
    
### Owning <div id = "ptr-own>
For owning pointers, always use smart pointers (`std::unique_ptr` or `std::shared_ptr` depending on the need) and never raw pointers.
    
```
int* x = new int(5); //No
auto y = std::make_unique<int>(5) //Yes
```

If the `new` keyword is seen in your code, your PR will be rejected no questions asked.

