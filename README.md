# Asciidoc執筆環境

## 概要

Asciidocの執筆環境を提供するVSCodeのDevContainersです。  
必要なツールや設定が整った統一的なコンテナを簡単に構築できます。

## ディレクトリ構成

```
workspace/
  README.md          # 本ファイル
  document/          # 文書格納フォルダ
    index.adoc       # メインドキュメント
    style.css        # スタイルシート
    components/      # 文書コンポーネント
      100_background.adoc  # 背景
      200_architecture.adoc # アーキテクチャ
      300_function.adoc    # 機能説明
      400_screen.adoc      # 画面説明
      410_main.adoc        # メイン画面
      500_glossary.adoc    # 用語集
    images/          # 画像ファイル
      210_hardware.drawio.svg  # ハードウェア構成図
      220_software.drawio.svg  # ソフトウェア構成図
      410_main.drawio.svg      # メイン画面図
```

## コンテナ環境

### 執筆環境

このコンテナでは以下の執筆環境が提供されます：

#### Asciidoc
- **Asciidoctor** - Asciidocファイルを処理するための機能
- **Asciidoctor-PDF** - AsciidocからPDFを生成する機能
- **Asciidoctor-Diagram** - 図表生成拡張機能

#### PlantUML
- **PlantUML** - 外部サーバーを使用せず、コンテナ内でPlantUML図表を生成する環境
- **Java 17(OpenJDK)** - PlantUML生成に必要なJava実行環境
- **Graphviz** - PlantUMLの図表レンダリングに必要なライブラリ

PlantUMLで作成した図表はすべてコンテナ内で処理されるため、インターネット接続やセキュリティ上の懸念なく安全に利用できます。

### VSCode拡張機能

コンテナでは以下の拡張機能がインストールされます。

- **asciidoctor.asciidoctor-vscode** - Asciidocファイルの編集とプレビュー機能
- **streetsidesoftware.code-spell-checker** - スペルチェック機能
- **mushan.vscode-paste-image** - 画像の貼り付け機能
- **hediet.vscode-drawio** - Draw.io図表の編集機能

## 使い方

### Dev Containerの使い方

1. VSCodeでこのディレクトリを開きます。
2. 画面左下の「Reopen in Container」または「Dev Containerで再度開く」をクリックします。
3. 自動的に必要な環境がセットアップされ、Asciidocの執筆やプレビューが可能になります。[（コンテナ移動後の使い方）](./workspace/README.md) 
