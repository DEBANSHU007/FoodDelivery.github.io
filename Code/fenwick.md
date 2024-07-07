## Fenwick Tree Algorithm

### Algorithm Description
A Fenwick Tree, or Binary Indexed Tree (BIT), is a data structure that efficiently supports prefix sum queries and updates , using an array with additional space proportional to the number of elements.

### C++ Code

```cpp
#include <iostream>

using namespace std;

int getSum(int BITree[], int index) 
{ 
    int sum = 0; 
    index = index + 1; 
    while (index > 0) 
    { 
        sum += BITree[index]; 
        index -= index & (-index); 
    } 
    return sum; 
} 

void updateBIT(int BITree[], int n, int index, int val) 
{ 
    index = index + 1; 
    while (index <= n) 
    { 
        BITree[index] += val; 
        index += index & (-index); 
    } 
} 

int *constructBITree(int arr[], int n) 
{ 
    int *BITree = new int[n+1]; 
    for (int i = 1; i <= n; i++) 
        BITree[i] = 0; 

    for (int i = 0; i < n; i++) 
        updateBIT(BITree, n, i, arr[i]); 

    return BITree; 
} 

int main() 
{ 
    int freq[] = {2, 1, 1, 3, 2, 3, 4, 5, 6, 7, 8, 9}; 
    int n = sizeof(freq)/sizeof(freq[0]); 
    int *BITree = constructBITree(freq, n); 
    cout << "Sum of elements in arr[0..5] is "
        << getSum(BITree, 5); 

    freq[3] += 6; 
    updateBIT(BITree, n, 3, 6); 

    cout << "\nSum of elements in arr[0..5] after update is "
        << getSum(BITree, 5); 

    return 0; 
} 
}
```

### Time and Space Complexity
![fenwick](https://github.com/DEBANSHU007/FoodDelivery.github.io/assets/67229736/dabb2bc9-7032-415a-b53b-e4e37a4ad184)



### Limitations
* Once constructed, the Fenwick Tree's size cannot easily be changed dynamically. Resizing or modifying the underlying array requires rebuilding the entire tree.


[← Back to Homepage]
