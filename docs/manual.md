---
  layout: default
  title: A manual for getting started with pro-theme
---

# Getting started
pro-theme is powered by [Jekyll](https://jekyllrb.com/) so switching is easy! If you are not familiar with building sites using Jekyll, they provide excellent [documentation](https://jekyllrb.com/docs/) and plenty of examples for how to get you started.

## Organizing your site
My personal and professional websites are hosted by Github Pages and use the following general folder structure: 

```txt
/docs
|
|_ _ /_data
|
|_ _ /_posts
|
|_ _ /assets

```

The root folder of the website is usually the `/docs/`. Inside the root, I have three more folders: `/_data`, `/_posts` and `/_assets`.

## Setting up your first website using pro-theme

### Creating the _config.yml

The `_config.yml` file lives in your root directory and includes configuration options for your website. The minimum needed is to specify that you are using a remote theme.

```yml
remote_theme: edsandorf/pro-theme
```

NOTE: The pro-theme is continuously under development. To use pro-theme with your own Github Pages is to fork the repository. This will also let you make more fundamental changes to the style and look of theme to fit your unique needs. 

### Adding index.md

```language-yml
---
layout: landing-page
---

Hello world!

```

By default the theme will use the title and description from Github on all pages. Therefore, you might want to specify separate titles for each page on your site. Note that only the landing page has a description in the banner. To change the title, all you have to do specify the corresponding elements in the YAML at the top of your markdown file. 

```yaml
title: [Title appearing in the banner on the landing page]
description: [A short description appearing below the title]
```

Your folder will now have the following structure

```txt
/docs
|
|_ _ /_data
|
|_ _ /_posts
|
|_ _ /assets
|
|_ _config.yml
|_ index.md

```

##  Extending the website

### Adding multiple pages and navigation

Now that we have built our basic website, let us add an "about" page. We create the following `about.md` and save it to our root folder. 

```txt
---
layout: default
title: About
---

A very good description!

```

Now that we have created a second website, we need to add navigation to our site. This requires us to change two files. First we need to tell pro-theme that we want to add navigation to our site by modifying the `_config.yml` by adding the following option:

```yml
show_navigation: true
```

Second, we need to add a file that can keep track of, and add, links to all of our pages. In the `_data` folder, we will create the file `navigation.yml`:

```yml
- name: Home
  link: /
- name: About
  link: /about.html
```

This file includes the name to be displayed in the navigation bar and the relative link to all pages, excluding pages such as posts, but including our landing page, specified as root: `/`. 

Our folder structure now looks like this: 

```txt
/docs
|
|_ _ /_data
|    |_ navigation.yml
|
|_ _ /_posts
|
|_ _ /assets
|
|_ _config.yml
|_ index.md
|_ about.md

```

### Adding social media icons and links
Many websites make use of links to popular social media platforms. You can add social media icons to the footer of the web site by specifying the following variables in your site's `_config.yml`. 

```yaml
e_mail: [Your e-mail address]
github_handle: [Your Github handle]
linkedin_handle: [Your LinkedIn handle]
twitter_handle: [Your Twitter handle]
```
The icons and links will be added to the footer of the website. At the moment only E-mail, Github, LinkedIn and Twitter are supported.

### Adding Google Analytics
You can add Google Analytics by adding the following to your `_config.yml`.

```yaml
google_analytics: [Your Google Analytics tracking ID]
```

### Adding a to-the-top button
If your website contains a a lot of text, a visitor will have to scroll down to read all of the content. While the navigation bar is sticky and always at the top of the viewport, there are times when you would like to give visitors an easy way to get to the top of the page. To add a simple button taking the visitor to the top, add the following to your `_config.yml`: 

```yml
to_the_top: true
```

### Adding download buttons to the landing page banner


# Adding blog posts to your site

Let us create our first blog post: `2019-12-19-my-first-blog-post.md` and place it in `/_posts/blog`. 

```txt
---
layout: post
title: My first blog post
author: Erlend
category: blog
image: "my-first-post-image.jpg"
excerpt: Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.
---

Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.
```

The YAML for the blog post consists of the `layout`, `title`, `author`, `category`, `image`, and `excerpt`. Only `title` is necessary, but specifying the others avoid reverting to defaults. If you do not specify a post image, pro-theme will default to a stock image. The image is taken from [Pixabay](https://pixabay.com/photos/water-drop-liquid-splash-wet-1761027/) and is distributed under the [Pixabay License](https://pixabay.com/service/license/). 

While creating a sub-directory for blogs is not strictly necessary, I find it helpful to use subdirectories to better keep track of different type of posts, e.g. news or publications. Top tip when using pro-theme: Always specify the category to be the type of post you are writing. We have created a post, but nothing on our website is linking to our new blog post. Pro-theme comes with three different ways of autmatically adding, updating and displaying new blog posts: 1) A post timeline, 2) a feed, and 3) a "card deck". For an example of each type, look at the examples [here]({{ site.url }}/feed.html) 

