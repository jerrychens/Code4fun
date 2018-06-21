Python 3

It's a simulation problem.

1. Use row, and col (sometime dx, dy) to define the coordinate scanning.
2. Use a helper function to get the number of neighbors.
3. 4 possible states: 0: 0 -> 0; 1: 1 -> 1; 2: 1 -> 0; 3: 0 -> 1 (in-line)
4. Mode 2 to get the binary values (whether it's live or dead)


```python
class Solution:
    def neighbor_check(self, i, j, n_row, n_col, board):
        # i, j are current location
        # m, n are the boundaris
        row = [-1,-1, 0, 1, 1, 1, 0,-1]
        col = [ 0, 1, 1, 1, 0,-1,-1,-1]
        direction = len(row)
        count = 0
        for k in range(direction):
            if (i + row[k]) <= (n_row - 1) and (i + row[k]) >= 0 and (j + col[k]) <= (n_col - 1) and (j + col[k]) >= 0:
                state = board[i + row[k]][j + col[k]]
                if state == 1 or state == 2:
                    count += 1
        return count
    
    def gameOfLife(self, board):
        """
        :type board: List[List[int]]
        :rtype: void Do not return anything, modify board in-place instead.
        """
        
        n_row = len(board)    
        n_col = len(board[0])

        # 0: 0 -> 0; 1: 1 -> 1; 2: 1 -> 0; 3: 0 -> 1
        for i in range(n_row):
            for j in range(n_col):
                neighbor_lives = self.neighbor_check(i, j, n_row, n_col, board)
                if board[i][j] == 1:
                    if neighbor_lives < 2:
                        board[i][j] = 2
                    if neighbor_lives > 3:
                        board[i][j] = 2
                    if neighbor_lives == 2 or neighbor_lives == 3:
                        board[i][j] = 1
                if board[i][j] == 0:
                    if neighbor_lives == 3:
                        board[i][j] = 3

        for i in range(n_row):
            for j in range(n_col):
                if board[i][j] % 2 == 0:
                    board[i][j] = 0
                if board[i][j] % 2 == 1:
                    board[i][j] = 1
```

