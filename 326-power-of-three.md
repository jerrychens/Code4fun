Python 3

1. Method 1: without using for loop: if the large/largest base-3 integer `(3**31) % n == 0`, then the number is the power of three.
2. Method 2: using for loop
3. Method 3: import math.log

**Method 1**

```python
class Solution:
    """
    @param n: an integer
    @return: if n is a power of three
    """
    def isPowerOfThree(self, n):
        # Write your code here

        # input check
        if n == 0:
            return False

        # Assume 32 bit        
        if 3**31 % n == 0:
            return True
        else:
            return False
```

**Method 2**

```python
class Solution:
    """
    @param n: an integer
    @return: if n is a power of three
    """
    def isPowerOfThree(self, n):
        # Write your code here

        # input check
        if n == 0:
            return False
            
        if n == 1:
            return True

        for i in range(31):
            n = n / 3
            if int(n) == 1:
                return True
            elif n % 3 != 0:
                return False
```


**Method 3**

```python
class Solution:
    """
    @param n: an integer
    @return: if n is a power of three
    """
    def isPowerOfThree(self, n):
        # Write your code here

        import math
        
        if n == 0:
            return False
        
        x = math.log(n, 3)

        if x - int(x) < 1e-14:
            return True
        else:
            return False
```
