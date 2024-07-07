## LRU Algorithm

### Algorithm Description
The LRU (Least Recently Used) cache algorithm maintains a fixed-size cache by evicting the least recently used items when the cache reaches its limit, ensuring efficient storage and retrieval of frequently accessed data. It operates based on the principle of minimizing the frequency of cache replacements.

### C++ Code

```cpp

#include <bits/stdc++.h> 
using namespace std;  

class LRUCache { 
	list<int> dq; 

	unordered_map<int, list<int>::iterator> ma; 
	int csize; 

public: 
	LRUCache(int); 
	void refer(int); 
	void display(); 
}; 

LRUCache::LRUCache(int n) { csize = n; } 

void LRUCache::refer(int x) 
{ 
	 
	if (ma.find(x) == ma.end()) { 
		 
		if (dq.size() == csize) { 
			
			int last = dq.back(); 

			dq.pop_back(); 

			ma.erase(last); 
		} 
	} 

	else
		dq.erase(ma[x]); 
 
	dq.push_front(x); 
	ma[x] = dq.begin(); 
} 

void LRUCache::display() 
{ 

	for (auto it = dq.begin(); it != dq.end(); it++) 
		cout << (*it) << " "; 

	cout << endl; 
} 

 
int main() 
{ 
	LRUCache ca(4); 

	ca.refer(1); 
	ca.refer(2); 
	ca.refer(3); 
	ca.refer(1); 
	ca.refer(4); 
	ca.refer(5); 
	ca.display(); 

	return 0; 
} 
}
```

### Time and Space Complexity
![LRU](https://github.com/DEBANSHU007/FoodDelivery.github.io/assets/67229736/6a3d8d16-386d-481a-ae79-4b4a0ccf4d41)


### Limitations
* The main limitation of the LRU (Least Recently Used) cache algorithm is its complexity in implementation compared to simpler cache strategies. Additionally, it may not perform optimally in scenarios where access patterns do not conform well to the LRU principle, potentially leading to less efficient cache utilization.

[← Back to Homepage](../README.md)
