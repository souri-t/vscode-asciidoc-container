# Asciidoc執筆環境

## 概要

このリポジトリはAsciidocを使用した文書作成のための執筆環境です。VS Code上で効率的に技術文書を作成・管理することができます。

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

## 環境構築

### 必要なツール

- VS Code
- Asciidoctor
- Draw.io Integration（画像編集用）

### VS Code拡張機能

以下の拡張機能をインストールすることをお勧めします：

- AsciiDoc
- Draw.io Integration
- Paste Image
- Code Spell Checker

## 使い方

1. `index.adoc`がメインドキュメントです。このファイルが他のコンポーネントファイルをインクルードしています。
2. 各セクションは`components/`フォルダにある個別のファイルに分割されています。
3. 図やダイアグラムは`images/`フォルダにDrawio形式で保存されています。

## ビルド方法

Asciidoctorを使用してHTMLやPDFに変換できます：

```bash
# HTMLに変換
asciidoctor document/index.adoc

# PDFに変換
asciidoctor-pdf document/index.adoc
```

## ファイル命名規則

- ドキュメントファイル：`NNN_name.adoc`（NNNは連番）
- 画像ファイル：対応するドキュメントと同じ番号を使用 `NNN_name.drawio.svg`
