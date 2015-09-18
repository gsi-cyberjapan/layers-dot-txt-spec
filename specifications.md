# ウェブ地図レイヤ定義 layers.txt 規約
※この規約は検討中のものであり、今後変更する可能性がある。
## 適用範囲
本文書は、画像タイルやGeoJSONタイル等で提供されるウェブ地図のレイヤ定義を共有するJSONファイル（※）のフォーマットを定義する。

（※）ウェブサーバ及びオペレーティングシステムにおける拡張子の登録状況を考慮し、拡張子をtxtとしている。

## サンプル
### layers.txt
```javascript
{"layers": [
{
  "type": "Layer",
  "title": "地理院タイル（標準地図）",
  "attribution": "地理院タイル（標準地図）",
  "legendUrl": "http://maps.gsi.go.jp/development/ichiran.html#std",
  "html": "<h1>地理院タイル（標準地図）</h1>",
  "url": "http://cyberjapandata-t{s}.gsi.go.jp/xyz/std/{z}/{x}/{y}.png",
  "subdomains": "123"
},
{
  "type": "LayerGroup",
  "title": "写真",
  "src": “http://cyberjapandata.gsi.go.jp/layers_txt/layers_divided.txt”,
}
]}
```
### src属性に記述されたURLのlayers.txt
```javascript
{"layers": [
{
  "type": "Layer",
  "title": "最新（2007年）",
  "attribution": "地理院タイル（オルソ画像）",
  "legendUrl": "http://maps.gsi.go.jp/development/ichiran.html#ort",
  "html": "<h1>地理院タイル（オルソ画像）</h1>",
  "url": "http://cyberjapandata-t{s}.gsi.go.jp/xyz/ort/{z}/{x}/{y}.jpg",
  "subdomains": "123"
}
]}
```

## 規定
1. layers という名前のプロパティにレイヤ定義の配列を格納した JSON ファイル（拡張子はtxt）によりレイヤ定義を表現する。
2. レイヤ定義は、Layer 又は LayerGroup による。

### Layer
レイヤを表現するプロパティの集合。

|属性名|属性値|意味|デフォルト|
|:----|:----|:--|:-------|
|type|Layer|Layerであることを示す。|（必須）|
|id|文字列|表示状態の再現に使用。<a href='https://github.com/gsi-cyberjapan/cocotile-spec'>ココタイル</a>に収録。|""|
|title|文字列|レイヤの名前。レイヤツリーのテキストとして使用。|（必須）|
|url|URL|タイルデータのテンプレートURL|（必須）|
|subdomains|<a href='http://leafletjs.com/reference.html#tilelayer'>L.TileLayer</a>と同じ|<a href='http://leafletjs.com/reference.html#tilelayer'>L.TileLayer</a>と同じ|<a href='http://leafletjs.com/reference.html#tilelayer'>L.TileLayer</a>と同じ|
|maxZoom|<a href='http://leafletjs.com/reference.html#tilelayer'>L.TileLayer</a>と同じ|<a href='http://leafletjs.com/reference.html#tilelayer'>L.TileLayer</a>と同じ|<a href='http://leafletjs.com/reference.html#tilelayer'>L.TileLayer</a>と同じ|
|minZoom|<a href='http://leafletjs.com/reference.html#tilelayer'>L.TileLayer</a>と同じ|<a href='http://leafletjs.com/reference.html#tilelayer'>L.TileLayer</a>と同じ|<a href='http://leafletjs.com/reference.html#tilelayer'>L.TileLayer</a>と同じ|
|maxNativeZoom|<a href='http://leafletjs.com/reference.html#tilelayer'>L.TileLayer</a>と同じ|<a href='http://leafletjs.com/reference.html#tilelayer'>L.TileLayer</a>と同じ|<a href='http://leafletjs.com/reference.html#tilelayer'>L.TileLayer</a>と同じ|
|attribution|<a href='http://leafletjs.com/reference.html#tilelayer'>L.TileLayer</a>と同じ|<a href='http://leafletjs.com/reference.html#tilelayer'>L.TileLayer</a>と同じ|<a href='http://leafletjs.com/reference.html#tilelayer'>L.TileLayer</a>と同じ|
|iconUrl|URL|レイヤを表現するアイコンのURL|""|
|legendUrl|URL|凡例のURL|""|
|html|文字列|レイヤに関する説明をHTMLで記述。|""|
|cocotile|true/false|<a href='https://github.com/gsi-cyberjapan/cocotile-spec'>ココタイル</a>を使って表示範囲に絞込みを有効にするかどうか。|true|


### LayerGroup
下位のレイヤを取りまとめたレイヤグループを構成するプロパティの集合。

|属性名|属性値|意味|デフォルト|
|:----|:----|:--|:-------|
|type|LayerGroup|LayerGroupであることを示す。|（必須）|
|title|文字列|レイヤグループの名前。レイヤツリーのテキストとして使用。|（必須）|
|iconUrl|URL|レイヤグループを表現するアイコンのURL|""|
|legendUrl|URL|凡例等のURL|""|
|html|文字列|レイヤグループに関する説明をHTMLで記述。|""|
|toggleall|true/false|下位レイヤ群を「全表示」「全非表示」するボタンを表示するかどうか。|false|
|entries|Layer 及び LayerGroupの配列|下位にあるLayer 及び LayerGroup群|[]<br>（entries属性かsrc属性のいずれかが必須）|
|src|URL|entriesの配列の内容が存在するlayers.txtのURL|""<br>（entries属性かsrc属性のいずれかが必須）|


## 参考文献
1. Leaflet リファレンス http://leafletjs.com/reference.html


