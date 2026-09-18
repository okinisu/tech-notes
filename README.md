# tech-notes

競技プログラミング・ロボット開発・CTF・一般開発・数学・Web3の参考資料と技術メモ。
参考リンクに一言添えるだけの投稿から、解法や開発記録まで置いていきます。

公開サイト: https://okinisu.github.io/tech-notes/

## 構成

```text
index.html                 トップページ
competitive-programming/   競技プログラミングの一覧
robotics/                  ロボット開発の一覧
ctf/                       CTFの一覧
development/               一般開発の一覧
mathematics/               数学の一覧
web3/                      Web3の一覧
_topics/                   分野の中のテーマ・サブテーマ
_notes/                    資料・メモのMarkdownファイル
  competitive-programming/
  robotics/
  ctf/
  development/
  mathematics/
  web3/
templates/                 新しい資料・メモのひな形（サイトには公開しない）
_data/categories.yml       分野の名前・説明・リンク
_layouts/                  共通レイアウト
_includes/                 テーマ一覧・記事一覧・パンくず
assets/css/                スタイル
_config.yml                サイト設定
```

## 資料・メモを追加する

1. `templates/resource.md`（参考リンク）か `templates/note.md`（解法・開発メモ）をコピーします。
2. `_notes/` の該当する分野のフォルダに、`cpp-reference.md` のような名前で保存します。ファイル名とフォルダ名がURLになります。
3. 冒頭の `title`、`description`、`category`、`topic` を書き換え、本文をMarkdownで記入します。テーマが未作成の分野では `topic` を省略できます。`tags` は空でも構いません。
4. `main` にコミット・pushすると、分野別の一覧に自動で追加され、GitHub Pagesへ反映されます。

`category` はフォルダと揃え、以下のいずれかを指定します。

| 分野 | category |
| --- | --- |
| 競技プログラミング | `competitive-programming` |
| ロボット開発 | `robotics` |
| CTF | `ctf` |
| 一般開発 | `development` |
| 数学 | `mathematics` |
| Web3 | `web3` |

`tags: [C++, BFS]` のように書くと、一覧と記事にタグが表示されます。タグによる検索・絞り込みはまだありません。

`kind` で一覧の掲載先を指定できます。参考資料は `reference`、問題の解法メモは `solution`、その他のメモは `note` にします。省略した記事も「メモ」に表示されます。

解法を折りたたむ場合は、メモのテンプレートにある `<details markdown="1">` を使えます。
サイト内リンクには、GitHub Pagesのサブパスを付けるため `{{ '/ctf/' | relative_url }}` のように `relative_url` を使います。
一覧は種類ごとに分かれ、それぞれタイトル順に並びます。資料が増えたら、分野ごとの細かな分類を追加できます。

## テーマによる分類

大分類の中にテーマを置き、その下にもサブテーマを作れます。競技プログラミングは次の構成です。

```text
競技プログラミング
├── 入門・学習の進め方
├── アルゴリズム
│   ├── 基本テクニック
│   ├── 探索・全探索
│   ├── 動的計画法（DP）
│   ├── 貪欲法
│   ├── グラフ・木
│   ├── データ構造
│   └── 文字列
└── C++
```

例えば木の直径のメモには `category: competitive-programming` と `topic: algorithms/graphs-trees` を指定します。「グラフ・木」と親の「アルゴリズム」、競プロ全体の一覧から同じ記事を開けます。記事のURLはテーマを変更しても変わりません。

CTFには「分野別」と「競技形式」の入口があります。例えばWebの問題は `topic: fields/web`、KoTHの参加メモは `topic: formats/koth` に分類します。複数のテーマに関わる記事は、主なテーマを1つ選び、ほかの技術名はタグで補足します。

ロボット開発・一般開発のテーマは以下のとおりです。

| 分野 | テーマ | topic |
| --- | --- | --- |
| ロボット開発 | 入門・環境構築 | `getting-started` |
| ロボット開発 | 機構・ハードウェア | `mechanical-hardware` |
| ロボット開発 | 電子回路・電源 | `electronics-power` |
| ロボット開発 | 組み込み・通信 | `embedded-communication` |
| ロボット開発 | 制御 | `control` |
| ロボット開発 | 認識・自律動作 | `perception-autonomy` |
| ロボット開発 | 製作記録 | `build-logs` |
| 一般開発 | 言語・ライブラリ | `languages-libraries` |
| 一般開発 | Web・アプリ開発 | `web-apps` |
| 一般開発 | 設計・データベース | `design-databases` |
| 一般開発 | 開発環境・ツール | `tools-environment` |
| 一般開発 | テスト・品質改善 | `testing-quality` |
| 一般開発 | インフラ・運用 | `infrastructure-operations` |
| 一般開発 | 制作記録 | `project-logs` |
| 一般開発 | OSごとの違い | `os-differences` |

記事では `category: robotics` または `category: development` と、表の `topic` を指定します。

数学とWeb3には独立した大分類を用意しています。テーマの細分化は、資料に合わせて追加できます。

テーマを追加するには、`_topics/分野/テーマ.md` を作り、以下の情報を記入します。

```yaml
---
title: グラフ・木
description: BFS、DFS、最短経路、木の直径など。
category: competitive-programming
topic: algorithms/graphs-trees
parent: algorithms
order: 50
---
```

この例の保存先は `_topics/competitive-programming/algorithms/graphs-trees.md` です。`topic` とファイルの階層を揃え、親のテーマも作成してください。大分類直下のテーマでは `parent: ""` にします。`order` は同じ親の下での表示順です。

`topic` を省略した記事も大分類の一覧に表示されます。公開前に、指定したテーマが `_topics/` 内に存在することを確認してください。

## ローカルで確認する

RubyとBundlerが必要です。

```sh
bundle config set --local path vendor/bundle
bundle install
bundle exec jekyll serve
```

http://localhost:4000/tech-notes/ を開きます。
ビルドだけ実行する場合は `bundle exec jekyll build` を使います。

## GitHub Pages

JekyllでMarkdownから静的ページを生成します。
リポジトリの **Settings → Pages** で、公開元を **Deploy from a branch / main / (root)** に設定します。
独自ドメインやリポジトリ名を変更する場合は `_config.yml` の `url` と `baseurl` も更新します。

参考: [GitHub PagesとJekyllについて](https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll/about-github-pages-and-jekyll)
