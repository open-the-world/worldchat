# API Image 作成

# ベースとなるイメージ
FROM golang:1.10.2-alpine3.7

# Gopkg.toml 等を事前にコピーして dep ensure が実行できるようにする
COPY src/api /go/src/api/

# dep ensure を行うプロジェクトルートに移動する
WORKDIR /go/src/api/

# 必要なパッケージをイメージにインストールする
RUN apk update \
  && apk add --no-cache git \
  && go get -u github.com/codegangsta/gin \
  && go get -u github.com/golang/dep/cmd/dep \
  && dep ensure

# コンテナ実行時のデフォルトを設定する
# ライブリロードを実行する
CMD gin -i run
