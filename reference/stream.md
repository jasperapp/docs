---
description: Streamに使用できるクエリのリファレンスです。
---

# Stream

Streamは`Add Stream`メニューから追加します。

{% tabs %}
{% tab title="Streamの追加" %}
![](../.gitbook/assets/add-stream.png)
{% endtab %}

{% tab title="Streamの設定" %}
![](../.gitbook/assets/09\_add\_stream2.png)
{% endtab %}
{% endtabs %}

{% hint style="info" %}
Streamに使用できるクエリはGitHub Searchのクエリと完全に互換性があります。GitHub Searchの全クエリとシンタックスについては「[Searching issues and pull requests - github.com](https://docs.github.com/en/github/searching-for-information-on-github/searching-issues-and-pull-requests)」と「[Understanding the search syntax - github.com](https://docs.github.com/en/github/searching-for-information-on-github/understanding-the-search-syntax)」を参照してください。
{% endhint %}

## issueの状態 <a href="#state" id="state"></a>

| クエリ                                                                 | 説明                            |
| ------------------------------------------------------------------- | ----------------------------- |
| `is:issue`, `is:pr`                                                 | issueのみ、pull requestのみ        |
| <p><code>is:open</code>, <code>is:closed</code></p><p>※非推奨</p>      | オープンされているissue、クローズされているissue |
| <p><code>is:merged</code>, <code>is:unmerged</code></p><p>※非推奨</p>  | マージされているissue、マージされていないissue  |
| <p><code>draft:true</code>, <code>draft:false</code></p><p>※非推奨</p> | ドラフトのissue、ドラフトではないissue      |

{% hint style="warning" %}
オープン状態、マージ状態、ドラフト状態のクエリは非推奨です。これらのクエリを使用する場合はFilter Streamをお使いください。詳しくは[こちら](../usecase/query.md#open-issue)を参照してください。
{% endhint %}

## ユーザやチーム <a href="#involves" id="involves"></a>

| クエリ                  | 説明                |
| -------------------- | ----------------- |
| `involves:defunkt`   | ユーザが関係するissue     |
| `author:defunkt`     | ユーザが作成したissue     |
| `assignee:defunkt`   | ユーザがアサインされたissue  |
| `mentions:defunkt`   | ユーザがメンションされたissue |
| `commenter:defunkt`  | ユーザがコメントしたissue   |
| `team:github/owners` | チームがメンションされたissue |

{% hint style="info" %}
同じ種類のクエリを複数指定するとOR条件になります。例えば、`involves:defunkt involves:jlord` は`defunkt`もしくは`jlord`が関係するissueです。
{% endhint %}

{% hint style="info" %}
involvesはauthor, assignee, mentions, commenter, review-requestedをまとめて指定したものと同様になります。
{% endhint %}

## Pull requestレビュー <a href="#review" id="review"></a>

| クエリ                                           | 説明                                                                      |
| --------------------------------------------- | ----------------------------------------------------------------------- |
| `review-requested:defunkt`                    | ユーザにレビューリクエストされたpull request                                            |
| `team-review-requested:github/owners`         | チームにレビューリクエストされたpull request                                            |
| `reviewed-by:defunkt`                         | ユーザがレビューしたpull request                                                  |
| `review:approved`, `review:changes_requested` | <p>approvedされたpull request, </p><p>changes requestedされたpull request</p> |

{% hint style="info" %}
同じ種類のクエリを複数指定するとOR条件になります。例えば、`review-requested:defunkt review-requested:jlord`は`defunkt`もしくは`jlord`がレビューリクエストされたpull requestです。
{% endhint %}

## リポジトリやOrganization <a href="#repo" id="repo"></a>

| クエリ                | 説明                 |
| ------------------ | ------------------ |
| `repo:nodejs/node` | リポジトリのissue        |
| `org:nodejs`       | Organizationのissue |
| `user:defunkt`     | ユーザ下のissue         |

{% hint style="info" %}
同じ種類のクエリを複数指定するとOR条件になります。例えば、`repo:nodejs/node repo:electron/electron`は`nodejs/node`もしくは`electron/electron`のissueです。
{% endhint %}

## ラベルやマイルストーンなど <a href="#label" id="label"></a>

| クエリ                         | 説明                       |
| --------------------------- | ------------------------ |
| `label:bug`                 | ラベルがついたissue             |
| `milestone:v1.0.0`          | マイルストーンがついたissue         |
| `project:github/57`         | Organizationプロジェクトのissue |
| `project:github/linguist/1` | リポジトリプロジェクトのissue        |

{% hint style="info" %}
同じ種類のクエリを複数指定するとOR条件になります。例えば、`milestone:v1.0.0 milestone:v2.0.0`は`v1.0.0`もしくは`v2.0.0`のissueです。\
ただし、ラベルについてはAND条件となります。
{% endhint %}

{% hint style="info" %}
スペースを含むラベルやマイルストーンの場合は`label:"foo bar"`のようにダブルクオーテーションで囲んでください。
{% endhint %}

## 任意のキーワード <a href="#keyword" id="keyword"></a>

| クエリ                  | 説明                     |
| -------------------- | ---------------------- |
| `github octocat`     | キーワード(AND条件)が含まれるissue |
| `github OR octocat`  | キーワード(OR条件)が含まれるissue  |
| `github NOT octocat` | キーワード(NOT条件)が含まれるissue |

{% hint style="info" %}
スペースを含む場合は`"hello world"`のようにダブルクオーテーションで囲んでください。
{% endhint %}

{% hint style="info" %}
AND, OR, NOTについては5つまでしか含まれることはできません。詳しくは「[Limitations on query length - github.com](https://docs.github.com/en/github/searching-for-information-on-github/troubleshooting-search-queries#limitations-on-query-length)」を参照してください。
{% endhint %}

## 除外・未設定 <a href="#exclude" id="exclude"></a>

| クエリ                                                                                                                                  | 説明                                               |
| ------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------ |
| <p><code>-label:bug</code>,  <code>-milestone:v0.0.1</code>, <br><code>-repo:nodejs/node</code> <code>-involves:defunk</code>...</p> | 指定した条件が含まれないissue                                |
| <p><code>no:label</code>, <code>no:milestone</code>, <br><code>no:assignee</code>, <code>no:project</code></p>                       | <p>ラベル、マイルストーン、アサイン、<br>プロジェクトが設定されていないissue</p> |
