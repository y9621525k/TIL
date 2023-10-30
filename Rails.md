## アセットパイプライン
JavaScript、CSS、画像などのリソース(アセット)を効率的に扱うための仕組み  
開発者が書いたJavaScriptやCSSを、最終的にアプリを使う上で都合の良い状態(ブラウザが読み取れる形式で実行速度が速くブラウザキャッシュに対して最適化される)にするためのパイプライン処理を行う  
sprockets-railsというgemにて提供されるSprocketsの機能で、デフォルトで有効

## 各ディレクトリの構造
appディレクトトリ：Model、View、Controller、helperファイル、Assetファイル
onfigディレクトリ：ルーティング、各種設定ファイル、master.key
dbディレクトリ：データベースのスキーマファイル、マイグレーションファイル

## layoutファイル
Webページを表示する際に必要な情報（html head bodyタグなど）を記載するファイル。Viewページを作成する際に最初に読み込まれる。
デフォルトではapplication.html.erbが読み込まれ、タグやタグの中で <%= yield %> を記載して個別のテンプレートファイルのHTMLを表示する。