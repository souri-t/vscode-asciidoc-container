
# AsciiDocドキュメント生成ツール

## 概要
このワークスペースは、AsciiDoc形式のドキュメントを効率的に作成・管理し、HTMLおよびPDF形式で出力するためのツール群を提供します。
ソースコードから外部設計書を自動生成するプロンプトも含まれています。

## 特徴
- AsciiDoc記法による高品質なドキュメント作成
- PlantUMLによる図表生成対応
- HTML・PDF両形式への出力
- テーマや画像ディレクトリのカスタマイズ対応

## ドキュメントファイル生成コマンド

### HTML形式で生成
```
asciidoctor -b html5 -r asciidoctor-diagram sample.adoc
```

### PDF形式で生成
```
asciidoctor-pdf -r asciidoctor-diagram sample.adoc
```

## 仕様書生成プロンプトについて

本ワークスペースには、指定したフォルダ内のソースコードを解析し、外部設計書を自動生成するプロンプトが含まれています。

### プロンプトの使い方

1. Copilotのチャットにて以下のコマンドを入力すると、プロンプトがソースコードを解析し、外部設計書をAsciiDoc形式で生成します。

```command
/write-ed-spec [ドキュメント生成したいアプリのフォルダ名]
```
