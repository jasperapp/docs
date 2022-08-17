---
description: Jasperをダウンロードして、GitHubのアクセストークンを設定するだけですぐに使用できます。
---

# セットアップ

## インストール <a href="#install" id="install"></a>

[jasperapp.io](https://jasperapp.io/) から最新のJasperをダウンロードし、zipファイルを展開してください。Jasperを起動すると、Mac/Windowsでは以下の確認が表示されます。説明に従い起動を完了してください。

{% tabs %}
{% tab title="Mac" %}
![](../.gitbook/assets/02\_mac.png)
{% endtab %}

{% tab title="Windows" %}
![](../.gitbook/assets/02\_windows1.png)

![](../.gitbook/assets/02\_windows2.png)
{% endtab %}
{% endtabs %}

## アクセストークンの設定 <a href="#access-token" id="access-token"></a>

Jasperを起動するとGitHub, GHE(GitHub Enterprise)の選択が表示されます。GHEの場合はホスト名`例 ghe.example.com`を入力してください。

つぎにアクセストークンの入力が必要になります。GitHubとGHEで設定方法が異なります。

{% tabs %}
{% tab title="GitHubの場合" %}
GitHubの場合はOAuthによるアクセストークンの設定を推奨します。画面の指示に従って、OAuth認証を実施してください。

![](<../.gitbook/assets/スクリーンショット 2022-08-17 12.11.07.png>)

もしくは[Personal access token](https://github.com/settings/tokens)からアクセストークンを作成して使用することもできます。必要なスコープは`repo`, `read:org`, `notifications`, `user`, `read:project` です。&#x20;

![](<../.gitbook/assets/スクリーンショット 2022-08-17 12.11.15.png>)
{% endtab %}

{% tab title="GHEの場合" %}
GHEの場合はPersonal access tokenを`https://GHEのホスト/settings/tokens`から作成してください。必要なスコープは`repo`, `read:org`, `notifications`, `user`, `read:project`です。&#x20;

![](<../.gitbook/assets/スクリーンショット 2022-08-17 12.12.24.png>)
{% endtab %}
{% endtabs %}

最後に設定内容を確認してOKを押してください。ユーザ名が表示されれば完了です🎉

![](<../.gitbook/assets/Screen Shot 2022-08-16 at 16.41.32.png>)

## 初回読み込み <a href="#initial-loading" id="initial-loading"></a>

設定が完了すると、自動的にissueの読み込みが開始されます。この初回の読み込みには数分ほどかかります。Jasperを終了せず、お使いください。

初回読み込み中に「[基本的な使い方](basic-usage.md)」をお読みいただくことで、Jasperをスムーズに使い始めることができます。
