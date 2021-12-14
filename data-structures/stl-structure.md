---
description: 多樣的STL容器
---

# STL的容器

## 線性容器

線性容器，裡面的元素顧名思義就是一個接著一個的。

缺點是對於特定指令，如區間操作、查詢元素 $$k$$ 是否包含在內等，有較爛的複雜度。

{% tabs %}
{% tab title="vector" %}

`vector`可以想像成可更改大小的陣列。除此之外，還有一些其他好用的函式可用。

**不能提前得知陣列需要開多大**時，常用`vector`來寫。

常用函式複雜度:

| 函式1 | 複雜度1 | 函式2 | 複雜度2 |
| --------------- | -------- | -------------- | -------- |
| `.front()`      | $$O(1)$$ | `.back()`      | $$O(1)$$ |
| `.size()`       | $$O(1)$$ | `vector[n]`    | $$O(1)$$ |
| `.pop_back()`   | $$O(1)$$ | `.push_back()` | $$O(1)$$ |
| `.empty()`      | $$O(1)$$ | `.clear()`     | $$O(n)$$ |
| `.erase(it)`    | $$O(n)$$ | `.erase(l, r)` | $$O(n)$$ |
| `.insert(p, v)` | $$O(n)$$ | `.resize(n)`   | $$O(n)$$ |

```cpp
#include <vector>
#include <algorithm>

vector<int> v; //宣告儲存int的vector
vector<float> a(10); //宣告儲存float的vector，且大小開10
vector<char> c(3, 'l') //宣告儲存char的vector，且大小為5，並將'l'填入這些空格
vector<vector<int>> adj(2, vector<int>(3, -1)); //宣告儲存vector<int>的vector...
//v = {}
//a = { , , , , , , , , , } (這裡的空格是指仍未initialize的值)
//c = {'l', 'l', 'l'}
//adj = {{-1, -1, -1}, {-1, -1, -1}}

//輸出"0 9 3 2" 
cout << v.size() << ' ' << a.size() << ' ' 
     << c.size() << ' ' << adj.size();
     
//輸出 "1 0 0 0"
cout << v.empty() << ' ' << a.empty() << ' '
     << c.empty() << ' ' << adj.empty();
     
v.resize(3); //v的大小現在為3
c.resize(4); //c的大小現在為4，也就是只多開了1格。c = {'l','l','l', }
v.resize(4, 7); //v = { , , , 7};
a.resize(5); //沒有效果
a.shrink_to_fit(5); //a的大小現在為5，4個元素被刪除

cout << v[3] << ' ' << c[2]; //輸出"4 l"
c.push_back(); //c = {'l','l','l', ,'a'}
v.pop_back(); //v = { , , }
cout << c.front() << ' ' << c.back(); //輸出"l a"
adj.clear(); //刪除所有元素。adj = {}
c[0] = 'b'; c[1] = 'k'; //c = {'b', 'k', 'l', , 'a'}
c.erase(c.begin()+2); //刪除元素(用iterator)。 c = {'b', 'k', , 'a'}
c.erase(c.begin(), c.begin()+2); //區間刪除。c = { , 'a'}
c.insert(1, 'z'); //c = { , 'z', 'a'}
v = {7, 3, 1, 6, 9, 2};
sort(v.begin(), v.end()); //v = {1, 2, 3, 6, 7, 9}
```
{% endtab %}

{% tab title="stack" %}

可以想像成疊盤子。新的盤子疊在最上方，要拿盤子時也是先拿最上面(最新)的。

常用函式複雜度:

| 函式1 | 複雜度1 | 函式2 | 複雜度2 |
| --------------- | -------- | -------------- | -------- |
| `.top()`        | $$O(1)$$ | `.pop()`       | $$O(1)$$ |
| `.push()`       | $$O(1)$$ | `.empty()`     | $$O(1)$$ |
| `.size()`       | $$O(1)$$ | 

