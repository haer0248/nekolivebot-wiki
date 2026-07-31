# 洗版偵測
> 指令：`/antispam`  
> 權限需求：`管理伺服器 Manage Server`

偵測同一個人在短時間內發送大量訊息（洗版），預設門檻是 {==**7 秒內 5 則**==}。

偵測邏輯只計算「訊息則數/秒數」，不會讀取訊息內容，機器人也不會保留或分析聊天內容。

!!! info "為什麼預設這麼保守"
    預設值刻意設定為只通知、不刪訊息、不處分，需要管理員自己觀察一陣子之後，再使用 `/antispam config` 調高處置力道，避免機器人剛裝上就因為誤判而處分到真的成員。

## 總開關

功能本身要不要執行，是用 `/settings enable|disable anti_flood` 控制（見[群組功能開關](settings.md)）。  
`/antispam config` 負責的是「執行了之後要怎麼處理」，兩者分開調整。

## 指令

* `/antispam config [notify_owner] [delete_messages] [action] [threshold] [interval] [timeout_minutes]`：調整設定，所有選項為選填
* `/antispam status`：查看目前設定

## 提供設定選項

| 選項 | 說明 | 預設 |
|---|---|---|
| `notify_owner` | 偵測到時要不要私訊通知群組擁有者 | 開啟 |
| `delete_messages` | 要不要刪除洗版的那些訊息 | 關閉 |
| `action` | 處理動作：不處理、禁言、踢出、封鎖（四選一） | 不處理 |
| `threshold` / `interval` | 幾秒內幾則算洗版 | 7 秒 / 5 則 |
| `timeout_minutes` | 禁言分鐘數，`action` 設成禁言時使用 | 系統預設值 |

> `action` 不是三個獨立開關，因為對同一次洗版事件而言，禁言、踢出、封鎖本質上是嚴重程度的選擇，不會同時執行。
