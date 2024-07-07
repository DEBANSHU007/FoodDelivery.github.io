## Priority Queue Algorithm

### Algorithm Description
A priority queue is a data structure that manages a collection of elements with associated priorities, supporting efficient retrieval of the highest-priority element and insertion of new elements with their priorities.

### C++ Code

```cpp
#include <iostream>
#include <cstdio>
#include <cstring>
#include <cstdlib>
using namespace std; 

struct node
{
	int priority;
	int info;
	struct node *link;
};

class Priority_Queue
{
    private:
        node *front;
    public:
        Priority_Queue()
        {
            front = NULL;
        }
        void insert(int item, int priority)
        {
            node *tmp, *q;
            tmp = new node;
            tmp->info = item;
            tmp->priority = priority;
            if (front == NULL || priority < front->priority)
            {
                tmp->link = front;
                front = tmp;
            }
            else
            {
                q = front;
                while (q->link != NULL && q->link->priority <= priority)
                    q=q->link;
                tmp->link = q->link;
                q->link = tmp;
            }
        }
        void del()
        {
            node *tmp;
            if(front == NULL)
                cout<<"Queue Underflow\n";
            else
            {
                tmp = front;
                cout<<"Deleted item is: "<<tmp->info<<endl;
                front = front->link;
                free(tmp);
            }
        }
        void display()
        {
            node *ptr;
            ptr = front;
            if (front == NULL)
                cout<<"Queue is empty\n";
            else
            {	cout<<"Queue is :\n";
                cout<<"Priority       Item\n";
                while(ptr != NULL)
                {
                    cout<<ptr->priority<<"                 "<<ptr->info<<endl;
                    ptr = ptr->link;
                }
            }
        }
};

int main()
{
    int choice, item, priority;
    Priority_Queue pq; 
    do
    {
        cout<<"1.Insert\n";
        cout<<"2.Delete\n";
        cout<<"3.Display\n";
        cout<<"4.Quit\n";
        cout<<"Enter your choice : "; 
        cin>>choice;
        switch(choice)
        {
        case 1:
            cout<<"Input the item value to be added in the queue : ";
            cin>>item;
            cout<<"Enter its priority : ";
            cin>>priority;
            pq.insert(item, priority);
            break;
        case 2:
            pq.del();
            break;
        case 3:
            pq.display();
            break;
        case 4:
            break;
        default :
            cout<<"Wrong choice\n";
        }
    }
    while(choice != 4);
    return 0;
}
}
```

### Time and Space Complexity
![PriorityQueue](https://github.com/DEBANSHU007/FoodDelivery.github.io/assets/67229736/656e9dc9-5c1b-4cce-9d69-424096bc80ee)



### Limitations
* Modifying the priority of an existing element or removing elements based on criteria other than the highest priority can be inefficient or not supported by some implementations.
* Unlike arrays or lists, priority queues do not allow direct access to elements based on their position or index, which limits flexibility in certain operations.

[← Back to Homepage]
