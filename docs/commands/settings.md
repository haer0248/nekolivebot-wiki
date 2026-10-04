# 群組功能開關
> 指令：`/settings`  
> 權限需求：`管理伺服器 Manage Server`

機器人的功能可以個別開關，不想用的可以直接關掉。

* `/settings list`：查看此群組目前所有功能的啟用狀態
* `/settings enable <feature>`：啟用指定功能
* `/settings disable <feature>`：停用指定功能

!!! note "開關跟設定 (config) 是分開的"
    功能開關只決定「這個功能要不要執行」，實際偵測規則與處理動作（要不要自動踢出、封鎖、禁言、通知等功能）於另外用各自的 `config` 指令設定，例如 `/antispam config`、`/honeypot config`、`/accountcheck config`。

## 目前有哪些功能？

| 功能 | 鍵值 | 說明 | 預設 |
|---|---|---|---|
| [洗版偵測](antispam.md) | `anti_flood` | 偵測到有人短時間內大量發送訊息（洗版）時，依設定通知群組擁有者、刪除訊息、禁言、踢出或封鎖。 | 啟用 |
| [全域黑名單](blacklist.md) | `blacklist_alert` | 接收或自動偵測於平台黑名單使用者的資訊。 | 啟用 |
| [誘餌頻道](honeypot.md) | `honeypot` | 抓取在禁止發送訊息頻道的使用者並給予相對應的懲罰。 | 啟用 |
| [可疑帳號偵測](accountcheck.md) | `suspicious_account` | 當有新成員加入時，依設定的規則（帳號建立時間、預設頭貼、個人資料是否為空）判斷是否為疑似機器人帳號，符合就通知群組擁有者並可執行處理動作。 | 未啟用 |
| [大量標記偵測](mentionguard.md) | `mention_guard` | 沒有「管理伺服器」權限的人觸發 @everyone／@here，或一次標記大量身分組、成員時，依設定刪除訊息、通知擁有者並執行處理動作。 | 未啟用 |
| [伺服器結構備份](backup.md) | `server_backup` | 定期備份類別、頻道與身分組（含頻道權限覆寫），並在偵測到頻道或身分組被刪除的當下自動保存「刪除前」的快照，之後可還原結構。 | 未啟用 |
| [伺服器紀錄](serverlog.md) | `server_log` | 記錄成員加入／離開、訊息編輯／刪除、語音頻道進出，可在後台查詢，也可以指定頻道即時發送。 | 未啟用 |
| [身分組領取](rolepanel.md) | `role_panel` | 在頻道放一則面板訊息，成員自己用按鈕、下拉選單或表情反應領取創作者開放的身分組。 | 未啟用 |
| [公告頻道自動發佈](publish.md) | `announce_publish` | 公告頻道的訊息自動「發佈」給追蹤這個頻道的其他伺服器。預設所有公告頻道都會發佈，不想發佈的頻道用 `/publish exclude` 排除。 | 啟用 |
| [網址安全檢查](urlsafety.md) | `url_safety` | 成員貼的網址送到 Google 安全瀏覽檢查（常見社群網站略過），檢查出有問題才會提醒大家謹慎點選。 | 未啟用 |
| [邀請連結偵測](inviteguard.md) | `invite_guard` | 全域累計各伺服器出現的 Discord 邀請連結，同一個邀請被貼到第 5 次時查詢目標伺服器名稱，符合 18+／NSFW 等違規關鍵字就刪除訊息或處分。 | 未啟用 |
| [自動討論串](autothread.md) | `auto_thread` | 在指定頻道發訊息，機器人會自動用那則訊息開一個討論串。要先用 `/autothread add` 設定頻道才會有作用。 | 啟用 |
| [自動懲處](autopunish.md) | `auto_punish` | 偵測 Discord Nitro 免費領取等詐騙訊息，以及全域與伺服器自訂的黑名單文字，自動刪除訊息並處分。 | 未啟用 |
| [Twitter／X 連結預覽](twitter.md) | `twitter_embed` | 成員貼 Twitter／X 的貼文連結時，機器人回覆一則換成 vxtwitter 的連結，讓 Discord 正常顯示貼文預覽。 | 未啟用 |
| [私密轉送](silent.md) | `silent` | 成員用 `/silent send` 送出訊息，由機器人匿名轉送到指定頻道。要先用 `/silent-setup channel` 設定轉送頻道才會有作用。 | 啟用 |
| [動態語音頻道](voice.md) | `dynamic_voice` | 成員加入入口語音頻道時，自動開一個自己的語音頻道，沒有人時自動刪除。要先用 `/voice default enter` 設定入口頻道才會有作用。 | 啟用 |

## 匯入舊機器人設定

* `/settings import-legacy`：匯入舊機器人 haer0248.me-v3 在這個伺服器的設定，詳見[從舊機器人轉移](../migration.md)

## 平台後台

這些開關與各功能的詳細設定，也可以在創作者斗內平台的「Discord 機器人設定 → 模組設定」調整；「群組設定」只負責綁定伺服器。
