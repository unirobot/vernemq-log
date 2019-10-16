# Dockerfileを使ってpluginが起動と同時に有効になるコンテナを作る

コンテナ起動と同時にpluginが有効になるDockerfileを作成しました


vernemq-logにて以下のコマンドでビルド，起動を行う
```
sudo docker build -f vernemq_builder/Dockerfile -t vernemq_with_log_plugin .
sudo docker run -p 1883:1883 --name vernemq_container -d vernemq_with_log_plugin
```
コンテナにログインし，以下のコマンドでプラグインがvernemq_log_pluginが有効になっていれば成功です．
```
vmq-admin plugin show
```



### やったこと
vernemq.conf に以下の記述を追加しました  

plugins.vernemq_log_plugin=on  
plugins.vernemq_log_plugin.path=/vernemq/_build/default

vernemq_log_pluginをビルドしたファイルをコンテナ内に配置

Dockerfileはerlangをインストールしています
