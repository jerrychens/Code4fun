Python 3

1. Dynamic programing

```python
class Solution:
    """
    @param m: positive integer (1 <= m <= 100)
    @param n: positive integer (1 <= n <= 100)
    @return: An integer
    """
    def uniquePaths(self, m, n):
        # write your code here
        F = [[0 for i in range(n)] for j in range(m)]
        
        # initial
        F[0][0] = 1
        
        # edge
        for i in range(1, m):
            F[i][0] = F[i - 1][0] # = 1
        for j in range(1, n):
            F[0][j] = F[0][j - 1] # = 1

        # transition formula
        for i in range(1, m):
            for j in range(1, n):
                F[i][j] = F[i - 1][j] + F[i][j - 1]
        return F[m - 1][n - 1]
```
