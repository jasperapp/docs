---
description: issueの並び順についてのリファレンスです。
---

# 並び順

通常、issueは更新順で表示されています。issue一覧の上部にある並び順アイコンから並び順を変更することができます。また、Filter StreamやFilterに`sort:ORDER`を指定することで並び順を変更することもできます。

{% tabs %}
{% tab title="並び順の変更" %}
![](../.gitbook/assets/14_sort_menu.png)
{% endtab %}

{% tab title="Filterにsort:ORDERを指定" %}
![](../.gitbook/assets/14_sort_filter.png)
{% endtab %}
{% endtabs %}

`sort:ORDER`には次の値を指定できます。

| sort | 説明 |
| :--- | :--- |
| `sort:updated` | 更新順 |
| `sort:created` | 作成順 |
| `sort:closed` | クローズ順 |
| `sort:merged` | マージ順 |
| `sort:read` | 閲覧順 |
| `sort:archived` | アーカイブされた順 |
| `sort:bookmark` | ブックマークされた順 |
| `sort:author` | 作者名順 |
| `sort:user` | ユーザ名、organization名順 |
| `sort:repo` | リポジトリ名順 |
| `sort:milestone` | マイルストーン名順 |
| `sort:dueon` | マイルストーンに設定されている締切日順 |
| `sort:title` | タイトル順 |
| `sort:number` | issueの番号順 |
| `sort:type` | issueの種類（Issue or Pull Request） |

複数の並び順、昇順/降順を指定することもできます。

```text
sort:"updated desc, author asc"
```

