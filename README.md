# compiler-llvm
A compiler for a language written in C++ and LLVM

https://llvm.org/docs/tutorial/index.html


# brew install llvm
# Compile
clang++ -g -O3 -std=c++17 toy.cpp `llvm-config --cxxflags`
clang++ -g -O3 -std=c++17 toy.cpp `/usr/local/opt/llvm/bin/llvm-config --cxxflags`
# Run
./a.out

To use the bundled libc++ please add the following LDFLAGS:
  LDFLAGS="-L/usr/local/opt/llvm/lib -Wl,-rpath,/usr/local/opt/llvm/lib"

llvm is keg-only, which means it was not symlinked into /usr/local,
because macOS already provides this software and installing another version in
parallel can cause all kinds of trouble.

If you need to have llvm first in your PATH, run:
  echo 'export PATH="/usr/local/opt/llvm/bin:$PATH"' >> ~/.zshrc

For compilers to find llvm you may need to set:
  export LDFLAGS="-L/usr/local/opt/llvm/lib"
  export CPPFLAGS="-I/usr/local/opt/llvm/include"

//Todo: 
1. This isn't doing sufficient error checking. It will incorrectly read "1.23.45.67"
   and handle it as if you typed "1.23" 
