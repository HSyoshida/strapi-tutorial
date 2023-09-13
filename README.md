
# 環境構築

## 最新版Ubuntuでコンテナ作成

```
docker run -it --rm --pull always ubuntu
```

## 日本語化

```
apt-get update
apt-get install -y language-pack-ja-base language-pack-ja locales
locale-gen ja_JP.UTF-8
echo "export LANG=ja_JP.UTF-8" >> ~/.bashrc
source ~/.bashrc
```

## Node.js

### Node.jsと必要なpackageをインストール

```
apt install sudo -y
sudo apt install -y nodejs npm
sudo apt install -y curl
npm install -g n
```

### Node.js安定版のバージョン確認

```
n --stable
```

### Node.js安定版をインストール

```
n stable
```

### バージョン切り替え

```
n
```

### 再ログイン

```
exec $SHELL -l
```

### Node.jsのバージョン確認

```
node -v
```

### npmのアップデート

```
npm update -g npm
```

## yarnを使えるようにする

### corepackを有効化

```
sudo corepack enable
```

### yarn安定版をインストール

```
yarn set version stable
```

### yarnのバージョン確認

```
yarn -v
```

## Strapiのインストール

### 作業用ディレクトリ作成

```
mkdir -p /projects/strapi && cd $_
```

### Strapiをインストール(エラーが出る)

```
yarn create strapi-app my-project --quickstart
```

### 空の yarn.lock ファイルを作成

```
touch /projects/strapi/my-project/yarn.lock
```

### プロジェクトファイルに移動

```
cd /projects/strapi/my-project/
```

### 依存ファイルをインストール

```
yarn install
```

# Strapiの実行

## アプリケーションの実行

### プロジェクトファイルに移動(別階層にいる場合)

```
cd /projects/strapi/my-project/
```

### Strapi起動(開発サーバ)

```
yarn develop
```

## コンテナの作業を保存・再開

### dockerfile作成

Dockerログイン中のプロセスとは別プロセスになっていること

```
docker ps
docker commit <上記コマンドで取得したID> strapi
docker save strapi -o strapi-tutorial
```

## Dockerfileからコンテナを作成・起動

<http://localhost:1337/admin> にアクセスできるように起動

```
docker run -it -p 1337:1337 --name strapi-tutorial strapi /bin/bash
```

### コンテナ作成済の場合は起動してログイン

```
docker start strapi-tutorial
docker exec -it strapi-tutorial /bin/bash
```

### ログアウト

```
exit
```

### コンテナを停止
```
docker stop strapi-tutorial
```

# 参考サイト

## Docker

* [Docker Docs](https://matsuand.github.io/docs.docker.jp.onthefly/)

## Strapi公式

* [Quick Start Guide](https://docs.strapi.io/dev-docs/quick-start)
* [REST API](https://docs.strapi.io/dev-docs/api/rest)
* [Managing API tokens](https://docs.strapi.io/user-docs/settings/API-tokens)

## HTML

* [Document.createDocumentFragment()](https://developer.mozilla.org/ja/docs/Web/API/Document/createDocumentFragment)
* [template: コンテンツテンプレート要素](https://developer.mozilla.org/ja/docs/Web/HTML/Element/template)
* [フェッチ API の使用](https://developer.mozilla.org/ja/docs/Web/API/Fetch_API/Using_Fetch)
* [Marked.js](https://github.com/markedjs/marked)
