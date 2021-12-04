---
description: 學Python的伊始
---

# Day 1 (9/10): 基礎輸出、基礎運算、基礎變數

## 基礎輸出

如果要Python輸出，可以使用`print(要輸出的東西)` 函式。

```python
print(100000)  #輸出100000
print('hello') #輸出hello
```

## 基礎運算

可以用以下**運算符號**對Python的數字進行操作。\
運算時，先次方，再乘除、取餘數商數，最後加減。\
特別注意到`^`，它不代表次方。\
`+ `加\
`- `減\
`* `乘\
`/ `除\
`//`取商數\
`% `取餘數\
`**`次方

```python
print(100 + 200 * 3) #輸出700
print((2 - 7) * 6)   #輸出-30
print(7 / 2 ** 2)    #輸出1.75
print(5 ^ 4)         #輸出1
print(5 ** 4)        #輸出625
print(11 // 3)       #輸出3
```

## 基礎變數

想將**資料儲存**下來時就要使用到變數。\
想宣告一個變數，或者改變變數的值，可以寫`(變數名稱) = (給他的值)`。\
注意，變數名稱不可以以數字為開頭、中間也不能有空格。

```python
123drink = "beer"    #母湯
good snack = 'candy' #母湯

name_1 = "John" #現在叫做name_1的變數等於"John"
hahaxd = 10     #現在叫做hahaxd的變數等於10
rofl = 4201773  #現在叫做rofl的變數等於4201773
time = '06:25'  #現在叫做time的變數等於'06:25'

rofl = "funny joke" #rofl被改成"funny joke"
time = 3.1415       #time被改成3.1415

print(hahaxd + time)#輸出13.1415
```

## 課後小延伸

基礎運算中提到的加`+`和乘`*`也可以對字串進行運算。\
運算結果很直觀，不太複雜。\
`(字串1) + (字串2)`→ 將`字串1`、`字串2`接起來。 \
`(字串1) * (數字n)`→ 將`字串1`的內容重複`n`次。

```python
s1 = 'foo'
s2 = 'bar'
print(s1 + ' ' + s2) #輸出 "foo bar"
print(s1 + s2 * 3)   #輸出 "foobarbarbar"
print(s2 * '1337')   #母湯 字串不能乘以字串。

s3 = (s1 + 'baz' + s2) * 2
s4 = '   ' + s2 * 5
print(s3) #輸出 "foobazbarfoobazbar"
print(s4) #輸出 "   barbarbarbarbar"
```
