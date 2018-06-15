Python 3

(1) Check the input if it is empty
(2) Scan from the right to the left. Find the max and its subsiquent min (marching left). If we find the next max value (greater than the current max), then we update the low and high values. Before updating the low and high values, we need to update the max_profit variable (done by a function). Time: O(n)
(3) 2 Cases: Fluctuation price or Monotonic price


``` python
class Solution:
    """
    @param prices: Given an integer array
    @return: Maximum profit
    """
    def maxProfit(self, prices):
        # write your code here
        
        # input check
        if not prices:
            return 0
        
        # initialization    
        self.max_profit = 0
        high = prices[-1]
        low = prices[-1]
        
        def update_max_profit(profit):
            if profit > self.max_profit:
                    self.max_profit = profit
        
        # scan from right to left
        # Fluctuation case: find the local max and subsequent local min.
        # Updtate the high (and low) when it encounters the next max.
        for i in reversed(prices):
            if i > high:
                update_max_profit(high - low)
                high, low = i, i # reset high/low values
            if i < low:
                low = i

        # Monotonic case.
        if high != low:
            update_max_profit(high - low)
        
        return self.max_profit
	```
