# LIFF Python Course Cards

這是一個可以部署到 GitHub Pages 的 LINE LIFF 靜態網頁。頁面會初始化 LIFF，並透過 `liff.shareTargetPicker()` 分享一則 Flex Message carousel，內容是 10 張 Python 新手課程小卡。

## 檔案

- `index.html`：LIFF 網頁主頁，包含初始化狀態、分享按鈕與錯誤訊息。
- `flex.json`：Flex Message 內容，共 10 張 Python 課程卡片。
- `.nojekyll`：讓 GitHub Pages 直接發布靜態檔案。

## 替換 LIFF ID

打開 `index.html`，找到這一行：

```js
const LIFF_ID = "YOUR_LIFF_ID";
```

把 `YOUR_LIFF_ID` 換成 LINE Developers Console 產生的 LIFF ID，例如：

```js
const LIFF_ID = "2001234567-AbCdEfGh";
```

## LINE Developers 設定

1. 前往 [LINE Developers Console](https://developers.line.biz/console/)。
2. 建立或選擇一個 Provider。
3. 建立或選擇一個 LINE Login Channel。
4. 進入該 Channel 的 LIFF 分頁，新增 LIFF App。
5. Endpoint URL 填入 GitHub Pages 網址，例如：

   ```text
   https://你的 GitHub 帳號.github.io/liff-python-course/
   ```

6. 在同一個 LIFF 分頁找到 `shareTargetPicker`，閱讀並同意 Agreement Regarding Use of Information，然後按 Enable。
7. 儲存設定後，將 LIFF ID 複製回 `index.html`。

LINE 官方文件提到，使用 `liff.shareTargetPicker()` 前需要在 LINE Developers Console 啟用 Share Target Picker，並在 LIFF 環境初始化後檢查 `liff.isApiAvailable("shareTargetPicker")`。

## 啟用 GitHub Pages

1. 建立 GitHub repository，建議名稱：`liff-python-course`。
2. 將這些檔案推送到 repository 的 `main` 分支。
3. 到 repository 的 Settings → Pages。
4. Source 選擇 Deploy from a branch。
5. Branch 選擇 `main`，資料夾選擇 `/root`。
6. 儲存後等待 GitHub Pages 部署完成。

部署完成後，網站通常會在：

```text
https://你的 GitHub 帳號.github.io/liff-python-course/
```

## 本機測試

因為瀏覽器直接開啟 `index.html` 時，`fetch("./flex.json")` 可能受到限制，建議用本機伺服器測試：

```bash
python3 -m http.server 8080
```

然後打開：

```text
http://localhost:8080/
```

注意：真正呼叫 LINE LIFF 功能仍需要有效的 LIFF ID，以及符合 LINE Developers Console 設定的 Endpoint URL。

## 參考文件

- [LINE Developers：Developing a LIFF app](https://developers.line.biz/en/docs/liff/developing-liff-apps/)
- [LINE Developers：LIFF API reference](https://developers.line.biz/en/reference/liff/)
- [GitHub Docs：Creating a GitHub Pages site](https://docs.github.com/en/pages/getting-started-with-github-pages/creating-a-github-pages-site)
