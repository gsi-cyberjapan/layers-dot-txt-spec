layers-dot-txt-spec
====================

- [ウェブ地図レイヤ定義 layers.txt 規約](specifications.md)
- [地理院地図の layers.txt 一覧](list.md)

## 変更履歴
|日付      |内容      |
|:---------|:---------|
|2014-10-07|ウェブサーバ及びオペレーティングシステムにおける拡張子の登録状況を考慮し、拡張子をjsonからtxtに変更。|
|2015-08-28|[地理院地図の layers.txt 一覧](list.md)を追加し、仕様部分を [specifications.md](specifications.md) に分離。|
|2015-09-18|[ウェブ地図レイヤ定義 layers.txt 規約](specifications.md) を更新。<ul><li>Entryを解消し、LayerとLayerGroupに分解</li><li>open属性、zIndex属性の削除（活用の見込みなし。）</li><li>id属性の追加（表示状態の再現に使用。<a href='https://github.com/gsi-cyberjapan/cocotile-spec'>ココタイル</a>に収録。）</li><li>cocotile属性の追加（表示範囲に絞込みに<a href='https://github.com/gsi-cyberjapan/cocotile-spec'>ココタイル</a>を使用するかどうか。）</li><li>toggleall属性の追加（全表示・全非表示ボタンを表示するかどうか。）</li><li>src属性の追加（layers.txtの分割に使用。）</li><li>その他軽微な更新</li></ul>|
