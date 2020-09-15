特に面白かったことを書いていく
（網羅的に把握するのは諦めました）

- HTML 内でも style 属性にスタイル情報を書ける
- margin-left, right を auto で中央揃えになる
- opacity は色・画像の透明度を操作できる（有能そう）

# スタイルの継承という概念

例：color は継承する。border は継承しない。
本来継承しないものを継承させたい場合は
子要素側で、同じプロパティに対し、値を inherit とする。

# line-height の値表記について

- line-height:14px;
  ピクセル指定。子要素にも同じ値で継承される。

- line-height:3em;
  指定された要素の font-size の 3 倍のピクセル。子要素にも同じ値で継承される。

- line-height:3;
  指定された要素の font-size の 3 倍のピクセル。子要素には「font-size の 3 倍」という概念だけ継承される。

# padding プロパティの値の引数について

- padding 40px 30px 20px 10px;
  top から時計回り。top, right, bottom, left
- padding 40px 30px 10px;
  top, right-left, bottom
- padding 40px 10px;
  top-bottom, right-left
- padding 40px;
  top-right-bottom-left all

# margin の相殺

垂直方向に margin が重なると、少ない方の margin が効力を失う

# display プロパティについて

- display: block;
  追加順：下に連なる
  width: 親要素の幅
  height: コンテンツの高さ
  width, height プロパティ設定で上書き可能

- display: block;
  追加順：左に詰めて追加
  width: コンテンツの幅
  height: コンテンツの高さ
  width, height プロパティ設定で上書き不可

- display: inline-block;
  追加順：左に詰めて追加
  width: コンテンツの幅
  height: コンテンツの高さ
  width, height プロパティ設定で上書き「可能」

- display: none;
  要素を表示しない

# position プロパティについて

- position: static;
  デフォルトの設定

- position: relative;
  static であった時に対して
  top, right, left, bottom プロパティ分移動

- position: fixed;
  ブロック組みから外れる。要素が飛ばされる
  画面上の位置は固定
  top 上端から px 数の距離
  right 右端から px 数の距離
  bottom 下端から px 数の距離
  left 左端から px 数の距離

- position: absolute;
  親要素が position:static;の場合
  スクロールすると流れていく
  top 最上部分表示ウィンドウ上端から px 数の距離
  right 最上部分表示ウィ„ンドウ右端から px 数の距離
  bottom 最上部分表示ウィンドウ下端から px 数の距離
  left 最上部分表示ウィンドウ左端から px 数の距離

親要素が position:relative;の場合
top 親要素の上端から px 数の距離
right 親要素の右端から px 数の距離
bottom 親要素の下端から px 数の距離
left 親要素の左端から px 数の距離

# z-index プロパティについて

数値の大きい順で上にくる

# box-sizing

border-box にすると、width と height の指定値の中に、border と padding が含まれる

# calc 関数

使用例
width: calc((100% - 40px) /3);
100%は画面の表示幅

# box-shadow

box-shadow: 10px 5px 3px 10px rgba(0, 0, 0, 0.3);
1 つめ：影の左右位置（正：right, 負：left）
2 つめ：影の上下位置（正：top, 負：bottom）
3 つめ：影のぼかし具合
4 つめ：影の太さ

# float, clear

- float: right;
  通常の配置からは外れ、その後に続く要素は画像がなかったかのように配置されるが
  テキストだけは回り込むように配置
- clear: left / right / both;
  指定した方向では要素が重ならないように空間を確保する

# flex デザインについて

## 親要素に設定

- flex 設定
  display: flex;
- 折り返し設定
  flex-wrap: wrap;
- 並べる方向の設定
  flex-direction: column;

## 子要素に設定

- 引き伸ばし設定
  flex: auto;
- 折り返し設定
  width: 50%;

# メディアクエリについて

ある条件を満たすと発動する css
@media (max-width: 1000px){

}

# 入れ子構造について

.header {
font-size:14px;
ul {
padding:10px;
}
}
※あくまで階層構造になっている場合のみ。同階層になっている場合は&を用いて表現。
例：

<li>あいうえお</li>
<li class="current-page">かきくけこ</li>
に対して
li {
  font-size:14px;
  &.current-page{
    color:red;
  }
}
と、&(親セレクタを参照する記号)を用いて表現する。

# 変数について

\$progate-color: #26556a;
と先に定義。
その後の箇所で、代入して使用可能。
また、スコープ（変数を利用できる範囲）も指定可能。

# mixin 機能について

@mixin <mixin 名> ($<引数名>){
}
で設定。$<引数名>も使用可能。
@include <mixin 名>; で呼び出し。

# darken, lighten 関数

ex.) color: darken($blue, 10%);
     color: lighten($pink, 20%);

# import

ex.) @import "_colors.scss";
@import "variables"; ( "_" と拡張子は省略可)
