## MaxHeap Algorithm

### Algorithm Description
A max-heap is a complete binary tree where each node is larger than its children, ensuring the maximum element is always at the root. It supports efficient insertion and extraction of the maximum element.

### C++ Code

```cpp
#include <iostream>
#include <vector>
#include <stdexcept>

class MaxHeap {
private:
    std::vector<int> heap;

    int parent(int i) { return (i - 1) / 2; }
    int leftChild(int i) { return 2 * i + 1; }
    int rightChild(int i) { return 2 * i + 2; }

    void heapifyDown(int i) {
        int largest = i;
        int left = leftChild(i);
        int right = rightChild(i);

        if (left < heap.size() && heap[left] > heap[largest])
            largest = left;

        if (right < heap.size() && heap[right] > heap[largest])
            largest = right;

        if (largest != i) {
            std::swap(heap[i], heap[largest]);
            heapifyDown(largest);
        }
    }

    void heapifyUp(int i) {
        if (i && heap[parent(i)] < heap[i]) {
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

    int extractMax() {
        if (heap.empty())
            throw std::out_of_range("Heap underflow");

        int root = heap.front();
        heap[0] = heap.back();
        heap.pop_back();
        heapifyDown(0);
        return root;
    }

    int getMax() {
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
    MaxHeap heap;

    heap.insert(3);
    heap.insert(2);
    heap.insert(15);
    heap.insert(5);
    heap.insert(4);
    heap.insert(45);

    std::cout << "Max-Heap array: ";
    heap.printHeap();

    std::cout << "Extracted max: " << heap.extractMax() << std::endl;
    std::cout << "Current max: " << heap.getMax() << std::endl;

    heap.insert(1);
    std::cout << "Max-Heap array after inserting 1: ";
    heap.printHeap();

    return 0;
}
}
```

### Time and Space Complexity

![maxheap](https://github.com/DEBANSHU007/FoodDelivery.github.io/assets/67229736/5622a51a-db34-4f3d-801b-c6152ad9c43e)


### Limitations
*	Designed for efficient maximum element extraction, it's less suited for tasks requiring minimum element extraction or dynamic changes in priority.
*	While efficient for priority queue operations, it may not be the best choice for tasks that require frequent changes in priorities or where sorting or searching flexibility is needed.


[← Back to Homepage]