First, we would create a page (or use an existing one) where we want to display our new blog posts. Let us create an empty page `blog.md`: 

```txt
---
layout: default
title: Blog posts
---


```

and link it to the rest of our pages by modifying `navigation.yml`. 

```yml
- name: Home
  link: /
- name: Blog
  link: /blog.html
- name: About
  link: /about.html
```

## Adding a post timeline
The timeline implemented here is modified from Kirby Turner's [timeline-jekyll-theme](https://github.com/kirbyt/timeline-jekyll-theme). To add the timeline, simply add the following include statement to your site where you want the timeline to be, in our case `blog.md`.

{% raw %}
```markdown
  {% include timeline.html %}
```
{% endraw %}


## Adding a post feed
To add the post feed, simply add the following include statement to your site where you want the timeline to be. 

{% raw %}
```markdown
  {% include feed.html %}
```
{% endraw %}

##  Adding a card deck feed
To add the card deck feed, simply add the following include statement to your site where you want the timeline to be. 

{% raw %}
```markdown
  {% include carddeck.html %}
```
{% endraw %}

## Only listing posts of a certain category
By default, when you include a timeline, feed or card deck to display new posts, all posts in `_posts` will be displayed. However, we can modify the YAML of the site with the feed to include the following:

```yml
category: blog
```

In this example our feed will only include posts with the category "blog". This is why my top tip above was to always specify the category YAML variable for your posts and keep separate posts in separate sub-folders within the `_posts` folder. The trick to making this work is that we are using the current `page.category` to filter all posts based on the `site.categories` variable.

##  Listing only the first few posts
By default, when you include a timeline, feed or card deck to display new posts, all posts in `_posts` will be displayed. Just like you might want to only display posts of a certain type, you might want to only display, e.g. the three newest posts. We can specify the number of posts to display as follows:

```yml
display: 3
```

Now that we have added our first blog post and set up a page with a feed to display all new posts, your folder structure should look something like this. 

```txt
/docs
|
|_ _ /_data
|    |_ navigation.yml
|
|_ _ /_posts
|    |_ _ /blog
|         |_ 2019-12-19-my-first-blog-post.md
|
|_ _ /assets
|    |_ _ /img
|         |_ my-first-post-image.jpg
|
|_ _config.yml
|_ index.md
|_ about.md
|_ blog.md

```

# Adding search functionality to your site
As your website grows, it is useful to add a search function. The search function allows your readers to quickly find relevant posts based on a set of keywords. Pro-theme uses Christian Fei's [Simple-Jekyll-Search](https://github.com/christian-fei/Simple-Jekyll-Search) with a few minor modifications. To add search functionality to our site, we need to add the following to our `_config.yml`:

```yml
show_search_bar: true
```

And we need to create the database to search. Specifically, we need to add `search.json` to our root folder. The `search.json` file contains the following:

<!-- Use raw tag to be able to print liquid tags without the engine processing it -->
{% raw %}
```json
---
layout: null
---
{% assign default-img-url = "https://github.com/edsandorf/pro-theme/blob/master/assets/img/default-img.jpg?raw=true" %}

[
  {% for post in site.posts %}
    {
      "title"    : "{{ post.title | escape }}",
      "author"   : "{{ post.author }}",
      "category" : "{{ post.category }}",
      "tags"     : "{{ post.tags | join: ', ' }}",
      "url"      : "{{ site.baseurl }}{{ post.url }}",
      "date"     : "{{ post.date | date_to_long_string }}",
      "image"    : "{{ site.baseurl }}{% if post.image %}{{ post.image }}{% else %}{{default-img-url}}{% endif %}"
    } {% unless forloop.last %}, {% endunless %}
  {% endfor %}
]


```
{% endraw %}

You should now be able to search all of your sites pages and posts based on title, author, category, tags, url, date and image. 

Your folder and file structure will look something like this: 

```txt
/docs
|
|_ _ /_data
|    |_ navigation.yml
|
|_ _ /_posts
|    |_ _ /blog
|         |_ 2019-12-19-my-first-blog-post.md
|
|_ _ /assets
|    |_ _ /img
|         |_ my-first-post-image.jpg
|
|_ _config.yml
|_ index.md
|_ about.md
|_ blog.md
|_ search.json

```

# Previewing the website locally
