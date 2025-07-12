# ドキュメント生成ツール

## 概要
このツールはAsciidoctorを使用してドキュメントをHTML形式に変換します。  
CSSスタイルシートに基づいた文書レイアウトを実現するためPDF形式ではなくHTML形式で出力します。
最終的にPDFに変換したい場合はブラウザでHTMLを開いた後、ブラウザの機能でPDFに変換することを勧めます。

## 使い方

### HTMLドキュメントの生成
以下のコマンドを実行して、Asciidoctorドキュメントを変換します。
```
asciidoctor -a stylesheet=style.css -r asciidoctor-diagram -o ./output/index.html ./document/index.adoc
```

解説：
- `-a stylesheet=style.css`: カスタムCSSスタイルシートを適用します
- `-r asciidoctor-diagram`: 図表をサポートするプラグインを読み込みます
- `-o ./output/index.html`: 出力先のHTMLファイルを指定します
- `./document/index.adoc`: 入力となるAsciidoctorソースファイルです

### 出力結果のアーカイブ作成
変換したファイルをZIPアーカイブに保存するには以下のコマンドを実行します：
```
mkdir -p ./archive && zip -r ./archive/output.zip ./output/
```

解説：
1. `mkdir -p ./archive`: アーカイブディレクトリを作成します（存在しない場合）
2. `zip -r ./archive/output.zip ./output/`: outputディレクトリの内容をZIPアーカイブに圧縮します
