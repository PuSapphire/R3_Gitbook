# 基礎語法

{% tabs %}
{% tab title="Python" %}
```python
#Python程式由上而下執行
x, y = 2, 3       #宣告變數
z = input()       #讀取輸入
u, v = input().split(' ') #讀取由空格隔開的輸入

print(x + y)      #輸出
print(z, end=' ') #輸出而不換行，以單空格結尾

#跑到最下面，Python程式結束
```
{% endtab %}

{% tab title="C++" %}
```cpp
#include <iostream>  //標頭檔
using namespace std; //使用std內的函數

int main() {   //執行時，會自動從main()開始執行
    int x, y;  //宣告變數
    int z = 3;
    
    cin >> x;  //讀取輸入
    cout << z; //輸出
    return 0;  //結束main()函式，不要隨意更改，但在較新編譯器中可省略
}
```
{% endtab %}
{% endtabs %}

{% hint style="info" %}
小知識：\
\
C++主要以分號`;`與大括號`{ }`來區分「不同區塊」的程式碼，所以編寫C++時其實不必縮排也不必換行，你想要把你的程式全部擠成一行也沒關係。（但你的眼睛會恨你）\
\
Python主要以`縮排`來區分「不同區塊」的程式碼，所以必須縮排，否則會出現錯誤。
{% endhint %}

以下是部分常用的基礎變數型態。

| C++                                                                                                                             | Python                                                                                     | 儲存資料                                                                                                                                                                                      |
| ------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <p><code>int x;</code></p><p><code>int y = 0;</code></p><p><code>int z;</code></p><p><code>cin >> z;</code></p>                 | <p><code>y = 0;</code></p><p><code>z = int(input())</code></p>                             | <p>整數。 <br><br>注意，C++中的int只能儲存到<code>(2的31次方)-1</code>。<br>Python的數字則無限制。</p>                                                                                                             |
| <p><code>string s;</code></p><p><code>string line = "cool"</code></p><p><code>string p;</code></p><p><code>cin >> p;</code></p> | <p><code>s = ""</code></p><p><code>line = "cool"</code></p><p><code>p = input()</code></p> | <p>字串，如"Hello world" 、"你們好"<br><br>C++的字串，必須用<code>"</code>符號包起來。 <br><br>Python的字串，必須用<code>"</code>或<code>'</code>符號包起來。</p>                                                            |
| <p><code>float f;</code></p><p><code>float g = 1.23;</code></p><p><code>float h;</code></p><p><code>cin >> h;</code></p>        | <p><code>g = 1.23</code></p><p><code>h = float(input())</code></p>                         | <p>小數。 <br><br>注意，由於電腦儲存資料的方式，<br>小數在運算時可能產生誤差。</p>                                                                                                                                       |
| <p><code>bool b = true;</code></p><p><code>bool check = 1;</code></p>                                                           | <p><code>b = 1</code></p><p><code>check = True;</code></p>                                 | <p>布林值，只能是<code>1 (True)</code>或<code>0 (False)</code>。<br></p><p>注意C++中的<code>true</code>、<code>false</code>是小寫、<br>Python中的<code>True</code>、<code>False</code>是大寫。<br><br>記憶體使用量小。</p> |

