# Knowledge

このディレクトリは、個別事例から再利用可能な知見を育てるための知識ベースです。
何も知らない LLM が、まず `insights/` で大枠を掴み、次に `relations/` で具体的な論点と事例の対応を知り、最後に `writeup/` で個別事例の詳細を確認できる流れを想定します。

## 役割

- `insights/` は topic レベルの一般知識です。特定の writeup や relation を参照せず、見方、切り分け方、定石だけを書きます。
- `relations/` は接続層です。関連する insights を参照し、具体例つきの概要を書き、対応する writeup への index として機能させます。
- `writeup/` は個別事例です。問題本文、ヒント、解説、答え、観察、実際の手順など、具体的な情報を残します。

## 接続ルール

- `insights`、`relations`、`writeup` は多対多で扱います。1対1対応にしません。
- insight は topic の理解を助ける抽象知識として書き、relation や writeup へのリンクを持ちません。
- relation は1つ以上の insight を参照し、1つ以上の writeup を参照します。
- writeup は基本的に1つ以上の relation から参照されるようにします。
- relation は「この topic の具体例を探す入口」です。詳細な解法そのものは writeup に置き、relation には概要、比較観点、具体例の短い説明を書きます。
- relation が複数の insight を参照している場合、その topic には複数の見方が必要だと判断します。

## 構成

```text
.knowledge/
├── README.md
├── SKILL.md
├── insights/
│   ├── language.md
   ├── layout.md
   └── number.md
├── relations/
│   ├── language.md
   ├── layout.md
   └── number.md
└── writeup/
    └── example-site/
        ├── README.md
        ├── no0001-0010/
        ├── no0011-0020/
        └── ...
```

## Writeup 配置

writeup は対象サイトや問題セットごとに、管理しやすい粒度で置きます。

```text
writeup/example-site/no0001-0010/no-0001_タイトル.md
writeup/example-site/no0011-0020/no-0011_タイトル.md
```

各 writeup には、少なくとも次を入れます。

- Source / Explanation / Date / Updated / Answer
- 問題画像
- 問題本文
- ヒント
- 解説
- 解答

## 運用

- writeup を追加・更新したら、関係する relation に追記します。
- relation には、関連 insights と確認元 writeup へのリンクを入れます。
- 新しい一般知識が出たときだけ insight を追加・更新します。
- 具体的な観察、例外、入力、制約、問題ごとの差分は writeup に置きます。
- 既存 topic で自然に束ねられるなら、むやみに insight や relation ファイルを増やしません。

## 使い分け

- insight: 「この形式の事例では、どんな観点で見るか」
- relation: 「この topic は、どの insights とどの writeup を結ぶか」
- writeup: 「その事例で実際に何が出て、どう解いたか」
