---
layout: post
title: Add tags to Jekyll pages
category:
tags: [Jekyll, Tag]
---

1. Create `/tag.html` and copy below front matter and liquid codes to it.

```
---
layout: default
title: Tag
---
```

```liquid
{% comment %}
=======================
The following part extracts all the tags from your posts and sort tags, so that you do not need to manually collect your tags to a place.
=======================
{% endcomment %}
{% assign rawtags = "" %}
{% for post in site.posts %}
    {% assign ttags = post.tags | join:'|' | append:'|' %}
    {% assign rawtags = rawtags | append:ttags %}
{% endfor %}
{% assign rawtags = rawtags | split:'|' | sort %}
```

```liquid
{% comment %}
=======================
The following part removes dulpicated tags and invalid tags like blank tag.
=======================
{% endcomment %}
{% assign tags = "" %}
{% for tag in rawtags %}
    {% if tag != "" %}
        {% if tags == "" %}
            {% assign tags = tag | split:'|' %}
        {% endif %}
        {% unless tags contains tag %}
            {% assign tags = tags | join:'|' | append:'|' | append:tag | split:'|' %}
        {% endunless %}
    {% endif %}
{% endfor %}
```

```liquid
{% comment %}
=======================
The purpose of this snippet is to list all the tags you have in your site.
=======================
{% endcomment %}
{% for tag in tags %}
    <a href="#{{ tag | slugify }}">
        <div class="tags">{{ tag }}</div> 
    </a>
{% endfor %}
```

```liquid
{% comment %}
=======================
The purpose of this snippet is to list all your posts posted with a certain tag.
=======================
{% endcomment %}
{% for tag in tags %}
    <h2 id="{{ tag | slugify }}">{{ tag }}</h2>
    <ul>
     {% for post in site.posts %}
         {% if post.tags contains tag %}
         <li>
         <h3>
         <a href="{{ post.url }}">
         {{ post.title }}
         <small>{{ post.date | date_to_string }}</small>
         </a>
         {% for tag in post.tags %}
             <a class="tag" href="/blog/tag/#{{ tag | slugify }}">{{ tag }}</a>
         {% endfor %}
         </h3>
         </li>
         {% endif %}
     {% endfor %}
    </ul>
{% endfor %}
```


2. Add `<a href="{{ site.baseurl }}/tags">Tag</a>` to `_layouts/default.html`

3. Add below codes to `/style.scss`

```css
.tags {
  display: inline-block;
  border: 1px solid $gray;
  border-radius: .313rem;
  padding: .25rem .625rem;
  margin-right: .125rem;
  margin-bottom: .5rem;
  border-bottom: 2px solid $gray;
}
```