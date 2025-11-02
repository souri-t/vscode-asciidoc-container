---
mode: agent
---

User input:

${fileDirname}

# 依頼事項
入力されたフォルダ名のソースコードを解析し、外部設計書を作成してください。各セクションに必要な情報を具体的に記載し、システムの全体像と外部設計が明確になるようにしてください。

# 記載ルール
- 出力フォーマットはAsciiDoc（.adoc）とすること。
- 文章は日本語で記載すること。
- セクション構成は #file:external-design-specification.md に従うこと。
- 図表を記載する場合はplantumlを使用すること。
- 属性設定は 以下で指定されているものをそのまま使うこと。

# 適用する属性設定
:doctype: article
:lang: ja
:toc: left
:toclevels: 3
:toc-title: 目次
:sectnums:
:sectnumlevels: 6
:sectlinks:
:sectanchors:
:source-highlighter: rouge
:icons: font
:experimental:
:stem:
:imagesdir: images
:pdf-theme: theme/document-theme.yml
:pdf-fontsdir: theme/fonts
:title-page:
:revdate: {docdate}
:revnumber: 1.0
:author: システム開発株式会社