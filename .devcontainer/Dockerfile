# Node.jsの公式Debian系イメージを使用
FROM node:22-bookworm-slim

# 必要なパッケージをインストール
RUN apt-get update -y \
    && apt-get -y install --no-install-recommends \
        build-essential \
        git \
        curl \
        ca-certificates \
        apt-utils \
        dialog \
        zip \
        graphviz \
        openjdk-17-jre \
        unzip

# AsciidoctorとAsciidoctor-PlantUMLのインストール
RUN apt-get install ruby -y
RUN gem install asciidoctor asciidoctor-diagram asciidoctor-pdf

# 不要なパッケージを削除
RUN rm -rf /var/lib/apt/lists/*

# ワークディレクトリの作成
WORKDIR /workspace

# コンテナユーザーを設定
USER node