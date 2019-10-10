# verneMQ プラグインを作成しました
https://github.com/vernemq/vernemq_demo_plugin.git をもとに作成しています．

## 実行方法



dockerのコンテナを作成する(以下コンテナ名はvernemq_testとします)
```
sudo docker run -p 1883:1883 --name vernemq_test -d erlio/docker-vernemq

```

dockerのイメージにログイン
```
sudo docker exec -it --user root vernemq_test /bin/bash
```

#### 前準備
```
apt update
apt upgrade
apt install erlang
apt install git
apt install vim
```

匿名ログインを有効にします
```
vim etc/vernemq.conf
```
allow_anonymous=offを
allow_anonymous=onに書き換えます

ここで設定を更新するためサーバーを再起動します
```
vernemq restart
sudo docker start vernemq_test
sudo docker exec -it --user root vernemq_test /bin/bash
```



/vernemqにて以下を実行
```
git clone https://gitlab.unibo.info/unirobot/vernemq-log.git
cd vernemq-log
cd vernemq_log_plugin
./rebar3 compile
```


pluginを有効化する
```
vmq-admin plugin enable -n vernemq_log_plugin -p vernemq-log/vernemq_log_plugin/_build/default
```



以上を行った後にpublishやsubscribeを行うとログが出ます。

コンテナからログアウトし、

```
git clone https://gitlab.unibo.info/unirobot/vernemq-log.git
pip3 install paho-mqtt
cd vernemq-log/client_test

```

その後
```
python3 recv.py
```
```
python3 send.py
```
にてそれぞれsubscribe,publishが行えます。

成功していれば以下のコマンドでログが確認できます
```
sudo docker logs vernemq_test
```
