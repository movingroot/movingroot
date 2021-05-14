## Tree

- linked structure
- complicated data relationships: parent, child, sibling, ancestor, grandchild, grandparent
- element: *node* connection: *edge*

> rooted, directed, and acyclic structure
- must have
    - root
    - directed edges
    - no cycle

---

### Binary Tree

- every node has at most two children
- similar to *linked list data structure*
    -> linked list w/ 2 pointers (max) at every node
- **full** if and only if every node has either 0 or 2 children
- **perfect** if and only if all nodes have 2 children & leaves are at the same level
- **complete** if and only if up until the last level & all leafs on the last level are pushed to the left
    -> important for `heap` structure

```C++
template <typename T>
class BinaryTree 
{
    public:
    ...

    private:
        class TreeNode
        {
            public:
                T & data;
                TreeNode *left, *right;
                TreeNode(T & data) :
                    data(data), left(nullptr), right(nullptr) { }
        };
};
```

---

### Tree Traversals

- require every single node to be visited

#### Pre-order

- root -> left node -> right node
---

#### In-order

- left node -> root -> right node
---

#### Post-order

- left node -> right node -> root
---

#### Level-order 

- read every single level
- one level at a time
- left to right

---

### Binary Search Tree

- BST
- **ordered** binary tree
- can be used as a search structure 
    - `Dictionary` : *key* with data
    ```C++
    template <typename K, typename D>
    class Dictionary {
        public:
            Dictionary();
            const D & find(const K & key);
            void insert(const K & key, const D & data);
            const D & remove(const K & key);
        
        private:
            class TreeNode {
                public:
                    const K & key;
                    const D & data;
                    TreeNode *left, *right;
                    TreeNode(const K & key, const D & data)
                        : key(key), data(data), left(nullptr), right(nullptr) { }
            };
    };
    ```
    - similar to tree structure (*implement* BST)

- from root :
    - every node on left side is less than root
    - every node on right side is greater than root

- height balance factor
    - height balance factor *b* = height(right subtree) - height(left subtree)
    - =0 : perfectly balanced; >0 : swayed to right; <0 : swayed to left

- **Balanced BST**

    : every node's balance factor has a magnitude of 0 | 1

---

#### In-Order Predecessor

- IOP : previous node in an in-order traversal of BST
- right-most node in the left sub-tree of root; biggest in smallers

---

#### Search 

: recursively find out if `root` is greater or less than the value to search
    -> greater : go to right and make that node root
    -> less : go to left and make that node root

- worst case search running time: tree's height; *O(n)* 

#### Insert

: recursively find out if `root` is less than the value to insert
    -> yes : insert
    -> no : recursively find out

#### Remove

- zero-children : delete the node
- one-child : work like linked list
- two-children :
    1. find the IOP of the node to be removed
    2. swap with the IOP
    3. remove the node in new position

---

### Analysis

|Operation|BST average|BST worst|Sorted Array|Sorted Linked List|
|---|---|---|---|---|
|find|O(log(n))\nlinked list|O(n)\nlinked list|O(log(n))\ndivide and conquer|O(n)|
|insert|O(log(n))|O(n)|O(n)|O(n)|
|remove|O(log(n))|O(n)|O(n)|O(n)|

- Best case for all : BST Average Case




