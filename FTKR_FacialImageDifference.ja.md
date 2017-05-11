[トップページに戻る](README.md)

# [FTKR_FacialImageDifference](FTKR_FacialImageDifference.js) プラグイン

アクターの状態によって顔画像を変えるプラグインです。

ダウンロード: [FTKR_FacialImageDifference.js](https://raw.githubusercontent.com/futokoro/RPGMaker/master/FTKR_FacialImageDifference.js)

## 目次

以下の項目の順でプラグインの使い方を説明します。
1. [概要](#概要)
2. [プラグインの登録](#プラグインの登録)
2. [基本仕様](#基本仕様)
2. [FTKR_CustomSimpleActorStatusと併用する場合](#FTKR_CustomSimpleActorStatusと併用する場合)
3. [FTKR_CSS_BattleStatusと併用する場合](#FTKR_CSS_BattleStatusと併用する場合)
3. [FTKR_ExSvMotionと併用する場合](#FTKR_ExSvMotionと併用する場合)
* [プラグインの更新履歴](#プラグインの更新履歴)
* [ライセンス](#ライセンス)

## 概要

本プラグインを実装することで、アクターのさまざまな状態において表示する顔画像を変更します。

## プラグインの登録

以下のプラグインと組み合わせて使用する場合は。
プラグイン管理画面で、以下の順の配置になるように登録してください。
```
FTKR_CustomSimpleActorStatus.js
FTKR_CSS_***の各プラグインはここに入れること
FTKR_CSS_BattleStatus.js
FTKR_ExSvMotion.js
FTKR_FacialImageDifference.js
```

## 基本仕様

本プラグインを単独で使用する場合、アクターの以下の状態によって、メニュー画面やステータス画面等で表示する顔画像が変わります。

* 通常
* 瀕死時
* 状態異常
* 睡眠
* 戦闘不能

なお、デフォルトのプラグインの状態では、すべてのアクターの状態に対して 0番の画像を指定しています。
必要に応じて、プラグインパラメータに値を設定してください。

### アクターの顔画像について

本プラグインを使用する場合、アクターの顔画像は以下の規格のものを使用してください。

* アクター１人に対して画像ファイルを１つ使用
* 一つの顔画像サイズ：144 * 144
* 一つのファイルには、顔画像を横に６列、縦に３行まで配置できます。
* 顔画像の番号は、左上を 0番、一つ右を 1番、一つ下を 6番と数えます。
* 一つの画像ファイルで最大18種類の顔画像を設定できます。

ファイルは、img/face/ フォルダに保存してください。

指定された番号の箇所に、画像がない場合は空欄で表示されますので注意してください。

[目次に戻る](#目次)

## FTKR_CustomSimpleActorStatusと併用する場合

`FTKR_CustomSimpleActorStatus`の設定によって表示する顔画像を変更します。
使用する番号は、基本仕様と同じです。

また、`FTKR_CustomSimpleActorStatus`の拡張プラグインによって、メニュー以外に表示した顔画像についても、同様に変更します。
 * FTKR_CSS_DetailedStatus
 * FTKR_CSS_SkillStatus


### FTKR_CSS_BattleStatusと併用する場合

バトル中のアクターの状態によって、顔画像を変更します。
アクターのアクション時にも、顔画像を変更することができます。

[目次に戻る](#目次)

## FTKR_ExSvMotionと併用する場合

`FTKR_ExSvMotion`の設定によって表示する顔画像を変更します。

`FTKR_ExSvMotion`の設定で、各状態のモーションを変更していた場合は、その設定に合わせて、顔画像も同じモーションの番号に変更します。

また、回復時、およびカスタムモーション時に使用するの顔画像番号を
設定できます。

### 別画像モーション時の画像
別画像モーション時には、アクターのメモ欄で設定した顔画像ファイルを使用します。
アクターのメモ欄に以下のタグを追記してください。

```
<FID_顔画像:filename>
<FID_FACE_IMAGE:filename>
```

画像ファイル filename.png は img/face/ に保存してください。

[目次に戻る](#目次)

## プラグインの更新履歴

| バージョン | 公開日 | 更新内容 |
| --- | --- | --- |
| [ver1.0.1](FTKR_FacialImageDifference.js) | 2017/05/11 | フロントビュー戦闘で顔画像が表示しない不具合を修正<br>顔画像にダメージポップアップやアニメーションを表示する機能を追加<br>YEP_BattleEngineCoreに対応 |
| ver1.0.0 | 2017/05/10 | 初版公開 |

## ライセンス

本プラグインはMITライセンスのもとで公開しています。

[The MIT License (MIT)](https://opensource.org/licenses/mit-license.php)

#
[目次に戻る](#目次)

[トップページに戻る](README.md)