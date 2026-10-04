# Twitter／X 連結預覽
> 指令：`/settings enable|disable twitter_embed`  
> 權限需求：`管理伺服器 Manage Server`

Discord 對 Twitter／X 貼文連結的預覽常常沒有圖片或影片。開啟這個功能後，成員貼貼文連結時，機器人會回覆一則換成 `vxtwitter.com` 的連結，Discord 就會顯示完整的貼文預覽。

這是舊機器人 haer0248.me-v3 的 `/setting twitter`，搬過來之後改成用[群組功能開關](settings.md)開關，預設**未啟用**。

* 一則訊息最多轉換 4 個連結，重複的只轉一次
* 用 `<>` 包起來的連結（例如 `<https://x.com/...>`）代表發訊息的人不想要預覽，不會轉換
* 只回覆轉好的連結，不會重貼原本的訊息，也不會標記任何人

平台後台「模組設定 → Twitter／X 連結預覽」與網頁控制台也可以開關。
