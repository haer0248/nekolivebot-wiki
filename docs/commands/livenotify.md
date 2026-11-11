# Twitch 開台通知
> 指令：`/livenotify`  
> 權限需求：`管理伺服器 Manage Server`

Twitch 頻道開台時，機器人會在指定的頻道發一則通知，下面附連到直播的按鈕。可以只通知，也可以設定下播後自動刪除通知。

* 每個伺服器最多 10 個開台通知，Twitch 頻道主授權過的不算在內（見下方「頻道主授權」）
* 同一個 Twitch 頻道可以通知到不同的頻道，例如公告頻道跟聊天頻道各發一則
* 任何 Twitch 頻道都可以，不用是 Nekolive 的創作者

## 指令

| 指令 | 說明 |
|---|---|
| `/livenotify add <twitch> [channel] [delete_on_end]` | 新增開台通知。`twitch` 填帳號或頻道網址；`channel` 不填就是目前的頻道；`delete_on_end` 設成 True 會在下播後刪除通知 |
| `/livenotify remove <id>` | 移除開台通知，已經發出去的通知不會被刪掉 |
| `/livenotify list` | 列出這個伺服器的開台通知 |
| `/livenotify test <id>` | 用目前的設定送一則測試通知，不會標記任何人 |

`id` 打字時會自動列出可以選的開台通知。

## 修改通知內容

通知的文字、按鈕文字和 Embed 在[網頁控制台](../dashboard.md)的「Twitch 開台通知」修改，旁邊有即時預覽。新增時會先帶入預設的內容：

> **頻道名稱** 開台了！快來看 👉 直播網址  
> Embed：🔴 頻道名稱 正在遊玩 分類！、直播標題、直播縮圖

可以用的參數：

| 參數 | 說明 |
|---|---|
| `{channel_name}` | 頻道顯示名稱 |
| `{channel_login}` | 頻道帳號 |
| `{stream_title}` | 直播標題 |
| `{stream_category}` | 直播分類 |
| `{stream_url}` | 直播網址 |
| `{thumbnail_url}` | 直播縮圖網址 |
| `{avatar_url}` | 頻道頭像網址 |
| `{viewer_count}` | 開台時的觀看人數 |
| `{started_at}` | 開台時間 |

要標記 @everyone 或某個身分組，直接寫在訊息文字裡，輸入 @ 會列出可以選的身分組。機器人需要「提及 @everyone、@here 和所有身分組」權限才標記得到。

按鈕文字預設是「觀看直播」，最多 80 字，一樣可以用上面的參數，例如「來看 {channel_name} 玩 {stream_category}」。

## 頻道主授權

請 Twitch 頻道主打開 [bot.nekolive.net/twitch](https://bot.nekolive.net/twitch)，按「用 Twitch 授權」就完成了。授權過的頻道：

* 開台通知不算進每個伺服器 10 個的上限，所有伺服器都一樣
* 開台通知會更穩定

授權不需要任何權限，NekoliveBot 不能讀取或修改頻道的資料。想取消的話，到 Twitch 的「設定 → 連線」中斷 NekoliveBot 就可以了，取消之後這個頻道的開台通知會重新算進上限。

網頁控制台的開台通知列表會在授權過的頻道旁邊標示「已授權」。

## 下播後刪除

開了「下播後刪除通知」的話，確認下播 5 分鐘後會刪掉那則通知。中途斷線、5 分鐘內重新開台算同一場，不會重發通知，也不會刪掉。

!!! info "機器人需要的權限"
    在通知頻道需要「檢視頻道」「發送訊息」「嵌入連結」。

!!! warning "已知限制"
    機器人重新啟動的那段時間剛好開台的話，那一場不會補發通知。
