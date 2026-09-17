# tech-notes

競技プログラミング・ロボット開発・CTF・一般開発の参考資料と技術メモ。
参考リンクに一言添えるだけの投稿から、解法や開発記録まで置いていきます。

公開サイト: https://okinisu.github.io/tech-notes/

## 構成

```text
index.html                 トップページ
competitive-programming/   競技プログラミングの一覧
robotics/                  ロボット開発の一覧
ctf/                       CTFの一覧
development/               一般開発の一覧
_notes/                    資料・メモのMarkdownファイル
  competitive-programming/
  robotics/
  ctf/
  development/
templates/                 新しい資料・メモのひな形（サイトには公開しない）
_data/categories.yml       分野の名前・説明・リンク
_layouts/                  共通レイアウト
assets/css/                スタイル
_config.yml                サイト設定
```

## 資料・メモを追加する

1. `templates/resource.md`（参考リンク）か `templates/note.md`（解法・開発メモ）をコピーします。
2. `_notes/` の該当する分野のフォルダに、`cpp-reference.md` のような名前で保存します。ファイル名とフォルダ名がURLになります。
3. 冒頭の `title`、`description`、`category` を書き換え、本文をMarkdownで記入します。`tags` は空でも構いません。
4. `main` にコミット・pushすると、分野別の一覧に自動で追加され、GitHub Pagesへ反映されます。

`category` はフォルダと揃え、以下のいずれかを指定します。

| 分野 | category |
| --- | --- |
| 競技プログラミング | `competitive-programming` |
| ロボット開発 | `robotics` |
| CTF | `ctf` |
| 一般開発 | `development` |

`tags: [C++, BFS]` のように書くと、一覧と記事にタグが表示されます。タグによる検索・絞り込みはまだありません。

解法を折りたたむ場合は、メモのテンプレートにある `<details markdown="1">` を使えます。
サイト内リンクには、GitHub Pagesのサブパスを付けるため `{{ '/ctf/' | relative_url }}` のように `relative_url` を使います。
一覧はタイトル順です。資料が増えたら、分野ごとの細かな分類を追加できます。

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
