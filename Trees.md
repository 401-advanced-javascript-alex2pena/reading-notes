# Trees

**Common Terminology**
- Node - A node is the individual item/data that makes up the data structure 
- Root - The root is the first/top Node in the tree
- Left Child - The node that is positioned to the left of a root or node
- Right Child - The node that is positioned to the right of a root or node
- Edge - The edge in a tree is the link between a parent and child node
- Leaf - A leaf is a node that does not contain any children
- Height - The height of a tree is determined by the number of edges from the root to the bottommost node

## Traversals

### Depth First
*When you prioritize the depth (height) first*

**Pre-order:** `root >> left >> right`
```
psuedo
ALGORITHM preOrder(root)

  OUTPUT <-- root.value
  
  if root.left is not NULL
      preOrder(root.left)

  if root.right is not NULL
      preOrder(root.right)
```

**In-order:** `left >> root >> right`
```
ALGORITHM inOrder(node)
// INPUT <-- root node
// OUTPUT <-- in-order output of tree nodes

    if node.left is not NULL
        inOrder(node.left)

    OUTPUT <-- node.value

    if node.right is not NULL
        inOrder(node.right)
```

**Post-order:** `left >> right >> root`
```
ALGORITHM postOrder(node)
// INPUT <-- root node
// OUTPUT <-- post-order output of tree nodes

    if node.left is not NULL
        inOrder(node.left)

    if node.right is not NULL
        inOrder(node.right)

    OUTPUT <-- node.value
```

### Breadth First
*iterates through the tree by going through each level of the tree node-by-node*
```
ALGORITHM breadthFirst(root)
// INPUT  <-- root node
// OUTPUT <-- front node of queue to console

  Queue breadth <-- new Queue()
  breadth.enqueue(root)

  while breadth.peek()
    node front = breadth.dequeue()
    OUTPUT <-- front.value

    if front.left is not NULL
      breadth.enqueue(front.left)

    if front.right is not NULL
      breadth.enqueue(front.right)
```

## Binary Trees
- Restrict the number of children to two (hence our left and right children).
## Binary Search Trees
- Nodes are organized in a manner where all values that are smaller than the root are placed to the left, 
and all values that are larger than the root are placed to the right.
