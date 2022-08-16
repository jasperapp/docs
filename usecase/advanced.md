---
description: Integration with GitHub's features allows for more advanced usage.
---

# Advanced settings

## Smartphone integration <a href="#mobile" id="mobile"></a>

You must enable GitHub Notification Sync in order for Jasper to read issues viewed on a smartphone or normal browser.

![](../.gitbook/assets/07\_notification\_sync.png)

By enabling this setting, [GitHub Notifications](https://github.com/notifications) will periodically (usually at 60-second intervals) reflect this to Jasper.

{% hint style="warning" %}
Jasper will only reflect the issue in GitHub Notifications if you have "Viewed and marked the issue as read". The following operations will not be reflected in GitHub Notifications

* Unread issues in Jasper
* Issues read using a menu or keyboard shortcut in Jasper
{% endhint %}

## GitHub Projects Integration <a href="#project" id="project"></a>

To view issues related to a specific Github Project, create a Project Stream.

{% tabs %}
{% tab title="Creating a Project Stream" %}
![](../.gitbook/assets/07\_project\_stream1.png)
{% endtab %}

{% tab title="View Project Stream" %}
![](../.gitbook/assets/07\_project\_stream2.png)
{% endtab %}
{% endtabs %}

{% hint style="info" %}
With the `project:REPOSITORY/PROJECT_BOARD` query, you can still create a regular Stream to view issues related to GitHub Projects. However, we recommend using Project Stream as it allows you to work with the Project Board (Kanban).
{% endhint %}

## GitHub Team Integration <a href="#team" id="team"></a>

Use the Team Stream to view issues that have been mentioned to your GitHub Team.

{% tabs %}
{% tab title="Enable Team Stream" %}
![](../.gitbook/assets/07\_team\_stream1.png)
{% endtab %}

{% tab title="Team Stream" %}
![](../.gitbook/assets/07\_team\_stream3.png)
{% endtab %}

{% tab title="Team Stream queries" %}
Queries are automatically created from the Team you belong to.

![](../.gitbook/assets/07\_team\_stream2.png)
{% endtab %}
{% endtabs %}

## GitHub Watching Integration <a href="#watching" id="watching"></a>

You can use the Watching Stream to view issues in repositories that you have watched on GitHub.

{% tabs %}
{% tab title="Enable Watching Stream" %}
![](../.gitbook/assets/07\_watchiing\_stream1.png)
{% endtab %}

{% tab title="Watching Stream" %}
![](../.gitbook/assets/07\_watching\_stream2.png)
{% endtab %}

{% tab title="Watching Stream queries" %}
Queries are automatically created from the repositories you watch.

![](../.gitbook/assets/07\_watching\_stream3.png)
{% endtab %}
{% endtabs %}

## Register any issues <a href="#subscription" id="subscription"></a>

If you want the issue to be a Stream on its own, rather than a repository or organization, use the Subscription Stream, which you enable from the configuration screen.

{% tabs %}
{% tab title="Enable Subscription Stream" %}
![](../.gitbook/assets/07\_subscription\_stream1.png)
{% endtab %}

{% tab title="Subscription Stream" %}
![](../.gitbook/assets/07\_subscription\_stream2.png)
{% endtab %}

{% tab title="Register issue" %}
Right-click on the Subscription Stream and register the URL of the issue in the menu.

![](../.gitbook/assets/07\_subscription\_stream3.png)
{% endtab %}
{% endtabs %}

## Optimizing the update interval <a href="#optimize" id="optimize"></a>

Jasper typically looks for an issue every 10 seconds to get an update. This update interval is not per Stream, but rather for the entire Jasper. This means that the more Streams you create, the slower the update per Stream will be. For example, if you are creating three Streams, a Stream will only be updated every 30 seconds.

{% hint style="info" %}
The reason it works this way is so that more Streams don't overload GitHub.
{% endhint %}

This is why creating a lot of Streams can slow down updates. So we use fewer regular Streams and more Filter Streams, so that updates are not slowed down.

{% hint style="info" %}
Filter Stream does not search GitHub and filters local issues, so it does not affect the update interval. For more information on Filter Stream, see "[Filter Stream](../reference/filter-stream.md)".
{% endhint %}

For example, instead of creating two Streams, create a Stream and two Filter Streams, like this This will allow you to update at 10 second intervals per stream, instead of 20 seconds per stream in the former.

{% tabs %}
{% tab title="Two Streams" %}
```
org:nodejs
```

```
org:electron
```

![](../.gitbook/assets/07\_optimize\_interval1.png)
{% endtab %}

{% tab title="A Stream and two Filter Streams" %}
```
org:nodejs org:electron
```

```
org:nodejs
```

```
org:electron
```

![](../.gitbook/assets/07\_optimize\_interval2.png)
{% endtab %}
{% endtabs %}

Jasper recommends using Filter Stream actively in this way.
