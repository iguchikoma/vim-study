# vim-study

## 繰り返し

| key | description |
|:---|:---|
|.|直前の編集を繰り返す|

## 単語補完

| key | description |
|:---|:---|
|\<C-p\>|単語補完(前方検索)|

## モード

| key | description |
|:---|:---|
|I|行頭から挿入モードへ(insertの略)|
|a|カーソルの後ろから挿入モードへ(appendの略)|
|A|行末から挿入モードへ(insertの略)|
|C|カーソル位置から行末までを消してインサートモードに移る（レジスタにも格納）|
|S|カーソルのある行全体を消してインサートモードに移る|
|s|カーソルのある1文字を消してインサートモードに移る|
|cw|カーソル位置の単語を消してインサートモードに移る|
|gi|最後に入力がされた場所にテキストを入力. goto last insert position and start insert と思ってたがgは単なるprefixかも．後述するgvはgiのヴィジュアル版っぽい|

## 検索

| key | description | 繰り返し | 逆方向への繰り返し |
|:---|:---|:---|:---|
|\*|カーソル位置にある単語を検索する|n|N|
|f{char}/t{char}|行内で文字を前方検索|;|,|
|F{char}/T{char}|行内で文字を後方検索|;|,|
|/pattern\<CR\>|ドキュメント内で前方検索|n|N|
|?pattern\<CR\>|ドキュメント内で後方検索|n|N|

過去の検索履歴を出す場合は/を押した後に上や下の矢印キーを押す

"\>" というのは特別なマーカーで、単語がここで終わっている時だけヒットします。
同じように "\<" は単語の始まりにだけヒットします。つまり、"the" という単語だけ
を探したい場合は、次のようにします。

        /\<the\>

見えないtab等を表示 :set list

検索結果をハイライト表示 :set hls or :set nohls

## 置換

| key | description | 繰り返し | 逆方向への繰り返し |
|:---|:---|:---|:---|
|%s/target/replacement|置換の実行|&|u|

## operator + action
### if you duplicate operator command (e.g. dd), it will apply to current line.

| key | description | 
|:---|:---|
|c|変更|
|d|delete|
|y|yanc|
|g~|change Lowercase and Uppercase mutually|
|gu|change to Lowrcase|
|gU|change to Uppercase|
|>|add indent|
|<|delete indent|
|=|apply auto indent(use case is =G)|

## 挿入モードでの簡単修正

| key | description | 
|:---|:---|
|\<C-h\>|直前の1文字を削除|
|\<C-w\>|直前の1行を削除|
|\<C-u\>|行頭までを削除|

## ノーマルモードへの復帰

\<ESC\>か\<C-[\>でノーマルモードへ戻れる

## 挿入ノーマルモード

挿入モードで編集中に\<C-o\>で1コマンドだけノーマルモードのコマンドが打てる。
use case: \<C-o\>zz で、カーソルがいる行を画面中央に持ってくる

## レジスタ

レジスタの基本的な使い方
"{レジスタ名}{操作系コマンド}
{レジスタ名}はaや1といったレジスタ名を示す英数字記号
{操作系コマンド}はyやd

### レジスタの使用例(格納編)

| key | description | 
|:---|:---|
|"ayy|行全体をヤンクしてaレジスタへ格納|
|"byiw|カーソル位置の単語をヤンクしてbレジスタへ格納|
|"cyi)|()で囲まれた文字列をヤンクしてcレジスタへ格納|
|"dyi>|<>で囲まれた文字列をヤンクしてcレジスタへ格納|

### レジスタの使用例(読み出し編)

| key | description | 
|:---|:---|
|"ap|ノーマルモードでaレジスタの文字列をペースト|
|\<C-r\>b|挿入モードでbレジスタの文字列をペースト|

### レジスタに格納された文字列を確認する方法

| command | description | 
|:---|:---|
|:reg|レジスタの状態の一覧確認|

## 簡単な計算を挿入モードで実行する

| key | description | 
|:---|:---|
|\<C-r\>=6\*35\<CR\>|6 x 35の値を入力してくれる|

## visualモードでの選択状態での端点の切り替え
oを押せばOK

## vitコマンド

以下のような文章があった時にvitと打つとtag内部がvisualモードで選択される

```
<a href ="#">one</a>
<a href ="#">two</a>
<a href ="#">three</a>
```

### オブジェクト単位の移動
[{や]}や[[や]]で{や}や[や]へ移動できる。カーソルが{}[]の上にないときに便利

### オブジェクト単位の選択
aw
iw
aW
iW
as
is
ap
ip
a[
a]
i[
i]

#### 利用例
        "dl"    1文字削除 ("x" と同じです)              dl
        "diw"   inner word を削除                       diw
        "daw"   a word を削除                           daw
        "diW"   inner WORD を削除 (参照: WORD)        diW
        "daW"   a WORD を削除 (参照: WORD)            daW
        "dgn"   次に検索パターンにマッチするものを削除  dgn
        "dd"    1行削除                                 dd
        "dis"   inner sentence を削除                   dis
        "das"   a sentence を削除                       das
        "dib"   inner '(' ')' block を削除              dib
        "dab"   a '(' ')' block を削除                  dab
        "dip"   inner paragraph を削除                  dip
        "dap"   a paragraph を削除                      dap
        "diB"   inner '{' '}' Block を削除              diB
        "daB"   a '{' '}' Block を削除                  daB

the is there
