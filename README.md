layers-dot-json-spec
====================
# ウェブ地図レイヤ定義 layers.json 規約（案）
※この規約は検討中のものであり、今後変更する可能性がある。
## 適用範囲
本文書は、画像タイルやGeoJSONタイル等で提供されるウェブ地図のレイヤ定義を共有するJSONファイルのフォーマットを定義する。

## サンプル

```json
{"layers": [
{
  "type": "Layer",
  "title": "地理院タイル（標準地図）",
  "attribution": "地理院タイル（標準地図）",
  "legendUrl": "http://cyberjapan.jp/legend/std.pdf",
  "html": "<h1>地理院タイル（標準地図）</h1><a href='http://cyberjapan.jp/legend/std.pdf'>凡例</a>",
  "url": "http://cyberjapandata-t{s}.gsi.go.jp/xyz/std/{z}/{x}/{y}.png",
  "subdomains": "123"
},
{
  "type": "LayerGroup",
  "title": "写真",
  "open": true,
  "entries": [
  {
    "type": "Layer",
    "title": "最新（2007年）",
    "attribution": "地理院タイル（オルソ画像）",
    "legendUrl": "http://cyberjapan.jp/legend/ort.pdf",
    "html": "<h1>地理院タイル（オルソ画像）</h1><a href='http://cyberjapan.jp/legend/ort.pdf'>凡例</a>",
    "url": "http://cyberjapandata-t{s}.gsi.go.jp/xyz/ort/{z}/{x}/{y}.jpg",
    "subdomains": "123"
  }
}
]}
```

## 規定
1. layers という名前のプロパティにレイヤ定義（Entry）の配列を格納した JSON ファイルによりレイヤ定義を表現する。
2. レイヤ定義（Entry）は、下記 Entry のサブクラスである Layer 又は LayerGroup による。

### Entry
レイヤ及びレイヤグループ共通のプロパティ）の集合。

|属性名|属性値|意味|デフォルト|
|:----|:----|:--|:-------|
|type|"Layer"/"LayerGroup"||"Layer"|
|title|文字列|エントリの名前。レイヤツリーのテキストに使用することを想定する。|""|
|iconUrl|URL|レイヤ又はレイヤグループを表現するアイコンのURL|""|
|legendUrl|URL|凡例のURL|""|
|html|文字列|エントリに関する説明をHTMLで記述。レイヤの諸元表示領域に表示することを想定する。|""|

### Layer
typeをLayerとしたEntry。レイヤを表現する。Entry のプロパティに加えて、下記のプロパティを加える。

|属性名|属性値|意味|デフォルト|
|:----|:----|:--|:-------|
|url|URL|タイルデータのテンプレートURL|""|
|subdomains|L.TileLayerと同じ|L.TileLayerと同じ|L.TileLayerと同じ|
|attribution|L.TileLayerと同じ|L.TileLayerと同じ|L.TileLayerと同じ|
|zIndex|L.TileLayerと同じ|L.TileLayerと同じ|L.TileLayerと同じ|
|maxZoom|L.TileLayerと同じ|L.TileLayerと同じ|L.TileLayerと同じ|
|minZoom|L.TileLayerと同じ|L.TileLayerと同じ|L.TileLayerと同じ|
|maxNativeZoom|L.TileLayerと同じ|L.TileLayerと同じ|L.TileLayerと同じ|


### LayerGroup
typeをLayerGroupとしたEntry。下位のレイヤを取りまとめたレイヤグループを構成する。Entry のプロパティに加えて、下記のプロパティを加える。

|属性名|属性値|意味|デフォルト|
|:----|:----|:--|:-------|
|open|true/false|下位Entryが展開されて表示されるかどうか。|true|
|entries|Entryの配列|下位にあるEntry群|[]|


## 参考文献
1. Leaflet リファレンス http://leafletjs.com/reference.html
