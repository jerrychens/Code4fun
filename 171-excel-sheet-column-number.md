Python 3

1. We can consider it as a 26-based numerical system.
2. The alphabetic/numerical traslation can be dertermined by the differences in the ASCII code.

```python
class Solution:
    """
    @param s: a string
    @return: return a integer
    """
    def titleToNumber(self, s):
        # write your code here
        answer = 0
        n = len(s)
        for i in range(n):
            number = ord(s[n -1 -i]) - ord('A') + 1
            answer = answer + number * 26 ** i
        return answer
```
