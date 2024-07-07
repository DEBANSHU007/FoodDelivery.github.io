## Segent Trees Algorithm

### Algorithm Description
A segment tree is a binary tree used for storing intervals or segments, enabling efficient querying (such as sum, minimum, maximum) and updating of elements in logarithmic time. It is particularly useful for problems involving range queries and updates on an array.

### C++ Code
 
```cpp
#include <bits/stdc++.h> 
using namespace std; 

const int N = 100000; 

int n;  

int tree[2 * N]; 

 
void build( int arr[]) 
{ 

	for (int i=0; i<n; i++)	 
		tree[n+i] = arr[i]; 
 
	for (int i = n - 1; i > 0; --i)	 
		tree[i] = tree[i<<1] + tree[i<<1 | 1];	 
} 

void updateTreeNode(int p, int value) 
{ 

	tree[p+n] = value; 
	p = p+n; 
 
	for (int i=p; i > 1; i >>= 1) 
		tree[i>>1] = tree[i] + tree[i^1]; 
} 
 
int query(int l, int r) 
{ 
	int res = 0; 

	for (l += n, r += n; l < r; l >>= 1, r >>= 1) 
	{ 
		if (l&1) 
			res += tree[l++]; 
	
		if (r&1) 
			res += tree[--r]; 
	} 
	
	return res; 
} 

int main() 
{ 
	int a[] = {1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12}; 

	n = sizeof(a)/sizeof(a[0]); 

	build(a); 

	cout << query(1, 3)<<endl; 
 
	updateTreeNode(2, 1); 

	cout << query(1, 3)<<endl; 

	return 0; 
} 
}
```

### Time and Space Complexity
![segmenttrees](https://github.com/DEBANSHU007/FoodDelivery.github.io/assets/67229736/df91a73e-2bd0-40dd-a8b5-074c33ef480d)



### Limitations
* Segment trees require O(2n−1) space to store the tree for an array of size n, which can be significant for large arrays.
* Building, updating, and querying a segment tree involves complex code, making it harder to implement and debug compared to simpler data structures like arrays

[← Back to Homepage]
