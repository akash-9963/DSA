# Linked Lists in C++ – Lecture Summary

In this lecture, we explored the fundamental concepts of Linked Lists in C++. This session is designed to offer a comprehensive understanding of linked lists, ranging from their basic nodes to complex operations.

---

## 📌 Introduction to Nodes and Linked List

- **Node**: The foundational unit of a linked list, a node typically contains two elements:
  - The data
  - A pointer/reference to the next node

- **Linked List**: A sequential collection of nodes. Unlike arrays, their size can dynamically change and they do not require contiguous memory allocation.

---

## 🔗 Types of Linked Lists

### 1. Singly Linked List
- A unidirectional linked list.
- Each node points to the next node.
- The last node points to `nullptr`.

### 2. Doubly Linked List
- Each node contains two pointers:
  - One pointing to the next node
  - One pointing to the previous node
- Allows bidirectional traversal.

### 3. Circular Linked List
- The last node points back to the first node.
- Forms a circular structure.

---

## 🌐 Real World Relevance of Linked Lists

Linked lists are pivotal in applications that require dynamic memory and efficient memory management, such as:

- **Music/Playlist Management**:  
  - Sequential track playing → *Singly Linked List*  
  - Navigation through previous and next tracks → *Doubly Linked List*

- **Operating System's Task Scheduling**:  
  - Implements cyclic task execution → *Circular Linked List*

---

## ⚙️ Operations on Linked Lists

### ✅ Insertion

**At Beginning**:
```cpp
void insertAtBeginning(Node*& head, int data) {
    Node* newNode = new Node(data);
    newNode->next = head;
    head = newNode;
}
````

* Adjust head/tail pointers appropriately.

**At End**:

* Traverse to the end and update the tail.

**At Any Position**:

* Carefully adjust the links to insert a node at desired position.

---

### 🔍 Searching

* Traverse through the list comparing node data with the target value.
* Efficiency depends on the position of the target.

---

### ❌ Removal

**From Beginning**:

* Update the head pointer to the next node.

**From End**:

* Traverse and modify the second last node's next pointer to `nullptr`.

**Specific Node**:

* Bypass the node to be deleted by adjusting pointers of the neighboring nodes.

```cpp
void deleteNode(Node*& head, int key) {
    Node* temp = head;
    Node* prev = nullptr;
    
    if (temp != nullptr && temp->data == key) {
        head = temp->next;
        delete temp;
        return;
    }
    
    while (temp != nullptr && temp->data != key) {
        prev = temp;
        temp = temp->next;
    }
    
    if (temp == nullptr) return;

    prev->next = temp->next;
    delete temp;
}