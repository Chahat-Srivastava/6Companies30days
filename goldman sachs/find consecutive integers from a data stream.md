## Question : Find Consecutive Integers from a Data Stream

### Problem Statement:
For a stream of integers, implement a data structure that checks if the last k integers parsed in the stream are equal to value.

Implement the DataStream class:

DataStream(int value, int k) Initializes the object with an empty integer stream and the two integers value and k.
boolean consec(int num) Adds num to the stream of integers. Returns true if the last k integers are equal to value, and false otherwise. If there are less than k integers, the condition does not hold true, so returns false.

### Code (Python):
```python
class DataStream:

    def __init__(self, value: int, k: int):
        self.value=value
        self.k=k
        self.output=[]
        self.unique=0

    def consec(self, num: int) -> bool:
        if len(self.output)==self.k-1:
            self.output.append(num)
            if num!=self.value:
                self.unique=num
            if self.unique!=0 and self.unique in self.output:
                return False
            else:
                return True
        elif len(self.output)==self.k:
            self.output.pop(0)
            self.output.append(num)
            if num!=self.value:
                self.unique=num
            if self.unique!=0 and self.unique in self.output:
                return False
            else:
                return True
        else:
            self.output.append(num)
            if num!=self.value:
                self.unique=num
            return False


# Your DataStream object will be instantiated and called as such:
# obj = DataStream(value, k)
# param_1 = obj.consec(num)
