---
description: Just download Jasper and set up a GitHub access token and you're ready to go.
---

# Setup

## Install <a id="install"></a>

Download the latest version of Jasper from [jasperapp.io](https://jasperapp.io/) and extract the zip file. Follow the instructions to complete the launch.

{% tabs %}
{% tab title="Mac" %}
![](../.gitbook/assets/02_mac.png)
{% endtab %}

{% tab title="Windows" %}
![](../.gitbook/assets/02_windows1.png)

![](../.gitbook/assets/02_windows2.png)
{% endtab %}
{% endtabs %}

## Setting up an access token <a id="github"></a>

Jasperを起動するとGitHub, GHE\(GitHub Enterprise\)の選択が表示されます。GHEの場合はホスト名`例 ghe.example.com`を入力してください。

つぎにアクセストークンの入力が必要になります。GitHubの場合は[Personal access token](https://github.com/settings/tokens)の画面から作成できます。GHEの場合は管理者にお問い合わせください。必要なスコープは`repo`, `read:org`, `notifications`, `user`です。 

![](../.gitbook/assets/02_token.png)

最後に設定内容を確認してOKを押してください。ユーザ名が表示されれば完了です🎉

![](../.gitbook/assets/02_complete.png)

## 初回読み込み <a id="initial-loading"></a>

設定が完了すると、自動的にissueの読み込みが開始されます。この初回の読み込みには数分ほどかかります。Jasperを終了せず、お使いください。

初回読み込み中に「[基本的な使い方](basic-usage.md)」をお読みいただくことで、Jasperをスムーズに使い始めることができます。

