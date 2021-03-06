# TweetCommand

標準入力につぶやく内容を与えると,Twitterにその内容を投稿するスクリプト  

# 環境
macOS, Ubuntu, CentOSなど，シェルが使えるOS
Go言語で記述されているので，Windowsでもコンパイルしてやれば動くはず(未確認)

macOS Sierra 10.12.5, Ubuntu 16.04で動作確認済み

## 準備

### ダウンロードとコンパイル
必要があればコンパイルする  

```
# ダウンロード
$ git clone http://github.com/CoffeeTaro/TweetCommand
Cloning into 'TweetCommand'...
remote: Counting objects: 12, done.
remote: Compressing objects: 100% (7/7), done.
remote: Total 12 (delta 2), reused 12 (delta 2), pack-reused 0
Unpacking objects: 100% (12/12), done.
Checking connectivity... done.
$ ls
TweetCommand
$ cd TweetCommand/
$ ls
README.md  main.go  tweet-macOS
$ go version
go version go1.8.1 linux/amd64
# コンパイル: tweet-ubuntuというファイル名でコンパイル
$ go build -o tweet-ubuntu
$ ls
README.md  main.go  tweet-macOS  tweet-ubuntu
```

### 環境変数の設定
.bashrcまたは.bash_profileに下記を記述  
.bash_profileに書くことを推奨  

```
# Twitter API Keys
export TWITTER_CONSUMER_KEY="your_twiter_consumer_key"
export TWITTER_CONSUMER_SECRET="your_consumer_secret"
export TWITTER_ACCESS_TOKEN_KEY="your_access_token_key"
export TWITTER_ACCESS_TOKEN_SECRET="your_access_token_secret"
# Twitter Screen Name
export TWITTER_SCREEN_NAME="your_screen_name"
```

Cronなどで，指定した時刻にTweetコマンドを実行したい場合は/etc/environmentに下記のように記述してもいいでしょう

```
# Twitter API Keys
TWITTER_CONSUMER_KEY="your_twiter_consumer_key 
TWITTER_CONSUMER_SECRET="your_consumer_secret"
TWITTER_ACCESS_TOKEN_KEY="your_access_token_key"
TWITTER_ACCESS_TOKEN_SECRET="your_access_token_secret"
# Twitter Screen Name
TWITTER_SCREEN_NAME="your_screen_name"
```


### コマンドの追加

Pathの通ったディレクトリに実行ファイルをコピーする  

例えば，  

```
cp tweet /usr/local/bin/
```
のようにする．  

### 確認

```
$ which tweet
/usr/local/bin/tweet
```
のように実行ファイルを入れたディレクトリが表示されれば，準備完了

## 実行例

```
$ echo hoge | tweet
```

