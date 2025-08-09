# Rustの公式イメージをベースにする
FROM rust:latest

# 必要なパッケージをインストール
RUN apt-get update && apt-get install -y \
    sudo \
    git \
    curl \
    && rm -rf /var/lib/apt/lists/*

# vscodeユーザーを作成
RUN groupadd --gid 1000 vscode \
    && useradd --uid 1000 --gid vscode --shell /bin/bash --create-home vscode \
    && echo 'vscode ALL=(ALL) NOPASSWD:ALL' >> /etc/sudoers.d/vscode \
    && chmod 0440 /etc/sudoers.d/vscode

# ユーザーをvscodeに切り替え
USER vscode

# Rustのパスを設定
ENV PATH="/home/vscode/.cargo/bin:${PATH}"

# mdBookをインストール
RUN cargo install mdbook \
    && cargo install mdbook-mermaid

# 作業ディレクトリを設定
WORKDIR /workspace
