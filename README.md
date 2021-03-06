# AnQou C Compiler: aqcc

aqcc is yet another tiny self-hosted C compiler with an also tiny assembler,
linker and standard C library.

## To Build

Just `make`.

## Usage

`./aqcc [options] file...`

`options` are:

- `-S`: output an assembly file.
- `-c`: output an object file.
- `-o`: set the output file name.

To find the detail, try `make selfself_test`, which tells you all the things.

## Note

- aqcc is a product of [Security Camp 2018](https://www.ipa.go.jp/jinzai/camp/2018/zenkoku2018_index.html).
Special thanks to @rui314 san and @hikalium san.
- Many features, functions and so on have not yet been implemented in aqcc
that a C compiler generally has.
Feel free to implement missing features and to send pull requests :)


---------

AnQou C Compiler の使い方

## aqcc をビルド

`make` としてください。生成物を削除したいときは、 `make clean` などとしてください。

## aqcc の挙動をテスト

- `make test` 
    - 第一世代（gccなどによりコンパイルされたaqcc）をテスト
- `make self_test`
    - 第二世代（第一世代によりコンパイルされたaqcc）をテスト
- `make selfself_test`
    - 第三世代（第二世代によりコンパイルされたaqcc）をテスト
    - 第二世代と第三世代に違いがないことも確認されます。

## 一般のCファイルをコンパイル

`./aqcc [options] file...`

`options` には以下のようなものを使用できます。

- `-S`
    アセンブリファイルを出力します。
- `-c`
    オブジェクトファイルを出力します。
- `-o out`
    出力ファイル名を指定できます。

`program.c` を以下のようにしてコンパイルし、実行できます。
`aqcc` や `program.c` などは適宜読みかえてください。

```
$ ./aqcc program.c -o program
$ ./program
```

なお、`#include <stdio.h>` などとはできません。
`program.c` の中にこのような構文が含まれている場合は、取り除いて下さい。
その代わりに、自前で `puts()` 関数などの プロトタイプ宣言を `program.c` の冒頭に加えてください。
なお、カレントディレクトリ内のファイルはインクルードできますので、 `#include "aqcc.h"` などとインクルードして、
`aqcc.h` に記されているプロトタイプ宣言を流用できます。

また、標準ライブラリのうち提供されている機能はごく僅かです。
`stdlib.c` などを参照して下さい。aqccが自動でこれらをリンクすることはありません。明示的に指定してください。

## 謝辞

aqccは[セキュリティキャンプ全国大会2018](https://www.ipa.go.jp/jinzai/camp/2018/zenkoku2018_index.html)の成果物です。
講師の@rui314さんと@hikaliumさんに深く感謝申し上げます。

## 資料

- [セルフホストCコンパイラaqcc 開発記](https://anqou.net/poc/2018/08/21/post-1853/)
    - セキュリティキャンプの前日にセルフホストを達成するまでのaqcc開発日記。
- [ seccamp2018でセルフホストCコンパイラをつくった](https://speakerdeck.com/anqou/seccamp2018deseruhuhosutockonpairawotukututa)
    - Kernel/VM関西9回目での発表資料。
    - [ベストオブ頭おかしい発表に選ばれました](https://twitter.com/kernelvm/status/1044153390060625920)。ありがとうございます。

