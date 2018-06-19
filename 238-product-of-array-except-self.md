Python 3


```python
class Solution:
    """
    @param nums: an array of integers
    @return: the product of all the elements of nums except nums[i].
    """
    def productExceptSelf(self, nums):
        # write your code here
        n = len(nums)
        ans = []
        tmp = 1 
        
        for i in range(n):
            if i == 0:
                for j in range(1, n):
                    tmp *= nums[j]
                ans.append(tmp)
                tmp = 1 # reset
            elif i == (n - 1):
                for j in range(n - 1):
                    tmp *= nums[j]
                ans.append(tmp)
                tmp = 1 # reset
            else:
                for j in range(i):
                    tmp *= nums[j]
                for j in range(i + 1, n):
                    tmp *= nums[j]
                ans.append(tmp)
                tmp = 1 # reset
        return ans
```
