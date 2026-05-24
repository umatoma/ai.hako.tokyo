# topics/

ベンダー横断のトピック別ノート。複数の `frameworks/` や `sources/` を見比べて整理した知見を置く。

## ディレクトリ構成

業務領域 (domain) ごとにサブディレクトリを切る。複数 domain にまたがるテーマは `cross/` に置く。

- [`software-development/`](software-development/) — ソフト開発のトピック
- [`design/`](design/) — デザイン業務のトピック
- [`marketing/`](marketing/) — マーケティング業務のトピック
- [`sales/`](sales/) — 営業業務のトピック
- [`hr/`](hr/) — 人事業務のトピック
- [`cross/`](cross/) — 業務領域を横断するトピック（プロンプティング、エージェント設計、評価、コンテキスト管理など）

## frameworks/ との棲み分け

「ある特定の製品の話」になりそうなものは [`../frameworks/`](../frameworks/) 側に置く。topics/ はあくまで横断比較・原則の整理。
