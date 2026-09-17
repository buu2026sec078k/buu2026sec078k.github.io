---
layout: default
title: 文章列表
---

# <span class="emoji emoji2747"></span> 我的 Writeup 存档

> 这里放我做过的 CTF 和学习笔记

<ul style="list-style:none; padding-left:0;">
  {% for post in site.posts %}
  <li style="margin:14px 0; padding:10px 12px; border‑left:3px solid #5a9bd5;">
    <span style="opacity:0.7;">{{ post.date | date:"%Y‑%m‑%d" }}</span>
    <a href="{{ " style="margin-left:8px; font-weight:500;">
      {{ post.title }}</a >
 </li>
{% endfor %}
</ul>
