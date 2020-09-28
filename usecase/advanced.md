---
description: GitHubとの高度な連携や、Streamの更新間隔を最適化する方法を紹介します。
---

# 高度な設定

## スマートフォンと連携 <a id="mobile"></a>

スマートフォンや通常のブラウザで閲覧したissueを、Jasperでも既読にするためにはGitHub Notification Syncを有効にします。

![](../.gitbook/assets/07_notification_sync.png)

この設定を有効にすると定期的\(通常は60秒間隔\)に[GitHub Notification](https://github.com/notifications)からJasper側に反映させます。

{% hint style="warning" %}
JasperからGitHub Notificationへの反映は「issueを閲覧して既読にした」場合のみ行われます。次の操作はGitHub Notificationへは反映されません。

* Jasperで未読にしたissue
* Jasperでメニューやキーボードショートカットにより既読にしたissue
{% endhint %}

## GitHub Projectsと連携 <a id="project"></a>

特定のGithub Projectsに関連するissueを見るにはProject Streamを作成します。

{% tabs %}
{% tab title="Project Streamの作成" %}
![](../.gitbook/assets/07_project_stream1.png)
{% endtab %}

{% tab title="Project Streamの表示" %}
![](../.gitbook/assets/07_project_stream2.png)
{% endtab %}
{% endtabs %}

{% hint style="info" %}
`project:REPOSITORY/PROJECT_BOARD`クエリを使い、通常のStreamを作成しGitHub Projects に関連するissueを見ることはできます。しかしProject Streamを使うことでProject Board\(カンバン\)との連携が可能になるので、Project Streamを使うことをおすすめします。
{% endhint %}

## GitHub Teamと連携 <a id="team"></a>

自分が所属するGitHub Teamへメンションされたissueを見るにはTeam Streamを使います。Team Streamは設定画面から有効にします。

{% tabs %}
{% tab title="Team Streamの有効にする" %}
![](../.gitbook/assets/07_team_stream1.png)
{% endtab %}

{% tab title="Team Stream" %}
![](../.gitbook/assets/07_team_stream3.png)
{% endtab %}

{% tab title="Team Streamの内容" %}
自分が所属するTeamからクエリが自動的に作成されます。

![](../.gitbook/assets/07_team_stream2%20%281%29.png)
{% endtab %}
{% endtabs %}



## GitHub Watchingと連携する <a id="watching"></a>

自分がGitHub上でwatchしたリポジトリのissueを見るにはWatching Streamを使います。Watching Streamは設定画面から有効にします。

{% tabs %}
{% tab title="Watching Streamの有効にする" %}
![](../.gitbook/assets/07_watchiing_stream1.png)
{% endtab %}

{% tab title="Watching Stream" %}
![](../.gitbook/assets/07_watching_stream2.png)
{% endtab %}

{% tab title="Watching Streamの内容" %}
自分がwatchするリポジトリからクエリが自動的に作成されます。

![](../.gitbook/assets/07_watching_stream3.png)
{% endtab %}
{% endtabs %}

## 任意のissueを登録する <a id="subscription"></a>

リポジトリやorganizationではなく、issue単独でStreamにしたい場合はSubscription Streamを使います。Subscription Streamは設定画面から有効にします。

{% tabs %}
{% tab title="Subscription Streamを有効にする" %}
![](../.gitbook/assets/07_subscription_stream1.png)
{% endtab %}

{% tab title="Subscription Stream" %}
![](../.gitbook/assets/07_subscription_stream2.png)
{% endtab %}

{% tab title="issueを登録する" %}
Subscription Streamを右クリックして、メニューからissueのURLを登録します。

![](../.gitbook/assets/07_subscription_stream3.png)
{% endtab %}
{% endtabs %}

## 更新間隔を最適化する <a id="polling"></a>

Jasperは通常10秒ごとにissueを検索して更新を取得しています。この更新間隔はStreamごとではなく、Jasper全体の更新間隔です。つまり、Streamをたくさん作れば作るほど、Stream1個あたりの更新は遅くなります。例えばStreamを3つ作っていた場合、1つのStreamが更新されるのは30秒ごとになります。

{% hint style="info" %}
このような動作になっているのは、Streamが増えてもGitHub側に負荷をかけないようにするためです。
{% endhint %}

このため、たくさんStreamを作ると更新が遅くなってしまいます。そこで、通常のStreamを少なくしてFilter Streamを積極的に使うことで、更新が遅くならないようにします。

{% hint style="info" %}
Filter StreamはGitHubの検索を行わず、ローカルのissueをフィルターするため更新間隔に影響を与えません。Filter Streamについての詳細は「[Filter Stream](../reference/filter-stream.md)」を参照してください。
{% endhint %}

例えば次のような2つのStreamを作るのではなく、1つのStreamと2つのFilter Streamを作ります。こうすることで前者では1つのStreamあたり20秒間隔の更新だったものが、後者では1つのStreamあたり10秒間隔になります。

{% tabs %}
{% tab title="2つのStream" %}
```text
org:nodejs
```

```text
org:electron
```

![](../.gitbook/assets/07_optimize_interval1.png)
{% endtab %}

{% tab title="1つのStreamと2つのFilter Stream" %}
```text
org:nodejs org:electron
```

```text
org:nodejs
```

```text
org:electron
```

![](../.gitbook/assets/07_optimize_interval2.png)
{% endtab %}
{% endtabs %}

JasperではこのようにFilter Streamを積極的に利用することを推奨しています。

