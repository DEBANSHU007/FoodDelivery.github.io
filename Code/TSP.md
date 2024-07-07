## Travelling Salesman Problem Algorithm

### Algorithm Description
The Travelling Salesman Problem (TSP) is an optimization problem where the goal is to find the shortest possible route that visits a set of cities and returns to the starting point. The Travelling Salesman Algorithm is a method used to solve this problem, typically by exploring all possible routes and finding the one with the minimum total distance.

### C++ Code

```cpp
#include <iostream>
 
using namespace std;

const int n = 4;

const int MAX = 1000000;

int dist[n + 1][n + 1] = {
	{ 0, 0, 0, 0, 0 }, { 0, 0, 10, 15, 20 },
	{ 0, 10, 0, 25, 25 }, { 0, 15, 25, 0, 30 },
	{ 0, 20, 25, 30, 0 },
};

int memo[n + 1][1 << (n + 1)];

int fun(int i, int mask)
{
	
	if (mask == ((1 << i) | 3))
		return dist[1][i];
	if (memo[i][mask] != 0)
		return memo[i][mask];

	int res = MAX; 


	for (int j = 1; j <= n; j++)
		if ((mask & (1 << j)) && j != i && j != 1)
			res = std::min(res, fun(j, mask & (~(1 << i)))
									+ dist[j][i]);
	return memo[i][mask] = res;
}

int main()
{
	int ans = MAX;
	for (int i = 1; i <= n; i++)
		ans = std::min(ans, fun(i, (1 << (n + 1)) - 1)
								+ dist[i][1]);

	printf("The cost of most efficient tour = %d", ans);

	return 0;
}
}
```

### Time and Space Complexity
![TSP](https://github.com/DEBANSHU007/FoodDelivery.github.io/assets/67229736/8eb3b6dd-a381-4fce-91dc-f3a235faada6)



### Limitations
*	As the number of cities increases, the problem becomes exponentially harder to solve. With just 10 cities, there are already numerous permutations to consider.
*	The basic TSP can be extended with additional constraints like time windows, draft limits, and selective visits, further increasing the complexity.

[← Back to Homepage]
