# stan-d
Dockerfile for rstan on RStudio Server. Sorry, this repository is designed for Japanese only.

このDockerfileは,`rocker/tidyverse`をベースにし,`tokyor/rstudio`のDockerfileの記述をベースにして,以下のパッケージおよびそれらの依存パッケージを組み込んだものです。

- rstan
- rstanarm
- ggmcmc

必要に応じて,更新およびパッケージの見直しをしていきます。

## 導入方法

### Dockerの準備

まずはDockerが使えるようにしてください。Webで検索すれば,各プラットフォームでの導入方法が解説してあると思いますのでここでは省略します。

### Dockerイメージの導入

端末を開いて,以下のコマンドを実行してください:

```
$ docker pull kazutan/stan-d:latest
```

Ubuntuの場合,sudoが必要です。

ダウンロードが終了したら,以下のコマンドでイメージがちゃんと入ったか確認してください。

```
$ docker images
```

この中に`kazutan/stan-d`というイメージがあればOKです。

### Dockerコンテナの作成

端末を開いて,以下のコマンドを実行してください:

```
$ docker run -p 8787:8787 -v (リンクさせたいディレクトリパス):/home/rstudio -d --name (コンテナ名) kazutan/stan-d
```

Ubuntuの場合は`sudo`が必要です。

必要に応じてオプションなどは変更してください。例えば,手元PCのホームディレクトリとコンテナのホームディレクトリをリンクさせ,コンテナ名を"kosaki"にしたいなら,以下のような感じになります:

```
$ docker run -p 8787:8787 -v ~:/home/rstudio -d --name kosoaki kazutan/stan-d
```

現在起動しているコンテナを確認するため,以下のコマンドを実行してみます:

```
$ docker ps
```

なお,アクティブでないコンテナも含めて一覧を表示するには,以下のコマンドを実行してください:

```
$ docker ps -a
```

コマンドについては,以下を参考にしました:

https://gist.github.com/ongaeshi/a5609737489c46b863aa

細かいところは省略します。これでコンテナが作成され,バックエンドで起動します。つまり準備は整ったということです。

### RStudio Serverの起動

無事にコンテナが起動したら,ブラウザを起動させてURLのところに`localhost:8787`と入力してください。ログイン画面がでますので,ユーザー名を`rstudio`,パスワードを`rstudio`としてログインしてください。

あとは通常のRStudioと同様に使えますし,リンクさせたディレクトリが見えているはずです。

### Dockerコンテナの停止と再開

Dockerコンテナを停止するには,以下のコマンドを実行してください:

```
$ docker stop (コンテナ名)
```

Ubuntuの場合は`sudo`が必要です。

停止したDockerコンテナを再開するには,以下のコマンドを実行してください:

```
$ docker start (コンテナ名)
```

Ubuntuの場合は`sudo`が必要です。

### Dockerコンテナの削除

Dockerコンテナを削除するには,以下のコマンドを実行してください:

```
$ docker rm (コンテナ名)
```

Ubuntuの場合は`sudo`が必要です。

すぐにたまるので,残す必要がなければさっくと片付けた方がいいと思います。

## 注意点

- 割と頻繁に更新していく予定です
- 動作確認はUbuntu16.04上で行っています
- sorry, this repository made for Japanese.

## お願い

- なにかありましたら,issueにお願いします(日本語でOK)


