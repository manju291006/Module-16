# Exp. No: 16a 
## AVL Tree - 1 – construct an AVL tree

###  Aim
To Write a Python program to construct an AVL tree using the following elements 10 20 30 40 50 25

and Print the nodes of it using the appropriate packages and built in function.



###  Algorithm

Step 1: Start with an empty AVL tree.
Step 2: Insert elements one by one: 10, 20, 30, 40, 50, 25.
Step 3: After inserting each element, check the balance factor of each node.
Step 4: If the balance factor is greater than 1 or less than -1, perform appropriate rotations:

Left Rotation

Right Rotation

Left-Right Rotation

Right-Left Rotation
Step 5: Once all elements are inserted, perform an inorder traversal to print the nodes in sorted order.

### 🧾 Program
```
from TreeAVL.AVL import AVL  #Write your code here

def getDictTree(self):
 return self.dict_tree

def Construct_AVL(L):
    tree=AVL(L)
    print(getDictTree(tree))
    
L=[10, 20, 30, 40, 50, 25]
```

### OUTPUT
<img width="800" height="168" alt="image" src="https://github.com/user-attachments/assets/992ac2d7-caa9-4459-a13c-c05fa3425361" />

### RESULT
Thus the program was executed successfully 



# Exp. No: 16b 
## AVL Tree - 2 – Write a Python program to construct an AVL tree and insert the new node into it and balance it

###  Aim
To Write a Python program to construct an AVL tree and insert the new node into it and balance it


###  Algorithm

Creates an AVL Tree using insertions.

After each insertion, it calculates the balance factor.

If the tree becomes unbalanced, it performs rotations:

Right Rotate → LL Case

Left Rotate → RR Case

Left-Right Rotate → LR Case

Right-Left Rotate → RL Case

Finally, it prints the inorder traversal of the tree.

### 🧾 Program
```
from TreeAVL.AVL import AVL

def getDictTree(self):
 return self.dict_tree

def Construct_AVL(L,N):
  tree = AVL(L)
  for i in N:
      tree.insertNode(i)
  print("AVL Tree Before Balancing\n",getDictTree(tree))
  tree.BalanceTree()
  print("AVL Tree After Balancing\n",getDictTree(tree))
```

### OUTPUT
<img width="808" height="356" alt="image" src="https://github.com/user-attachments/assets/3efa2b07-9af8-4c43-b63a-bff95bb3028c" />

### RESULT
Thus the program was executed successfully 




# Exp. No: 16c 
## B Tree – Write a Python function def insert(self, k): to insert the nodes in a B Tree 

###  Aim
To Write a Python function def insert(self, k): to insert the nodes in a B Tree . Get the value from the user and Insert the new node to the BTree


###  Algorithm

Step 1: Start with an existing B-Tree.

Step 2: If the root is empty, create a new root node and insert the value.

Step 3: If the root or any node becomes full (maximum keys reached), split the node into two parts and move the middle key to the parent node.

Step 4: Find the correct position for the new key and insert it into the appropriate node so that keys remain sorted.

Step 5: Repeat the process until the new key is successfully inserted and the tree remains balanced.

### 🧾 Program
```
# Searching a key on a B-tree in Python


# Create a node
class BTreeNode:
  def __init__(self, leaf=False):
    self.leaf = leaf
    self.keys = []
    self.child = []


class BTree:
  def __init__(self, t):
    self.root = BTreeNode(True)
    self.t = t


  def insert(self, k):
      root=self.root
      if len(root.keys)==(2*self.t)-1:
          temp=BTreeNode()
          self.root=temp
          temp.child.insert(0,root)
          self.split_child(temp,0)
          self.insert_non_full(temp,k)
      else:
          self.insert_non_full(root,k)

  def insert_non_full(self, x, k):
    i = len(x.keys) - 1
    if x.leaf:
      x.keys.append((None, None))
      while i >= 0 and k[0] < x.keys[i][0]:
        x.keys[i + 1] = x.keys[i]
        i -= 1
      x.keys[i + 1] = k
    else:
      while i >= 0 and k[0] < x.keys[i][0]:
        i -= 1
      i += 1
      if len(x.child[i].keys) == (2 * self.t) - 1:
        self.split_child(x, i)
        if k[0] > x.keys[i][0]:
          i += 1
      self.insert_non_full(x.child[i], k)

  def split_child(self, x, i):
    t = self.t
    y = x.child[i]
    z = BTreeNode(y.leaf)
    x.child.insert(i + 1, z)
    x.keys.insert(i, y.keys[t - 1])
    z.keys = y.keys[t: (2 * t) - 1]
    y.keys = y.keys[0: t - 1]
    if not y.leaf:
      z.child = y.child[t: 2 * t]
      y.child = y.child[0: t - 1]

  # Print the tree
  def print_tree(self, x, l=0):
    print("Level ", l, " ", len(x.keys), end=":")
    for i in x.keys:
      print(i, end=" ")
    print()
    l += 1
    if len(x.child) > 0:
      for i in x.child:
        self.print_tree(i, l)

  

B = BTree(3)

for i in range(10):
    B.insert((i, 2 * i))
print("B Tree :")
B.print_tree(B.root)
n=int(input())
B.insert((n,))
# Write your code here

print("\nB Tree after insertion")
B.print_tree(B.root)
```

### OUTPUT
<img width="766" height="400" alt="image" src="https://github.com/user-attachments/assets/f19858fe-0216-458a-9032-56ab604bd92d" />


