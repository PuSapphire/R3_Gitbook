---
description: 用戶輸入、迴圈
---

# Day 2 (9/24)

## 讀取輸入

如果想讀入輸入可以使用`input`函式。

```python
x = input() #可以將input()視為字串，因此x此時為字串。
y = int(input()) #將輸入轉成數字。如果一行中不只有一個數字，如"1 2"、"1h"，會出錯。

print( int(input()) + 3*int(input()) ) #輸出((輸入1) + 3*(輸入2))運算結果。


z = input("請輸入選項")
#上面那行效果等同於
print("請輸入選項")
z = input()


u, v, w, m = input().split(' ') 
#也可以寫input().split()。split的()中沒有寫任何東西，預設為' '
#將輸入以' '為分界，拆成4個分別存給u v w m
#如果拆分後不只或不足4個，會出錯。
```

## 迴圈

迴圈分成for跟while兩種，語法不同。 \
`for (變數名稱) in range((數字)): `\
`(縮排) #code`

`while (判斷條件): `\
`(縮排) #code`

```python
#記得一定要縮排，否則當成在迴圈外。可按tab來縮排。

#輸出0~9，for跟while版本。
#絕大部分的程式語言喜歡從0開始數。
for i in range(10): 
    print(i)
    
x = 0
while x < 10:
    print(x)
    
##########

#以下的程式碼【沒有】問題。
#不同於C++，Python的for變數，以及在if、for、while等block內的變數，
#不會自動刪除。
j = 0
for it in range(3): #整個for輸出"0 7 0 1 8 1 2 9 2"
    x = it + 7
    print(it)
    print(x)
    print(j)
    j += 1
print(it) #2
print(x)  #9
print(j)  #3

##########

#迴圈裡面可以塞更多迴圈，稱作「巢狀迴圈」Nested loops。

for i in range(3): #整個for輸出"0 1 2 0 1 2 0 1 2"
    for j in range(3):
        print(j)
        
for i in range(3): #整個for輸出"0 1 2 A 0 1 2 A 0 1 2 A "
    for j in range(3):
        print(j)
    print(" A ")
        
for i in range(3): #整個for輸出"0 0 0 1 1 1 2 2 2"
    for j in range(3):
        print(i)
        
for i in range(9): #整個for輸出九九乘法表
    for j in range(9):
        print(i+1, 'x', j+1, '=', (i+1)*(j+1))
```

## 課後延伸

這裡順便說明一下用來判斷的運算子。\
特別注意到等於`==`，要有兩個等號。\
除了數字，字串也可以用下列的運算子進行比較。具體規則可以去參考**表單題目 Python題解**的第一題。

`<  ` 小於\
`>  ` 大於\
`<= ` 小於等於\
`>= ` 大於等於\
`== ` 等於\
`!= ` 不等於\
`and`「和」，左、右的判斷式都對才對\
`or `「或」，左、右的判斷式對一個就對\
`not`「非」，將判斷式的結果倒換。

其中`or`比`and`晚算、`and`比`not`晚算。\
但最好的方法不是記上面說的東西，而是用括號來強制規定他的運算先後。

```python
print(10 > 11)   #輸出False
print(42 < 1337) #輸出True
print(1 = 1)     #母湯
print(42 == 42)  #輸出True
print((10 > 11) == True) #輸出False
print((10 > 11) == False)#輸出True

print(10 > 11 and 42 < 1337) #輸出False
print(10 > 11 or 42 < 1337)  #輸出True
print(not 10 > 11) #輸出True

print(1<2 and 2<3 or 4<3 and 5>1)      #拜託不要這樣寫
print(((1<2 and 2<3) or (4<3 and 5>1)) #這樣寫才不會被先後順序的問題搞半天

#你看的懂下面在幹嘛嗎? 我也看不懂。
print(True and False or not False and True or False or not True and False)
```

其中`True`、`False`是特別的字，分別代表「正確」與「不正確」。 \
結合上面的`while`，一個簡單的無限迴圈可以這樣寫：

```python
while True:
    #你要無限執行的code
    
while False:
    #這裡面的東西永遠不會執行
```
