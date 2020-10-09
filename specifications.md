# ウェブ地図レイヤ定義 layers.txt 規約
※この規約は検討中のものであり、今後変更する可能性がある。
## 適用範囲
本文書は、画像タイルやGeoJSONタイル等で提供されるウェブ地図のレイヤ定義を共有するJSONファイル（※）のフォーマットを定義する。

（※）ウェブサーバ及びオペレーティングシステムにおける拡張子の登録状況を考慮し、拡張子をtxtとしている。

なお、地理院地図のソースプログラムにおける「[/layers_txt/layers.txt](https://github.com/gsi-cyberjapan/gsimaps/blob/gh-pages/layers_txt/layers.txt)」は、本仕様で定めるlayers.txtには含めない。

## サンプル
### layers.txt
```javascript
{"layers": [
{
  "type": "Layer",
  "title": "地理院タイル（標準地図）",
  "attribution": "地理院タイル（標準地図）",
  "legendUrl": "https://maps.gsi.go.jp/development/ichiran.html#std",
  "html": "<h1>地理院タイル（標準地図）</h1>",
  "url": "https://cyberjapandata-t{s}.gsi.go.jp/xyz/std/{z}/{x}/{y}.png",
  "subdomains": "123"
},
{
  "type": "LayerGroup",
  "title": "写真",
  "src": "https://cyberjapandata.gsi.go.jp/layers_txt/layers_divided.txt"
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
  "legendUrl": "https://maps.gsi.go.jp/development/ichiran.html#ort",
  "html": "<h1>地理院タイル（オルソ画像）</h1>",
  "url": "https://cyberjapandata-t{s}.gsi.go.jp/xyz/ort/{z}/{x}/{y}.jpg",
  "subdomains": "123"
}
]}
```


## 規定
1. layers という名前のプロパティにレイヤ定義の配列を格納した JSON ファイルによりレイヤ定義を表現する。
2. ファイルの拡張子は.txtとし、文字コードはUTF-8（BOMなし）とする。
3. レイヤ定義は、Layer 又は LayerGroup による。

### Layer
レイヤを表現するプロパティの集合。

|属性名|型|意味|省略可否|デフォルト値|
|:----|:----|:----|:----|:----|
|`type`|Stirng|Layerであることを示す。`"Layer"`で固定。|不可|N/A|
|`id`|Stirng|表示状態の再現に使用。[ココタイル](https://github.com/gsi-cyberjapan/cocotile-spec)に収録。|不可|N/A|
|`title`|Stirng|レイヤの名前。レイヤツリーのテキストとして使用。|不可|N/A|
|`url`|Stirng|タイルデータのテンプレートURL|不可|N/A|
|`subdomains`|[L.TileLayer](https://leafletjs.com/reference-0.7.7.html#tilelayer)と同じ|[L.TileLayer](https://leafletjs.com/reference-0.7.7.html#tilelayer)と同じ|可|[L.TileLayer](https://leafletjs.com/reference-0.7.7.html#tilelayer)と同じ|
|`attribution`|[L.TileLayer](https://leafletjs.com/reference-0.7.7.html#tilelayer)と同じ|[L.TileLayer](https://leafletjs.com/reference-0.7.7.html#tilelayer)と同じ|可|[L.TileLayer](https://leafletjs.com/reference-0.7.7.html#tilelayer)と同じ|
|`cocotile`|Boolean|[ココタイル](https://github.com/gsi-cyberjapan/cocotile-spec)を使って表示範囲に絞込みを有効にするかどうかを示す。|可|`true`|
|`minZoom`|[L.TileLayer](https://leafletjs.com/reference-0.7.7.html#tilelayer)と同じ|[L.TileLayer](https://leafletjs.com/reference-0.7.7.html#tilelayer)と同じ|可|[L.TileLayer](https://leafletjs.com/reference-0.7.7.html#tilelayer)と同じ|
|`maxZoom`|[L.TileLayer](https://leafletjs.com/reference-0.7.7.html#tilelayer)と同じ|[L.TileLayer](https://leafletjs.com/reference-0.7.7.html#tilelayer)と同じ|可|[L.TileLayer](https://leafletjs.com/reference-0.7.7.html#tilelayer)と同じ|
|`maxNativeZoom`|[L.TileLayer](https://leafletjs.com/reference-0.7.7.html#tilelayer)と同じ|[L.TileLayer](https://leafletjs.com/reference-0.7.7.html#tilelayer)と同じ|可|[L.TileLayer](https://leafletjs.com/reference-0.7.7.html#tilelayer)と同じ|
|`iconUrl`|Stirng|レイヤを表現するアイコンのURL|可|`""`|
|`legendUrl`|Stirng|凡例のURL|可|`""`|
|`styleurl`|Stirng|ベクトルタイルのstyle.jsを指定する場合のURL|可|`""`|
|`errorTileUrl`|[L.TileLayer](https://leafletjs.com/reference-0.7.7.html#tilelayer)と同じ|[L.TileLayer](https://leafletjs.com/reference-0.7.7.html#tilelayer)と同じ|可|[L.TileLayer](https://leafletjs.com/reference-0.7.7.html#tilelayer)と同じ|
|`bounds`|[L.TileLayer](https://leafletjs.com/reference-0.7.7.html#tilelayer)と同じ|[L.TileLayer](https://leafletjs.com/reference-0.7.7.html#tilelayer)と同じ|可|[L.TileLayer](https://leafletjs.com/reference-0.7.7.html#tilelayer)と同じ|
|`area`|Object |レイヤを代表する表示位置。Objectは{"lat" : number, "lng" : number, "zoom" : integer}の形で記述し、それぞれ緯度（10進法）、経度（10進法）、ズームレベルを指定する。|可|N/A|
|`html`|Stirng|レイヤに関する説明をHTMLで記述。|可|`""`|

### LayerGroup
下位のレイヤを取りまとめたレイヤグループを構成するプロパティの集合。

|属性名|型|意味|省略可否|デフォルト値|
|:----|:----|:----|:----|:----|
|`type`|Stirng|LayerGroupであることを示す。`"LayerGroup"`で固定。|不可|N/A|
|`id`|Stirng|表示状態の再現に使用。[ココタイル](https://github.com/gsi-cyberjapan/cocotile-spec)に収録。LayerGroupを1つのレイヤとして扱う場合に記述。|可 ※|N/A|
|`title`|Stirng|レイヤグループの名前。レイヤツリーのテキストとして使用。|不可|N/A|
|`toggleall`|Boolean|下位レイヤ群を「全表示」「全非表示」するボタンを表示するかどうかを示す。|可|`false`|
|`entries`|Array|下位にあるLayerまたはLayerGroup群|`entries`属性か`src`属性の<br>いずれかを省略可|`[]`|
|`src`|Stirng|`entries`の配列の内容が存在するlayers.txtのURL|`entries`属性か`src`属性の<br>いずれかを省略可|`""`|
|`iconUrl`|String|レイヤグループを表現するアイコンのURL|可|`""`|
|`legendUrl`|Stirng|凡例等のURL|可|`""`|
|`html`|String|レイヤグループに関する説明をHTMLで記述。|可|`""`|

※ LayerGroup配下のLayerをまとめて1つのレイヤのように表示させたい場合、id属性を記述する。


## 参考文献
1. Leaflet リファレンス https://leafletjs.com/reference-0.7.7.html
