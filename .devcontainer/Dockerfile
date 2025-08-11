# Rustの公式イメージをベースにする
FROM rust:latest

ENV TZ=Asia/Tokyo

# 必要なパッケージをインストール
RUN apt-get update && apt-get install -y \
    sudo \
    git \
    curl \
    locales \
    && rm -rf /var/lib/apt/lists/*

# GitHub CLIのインストール
RUN curl -fsSL https://cli.github.com/packages/githubcli-archive-keyring.gpg | dd of=/usr/share/keyrings/githubcli-archive-keyring.gpg \
    && chmod go+r /usr/share/keyrings/githubcli-archive-keyring.gpg \
    && echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/githubcli-archive-keyring.gpg] https://cli.github.com/packages stable main" > /etc/apt/sources.list.d/github-cli.list \
    && apt-get update \
    && apt-get install -y gh

# vscodeユーザーを作成
RUN groupadd --gid 1000 vscode \
    && useradd --uid 1000 --gid vscode --shell /bin/bash --create-home vscode \
    && echo 'vscode ALL=(ALL) NOPASSWD:ALL' >> /etc/sudoers.d/vscode \
    && chmod 0440 /etc/sudoers.d/vscode

# 日本語環境の設定（rootユーザーで実行）
ENV LANG ja_JP.UTF-8
ENV LC_ALL ja_JP.UTF-8
RUN sed -i '$d' /etc/locale.gen \
    && echo "ja_JP.UTF-8 UTF-8" >> /etc/locale.gen \
    && locale-gen ja_JP.UTF-8 \
    && /usr/sbin/update-locale LANG=ja_JP.UTF-8 LANGUAGE="ja_JP:ja"
RUN ln -sf /usr/share/zoneinfo/Asia/Tokyo /etc/localtime

# ユーザーをvscodeに切り替え
USER vscode

# Rustのパスを設定
ENV PATH="/home/vscode/.cargo/bin:${PATH}"

# mdBookをインストール
RUN cargo install mdbook \
    && cargo install mdbook-mermaid

# 作業ディレクトリを設定
WORKDIR /workspace
