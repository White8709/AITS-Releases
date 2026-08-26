# AITS 公開下載與操作說明

[繁體中文](README.md) | [English](README_EN.md)

AITS 是一款常駐於 macOS 選單列的 AI 助理，可根據目前畫面產生建議回覆，並針對選取文字提供改寫、翻譯與校對。App 不會開啟首頁，也不顯示 Dock 圖示；所有功能都可從選單列或快捷鍵啟動。

這個 repository 只提供公開安裝包與使用說明，不包含主程式碼、API key 或私人設定。

## 下載最新版

最新版：AITS v0.2.4

- [下載 AITS-0.2.4.dmg](https://github.com/White8709/AITS-Releases/releases/download/v0.2.4/AITS-0.2.4.dmg)
- [查看 AITS v0.2.4 Release](https://github.com/White8709/AITS-Releases/releases/tag/v0.2.4)
- SHA-256：`8db575ce5ec53afd63a79387bde1c3320f320ddbbd07d401bd35de8ebbe92f0b`

目前安裝包採 ad-hoc 簽署，尚未完成 Developer ID 簽章與 Apple notarization。第一次開啟時，macOS 可能會顯示安全性提示。

## 安裝

1. 下載並開啟 `AITS-0.2.4.dmg`。
2. 將 `AITS.app` 拖曳到 `Applications`。
3. 從「應用程式」開啟 AITS。
4. 如果 macOS 阻擋開啟，請到「系統設定 > 隱私權與安全性」找到 AITS，然後點選「強制打開」。
5. 啟動後，從 macOS 選單列開啟 AITS 或設定頁。

## 首次設定

AITS 需要下列 macOS 權限：

- 螢幕錄製：擷取目前畫面，供建議回覆功能理解上下文。
- 輔助使用：偵測選取文字，並將結果貼回原本的 App。

請到「系統設定 > 隱私權與安全性」啟用權限。若系統要求重新啟動 App，請完整結束 AITS 後再開啟。

接著在「設定 > AI」選擇 provider、模型並輸入 API key。API key 會儲存在 macOS Keychain，不會寫入本 repository。

## 功能與快捷鍵

| 功能 | 預設快捷鍵 | 說明 |
| --- | --- | --- |
| 建議與改寫 | `Control + T` | 未選取文字時根據畫面產生建議回覆；已選取文字時產生改寫建議。 |
| 翻譯 | `Control + Y` | 翻譯目前選取的文字，選取結果或按 Return 後貼回原 App。 |
| 校對 | `Control + U` | 修正文法、拼字、標點與明顯錯字，完成後自動貼回原 App。 |

翻譯與校對只會傳送你選取的文字；若沒有選取文字，AITS 不會送出 provider request。

## 選單列與快捷鍵開關

選單列提供：

- 手動產生建議
- Suggestions、Translation、Proofreading 三個獨立快捷鍵切換按鈕
- 全域暫停／恢復快捷鍵
- 開啟設定
- 結束 AITS

三個快捷鍵可以分別開關，狀態會保留到下次啟動。全域「暫停快捷鍵」是主開關：暫停時會停止所有快捷鍵，但不會修改三個獨立開關；恢復後只會重新啟用原本個別開啟的快捷鍵。

即使快捷鍵已暫停，仍可從選單列手動產生建議。

## 設定頁

- General：語言與全域「暫停快捷鍵」主開關。
- Suggestions：建議／改寫快捷鍵、建議數量、System Prompt 與改寫模式。
- Translation：翻譯快捷鍵、目標語言與 System Prompt。
- Proofreading：校對快捷鍵與 System Prompt。
- AI：provider、模型與 API key。

## 基本使用

### 產生建議回覆

1. 打開聊天、Email、客服或其他需要回覆的 App。
2. 不要選取文字，按下 `Control + T`。
3. AITS 會擷取目前畫面並產生建議。
4. 選取建議後，內容會複製到剪貼簿並嘗試貼回原本的 App。

### 改寫選取文字

1. 在任意 App 中選取一段文字。
2. 按下 `Control + T`。
3. 選擇需要的改寫模式與結果。
4. AITS 會嘗試用結果取代原本選取的文字。

### 翻譯選取文字

1. 選取需要翻譯的文字。
2. 按下 `Control + Y`。
3. 在結果面板選取翻譯，或按 Return 使用目前結果。
4. AITS 會將翻譯貼回原本的 App。

### 校對選取文字

1. 選取需要校對的文字。
2. 按下 `Control + U`。
3. AITS 完成校對後，會自動將結果貼回原本的 App。

## 常見問題

### macOS 顯示「無法驗證開發者」

目前版本尚未 Developer ID 簽章與 notarization。請到「系統設定 > 隱私權與安全性」，找到被阻擋的 `AITS.app`，點選「強制打開」後再次確認。

### 按快捷鍵沒有反應

請確認 AITS 已啟動、快捷鍵未被其他 App 佔用、對應的獨立快捷鍵開關已開啟，而且全域快捷鍵沒有暫停。

### 無法擷取畫面或自動貼上

請確認 AITS 已取得「螢幕錄製」與「輔助使用」權限。部分 App 或特殊輸入框可能不接受自動貼上，此時結果仍會保留在剪貼簿，可使用 `Command + V` 手動貼上。

## 隱私說明

- AITS 只會在你主動觸發功能時處理畫面或選取文字。
- 畫面或文字會送到你設定的 AI provider。
- API key 儲存在 macOS Keychain。
- 公開下載 repository 不包含 API key、私人設定或主程式碼。

## 已知限制

- 目前 Release 尚未 notarized。
- 不同 App 對選取文字與自動貼上的支援程度可能不同。
- 使用本機模型時，需自行啟動相容的本機服務。
