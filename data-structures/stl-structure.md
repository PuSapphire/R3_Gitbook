---
description: 多樣的STL容器
---

# STL的容器

## 線性容器

線性容器，裡面的元素顧名思義就是一個接著一個的。

好處是如「存取第 $$k$$ 個元素」這種操作僅需 $$O(1)$$ 。壞處是對於特定指令，如區間操作、查詢元素 $$k$$ 是否包含在內等，有較爛的複雜度。

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
sk.push(9);
sk.push(1);
while (!qu.empty()) { //輸出"7 8 9 1"
  cout << qu.top() << ' ';
  sk.pop();
}
```
{% endtab %}

{% endtabs %}
