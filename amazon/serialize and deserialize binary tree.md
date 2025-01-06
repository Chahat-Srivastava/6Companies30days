## Question : Serialize and Deserialize Binary Tree

### Problem Statement:
Serialization is the process of converting a data structure or object into a sequence of bits so that it can be stored in a file or memory buffer, or transmitted across a network connection link to be reconstructed later in the same or another computer environment.

Design an algorithm to serialize and deserialize a binary tree. There is no restriction on how your serialization/deserialization algorithm should work. You just need to ensure that a binary tree can be serialized to a string and this string can be deserialized to the original tree structure.
### Code (Python):
```python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Codec:

    def serialize(self, root):
        if root is None:
            return ""
        ans=""
        from collections import deque
        st=deque([root])
        while st:
            node=st.popleft()
            if node.val=="#":
                ans=ans+"#"+","
                continue
            else:
                ans=ans+str(node.val)+","
            if node.left:
                st.append(node.left)
            else:
                new=TreeNode("#")
                st.append(new)
            if node.right:
                st.append(node.right)
            else:
                new=TreeNode("#")
                st.append(new)
        return ans
    def deserialize(self, data):
        if (len(data)==0) or (len(data)==1 and data[0]=="#"):
            return None
        from collections import deque
        temp=data.split(",")
        root_val=temp.pop(0)
        root=TreeNode(int(root_val))
        st=deque([root])
        while st:
            node=st.popleft()
            left_val=temp.pop(0)
            if left_val!="#":
                left_node=TreeNode(int(left_val))
                node.left=left_node
                st.append(node.left)
            right_val=temp.pop(0)
            if right_val!="#":
                right_node=TreeNode(int(right_val))
                node.right=right_node
                st.append(node.right)
        return root

        """Decodes your encoded data to tree.
        
        :type data: str
        :rtype: TreeNode
        """
        

# Your Codec object will be instantiated and called as such:
# ser = Codec()
# deser = Codec()
# ans = deser.deserialize(ser.serialize(root))
