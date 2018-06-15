Python 3

1. Method 1: Hash set - Time O(n) hashset build O(1) quary, Space O(n)
2. Method 2: Sorted - Time O(n logn), Space: O(1) if we can modify the input, otherwise O(n)
3. Method 3: Math - get the sum by `(N+1)*N/2`, and use for loop to substrate each element in the list. The remain number is the answer. Time O(n), extra space O(1) 


**Method 1**

```python
class Solution:
    """
    @param nums: An array of integers
    @return: An integer
    """
    def findMissing(self, nums):
        # write your code here
        # Hash set: Time O(n), Space O(n)
        nums_set = set(nums)
        n = len(nums)
        for i in range(n + 1):
            if i not in nums_set:
                return i
```

**Method 2**

```python
class Solution:
    """
    @param nums: An array of integers
    @return: An integer
    """
    def findMissing(self, nums):
        # write your code here
        # sort: Time O(nlogn), Space O(1)
        n = len(nums)
        nums.sort()
        
        # missing the first
        if nums[0] != 0:
            return 0
        # missing the last
        if nums[-1] != n:
            return n
            
        for i in range(n):
            if i != nums[i]:
                return i
````

**Method 3**

```python
class Solution:
    """
    @param nums: An array of integers
    @return: An integer
    """
    def findMissing(self, nums):
        # write your code here
        # sort: Time O(n), Space O(1)
        n = len(nums)
        nums_sum =  (n + 1)*n//2
        for i in nums:
            nums_sum -= i
        return nums_sum
```
