---
layout: default
title: Home
---

<section class="homepage">

  {% assign featured = site.posts.first %}
  {% if featured %}
    <div class="featured-post-card">
      {% if featured.image %}
        <img src="{{ featured.image | relative_url }}" alt="{{ featured.title }}">
      {% endif %}
      <div class="card-content">
        <h2>Featured Post</h2>
        <h3><a href="{{ featured.url | relative_url }}">{{ featured.title }}</a></h3>
        {% if featured.excerpt %}
          <p>{{ featured.excerpt }}</p>
        {% endif %}
        <p class="read-more"><a href="{{ featured.url | relative_url }}">Read more →</a></p>
      </div>
    </div>
  {% endif %}

  <section class="post-list-cards">
    {% for post in site.posts %}
      <div class="post-card">
        {% if post.image %}
          <img src="{{ post.image | relative_url }}" alt="{{ post.title }}">
        {% endif %}
        <div class="card-content">
          <h3><a href="{{ post.url | relative_url }}">{{ post.title }}</a></h3>
          <p class="meta">{{ post.date | date: "%B %-d, %Y" }}</p>
        </div>
      </div>
    {% endfor %}
  </section>

</section>
