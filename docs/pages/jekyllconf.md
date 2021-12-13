---
layout: page
title: Jekyll 大会
permalink: /jekyllconf/
---

[Jekyll 大会](http://jekyllconf.com)是免费的在线会议，由 [CloudCannon](http://cloudcannon.com) 主办，讨论 Jekyll 的所有事情。每年 Jekyll 社区的成员都会谈论有趣的用例、他们学到的技巧或 Jekyll 元主题。

## 精选

{% assign random = site.time | date: "%s%N" | modulo: site.data.jekyllconf-talks.size %}
{% assign featured = site.data.jekyllconf-talks[random] %}

**{{ featured.topic }}** - [*{{ featured.speaker }}*](https://twitter.com/{{ featured.twitter_handle }})
<div class="videoWrapper">
    <iframe width="420" height="315" src="https://www.youtube.com/embed/{{ featured.youtube_id }}" frameborder="0" allowfullscreen></iframe>
</div>

{% assign talks = site.data.jekyllconf-talks | group_by: 'year' %}
{% for year in talks reversed %}
## {{ year.name }}
{% for talk in year.items %}
 * [**{{ talk.topic }}**](https://youtu.be/{{ talk.youtube_id }}) - [*{{ talk.speaker }}*](https://twitter.com/{{ talk.twitter_handle }})
{% endfor %}
{% endfor %}
