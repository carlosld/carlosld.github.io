---
layout: default
title: Carlos León - Tags
---

<!-- Get the tag name for every tag on the site and set them
to the `site_tags` variable. -->
{% capture site_tags %}{% for tag in site.tags %}{{ tag | first }}{% unless forloop.last %},{% endunless %}{% endfor %}{% endcapture %}

<!-- `tag_words` is a sorted array of the tag names. -->
{% assign tag_words = site_tags | split:',' | sort %}

<!-- Build the Page -->

<!-- List of all tags -->
<ul class="tags">
  {% for item in (0..site.tags.size) %}{% unless forloop.last %}
    {% capture this_word %}{{ tag_words[item] }}{% endcapture %}
    <li>
      <a href="#{{ this_word | cgi_escape }}" class="tag">{{ this_word }}
        <span>({{ site.tags[this_word].size }})</span>
      </a>
    </li>
  {% endunless %}{% endfor %}
</ul>

<!-- Posts by Tag -->
<div>
  {% for item in (0..site.tags.size) %}{% unless forloop.last %}
    {% capture this_word %}{{ tag_words[item] }}{% endcapture %}
    <h2 class="tag-header" id="{{ this_word | cgi_escape }}">{{ this_word }}</h2>
    {% for post in site.tags[this_word] %}{% if post.title != null %}
        <ol class="tag-post-list">
            <li class="post-stub post">
                <a class="js-ajax-link" title="{{ post.title }} | Carlos León" href="{{ post.url }}">
                    <h4 class="post-stub-title">{{ post.title }}</h4>

                    <time class="post-stub-date" datetime="{{ post.date }}">Publicado el {{ post.date | date: "%d/%m/%Y" }}</time>

                </a>
            </li>
        </ol>
    {% endif %}{% endfor %}
  {% endunless %}{% endfor %}
</div>