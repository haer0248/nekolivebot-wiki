# 自動懲處
> 指令：`/autopunish`  
> 權限需求：`管理伺服器 Manage Server`

主要抓「Discord Nitro 免費領取」這類詐騙訊息，另外也比對黑名單文字（假冒 Discord、Steam 的釣魚網域等），命中就自動刪訊息並處分。

## 會抓什麼

* **Nitro 詐騙**：訊息裡同時出現 discord、nitro、free 三個字（順序不限），**而且附有連結**。詐騙訊息常把英文字母換成長得一樣的西里爾字母（例如 `FRЕЕ` 裡的 Е），機器人會先換回來再判斷
* **假冒的 Nitro 禮物**：出現「you've been gifted a subscription」這類假禮物字樣，而且附有連結

沒有連結的閒聊（例如「discord nitro 現在免費嗎？」）不會被當成詐騙。
* **全域黑名單文字**：平台維護、所有伺服器共用的清單，多是假冒 Discord／Steam 的釣魚網域，不用自己加
* **伺服器黑名單文字**：你自己加的清單

黑名單文字是{==不分大小寫的子字串比對==}，訊息裡有出現就算命中，不是正規表示式。

先發正常訊息、再編輯成詐騙連結是常見的繞過手法，所以**編輯後的訊息也會檢查**。

!!! tip "管理員觸發時只會收到測試提示"
    擁有「管理伺服器」權限的成員與伺服器擁有者觸發時，機器人只會回覆「✅ 自動懲處測試」，不會刪訊息也不會處分，方便確認功能有在運作。這則訊息之後照常進其他功能（例如自動討論串）。

!!! info "不檢查的頻道"
    頻道名稱有「後台」「log」「error」的頻道不檢查（例如 `bot-log`、`機器人log`；`blog` 這種只是剛好包含 log 的不算），這些通常是機器人紀錄頻道，本來就會出現黑名單文字。

## 總開關

用 `/settings enable|disable auto_punish` 控制（見[群組功能開關](settings.md)），預設為**未啟用**。

## 指令

* `/autopunish config [action] [timeout_minutes] [delete_message] [warn_in_channel] [notify_owner] [check_bot_messages]`：調整設定，所有選項為選填
* `/autopunish status`：查看目前設定與黑名單文字數量
* `/autopunish words add <text>`：新增伺服器黑名單文字（2～100 個字）
* `/autopunish words remove <text>`：移除伺服器黑名單文字
* `/autopunish words list`：列出伺服器黑名單文字

平台後台「模組設定 → 自動懲處」也可以調整設定與黑名單文字。

## 提供設定選項

| 選項 | 說明 | 預設 |
|---|---|---|
| `action` | 處理動作：不處理、禁言、踢出、封鎖（四選一）。封鎖時會一併清掉這個人最近一天的訊息 | 禁言 |
| `timeout_minutes` | 禁言分鐘數，Discord 最長 28 天 | 10080 分鐘（7 天） |
| `delete_message` | 要不要刪除那則訊息 | 開啟 |
| `warn_in_channel` | 要不要在頻道發一則警告，提醒其他成員不要點 | 開啟 |
| `notify_owner` | 要不要私訊通知群組擁有者，附上原始訊息內容 | 關閉 |
| `check_bot_messages` | 要不要也檢查其他機器人的訊息（被盜用的機器人也會發詐騙），機器人只刪訊息、不處分 | 關閉 |

每次命中都會寫一筆進平台後台的執行紀錄，包含命中原因與訊息內容開頭。