```cpp
#include <stack>

stack<int> sk;
sk.push(7);
sk.push(8);
cout << sk.top(); //輸出8
sk.push(9);
sk.push(1);
while (!sk.empty()) { //輸出"1 9 8 7"
  cout << sk.top() << ' ';
  sk.pop();
}
```

{% endtab %}

{% tab title="queue" %}

可以想像成在排隊。新的人排後面，最早來的人先出來。

常用函式複雜度:

| 函式1 | 複雜度1 | 函式2 | 複雜度2 |
| --------------- | -------- | -------------- | -------- |
| `.front()`      | $$O(1)$$ | `.pop()`       | $$O(1)$$ |
| `.push()`       | $$O(1)$$ | `.empty()`     | $$O(1)$$ |
| `.size()`       | $$O(1)$$ | 

```cpp
#include <queue>

queue<int> qu;
qu.push(7);
qu.push(8);
cout << qu.front(); //輸出7
qu.push(9);
qu.push(1);
while (!qu.empty()) { //輸出"7 8 9 1"
  cout << qu.top() << ' ';
  qu.pop();
}
```
{% endtab %}

{% endtabs %}

## 非線性容器

**非線性容器**就如其名，其內部並非傳統的一段連續記憶體。這類的STL容器包含：
* 內部常為**平衡二搜樹**的`set`、`map`以及允許相同的`key`存在的對應`multi`容器。
* 內部常為**哈希表**的`unordered`系列。
* 內部常為**Heap**的`priority_queue`。

由於資料沒有存在一段連續的記憶體內，**「位置先後」的概念變得沒有意義**。
因此，`arr[i]`代表對`第i個元素`直接進行存取的語法，是不存在的。

相對地，想要存取這類容器內部的資料，就必須與`iterator`跌代器打交道。
跌代器就是一種類似指標`pointer`，用於走訪容器的東西。`STL`容器基本上都有這種東西。

以某`STL`容器`ctr`為例，`ctr.begin()`、`ctr.end()`分別指向容器「最前端的元素」與「最後端後面的記憶體虛空(也就是沒有東西)」。
如單純的`set`，內部元素由小排到大，此時的`.begin()`即指向`set`中最小的元素；`.end()`即指向`set`中最大元素後面的記憶體虛空。

至於`iterator`是怎麼知道接下來要移動到哪裡的記憶體讀取資料的，這個可以自己去看，由於對實際撰寫程式來說毫無相關，本篇不做描述。

{% tabs %}
{% tab title="set, map, multi" %}

`set`與`map`其實是同一種東西，內部通常以平衡二搜樹實作，只不過`map`儲存的元素會對應到另一個元素。兩者差異真的不大。

`multi`的容器被允許儲存多個`key`相同的元素，但也因此某些函式無法使用。

| 函式1 | 複雜度1 | 函式2 | 複雜度2 |
| ----------------- | ------------- | ----------------- | ------------- |
| `.begin()`        | $$O(1)$$      | `.end()`          | $$O(1)$$      |
| `.size()`         | $$O(1)$$      | `.empty()`        | $$O(1)$$      |
| `.insert(e)`      | $$O(\log n)$$ | `.erase(it)`      | $$O(\log n)$$ |
| `.find(e)`        | $$O(\log n)$$ | `.count(e)`       | $$O(\log n)$$ |
| `.lower_bound(e)` | $$O(\log n)$$ | `.upper_bound(e)` | $$O(\log n)$$ |

其中，`lower_bound()`、`upper_bound`，`vector`也有，只不過你必須保證`vector`呈遞增或遞減。

```cpp
#include <set>
#include <map>
#include <multiset>
#include <multimap>

set<int> st;
map<int, string> map; //int 對應到 string

set.insert(17);
map[1337] = "elite"; //map[e] -> 存取 e 對應的值
map.insert({420, "blazeit"}; 

```
