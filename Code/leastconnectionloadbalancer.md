## Least Connection Load balancing Algorithm

### Algorithm Description
The least connection load balancing algorithm distributes incoming requests to the server with the fewest active connections, optimizing resource utilization and minimizing response times by reducing load disparities among servers.

### C++ Code

```cpp
#include <iostream>
#include <unordered_map>
#include <string>
#include <climits>

class LeastConnectionLoadBalancer {
private:
    std::unordered_map<std::string, int> serverConnections;

public:
    LeastConnectionLoadBalancer() = default;

    void addServer(const std::string& serverName) {
        serverConnections[serverName] = 0;
    }

    std::string getServerWithLeastConnections() {
        int minConnections = INT_MAX;
        std::string selectedServer;

        for (const auto& entry : serverConnections) {
            if (entry.second < minConnections) {
                minConnections = entry.second;
                selectedServer = entry.first;
            }
        }

        if (!selectedServer.empty()) {
            serverConnections[selectedServer]++;
        }

        return selectedServer;
    }
};

int main() {
    LeastConnectionLoadBalancer loadBalancer;

    loadBalancer.addServer("Server1");
    loadBalancer.addServer("Server2");
    loadBalancer.addServer("Server3");

    for (int i = 0; i < 10; ++i) {
        std::string selectedServer = loadBalancer.getServerWithLeastConnections();
        std::cout << "Request " << (i + 1) << ": Routed to " << selectedServer << std::endl;
    }

    return 0;
}

}
```


### Limitations
* The main limitation of the least connection load balancing algorithm is its potential to overburden lightly loaded servers with long-lived connections, which can lead to uneven distribution of resources and reduced overall system performance.

[← Back to Homepage]
