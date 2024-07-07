## R Trees Algorithm

### Algorithm Description
An R-Tree is a height-balanced tree structure for indexing multi-dimensional information such as geographical coordinates, with each node representing a minimum bounding rectangle that can contain other rectangles or data points. It efficiently supports spatial queries like range searches and nearest neighbour searches.

### C++ Code

```cpp
#include <iostream>
#include <vector> 
#include <algorithm>
#include <limits>

struct Rect {
    double xmin, ymin, xmax, ymax;

    Rect(double xmin = 0, double ymin = 0, double xmax = 0, double ymax = 0)
        : xmin(xmin), ymin(ymin), xmax(xmax), ymax(ymax) {}

    bool contains(const Rect &other) const {
        return xmin <= other.xmin && xmax >= other.xmax &&
               ymin <= other.ymin && ymax >= other.ymax;
    }

    double area() const {
        return (xmax - xmin) * (ymax - ymin);
    }

    static Rect combine(const Rect &a, const Rect &b) {
        return Rect(std::min(a.xmin, b.xmin), std::min(a.ymin, b.ymin),
                    std::max(a.xmax, b.xmax), std::max(a.ymax, b.ymax));
    }
};

struct Node {
    Rect mbr; 
    std::vector<Node*> children;
    bool isLeaf;

    Node(const Rect &mbr, bool isLeaf = true) : mbr(mbr), isLeaf(isLeaf) {}
};

class RTree {
private:
    Node *root;
    int maxEntries;

    void insert(Node *node, Node *newNode) {
        if (node->isLeaf) {
            node->children.push_back(newNode);
            node->mbr = Rect::combine(node->mbr, newNode->mbr);
            if (node->children.size() > maxEntries) {
                splitNode(node);
            }
        } else {
            Node *bestChild = nullptr;
            double minEnlargement = std::numeric_limits<double>::max();

            for (auto &child : node->children) {
                Rect combinedMBR = Rect::combine(child->mbr, newNode->mbr);
                double enlargement = combinedMBR.area() - child->mbr.area();

                if (enlargement < minEnlargement) {
                    minEnlargement = enlargement;
                    bestChild = child;
                }
            }

            insert(bestChild, newNode);
            node->mbr = Rect::combine(node->mbr, newNode->mbr);
        }
    }

    void splitNode(Node *node) {
        std::vector<Node*> children = node->children;
        node->children.clear();

        Node *newNode1 = new Node(children[0]->mbr);
        Node *newNode2 = new Node(children[1]->mbr);

        for (size_t i = 2; i < children.size(); ++i) {
            Node *child = children[i];
            double area1 = Rect::combine(newNode1->mbr, child->mbr).area();
            double area2 = Rect::combine(newNode2->mbr, child->mbr).area();

            if (area1 < area2) {
                newNode1->children.push_back(child);
                newNode1->mbr = Rect::combine(newNode1->mbr, child->mbr);
            } else {
                newNode2->children.push_back(child);
                newNode2->mbr = Rect::combine(newNode2->mbr, child->mbr);
            }
        }

        node->children.push_back(newNode1);
        node->children.push_back(newNode2);
        node->isLeaf = false;
    }

public:
    RTree(int maxEntries = 4) : maxEntries(maxEntries) {
        root = new Node(Rect(), true);
    }

    void insert(const Rect &rect) {
        Node *newNode = new Node(rect);
        insert(root, newNode);
    }

    void print(Node *node, int depth = 0) const {
        if (!node) return;
        std::cout << std::string(depth, '-') << " Rect(" << node->mbr.xmin << ", " << node->mbr.ymin << ", "
                  << node->mbr.xmax << ", " << node->mbr.ymax << ")\n";
        for (auto &child : node->children) {
            print(child, depth + 1);
        }
    }

    void print() const {
        print(root);
    }
};

int main() {
    RTree tree;

    tree.insert(Rect(1, 1, 2, 2));
    tree.insert(Rect(2, 2, 3, 3));
    tree.insert(Rect(3, 3, 4, 4));
    tree.insert(Rect(4, 4, 5, 5));
    tree.insert(Rect(5, 5, 6, 6));

    tree.print();

    return 0;
}
}
```

### Time and Space Complexity
![Rtree](https://github.com/DEBANSHU007/FoodDelivery.github.io/assets/67229736/89d6d86c-fb0a-4790-a784-6b9d8ad63c2e)


### Limitations
* Updating an R-Tree dynamically with frequent changes to the data can be challenging and may impact performance.
* Over time, an R-Tree may suffer from index fragmentation, which can affect query performance and efficiency

[← Back to Homepage]
