# FAQ

## Concept <a id="concept"></a>

Jasper is more about flexibility than easily, and we aim to tailor the tool's use to a variety of use cases. We've tried to avoid deviating from the core functionality \(Stream\) of the tool to avoid becoming a "flexible but complex" tool.

This gives us an advantage over other similar tools. However, our emphasis on flexibility means that we are sometimes inferior to similar tools in the following respects

* Hurdles to master
  * Requires an understanding of GitHub search
  * Overspecified for occasional use.
* Maintenance of user settings
  * The user needs to maintain the Stream settings to suit the situation.
* Load on the server when using GHE
  * Jasper is a heavy user of the GitHub Search API

That's why we're developing Jasper, balancing flexibility with these shortcomings.

## Smartphone App

Jasper is compatible with Mac/Window/Linux, but it does not support Android/iOS smartphone apps. However, by integrating GitHub Notifications with Jasper, issues viewed from your smartphone's browser can be marked as read in Jasper as well. See "[Smartphone integration](usecase/advanced.md#mobile)" for more information.

## Synchronization of Multiple Machines

Jasper does not support multi-machine issue synchronization, although some users have used file synchronization services such as Dropbox to achieve this on their own. But we do not officially support this at this time. If you would like to use this service, try synchronizing the directories you open by going to `Menu → Dev → Open Data Directory`.

## Tabbed Browser <a id="tab-browser"></a>

Jasper's built-in browser does not support tabbed browsers. If you wish to view multiple issues at the same time, please use an external browser.

## Issue display speed

When viewing an issue in Jasper's internal browser, it may be slow, but this is due to a slow TTFB \(time to first byte\) on the GitHub side. I haven't been able to work around this on the Jasper side at the moment.

![](.gitbook/assets/17_ttfb.png)

## Jasper no longer appears.

 If you get a blank screen after starting Jasper, your data may have been corrupted. Follow these steps to delete and initialize the data in Jasper

1. Select `Menu → Dev → Open Data Directory` to view the directory
2. Quit Jasper
3. Delete the `config.json` and `main.db` in the directory we just left.
4. Launch Jasper and re-set up

This will delete the Stream you've created and any issues you've been holding in Jasper, but it will not affect any data on GitHub.

## Polling the GitHub Search API

Jasper's core functionality, Stream, is achieved by polling the [GitHub Search API](https://docs.github.com/en/free-pro-team@latest/rest/reference/search) on a regular basis. Short polling intervals place a heavy load on the GitHub side, while longer intervals result in poor user experience \(i.e., issue updates\). Jasper strikes a balance between these two by designing the polling as follows

* Instead of polling each Stream, poll the whole Jasper as one poll.
  * Therefore, if there are too many Streams, the update interval per Stream will increase. To mitigate this problem, see "[Optimizing the update interval](usecase/advanced.md#optimizing-the-update-interval)".
* Automatically extend the polling interval when the GitHub API rate limit is reached
  * The rate limit of the GitHub Search API is 10 requests per 60 seconds. The default polling interval is 6 requests per 60 seconds, so the rate limit will never be reached
  * GHE\(GitHub Enterprise\) may have its own rate limit set. Please contact the GHE administrator for more information.

## Supporter Subscriptions

