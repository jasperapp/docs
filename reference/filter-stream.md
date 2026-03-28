---
description: Filter Streamで使用できるフィルターのリファレンスです。
---

# Filter Stream

Filter StreamはStreamのissueをフィルターして表示します。

Filter StreamはStreamのメニューにある`Add Filter Stream`から追加します。もしくはトップレベルに作成する場合は`Add Filter Stream top-level`から追加します。また、一時的にFilterを適用することもできます。

{% tabs %}
{% tab title="Filter Streamの追加" %}
![](../.gitbook/assets/add-filter-stream.png)
{% endtab %}

{% tab title="Filter Streamの設定" %}
![](../.gitbook/assets/10\_filter\_stream2.png)
{% endtab %}

{% tab title="Top Levelへの追加" %}
![](../.gitbook/assets/add-filter-stream-top.png)
{% endtab %}

{% tab title="一時的" %}
![](../.gitbook/assets/10\_filter\_stream4.png)
{% endtab %}
{% endtabs %}

{% hint style="info" %}
Filter Streamで使用できるフィルターはStreamとほとんど同じ条件を指定できます。ただし、少し異なるものもあるので注意してください。
{% endhint %}

## issueの状態 <a href="#state" id="state"></a>

| フィルター                          | 説明                                               |
| ------------------------------ | ------------------------------------------------ |
| `is:issue`, `is:pr`            | issueのみ、pull requestのみ                           |
| `is:open`, `is:closed`         | オープンされているissue、クローズされているissue                    |
| `is:merged`, `is:unmerged`     | マージされているissue、マージされていないissue                     |
| `draft:true`, `draft:false`    | ドラフトのissue、ドラフトではないissue‌                        |
| `is:read`, `is:unread`         | 既読のissue、未読のissue                                |
| `is:bookmark`, `is:unbookmark` | <p>ブックマークされたissue、<br>ブックマークされていないissue</p>      |
| `is:archived`, `is:unarchived` | <p>アーカイブされたissue、</p><p>アーカイブされていないissue</p>     |
| `is:private`, `is:unprivate`   | <p>プライベートリポジトリのissue、</p><p>パブリックリポジトリのissue</p> |

## ユーザやチーム <a href="#involves" id="involves"></a>

| フィルター                | 説明                |
| -------------------- | ----------------- |
| `involves:defunkt`   | ユーザが関係するissue     |
| `author:defunkt`     | ユーザが作成したissue     |
| `assignee:defunkt`   | ユーザがアサインされたissue  |
| `mentions:defunkt`   | ユーザがメンションされたissue |
| `team:github/owners` | チームがメンションされたissue |

{% hint style="info" %}
同じ種類のフィルターを複数指定するとOR条件になります。例えば、`involves:defunkt involves:jlord`は`defunkt`もしくは`jlord`が関係するissueです。
{% endhint %}

{% hint style="info" %}
`involves`は`author`, `assignee`, `mentions`,`commenter`, `review-requested`をまとめて指定したものと同様になります。‌
{% endhint %}

## Pull requestレビュー <a href="#review" id="review"></a>

| フィルター                      | 説明                               |
| -------------------------- | -------------------------------- |
| `review-requested:defunkt` | ユーザ/チームがレビューリクエストされたpull request |
| `reviewed-by:defunkt`      | ユーザがレビューしたpull request           |

{% hint style="info" %}
同じ種類のクエリを複数指定するとOR条件になります。例えば、‌`review-requested:defunkt review-requested:jlord`は`defunkt`もしくは`jlord`がレビューリクエストされたpull requestです。
{% endhint %}

## リポジトリやOrganization <a href="#repo" id="repo"></a>

| フィルター              | 説明                 |
| ------------------ | ------------------ |
| `repo:nodejs/node` | リポジトリのissue        |
| `org:nodejs`       | Organizationのissue |
| `user:defunkt`     | ユーザ下のissue         |

{% hint style="info" %}
同じ種類のクエリを複数指定するとOR条件になります。‌例えば、`repo:nodejs/node repo:electron/electron`は`nodejs/node`もしくは`electron/electron`のissueです。
{% endhint %}

## ラベルやマイルストーンなど <a href="#label" id="label"></a>

