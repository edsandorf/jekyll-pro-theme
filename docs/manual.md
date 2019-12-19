---
  layout: default
  title: Manual
---

# Table of contents
<!-- %20 or - to include spaces -->
- [Adding blog posts to your site](#Adding-blog-posts-to-your-site)
  - [Adding a post feed](#Adding-a-post-feed)
- [Adding search functionality to your site](#Adding%20search%20functionality%20to%20your%20site)

# Adding blog posts to your site

##  Adding a post timeline
Adding a time line to your website makes it much easier for your readers to keep up to date with your posts. The timeline implemented here is modified from Kirby Turner's [timeline-jekyll-theme](https://github.com/kirbyt/timeline-jekyll-theme). To add the post timeline, simply add the following include statement to your site where you want the timeline to be. 

{% raw %}
```ruby
  {% include timeline.html %}
```
{% endraw %}

Once you have included the timeline on one of your sites, it is automatically updated every time you add a new post to your `_posts` folder. For an example, look at the [blogs]({{ site.url }}/blog.html) example on this website.

## Including a post feed
Alternatively, you can include a post feed. To add the post timeline, simply add the following include statement to your site where you want the timeline to be. 

{% raw %}
```ruby
  {% include feed.html %}
```
{% endraw %}

Once you have included the feed on one of your sites, it is automatically updated every time you add a new post to your `_posts` folder. For an example, look at the [blogs]({{ site.url }}/blog.html) example on this website.


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