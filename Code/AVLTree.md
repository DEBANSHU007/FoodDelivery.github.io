## AVL Tree

### Algorithm Description
AVL Trees are self-balancing binary search trees where the heights of the two child subtrees of any node differ by at most one.

### C++ Code

```cpp
#include<bits/stdc++.h> 
using namespace std; 

class Node { 
public: 
    int key; 
    Node *left; 
    Node *right; 
    int height; 
}; 

int height(Node *N) { 
    if (N == NULL) 
        return 0; 
    return N->height; 
} 

int max(int a, int b) { 
    return (a > b)? a : b; 
} 

Node* newNode(int key) { 
    Node* node = new Node(); 
    node->key = key; 
    node->left = NULL; 
    node->right = NULL; 
    node->height = 1; 
    return(node); 
} 

Node *rightRotate(Node *y) { 
    Node *x = y->left; 
    Node *T2 = x->right; 
    x->right = y; 
    y->left = T2; 
    y->height = max(height(y->left), height(y->right)) + 1; 
    x->height = max(height(x->left), height(x->right)) + 1; 
    return x; 
} 

Node *leftRotate(Node *x) { 
    Node *y = x->right; 
    Node *T2 = y->left; 
    y->left = x; 
    x->right = T2; 
    x->height = max(height(x->left), height(x->right)) + 1; 
    y->height = max(height(y->left), height(y->right)) + 1; 
    return y; 
} 

int getBalance(Node *N) { 
    if (N == NULL) 
        return 0; 
    return height(N->left) - height(N->right); 
} 

Node* insert(Node* node, int key) { 
    if (node == NULL) 
        return newNode(key); 
    if (key < node->key) 
        node->left = insert(node->left, key); 
    else if (key > node->key) 
        node->right = insert(node->right, key); 
    else 
        return node; 
    node->height = 1 + max(height(node->left), height(node->right)); 
    int balance = getBalance(node); 
    if (balance > 1 && key < node->left->key) 
        return rightRotate(node); 
    if (balance < -1 && key > node->right->key) 
        return leftRotate(node); 
    if (balance > 1 && key > node->left->key) { 
        node->left = leftRotate(node->left); 
        return rightRotate(node); 
    } 
    if (balance < -1 && key < node->right->key) { 
        node->right = rightRotate(node->right); 
        return leftRotate(node); 
    } 
    return node; 
} 

void preOrder(Node *root) { 
    if(root != NULL) { 
        cout << root->key << " "; 
        preOrder(root->left); 
        preOrder(root->right); 
    } 
} 

int main() { 
    Node *root = NULL; 
    root = insert(root, 10); 
    root = insert(root, 20); 
    root = insert(root, 30); 
    root = insert(root, 40); 
    root = insert(root, 50); 
    root = insert(root, 25); 
    cout << "Preorder traversal of the constructed AVL tree is \n"; 
    preOrder(root); 
    return 0; 
} 

```

### Time and Space Complexity

![AVLtree](https://github.com/DEBANSHU007/FoodDelivery.github.io/assets/67229736/e32a0bbe-a7fb-4fbf-bf3d-fa63caaba964)

### Limitations
* Maintaining strict balance can lead to more rotations and overhead compared to other balanced trees.
* Implementing and maintaining AVL tree operations (insertion, deletion, and rotation) can be more complex and error-prone


[← Back to Homepage]
