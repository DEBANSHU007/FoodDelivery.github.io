## Geographic Load Balancing Algorithm

### Algorithm Description
Geographic load balancing distributes user requests to servers based on their geographic proximity, optimizing performance by minimizing network latency and improving response times for users in different regions. It aims to enhance user experience and resource utilization across distributed systems.

### C++ Code

```cpp
#include <iostream>
#include <vector>
#include <string>
#include <cstdlib>
#include <ctime>

class Server {
public:
    std::string name;
    std::string location;
    int load; 

    Server(const std::string& name, const std::string& location)
        : name(name), location(location), load(0) {}
};

class GeographicLoadBalancer {
private:
    std::vector<Server> servers;

public:
    GeographicLoadBalancer() = default;

    void addServer(const std::string& name, const std::string& location) {
        servers.emplace_back(name, location);
    }

    Server getServer(const std::string& userLocation) {
       
        std::srand(static_cast<unsigned int>(std::time(0)));
        int index = std::rand() % servers.size();
        return servers[index];
    }
};

int main() {

    GeographicLoadBalancer loadBalancer;


    loadBalancer.addServer("Server1", "USA");
    loadBalancer.addServer("Server2", "Europe");
    loadBalancer.addServer("Server3", "Asia");

    std::vector<std::string> userLocations = {"USA", "Europe", "Asia", "USA", "Europe", "Asia"};
    for (const std::string& location : userLocations) {
        Server server = loadBalancer.getServer(location);
        std::cout << "Request from " << location << " served by " << server.name << std::endl;
    }

    return 0;
}

}
```

### Limitations
* Constantly updating and maintaining geographic data and calculations can introduce additional overhead and complexity in the load balancing process, potentially impacting performance.

[← Back to Homepage](../README.md)
