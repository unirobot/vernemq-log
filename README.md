# verneMQ プラグインを作成しました
https://github.com/vernemq/vernemq_demo_plugin.git をもとに作成しています．

## 実行方法
dockerのイメージにログイン

#### 前準備
```
apt update
apt upgrade
apt install erlang
apt install git
```



/verneMQにて以下を実行
```
git clone https://gitlab.unibo.info/unirobot/vernemq-log.git
cd vernemq-log
git clone https://github.com/vernemq/vernemq_demo_plugin.git
cp -r src vernemq-log/src
cd vernemq_demo_plugin
./rebar3 compile
```


pluginを有効化する
```
vmq-admin plugin enable -n vernemq_demo_plugin -p vernemq-log/vernemq_demo_plugin/_build/default
```

以上を行った後にclientフォルダにあるようなプログラムでpublishやsubscribeを行うとlogがdockerのログに出ます

