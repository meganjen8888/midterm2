# midterm2

What are the advantages of a BST vs. linked list?
Consider:
Linear vs. binary search
Arrays vs. linked lists

With linked list, you can only do linear search
Binary search trees can use binary search
Binary search is faster

When does a BST give the best performance?
Minimum height
Can use binary search (faster)

When does a BST give the worst performance?
Based on shape of the tree
Maximum height = when are insertions are in sorted order, we get generate tree
Every child only has a right node / will work like a linked list
Same applies for the reverse (every child has a node on the left)

Recursive way - we can count all of the binary nodes

Recursive code for count

The way it recursively works is when it’s a recursive function

Recursively counts all of the nodes

How do we recursively count nodes of a BST?




Review ADTs and Implementations

Abstract Data Types
Sorted List
Unsorted List
Stack
Queue
Heap 

Can you describe all of these ADTs?

Queue
FIFO / first in, first out
Access to data = front and back
Dequeue removes from front / enqueue adds to the back

Stack
LIFO / Last in, first out
Access: only from top
Method: push and pop
Removing: only from top

Heap
Insert or remove
Enqueue or dequeue
Insert at the end and dequeue from the end

Sorted list
List of elements in sorted order (ascending order, each element greater than the previous)
Random access
No insert/removal
Insert = right spot
Removal = right spot

Unsorted list
List of elements in unsorted order
Insert at one end and remove either end
No rules for enqueue or dequeue or insert and remove
No particular order
Access to all the elements

The above ADTs can be implemented with:
Array
Linked list
BST

Unsorted list might be an array or a linked list

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
Trace BST by traversals
What is the efficiency of BST at best and worst
When does the best and worst occur
Review Insert, Traversal, and CountNode methods
Write recursive methods to count nodes or levels
