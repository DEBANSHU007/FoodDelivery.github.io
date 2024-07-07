## Vehicle Routing Algorithm

### Algorithm Description
The Vehicle Routing Problem (VRP) involves determining the most efficient routes for a fleet of vehicles to deliver goods to a set of locations, minimizing total travel cost while considering constraints like vehicle capacity and delivery time windows.

### C++ Code

```cpp 
//Clarke-Wright Savings Algorithm

#include <iostream>
#include <vector>
#include <algorithm>
#include <tuple> 

using namespace std;

class ClarkeWright {
public:
    ClarkeWright(const vector<vector<int>>& distanceMatrix, int numVehicles)
        : distanceMatrix(distanceMatrix), numVehicles(numVehicles) {
        numLocations = distanceMatrix.size();
        for (int i = 1; i < numLocations; ++i) {
            routes.push_back({i});
        }
        calculateSavings();
    }

    void solve() {
        for (const auto& saving : savings) {
            int i, j;
            double save;
            tie(i, j, save) = saving;
            vector<int>* routeI = findRouteContaining(i);
            vector<int>* routeJ = findRouteContaining(j);
            if (routeI != routeJ) {
                mergeRoutes(routeI, routeJ);
            }
        }
    }

    void printRoutes() {
        for (const auto& route : routes) {
            for (int loc : route) {
                cout << loc << " ";
            }
            cout << endl;
        }
    }

private:
    vector<vector<int>> distanceMatrix;
    int numVehicles;
    int numLocations;
    vector<vector<int>> routes;
    vector<tuple<int, int, double>> savings;

    void calculateSavings() {
        for (int i = 1; i < numLocations; ++i) {
            for (int j = i + 1; j < numLocations; ++j) {
                double save = distanceMatrix[0][i] + distanceMatrix[0][j] - distanceMatrix[i][j];
                savings.push_back(make_tuple(i, j, save));
            }
        }
        sort(savings.begin(), savings.end(), [](const auto& a, const auto& b) {
            return get<2>(a) > get<2>(b);
        });
    }

    vector<int>* findRouteContaining(int location) {
        for (auto& route : routes) {
            if (find(route.begin(), route.end(), location) != route.end()) {
                return &route;
            }
        }
        return nullptr;
    }

    void mergeRoutes(vector<int>* routeI, vector<int>* routeJ) {
        routeI->insert(routeI->end(), routeJ->begin(), routeJ->end());
        routes.erase(remove(routes.begin(), routes.end(), *routeJ), routes.end());
    }
};

int main() {
    vector<vector<int>> distanceMatrix = {
        {0, 29, 20, 21},
        {29, 0, 15, 17},
        {20, 15, 0, 28},
        {21, 17, 28, 0}
    };
    int numVehicles = 2;

    ClarkeWright cw(distanceMatrix, numVehicles);
    cw.solve();
    cout << "Optimized routes:" << endl;
    cw.printRoutes();

    return 0;
}
}
```

### Time and Space Complexity
![VRP](https://github.com/DEBANSHU007/FoodDelivery.github.io/assets/67229736/e514de3d-4e48-41a3-ae35-8bc58c3bcbd8)



### Limitations
* VRP is a complex problem, meaning that finding the optimal solution becomes computationally infeasible as the number of locations and constraints increase.
* Real-world scenarios often involve dynamic changes such as traffic conditions, new delivery requests, and vehicle breakdowns, which are challenging to accommodate in static VRP algos.

[← Back to Homepage](../README.md)
