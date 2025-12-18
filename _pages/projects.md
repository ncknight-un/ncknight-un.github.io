---
layout: page
title: Projects
order: 1
permalink: /projects/
---

<div class="container">
  <div class="row">
    {% for post in site.posts %}
      <article class="col col-4 col-t-6 col-m-12 post-preview">
        {% if post.image %}
          <div class="post-image" style="background-image: url({{ site.baseurl }}/images/{{ post.image }});"></div>
        {% endif %}
        <h2 class="post-title">
          <a href="{{ site.baseurl }}{{ post.url }}">{{ post.title }}</a>
        </h2>
        <p class="post-excerpt">{{ post.excerpt | strip_html | truncate: 120 }}</p>
        <span class="post-date">{{ post.date | date: "%b %d, %Y" }}</span>
      </article>
    {% endfor %}
  </div>
</div>