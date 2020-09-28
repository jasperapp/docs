---
description: >-
  Stream allows you to specify flexible queries. Here are some of the most
  commonly used queries.
---

# Stream queries

## Open issues <a id="open-issue"></a>

You can use `is:open` to create a Stream to view issues in an open \(unclosed or unmerged\) state. For example, to view an open issue in the `nodejs/node` repository, you can create a Stream with the following query

```text
repo:nodejs/node is:open is:issue
```

However, Jasper does not recommend using `is:open` to create a Stream because Jasper will not be able to detect when the Stream is closed from open to closed.

{% hint style="info" %}
This is a limitation of Jasper's polling of the GitHub Search API
{% endhint %}

So when using `is:open`, you should use the Filter Stream instead of the regular Stream. Filter Stream can be used to apply custom filters to a normal Stream. In the previous example, this would look like

Stream

```text
repo:nodejs/node is:issue
```

Filter Stream

```text
is:open
```

![](../.gitbook/assets/05_open.png)

{% hint style="info" %}
For more information about Filter Stream, see "[Filter Stream](../reference/filter-stream.md)" in the reference.
{% endhint %}

{% hint style="info" %}
The same restrictions apply to close, merge and draft states.
{% endhint %}

## Team mentioned issues <a id="team-issue"></a>

To view Team mentioned issues, use `team:ORGNAME/TEAMNAME`. For example, to view issues where `@jekyll/owners` are mentioned, create a Stream with a query like this

```text
team:@jekyll/owners
```

GitHub Docs: [Search by team mention](https://docs.github.com/en/github/searching-for-information-on-github/searching-issues-and-pull-requests#search-by-team-mention)

## User involved issues <a id="involves-issue"></a>

To view issues involving a particular user, use the `involves:USERNAME`. For example, to see the issues involving a `defunkt` or `jlord`, create a Stream with a query like this

```text
involves:defunkt involves:jlord
```

{% hint style="info" %}
The `involves:USERNAME` is a useful query to specify author, assign, mention, comment, and review-requested all together.
{% endhint %}

GitHub Docs: [Search by a user that's involved in an issue or pull request](https://docs.github.com/en/github/searching-for-information-on-github/searching-issues-and-pull-requests#search-by-a-user-thats-involved-in-an-issue-or-pull-request)

## Repository and organization issues <a id="repo-issue"></a>

To view issues in a specific repository, use `repo:USERNAME/REPOSITORY`. For example, to view issues in the `nodejs/node` or `electron/electron` repositories, you would create a Stream with a query like this

```text
repo:nodejs/node repo:electron/electron
```

To view a specific Organization issue, use `org:ORGNAME`. For example, to view issues of the `nodejs` or `electron` Organization, you can create a Stream with a query like this

```text
org:nodejs org:electron
```

GitHub Docs: [Search within a user's or organization's repositories](https://docs.github.com/en/github/searching-for-information-on-github/searching-issues-and-pull-requests#search-within-a-users-or-organizations-repositories)

## Issues with milestones and labels <a id="label-issue"></a>

You can view issues with a specific milestone by using `milestone:MILESTONE_NAME`. For example, to see an issue with a milestone of `13.0.0` or `14.0.0` in the `nodejs/node` repository, create a Stream with a query like this

```text
repo:nodejs/node milestone:13.0.0 milestone14.0.0
```

You can view issues labeled with a specific label using `label:LABEL_NAME`. For example, to view an issue labeled `build` **and** `zlib` in the `nodejs/node` repository, create a Stream with the following query

```text
repo:nodejs/node label:build label:zlib
```

{% hint style="info" %}
If multiple labels are specified, it is an and condition.
{% endhint %}

{% hint style="info" %}
For milestones and labels that contain spaces, specify them as `milestone: "foo bar"`.
{% endhint %}

GitHub Docs: [Search by milestone](https://docs.github.com/en/github/searching-for-information-on-github/searching-issues-and-pull-requests#search-by-milestone), [Search by label](https://docs.github.com/en/github/searching-for-information-on-github/searching-issues-and-pull-requests#search-by-label) 

## Issues containing the keywords <a id="keyword-issue"></a>

To view issues containing specific keywords, use the `KEYWORD`. For example, to see issues containing the `octocat` and `github`, create a Stream with the following query

{% tabs %}
{% tab title="AND condition" %}
```text
octocat github
```
{% endtab %}

{% tab title="OR condition" %}
```
octocat OR github
```
{% endtab %}

{% tab title="NOT condition" %}
```
octocat NOT github
```
{% endtab %}
{% endtabs %}

{% hint style="info" %}
Keywords including multi-byte characters and spaces should be specified as `"foo bar"`.
{% endhint %}

GitHub Docs: [Limitations on query length](https://docs.github.com/en/github/searching-for-information-on-github/troubleshooting-search-queries#limitations-on-query-length),  [Exclude certain results](https://docs.github.com/en/github/searching-for-information-on-github/understanding-the-search-syntax#exclude-certain-results)

## Exclusionary specification <a id="exclude-issue"></a>

You can use `-QUALIFIER` to exclude a specific repository, label or etc . For example, to view issues in the `nodejs` organizaton that do not contain a `nodejs/node` repository and a `bug` label, you can create a Stream with a query like this

```text
org:nodejs -repo:nodejs/node -label:bug
```

GitHub Docs: [Exclude certain results](https://docs.github.com/en/github/searching-for-information-on-github/understanding-the-search-syntax#exclude-certain-results)

