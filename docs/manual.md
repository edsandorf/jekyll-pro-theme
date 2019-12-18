---
  layout: default
  title: Manual
---

# Table of contents
<!-- %20 or - to include spaces -->
1. [Adding search functionality to your site](#Adding%20search%20functionality%20to%20your%20site)


# Adding search functionality to your site

The search functionality is implemented using Christian Fei's [Simple-Jekyll-Search](https://github.com/christian-fei/Simple-Jekyll-Search). I have made minor modifications to customize the search function to work with this theme. 

To add search functionality we need to add `search.json` to our `/docs/` folder. 

<!-- Use raw tag to be able to print liquid tags without the engine processing it -->
{% raw %}
```json
---
layout: null
---

[
 
  {% for post in site.posts %}
    {
      "title"    : "{{ post.title | escape }}",
      "category" : "{{ post.category }}",
      "tags"     : "{{ post.tags | join: ', ' }}",
      "url"      : "{{ site.baseurl }}{{ post.url }}",
      "date"     : "{{ post.date }}",
      "image"    : "{{ site.baseurl }}/assets/img/{{ post.image }}"
    } {% unless forloop.last %}, {% endunless %}
  {% endfor %}

]

```
{% endraw %}