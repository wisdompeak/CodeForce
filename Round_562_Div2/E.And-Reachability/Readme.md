### E.And-Reachability

本题是说，给一堆nums和两个索引x和y。问是否能在```[x,y]```之间找出若干个顺序的索引pi，使得相邻的nums[p_i]和nums[p_i+1]的“位与”都不为零。

我们定义next[i][k]表示从i开始，下一个可以到达的、且第k个bit位是1的索引。如果nums[i]本身的第k个bit位是一，那么定义next[i][k]=i本身。

另外定义latest[i][k]表示从i开始，下一个第k个bit位是一的索引。注意，latest严格不包括i本身；并且从i不一定能达到latest[i][k]。这里，因为不涉及“到达”的约束，所以latest[i][k]我们不难预先计算出来。

接下来，如何更新next[i][k]呢？既然不知道怎么去判定下一个能“到达”的位置，那就从一定可以判定“到达”的位置入手！对于nums[i]而言，如果它的第j位为一，那么显然一定可以从i到达latest[i][j].然后我们就可以再进一步，一定可以走到next[latest[i][j]][k].事实上，遍历所有的j的可能（从0到31），得到的最小一个next[latest[i][j]][k]，就是next[i][k]。

对于给定的[x,y]，我们只要遍历所有y里面不为零的位j，看看next[x][j]=p是否小于y。如果有的话，就说明从x可以“到达”p，而p与y在第j位上又都是一，说明p一定可以到达y的。这就证明了索引x可以“到达”索引y。
