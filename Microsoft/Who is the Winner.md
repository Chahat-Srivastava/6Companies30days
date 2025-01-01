## Question : Who is the winner?

### Problem Statement:
There are n friends that are playing a game. The friends are sitting in a circle and are numbered from 1 to n in clockwise order. More formally, moving clockwise from the ith friend brings you to the (i+1)th friend for 1 <= i < n, and moving clockwise from the nth friend brings you to the 1st friend.

The rules of the game are as follows:

Start at the 1st friend.
Count the next k friends in the clockwise direction including the friend you started at. The counting wraps around the circle and may count some friends more than once.
The last friend you counted leaves the circle and loses the game.
If there is still more than one friend in the circle, go back to step 2 starting from the friend immediately clockwise of the friend who just lost and repeat.
Else, the last friend in the circle wins the game.
Given the number of friends, n, and an integer k, return the winner of the game.
### Code (Python):
```python
class CircularLinkedList:
    def __init__(self,value):
        self.data=value
        self.next=self
class Solution:
    def insertList(self,n):
        for i in range(n):
            if i==0:
                new_node=CircularLinkedList(i+1)
                head=new_node
                temp=new_node
            else:
                new_node=CircularLinkedList(i+1)
                temp.next=new_node
                new_node.next=head
                temp=temp.next
        return head,new_node
    def findTheWinner(self, n: int, k: int) -> int:
        if n==1:
            return 1
        head,tail=self.insertList(n)
        count=1
        while n>=2:
            count=1
            prev=tail
            curr=head
            while True:
                if count==k:
                    prev.next=curr.next
                    head=prev.next
                    break
                else:
                    count+=1
                prev=curr
                curr=curr.next
            n-=1
        return head.data
        
