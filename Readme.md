# SweepOptimizer

## 概要
Cygames Inc.提供のスマホゲー「ルームスイーパ」の解を探索します。  
(https://chogetsuku.jp/product/roomsweeper/)

## 使い方
`usage: SweepOptimizer input.txt`

- input.txt(問題ファイル)の形式は後述します
- 出力としては、初期盤面・解答盤面・各キャラクターの座標の推移があります
- 座標は[X,Y](どちらにせよ0スタート、左上基準)で、歩数は現在/最大歩数です

## 入出力例

`SweepOptimizer sample.txt`

    横5マス,縦5マス  
    ×××□□  
    □□瓶□□  
    □□ゴリ□  
    □実□×□  
    水□□□■  
    男の子[0,0](0/7)歩 男の子[3,3](0/4)歩 女の子[1,0](0/4)歩 Robot[2,0](0/3)歩  
    横5マス,縦5マス  
    ×××××  
    ×××××  
    ××ゴリ×  
    ×××××  
    ××××■  
    男の子[3,4](7/7)歩 男の子[4,0](4/4)歩 女の子[2,3](4/4)歩 Robot[3,0](3/3)歩  
    男の子 [0,0]->[0,1](下)->[0,2](下)->[0,3](下)->[0,4](下)->[1,4](右)  
    　　　->[2,4](右)->[3,4](右)  
    男の子 [3,3]->[4,3](右)->[4,2](上)->[4,1](上)->[4,0](上)  
    女の子 [1,0]->[1,1](下)->[1,2](下)->[1,3](下)->[2,3](右)  
    Robot [2,0]->[2,1](下)->[3,1](右)->[3,0](上)  
    処理時間：159[ms]
   
## 入力ファイルの形式
- 1行目は「横のマス数(以下X) 縦のマス数(以下Y)」
- 2〜Y+1行目は「床の状態を0〜10でスペース区切りで記述」
- Y+2行目は「男の子の人数 それぞれの最大歩数をスペース区切りで記述」
- Y+3行目は「女の子の人数 それぞれの最大歩数をスペース区切りで記述」
- Y+4行目は「ロボットの人数 それぞれの最大歩数をスペース区切りで記述」
- 床の状態は以下の通り

|数字|対応する状態|記号|備考                      |
|----|------------|----|--------------------------|
|0   |汚れた床    |□  |これを全て綺麗な床にしたい|
|1   |綺麗な床    |×  |                          |
|2   |男の子      |男  |水たまりを処理できる      |
|3   |女の子      |女  |リンゴを処理できる        |
|4   |ロボット    |Ｒ  |ビンを処理できる          |
|5   |水たまり    |水  |処理後は綺麗な床になる    |
|6   |リンゴ      |実  |処理後は綺麗な床になる    |
|7   |ビン        |瓶  |処理後は綺麗な床になる    |
|8   |ゴミ箱      |ゴ  |リンゴの捨て場所          |
|9   |リサイクル箱|リ  |ビンの置き場所            |
|10  |障害物      |■  |進入不可                  |

## ユーティリティについて
- utilityフォルダに、補助ソフト(マップエディタ)を置いておきました
- 画面サイズをインプットボックスで指定し、マップの状態はマス目をクリック/右クリックして切り替えます
- 画面下の空白部分をクリックするとマップをコピーし、右クリックするとマップを消去できます
- 各掃除人の最大歩数は指定できませんので、別途テキストエディタで修正してください
- ファイルのドラッグ＆ドロップには対応していません

## 注意点
- ベタな実装なので別に速くはないです
- サンプルファイルは完全に自作です
- 本体はC++(Visual Studio 2015)で書きましたが、補助ソフトはHSP3で書きました

## ライセンス
MITライセンスとします。

## 開発者
|名前       |GitHub                        |Twitter                      |
|:----------|:-----------------------------|:----------------------------|
|YSR        |https://github.com/YSRKEN     |https://twitter.com/YSRKEN   |

## バージョン履歴
### Ver.1.0.0
とりあえずリリースしました。
