# hakoniwa-management-list-archive

箱庭クラフト（HAKONIWA CRAFT）公式サイトの運営管理用データ（ニュース・支援者様一覧）を配信するリポジトリです。

（旧 `hakoniwa-news-archive` から改名・統合。News配信の対象は変わりません。）

## 構成

- `news.json`: ニュース・お知らせデータ本体
  - 表示先: [https://hakoniwa-craft.com/news/](https://hakoniwa-craft.com/news/)
  - `hakoniwacraft-site` の `news/site-generate.js` が本ファイルを取得して一覧・詳細を動的表示する。
- `supporter.json`: 支援者様一覧データ本体
  - 表示先: 公式サイトの `pages/donation-info.html`（🙏 支援者様一覧セクション）
  - 取得に失敗した場合・配列が空の場合は、ページ側の静的な案内文にフォールバックする（安全設計のため、無理に空配列を書く必要はない）。

---

## news.json のフォーマット

各記事は以下のフィールドを持つオブジェクトです。

| フィールド | 内容 |
| --- | --- |
| `id` | 記事を一意に識別するID（**一度公開したら変更しない**。共有リンクが壊れるため） |
| `title` | 記事タイトル |
| `date` | 公開日（`YYYY.MM.DD` 形式） |
| `category_id` | カテゴリーID（`"1"`〜`"6"` の文字列。`hakoniwacraft-site/news/site-generate.js` の `CATEGORY_DEFINITION` に準拠: 1:Tech, 2:Update, 3:Event, 4:Info, 5:OTHER, 6:SPECIAL） |
| `author` | 投稿者・チーム名 |
| `content` | 記事本文（インラインスタイル付きHTML文字列。既存記事と同じ書式に合わせること） |

編集後は必ずJSONとして正しくパースできるか検証すること。

---

## supporter.json のフォーマット

支援者1名につき1オブジェクトを配列に追加します。

```json
[
  {
    "name": "支援者様の表示名（必須）",
    "type": "cien",
    "plan": "奉納プラン",
    "message": "応援しています！"
  },
  {
    "name": "支援者様の表示名（必須）",
    "type": "gift",
    "amount": "1,000円分",
    "message": "少しですが応援します"
  }
]
```

| フィールド | 必須 | 内容 |
| --- | --- | --- |
| `name` | 必須 | 表示するお名前・ハンドルネーム。**ご本人の同意のもとで掲載すること。** |
| `type` | 必須 | `"cien"`（Ci-enでの継続支援）または `"gift"`（単発支援：寄付フォーム・ほしい物リスト等）。この2値以外は表示されない。 |
| `plan` | 任意（`cien`向け） | Ci-enのプラン名（例: `"普請料プラン"`）。 |
| `amount` | 任意（`gift`向け） | 支援額の表示用テキスト（例: `"1,000円分"`）。厳密な金額でなくてもよい。 |
| `message` | 任意 | 支援者様からの一言メッセージ。**掲載してよいか確認してから入れること。** |

### 注意点

- `type` を書き忘れると、そのデータはどちらの列にも表示されない。
- `name` / `message` はプレーンテキストとして自動エスケープ表示されるため、HTMLタグは使えない。
- 掲載前に、お名前・メッセージの公開について本人の同意を必ず得ること。

## ライセンス

本リポジトリのコンテンツの取り扱いについては [LICENSE.md](LICENSE.md) を参照してください。
