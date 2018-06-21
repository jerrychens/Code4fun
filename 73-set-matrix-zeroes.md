Python 3

1. Time O(mn); Space O(1)
2. Use one state variable to store how we take care of the first row, first column and upper left (`matrix[0][0]`).
3. Use the first column/row to store the information on whether we need to remove the column/row or not.
4. Can further avoid the traverse but may need messier code or extra (constant) space.


```python
class Solution:
    """
    @param matrix: A lsit of lists of integers
    @return: nothing
    """
    def setZeroes(self, matrix):
        # write your code here
        
        n_row = len(matrix)
        if not n_row:
            return []
        n_col = len(matrix[0])
        state = 0

        # state 1: first row is 0, state 2: first col is 0
        # state 3: first row/col are 0.
        if  matrix[0][0] == 0:
            state = 3

        for i in range(1, n_row):
            if matrix[i][0] == 0:
                state = 2
                
        for j in range(1, n_col):
            if matrix[0][j] == 0:
                state = 1
        
        # record if we need to clean up the row/col
        for i in range(1, n_row):
            for j in range(1, n_col):
                if matrix[i][j] == 0:
                    matrix[0][j] = 0
                    matrix[i][0] = 0
                    
        # clean up based on the first row/col mark
        for i in range(1, n_row):
            if matrix[i][0] == 0:
                for j in range(1, n_col):
                    matrix[i][j] = 0

        for j in range(1, n_col):
            if matrix[0][j] == 0:
                for i in range(1, n_row):
                    matrix[i][j] = 0                    
        
        # Clean up the first row/col and the matrix[0][0]
        if state == 3:
            for i in range(n_row):
                matrix[i][0] = 0
            for j in range(n_col):
                matrix[0][j] = 0
        elif state == 2:
            for i in range(n_row):
                matrix[i][0] = 0
        elif state == 1:
            for j in range(n_col):
                matrix[0][j] = 0
```
