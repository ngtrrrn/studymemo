特に面白かったことを書いていく
（網羅的に把握するのは諦めました）

- margin-left, rightをautoで中央揃えになる

# flexデザインについて
## 親要素に設定
- flex設定
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
ある条件を満たすと発動するcss
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
$progate-color: #26556a;
と先に定義。
その後の箇所で、代入して使用可能。
また、スコープ（変数を利用できる範囲）も指定可能。

# mixin機能について
@mixin <mixin名> ($<引数名>){
}
で設定。$<引数名>も使用可能。
@include <mixin名>; で呼び出し。

# darken, lighten関数
ex.) color: darken($blue, 10%);
     color: lighten($pink, 20%);

# import 
ex.) @import "_colors.scss";
     @import "variables"; ( "_" と拡張子は省略可)
