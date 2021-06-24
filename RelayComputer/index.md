# リレーコンピュータ

[Maker Faire Tokyo](https://makezine.jp/event/mft2021/) (2021/10/2-3 @東京ビックサイト) で展示予定

[製作進捗](./progress/)


![](RelayAdder.jpeg)


トランジスタを使わずにリレーで計算をするコンピュータです．

## リレーとは？

![](relay.drawio.svg)

電磁石で動くスイッチです．

## 簡単なCPU

<blockquote class="twitter-tweet"><p lang="ja" dir="ltr">カウントアップができました！実質CPU <a href="https://t.co/3P3C7U6cvV">pic.twitter.com/3P3C7U6cvV</a></p>&mdash; Next-MICON (@Next_MICON) <a href="https://twitter.com/Next_MICON/status/1407661031996878850?ref_src=twsrc%5Etfw">June 23, 2021</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>

![](increment.drawio.svg)

## アーキテクチャ

1. 簡潔な命令セットでクロック周波数を高速化
2. 計算モジュールを交換することでさまざまな計算を高速に実行可能

![](arch.drawio.svg)

| Function | OP  | OPR1       | OPR2          |
| -------- | --- | ---------- | ------------- |
| NOP      | 00  | -          | -             |
| JMPIF    | 01  | Condition  | JumpTo        |
| MOV      | 10  | SourceAddr | DirectionAddr |
| LOAD     | 11  | Immidiate  | DirectionAddr |


