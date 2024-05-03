class: middle, center

<img src="./assets/logo.png" width="300" />

# JSR の紹介

Yoshiya Hinosawa @kt3k

---
class: text-4xl

# Agenda

- JSR の狙い
- JSR の特徴

---

## 話す人: Yoshiya Hinosawa @kt3k

<img src="./assets/hinosawa.jpg" width="180" />

- x.com: @kt3k
- github: @kt3k

Deno の中の人。主に Standard Library (deno_std) と Deno Deploy の UI を担当

---
# npm

- プログラミング界の最大のパッケージレジストリ
- 250万パッケージが存在

<img src="./assets/modulecounts.png" width="500" />


---
# npm is great!

---
class: middle, center inverse

# しかし

---

# npm はレガシー

- ES6 も TS も無い時にデザインされたため古くなっている
- CommonJS がデフォルト
  - CJS と ESM をサポートするための conditional exports
  - モジュール定義が複雑、dual package 辛い
- TypeScript に関するサポートが無い
  - 自前で d.ts をビルド or DefinitelyTyped を手動でメンテ -> 辛い

---
# npm の開発は低調(?)

- 新機能があまり追加されていない
- npm は2020年に github に買収された
- 買収直前に主要メンバーが npm を去った
- Open Source では無いので、コミュニティー主体で開発を進めることも出来ない

---

## JSR チームが考えたこと

--

=> レジストリに関する革新がここ数年止まってしまっているのではないか?

--

=> TS はメインストリームと言われているのに「TS で普通にライブラリを書くこと」が辛いのはおかしいのでは?

--

=> ESM と TS を前提としたレジストリを0から設計したら良いのではないか?

---
class: middle center

# Introducing

<img src="./assets/logo.png" width="400" />

--

JSR = JavaScript Registry

---

# JSR の特徴

- TypeScript を直接パブリッシュ出来る
- モジュール解決は ESM だけ (CommonJS は無し)
- npm と互換性あり
- 複数ランタイムを意識した作り
- 各種 DX 改善
- オープンソース

---

# npn 互換性

- JSR パッケージから npm パッケージを使える
- npm パッケージから JSR パッケージを使える

---

# npm 互換性

- JSR は npm とは別の何かではなく、npm の資産を活用しつつ拡張するもの (スーパーセット)

<p class="text-center">
<img src="./assets/jsr-include-npm.png" width="500" />
</p>


---

# TypeScript サポート

- TypeScript を直接パブリッシュできる
- トランスパイルが不要
- d.ts は JSR が自動生成
- TypeScript の doc コメントからドキュメントページを自動生成

--

<p class="text-center">
「ソースコードを書いて publish するだけ」
</p>

---

# 複数ランタイム前提

- サポートしてるランタイムを JSR 上で設定できる

<p class="text-center">
<img src="./assets/runtime-supports.png" width="500" />
</p>

---
## 改善されたDX(ライブラリ提供者目線)

- ビルドしなくて良い
- ドキュメントはソースコードに書くだけで良い

---
## 改善されたDX(ライブラリ利用者目線)

- 型が壊れている事が無い
- 何が export されているか必ず分かる
- ドキュメントがある可能性が高い
- どのランタイムがサポートされているか分かる

---
# JSR はオープンソース

- https://github.com/jsr-io/jsr で開発されている
- レジストリの全体が公開
- セルフホストも可能
- 機能要望、機能提案なども可能

---
### 注意点

- JSR は ESM しかサポートしない
- CJS を使っているユーザーはサポートできない

--
- CJS からの利用が絶対必要な人は「まだ」使わないほうが良いかもしれません

--
- ただし Node.js v22 で require(ESM) ができるようになる予定がある
  - => require sync esm で検索

---
### FAQ: JSR って Deno のためのものではないの?

- JSR の開発者は今のところ Deno の開発者が多い
- Deno のためのより良いレジストリを作りたいと言うのがモチベーションの1つとしてあった
- 設計を進める中で、Deno に限らず、すべてのランタイムのためのレジストリを作るべきという目的意識に変わっていった
- Deno は JSR でマネタイズする予定はない

---
class: middle center

# <p class="flex items-center justify-center gap-2">Let's try <img src="./assets/logo.png" width="180" /></p>

# https://jsr.io

--

ご清聴ありがとうございました 🙇‍♂️
