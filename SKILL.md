# SKILL

このリポジトリでは、個別の writeup（事例）を材料にして、topic ごとの知識を育てます。
`writeup` は事例、`insights` は一般知識、`relations` は `insights` と `writeup` をつなぐ接続層として扱います。特定の分野に偏らない汎用的な構造を目指します。

## 読む順番

何も知らない状態では、次の順で読むことを想定します。

1. `insights/` で topic の見方を掴む。
2. `relations/` で、その topic に属する具体例と対応 writeup を探す。
3. `writeup/` で、個別事例の本文、ヒント、解説、答えを確認する。

## ディレクトリ

- 個別事例は [writeup/](writeup) に置く。
- 一般知識は [insights/](insights) に置く。
- 具体参照と接続情報は [relations/](relations) に置く。

## 粒度

- `insights/{topic}.md` は topic レベルで書く。特定の問題名、writeup、relation を参照しない。
- insight には、切り分け方、典型的な仕掛け、初動の見方、解法パターンをまとめる。
- `relations/{topic}.md` は、複数の insights と複数の writeup を結ぶ index として書く。
- relation には、関連 insights、topic の概要、具体例、writeup リンク、比較観点を置く。
- `insights`、`relations`、`writeup` は多対多で扱う。1対1の対応表にしない。
- 1つの writeup が複数 topic に関係する場合は、複数 relation から参照してよい。
- 1つの relation が複数 insight に関係する場合は、`関連 insights` にすべて列挙する。
- 細かい topic ごとにファイルを増やしすぎない。1ファイルが1000行を超えて読みにくくなった場合だけ分割を検討する。

## 参照ルール

- insight は relation や writeup を参照しない。
- relation は1つ以上の insight を参照する。
- relation は1つ以上の writeup を参照する。
- writeup は基本的に1つ以上の relation から参照されるようにする。
- relation は解法の全文を持たず、writeup へ辿るための概要と索引を持つ。

## Writeup 配置

対象サイトや問題セットごとに自然な構造を選ぶ。例:

```
writeup/example-site/no0001-0010/no-0001_タイトル.md
writeup/example-competition/2026-w01/0104_new-year-problem.md
```

各 writeup には、`category`、`difficulty`、`tags` に加え、Source / Explanation / Date / Updated / Answer、問題本文、ヒント、解説、解答を入れる。
LLM が拾う前提なので、見出しと表現は短く揃える。

## 更新手順

- 問題（事例）を追加したら、まず writeup を作る。
- writeup から再利用できる見方を抽出し、関係する relation に概要とリンクを追記する。
- relation から参照すべき insight を確認し、足りない一般知識がある場合だけ insight を追加または更新する。
- 具体的な観察、手順、制約、例外、失敗は writeup に置く。
- relation と insight は必ずしも同時に1ペアで作らない。
