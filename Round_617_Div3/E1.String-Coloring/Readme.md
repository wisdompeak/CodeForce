### E1.String-Coloring

题意描述：给你一个字符串s，你可以将每个字符任意涂红色或者黑色。然后对于任何两个不同颜色的字符，你都可以将它们交换。问是否存在一种涂色方案，在经过有限次swap后使得整个字符串是升序排列。

本题的本质是：是否能将这个字符串分解为两个subsequence，每个子序列都是递增的。

举个例子：如果字符串可以分解如下：
```
0 0  0 00
 1 11 1
```
我们发现总可以通过01之间的移动，来将各个1放在全局的任何地方，同理也可以将任何0放在全局的任何地方，只要0与0之间（或者1与1之间）不发生相对位置的改变就行。

那么我们如何实现这样的拆分呢？很简单，建立两个字符串s1和s2，看当前的s[i]是否能接在s1上，不行的话再试一试s2。如果都接不上，那么就说明不可能实现。

