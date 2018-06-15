Python 3

1. Use dictionary (hash table) to store 7 Roman numbers and their values.
2. Scan the string from right to left: left digit < right digit -> substract; left digit >= right digit -> add 


```python
class Solution:
    """
    @param s: Roman representation
    @return: an integer
    """
    def romanToInt(self, s):
        # write your code here
        roman_numerals = {'I': 1, 'V': 5, 'X':10, 'L':50, 'C':100, 'D':500, 'M':1000}
        n = len(s)
        answer = roman_numerals[s[n - 1]]
        for i in reversed(range(n - 1)):
            current_digit = roman_numerals[s[i]]
            previous_digit = roman_numerals[s[i + 1]] 
            if current_digit < previous_digit:
                answer = answer - current_digit
            else:
                answer = answer + current_digit 
        return answer
```
