# Vectors

Vectors is a library in `stl` library. they can get dynamically resized.

```cpp
1. vector<int> vec;

2. vector<int> vec = {1, 2, 3}

3. vector<int> vec(3,0)
```

`vec` is the name of the vector, befor that include `#include<vector>`, initially the size is zero when using `1.`, use individual header files, rather than using bits c++.

> segmentation fault = trying to access the part of the memory which doesn't exist.

`3.` shows (3,0) 3 shows the size of vector and 0 shows what value each index must have. so all index will have 0.

#### for each loop

```cpp
for(int i : vec){
    cout << i <<endl ;
    
}
```

this will show the value in the vector, and this `i` doesnt show the index.

so we know the workability, so for more general purpose we use `val` instead of `i`.

## Vector function

#### Size

`vec.size()` = shows the size of vector.

#### push an element

`vec.push_back(anyval)` = then it is added from the last.

#### pop back

`vec.pop_back()` = last value gets deleted and size decreased.

#### front

`vec.front()` = prints the first/front value of the vector.

#### at

`vec.at(index)` = koi bhi index ki value print ho jayegi.

# Static vs Dynamic Allocation

Static memory gets allocated in compile time and dynamic memory gets allocated in runtime.

As vector is dynamic, meaning no size is given, and in code we are pushing or poping an element which happens on runtime, so memory is added and removed in executing the file only.

Static memory is created inside the stack memory and dynamic allocation is done in heap.

### How vectors are allocated in dynamic memory


So for example we initialize a vector and then push a single element, then in the memory a kind of array is generated, if we input another element, that array is full so, it creates a double space in the same array and stores in it, when creating third element, the 2 spaces array gets doubled now 4 spaces are present, the old array is automatically deleted.

vec - size & capacity

so size is 3 in the above eg and capacity is 4.

