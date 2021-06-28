# リレーコンピュータ

[Maker Faire Tokyo](https://makezine.jp/event/mft2021/) (2021/10/2-3 @東京ビックサイト) で展示予定

![](RelayAdder.jpeg)

コンピュータといえば半導体という印象が強いですが，実はトランジスタが登場する何十年も前からコンピュータは存在しました．リレーコンピュータもそんな前半導体時代のコンピュータのひとつです．

今回のリレーコンピュータプロジェクトの目標は，昔の再現ではなく，現代的な視点からの再構築です．半導体時代にあえてリレーという制約条件を課したとき，どんなコンピュータができるのか．

## リレーとは？

電磁石で動くスイッチです．

![](relay.drawio.svg)

原理は小学生の理科の知識でわかるぐらい単純です．

## 順序回路

<blockquote class="twitter-tweet"><p lang="ja" dir="ltr">カウントアップができました！実質CPU <a href="https://t.co/3P3C7U6cvV">pic.twitter.com/3P3C7U6cvV</a></p>&mdash; Next-MICON (@Next_MICON) <a href="https://twitter.com/Next_MICON/status/1407661031996878850?ref_src=twsrc%5Etfw">June 23, 2021</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>

![](increment.drawio.svg)

## アーキテクチャの考察

### リレーの特徴

リレーのスイッチング時間は半導体に比べて圧倒的に遅い．さらに消費電力も圧倒的に多い．

|                  | スイッチング時間 | 動作電流 | 動作電圧 |
| ---------------- | :--------------: | -------- | -------- |
| リレー(小信号用) |     数十 ms      |          |          |
| 半導体(CMOS)     |      数 ns       |          |          |

まともに争っても仕方ないので，ここでリレーの特徴を挙げてみる

- 大きい
- ノイズ・熱などにタフ

### モジュラーアーキテクチャ

1. 簡潔な命令セットでクロック周波数を高速化
2. 計算モジュールを交換することでさまざまな計算を高速に実行可能

細かい粒度で並列化することで，重い計算のせいでプログラムが遅延しないようにする

![](arch.drawio.svg)

| Function | OP  | OPR1       | OPR2          |
| -------- | --- | ---------- | ------------- |
| NOP      | 00  | -          | -             |
| JMPIF    | 01  | Condition  | JumpTo        |
| MOV      | 10  | SourceAddr | DirectionAddr |
| LOAD     | 11  | Immidiate  | DirectionAddr |
