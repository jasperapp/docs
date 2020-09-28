---
description: Streamに使用できるクエリのリファレンスです。
---

# Stream

Streamは`Add Stream`メニューから追加します。

{% tabs %}
{% tab title="Streamの追加" %}
![](../.gitbook/assets/09_add_stream1.png)
{% endtab %}

{% tab title="Streamの設定" %}
![](../.gitbook/assets/09_add_stream2.png)
{% endtab %}
{% endtabs %}

{% hint style="info" %}
Streamに使用できるクエリはGitHub Searchのクエリと完全に互換性があります。GitHub Searchの全クエリとシンタックスについては「[Searching issues and pull requests - github.com](https://docs.github.com/en/github/searching-for-information-on-github/searching-issues-and-pull-requests)」と「[Understanding the search syntax - github.com](https://docs.github.com/en/github/searching-for-information-on-github/understanding-the-search-syntax)」を参照してください。
{% endhint %}

## issueの状態を指定するクエリ <a id="is-query"></a>

<table>
  <thead>
    <tr>
      <th style="text-align:left">&#x30AF;&#x30A8;&#x30EA;</th>
      <th style="text-align:left">&#x6761;&#x4EF6;</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><code>is:issue</code>, <code>is:pr</code>
      </td>
      <td style="text-align:left">issue&#x306E;&#x307F;&#x3001;pull request&#x306E;&#x307F;</td>
    </tr>
    <tr>
      <td style="text-align:left">
        <p><code>is:open</code>, <code>is:closed</code>
        </p>
        <p>&#x203B;&#x975E;&#x63A8;&#x5968;</p>
      </td>
      <td style="text-align:left">&#x30AA;&#x30FC;&#x30D7;&#x30F3;&#x3055;&#x308C;&#x3066;&#x3044;&#x308B;issue&#x3001;&#x30AF;&#x30ED;&#x30FC;&#x30BA;&#x3055;&#x308C;&#x3066;&#x3044;&#x308B;issue</td>
    </tr>
    <tr>
      <td style="text-align:left">
        <p><code>is:merged</code>, <code>is:unmerged</code>
        </p>
        <p>&#x203B;&#x975E;&#x63A8;&#x5968;</p>
      </td>
      <td style="text-align:left">&#x30DE;&#x30FC;&#x30B8;&#x3055;&#x308C;&#x3066;&#x3044;&#x308B;issue&#x3001;&#x30DE;&#x30FC;&#x30B8;&#x3055;&#x308C;&#x3066;&#x3044;&#x306A;&#x3044;issue</td>
    </tr>
    <tr>
      <td style="text-align:left">
        <p><code>draft:true</code>, <code>draft:false</code>
        </p>
        <p>&#x203B;&#x975E;&#x63A8;&#x5968;</p>
      </td>
      <td style="text-align:left">&#x30C9;&#x30E9;&#x30D5;&#x30C8;&#x306E;issue&#x3001;&#x30C9;&#x30E9;&#x30D5;&#x30C8;&#x3067;&#x306F;&#x306A;&#x3044;issue</td>
    </tr>
  </tbody>
</table>

{% hint style="warning" %}
オープン状態、マージ状態、ドラフト状態のクエリは非推奨です。これらのクエリを使用する場合はFilter Streamをお使いください。詳しくは[こちら](../usecase/stream-query.md#open-issue)を参照してください。
{% endhint %}

## ユーザやチームが関係するissueを指定するクエリ <a id="involves-query"></a>

| クエリ | 条件 |
| :--- | :--- |
| `involves:defunkt involves:jlord` | ユーザが関連するissue |
| `author:defunkt author:jlord` | ユーザが作成したissue |
| `assignee:defunkt assignee:jlord` | ユーザがアサインされたissue |
| `mentions:defunkt mentions:jlord` | ユーザがメンションされたissue |
| `commenter:defunkt commenter:jlord` | ユーザがコメントしたissue |
| `team:github/owners team:octocat/owners` | チームがメンションされたissue |

{% hint style="info" %}
同じ種類のクエリを複数指定するとOR条件になります。
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

