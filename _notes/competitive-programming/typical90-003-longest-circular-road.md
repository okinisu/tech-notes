---
title: "003 - Longest Circular Road（★4）"
description: "木に道路を1本追加し、できる閉路を最長にする問題。"
category: competitive-programming
topic: algorithms/graphs-trees
kind: solution
tags: [AtCoder, 競プロ典型90問, 木, BFS, 木の直径]
---

[問題を読む：003 - Longest Circular Road（★4）](https://atcoder.jp/contests/typical90/tasks/typical90_c)

<details markdown="1">
<summary>解法メモを見る</summary>

## 正攻法：BFSを2回行う

1. 任意の頂点からBFS（幅優先探索）を行い、最も遠い頂点 `u` を探す。これが木の直径の一方の端になる。
2. `u` からもう一度BFSを行い、最も遠い頂点 `v` までの距離 `D` を求める。これが木の直径になる。
3. **答えは `D + 1`。** 直径の両端を新しい道路1本でつなぐため、その1本も数える。

ここで距離は、通る辺の本数です。木の任意の2頂点を結ぶ経路は1つなので、新しい道路を加えてできる閉路の長さは「もとの経路の長さ＋1」になります。

BFSは1回 `O(N)`、2回行っても全体の時間計算量は `O(N)` です。この求め方は木に対するもので、一般のグラフで必ず直径が求まるわけではありません。

## 関連資料

[木（グラフ理論）の参考資料]({{ '/notes/competitive-programming/tree-basics/' | relative_url }})

</details>
