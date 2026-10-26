# 清除成員
> 指令：`/prune member [role]`、`/prune whitelist`  
> 權限需求：`踢出成員 Kick Members`

一次踢出很久沒整理、沒有身分組的成員。

## 清除：`/prune member [role]`

* 不填身分組：踢出**沒有任何身分組**的成員
* 填了身分組：只踢出「**只有這一個身分組**」的成員，同時有其他身分組的不會動；不能選 @everyone，也不能選位階不低於你的身分組

下指令後不會馬上踢人，會先列出符合條件的人數、前 20 位和完整名單（附件），按「確認踢出」才會執行，名單 10 分鐘內有效，只有下指令的人可以確認或取消。

以下的人一定不會被踢：

* [白名單](#prune-whitelist)裡的成員
* 伺服器擁有者、你自己、機器人帳號
* 身分組位階比機器人高（機器人踢不動），或位階不低於你的成員

按確認時會再檢查一次，這段時間內身分組變了、已經離開、或剛被加進白名單的人都會略過。

!!! note "踢出不是封鎖"
    被踢出的人之後還能用邀請連結回來。要封鎖請用 [`/pban`](pban.md)。

## 白名單：`/prune whitelist` {#prune-whitelist}

* `/prune whitelist add <user> [reason]`：加進白名單
* `/prune whitelist remove <user>`：移出白名單
* `/prune whitelist list`：列出白名單

每個伺服器各自一份，[網頁控制台](../dashboard.md)的「清除成員」頁也能管理。
