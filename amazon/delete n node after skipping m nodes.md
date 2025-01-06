## Question : Delete N nodes after M nodes of a linked list

### Problem Statement:
Given a linked list, delete n nodes after skipping m nodes of a linked list until the last of the linked list.
 
### Code (Python):
```python
class Node:
    # Constructor to initialize the node object
    def __init__(self, data):
        self.data = data
        self.next = None
'''
class Solution:
    def linkdelete(self, head, n, m):
        count1=0
        count2=0
        prev=None
        curr=head
        if m==0:
            m=1
        if n>0:
            while curr and curr.next:
                while curr and curr.next and count1<m:
                    prev=curr
                    curr=curr.next
                    count1+=1
                if count1<m and curr:
                    prev=curr
                    curr=curr.next
                while curr and curr.next and count2<n:
                    curr=curr.next
                    count2+=1
                if count2<n and curr:
                    curr=curr.next
                prev.next=curr
                count1=0
                count2=0
        
