# wordexp.cpp
templated wordexp.h wrapper for C++.

Expand words like POSIX shell.

Works for: char, wchar, char8, char16, char32

# note
This module is in development, expansion isn't actually supported yet. But it does find great use in correctly turning an argument string into a correct `argv` array.

# usage

```cpp
#include "wordexp.h"

//...
char* str = /* ... */;
Wordexp<char> words{ str };
//...
```

Example:

`single words 'multiple words' "\"escaped\" characters -e --option="value string"`
```cpp
Wordexp words{ "single words 'multiple words' \"\\\"escaped\\\" characters\" -e --option=\"value string\"" };
for (char* word : words) std::cout << word << std::endl;
//single
//words
//multiple words
//"escaped" characters
//-e
//--option=value string
```