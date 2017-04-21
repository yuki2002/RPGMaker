[トップページに戻る](README.ja.md)

# [FTKR_ExItemConfig_ItemBasic](FTKR_ExItemConfig_ItemBasic.js) プラグイン

アイテムの基本設定を拡張するプラグインです。

ダウンロード: [FTKR_ExItemConfig_ItemBasic.js](https://raw.githubusercontent.com/futokoro/RPGMaker/master/FTKR_ExItemConfig_ItemBasic.js)

## 目次

以下の項目の順でプラグインの使い方を説明します。
1. [概要](#概要)
2. [アイテムの基本設定の変更](#アイテムの基本設定の変更)
* [プラグインの更新履歴](#プラグインの更新履歴)
* [ライセンス](#ライセンス)

## 概要

本プラグインを実装することで、アイテム(武器・防具含む)に、以下の仕様を追加します。

1. アイテムの価格を数値以外を設定することができます。
2. 事前に複数の設定を登録し、ゲーム内で条件付けでアイテムの設定を変えることができます。

## アイテムの基本設定の変更

アイテム(武器・防具含む)に以下のノートタグを追記することで、一つのアイテムに対して複数の基本設定を登録することができます。

データベース上の設定は、データID0 に登録されます。
データID0は、他のIDの適用条件が満たない場合に適用します。

注意：データIDを追加する場合は、必ずID1 から順番に追加してください。

データID x に対して code部の設定を登録します。
```
<EIC 基本設定: x>
code
</EIC 基本設定>
```

### code部で設定できる項目
```
有効条件: 計算式
enabled: eval
```
データID x の適用条件を 計算式(eval) で設定します。
適用条件が複数のIDで重なった場合は、IDが大きい方を適用します。
適用条件を設定しない場合、常に有効になります。

これ以降のcodeは、設定しなかった場合、データベース上の設定を適用します。
```
名前: アイテム名
name: アイテム名
```
アイテムの名前を'アイテム名'に変更します。

```
アイコン: y
icon: y
```
アイコンを y に変更します。

```
価格: 計算式
price: eval
```
アイテムの価格を 計算式(eval) で設定した値に変更します。

```
説明: 説明文
desc: 説明文
```
アイテムの説明を'説明文'に変更します。
制御文字を使用できます。
二つ設定することで、説明文を2行に表示できます。

```
使用可能時: 状況
used: 状況
```
使用可能時の設定を'状況'に変更します。
'状況'には以下の文字または数字を入力します。
* 0 - 常時
* 1 - バトル画面
* 2 - メニュー画面
* 3 - 使用不可 


### 計算式(eval) の値について
計算式(eval)は、ダメージ計算式のように、計算式を入力することで、
固定値以外の値を使用することができます。以下のコードを使用できます。
* a[x].param - アクターID x のパラメータを参照します。
* s[x]       - スイッチID x の状態を参照します。
* v[x]       - 変数ID x の値を参照します。
* iv[x]      - アイテムのセルフ変数ID x の値を参照します。(*1)

(*1) セルフ変数を使用する場合は、FTKR_ItemSelfVariables.jsが必要です。


### 入力例
アイテムのセルフ変数ID1 が O の時にアイテムの設定を変える場合の設定。
鑑定イベント等を作成し、アイテムのセルフ変数ID1を 0 以外に変えるとアイテム本来の表示になります。
```
<EIC 基本設定: 1>
有効条件: !iv[1]
名前: 何かのアイテム
アイコン: 160
価格: 0
説明: 何に使えるか不明なアイテム。
説明: 鑑定するまで使用できない。
使用可能時: 使用不可
</EIC 基本設定>
```

[目次に戻る](#目次)

## プラグインの更新履歴

| バージョン | 公開日 | 更新内容 |
| --- | --- | --- |
| [ver1.0.0](FTKR_ExItemConfig_ItemBasic.js) | 2017/04/14 | 初版公開 |

## ライセンス

本プラグインはMITライセンスのもとで公開しています。

[The MIT License (MIT)](https://opensource.org/licenses/mit-license.php)

#
[目次に戻る](#目次)

[トップページに戻る](README.ja.md)