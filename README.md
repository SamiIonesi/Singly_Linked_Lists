# Singly_Linked_Lists
This repository describes the methods that are relevant to a singly linked list.

## Notes for a singly linked list

In a singly linked list each node contains data and a pointer to the next node. <br>
The traversal is unidirectional, only forward.

## Node class 

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

## Singly linked list class

```cpp
class SinglyLinkedList
{
    private:
        Node* head;
        Node* tail;
        int length;

    public:
        SinglyLinkedList(){};
        SinglyLinkedList(int value)
        {
            Node* newNode = new Node(value);
            head = newNode;
            tail = newNode;
            length = 1;
        }

        ~SinglyLinkedList()
        {
            Node* temp = head;

            while(temp != nullptr)
            {
                temp = temp->next;
                delete head;
                head = temp;
            }
        }

        Node* getHead() { return head; } 
        Node* getTail() { return tail; }

};
```

## Function members of singly linked list (methods)

### 1. Insertion methods

#### - append(value)
```cpp

```
#### - prepand(value)
#### - insert(value)

### 2. Deletion methods
#### - delete

### 3. Search methods

#### - search(value)

### 4. Utility methods

#### - getLength()

This function will return the length of the singly linked list.

```cpp
int getLength() { return length; }
```

#### - display()

This function will display all the elements present in the singly linked list.

It has a time complexity of:
- **Ω(n)** for best case
- **θ(n)** for average case
- **O(n)** for worst case

```cpp
void display()
{
    Node* temp = head;

    cout << "---------Nodes-value------------" << endl;

    while(temp != nullptr)
    {
        cout << temp->value << endl;
        temp = temp->next;
    }

    cout << "--------------------------------" << endl;
}
```

#### - recursiveDisplay(Node)

This function will display recursively all the elements present in the singly linked list.

It has a time complexity of:
- **Ω(n)** for best case
- **θ(n)** for average case
- **O(n)** for worst case

```cpp
void recursiveDisplay(Node* temp)
{
    if(temp != nullptr)
    {
        cout << temp->value << endl;
        recursiveDisplay(temp->next);
    }
}
```


#### - create(array, sizeOfArray)

This function will create a singly linked list having as input an array of elements with a specific size.

It has a time complexity of:
- **Ω(n)** for best case
- **θ(n)** for average case
- **O(n)** for worst case

```cpp
void create(int* array, int arraySize)
{
    Node* temp = new Node(array[0]);

    head = temp;
    tail = head;
    length = arraySize;

    for(int i = 1; i < arraySize; i++)
    {
        Node* current = new Node(array[i]);
        tail->next = current;
        tail = current;
    }
    
}
```
#### - reverse()
#### - isEmpty()
