---
description: A flexible and powerful issue reader for GitHub
---

# Jasperとは

![](.gitbook/assets/ss.png)

[Jasper](https://jasperapp.io/)はGitHubのissueやpull requestを柔軟な条件で閲覧できるツールです。例えば「自分が作成したpull request」「nodejs/nodeのbugラベルがついたissue」などの条件でissueを閲覧したり更新通知を受け取ることができます。

Jasperではこの機能を**Stream**と呼んでいます。Streamに次のようなクエリを設定することで前述した条件のissueを閲覧することができます。

```
author:defunkt is:pr
```

```
repo:nodejs/node label:bug is:issue
```

## Stream <a href="#stream" id="stream"></a>

Streamは[GitHub Search API](https://docs.github.com/en/rest/reference/search)を使って実現されています。GitHub Search APIは非常に強力なクエリを使うことができます。例えば次のようなクエリです。

| 条件                                                               | クエリ                                                                                  |
| ---------------------------------------------------------------- | ------------------------------------------------------------------------------------ |
| defunktが作成したissue                                                | [`author:defunkt is:issue`](https://github.com/search?q=author%3Adefunkt+is%3Aissue) |
| nodejs/nodeリポジトリのpull request                                    | [`repo:nodejs/node is:pr`](https://github.com/search?q=repo%3Anodejs%2Fnode+is%3Apr) |
| <p>nodejs organizationで</p><p>bugラベルがついているissue/pull request</p> | [`org:nodejs label:bug`](https://github.com/search?q=org%3Anodejs+label%3Abug)       |

そして、StreamはGitHub Search APIと全く同じクエリを使用することができるため、自分が関心のあるissueを柔軟に閲覧することができます。

![](.gitbook/assets/stream\_editor.png)

{% hint style="info" %}
Streamで使用できるクエリは「[Streamのクエリ](usecase/query.md)」や「[Stream](reference/stream.md)」を参照してください。
{% endhint %}

## 高い柔軟性 <a href="#flexible" id="flexible"></a>

現在、GitHubのissueを閲覧するツールはいくつか存在し、大きく3つのカテゴリにわかれます。

1. issueの閲覧や通知を管理するツール\
   [GitHub Notifications](https://github.com/notifications), [DevHub](https://devhubapp.com/), [Trailer](http://ptsochantaris.github.io/trailer/) など
2. チームコラボレーションをするツール\
   [GitHub Scheduled reminders](https://docs.github.com/en/github/setting-up-and-managing-organizations-and-teams/managing-scheduled-reminders-for-your-team), [Pull Panda](https://pullpanda.com/) など
3. プロジェクト管理をするツール\
   [GitHub Projects](https://docs.github.com/en/github/managing-your-work-on-github/managing-project-boards), [Zen Hub](https://www.zenhub.com/) など

Jasperは1のカテゴリに属するツールです。通常、このカテゴリのツールは[GitHub Notification API](https://docs.github.com/en/rest/reference/activity#notifications)を使っています。しかしJasperは[GitHub Search API](https://docs.github.com/en/rest/reference/search)を使って作られているため他のツールにはない高い柔軟性を実現しています。一方で簡単さについては他のツールより劣る場合があります。そのためJasperは「柔軟性」と「簡単さ」のバランスを考慮しながら開発されています。

{% hint style="info" %}
詳しくは「[コンセプト](faq.md#concept)」を参照してください。
{% endhint %}
