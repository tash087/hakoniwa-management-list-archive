# hakoniwa-news-archive

箱庭クラフト（HAKONIWA CRAFT）公式サイトのニュース・お知らせ配信用データリポジトリです。

- 表示先: [https://hakoniwa-craft.com/news/](https://hakoniwa-craft.com/news/)
- 本リポジトリの `news.json` を元に、上記ページのお知らせ一覧が動的に生成・表示されます。

## 構成

- `news.json`: ニュース記事データ本体（JSON形式）

### news.json のフォーマット

各記事は以下のフィールドを持つオブジェクトです。

| フィールド | 内容 |
| --- | --- |
| `id` | 記事を一意に識別するID |
| `title` | 記事タイトル |
| `date` | 公開日（`YYYY.MM.DD` 形式） |
| `category_id` | カテゴリーを表すID |
| `author` | 投稿者・チーム名 |
| `content` | 記事本文（インラインスタイル付きHTML文字列） |

## ライセンス

本リポジトリのコンテンツの取り扱いについては [LICENSE.md](LICENSE.md) を参照してください。
また、箱庭クラフト全体の知的財産権に関する方針は公式ドキュメントの
[IPポリシー](https://docs.hakoniwa-craft.com/docs/ip-policy-711/) に準拠します。
