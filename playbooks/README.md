# playbooks/

自分たちの作業に直接使える実践レシピ。「明日からこの手順で動ける」レベルに落とし込んだものを置く。

`frameworks/` や `topics/` が「知識」なのに対し、こちらは「手順」。

## ディレクトリ構成

業務領域 (domain) ごとにサブディレクトリを切る。

- [`software-development/`](software-development/) — Claude Code を中心としたソフト開発手順
- [`design/`](design/) — デザイン業務
- [`marketing/`](marketing/) — マーケティング業務
- [`sales/`](sales/) — 営業業務
- [`hr/`](hr/) — 人事業務
- [`knowledge-base/`](knowledge-base/) — このリポ自体の運用（外部情報の取り込み等のメタ手順）

業務領域ではない、このナレッジベース自体の運用手順は `knowledge-base/` に置く。

## 命名

各 domain 内のファイルは `NN-日本語タイトル.md` の連番命名で、訪問者が読む順に並べる。番号は domain 内でユニーク（domain 間では重複してよい）。
