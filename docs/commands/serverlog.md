# 伺服器紀錄
> 指令：`/serverlog`  
> 權限需求：`管理伺服器 Manage Server`

記錄伺服器裡的動靜：成員加入／離開、身分組變更、訊息編輯／刪除、語音頻道進出。

紀錄會寫進平台後台，可以在 **Discord 機器人設定 → 執行紀錄** 查詢；另外也可以指定一個頻道，讓機器人即時把紀錄發過去。

!!! info "紀錄保留 30 天"
    訊息紀錄包含訊息內容，所以只保留 30 天，超過會自動清除。其他自動處理的紀錄（洗版、誘餌頻道等）不受這個期限影響。

## 總開關

功能本身要不要執行，是用 `/settings enable|disable server_log` 控制（見[群組功能開關](settings.md)），預設為**未啟用**。

## 指令

* `/serverlog channel [channel]`：設定紀錄頻道，留空則清除（改成只記錄在後台）
* `/serverlog config [member_join] [member_leave] [member_role] [message_edit] [message_delete] [voice_join] [voice_move] [voice_leave] [voice]`：設定要記錄哪些事件，所有選項為選填（`voice` 一次設定語音三種，個別填的優先）
* `/serverlog status`：查看目前設定

設定頻道時，機器人會先確認自己在那個頻道有「檢視頻道」與「發送訊息」權限，缺權限會直接擋下並告訴你缺哪一個——避免設定好了卻默默什麼都沒發出來。

## 提供設定選項

| 選項 | 說明 | 預設 |
|---|---|---|
| `member_join` | 記錄成員加入 | 開啟 |
| `member_leave` | 記錄成員離開 | 開啟 |
| `member_role` | 記錄身分組變更：成員被加上或拿掉哪些身分組、是誰操作的 | 開啟 |
| `message_edit` | 記錄訊息編輯（只顯示修改處與前後文） | 開啟 |
| `message_delete` | 記錄訊息刪除 | 開啟 |
| `voice_join` | 記錄進入語音頻道 | 開啟 |
| `voice_move` | 記錄移動語音頻道（還在語音裡，只是換到別的頻道） | 開啟 |
| `voice_leave` | 記錄離開語音頻道 | 開啟 |

!!! info "身分組變更的執行者"
    要記下是誰加上或拿掉身分組，機器人需要「檢視審核日誌」權限，沒有的話執行者會顯示「不明」。成員自己用[身分組領取](rolepanel.md)面板領的，執行者會是機器人。

## 在平台後台操作

同樣的設定也可以在 Nekolive 平台後台的 **Discord 機器人設定 → 伺服器紀錄** 調整，兩邊改的是同一份設定。
