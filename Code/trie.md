## Trie Algorithm

### Algorithm Description
A Trie (prefix tree) is a tree-like data structure where each node represents a character or a sequence of characters, commonly used for efficient retrieval and storage of strings, particularly in search and autocomplete applications.

### C++ Code

```cpp
#include <stdio.h>
#include <stdlib.h>
#include <string.h> 


#define N 26

typedef struct TrieNode TrieNode;

struct TrieNode {
    char data; 
    TrieNode* children[N];
    int is_leaf;
};

TrieNode* make_trienode(char data) {
    
    TrieNode* node = (TrieNode*) calloc (1, sizeof(TrieNode));
    for (int i=0; i<N; i++)
        node->children[i] = NULL;
    node->is_leaf = 0;
    node->data = data;
    return node;
}

void free_trienode(TrieNode* node) {
   
    for(int i=0; i<N; i++) {
        if (node->children[i] != NULL) {
            free_trienode(node->children[i]);
        }
        else {
            continue;
        }
    }
    free(node);
}

TrieNode* insert_trie(TrieNode* root, char* word) {
    
    TrieNode* temp = root;

    for (int i=0; word[i] != '\0'; i++) {
        
        int idx = (int) word[i] - 'a';
        if (temp->children[idx] == NULL) {
            
            temp->children[idx] = make_trienode(word[i]);
        }
        else {
            
        }
       
        temp = temp->children[idx];
    }
    
    temp->is_leaf = 1;
    return root;
}

int search_trie(TrieNode* root, char* word)
{
   
    TrieNode* temp = root;

    for(int i=0; word[i]!='\0'; i++)
    {
        int position = word[i] - 'a';
        if (temp->children[position] == NULL)
            return 0;
        temp = temp->children[position];
    }
    if (temp != NULL && temp->is_leaf == 1)
        return 1;
    return 0;
}

void print_trie(TrieNode* root) {
    
    if (!root)
        return;
    TrieNode* temp = root;
    printf("%c -> ", temp->data);
    for (int i=0; i<N; i++) {
        print_trie(temp->children[i]); 
    }
}

void print_search(TrieNode* root, char* word) {
    printf("Searching for %s: ", word);
    if (search_trie(root, word) == 0)
        printf("Not Found\n");
    else
        printf("Found!\n");
}

int main() {
   
    TrieNode* root = make_trienode('\0');
    root = insert_trie(root, "hello");
    root = insert_trie(root, "hi");
    root = insert_trie(root, "teabag");
    root = insert_trie(root, "teacan");
    print_search(root, "tea");
    print_search(root, "teabag");
    print_search(root, "teacan");
    print_search(root, "hi");
    print_search(root, "hey");
    print_search(root, "hello");
    print_trie(root);
    free_trienode(root);
    return 0;
}
}
```

### Time and Space Complexity
![trie](https://github.com/DEBANSHU007/FoodDelivery.github.io/assets/67229736/a0914a69-176b-4aa4-b98b-c434dbb1bbd3)



### Limitations
*	Operations like insertion and deletion may involve a lot of pointer manipulation and can be more complex compared to simpler data structures like hash tables.
*	Tries can consume a significant amount of memory, especially when storing a large number of short strings or when characters are sparsely distributed.

[← Back to Homepage](../README.md)
