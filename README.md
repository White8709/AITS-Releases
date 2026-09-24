# AITS 公開下載與操作說明

[繁體中文](README.md) | [English](README_EN.md)

AITS 是一款常駐於 macOS 選單列的 AI 助理，可根據目前畫面產生建議回覆，並針對選取文字提供改寫、翻譯、校對、圖片 OCR 與長按 fn 語音輸入。App 不會開啟首頁，也不顯示 Dock 圖示；所有功能都可從選單列或快捷鍵啟動。

這個 repository 只提供公開安裝包與使用說明，不包含主程式碼、API key 或私人設定。

## 下載最新版

最新版：AITS v0.4.3

- [下載 AITS-0.4.3.dmg](https://github.com/White8709/AITS-Releases/releases/download/v0.4.3/AITS-0.4.3.dmg)
- [查看 AITS v0.4.3 Release](https://github.com/White8709/AITS-Releases/releases/tag/v0.4.3)
- SHA-256：`38e2cca70f9869ea7292b1f43b69170247f9394bbfe3d30d485da882701f1bed`

目前安裝包採 ad-hoc 簽署，尚未完成 Developer ID 簽章與 Apple notarization。第一次開啟時，macOS 可能會顯示安全性提示。

## 安裝

1. 下載並開啟 `AITS-0.4.3.dmg`。
2. 將 `AITS.app` 拖曳到 `Applications`。
3. 從「應用程式」開啟 AITS。
4. 如果 macOS 阻擋開啟，請到「系統設定 > 隱私權與安全性」找到 AITS，然後點選「強制打開」。
5. 啟動後，從 macOS 選單列開啟 AITS 或設定頁。

## 首次設定

AITS 需要下列 macOS 權限：

- 螢幕錄製：擷取目前畫面，供建議回覆功能理解上下文。
- 輔助使用：偵測選取文字，並將結果貼回原本的 App。
- 麥克風：長按 fn 使用語音輸入時擷取音訊。

請到「系統設定 > 隱私權與安全性」啟用權限。若系統要求重新啟動 App，請完整結束 AITS 後再開啟。

接著在「設定 > AI」選擇 provider、模型並輸入 API key。API key 會儲存在 macOS Keychain，不會寫入本 repository。

## 功能與快捷鍵

| 功能 | 預設快捷鍵 | 說明 |
| --- | --- | --- |
| 建議與改寫 | `Control + T` | 未選取文字時根據畫面產生建議回覆；已選取文字時產生改寫建議。 |
| 翻譯 | `Control + Y` | 翻譯目前選取的文字，選取結果或按 Return 後貼回原 App。 |
| 校對 | `Control + U` | 修正文法、拼字、標點與明顯錯字，完成後自動貼回原 App。 |
| 圖片 OCR | `Option + V` | 辨識剪貼簿中的圖片文字，直接貼回原 App。 |
| 語音輸入 | 長按 `fn` | 將語音即時轉寫並插入目前聚焦的文字欄位。 |

翻譯與校對只會傳送你選取的文字；圖片 OCR 只會傳送剪貼簿中的圖片資料。若沒有可處理的內容，AITS 不會送出 provider request。

## 選單列與快捷鍵開關

選單列提供：

- 手動產生建議
- Suggestions、Translation、Proofreading 三個獨立快捷鍵切換按鈕
- OCR 獨立快捷鍵切換按鈕
- 語音輸入開關與狀態
- 全域暫停／恢復快捷鍵
- 開啟設定
- 結束 AITS

四個快捷鍵可以分別開關，狀態會保留到下次啟動。全域「暫停快捷鍵」是主開關：暫停時會停止所有快捷鍵，但不會修改個別開關；恢復後只會重新啟用原本個別開啟的快捷鍵。

即使快捷鍵已暫停，仍可從選單列手動產生建議。

## 設定頁

- General：語言與全域「暫停快捷鍵」主開關。
- Suggestions：建議／改寫快捷鍵、建議數量、System Prompt 與改寫模式。
- Translation：翻譯快捷鍵、目標語言與 System Prompt。
- Proofreading：校對快捷鍵與 System Prompt。
- OCR：圖片 OCR 快捷鍵與專用 System Prompt。
- Voice：長按 fn 語音輸入、Gemini Provider、語音模型與長按判定時間。
- AI：provider、模型與 API key。

「設定 > General」也可開啟「登入時自動啟動」；若 macOS 要求核准，請到「系統設定 > 一般 > 登入項目」允許 AITS。

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

### 辨識剪貼簿圖片

1. 在任意 App 中複製圖片。
2. 按下 `Option + V`。
3. AITS 會辨識圖片中的文字，並直接貼回原本的 App。

OCR 不會開啟結果視窗；辨識狀態與錯誤會顯示在選單列。Finder 複製的圖片檔案不會觸發 OCR。

### 語音輸入

1. 在「設定 > Voice」啟用語音輸入，選擇已設定的 Gemini Provider，並確認已允許麥克風權限。
2. 按住 `fn` 開始說話，不需要先聚焦可編輯欄位。
3. 轉寫中的文字會即時寫入游標位置，並隨辨識結果更新。
4. 放開 `fn` 完成輸入；切換 App、點擊或按下其他按鍵會停止後續寫入。

若 macOS 的 fn 鍵短按會觸發系統功能，請在「系統設定 > 鍵盤」將「按下 fn 鍵時」設為「不執行任何操作」。

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
