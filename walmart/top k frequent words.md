## Question : Top K Frequent Words

### Problem Statement:
Given an array of strings words and an integer k, return the k most frequent strings.

Return the answer sorted by the frequency from highest to lowest. Sort the words with the same frequency by their lexicographical order.

Example 1:

Input: words = ["i","love","leetcode","i","love","coding"], k = 2
Output: ["i","love"]
Explanation: "i" and "love" are the two most frequent words.
Note that "i" comes before "love" due to a lower alphabetical order.
### Code (Python):
```python
class Solution:
    def topKFrequent(self, words: List[str], k: int) -> List[str]:
        import heapq
        from collections import defaultdict
        dict1=defaultdict(lambda:[0,""])
        for i in words:
            dict1[i]=[dict1[i][0]-1,i]
        output=list(dict1.values())
        heapq.heapify(output)
        output=heapq.nsmallest(k,output)
        ans=[]
        for i in output:
            ans.append(i[1])
        return ans
