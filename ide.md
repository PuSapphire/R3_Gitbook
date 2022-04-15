---
description: Python IDE - Anaconda Spyder
---

# 編譯環境

## 線下編譯

首先到[官網](https://www.anaconda.com/products/individual-d#Downloads)下載符合作業系統的Installer。

![](<.gitbook/assets/Tut 0.jpg>)

\
打開Installer，除了安裝路徑可修改以外，其他選項不需要碰。\
"Setting up the base environment ..." 的部分會跑比較久。

![](<.gitbook/assets/Tut 1.jpg>)

安裝完成後，可以在工作列中找到它。

![](<.gitbook/assets/Tut 2.png>)

或者，在檔案總管中，將以下文字複製貼上。\
`(安裝路徑)\pythonw.exe (安裝路徑)\cwp.py (安裝路徑)\anaconda3 (安裝路徑)\pythonw.exe (安裝路徑)\Scripts\spyder-script.py`

![](<.gitbook/assets/Tut 2.1.png>)

![](<.gitbook/assets/Tut 3.png>)

即可使用Spyder來寫Python。 \
如果需要換成中文，可以依照以下步驟來做。

![](<.gitbook/assets/Tut 4.jpg>)

![](<.gitbook/assets/Tut 5.jpg>)

## 線上編譯環境

如果不想下載，可以到[這個網站](https://replit.com/\~)線上編寫。 \
登入時可使用Google帳號。

注意，需要編譯的程式語言（如C++）運行會較慢，且受網速影響。\
Python為直譯式語言，速度較不受影響（但非沒有）。

由於**介面為全英文**，在此不多解釋。 \
想使用的社員可以自行前往摸索。

# 更多import

用Anaconda裝Spyder來跑Python會自帶許多常用的module，直接import即可。

如果沒有，可以自行使用pip安裝。對於大部分的module，只要打開Anaconda Prompt(如上面搜尋Spyder的方式尋找到它)並輸入"pip install (名稱)"即可安裝完畢。
