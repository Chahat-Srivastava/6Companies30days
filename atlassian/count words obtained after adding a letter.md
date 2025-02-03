## Question : Count Words Obtained After Adding a Letter

### Problem Statement:
You are given two 0-indexed arrays of strings startWords and targetWords. Each string consists of lowercase English letters only.

For each string in targetWords, check if it is possible to choose a string from startWords and perform a conversion operation on it to be equal to that from targetWords.

The conversion operation is described in the following two steps:

Append any lowercase letter that is not present in the string to its end.
For example, if the string is "abc", the letters 'd', 'e', or 'y' can be added to it, but not 'a'. If 'd' is added, the resulting string will be "abcd".
Rearrange the letters of the new string in any arbitrary order.
For example, "abcd" can be rearranged to "acbd", "bacd", "cbda", and so on. Note that it can also be rearranged to "abcd" itself.
Return the number of strings in targetWords that can be obtained by performing the operations on any string of startWords.

Note that you will only be verifying if the string in targetWords can be obtained from a string in startWords by performing the operations. The strings in startWords do not actually change during this process.

### Code (Python):
```python
class Solution:
    def wordCount(self, startWords: List[str], targetWords: List[str]) -> int:
        start_set = set()
        for word in startWords:
            start_set.add(frozenset(word))
        print(start_set)
        count = 0
        for target in targetWords:
            target_set = frozenset(target)
            for char in target:
                if target_set - {char} in start_set:
                    count += 1
                    break
        
        return count
        
        
        
