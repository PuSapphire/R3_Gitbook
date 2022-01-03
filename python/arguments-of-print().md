---
description: Arguments of print()
---

# print()函式的參數

`print()`有很多可省略不填的參數。\
以下為較為（但仍不）完整的print()，剩餘的參數因使用率較低而不講。

`print((物件1), (物件2)..., sep=(輸出分隔字元), end=(結尾輸出))`\
`物件n`：要輸出的東西，比如`13`、`"l33th4x0r"`等。\
`sep`：輸出的每個物件之間要輸出的字元。沒有填的話默認是空格`' '`\
`end`：所有物件輸出後輸出的字元。沒有填的話默認是換行符號`'\n'`

其中`sep`、`end`必須是字串。

上面的文字敘述可能讓你滿臉黑人問號，以下附帶幾個例子。

```python
x = 10
y = 15
s = "hello"
t = "world"

print()
#甚麼都不輸出，然後換行。

print(x, y) 
print(x, y, sep=' ', end='\n')
#以上兩行程式碼，在內部運行時完全相等。
#輸出: "10 15" 換行。

print(x, t) 
print(x, t, sep=' ', end='\n')
#以上兩行程式碼，在內部運行時完全相等。
#輸出: "10 world" 換行。

print(x, y, end='numbers be like') 
#輸出: "10 15 numbers be like" 不換行。

print(s, x, t, sep='') 
#輸出: "hello10world" 換行。

print(x, y, s, t, sep='---', end=" and that is it.")
#輸出: "10---15---hello---world and that is it." 不換行。

print("x=", x, "y=", y, "so x+y=", x+y, sep='/', end='. So easy.\n')
#輸出: "x=/10/y=/15/so x+y=/25. So easy." 換行。

print(1, 2, 3, sep='\n', end='uvuevuevue')
#輸出:
#1
#2
#3uvuevuevue 最後不換行。

print(5, x, s, sep='\n\n', end='\n\n\n')
#輸出:
#5
#
#10
#
#hello 最後換三行。
```
