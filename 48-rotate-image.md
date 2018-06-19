Python 3

1. `list.reverse()` modifies the list itself, whereas `reversed(list)` returns an iterator ready to traverse the list in reversed order.
2. Always think about (1) index swap `[i][j]` to `[j][i]` (2) reverse in such array flip problems.
3. Flip along the x=y once (front-back flip and rotate -90 degree), and reverse the order each row (front-back flip and rotate 180 degree).

```python
class Solution:
    """
    @param matrix: a lists of integers
    @return: nothing
    """
    def rotate(self, matrix):
        # write your code here
        n = len(matrix)
        for i in range(n):
            for j in range(i + 1, n): # upper right triangle
                matrix[i][j], matrix[j][i] = matrix[j][i], matrix[i][j]
        for i in range(n):
            matrix[i].reverse()
        return matrix

```
