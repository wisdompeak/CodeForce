### C.Skyscrapers

显然，每题要求答案中的所有元素组成一个单峰的上凸函数。我们容易想到，如果固定某个元素是peak，那么很容易往左往右走一遍把其他位置的高度都确定下来。但遍历所有的peak再走一遍，那就是o(N^2)的复杂度。

我们再研究，如果任意取i为peak再往左到底的“山坡”，与任意取j为peak再往左到底的“山坡”，会有一定程度的相似性。这是为什么，以及该如何利用呢？

我们任取位置i作为peak来考虑。我们考虑i之前的prev smaller，假设位置为j。那么[i+1,j]之间都是比m[i]大的元素，所以这段区间内的gain就可以直接计算为```(i-j)*m[i]```。接下来[0,j]这部分区间的gain怎么算呢？其实这就和以j为peak的左端收益完全等价了。因此我们可以有如下的状态转移方程：
```
left[i] = left[prev[i]] + (i-prev[i])*m[i]
```
其中left[i]表示以i为peak的左端收益。同理我们可以计算right[i]表示以i为peak的右端收益。那么以i为peak的总收益就是：
```
left[i]+right[i]-m[i]
```
于是我们遍历一遍left和right，就可以挑出最好的位置作为peak。
