---
layout: post
title: Modify set value: cast_conversion in C++
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
   int* p2 = const_cast<int*>(&b);
   (*p2)++;
   cout << "b = " << b << "\n"; 
```
The output(surprised?):
a = 7

b = 8

A possible explantion is that a and b are not necessarily 

This is an example of changing elements in set using const_cast, but the alphabetic order is no longer preserved 
```cpp
   set<string> myset{"hello","hi","hey"};
   for(auto itr = myset.begin(); itr!=myset.end(); ++itr)
      cout<< *itr <<'\t';
   cout <<"\n";   
   set<string>:: iterator itr = myset.begin();
   const_cast<string&> (*itr) = "hooray";
   for(auto itr = myset.begin(); itr!=myset.end(); ++itr)
      cout<< *itr <<'\t';
   cout <<"\n";   
   set<int> mynum{1,3,2};
   set<int>:: iterator itr2 = mynum.begin();
   for(auto itr2 = mynum.begin(); itr2!=mynum.end(); ++itr2)
      cout<< *itr2 <<'\t';
   cout <<"\n";  
   const_cast<int&> (*itr2) = 4;
   for(auto itr2 = mynum.begin(); itr2!=mynum.end(); ++itr2)
      cout<< *itr2 <<'\t';
   cout <<"\n";     
```
The output:
hello	hey	hi	(ordered!)
hooray	hey	hi	(not ordered!)
1	2	3	(ordered!)
4	2	3	(not ordered!)

That's why set value is always suggested to modify by insert, erase, swap, and clear function) to preserve the alphabetic order.
For more "cast" function, here's reference to [Source Code Credit](https://en.cppreference.com/w/cpp/language/const_cast).  


----
****
