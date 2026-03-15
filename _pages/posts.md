---
layout: archive
title: "Posts"
permalink: /posts/
author_profile: true
header:
  overlay_color: "#101010"
  overlay_text: "文章辑"
---

<p>这是我目前正在整理或者已经完成的两篇文章，按时间排序，点标题可以直接查看。</p>

{% assign focus_titles = "AI Hackathon Journey,Why Learn Math" | split: "," %}
{% assign focus_posts = site.posts | where_exp: "post", "focus_titles contains post.title" | sort: "date" | reverse %}

{% if focus_posts.size > 0 %}
  {% for post in focus_posts %}
    {% include archive-single.html post=post %}
  {% endfor %}
{% else %}
  <p>暂时还没有匹配的文章，稍后补充。</p>
{% endif %}