| フィルター                                  | 説明                                        |
| -------------------------------------- | ----------------------------------------- |
| `label:bug`, `label:bug-%`             | <p>ラベルがついたissue<br>%は任意の文字列にマッチ</p>       |
| `milestone:v1.0.0`, `milestone:v2.0.%` | <p>マイルストーンがついたissue<br>%は任意の文字列にマッチ</p>   |
| `title:テスト`, `title:%テスト%`             | <p>指定されたタイトルがついたissue<br>%は任意の文字列にマッチ</p> |
| `project-name:hello-pj`                | プロジェクトに紐付いたissue                          |
| `project-column:now-doing`             | プロジェクトカラムに紐付いたissue                       |
| `number:123`                           | 特定のissue番号                                |

ラベルには以下のように動的な日付を指定することもできます。

| フィルター                                                            | 説明（今日が2022-08-16だとする）                                                                                                                 |
| ---------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------- |
| `label:release_@current_date`                                    | `@current_date`が現在の日付に置き換えられます。つまりフィルターとしては`label:release_2022%08%16`が実行されます。                                                         |
| `label:release_@prev_date`                                       | `@prev_date`が昨日の日付に置き換えられます。つまりフィルターとしては`label:release_2022%08%15`が実行されます。                                                            |
| `label:release_@next_date`                                       | `@next_date`が明日の日付に置き換えられます。つまりフィルターとしては`label:release_2022%08%17`が実行されます。                                                            |
| `label:release_@current_date+1`, `label:release_@current_date-1` | `@current_date`に続けて、`+1`や`-1`を指定すると、現在の日付から相対的な日付に置き換えられます。つまりフィルターはとしては`label:release_2022%08%17`や`label:release_2022%08%15`が実行されます。 |

{% hint style="info" %}
同じ種類のクエリを複数指定するとOR条件になります。例えば、`milestone:v1.0.0 milestone:v2.0.0`は`v1.0.0`もしくは`v2.0.0`のマイルストーンがついたissueです。ただし、ラベルについてはAND条件となります。
{% endhint %}

{% hint style="info" %}
スペースを含むラベルやマイルストーンの場合は`label:"`hello `world"`のようにダブルクオーテーションで囲んでください。‌
{% endhint %}

## GitHub プロジェクト

| フィルター                                  | 説明                                        |
| -------------------------------------- | ----------------------------------------- |
| `project-field:status/ToDo` | statusフィールドがToDoになっているissue      |
| `project-field:sprint/@current_iteration` | sprintフィールドが現在のイテレーションになっているissue      |
| `project-field:foo/bar` | fooフィールドがbarになっているissue      |

以下はclassicプロジェクト用のフィルターです。

| フィルター                                  | 説明                                        |
| -------------------------------------- | ----------------------------------------- |
| `project-name:hello-pj` (classic project) | プロジェクトに紐付いたissue                          |
| `project-column:now-doing` (classic project) | プロジェクトカラムに紐付いたissue                       |


## 任意のキーワード <a href="#keyword" id="keyword"></a>

| フィルター            | 説明                     |
| ---------------- | ---------------------- |
| `github octocat` | キーワード(AND条件)が含まれるissue |

{% hint style="info" %}
スペースを含む場合は`"hello world"`のようにダブルクオーテーションで囲んでください。
{% endhint %}

{% hint style="info" %}
キーワードはissue本文, author, assignee, label, milestone, repository, org, involves, review-requested, review, project-name, project-columnsを対象とします。
{% endhint %}

{% hint style="warning" %}
OR, NOTには対応していません。
{% endhint %}

## 除外・欠如 <a href="#exclude" id="exclude"></a>

| フィルター                                                                                                                                          | 説明                                        |
| ---------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------- |
| `-label:bug`, `-milestone:v0.0.1`, `-repo:nodejs/node` `-involves:defunk`...                                                                   | 指定した条件が含まれないissue                         |
| `no:label`, `no:milestone`, `no:assignee`, `no:project`, `no:dueon`                                                                            | ラベル、マイルストーン、アサイン、 プロジェクト、締切が設定されていないissue |
| <p><code>have:label</code>, <code>have:milestone</code>, <code>have:assignee</code>, <code>have:project</code>,<br><code>have:dueon</code></p> | ラベル、マイルストーン、アサイン、 プロジェクト、締切が設定されているissue  |
