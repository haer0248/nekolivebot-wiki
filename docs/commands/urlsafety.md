# 網址安全檢查
> 指令：`/urlsafety`  
> 權限需求：`管理伺服器 Manage Server`

成員貼的網址會送到 Google 安全瀏覽（Safe Browsing）檢查，檢查出是詐騙、釣魚或惡意軟體網站時，機器人會回覆：

> ⚠️ 這個網址有問題，請謹慎點選

並在原訊息加上 ⚠️ 反應。沒問題的網址不會有任何動作，不會每則訊息都多一個反應。

這個功能**只提醒、不刪訊息也不處分**。想直接處理詐騙連結，請搭配[自動懲處](autopunish.md)。

## 總開關

用 `/settings enable|disable url_safety` 控制（見[群組功能開關](settings.md)），預設為**未啟用**。

## 指令

* `/urlsafety check <url>`：手動檢查一個網址
* `/urlsafety status`：查看目前使用的檢查來源與略過的網域

## 略過的網域

下面這些網域（含子網域）不會送出檢查，避免每則 YouTube、Twitch 連結都查一次：

| 類型 | 網域 |
|---|---|
| Discord | discord.com、discord.gg、discordapp.com、discordapp.net、dis.gd 等 |
| 社群媒體 | facebook.com、fb.watch、instagram.com、threads.net、twitter.com、x.com、github.com、google.com、tenor.com、reddit.com、plurk.com |
| 影音串流 | youtube.com、youtu.be、twitch.tv、netflix.com、bilibili.com、nicovideo.jp、kick.com |
| 圖床 | imgur.com、giphy.com、pixiv.net |
| 自家網域 | nekolive.net 等 |

## 檢查結果的快取

同一個網址的檢查結果所有伺服器共用：沒問題的記 24 小時、有問題的記 7 天、查不到結果的記 1 小時，所以同一個網址短時間內被貼很多次，也只會查一次。

!!! info "查不到結果時不會提醒"
    Google 那邊暫時連不上，或回傳的資料看不懂時，機器人會當作「不知道」，不會提醒。寧可漏報，也不要把正常網址標成危險。
