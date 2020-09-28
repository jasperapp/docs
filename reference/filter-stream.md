---
description: This is a reference for the filters available in Filter Stream.
---

# Filter Stream

Filter Stream filters the Stream's issues and displays them.

Filter Streams are added from the `Add Filter Stream` menu in the Stream menu. Or, to create a top-level stream, add it from the `Add Filter Stream top-level` menu. It is also possible to apply a Filter temporarily.

{% tabs %}
{% tab title="Add Filter Stream" %}
![](../.gitbook/assets/10_filter_stream1.png)
{% endtab %}

{% tab title="Filter Stream setting" %}
![](../.gitbook/assets/10_filter_stream2.png)
{% endtab %}

{% tab title="Add Top Level Filter Stream" %}
![](../.gitbook/assets/10_filter_stream3.png)
{% endtab %}

{% tab title="Temporarily" %}
![](../.gitbook/assets/10_filter_stream4.png)
{% endtab %}
{% endtabs %}

{% hint style="info" %}
The filters available in the Filter Stream are pretty much the same as in the Stream, but note that some of them are slightly different.
{% endhint %}

## State of issues

| Filter | Condition |
| :--- | :--- |
| `is:issue`, `is:pr` | Issues only, pull requests only |
| `is:open`, `is:closed` | Opened issues, closed issues |
| `is:merged`, `is:unmerged` | Merged issues, unmerged issues |
| `draft:true`, `draft:false` | Draft issues, not draft issue‌s |
| `is:read`, `is:unread` | Read issues, unread issues |
| `is:bookmark`, `is:unbookmark` | Bookmarked issues, not bookmarked issue |
| `is:archived`, `is:unarchived` | Archived issues, not archived issues |
| `is:private`, `is:unprivate` | Private repository issues, not private repository issues |

## Involve users and teams <a id="involves-filter"></a>

| Filter | Condition |
| :--- | :--- |
| `involves:defunkt` | User involved issues |
| `author:defunkt` | User created issues |
| `assignee:defunkt` | User assigned issues |

{% hint style="info" %}
Multiple filters of the same type can be specified as OR conditions. For example, `involves:defunkt involves:jlord` is issues involving `defunkt` or `jlord`.
{% endhint %}

{% hint style="info" %}
`involves` as well as `author`, `assignee`, `commenter` and `review-requested` all together.‌
{% endhint %}

## Pull requests review <a id="review-filter"></a>

| Filter | Condition |
| :--- | :--- |
| `review-requested:defunkt` | Pull requests where the user/team has requested a review |
| `reviewed-by:defunkt` | User reviewed pull requests |

{% hint style="info" %}
Specifying multiple queries of the same type is an OR condition. For example, `review-requested:defunkt review-requested:jlord` is pull requests where `defunkt` or `jlord` is the review request.
{% endhint %}

## Repository and Organization <a id="repo-filter"></a>

| Filter | Condition |
| :--- | :--- |
| `repo:nodejs/node` | Repository issues |
| `org:nodejs` | Organization issues |
| `user:defunkt` | User issues |

{% hint style="info" %}
Specifying multiple queries of the same type is an OR condition. For example, `repo:nodejs/node repo:electron/electron` is issues of `nodejs/node` or `electron/electron`.
{% endhint %}

## Label, milestone, etc <a id="label-filter"></a>

| Filter | Condition |
| :--- | :--- |
| `label:bug` | Labeled issues |
| `milestone:v1.0.0` | Milestone issues |
| `project-name:hello-pj` | Project issues |
| `project-column:now-doing` | Project column issues |
| `number:123` | Issue number |

{% hint style="info" %}
Specifying multiple queries of the same type is an OR condition. For example, `milestone:v1.0.0.0 milestone:v2.0.0` is issues with a `v1.0.0` or `v2.0.0.0` milestone. However, this is an AND condition for labels.
{% endhint %}

{% hint style="info" %}
スペースを含むラベルやマイルストーンの場合は`label:"`hello `world"`のようにダブルクオーテーションで囲んでください。‌
{% endhint %}

## 任意のキーワード <a id="keyword-filter"></a>

| フィルター | 条件 |
| :--- | :--- |
| `github octocat` | キーワード\(AND条件\)が含まれるissue |

{% hint style="info" %}
スペースを含む場合は`"hello world"`のようにダブルクオーテーションで囲んでください。
{% endhint %}

{% hint style="info" %}
キーワードはissue本文, author, assignee, label, milestone, repository, org, involves, review-requested, review, project-name, project-columnsを対象とします。
{% endhint %}

{% hint style="warning" %}
OR, NOTには対応していません。
{% endhint %}

## 除外・欠如 <a id="exclude-filter"></a>

| フィルター | 条件 |
| :--- | :--- |
| `-label:bug`, `-milestone:v0.0.1`, `-repo:nodejs/node` `-involves:defunk`... | 指定した条件が含まれないissue |
| `no:label`, `no:milestone`, `no:assignee`, `no:project`, `no:dueon` | ラベル、マイルストーン、アサイン、 プロジェクト、締切が設定されていないissue |
| `have:label`, `have:milestone`, `have:assignee`, `have:project`, `have:dueon` | ラベル、マイルストーン、アサイン、 プロジェクト、締切が設定されているissue |

