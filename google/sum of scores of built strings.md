## Question : Sum of Scores of Built Strings

### Problem Statement:
You are building a string s of length n one character at a time, prepending each new character to the front of the string. The strings are labeled from 1 to n, where the string with length i is labeled si.

For example, for s = "abaca", s1 == "a", s2 == "ca", s3 == "aca", etc.
The score of si is the length of the longest common prefix between si and sn (Note that s == sn).

Given the final string s, return the sum of the score of every si.

### Code (Python):
```python
class Solution:
    def sumScores(self, s: str) -> int:
        def calculate_z_values(seq):
            n = len(seq)
            z_values = [0] * n
            window_start, window_end = 0, 0

            for index in range(1, n):
                if index <= window_end:
                    z_values[index] = min(window_end - index + 1, z_values[index - window_start])
                while index + z_values[index] < n and seq[z_values[index]] == seq[index + z_values[index]]:
                    z_values[index] += 1
                if index + z_values[index] - 1 > window_end:
                    window_start, window_end = index, index + z_values[index] - 1

            return z_values

        return len(s) + sum(calculate_z_values(s))