If you want to support the developer \([@h13i32maru](https://twitter.com/h13i32maru)\), it would be great if you could make a small subscription through "[Support Subscription](https://h13i32maru.jp/supporter/)".

## Feedback <a id="competitor"></a>

Please feel free to give us your feedback, and we'd love it if you could write a blog post about Jasper and [\#jasperapp](https://twitter.com/hashtag/jasperapp) on Twitter. If you have a bug or feature request, please send it to [jasperapp/jasper](https://github.com/jasperapp/jasper). We'll do our best to address them as much as possible.

## Competitor <a id="competitor"></a>

Similar to Jasper, tools to manage issue viewing and notification are currently available \(2020.09\)

| Tool | Active | period |
| :--- | :--- | :--- |
| [Jasper](https://jasperapp.io/)  | ✅ | 2016.06 ~ 2020.07 |
| [Trailer](http://ptsochantaris.github.io/trailer/) | ✅ | 2013.08 ~ 2020.09 |
| [DevHub](https://devhubapp.com/)  | ✅ | 2017.05 ~ 2020.08 |
| [Octobox](https://octobox.io/) | ✅ | 2016.12 ~ 2020.09 |
| [GitHawk](http://githawk.com/) | ✅ | 2017.06 ~ 2020.05 |
| [Deck](https://tilfin.github.io/deck/) |  | 2016.03 ~ 2019.12 |
| [faao](https://github.com/azu/faao) |  | 2017.05 ~ 2019.12 |
| [Cashew](https://github.com/bellebethcooper/cashew) |  | 2017.11 ~ 2019.04 |
| [Bee](http://www.neat.io/bee/github-issues-client.html) |  |  2013.08 ~ 2018.09 |
| [Gitscout](https://gitscout.com/) |  | 2015.11 ~ 2017.05 |
| [Ship](https://www.realartists.com/blog/ship-20.html) |  | 2016.01 ~ 2017.01 |
| [DeckHub](https://getdeckhub.com/) |  | 2016.02 ~ 2016.04 |
| [BugHub](http://www.bughubapp.com/) |  | 2013.04 ~ 2015.11 |

## Articles

Developer articles

* [JasperというGitHub Issue Readerを作りました -  blog.h13i32maru.jp](http://blog.h13i32maru.jp/entry/2016/06/08/090000)
* [GitHub用のIssue Reader「Jasper」の開発を振り返ってみる - blog.h13i32maru.jp](http://blog.h13i32maru.jp/entry/2016/12/11/184433)
* [Jasper\(GitHub用のIssue Reader\)を無料にしました - blog.h13i32maru.jp](https://blog.h13i32maru.jp/entry/2018/07/17/083215)
* [ストレスフリーなGitHubのIssue生活 - techlife.cookpad.com](http://techlife.cookpad.com/entry/2017/03/14/100000)
* [Project of the Week: Jasper - electronjs.o](https://www.electronjs.org/blog/jasper)

User articles

* [GithubのISSUEでなにやらやるなら、Jasperが便利だぞ！の話 - uzulla.hateblo.jp](http://uzulla.hateblo.jp/entry/2016/07/13/021425)
* [GitHub Issue Reader の Jasper を1週間使っての所感 - ohbarye.hatenablog.jp](http://ohbarye.hatenablog.jp/entry/2016/11/19/004719)
* [Check my favorite OSS with Jasper - blog.lorentzca.me](https://blog.lorentzca.me/check-my-favorite-oss-with-jasper/)
* [最近使い始めてよかった３つのMacアプリ - medium.com](https://medium.com/@y_koh/%E6%9C%80%E8%BF%91%E4%BD%BF%E3%81%84%E5%A7%8B%E3%82%81%E3%81%A6%E3%82%88%E3%81%8B%E3%81%A3%E3%81%9F%EF%BC%93%E3%81%A4%E3%81%AEmac%E3%82%A2%E3%83%97%E3%83%AA-2e39bc77c925#.j1hugdgm7)
* [Github Issueを管理するJasperを買った - kechol.hatenablog.jp](http://kechol.hatenablog.jp/entry/jasper-a-github-issue-tracker)
* [GitHub Issue Reader「Jasper」をデザイナーにもオススメしたい - transitkix.hatenablog.jp](http://transitkix.hatenablog.jp/entry/2017/08/10/231124)
* [jasperがよかった - medium.com](https://medium.com/@naomeme/jasper%E3%81%8C%E3%82%88%E3%81%8B%E3%81%A3%E3%81%9F-fb70ebd117c0)
* [Jasper。プロダクトマネージャーがボトルネックとならないための最高のツール - quipper.hatenablog.com](https://quipper.hatenablog.com/entry/2018/06/28/120000)

