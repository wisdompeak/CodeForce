### D.Dirty-Deeds-Done-Dirt-Cheap

其实本题的解法非常简单。

对于x<y的(x,y)配对，我们按照y从小到大排列：
```
        x3__________________y3
  x2___________________y2
    x1_________y1
x0_____y0
```
我们发现，从后往前的(x,y)，永远满足 ```x3<y3 > x2<y2 > x1<y1 > x0<y0 ....```


对于x>y的(x,y)配对，我们按照y从大到小排列：
```
                y0_____x0
                    y1____________x1
                        y2____________x2
                            y3____x3
```
我们发现，从前往后的(x,y)，永远满足 ```x0>y0 < x1>y1 < x2>y2 < x3>y3....```

也就是说，想要让同一个类型的(x,y)按照上述规则关联起来，永远都是有解的！
