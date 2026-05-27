# AITS 操作手冊

AITS 是一款 macOS AI 建議回覆工具。你可以在任何 App 中按下快捷鍵，讓 AITS 擷取目前畫面，並依照畫面內容產生可直接貼上的建議回覆；如果你已選取文字，AITS 會自動進入改寫模式，產生可取代原文的改寫建議。

這個 repository 只提供公開下載檔案，不包含主程式碼。

## 下載

最新版：AITS v0.1.2

- [下載 AITS-0.1.2.dmg](https://github.com/White8709/AITS-Releases/releases/download/v0.1.2/AITS-0.1.2.dmg)
- [查看 Release 頁面](https://github.com/White8709/AITS-Releases/releases/tag/v0.1.2)
- SHA-256：`f78a78adb745e994bc86acd3fa6596504079b3f1774e41c56df2a1e66618bcb2`

注意：目前版本是 ad-hoc signed local testing build，尚未完成 Developer ID 簽章與 notarization。第一次開啟時，macOS 可能會顯示安全性提示。

## 安裝

1. 下載 `AITS-0.1.2.dmg`。
2. 開啟 DMG。
3. 將 `AITS.app` 拖曳到 `Applications`。
4. 從 `Applications` 開啟 AITS。
5. 如果 macOS 阻擋開啟，請在 Finder 中對 `AITS.app` 按右鍵，選擇「打開」，再確認開啟。

## 首次設定

首次使用前，建議先完成以下設定。

### 權限

AITS 需要兩個 macOS 權限：

- 螢幕錄製：用來擷取目前畫面，讓 AI 理解上下文。
- 輔助使用：用來偵測選取文字，以及在你點選建議後自動貼回原 App。

設定位置：

1. 開啟「系統設定」。
2. 進入「隱私權與安全性」。
3. 分別到「螢幕錄製」與「輔助使用」。
4. 啟用 AITS。
5. 若系統要求重新啟動 App，請結束並重新開啟 AITS。

### AI Provider

在 AITS 的「AI 設定」頁中設定 Provider。

目前設計支援：

- OpenAI / OpenAI-compatible API
- Gemini
- Ollama
- LM Studio
- Custom provider

Provider 會按照設定頁中的順序使用：

- 第一順位是主要 provider。
- 後面的 provider 是 fallback。
- 如果第一個 provider 失敗，AITS 會依序嘗試後面的 provider。

每個 provider 可設定自己的 API key。API key 會儲存在 macOS Keychain，不會寫入公開設定檔。

本機模型例如 Ollama 或 LM Studio 通常需要先在本機啟動服務，並確認 base URL 與模型名稱正確。

## 快捷鍵

預設快捷鍵：

```text
Control + T
```

你可以在設定頁修改快捷鍵。

## 基本使用

### 產生建議回覆

適合用在聊天、Email、客服、協作工具等場景。

1. 打開任意 App，例如 Slack、Notion、Safari、Chrome、Mail。
2. 不選取文字。
3. 按下 `Control + T`。
4. AITS 會擷取目前畫面並產生建議回覆。
5. 點選其中一則建議。
6. AITS 會將該建議複製到剪貼簿，並嘗試貼回原本 App。
7. 貼上成功後，建議彈窗會自動關閉。

### 改寫選取文字

適合用在改語氣、改正式程度、縮短文字、改成商務或客服口吻。

1. 在任意 App 中選取一段文字。
2. 按下 `Control + T`。
3. AITS 會自動進入「改寫」模式。
4. 彈窗上方的「改寫模式」預設為「不套用模式」。
5. 你可以選擇其他改寫模式，例如「正式語氣」、「友善語氣」、「精簡版本」。
6. 點選建議後，AITS 會嘗試用建議內容取代原本選取的文字。
7. 成功後，彈窗會自動關閉。

## 重新產生

建議彈窗上方有一個補充指令輸入框。

你可以：

- 不輸入任何內容，直接按「重新產生」。
- 輸入補充指令，例如「請更正式一點」、「請縮短」、「請改成適合回覆上司」。

AITS 會保留同一輪的畫面與選取文字，不會重新截圖，也不會重新偵測選字，直接產生另一輪建議。

## 改寫模式設定

在「AI 設定」頁可以管理改寫模式。

可設定項目：

- 新增改寫模式
- 刪除改寫模式
- 重新命名
- 編輯改寫模式的 system prompt
- 調整改寫模式排序
- 設定預設改寫模式
- 預設也可以選擇「不套用模式」

排序會影響建議彈窗中的改寫模式下拉選單順序。

## 建議面板

建議面板支援：

- 拖曳移動
- 縮放大小
- `Esc` 關閉
- `Return` 複製目前選取建議
- 上下方向鍵切換建議

你可以在設定中開關面板拖曳與縮放。

## 常見問題

### macOS 說無法驗證開發者，怎麼辦？

目前版本尚未 Developer ID 簽章與 notarization。請在 Finder 中對 `AITS.app` 按右鍵，選擇「打開」，再確認開啟。

### 按快捷鍵沒有反應

請確認：

- AITS 已經開啟。
- 快捷鍵沒有被其他 App 佔用。
- AITS 沒有暫停快捷鍵。
- AITS 已取得必要權限。

### 無法擷取畫面

請確認 AITS 已取得「螢幕錄製」權限。授權後請重新啟動 AITS。

### 選取文字後沒有進入改寫模式

請確認 AITS 已取得「輔助使用」權限。部分 App 對選取文字支援不一致，AITS 會嘗試使用剪貼簿 fallback 偵測選取文字。

### 點選建議後沒有自動貼上

請確認 AITS 已取得「輔助使用」權限。部分 App 或特殊輸入框可能不接受自動貼上，此時建議內容仍會被複製到剪貼簿，可手動按 `Command + V` 貼上。

### API key 存在哪裡？

API key 會儲存在 macOS Keychain。AITS 不會把 API key 寫入 release repo 或公開檔案。

## 隱私說明

- 截圖只會在你觸發建議時處理。
- 截圖會送到你設定的 AI provider。
- API key 儲存在 Keychain。
- 點選建議後才會寫入剪貼簿並嘗試貼上。
- Public release repo 只提供下載檔，不包含私有設定或 API key。

## 已知限制

- 目前 release 尚未 notarized。
- 不同 App 對選取文字與自動貼上的支援程度不同。
- 本機模型需要自行啟動 Ollama、LM Studio 或相容服務。
