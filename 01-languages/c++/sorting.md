# Sorting

arranging a data in a particular order.

Eg = ascending, descending etc.

## Bubble sort

n-1 times loop or iterations, comparing adj elemeents and the larger element to be shifted to the last. Using swap function.

`[4, 1, 5, 2, 3]` 

compare pairs, here 4 > 1, so it will swap, so 2nd me jayega. then 4 and 5, no change, 5 and 2 , 5 swaps, and then 5 gets shifted to the last. so in first iteration, largest get shifted to last.

`[1,4,2,3,5]`

2nd iteration

2 and 4, 4 swaps, 3 and 4, 4 swapped. 2nd iteration completed. 

3rd iteration 

`[1,2,3,4,5]`

Still comparison chalta rhega as n-1 iterations hona h, so 4 iteration hona padega, one thing to note jis iteration me element chala gya highest waala, it may not be compared again, so the loop would not consider that element, so it's decreasing.

### PSeudocode

i = 0 --> 4 comparisom
i = 1 --> 3 comparison and so on

we can find the pattern

so 4 = n - i - 1

```cpp
for(i = 0; i< n - 1; i++ ){
    for(j = 0; j < n- i - 1; j++){
        if (arr[j] > arr[j+1]){
            swap(A[j],A[j+1]);
        }
    }
}
```

FULLCODE

```cpp
#include<iostream>
using namespace std;

void bubbleSort(int arr[], int n){
    for( int i = 0; i < n - 1; i++){

        for (int j = 0; j < n - i -1; j++){
            if(arr[j] > arr[j+1]){
                swap(arr[j] , arr[j+1]);
            }
        }
    }
}


void printArray(int arr[], int n){
    for(int i = 0; i <n; i++){
        cout << arr[i]<< endl;
    }
}
int main(){
    int n = 5;
    int arr[] = {4, 1, 5, 2, 3};

    bubbleSort(arr , n);
    printArray(arr , n);
}
```

Time complexity is O(n^2), not that much good for optimisation.

now even if sorted array is send in bubble sort, it will keep on running, so n^2 chalta rhega.

So one optimisation can be done.

```cpp
void bubbleSort(int arr[], int n){
    for( int i = 0; i < n - 1; i++){
        bool isSwap = false;
        for (int j = 0; j < n - i -1; j++){
            if(arr[j] > arr[j+1]){
                swap(arr[j] , arr[j+1]);
                isSwap = true;
            }
        }
        if (!isSwap){
            return;
        }
    }
}

```

this becomes little optimised.

# Selection Sort

imagine the array into a sorted and unsorted part, so we select an element from unsorted part to sorted part.

take this array

`[4,1,5,2,3]` 

assume whole to be unsorted, so we pick the smallest elementm and place it at it's righteous place,, at the index 0, so that part becomes sorted.

now 4 5 2 3, smallest is 2, so it gets swapped near to the sorted part.

and same happens , n-1 smallest elements find krna, so n - 1 times loop chalana h.

we can assume the first element to be the smallest and then start comparing.


```cpp
void selectionSort(int arr[], int n){
for(i = 0; i < n-1 ; i ++){
    int smallestIndex = i;
    for(j = i + 1 ; j< n; j++){
        if(arr[j] < arr[SI]){
            SI = j;
        }
    }
    swap(arr[i], arr[SI])
}
}
```

# Insertion Sort

assuming some part to be sorted, and the new element to be inserted, and sorted acc

4,1,5,2,3

4 ko assume sorted, so next element liya which is 1(if 4 se bada bhi hota still we would have taken) and then we would want to put that into the sorted region. So we have to take an external variable lets say `current`. Here after putting current into 1, we can assume that 1 in array to be empty, then we would see the sorted part to see where would it fit, so we will take the pointer , prev on the first element and then compare with prev + 1, here then we find that 1 < 4 so 4 has to shift forward, so it gets swapped.

1,4,5,2,3 now the in current variable 5 is stored now and the pointer shifts to 4 then compares to 5, 4 < 5, so 4 is in correct postion.

1,4,5,2,3

current= 2, 

if arr[prev] > current

A[prev+1] = A[prev]

then prev shifts back to 4, checks that 2 < 4 so 4 also shifts right and then two sits rightly, prev shifts to 1, it is correct so the condition stays, then current variable puts 2 in the 1st index. 

```cpp
void insertionSort(int arr[], int n){
    for ( int i  = 1; i < n ; i ++ ){
        int curr = arr[i];
        int prev = i - 1;

        while(prev >= 0 && arr[prev] > curr){
            arr[prev+1] = arr[prev];
            prev--;
        }
        arr[prev+1] = curr;
    }
}
```
What about descending, jo bhi comparision waali, parameters h, reverse the sign(not the for loop one conditions).