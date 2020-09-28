---
description: System Streamのリファレンスです。
---

# System Stream

System Streamとは動的にクエリを生成するシステム組み込みのストリームです。System Streamを使用する場合は`メニュー → Preferences → Streams`から有効にしてください。

![](../.gitbook/assets/13_system_stream.png)

| System Stream | 説明 |
| :--- | :--- |
| `Team Stream` | 自身がGitHub上で所属するチームがメンションされたissue |
| `Watching Stream` | 自身がGitHub上でwatchしているリポジトリのissue |
| `Subscription Issue` | 個別に指定されたissue |

`Team Stream`は自身がGitHub上で所属するチームを取得して、そのチームがメンションされたissueを扱うことができます。新しくチームに所属した場合、自動的にチームが追加されます。

`Watching Stream`は自身がGitHub上でwatchしたリポジトリを取得して、そのリポジトリのissueを扱うことができます。新しくリポジトリをwatchした場合、自動的にリポジトリが追加されます。

`Subscription Stream`は個別に指定されたissueを扱うことができます。Subscription StreamのメニューからissueのURLを登録してください。

