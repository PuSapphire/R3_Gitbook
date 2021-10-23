---
description: 跳脫字元、f-string、.format
---

# 淺談字串 <1>

在第一天社課中，教學便講了兩種資料型態，字串與數字。\
其中字串必須以`'`或`"`包起來。

然而實際上，字串遠遠不只如此如此簡單。

比如說，你實際上可以用`for`迴圈來遍歷它。

```python
 s = "Beethoven"
 for c in s:
     print(c, end=' ')
#輸出 "B e e t h o v e n"
```

## 跳脫字元

字串必須被`'`或`"`包起來。但如果我想輸出這兩個字元怎麼辦？\
對於`'`的輸出，其實並不難解決：用`"`包起來的字串，裡面的`'`不會影響輸出。\
同理，用`'`包起來的字串，裡面的`"`抑不影響輸出。

如果我想同時輸出`'`和`"`呢？這時候，就必須使用跳脫字元`\`。具體的使用方法，是將跳脫字元擺在`'`或`"`前面，這樣Python就知道他不表示字串結束了。

除此之外，跳脫字元還能用來表示其他較特殊的字元，比如換行字元`\n`。\
跳脫字元常用的情況有：\
`\n` → 換行\
`\\` → 輸出`\`字元\
`\'` → 輸出`'`字元\
`\"` → 輸出`"`字元

```python
print('Where's my superhero suit?')    #看顏色就知道，母湯。
print("It's a beautiful day outside.") #可以

print("Dwayne "The Rock" Johnson is a famous celebrity.") #母湯
print('"Good job." Said Anne.') #可以

print("It's no use. "Juuust Great." Said Anne.")    #母湯
print('It's no use. "Juuust Great." Said Anne.')    #母湯
print("It's no use. \"Juuust Great.\" Said Anne.")  #可以。
print("It\'s no use. \"Juuust Great.\" Said Anne.") #可以。
print('It\'s no use. "Juuust Great." Said Anne.')   #可以。

print("Hello\nMy name is\n Rick.") 
#輸出
#Hello
#My name is 
# Rick.

print("\\\\\\\\") #輸出"\\\\"
```

## F-string與.format()

如果說我想要這樣的一個字串：\
(數字A) + (數字B) \* (數字C) - (數字D) = (運算結果)\
固然可以用str將數字轉換成字串，再用+接起來。但這樣好難讀，又好麻煩喔！

```python
a = 9
b = 4
c = 8
d = 9
s0 = str(a)+" + "+str(b)+" * "+str(c)+" - "+str(d)+" = "+str(a+b*c-d)
print(s0)
```

### string.format()

我們可以利用`string.format()`函式來達成我們想要的效果。\
首先，將原先的字串中置入`{}`，代表接下來要帶入東西的位置。\
其中，大括號裡面可以放名字`{變數名}`，或特殊順序`{順序}`，或甚麼都不放`{}`。\
甚麼都不放，就等同於由左至右塞入。

注意，如果用了`{}`就不能用`{順序}`。

```python
s1 = "{} + {} * {} - {} = {}"
print(s1.format(9, 4, 8, 7, 9+4*8-7))
#輸出"9 + 4 * 8 - 7 = 34"

s2 = "time is {a} and we're {state}"
print(s2.format(state="late", a="03:35"))
#輸出"time is 03:64 and we're late"
 
s3 = "{2}, {1}, {0} {0} {0}!"
print(s3.format("go", "set", "ready"))
#輸出"ready, set, go go go!" 


#要注意，包順序的放前面，用(名字)=...指定的放後面
dislike = "spiders"
person_job = "nurse"
s4 = "{name} is a {job}, and she hates {0}, {2}, and {1}"
print(s4.format("bugs", dislike, "crabs", name="Stella", job=person_job))
#輸出 "Stella is a Nurse, and she hates bugs, crabs, and spiders"

print(s4.format(name="Stella", "bugs", dislike, "crabs", job=person_job))
#母湯
```

但即便如此，`.format()`感覺還是好長好麻煩喔。

### F-string

沒關係，自Python 3.6開始，有更簡潔的東西能用——`f-string`！

`f-string`的語法，即在字串前加上`f`或`F`，接下來的內容就與`.format()`十分相似。

不同的是，`f-string`的`{變數名}`會直接從程式中抓出那個變數塞進去，這樣就不用什麼`job=person_job`之類的鬼東西了。除此之外，`f-string`還有`{算式}`語法，讓一切變得簡單許多。

`f-string`沒有`{}`或`{順序}`的語法。

`f-string`的`f`或許還有`fast`的意思(滑稽.jpg)，因為`f-string`比`.format()`，以及這裡因為基本上算是被淘汰的字串`%`，還要快許多。

```python
name = "Es"
weapon = "Sword"
print(f"{name} is a {weapon} user.")
#輸出 "Es is a Sword user."

cps = 64
sec = 12
print(f"{name} can cut {cps*sec} times in {sec} seconds.")
#輸出 "Es can cut 768 times in 12 seconds."
```
