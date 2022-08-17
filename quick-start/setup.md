---
description: Just download Jasper and set up a GitHub access token and you're ready to go.
---

# Setup

## Install <a href="#install" id="install"></a>

Download the latest version of Jasper from [jasperapp.io](https://jasperapp.io/) and extract the zip file. Follow the instructions to complete the launch.

{% tabs %}
{% tab title="Mac" %}
![](../.gitbook/assets/02\_mac.png)
{% endtab %}

{% tab title="Windows" %}
![](../.gitbook/assets/02\_windows1.png)

![](../.gitbook/assets/02\_windows2.png)
{% endtab %}
{% endtabs %}

## Setting up an access token <a href="#access-token" id="access-token"></a>

When Jasper is launched, you will be presented with a choice of GitHub or GHE (GitHub Enterprise), for GHE enter the hostname `example ghe.example.com`.

Next, you will need to enter an access token, which differs between GitHub and GHE.

{% tabs %}
{% tab title="For GitHub" %}
For GitHub, we recommend setting up an access token using OAuth. Please follow the on-screen instructions to perform OAuth authentication.

![](<../.gitbook/assets/Screen Shot 2022-08-16 at 16.27.19.png>)

Alternatively, an access token can be created and used from a [Personal access token](https://github.com/settings/tokens). The required scopes are `repo`, `read:org`, `notifications`, `user` and `read:project` .

![](<../.gitbook/assets/Screen Shot 2022-08-17 at 12.15.06.png>)
{% endtab %}

{% tab title="For GHE" %}
For GHE, you can create an access token from `https://GHE_HOST/settings/tokens`. The required scopes are `repo`, `read:org`, `notifications`, `user` and `read:project` .

![](<../.gitbook/assets/Screen Shot 2022-08-17 at 12.15.14.png>)
{% endtab %}
{% endtabs %}

Finally, confirm the settings and press OK. When the user name is displayed, you are done 🎉.

![](<../.gitbook/assets/Screen Shot 2022-08-16 at 16.41.32.png>)

## Initial loading <a href="#initial-loading" id="initial-loading"></a>

Once the setup is complete, the system will automatically start loading the issue. This initial loading takes a few minutes or so - do not exit Jasper and use it.

To help you get started with Jasper, please read the "[Basic Usage](basic-usage.md)" section during the initial loading process.
