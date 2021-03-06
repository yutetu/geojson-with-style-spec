geojson-with-style-spec
=======================
# スタイルつき GeoJSON 規約
※この規約は検討中のものであり、今後変更する可能性がある。
## 適用範囲
この文書は、スタイル属性を GeoJSON ファイルの内部に埋め込む方法を定義する。スタイル属性を埋め込んだ GeoJSON ファイル（以下「スタイルつき GeoJSON」という）は、今後「KMLウェブ地図プロファイル」（http://portal.cyberjapan.jp/help/howtouse/30Jul2013_kmp.pdf ）を置き換えていくことを想定している。

## 規約
1. properties に、Leaflet の path オプションその他のスタイル属性を埋め込む。但し、スタイル用のオプションであることを明示するために、オプション名の前にはアンダーバー(_)を加える。
2. スタイル属性は、Leaflet の Icon, DivIcon, CircleMarker に用いられているものを用いる。また、これらのうちどのマーカー種類を使うか明示するため、_markerType にクラス名（Icon, DivIcon 又は CircleMarker）を記載する。

## サンプル
```json
{"type": "FeatureCollection", "features": [
{
  "type": "Feature",
  "geometry": {"type": "Point", "coordinates": [135, 35]},
  "properties": {
    "名称": "○○公園",
    "住所": "○○県○○市○○",
    "_iconUrl": "http://cyberjapan.jp/symbols/010.png", 
    "_iconSize": [20, 20],
    "_iconAnchor": [10, 10],
    "_className": "park"
  }
}
]}
```

## スタイル属性一覧

|属性名|属性値|デフォルト|
|:----|:----|:--|
|_markerType|Icon/DivIcon/CircleMarker|Icon|
|_className, _stroke, _color, _weight, _opacity, _fill, _fillColor, _fillOpacity, _dashArray, _lineCap, _lineJoin, _clickable|L.Pathの仕様による|L.Pathの仕様による|
|_iconUrl, _iconSize, _iconAnchor|L.Iconの仕様による|L.Iconの仕様による|
|_html,|L.DivIconの仕様による|L.DivIconの仕様による|
|_radius,|L.CircleMarkerの仕様による|L.CircleMarkerの仕様による|

## 今後の課題
- 「KMLウェブ地図プロファイル」からの上位互換性の確保。

## 参考文献
1. Leaflet リファレンス http://leafletjs.com/reference.html （特にIcon, DivIcon、CircleMarker 及び Path）

