## Array

- store data in **blocks of sequential memory**
- size is fixed 
    - accessing memory location of each element is easy to be calculated
    - to add element, allocate new array and copy over all data 

```C++
int main() {
    int values[10] = { 1, 2, 3, 4, 5, 6, 7, 8, 9, 10 };

    // caculate the offset from the beginning of the array
    // 4 bytes per index (size of int)
    int offset = (long) &(values[index]) - (long) &(values[0]);

    return 0;
}
```

---

## Linked List

- linked list | linked memory
- store data with **link** to the location in memory of the next list node
    - ~= store data in **node** linked together by **link**
- `ListNode` are linked together to form a *Linked List*
- **Head pointer** stores the link to the beginning of the list : point [0]
- **ø** points to `nullptr` : mark the end of the list

### List Node
- pair of the data and the link
- data and pointer that points to the next element of the list

```C++
template <typename T>
class List {
    public:
        const T & operator[](unsigned index);
        void insertAtFront(const T & data);
    
    private:
        class ListNode {
            public:
                T &data;
                ListNode *next; // pointer
                ListNode(T & data) : data(data), next(Null) { }
        };
    
    ListNode *head_; // head pointer
}

```

### List::get

- move from head pointer to the next pointer... so on
- take longer time than `array` : **runtime disadvantage**

```C++
template <typename T>
const T & List<T>::operator[](unsigned index) {
    // start a 'thru' pointer to go through the list
    ListNode *thru = head_;

    // loop until the end of the list (or nullptr)
    while (index > 0 && thru->next != nullptr) {
        thru = thru->next;
        index--;
    }

    return thru->data;
}
```

### List::insert

- make the `LinkNode` want to insert to point the one at the index I want to insert on
- make the previous `LinkNode` to point the one inserted

```C++
template <typename T>
void List<T>::insertAtFront(const T & data) {
    // new LinkNode on the heap
    ListNode *node = new ListNode(data);

    // set the new one's next pointer point the current head of the list
    node->next = head_;

    // set the list's head pointer points the new node
    head_ = node;
}
```

---

## Run-time Analysis

### Array vs LinkedList

- access to a given index in length(n)
    - array : direct access via offset formula -> take 1 time; *O(1)*
    - Linked List : traverse every elements to reach the index -> take n times; *O(n)*

- find the location of a data
    - array : search full array -> *O(n)*
    - Linked List : search full list -> *O(n)*

---

#### Find data in sorted array

- Array's find algorithm can be faster than *O(n)* if sorted
    - **Binary Search** : cut in half each time; *O(log(n))*

- Linked List's find algorithm is same in sorted and unsorted; *O(n)*
    - have to traverse the full list

---

---

#### Data Modification (Insertion & Deletion)

- Array : have to move push 2 parts (before and after); *O(n)*

- Linked List : create/delete new linkNode and change pointers where to point at; *O(1)*

### Array Resize Strategy

- strategy 1 : grow array by +2 each time
    - total work done by adding n elements : *O(n^2)*

- strategy 2 : grow array by double each time
    - total work done by adding n elements : *O(n)*
    - average work per element: O(n) / n == O(1)


