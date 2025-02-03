## Question : Kth Largest Element in a stream

### Problem Statement:
You are part of a university admissions office and need to keep track of the kth highest test score from applicants in real-time. This helps to determine cut-off marks for interviews and admissions dynamically as new applicants submit their scores.

You are tasked to implement a class which, for a given integer k, maintains a stream of test scores and continuously returns the kth highest test score after a new score has been submitted. More specifically, we are looking for the kth highest score in the sorted list of all scores.

Implement the KthLargest class:

KthLargest(int k, int[] nums) Initializes the object with the integer k and the stream of test scores nums.
int add(int val) Adds a new test score val to the stream and returns the element representing the kth largest element in the pool of test scores so far.

### Code (Python):
```python
class KthLargest:
    import heapq
    def __init__(self, k: int, nums: List[int]):
        self.ans = []
        self.k = k
        for i in nums:
            self.add(i)
    def add(self, val: int) -> int:
        if len(self.ans)<self.k:
            heapq.heappush(self.ans,val)
        elif self.ans[0]<val:
            heapq.heappop(self.ans)
            heapq.heappush(self.ans,val)
        return self.ans[0]



# Your KthLargest object will be instantiated and called as such:
# obj = KthLargest(k, nums)
# param_1 = obj.add(val)
