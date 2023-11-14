For example, we have a list
`size = [13, 14, 16]`, and now need to unpack these variables

1/ [X]不符合最佳实践 
```
small = size[0]
medium = size[1]
large = size[2]

del small, medium, large
```
2/ [X]不符合最佳实践
```
small, medium, large = size[0], size[1], size[2]

del small, medium, large
```
3/ [√]符合最佳实践 
```
small, medium, large = size
small
medium
large
```

4/ 不用担心，混合变量也可以拆分
```
laptop = ['mbp', 16, 3299.00, (149.18, 24, 7.99, 3580.39)]

brand, screen_size, price, financing = laptop
or
brand, screen_size, price, (per_month, months, rate, total_cost) = laptop
```

5/ 如果左右到变量的数量不匹配，会报错
```
size = [13, 14, 16]
e_small, e_medium = size
```

6/ 字符串同样可以拆分，因为字符串本身也是可以循环的
```
string = 'Apple'
a, b, c, d, e = s
```

7/ 只保留需要的变量
```
laptop = ['mbp', 16, 3299.00, (149.18, 24, 7.99, 3580.39)]
如果只想保留直接购买的价格，和分期付款的总价格，然后计算分期付款的利息成本，可以这样做
_, _, price, (_, _, _, total_cost) = laptop
```
最懒的程序员就是最优秀的程序员！
下面这个方案更棒！
```
*_, price, (*_, total_cost) = laptop
price
total_cost
interest_cost = total_cost - price
```