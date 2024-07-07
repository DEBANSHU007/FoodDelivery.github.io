## Min Heap Algorithm

### Algorithm Description
A min-heap is a complete binary tree where each node is smaller than its children, ensuring the minimum element is always at the root. It supports efficient insertion and extraction of the minimum element.

### C++ Code

```cpp

#include <iostream>
#include <vector>
#include <stdexcept>

class MinHeap {
private:
    std::vector<int> heap;

    int parent(int i) { return (i - 1) / 2; }
    int leftChild(int i) { return 2 * i + 1; }
    int rightChild(int i) { return 2 * i + 2; }

    void heapifyDown(int i) {
        int smallest = i;
        int left = leftChild(i);
        int right = rightChild(i);

        if (left < heap.size() && heap[left] < heap[smallest])
            smallest = left;

        if (right < heap.size() && heap[right] < heap[smallest])
            smallest = right;

        if (smallest != i) {
            std::swap(heap[i], heap[smallest]);
            heapifyDown(smallest);
        }
    }

    void heapifyUp(int i) {
        if (i && heap[parent(i)] > heap[i]) {
            std::swap(heap[i], heap[parent(i)]);
            heapifyUp(parent(i));
        }
    }

public:
    void insert(int key) {
        heap.push_back(key);
        int index = heap.size() - 1;
        heapifyUp(index);
    }

    int extractMin() {
        if (heap.empty())
            throw std::out_of_range("Heap underflow");

        int root = heap.front();
        heap[0] = heap.back();
        heap.pop_back();
        heapifyDown(0);
        return root;
    }

    int getMin() {
        if (heap.empty())
            throw std::out_of_range("Heap is empty");

        return heap.front();
    }

    void printHeap() {
        for (int i : heap) {
            std::cout << i << " ";
        }
        std::cout << std::endl;
    }
};

int main() {
    MinHeap heap;

    heap.insert(3);
    heap.insert(2);
    heap.insert(15);
    heap.insert(5);
    heap.insert(4);
    heap.insert(45);

    std::cout << "Min-Heap array: ";
    heap.printHeap();

    std::cout << "Extracted min: " << heap.extractMin() << std::endl;
    std::cout << "Current min: " << heap.getMin() << std::endl;

    heap.insert(1);
    std::cout << "Min-Heap array after inserting 1: ";
    heap.printHeap();

    return 0;
}
}
```

### Time and Space Complexity
![minheap](https://github.com/DEBANSHU007/FoodDelivery.github.io/assets/67229736/cefa1461-f72f-496b-87cb-642d1de2a45e)



### Limitations
* While efficient for priority queue operations, min-heaps are not optimal for all types of sorting or searching tasks compared to other data structures like balanced trees or hash tables.

[← Back to Homepage]
