![tree traversal](./traversals.png)
[nice article](https://www.enjoyalgorithms.com/blog/iterative-binary-tree-traversals-using-stack)

## recursive tree dfs

```py
class TreeNode:
    def __init__(self, value):
        self.val = value
        self.left = None
        self.right = None
        
root = TreeNode(1)
root.left = TreeNode(2)
root.right = TreeNode(3)

root.left.left = TreeNode(4)
root.left.right = TreeNode(5)
        
root.right.left = TreeNode(6)
root.right.right = TreeNode(7)


# tree traversals
# def inorder(rt):
#     if not rt:
#         return
#     inorder(rt.left)
#     print(rt.val)
#     inorder(rt.right)

# def preorder(rt):
#     if not rt:
#         return
#     print(rt.val)
#     inorder(rt.left)
#     inorder(rt.right)

# def postorder(rt):
#     if not rt:
#         return
#     inorder(rt.left)
#     inorder(rt.right)
#     print(rt.val)
# postorder(root)
```

## iterative preorder traversal

```py

# preorder traversal
# Root -> Left -> Right 

def preorder(rt):
	if not root:
		return
	
	stack = []
	curr = rt
	prev = None
	
	#either stack or curr should have vals
	while stack or curr:
		
		if curr:
			print(curr.val)
			
			#-----------------
			# we push the curr node as we know the node exist
			this takes extra memory
			#stack.append(curr)
			#-----------------
			# this pushes the required right node if available
			if curr.right:
				stack.append(curr.right)
			#-----------------
			
			curr = curr.left
		else:
			prev = stack.pop()
			curr = prev.right
```

## traversing two trees simultaniously

```py
def simultaneousInOrderTraversal(node1, node2):
	if not node1 and not node2:
		return

	if node1:
		simultaneousInOrderTraversal(node1.left, node2.left)
		print(f"({node1.val}, {node2.val})", end=", ")
		simultaneousInOrderTraversal(node1.right, node2.right)
```










