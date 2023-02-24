# Effective multi-threaded summation of large numbers
This is a program for parallelizing the calculation of the sum of large numbers using multiple threads. 
The program divides the range of numbers to be summed into smaller segments and assigns each segment to a separate thread for processing.
The individual thread results are then combined to obtain the final sum. This approach speeds up the calculation of the sum, especially for large input ranges,
by utilizing multiple CPU cores in parallel.

# Functors
In C++, functors are objects that act like functions. They are also known as function objects.
Functors are implemented as classes that overload the function call operator operator(). 
When you create an instance of a functor class and call it like a function, 
the operator() function is executed. This allows you to use the functor as if it were a function.

# Shared_ptr in C++
In the code you provided, the Sum object refers to an instance of the Sum class that is dynamically allocated using the new operator. The std::shared_ptr is used to manage the memory of this object.

When the std::shared_ptr is created using std::make_shared<Sum>(), it dynamically allocates a new instance of the Sum class, and the shared pointer takes ownership of the object. The Sum object is then referred to by the shared pointer, and it exists in memory as long as at least one shared pointer points to it.

In the given code, the Sum object is referenced by two shared pointers. One is the sumObj shared pointer, which is created using std::make_shared<Sum>(), and the other is the shared pointer held in the vectSum vector, which is a copy of the sumObj shared pointer. Both shared pointers point to the same Sum object in memory.

So when we say "the Sum object," we are referring to the instance of the Sum class that is being managed by the shared pointers created in the code.


