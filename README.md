# docker-openwrt-ftp

* [mcreations/ftp](https://hub.docker.com/r/mcreations/ftp/)を改良
* 複数アカウント作成に対応
* HOMEディレクトリを他のユーザと同じPATHを指定可能

## ホスト名設定

* docker-compose.yml

```
  environment:
    #- HOST=my.server.com
    - HOST=localhost
    #- HOST=192.168.10.7
```

* PASVのため、自サーバ以外から接続する場合
    * `HOST`の値をIPアドレスか
    * 名前解決が出きるホスト名を指定する必要があります

## アカウント設定

* image/root/users.txt

```
user1   pass1
user2   pass2
user3   pass    share
user4   pass    share
user5   pass    share
```

3番目の内容`share`はPATHを`/data/share/`でログイン。
user3, user4, user5は`/data/share/`を利用。

## 起動方法

```
docker-compose up -d
```
