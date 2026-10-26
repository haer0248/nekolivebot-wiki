# 社交媒體預覽
> 指令：`/settings enable|disable twitter_embed`  
> 權限需求：`管理伺服器 Manage Server`

Discord 對 Twitter／X、Instagram、Threads、Facebook 的貼文連結，預覽常常沒有圖片或影片。開啟這個功能後，成員貼這些平台的貼文連結時，機器人會回覆一則修正過的連結，Discord 就會正常顯示貼文的文字、圖片與影片。

這是舊機器人 haer0248.me-v3 的 `/setting twitter`，原本只支援 Twitter／X，現在多了其他平台。用[群組功能開關](settings.md)開關，預設**未啟用**；功能的鍵值還是 `twitter_embed`，以前開過的伺服器不用重新設定。

## 支援的平台

| 平台 | 支援的連結 |
|---|---|
| Twitter／X | 貼文 |
| Instagram | 貼文、Reels、限時動態、分享連結 |
| Threads | 貼文、分享連結 |
| Facebook | 貼文、社團貼文、Reels、分享連結 |

## 規則

* 一則訊息最多轉換 4 個連結，重複的只轉一次
* 用 `<>` 包起來的連結（例如 `<https://x.com/...>`）代表發訊息的人不想要預覽，不會轉換
* 只回覆轉好的連結，不會重貼原本的訊息，也不會標記任何人

平台後台「模組設定 → 社交媒體預覽」與[網頁控制台](../dashboard.md)也可以開關。
