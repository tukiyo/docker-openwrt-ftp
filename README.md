# 起動方法

```
git clone https://github.com/tukiyo/docker-openwrt-ftp.git
cd docker-openwrt-ftp
```

```ruby:docker-compose.yml
  environment:
    #- HOST=my.server.com
    - HOST=localhost
    #- HOST=192.168.100.70
```

* (PASVのため) 自サーバ以外から接続する場合
    * `HOST`の値をIPアドレスか、名前解決が出きるホスト名を指定


```bash:
docker-compose up -d
```

# docker-openwrt-ftp

* [mcreations/ftp](https://hub.docker.com/r/mcreations/ftp/)を改良
* 複数アカウント作成に対応
* HOMEディレクトリを他のユーザと同じPATHを指定可能
* (chrootにより)所有者がUIDで表示されていたのでUsername表示の対応
* timezoneの初期値をJST-9(つまり日本)に設定。

![ftp.png](https://qiita-image-store.s3.amazonaws.com/0/25728/ce43ba7f-dbbb-004a-0754-ce2473e6cdbb.png)


## アカウント設定

* image/root/users.txt

```
user1   pass1
user2   pass2
user3   pass    share
user4   pass    share
user5   pass    share
```

* 1行目: FTPのユーザ名
* 2行目: FTPのパスワード
* 3行目: ログインするPATHを`/data/share/`に指定。
    * user3, user4, user5は`/data/share/`を利用。
    * user1は/data/user1/
    * user2は/data/user2/を利用。
