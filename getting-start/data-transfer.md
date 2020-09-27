---
description: 新しいマシンにJasperのデータを移行することができます。
---

# データ移行

## 1. 既存のデータを保存 <a id="export-data"></a>

古いマシンでJasperを起動して、`メニュー → Jasper → Export Data`を選択します。

![](../.gitbook/assets/04_export.png)

`Open data directory`をクリックして、ディレクトリを表示します。表示されたディレクトリ内にある`config.json`と`main.db`をデスクトップにコピーしてください。これらのデータをGoogle DriveやDropboxなどを使い、新しいマシンに移動してください。

{% hint style="info" %}
Jasperに複数アカウントを登録している場合、`main-123456789.db`のようなファイルもあるので、一緒にコピーしていただく必要があります。
{% endhint %}

## 2. 新しいマシンにデータを移行 <a id="import-data"></a>

新しいマシンでJasperを起動してください。最初の設定画面で`Import Data`を選択します。

![](../.gitbook/assets/03_import.png)

`Open data directory`をクリックして、ディレクトリを表示します。このディレクトリに先程移動してきた`config.json`と`main.db`をコピー\(上書き\)してください。最後に`Restart Jasper`をクリックすれば、データ移行は完了です。



