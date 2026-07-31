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

