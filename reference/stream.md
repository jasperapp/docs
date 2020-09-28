---
description: A query reference that can be used for Stream.
---

# Stream

Streams can be added from the `Add Stream` menu.

{% tabs %}
{% tab title="Add Stream" %}
![](../.gitbook/assets/09_add_stream1.png)
{% endtab %}

{% tab title="Stream setting" %}
![](../.gitbook/assets/09_add_stream2.png)
{% endtab %}
{% endtabs %}

{% hint style="info" %}
Streamに使用できるクエリはGitHub Searchのクエリと完全に互換性があります。  
See "[Searching issues and pull requests - github.com](https://docs.github.com/en/free-pro-team@latest/github/searching-for-information-on-github/searching-issues-and-pull-requests)"and "[Understanding the search syntax - github.com](https://docs.github.com/en/free-pro-team@latest/github/searching-for-information-on-github/understanding-the-search-syntax)" for all GitHub Search queries and syntax.
{% endhint %}

## Specify the state of an issue

<table>
  <thead>
    <tr>
      <th style="text-align:left">Query</th>
      <th style="text-align:left">Condition</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><code>is:issue</code>, <code>is:pr</code>
      </td>
      <td style="text-align:left">Issue only, pull request only</td>
    </tr>
    <tr>
      <td style="text-align:left">
        <p><code>is:open</code>, <code>is:closed</code>
        </p>
        <p><em>not recommended</em>
        </p>
      </td>
      <td style="text-align:left">Open issues, closed issues</td>
    </tr>
    <tr>
      <td style="text-align:left">
        <p><code>is:merged</code>, <code>is:unmerged</code>
        </p>
        <p><em>not recommended</em>
        </p>
      </td>
      <td style="text-align:left">Merged issues, unmerged issues</td>
    </tr>
    <tr>
      <td style="text-align:left">
        <p><code>draft:true</code>, <code>draft:false</code>
        </p>
        <p><em>not recommended</em>
        </p>
      </td>
      <td style="text-align:left">Draft issues&#x3001;not draft issues</td>
    </tr>
  </tbody>
</table>

{% hint style="warning" %}
Open, merge and draft state queries are not recommended. If you use these queries, use Filter Stream. See [here](../usecase/stream-query.md#open-issue) for more information.
{% endhint %}

## Specify issues that involve users and teams

| Query | Condition |
| :--- | :--- |
| `involves:defunkt involves:jlord` | User involved issues |
| `author:defunkt author:jlord` | User created issues |
| `assignee:defunkt assignee:jlord` | User assigned issues |
| `mentions:defunkt mentions:jlord` | User mentioned issues |
| `commenter:defunkt commenter:jlord` | User commented issues |
| `team:github/owners team:octocat/owners` | Team mentioned issues |

{% hint style="info" %}
Multiple queries of the same type become OR conditions. `Involves:defunkt involves:jlord` is an issue involving `defunkt` or `jlord`.
{% endhint %}

{% hint style="info" %}
involvesはauthor, assignee, mentions, commenter, review-requestedをまとめて指定したものと同様になります。
{% endhint %}

## レビューに関係するpull requestを指定するクエリ <a id="review-query"></a>

| クエリ | 条件 |
| :--- | :--- |
| `review-requested:defunkt review-requested:jlord` | ユーザにレビューリクエストされたpull request |
| `team-review-requested:github/owners team-review-requested:octocat/owners` | チームにレビューリクエストされたpull request |
| `reviewed-by:defunkt reviewed-by:jlord` | ユーザがレビューしたpull request |
| `review:approved`, `review:changes_requested` | approvedされたpull request, changes requestedされたpull request |

{% hint style="info" %}
同じ種類のクエリを複数指定するとOR条件になります。
{% endhint %}

## issueのリポジトリやOrganizationを指定するクエリ <a id="repo-query"></a>

| クエリ | 条件 |
| :--- | :--- |
| `repo:nodejs/node repo:electron/electron` | リポジトリのissue |
| `org:nodejs org:electron` | Organizationのissue |
| `user:defunkt user:jlord` | ユーザ下のissue |

{% hint style="info" %}
同じ種類のクエリを複数指定するとOR条件になります。
{% endhint %}

## ラベルなどのissueの属性を指定するクエリ <a id="label-query"></a>

| クエリ | 条件 |
| :--- | :--- |
| `label:bug label:important` | ラベルがついたissue |
| `milestone:v1.0.0 milestone:v2.0.0` | マイルストーンがついたissue |
| `project:github/57` | Organizationレベルのプロジェクト に紐付いたissue |
| `project:github/linguist/1` | リポジトリレベルのプロジェクト に紐付いたissue |

{% hint style="info" %}
同じ種類のクエリを複数指定するとOR条件になります。ただし、ラベルについてはAND条件となります。
{% endhint %}

{% hint style="info" %}
スペースを含むラベルやマイルストーンの場合は`label:"foo bar"`のようにダブルクオーテーションで囲んでください。
{% endhint %}

## issueのキーワードを指定するクエリ <a id="keyword-query"></a>

| クエリ | 条件 |
| :--- | :--- |
| `github octocat` | キーワード\(AND条件\)が含まれるissue |
| `github OR octocat` | キーワード\(OR条件\)が含まれるissue |
| `github NOT octocat` | キーワード\(NOT条件\)が含まれるissue |

{% hint style="info" %}
スペースを含む場合は`"hello world"`のようにダブルクオーテーションで囲んでください。
{% endhint %}

{% hint style="info" %}
AND, OR, NOTについては5つまでしか含まれることはできません。詳しくは「[Limitations on query length - github.com](https://docs.github.com/en/github/searching-for-information-on-github/troubleshooting-search-queries#limitations-on-query-length)」を参照してください。
{% endhint %}

## 除外・欠如を指定するクエリ <a id="exclude-query"></a>

| クエリ | 条件 |
| :--- | :--- |
| `-label:bug`,  `-milestone:v0.0.1`,  `-repo:nodejs/node` `-involves:defunk`... | 指定した条件が含まれないissue |
| `no:label`, `no:milestone`,  `no:assignee`, `no:project` | ラベル、マイルストーン、アサイン、 プロジェクトが設定されていないissue |

