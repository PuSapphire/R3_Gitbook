---
description: 列表推導式List Comprehension
---

# 列表推導式 List Comprehension

## 列表推導式 List Comprehension

在[Day 4](/Review/day4-11-5.md)中，我們提到空格隔開的測資可以使用`.split()`函式進行輸入。\
然而，這樣的方式輸入進來的是字串。如果我們想要他全都是數字型態以進行運算，可以怎麼做?

```python
x, y, z = input().split() #x, y, z都是字串
x = int(x)
y = int(y)
z = int(z)

arr = input().split() #list內的東西都是字串
for i in range(len(arr)):
  arr[i] = int(i)
 
#計算...這樣寫真麻煩。
```

有更好的方法。\
列表推導式(List Comprehension)是Python中一個十分強大的語法，可以在一行內創建十分複雜的List，而又不失其可讀性。\
而它超廣泛用途的其中之一，就是讓入空格隔開的測資時，就將他們通通轉成數字。\
（小提醒：`string.split()`回傳的東西是List。）

```python
x, y, z = [int(i) for i in input().split()]
arr = [int(i) for i in input().split()]
#直接就可以計算了!
```

是不是寫起來很快? 很好讀? 很方便?\
學Python其中一定一定要會的偷懶方式就是這個List Comprehension。

---

List Comprehension包含了表達式、後面接`for`跟`in`，並在後面能接更多的`if`或`for`。\
語法如下：

```py
new_list = [(表達式) for (物品) in (可迭代容器) if (狀態)]
```
(物品)、(表達式)可以想像成一個函數的x與其對應的y。如果表達式跟物品完全沒關係，就可以想像成常數函數。\
(可迭代容器)不懂沒關係，只要知道他包含`list`、`range`就好了。

當然List Comprehension還有更複雜的方法，不過上面的寫法足以應付大部分需求了。\
以下是幾個例子。

```python
arr = [7 for i in range(5)]
# arr = [7, 7, 7, 7, 7]

arr = [i+7 for i in range(5)]
# arr =[7, 8, 9, 10, 11]

arr = [i for i in range(100) if i%2==0]
# arr = 包含所有小於100的偶數的陣列

arr = [int(i) for i in input().split()]
# 將以空格分開的輸入，轉成數字存在list中

arr = [float(i) for i in input().split()]
# 將以空格分開的包含小數的輸入，轉成數字存在list中

arr = [int(i) for i in input().split() if i > 0]
# 將以空格分開的輸入，轉成數字並取其大於零的存在list中

arr = [int(i)**2+7 for i in input().split()]
# 將以空格分開的輸入，每個數字取次方並加7，存在list中
```

## 更複雜的List Comprehension

```python
arr = [[x, y] for x in [1, 2, 3] for y in [3, 4, 5] if x != y]
# arr = [[1, 3], [1, 4], [1, 5], [2, 3], [2, 4], [2, 5], [3, 4], [3, 5]]

matrix = [
  [1, 2, 3, 4],
  [5, 6, 7, 8],
  [9, 10, 11, 12],
]
arr = [[row[i] for row in matrix] for i in range(4)]
# arr = [[1, 5, 9], [2, 6, 10], [3, 7, 11], [4, 8, 12]]