### RESULT
Thus the program was executed successfully 





# Exp. No: 16d
## AB+ Tree – Write a Python function def insert(self, key, value): to insert elements in the B+ Tree.

###  Aim
To Write a Python function def insert(self, key, value): to insert elements in the B+ Tree.



###  Algorithm

Step 1: Start with an existing B+ Tree or create a new one if it’s empty.

Step 2: Find the correct leaf node where the new key should be inserted by comparing keys from the root to the leaves.

Step 3: Insert the key and value into the leaf node in sorted order.

Step 4: If the leaf node overflows (exceeds maximum keys), split the node and move the middle key up to the parent.

Step 5: If the parent also overflows, repeat splitting until the tree is balanced.

Step 6: Stop when the key is successfully inserted and the B+ Tree remains balanced.

### 🧾 Program
```
class Node(object):
    
    def __init__(self, order):
        
        self.order = order
        self.keys = []
        self.values = []
        self.leaf = True

    def add(self, key, value):
        
        if not self.keys:
            self.keys.append(key)
            self.values.append([value])
            return None

        for i, item in enumerate(self.keys):
            
            if key == item:
                self.values[i].append(value)
                break

            
            elif key < item:
                self.keys = self.keys[:i] + [key] + self.keys[i:]
                self.values = self.values[:i] + [[value]] + self.values[i:]
                break

        
            elif i + 1 == len(self.keys):
                self.keys.append(key)
                self.values.append([value])

    def split(self):
        
        left = Node(self.order)
        right = Node(self.order)
        mid = self.order // 2

        left.keys = self.keys[:mid]
        left.values = self.values[:mid]

        right.keys = self.keys[mid:]
        right.values = self.values[mid:]

      
        self.keys = [right.keys[0]]
        self.values = [left, right]
        self.leaf = False

    def is_full(self):
     
        return len(self.keys) == self.order

    def show(self, counter=0):
        
        print(counter, str(self.keys))

        
        if not self.leaf:
            for item in self.values:
                item.show(counter + 1)

class BPlusTree(object):
    
    def __init__(self, order=8):
        self.root = Node(order)

    def _find(self, node, key):
        
        for i, item in enumerate(node.keys):
            if key < item:
                return node.values[i], i

        return node.values[i + 1], i + 1

    def _merge(self, parent, child, index):
        
        parent.values.pop(index)
        pivot = child.keys[0]

        for i, item in enumerate(parent.keys):
            if pivot < item:
                parent.keys = parent.keys[:i] + [pivot] + parent.keys[i:]
                parent.values = parent.values[:i] + child.values + parent.values[i:]
                break

            elif i + 1 == len(parent.keys):
                parent.keys += [pivot]
                parent.values += child.values
                break

    def insert(self, key, value):
        parent=None
        child=self.root
        while not child.leaf:
            parent=child
            child,index=self._find(child,key)
        child.add(key,value)
        if child.is_full():
            child.split()
            if parent and not parent.is_full():
                self._merge(parent,child,index)
        
        
        # Write your code here
        
        
        
        
        
        
        
        
        
        
        
        
        

    def retrieve(self, key):
       
        child = self.root

        while not child.leaf:
            child, index = self._find(child, key)

        for i, item in enumerate(child.keys):
            if key == item:
                return child.values[i]

        return None

    def show(self):
        
        self.root.show()

def demo_node():
    node = Node(order=4)
    node.add('a', 'alpha')
    node.add('b', 'bravo')
    node.add('c', 'charlie')
    node.add('d', 'delta')
    node.show()

    print('\nSplitting node...')
    node.split()
    node.show()

def demo_bplustree():
    print('B+ tree...')
    bplustree = BPlusTree(order=4)
    x='y'
    y='ab'
   
    bplustree.insert('a', 'alpha')
    bplustree.insert('b', 'bravo')
    bplustree.insert('c', 'charlie')
    bplustree.insert('d', 'delta')
    bplustree.insert('e', 'echo')
    bplustree.insert('f','foxtrot')

    bplustree.show()

    

if __name__ == '__main__':
    demo_node()
    print('\n')
    demo_bplustree()


```

### OUTPUT
<img width="576" height="432" alt="image" src="https://github.com/user-attachments/assets/bfd1b12a-f2fe-4f50-a3df-ee55cf278afd" />


### RESULT
Thus the program was executed successfully 





# Exp. No: 16e 
## SEB – construct an AVL tree

###  Aim
To Write a Python program to construct an AVL tree using the following elements 12 8 18 5 11 17 4 7 2

and Print the nodes of it using the appropriate packages and built in function.


###  Algorithm

Step 1: Start with an empty AVL tree.
Step 2: Insert elements one by one
Step 3: After inserting each element, check the balance factor of each node.
Step 4: If the balance factor is greater than 1 or less than -1, perform appropriate rotations:

Left Rotation

Right Rotation

Left-Right Rotation

Right-Left Rotation
Step 5: Once all elements are inserted, perform an inorder traversal to print the nodes in sorted order.

### 🧾 Program
```
from TreeAVL.AVL import AVL

def getDictTree(self):
    return self.dict_tree

def Construct_AVL(L):
    tree=AVL(L)
    print(getDictTree(tree))
L=[12, 8, 18, 5, 11, 17, 4, 7, 2]
    
    
```

### OUTPUT
<img width="800" height="175" alt="image" src="https://github.com/user-attachments/assets/3f20a735-3f50-4892-8767-bc52fd67b852" />


### RESULT
Thus the program was executed successfully 
