# 全域黑名單
> 指令：`/blacklist`  
> 權限需求：`管理伺服器 Manage Server`

黑名單以 Discord `user_id` 為單位，**跨群組共用**（不是每個群組各自一份）。

## 指令

| 指令 | 說明 |
|---|---|
| `/blacklist check <user_id>` | 查詢某個使用者是否在黑名單中 |
| `/blacklist scan` | 主動掃描目前群組成員，抓出在黑名單中的人 |
| `/blacklist config <join_action> [timeout_minutes]` | 設定黑名單使用者「加入這個群組時」要怎麼處理 |
| `/blacklist status` | 查看目前群組的黑名單相關設定 |

## 被動偵測

* **黑名單使用者加入群組時**（需要此群組的 `blacklist_alert` 功能是啟用狀態，見[群組功能開關](settings.md)）：
  * `join_action = none`（預設）：私訊群組擁有者，附上「禁言、踢出、封鎖、忽略」按鈕，由擁有者當下點擊決定
  * `join_action = timeout / kick / ban`：加入當下直接自動執行該動作，私訊擁有者處理結果
* **黑名單使用者在群組發言時**：私訊通知群組擁有者（同一人同一群組 1 小時內只通知一次，避免灌爆私訊）

通知一律私訊群組擁有者，若擁有者關閉私訊或抓不到擁有者，只會被略過（見[快速開始](../index.md)的私訊隱私設定提醒）。
