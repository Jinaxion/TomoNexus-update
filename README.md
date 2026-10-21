# TomoNexus-update

Windows アプリ **TomoNexus** の版情報（`update.json`）と更新履歴（`history.json`）を置いています。

- `update.json` … アプリが起動時に読み、新しい版があればお知らせを出します（4KB まで・URL は書かない）
- `history.json` … 公式サイト（https://jinaxion.github.io/TomoNexus_website/history.html ）の「更新履歴」がここを読んで表示します。アプリは読みません

このリポジトリにアプリのソースコードは含まれません。

## 新しい版を出すとき（2ファイルを同じコミットで）

1. `update.json` の `latest`・`notes`（80文字まで）・`publishedAt` を書き換える
2. `history.json` の `entries` の**いちばん上**に、新しい版を1件足す

```json
{
  "version": "1.1.0",
  "date": "2026-11-01",
  "title": "トークノートの英訳を選べるように",
  "summary": "（任意）ひとことの説明",
  "download": {
    "file": "TomoNexus-1.1.0-win.zip",
    "size": "250.1MB",
    "sha256": "ZIPのSHA-256（ビルド時に出る値）",
    "virustotal": "https://www.virustotal.com/gui/file/<SHA-256を小文字で>"
  },
  "changes": [
    { "type": "new", "text": "新しくできるようになったこと" },
    { "type": "improve", "text": "使いやすくしたこと" },
    { "type": "fix", "text": "直した不具合" },
    { "type": "notice", "text": "お知らせ（料金・外部サービスの変更など）" }
  ]
}
```

- `type` は `new`（新機能）・`improve`（改善）・`fix`（修正）・`notice`（お知らせ）の4つ
- 文字はそのまま表示されます（HTML は使えません）
- `download` は公式サイトの「安心して試してもらうために」と更新履歴に出ます。いちばん新しい `download` が使われます
  - ZIP を作り直したら SHA-256 も変わるので、**BOOTH に置いた ZIP の値**を書く
  - `virustotal` は、その ZIP を VirusTotal で検査したページの URL（`https://www.virustotal.com/` で始まるものだけ表示）
- サイトへの反映は、コミットしてから数分かかります
