---
description: 我包含我自己?!
---

# Day 5 (12/3): import, 自定義函式, 遞迴

## Modules

Python中有很多預設的函式，比如說`max(a, b, c...)`能在一堆數字中出最大值並回傳，十分方便。

但是這些函式實在太多了，因此Python將其很大一部分塞到了其他地方。\
這就比如平時上課常用到筆，因此筆盒裡就會裝有幾隻。\
相較之下，膠水可能較少用到，因此可能放在書包裡或其他地方，雖然要拿的時候較不方便，但平時它們不會占據筆盒的空間。

同理，如`min`、`max`等常用的東西就可以直接用，而如三角函數、計算時間等，功能較為特定的函式就在平時被隱藏起來。

它們被藏到哪了呢? 這些空間叫做**模組(Module)**。想使用模組內的東西，就必須使用`import`。

我們直接舉例，並將模組當成「工具箱」來做說明:

```python
import calendar #將整個叫做「calendar」的工具箱都拿來
import sys as s #將「sys」工具箱拿來，並以「s」簡稱
from math import sqrt #從名為「math」的工具箱中拿「sqrt」出來
from math import log10 as log #從名為「math」的工具箱中拿「log10」出來，並以「log」簡稱

x = calendar.isleap(1000) # calendar.isleap → 從「calendar」工具箱中拿「isleap」來用
s.setrecursionlimit(5000) # 從「s」(也就是sys的簡稱)工具箱中拿「setrecursionlimit」來用

y = sqrt(2) # 已經知道是從math拿出來的了，就不用寫「math.sqrt(2)」
print(y) # 輸出 1.414...

z = log(2)
print(z) # 輸出 0.301...
```

Python的模組很多，模組內的函式也很多，建議自己去查查看。

## 自定義函式

一個函式可以想像成一個機器，比如`max`就是丟一堆東西進去，最大的那個吐出來。\
也有不會吐出東西的機器，比如說垃圾處理器之類的。

利用`def`語法，我們能自己寫一個函式。

```python

#只要還在縮排內，就會被當成是函式的一部分
def f(a, b, c): #定義一個叫做「f」的函式。這個函式會吃入三個東西，這三個東西被函式分別認定為「a」、「b」、「c」
  print(a + b)
  return 3*a + 2*b + c # return → 回傳東西，就如max(a, b, c...)回傳最大
  print(c) #注意: 函式return後，下面的所有東西都不會跑。
  
print(10) #輸出10。這行不被當作在f()的定義內。
  
z = f(3, 2, 1) #函式內部把3認定為a、2認定為b、1認定為c
print(z)
# 輸出 "5 14"
```

## 遞迴

所謂遞迴就是定義內包含自己。如費式數列:

$$ 
F(n) = 
\begin{cases}
  1               &\text{if $$n = 1,\ 2$$} \\
  F(n-1) + F(n-2) &\text{if $$n > 2$$}
\end{cases} 
$$

實作方面，就是使用`def`，其餘的都一樣。

Python中的遞迴為了方便debug而沒有優化，因此如果時限較緊，不建議使用。\
當然，時間複雜度仍然是最重要的。如果有遞迴 $$O(n \log n)$$ 沒遞迴 $$O(n^2)$$，那當然還是選前者。

```python
#複雜度O(n^2)，這只是示範，實際上不要這樣寫
#可以想想為什麼複雜度這麼差
def f(n):
  if n <= 2:
    return 1
  return f(n-1) + f(n-2)

#Collatz猜想的模擬
#數字=1結束，否則若為偶數則除二繼續，若為奇數則*3 + 1繼續
def collatz(k):
  print(k)
  if k == 1: 
    return
  if k % 2 == 0:
    collatz(k//2)
  else:
    collatz(3*k + 1)
    
    
#列舉所有組合:
#對每個元素，有拿或不拿兩種選擇

#想自我精進的同學，可以去查「dfs」
arr = ['a', 'b', 'c', 'd', 'e']
def dfs(memory, position):
  if index == len(arr):
    print(memory)
  else:
    dfs(memory + arr[position], position+1)
    dfs(memory, position+1)
```

理解遞迴很重要。它是許多更高階的概念，如枚舉、分治、樹狀結構等，的基石。
