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

# std::shared_ptr in C++
In the code you provided, the Sum object refers to an instance of the Sum class that is dynamically allocated using the new operator. The std::shared_ptr is used to manage the memory of this object.

When the std::shared_ptr is created using std::make_shared<Sum>(), it dynamically allocates a new instance of the Sum class, and the shared pointer takes ownership of the object. The Sum object is then referred to by the shared pointer, and it exists in memory as long as at least one shared pointer points to it.

In the given code, the Sum object is referenced by two shared pointers. One is the sumObj shared pointer, which is created using std::make_shared<Sum>(), and the other is the shared pointer held in the vectSum vector, which is a copy of the sumObj shared pointer. Both shared pointers point to the same Sum object in memory.

So when we say "the Sum object," we are referring to the instance of the Sum class that is being managed by the shared pointers created in the code.


At the end of the for-loop, the sumObj shared pointer goes out of scope, which means that the reference count of the Sum object it points to is decremented by 1. However, the Sum object is still being referenced by the vectSum vector, which holds another copy of the same shared pointer. This means that the reference count of the Sum object remains at 1 even though the sumObj shared pointer has gone out of scope.

Because the Sum object's reference count is still 1, it will not be deleted. The Sum object will remain in memory and continue to be accessible through the shared pointer held in the vectSum vector.

This means that the Sum object will not be deleted until all shared pointers that reference it have gone out of scope or have been destroyed. In this case, the vectSum vector is holding a copy of the shared pointer, which will also go out of scope or be destroyed at some point in the future. Once that happens, the reference count of the Sum object will be decremented by 1 again. If, at that point, the reference count reaches 0, the Sum object will be deleted automatically by the shared pointer's destructor.

In short, the Sum object will be deleted only when all shared pointers that reference it have gone out of scope or have been destroyed, and its reference count reaches 0.
  
 # Using std::shared_ptr for Safe and Efficient Memory Management in C++
  In the given code, a shared pointer is being used to manage the memory of an object of the Sum class. std::shared_ptr is a smart pointer that enables shared ownership of a dynamically allocated object. It maintains a reference count for the number of shared pointers that refer to the object. When the reference count drops to zero, the object is automatically deleted.

Each time a std::shared_ptr object is copied or assigned, the reference count is incremented. When a std::shared_ptr object goes out of scope, the reference count is decremented. If the reference count becomes zero, the std::shared_ptr destructor deletes the managed object.

In the given code, a std::shared_ptr object named sumObj is created using the std::make_shared function. The Sum object is dynamically allocated and managed by the std::shared_ptr. The workers.emplace_back function is then called with *sumObj as the first argument, which passes a reference to the Sum object to the worker thread.

After that, the sumObj shared pointer is copied into the vectSum vector using the std::vector::at function. This means that the memory address of the Sum object is being copied into the vector, and the reference count of the shared pointer is incremented. As a result, the reference count for the Sum object becomes 2.

At the end of the for-loop, the sumObj shared pointer goes out of scope, and its reference count is decremented. However, since the Sum object is also referenced by the vectSum vector, its reference count remains at 1. Therefore, the Sum object will not be deleted until all the shared pointers referencing it go out of scope or are destroyed.

In summary, the shared pointer in the given code manages the memory of a dynamically allocated Sum object, and its reference count is incremented each time the shared pointer is copied or assigned. After the for-loop, the Sum object will not be deleted since its reference count is still 1, and it will continue to be accessible through the vectSum vector.
