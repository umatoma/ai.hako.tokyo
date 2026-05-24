# _templates/

新しいノートを作るときのコピー元テンプレート。

| ファイル | 用途 |
|---|---|
| [`source-blog.md`](./source-blog.md) | ブログ記事を `sources/<vendor>/blog/` に取り込むとき |
| [`source-pdf.md`](./source-pdf.md) | PDF を Markdown 化して `sources/<vendor>/docs/` に保存するとき |
| [`framework-or-topic.md`](./framework-or-topic.md) | `frameworks/` または `topics/` の二次情報ノートを作るとき |

使い方は [`playbooks/03-外部情報を取り込む.md`](../playbooks/03-外部情報を取り込む.md) 参照。

## 命名規約

- `sources/` 配下のブログ・記事: `YYYY-MM-DD-slug.md`
- `sources/` 配下のドキュメント: `slug.md`
- それ以外: `kebab-case.md`
