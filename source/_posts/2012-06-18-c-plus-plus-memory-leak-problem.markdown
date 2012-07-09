---
layout: post
title: "C++ memory leak problem"
date: 2012-06-18 16:02
comments: true
categories: 
---
There is a trouble puzzled me for a long time.

I implemented a simple matrix class.

``` c++
template<class T>
class matrix_t
{
public:
	matrix_t(int rows, int cols, T *p = 0)
	{
		std::cout << "construct." << std::endl;
		this->width_ = cols;
		this->height_ = rows;
		this->len_ = cols * rows;
		this->p_ = new T[len_];
		memset(this->p_, 0, sizeof(T) * len_); // Important!
		if (p != 0)
		{
			for (int i = 0; i<len_; i++) this->p_[i] = p[i];
		}
	}
};
```

which is really simple and nothing special (maybo not elegant at all :P). 

But when I try to use, I found when I use syntax like:

``` c++
matirx_t a(10, 10);
matrix_t b = a;
```

always cause me some trouble like segmentation fault. Soon I realized I forget to add a copy constructor and because I use dynamic memory allocation. The destructor will try to free the already deleted pointer.

when I finished a copy constructor, more problem came out.

When I try
``` c++
matrix_t a(10, 10);
matrix_t b(10, 10);
b = a;
```
This causes me the same problem as above. After some study, I knew that, copy constructor is different from =operator, they have different usage. Please refer this [Copy Constructor and assignment operator](http://www.learncpp.com/cpp-tutorial/911-the-copy-constructor-and-overloading-the-assignment-operator/)
for detail explanation.

I will update the full implementation of the simple matrix class, when I figure out how to post code using this blog system.
							
