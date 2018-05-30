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
    
## Functions and Scopes <div id = functions">
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
```
