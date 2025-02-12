# Linking Headers

Linking local and global headers.

```c++
#include <header.h>
#include "header.h"
```

# Included Multiple Times

If a header file is included many times and is not formatted properly, then it'll cause redefinition errors during compilation. To avoid this add these 3 lines.

```c++
#ifndef TAG
#define TAG

#ifndef THISLIBRARY
#define THISLIBRARY
```

These two lines tell the compiler that, if `TAG` is not defined yet, then define it. The `TAG` must all capital case letters and must not include spaces or dashes `-`. #gap

After that put the proper contents of the header file. To end the definition put this line at the end of the file.

```c++
#endif
```

This is a proper way to resolve redefinition conflicts. `Pragma once` sometimes works, sometimes it doesn't and is not a standard solution, hence the above is preferred.

The entire properly formatted file should look like this:

```c++
#ifndef GETEXTENSION
#define GETEXTENSION

#include <string>

int my_function(std::string text) {

	int i = text.length();
	
	return i;
}

#endif
```

# External file

Declare functions and classes in `.h` and write implementation in `.cpp` file. In other files link `.h` and compile `.cpp` into object and then link. 

```cpp
// header.h

int thisfunction (int a);

class cc {
	int a;
public:
	int getA ();
}
```

```cpp
// header.cpp

#include header.h

int thisfunction (int a) {
	return a * 2;
}

int cc::getA () {
	return a;
}
```