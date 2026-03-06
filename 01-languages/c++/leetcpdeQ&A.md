# leetcode

## Single number(136)

The question is about finding the single number which is not repeating 2 times or more.

`vector<int>& nums` = why & given, because by default the vector is pass by value stored, so we want that the changes which happens in a function must reflect, so we put it in pass by reference.

So the ampersand creates an alias of the original vector and it reflects on the main vector.

OK so the approach to solve this type of question, lets take an example of 4, 1, -1. we need to find single number so the approach it by adding the numbers and we get four. So how convenient would it be to know a method where we can, cancel out the duplicate numbers. 

So for this we will use bitwise manipulation, XOR which means, 1^1 and 0^0 = 0 and differnent number gives one so, we can run xor in the wholearray so if it consists - 4,1,2,1,2. So, 4^1^2^1^2. so in then end we will get 4. n^n = 0. n^0 = n. 

```cpp
int singleNumber(vector<int>& nums){
   for(int val : nums){ 
    ans = ans ^ val;
}

return ans;
}
```



