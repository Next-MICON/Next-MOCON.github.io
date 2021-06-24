# リレーコンピュータ

[Maker Faire Tokyo](https://makezine.jp/event/mft2021/) (2021/10/2-3 @東京ビックサイト) で展示予定

[製作進捗](./progress/)


![](RelayAdder.jpeg)


トランジスタを使わずにリレーで計算をするコンピュータです．

## リレーとは？

![](relay.drawio.svg)

電磁石で動くスイッチです．



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


