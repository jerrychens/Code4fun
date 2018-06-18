Python 3

1. Use helper function 
2. Becareful of the string/integer conversion
3. Use counter j (or two pointers)

```python
class Solution:
    """
    @param n: the nth
    @return: the nth sequence
    """
    def countAndSay(self, n):
        # write your code here
        # n = 1
        if n == 1:
            return str(1)
        # n >= 2
        results = [1]
        for i in range(n - 1):
            results.append(self.helper(results[-1]))
        return results[-1]

    def helper(self, number):
        ans = ''
        j = 1 # counter
        s = str(number) + 'a' # a is an arbitrary tail
        length = len(s)
        
        for i in range(1, length):
            if s[i] != s[i - 1]:
                ans += str(j) + s[i - 1]
                print(ans)
                j = 1 # reset j
            else:
                j += 1
        return ans
```
