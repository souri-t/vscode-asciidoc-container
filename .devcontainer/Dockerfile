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
        unzip \
        default-jre \ 
        fonts-ipafont

# PlantUMLのインストール
RUN curl -o /usr/local/bin/plantuml.jar http://sourceforge.net/projects/plantuml/files/plantuml.jar/download

# PlantUMLの実行環境を作成
RUN echo -e '#!/bin/bash\n\njava -jar /usr/local/bin/plantuml.jar "$@"' > /usr/local/bin/plantuml && \
    chmod +x /usr/local/bin/plantuml

# AsciidoctorとAsciidoctor-PlantUMLのインストール
RUN apt-get install ruby -y
RUN gem install asciidoctor asciidoctor-diagram asciidoctor-pdf
RUN gem install asciidoctor-diagram-plantuml

# 不要なパッケージを削除
RUN rm -rf /var/lib/apt/lists/*

# ワークディレクトリの作成
WORKDIR /workspace

# コンテナユーザーを設定
USER node