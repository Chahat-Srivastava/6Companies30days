## Question : Extra Characters in a String

### Problem Statement:
You are given a 0-indexed string s and a dictionary of words dictionary. You have to break s into one or more non-overlapping substrings such that each substring is present in dictionary. There may be some extra characters in s which are not present in any of the substrings.

Return the minimum number of extra characters left over if you break up s optimally.

Example 1:

Input: s = "leetscode", dictionary = ["leet","code","leetcode"]
Output: 1
Explanation: We can break s in two substrings: "leet" from index 0 to 3 and "code" from index 5 to 8. There is only 1 unused character (at index 4), so we return 1.

### Code (Python):
```python
class Solution:
    def minExtraChar(self, s: str, dictionary: List[str]) -> int:
        wordSet = set(dictionary)
        n = len(s)
        dp = [0] * (n + 1)
        for i in range(n - 1, -1, -1):
            dp[i] = dp[i + 1] + 1
            for length in range(1, n - i + 1):
                if s[i:i + length] in wordSet:
                    dp[i] = min(dp[i], dp[i + length])
        return dp[0]
