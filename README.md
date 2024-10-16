# Singly_Linked_Lists
This repository describes the methods that are relevant to a singly linked list.

In a singly linked list each node contains data and a pointer to the next node. <br>
The traversal is unidirectional, only forward.

### Node class 

```cpp
class Node 
{
    public:
        int value;
        Node* next;
    
        Node(int value)
        {
            this->value = value;
            next = nullptr;
        }
};
```

### Singly linked list class

```cpp
class SinglyLinkedList
{
    private:
        Node* head;
        Node* tail;
        int length;

    public:
        SinglyLinkedList(int value)
        {
            Node* newNode = new Node(value);
            head = newNode;
            tail = newNode;
            length = 1;
        }

        Node* getHead() { return head; } 
        Node* getTail() { return tail; }

        ~SinglyLinkedList()
        {
          
        }

};
```

### Function members of singly linked list (methods)

1. Insertion methods
   - append(value)
  ```cpp

  ```
   - prepand(value)
   - insert(value)
2. Deletion methods
   - delete
3. Search methods
   - search(value)
4. Utility methods
   - getLength()
      ```cpp
      int getLength() { return length; }
      ```
   - display()
   - reverse()
   - isEmpty()
