# RelayComputer / リレーコンピュータ

A Computer made with no semiconductor but relay. In order to be able to solve a wider variety of problems faster, this CPU is based on modular architecture. 

![](RelayAdder.jpeg)

![](arch.drawio.svg)

| Function | OP  | OPR1       | OPR2          |
| -------- | --- | ---------- | ------------- |
| NOP      | 00  | -          | -             |
| MOV      | 01  | SourceAddr | DirectionAddr |
| LOAD     | 10  | Immidiate  | DirectionAddr |
| JMPIF    | 11  | Condition  | JumpTo        |
