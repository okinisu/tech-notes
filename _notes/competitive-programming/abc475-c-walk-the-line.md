---
title: "ABC475 C - Walk the Line"
description: "一直線上の街を、移動距離の上限以内でできるだけ多く訪れる問題。"
category: competitive-programming
kind: solution
tags: [AtCoder, 累積和, 全探索]
---

[問題を読む：C - Walk the Line](https://atcoder.jp/contests/abc475/tasks/abc475_c)

<details markdown="1">
<summary>解法メモを見る</summary>

## 解答手順

1. 道の長さの累積和を求め、各街の位置を計算する。
2. 訪れる区間の左端 `l` と右端 `r` を二重ループで全探索する。開始地点 `S` を含む、`l ≤ S ≤ r` の区間だけを考える。
3. その区間を回る最小移動距離が `L` 以下なら、訪れる街の数 `r - l + 1` で答えを更新する。

## 最小移動距離の求め方

街 `i` の位置を `P[i]` とすると、累積和で `P[1] = 0`、`P[i + 1] = P[i] + A[i]` と計算できます。

開始地点から左端までの距離を `x = P[S] - P[l]`、右端までの距離を `y = P[r] - P[S]` とします。

- 左端へ行ってから右端へ向かうと、移動距離は `2*x + y`。
- 右端へ行ってから左端へ向かうと、移動距離は `x + 2*y`。

この小さい方、`min(2*x + y, x + 2*y)` が `L` 以下かを調べればOKです。出発地点に戻る必要はありません。

累積和を使うと区間ごとの判定は `O(1)`、全体の時間計算量は `O(N²)` です。距離や `L` は大きくなるため、C++なら `long long` を使います。

確認用：[AtCoder公式解説](https://atcoder.jp/contests/abc475/editorial/25534)

</details>
