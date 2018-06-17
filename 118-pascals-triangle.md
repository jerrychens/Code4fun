Python 3

1. Time: O(numRow^2)
2. Take care of the numRow = 0 and 1 case.

**Explicit**

```python
class Solution:
    def generate(self, numRows):
        """
        :type numRows: int
        :rtype: List[List[int]]
        """
        pascal = []
        layer_1 = [1]
        layer_2 = [1, 1]

        if numRows == 0:
            return pascal
        elif numRows == 1:
            return [layer_1]
        elif numRows == 2:
            return [layer_1, layer_2]
        elif numRows >= 3:
            pascal = [layer_1, layer_2]
            for i in range(numRows - 2):
                a = pascal[-1]
                n = len(a)
                pascal.append([1] + [(a[i] + a[i+1]) for i in range(n-1)] + [1]) 
            return pascal
```

**Better** (Same concept but concise)

```python
class Solution:
    def generate(self, numRows):
        """
        :type numRows: int
        :rtype: List[List[int]]
        """
        A = []
        for i in range(numRows):
            A.append([1 for _ in range(i+1)])
            for j in range(1, i):
                A[i][j] = A[i-1][j-1] + A[i-1][j]
        return A
```
