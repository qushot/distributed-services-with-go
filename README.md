[Go 言語による分散サービス](https://www.oreilly.co.jp/books/9784873119977/)のサンプルコード写経。

## メモ

「4 章 gRPC によるリクエスト処理」までの写経。

## 必要なツール等

※ 自分の環境は WSL2 の Ubuntu 22.04

```sh
$ cat /etc/os-release
PRETTY_NAME="Ubuntu 22.04.1 LTS"
NAME="Ubuntu"
VERSION_ID="22.04"
VERSION="22.04.1 LTS (Jammy Jellyfish)"
VERSION_CODENAME=jammy
ID=ubuntu
ID_LIKE=debian
HOME_URL="https://www.ubuntu.com/"
SUPPORT_URL="https://help.ubuntu.com/"
BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
UBUNTU_CODENAME=jammy
```

### Protocol Buffers コンパイラのインストール

```sh
$ wget https://github.com/protocolbuffers/protobuf/releases/download/v27.3/protoc-27.3-linux-x86_64.zip
$ unzip protoc-27.3-linux-x86_64.zip -d $HOME/.local/protobuf
$ export PATH=$PATH:$HOME/.local/protobuf/bin
```

### Protocol Buffers プラグインのインストール

```sh
# Go
$ go install google.golang.org/protobuf/cmd/protoc-gen-go@latest

# gRPC
$ go install google.golang.org/grpc/cmd/protoc-gen-go-grpc@v1.2.0
```

### Protocol Buffers のコンパイル

```sh
$ protoc api/v1/*.proto \
--go_out=. \
--go_opt=paths=source_relative \
--proto_path=.
```

### grpc パッケージのダウンロード

※ v.1.50.0 までのバージョンでないとコンパイルできない模様

```sh
$ go get google.golang.org/grpc@v1.50.0
```

## その他

正誤表: https://yoshikishibata.github.io/myhomepage/errata/distributed_services_in_go.html

70 頁：`grpcServerメソッド` は `grpcServer構造体` の誤りっぽい
