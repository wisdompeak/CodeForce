### A.Stock_Arbitraging

卖出价肯定是选择最高的，没有什么好说的。

买入价的确定，需要考虑两个因素：既要充分利用手头的钱，又要尽可能地买入最便宜的。显然同时存在两个目标是无法做的，我们就转换成，如果给定的钱是r，购入哪些买入价能赚最高的利润？显然这就是一个背包问题。
```cpp
for (int r=1; r<=maxVal; r++)
  dp[r] = max { dp[r-Pi] + (sell-Pi) } for 各种买入价Pi
``` 