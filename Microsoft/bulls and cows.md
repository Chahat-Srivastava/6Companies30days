## Question : Bulls and Cows

### Problem Statement:
You are playing the Bulls and Cows game with your friend.

You write down a secret number and ask your friend to guess what the number is. When your friend makes a guess, you provide a hint with the following info:

The number of "bulls", which are digits in the guess that are in the correct position.
The number of "cows", which are digits in the guess that are in your secret number but are located in the wrong position. Specifically, the non-bull digits in the guess that could be rearranged such that they become bulls.
Given the secret number secret and your friend's guess guess, return the hint for your friend's guess.

The hint should be formatted as "xAyB", where x is the number of bulls and y is the number of cows. Note that both secret and guess may contain duplicate digits.
### Code (Python):
```python
class Solution:
    def getHint(self, secret: str, guess: str) -> str:
        dict1_bulls={}
        dict1={}
        dict2={}
        count1=0
        count2=0
        set1=set()
        for i in range(len(secret)):
            if secret[i]==guess[i]:
                count1+=1
                if secret[i] in dict1_bulls:
                    dict1_bulls[secret[i]]+=1
                else:
                    dict1_bulls[secret[i]]=1
        for i in range(len(secret)):
            if secret[i] in dict1:
                dict1[secret[i]]+=1
            else:
                dict1[secret[i]]=1
            if guess[i] in dict2:
                dict2[guess[i]]+=1
            else:
                dict2[guess[i]]=1
        for i in sorted(dict1):
            if i in dict2:
                count2+=min(dict1[i],dict2[i])
                set1.add(i)
        for i in sorted(dict1_bulls):
            if i in set1:
                count2-=dict1_bulls[i]
        ans=str(count1)+"A"+str(count2)+"B"
        return ans
