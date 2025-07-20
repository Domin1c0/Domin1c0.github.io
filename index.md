---
layout: default
title: "Welcome to Domin1c0's Blog"
---

## 📘 学びの猛虎最速の伝説

这里是我的博客主页，将会分享学习过程中撰写的笔记

![博客logo](/assets/images/logo.png)

---

## 最新文章推荐

{% for post in site.posts limit:5 %}
- [{{ post.title }}]({{ post.url }}) — {{ post.date | date: "%Y-%m-%d" }}
{% endfor %}

---

## 快速导航

- [笔记分类](https://domin1c.github.io/tags/)
- [关于我](about.md)
- [GitHub](https://github.com/domin1c0)
- [友情链接](friends.md)

---

感谢你的访问，祝你学习愉快！🚀
