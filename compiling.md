## Compiling with G++
a step by step intro:

1. Create a hello world program, save as hello.cpp
```
#include<iostream>

int main() {
    std::cout << "Hello, World!" << std::endl;

    return 0;
}
```
2. Compile this file
```
    g++ hello.cpp
```
By default, g++ will create an executable file named a.out. Output file name can be changed by passing the name to the -o flag. This will compile hello.cpp to an executable named hello.
```
    g++ -o hello hello.cpp
```
3. Run the executable and see the output
```
    ./hello
```
    
#SOURCES
https://earthly.dev/blog/g++-makefile/


## Troubleshooting
If code isn't compiling because a library isn't loading, check to see if you have the current module installed.
```
module avail
module load [x]
```

If you are still having issues, try adding -std=c++20 for example:
```
g++ -std=c++20 hello.cpp
```
