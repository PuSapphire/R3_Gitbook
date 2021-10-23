---
description: '"小小的測驗" C++篇'
---

# 表單題目 C++題解

## C++ 0：^ 運算子

```cpp
//執行以下程式碼會輸出?
#include <iostream>
using namespace std;

int main() {
    int x = 5;
    cout << (x ^ 4);
    return 0;
}
```

**答：１**

`^`是位元運算子(Bitwise Operator)中的`XOR`，對應到布林運算的`!=`。\
計算時，先分別將5、4拆成二進制，並將兩者直式排列。\
對於每一位數字，如果兩者不同則算出1，否則算出0。\
最後，將運算結果換回十進位。

![](<../.gitbook/assets/form c0.jpg>)

###

## C++ 1：char與int

```cpp
//執行以下程式碼會輸出?
#include <iostream>
using namespace std;

int main() {
    for (char i='a'; i<='d'; i++) {
        cout << i+1 << ' ';
        if (i == 'c') continue;
    }
    return 0;
}
```

**答：以上皆非（正解："98 99 100 101"） **

`char`與`int`其實可以互相轉換，具體可參考[ASCII表](https://en.cppreference.com/w/cpp/language/ascii)中的`dec`欄位。\
`char`加上數字後就會被替換成`int`。如果想轉回來則必須`cast`，如：

```cpp
#include <iostream>
using namespace std;

int main() {
    for (char i='a'; i<='d'; i++) {
        cout << char(i+1) << ' ';
        if (i == 'c') continue;
    }
    return 0;
}
//輸出 "b c d e"
```

`continue`的意思是「跳回迴圈最上層」，但我們已經先`cout`了，因此這行對輸出無影響。

```cpp
#include <iostream>
using namespace std;

int main() {
    for (int i=0; i<=6; i++) {
        if (i == 3) continue;
        cout << i << ' ';
    }
    return 0;
}
//輸出 "0 1 2 4 5 6"
```

## C++挑戰題：動態規劃

```cpp
//若要形容以下程式碼，最符合的敘述是?
#include <iostream>
using namespace std;

int func(int w[], int v[], int n, int k) {
    int dat[n][k];
    for (int i=0; i<n; i++) {
        for (int j=0; j<k; j++) {
            dat[i][j] = 0;
        }
    }
    
    for (int i=0; i<n; i++) {
        for (int j=k-1; j>w[i]; j--) {
            if (i == 0) {
                dat[i][j] = v[i][j]
            }
            else {
                dat[i][j] = max(dat[i-1][j], dat[i-1][j-w[i]]+v[i]);
            }
        }
    }
    return dat[n-1][k-1]
}
```

**答：動態規劃**

**動態規劃(Dynamic Programming)**，指的是記錄先前計算的結果，用於後面的計算。 \
要具體一點形容的話，就是在填表格。

試問，擲3顆1\~6點的骰子，請問點數和為10的情況有幾種？ \
我們可以這樣想： \
10 = 9+1 = 8+2 = 7+3 = 6+4 = 5+5 = 4+6 \
所以，點數的情況就是 \
(前兩顆和=9，第三顆骰1) \
(前兩顆和=8，第三顆骰2) \
... \
(前兩顆和=4，第三顆骰6)

延續這樣的辦法，前兩顆和=9的情形： \
9 = 8+1 = 7+2 = 6+3 = 5+4 = 4+5 = 3+6 \
我們繼續往下看，前兩顆和=8的情形： \
8 = 7+1 = 6+2 = 5+3 = 4+4 = 3+5 = 2+6

可以發現，骰到**第n顆骰子和為s的情形**，可以從骰到**第n-1顆骰子**時，**和為(s-1, s-2..., s-6)的情形**推得**。**

![骰骰子的點數情形，是在「填表格」](<../.gitbook/assets/form c2 DP.jpg>)

可以發現，n骰s點的問題**可以被拆成許多小問題**(n-1，{s-1, s-2..., s-6})，然後小問題可以再被拆成更小的問題，並且透過**計算小問題，能夠推得大問題的答案**。

在這樣的過程中，會有許多的**資料一直被重複使用**，既然如此，不如**算完一次就先儲存起來**（填表格），下次使用時就不用重新再算了。

回到程式碼，在第19行： \
`dat[i][j] = max(dat[i-1][j], dat[i-1][j-w[i]]+v[i]); `\
就用到了先前的計算結果。

P. S：其實這段程式碼是一題非常經典題目的解答。

P. P. S：其實Google表單上的題目程式碼打錯了。你有發現嗎？
