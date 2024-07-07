## LFU Algorithm

### Algorithm Description
LFU (Least Frequently Used) is a cache eviction algorithm that removes the least frequently accessed items when the cache is full, based on how often each item is accessed. It aims to optimize cache performance by prioritizing removal of less frequently used data.

### C++ Code

```cpp
 
#include <bits/stdc++.h>
using namespace std;

void swap(pair<int, int>& a, pair<int, int>& b)
{
	pair<int, int> temp = a;
	a = b;
	b = temp;
}

inline int parent(int i)
{
	return (i - 1) / 2;
}

inline int left(int i)
{
	return 2 * i + 1;
}

inline int right(int i)
{
	return 2 * i + 2;
}

void heapify(vector<pair<int, int> >& v,
			unordered_map<int, int>& m, int i, int n)
{
	int l = left(i), r = right(i), minim;
	if (l < n)
		minim = ((v[i].second < v[l].second) ? i : l);
	else
		minim = i;
	if (r < n)
		minim = ((v[minim].second < v[r].second) ? minim : r);
	if (minim != i) {
		m[v[minim].first] = i;
		m[v[i].first] = minim;
		swap(v[minim], v[i]);
		heapify(v, m, minim, n);
	}
}

void increment(vector<pair<int, int> >& v,
			unordered_map<int, int>& m, int i, int n)
{
	++v[i].second;
	heapify(v, m, i, n);
}

void insert(vector<pair<int, int> >& v,
			unordered_map<int, int>& m, int value, int& n)
{
	
	if (n == v.size()) {
		m.erase(v[0].first);
		cout << "Cache block " << v[0].first
							<< " removed.\n";
		v[0] = v[--n];
		heapify(v, m, 0, n);
	}
	v[n++] = make_pair(value, 1);
	m.insert(make_pair(value, n - 1));
	int i = n - 1;

	while (i && v[parent(i)].second > v[i].second) {
		m[v[i].first] = parent(i);
		m[v[parent(i)].first] = i;
		swap(v[i], v[parent(i)]);
		i = parent(i);
	}
	cout << "Cache block " << value << " inserted.\n";
}

void refer(vector<pair<int, int> >& cache, unordered_map<int,
					int>& indices, int value, int& cache_size)
{
	if (indices.find(value) == indices.end())
		insert(cache, indices, value, cache_size);
	else
		increment(cache, indices, indices[value], cache_size);
}

int main()
{
	int cache_max_size = 4, cache_size = 0;
	vector<pair<int, int> > cache(cache_max_size);
	unordered_map<int, int> indices;
	refer(cache, indices, 1, cache_size);
	refer(cache, indices, 2, cache_size);
	refer(cache, indices, 1, cache_size);
	refer(cache, indices, 3, cache_size);
	refer(cache, indices, 2, cache_size);
	refer(cache, indices, 4, cache_size);
	refer(cache, indices, 5, cache_size);
	return 0;
}
}
```

### Time and Space Complexity
![LFU](https://github.com/DEBANSHU007/FoodDelivery.github.io/assets/67229736/8bde6cc6-8af3-4432-b3e5-120d52f711fd)



### Limitations
* LFU requires maintaining additional data structures (like frequency counters) for tracking access frequencies, which can increase memory and computational overhead.
  
[← Back to Homepage](../README.md)
