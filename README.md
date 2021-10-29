# midterm2

## What are the advantages of a BST vs. linked list?
Consider:
Linear vs. binary search
Arrays vs. linked lists

With linked list, you can only do linear search
Binary search trees can use binary search
Binary search is faster

## When does a BST give the best performance?
Minimum height
Can use binary search (faster)

## When does a BST give the worst performance?
Based on shape of the tree
Maximum height = when are insertions are in sorted order, we get generate tree

Every child only has a right node / will work like a linked list

Same applies for the reverse (every child has a node on the left)

In the worst case, it's searching for the last node in a linear linked list. This is when the user must look at every node in the list. In average, they would search half the list, and if it contains n nodes, then the user makes n number of comparisons to find the last node. If n nodes were arranged in a binary search tree of minimum height, the user would not make more than 10(log2(n)<10) comparisons. 

**Recursive way** - we can count all of the binary nodes

Recursive code for count

The way it recursively works is when it’s a recursive function

Recursively counts all of the nodes

How do we recursively count nodes of a BST?

```cpp
int CountNodes(TreeNode* tree);
int TreeType::GetLength() const
// Calls the recursive function CountNodes to count the
// nodes in the tree.
{
    return CountNodes(root);
}
int CountNodes(TreeNode* tree)
// Post: Returns the number of nodes in the tree.
{
    if (tree == NULL)
        return 0;
    else
        return CountNodes(tree->left) +
          CountNodes(tree->right) + 1;
}
```
## What is the cause of a degenerate tree?

When a tree is balanced. It is not as efficient.

## Review ADTs and Implementations

Abstract Data Types
Sorted List
Unsorted List
Stack
Queue
Heap 

## Can you describe all of these ADTs?

- ### Queue
 - FIFO / first in, first out
 - Access to data = front and back
 - Dequeue removes from front / enqueue adds to the back

- ### Stack
- LIFO / Last in, first out
 - **Access**: only from top
 - **Method**: push and pop
 - **Removing**: only from top

- ### Heap
 - Insert or remove
 - Enqueue or dequeue
 - Insert at the end and dequeue from the end

- ### Sorted list
 - List of elements in sorted order (ascending order, each element greater than the previous)
 - Random access
 - No insert/removal
 - Insert = right spot
 - Removal = right spot

- ### Unsorted list
 - List of elements in unsorted order
 - Insert at one end and remove either end
 - No rules for enqueue or dequeue or insert and remove
 - No particular order
 - Access to all the elements

- ## The above ADTs can be implemented with:
 - Array
 - Linked list
 - BST

**Unsorted list** might be an array or a linked list

Stack could be implemented as an array
Access one side (top)

Stack implemented as linked list = simplest way
Remove from one side

Want to avoid copying elements back and forth
Thoughtful design for elements

Could you create a stack or a queue class?
What does it hold?

Template type - way to hold class with different types


Array, linked list, binary search tree to implement a list internally
Same for stack


BSTs
Review BSTs
Insert elements into a BST

```cpp
void Insert(TreeNode*& tree, ItemType item);

void TreeType::PutItem(ItemType item)
//Call the recursive function Insert to insert the item into the tree
{
 Insert(root, item);
}

void Insert(TreeNode*& tree, ItemType item) 
//Insert the item into the tree
//And then item is in the tree. Search property is maintained
{
 if (tree==NULL) //Insertion place found
 {
  tree = new TreeNode;
  tree->right = NULL;
  tree->left = NULL;
  tree->info = item;
 }
 else if (item < tree->info) 
  Insert(tree->left, item); //Item is in left subtree
 else
  Insert(tree->right, item); //In right subtree
}
```

Trace BST by traversals
What is the efficiency of BST at best and worst
When does the best and worst occur
Review Insert, Traversal, and CountNode methods

### CountNode

This is used to count the number of nodes in the Binary Search tree. The user calls this recursively with the pointer to the subtree as an argument. Therefore, they can write the general case. 
```cpp
if ((Left tree is NULL) and (Right tree is NULL)) 
    return 1;
else
    return CountNodes(Left tree) + CountNodes(Right tree) + 1;
```
It works for Figure 8.5a in page 517, but not 8.5b. However, the user can check whether the left or right child of the tree is NULL without calling CountNodes if it is.

```cpp
if ((Left Tree is NULL) and (Right tree is NULL))
    return 1
else if (Left tree is NULL)
    return CountNodes(Right Tree) + 1;
else if (Right tree is NULL)
    return CountNodes(Left tree) + 1;
else return CountNodes(Left tree) + CountNodes(Right tree) + 1;
```

This works if CountNodes has a precondition that the tree isn't empty. But an initially empty tree would cause a crash.

```cpp
if (tree == NULL)
    return 0;
else if (Left tree is NULL and so if the Right tree)
    return 1;
else if (Left is NULL)
    return CountNodes(Right Tree) + 1;
else if (Right tree is NULL)
    return CountNodes(Left Tree) + 1;
else return CountNodes(Left Tree) + CountNodes(Right tree) + 1;
```

Simpler algorithm for CountNode:

```cpp
if tree is NULL
    return 0
else
    return CountNodes(Left Tree) + CountNodes(Right Tree) + 1;
```
Write recursive methods to count nodes or levels

How to remove a node from BST:

1. Find the node you want to delete
2. Find the successor node of p. It's the node in the right subtree which has the minimum value.
3. Replace the content of node p with the content of the successor node
4. Remove the successor node


```cpp
void DeleteNode(TreeNode*& tree);

void Delete(TreeNode*& tree, ItemType item);

void TreeType::DeleteItem(ItemType item)
{ //Calls recursive function Delete to remove the item from the tree
 Delete(root, item);
}
void Delete(TreeNode*& tree, ItemType item) 
//This deletes the item from the tree
//And then the item is gone
{
 if(item < tree->info)
  Delete(tree->left, item); //Looks in the left subtree
 else if (item > tree -> info)
  Delete(tree->right, item); //Looks in the right subtree
 else
  DeleteNode(tree); //It's found. We call DeleteNNode
}
```

Logic: In a stack you would delete/pop the top of the stack. So you create a temp new Node and and set it to top->next. (temp = top->next) you can then delete top then set top = temp and you are done.

In a linked list logic is the same but you would need to find the node you want to delete, copy it's next, previous nodes into a temp newNodes, delete then node, then set tempPrevious->next = tempNext

Code for a stack deletion:
```cpp
 Word WordStack::pop()
{
    // create a temporary new Node
    StackNode* temp = nullptr;
    // create a temporary new Word object
    Word w;

    // check is stack is empty else "pop" off the top Node and return Word object
    if (isEmpty())
    {
        // throw an exception when popping from an empty stack
        throw EmptyStack();
    }
    else
    {
        // set our temp Word object w to the top Node's Word Object
        w = top->word;
        // sets out temp StackNode to top->next memory address
        temp = top->next;
        // deleting top Node
        delete top;
        // new top Node is now temp memory address linking the list back together
        top = temp;
        // return Word w object
        return w;
    }
}
```
