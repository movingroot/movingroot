## Queue

- FIFO (first-in first-out) data structure
- can be implemented with both array and a doubly-linked list

- Queue ADT(abstract data type)
    - create
    - push : add data to the back of the queue
    - pop : remove data from the front of the queue
    - empty

---

### Array-based Queue

- keep track of index
- push, pop : *O(1)*

### List-based Queue

- **tail pointer** to access the last element of the list : find the last element *O(1)*
- **Doubly-linked list** add pointers that points backwards : can add element directly to the head : *O(1)*
- find, update: *O(1)*

---

|ff|Array|Linked List|
|Create|O(1)|O(1)|
|Push|O(1)|O(1)|
|Pop|O(1)|O(1)|
|Empty|O(1)|O(1)|

- array.push, pop: occasional need to optimize the capacity of the array
- *Queue guarantee constant runtime no matter how large the queue grows*

---

## Stack

- LIFO (last-in first-out) data structure
- can be implemented with both array and a singly-linked list

- Stack ADT
    - create
    - push : add data to the top of the stack
    - pop : remove data from the top of the stack
    - empty

---

### Array-based Stack

- push, pop : *O(1)*

---

### Linked-List-based Stack

- update the front of the list to `add`; *O(1)*

- remove the front element and update the head pointer to `delete`; *O(1)*

---

|" "|Array|Linked List|
|Create|O(1)|O(1)|
|Push|O(1)|O(1)|
|Pop|O(1)|O(1)|
|Empty|O(1)|O(1)|

- array.push, pop : occasional need to optimize the capacity of the array
- singly-linked list is sufficient : no tale pointer
- *Stack guarantee constant runtime no matter how large the stack grows*
