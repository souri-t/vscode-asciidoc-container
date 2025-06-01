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

# Install dependencies for Puppeteer/headless Chrome (for Mermaid CLI)
RUN apt-get update -y && apt-get install -y --no-install-recommends \
    ca-certificates \
    fonts-liberation \
    libasound2 \
    libatk-bridge2.0-0 \
    libatk1.0-0 \
    # libc6 is very likely already there from the base image \
    libcairo2 \
    libcups2 \
    libdbus-1-3 \
    libexpat1 \
    libfontconfig1 \
    libgbm1 \
    # libgcc1 is very likely already there \
    libglib2.0-0 \
    libgtk-3-0 \
    libnspr4 \
    libnss3 \
    libpango-1.0-0 \
    libpangocairo-1.0-0 \
    # libstdc++6 is very likely already there \
    libx11-6 \
    libx11-xcb1 \
    libxcb1 \
    libxcomposite1 \
    libxcursor1 \
    libxdamage1 \
    libxext6 \
    libxfixes3 \
    libxi6 \
    libxrandr2 \
    libxrender1 \
    libxss1 \
    libxtst6 \
    lsb-release \
    # wget is already installed earlier \
    xdg-utils \
    # End of Puppeteer dependencies

# PlantUMLのインストール
RUN curl -o /usr/local/bin/plantuml.jar http://sourceforge.net/projects/plantuml/files/plantuml.jar/download

# PlantUMLの実行環境を作成
RUN echo -e '#!/bin/bash\n\njava -jar /usr/local/bin/plantuml.jar "$@"' > /usr/local/bin/plantuml && \
    chmod +x /usr/local/bin/plantuml

# AsciidoctorとAsciidoctor-PlantUMLのインストール
RUN apt-get install ruby -y
RUN npm install -g @mermaid-js/mermaid-cli
RUN gem install asciidoctor asciidoctor-diagram asciidoctor-pdf asciidoctor-kroki
RUN gem install asciidoctor-diagram-plantuml

# 不要なパッケージを削除
RUN rm -rf /var/lib/apt/lists/*

# ワークディレクトリの作成
WORKDIR /workspace

# コンテナユーザーを設定
USER node