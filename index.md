---
layout: default
title: "Learn ASP.NET core"
---

# Welcome to My GitHub Pages App

This application automatically displays Markdown files from multiple folders.

<ul>
  {% for folder in site.folders %}
    <li><a href="{{ folder.url }}">{{ folder.title }}</a></li>
  {% endfor %}
</ul>
