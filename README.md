# 粵語配音台 · 下載網站

呢個 repo 係一版**靜態落地頁**，俾人下載「粵語配音台」程式。
下載掣連去 **GitHub Releases** 最新版嘅 zip——即係話你日後更新 app，只需上傳一個新 release，呢個網站唔使掂、唔使重新部署。

```
index.html      ← 落地頁（純靜態，冇後端）
vercel.json     ← Vercel 設定
README.md       ← 你而家睇緊呢份
```

> 個 app 本身（index.html + serve.py + 啟動器）唔喺呢個 repo。
> 佢要本機 Python + ffmpeg 先行到，Vercel 寄存唔到。呢度淨係落地頁。

---

## 下載掣點搵到個 zip

index.html 頂部有兩行設定：

    const GH_USER = 'wongsir1011';
    const GH_REPO = 'cantonese-dubbing-desk';

頁面載入時會呼叫 api.github.com 攞最新 release 入面第一個 .zip 資產，填落下載掣。
攞唔到（未 publish release、或者 API 限速）就自動連去 releases 頁，個掣唔會撳死。

所以個下載掣要 work，你要喺 app repo 開一個 release 並附上個 zip。

---

## 部署（全網頁，唔使命令行）

1. 將 index.html、vercel.json、README.md 上載去一個新 GitHub repo（例如 cantonese-dubbing-site）
2. 去 vercel.com/new 用 GitHub 登入，Import 呢個 repo
3. Framework Preset 揀 Other，其餘留返預設，撳 Deploy

因為 index.html 喺 repo 根目錄，Vercel 會直接 serve 佢做首頁，唔使改任何 output 設定。

---

## 日後更新

- 改咗 app → 喺 app repo 開新 release 附新 zip。網站個下載掣自動跟到，Vercel 唔使掂。
- 改咗落地頁 → 改 index.html 再重新上載，Vercel 自動重新部署。
