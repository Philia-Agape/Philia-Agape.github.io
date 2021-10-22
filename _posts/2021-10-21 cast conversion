---
layout: post
title: cast conversion in C++
---
The problem arises with the modification of set value in C++, consider the example: 
```cpp     
set<string> myset{"hello","hi","hey"};
set<string>:: iterator itr = myset.begin();
*itr = "hooray";
```
Unfortunately, it's not allowed;( 
The compiler says it's an action of assigning new value to read-only location, which is the iterator to the beginning of set.

Consider the difference between two types of pointers: const T* and T* const, what do these two pointers do?
First, const T* is a pointer to type T that can not modify the value it's pointing to by * operator, so and T* const
is pointing to type T whose address is not allowed to midify.

There're three main ways of type conversion in C++ as far as I've used. const_cast, static_cast, and dynamic_cast.

consider another interesting case, guess what output will be:
CODE FOLLOWS:  
```cpp     
   const int a = 7;
   int* p1 = const_cast<int*>(&a);
   (*p1)++;
   cout << "a = " << a << "\n";
   
   int i = 7;
   const int b = i;
   int* p2 = const_cast<int*>(&c);
   (*p2)++;
   cout << "b = " << b << "\n"; 
```
The output(surprised?):
a = 7
b = 8

For more "cast" function, here's reference to [Source Code Credit](https://en.cppreference.com/w/cpp/language/const_cast).  




----
****
