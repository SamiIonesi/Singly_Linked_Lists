# Singly_Linked_Lists
This repository describes the methods that are relevant to a singly linked list.

## Notes on singly linked list

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
        SinglyLinkedList()
        {
            head = nullptr;
            tail = nullptr;
            length = 0;
        };

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

This function will insert a new node at the end of the singly linked list.

It has a time complexity of:
- **Ω(1)** for best case
- **θ(1)** for average case
- **O(1)** for worst case

```cpp
void append(int value)
{
    Node* temp = new Node(value);

    if(head == nullptr)
    {
        head = temp;
        tail = temp;
    }
    else
    {
        tail->next = temp;
        tail = temp;
    }

    length++;
}
```

#### - prepand(value)

This function will insert a new node at the beginning of the singly linked list.

It has a time complexity of:
- **Ω(1)** for best case
- **θ(1)** for average case
- **O(1)** for worst case

```cpp
void prepand(int value)
{
    Node* temp = new Node(value);

    if(head == nullptr)
    {
        head = temp;
        tail = temp;
    }
    else
    {
        temp->next = head;
        head = temp;
    }
    length++;
}
```
#### - insert(value, index)

This function will insert a new node at a specific index, with a specific value in the list.

It has a time complexity of:
- **Ω(1)** for best case
- **θ(n)** for average case
- **O(n)** for worst case

```cpp
void insert(int value, int index)
{
    if(index > length)
        return;

    if(index == 0)
        prepand(value);
    else if(index == length) 
        append(value);
    else
    {
        Node* newNode = new Node(value);
        Node* temp = head;
        int i = 1;

        while(i != index)
        {
            temp = temp->next;
            i++;
        }

        newNode->next = temp->next;
        temp->next = newNode;
    }
    length++;
}
```

### 2. Deletion methods
#### - delete(index)

This function will delete a node from a specific index in the list.

It has a time complexity of:
- **Ω(1)** for best case
- **θ(n)** for average case
- **O(n)** for worst case

```cpp
void deleteNode(int index)
{
    if(index < 0 || index >= length)
        return;
    
    Node* temp = head;
    Node* nodeToDelete = head;

    for(int i = 0; i < index; i++)
    {
        temp = nodeToDelete;
        nodeToDelete = nodeToDelete->next;
    }

    if(index == 0)
        head = temp->next;
    
    if(index == length - 1)
        tail = temp;
    
    temp->next = nodeToDelete->next;
    delete nodeToDelete;
}
```

#### - deleteFirst()

This function will delete the first node of the list.

It has a time complexity of:
- **Ω(1)** for best case
- **θ(1)** for average case
- **O(1)** for worst case

```cpp
void deleteFirst()
{
    if(head == nullptr)
        return;

    Node* temp = head;

    if(head == tail)
        tail = temp->next;

    head = temp->next;
    delete temp;
}
```

### 3. Search methods

#### - linearSearch(key)

This function will search linearly for a specific node value in a singly linked list. <br>
Condition: Elements from the list must be unique. <br>
This algorithm can be improved by using the next method:
- **Move to Head**: when the element is found, change the found element with the first node of the list. <br>

In this way, the next time when you search and you do it with the same key, it will do a single comparison, so the time complexity is O(1).
  
It has a time complexity of:
- **Ω(1)** for best case
- **θ(n)** for average case
- **O(n)** for worst case

```cpp
int linearSearch(int key)
{
    Node* temp = head;
    
    while(temp != nullptr)
    {
        if(temp->value == key)
        {
            int change = temp->value;
            temp->value = head->value;
            head->value = change;
            return key;
        }
        temp = temp->next;
    }

    return INT_MIN;
        }
```

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

#### - countNodes()

This function will count the nodes present in the singly linked list.

It has a time complexity of:
- **Ω(1)** for best case
- **θ(n)** for average case
- **O(n)** for worst case

```cpp
int countNodes()
{
    Node* temp = head;
    int count = 0;

    if(length > 0)
    {
        while(temp != nullptr)
        {
            count++;
            temp = temp->next;
        }
    }

    return count;
}
```

#### - sumOfNodesValue()

This function will return the sum of all the nodes value present in the singly linked list.

It has a time complexity of:
- **Ω(1)** for best case
- **θ(n)** for average case
- **O(n)** for worst case

```cpp
int sumOfNodesValue()
{
    Node* temp = head;
    int sum = 0;

    if(length > 0)
    {
        while(temp != nullptr)
        {
            sum += temp->value;
            temp = temp->next;
        }
    }

    return sum;
}
```

#### - maxElement()

This function will return the maximum element value from a singly linked list.

It has a time complexity of:
- **Ω(1)** for best case
- **θ(n)** for average case
- **O(n)** for worst case

```cpp
int maxElement()
{
    Node* temp = head;

    if(length <= 0)
        return 0;
    else
    {
        int maxValue = head->value;
        while(temp != nullptr)
        {
            if(temp->value > maxValue)
                maxValue = temp->value;
            temp = temp->next;
        }
        return maxValue;
    }
}
```
