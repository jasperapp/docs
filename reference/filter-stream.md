---
description: This is a reference for the filters available in Filter Stream.
---

# Filter Stream

Filter Stream filters the Stream's issues and displays them.

Filter Streams are added from the `Add Filter Stream` menu in the Stream menu. Or, to create a top-level stream, add it from the `Add Filter Stream top-level` menu. It is also possible to apply a Filter temporarily.

{% tabs %}
{% tab title="Add Filter Stream" %}
![](../.gitbook/assets/add-filter-stream.png)
{% endtab %}

{% tab title="Filter Stream setting" %}
![](../.gitbook/assets/10\_filter\_stream2.png)
{% endtab %}

{% tab title="Add Top Level Filter Stream" %}
![](../.gitbook/assets/add-filter-stream-top.png)
{% endtab %}

{% tab title="Temporarily" %}
![](../.gitbook/assets/10\_filter\_stream4.png)
{% endtab %}
{% endtabs %}

{% hint style="info" %}
The filters available in the Filter Stream are pretty much the same as in the Stream, but note that some of them are slightly different.
{% endhint %}

## State of issues <a href="#state" id="state"></a>

| Filter                         | description                                              |
| ------------------------------ | -------------------------------------------------------- |
| `is:issue`, `is:pr`            | Issues only, pull requests only                          |
| `is:open`, `is:closed`         | Opened issues, closed issues                             |
| `is:merged`, `is:unmerged`     | Merged issues, unmerged issues                           |
| `draft:true`, `draft:false`    | Draft issues, not draft issue‌s                          |
| `is:read`, `is:unread`         | Read issues, unread issues                               |
| `is:bookmark`, `is:unbookmark` | Bookmarked issues, not bookmarked issue                  |
| `is:archived`, `is:unarchived` | Archived issues, not archived issues                     |
| `is:private`, `is:unprivate`   | Private repository issues, not private repository issues |

## Involve users and teams <a href="#involves" id="involves"></a>

| Filter               | description           |
| -------------------- | --------------------- |
| `involves:defunkt`   | User involved issues  |
| `author:defunkt`     | User created issues   |
| `assignee:defunkt`   | User assigned issues  |
| `mentions:defunkt`   | User mentioned issues |
| `team:github/owners` | Team mentioned issues |

{% hint style="info" %}
Multiple filters of the same type can be specified as OR conditions. For example, `involves:defunkt involves:jlord` is issues involving `defunkt` or `jlord`.
{% endhint %}

{% hint style="info" %}
`involves` as well as `author`, `assignee`, `mentions`,`commenter` and `review-requested` all together.‌
{% endhint %}

## Pull requests review <a href="#review" id="review"></a>

| Filter                     | description                                              |
| -------------------------- | -------------------------------------------------------- |
| `review-requested:defunkt` | Pull requests where the user/team has requested a review |
| `reviewed-by:defunkt`      | User reviewed pull requests                              |

{% hint style="info" %}
Specifying multiple queries of the same type is an OR condition. For example, `review-requested:defunkt review-requested:jlord` is pull requests where `defunkt` or `jlord` is the review request.
{% endhint %}

## Repository and Organization <a href="#repo" id="repo"></a>

| Filter             | description         |
| ------------------ | ------------------- |
| `repo:nodejs/node` | Repository issues   |
| `org:nodejs`       | Organization issues |
| `user:defunkt`     | User issues         |

{% hint style="info" %}
Specifying multiple queries of the same type is an OR condition. For example, `repo:nodejs/node repo:electron/electron` is issues of `nodejs/node` or `electron/electron`.
{% endhint %}

## Label, milestone, etc <a href="#label" id="label"></a>

| Filter                                 | description                                               |
| -------------------------------------- | --------------------------------------------------------- |
| `label:bug`, `label:bug-%`             | <p>Labeled issues<br>% matches any string</p>             |
| `milestone:v1.0.0`, `milestone:v2.0.%` | <p>Milestone issues<br>% matches any string</p>           |
| `title:test`, `title:%test%`           | <p>Issue with specified title<br>% matches any string</p> |
| `project-name:hello-pj`                | Project issues                                            |
| `project-column:now-doing`             | Project column issues                                     |
| `number:123`                           | Issue number                                              |

Labels can also specify dynamic dates as follows.

| Filter                                                           | Description (assuming today is 2022-08-16)                                                                                                                                   |
| ---------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `label:release_@current_date`                                    | `@current_date` is replaced by the current date. In other words, `label:release_2022%08%16` is executed as a filter.                                                         |
| `label:release_@prev_date`                                       | The `@prev_date` is replaced by yesterday's date. In other words, `label:release_2022%08%15` is executed as a filter.                                                        |
| `label:release_@next_date`                                       | The `@next_date` is replaced by tomorrow's date. In other words, `label:release_2022%08%17` is executed as a filter.                                                         |
| `label:release_@current_date+1`, `label:release_@current_date-1` | Following `@current_date` with `+1` or `-1` replaces the date relative to the current date. So the filter will run `label:release_2022%08%17` or `label:release_2022%08%15`. |



{% hint style="info" %}
Specifying multiple queries of the same type is an OR condition. For example, `milestone:v1.0.0.0 milestone:v2.0.0` is issues with a `v1.0.0` or `v2.0.0.0` milestone. However, this is an AND condition for labels.
{% endhint %}

{% hint style="info" %}
A label or milestone containing spaces should be enclosed in double quotation marks, such as `label: "hello world"`.
{% endhint %}

## Any keywords <a href="#keyword" id="keyword"></a>

| Filter           | description                                     |
| ---------------- | ----------------------------------------------- |
| `github octocat` | Issues containing the keywords (AND conditions) |

{% hint style="info" %}
To include spaces, use double quotation marks, such as `"hello world"`.
{% endhint %}

{% hint style="info" %}
Search keywords in issue body, author, assignee, label, milestone, repository, org, involves, review-requested, review, project-name and project-columns.
{% endhint %}

{% hint style="warning" %}
OR and NOT are not supported.
{% endhint %}

## Exclusion and missing <a href="#exclude" id="exclude"></a>

| Filter                                                                                                                                                    | Condition                                                                          |
| --------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------- |
| <p><code>-label:bug</code>,<br><code>-milestone:v0.0.1</code>, <br><code>-repo:nodejs/node</code> ,<br><code>-involves:defunk</code> ,</p><p>and more</p> | Issues that do not contain the specified conditions                                |
| <p><code>no:label</code>,<br><code>no:milestone</code>,<br><code>no:assignee</code>,<br><code>no:project</code>,<br><code>no:dueon</code></p>             | <p>Labels, Milestones, Assignments, </p><p>and An issue with no project set up</p> |
| <p><code>have:label</code>,<br><code>have:milestone</code>,<br><code>have:assignee</code>,<br><code>have:project</code>,<br><code>have:dueon</code></p>   | <p>Labels, Milestones, Assignments, </p><p>and An issue with project set up</p>    |

