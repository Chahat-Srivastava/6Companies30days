## Question : Integer to English Words

### Problem Statement:
Convert a non-negative integer num to its English words representation.
### Code (Python):
```python
class Solution:
    def helper_function(self,num):
        digit=["Zero","One","Two","Three","Four","Five","Six","Seven","Eight","Nine"]
        teen=["Ten","Eleven","Twelve","Thirteen","Fourteen","Fifteen","Sixteen","Seventeen","Eighteen","Nineteen"]
        ten=["","","Twenty","Thirty","Forty","Fifty","Sixty","Seventy","Eighty","Ninety"]
        result=""
        if num>99:
            result+=digit[num//100]+" Hundred "
        num=num%100
        if num<20 and num>9:
            result+=teen[num-10]+" "
        else:
            if num>=20:
                result+=ten[num//10]+" "
            num=num%10
            if num>0:
                result+=digit[num]+" "
        return result
    def numberToWords(self, num: int) -> str:
        if num==0:
            return "Zero"
        output=["Thousand","Million","Billion"]
        result=self.helper_function(num%1000)
        num=num//1000
        for i in range(len(output)):
            if num>0 and num%1000>0:
                result=self.helper_function(num%1000)+output[i]+" "+result
            num=num//1000
        return result.strip()
        
