---
layout: boxed
header-image: "https://github.com/edsandorf/pro-theme/blob/master/assets/img/default-img.jpg?raw=true"
title: Getting started with Jekyll-Pro-Theme
subtitle: A short user manual outlining the main features of Jekyll-Pro-Theme
---

# Getting started
Getting started with jekyll-pro-theme is easy. I made the template to work with Github pages using the remote theme feature. I am hosting my personal website on Github and use the theme for my other Github project websites. I am currently not providing a Gem based version of the theme, but if you want, or need, a Gem based version, the easiest would be to clone the jekyll-pro-theme repository and build one yourself. Jekyll-pro-theme is (obviously) powered by [Jekyll](https://jekyllrb.com/). To get started, head over to their website for instructions on how to [get started ](https://jekyllrb.com/docs/) with Jekyll.

## Organizing your site
A good organization of your site makes maintaining it easier. Project websites hosted on Github using Github Pages are usually placed in the `/docs/` folder of your project. I tend to use the following folder structure and I recommend any user of jekyll-pro-theme to do the same. Doing so will make it easier to follow the examples provided here and may avoid issues and bugs with my coding of the theme and its functionality.

```txt
/docs
|
|_ _ /_data
|
|_ _ /_posts
|
|_ _ /assets

```

As stated above, when hosting project websites using Github Pages, the root folder of the website is usually the `/docs/` folder of your project. Inside the root, I have three more folders: `/_data`, `/_posts` and `/assets`. The underscore prefix of the folder names are necessary since we are working with Jekyll. If this is unfamiliar to you, please have a read through their documentation.

## Setting up your first website using pro-theme

### Creating the _config.yml
The first thing we need to do is set up a configuration file. The `_config.yml` file lives in your root directory and includes configuration options for your website. Throughout the rest of this manual, we will cover most, if not all, of the available configuration options. The minimum specification is the theme you are using. For example, the YAML below specifies that you are using jekyll-pro-theme, which is a theme repository hosted by me.

```yml
remote_theme: edsandorf/jekyll-pro-theme
```

It is worth noting that jekyll-pro-theme (and this manual) is under continuous development to meet my needs. I may, at any point, make changes that may or may not break the layout of your website. All changes will be reflected in this manual. However, the safest approach if you wish to use jekyll-pro-theme with your own Github Pages would be to fork or clone the repository. As an added benefit, this will also let you make more fundamental changes to the style and layout of the theme to fit your unique needs. The theme is freely available under a GPL-3 license.

### Adding index.md
Having created our `_config.yml` file, we can now create the first page of our website. To keep with the philosophy of Jekyll, to keep focus on the content, we will write our pages (and posts) using markdown. These markdown files are translated into HTML by the Jekyll engine. Our first page is called `index.md` and it is the landing page of our website. When people type in the web address of your site, this is where they end up. A minimal `index.md` markdown could look like this:

```yml
---
layout: default
landing-page: true
---

Hello world!

```

All pages live in the root directory of your website. In the YAML front matter, we have specified that we are using the default layout (not technically necessary) and that this is our landing page. Explicitly setting the landing page option like this, enables a few extra bells and whistles under the hood of jekyll-pro-theme.

By default the jekyll-pro-theme will use the title and description from Github on all pages. I find this to be a useful feature, however, often you may want to specify separate titles, subtitles and descriptions for each page on your site. Only the landing page (enabled above) has a description in the header. To set a new title or subtitle for our page, we specify the corresponding elements in the YAML front matter at the top of our markdown file as follows:

```yml
title: [Title appearing in the banner on the landing page]
description: [A short description appearing below the title]
```
Your file and folder structure should now look like this:

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

Congratulations, we have now created a minimal website using jekyll-pro-theme. However, a website rarely contains only a single landing page with a simple design. The rest of this manual is dedicated to explaining how you can use jekyll-pro-theme to fit your needs. You can see how the theme is used on my [personal website](https://edsandorf.me) or a [project website](https://obfuscator.edsandorf.me).  

##  Extending the website

### Adding multiple pages and navigation
The first, and most natural, extension to our website is adding another page. Personal and professional websites often have an "about me" page. Let's add one.

```yml
---
layout: default
title: About me
cv_address: "#"
---

{% include polaroid.html image = "https://github.com/edsandorf/pro-theme/blob/master/assets/img/default-img.jpg?raw=true" caption = "Erlend" %}

A very good description!

```
Adding another page to your site is no use if your visitor cannot navigate to it. The first thing we need to do is add `show_navigation: true` to our `_config.yml` file. Second, we need to add a new YAML file that contains the names and relative paths to all pages on our website. We call this file `navigation.yml` and it lives in our `_data` folder. In this example, our `navigation.yml` looks like this:

```yml
- name: Home
  link: /
- name: About
  link: /about.html
```
We see that this file includes the names to be displayed in the navigation bar and the relative paths to all pages, excluding posts (we get back to these in detail later), but including our landing page, specified as root: `/`.

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

We have now successfully added another page to our site and set up navigation to that page.

### Adding social media icons and links
Personally, and professionally, I have a social media presence. With jekyll-pro-theme it is very easy to add social media icons and hyperlinks to your various social media platforms directly in the footer of the website. You simply specify the following variables in your websites `_config.yml` file:

```yaml
e_mail: [Your e-mail address]
github_handle: [Your Github handle]
linkedin_handle: [Your LinkedIn handle]
twitter_handle: [Your Twitter handle]
```
The icons will appear in the footer of the website. The icons are from the [Font Awesome](https://fontawesome.com/) icon set. Currently, only E-mail, Github, LinkedIn and Twitter are supported.

### Adding creator name to the footer
If you want to add your name to the footer as the creator of the website, you can do so by adding the following to your site's YAML:

```yml
creator: Erlend
```

Now, the site will display the text: "Created by Erlend in the footer".

### Adding Google Analytics
Tracking users on your website to see how they interact with your content can be very useful. It is very easy to get started using [Google Analytics](https://analytics.google.com/). To use Google Analytics with jekyll-pro-theme, just add the following to your `_config.yml`.

```yml
google_analytics: [Your Google Analytics tracking ID]
```

### Adding a to-the-top button
If your website contains a a lot of text, a visitor will have to scroll down to read all of the content. While the navigation bar is sticky and always at the top of the viewport, there are times when you would like to give visitors an easy way to get to the top of the page. To add a simple button taking the visitor to the top, add the following to your `_config.yml`:

```yml
to_the_top: true
```

### Adding download buttons to the landing page banner
If you use jekyll-pro-theme for project websites, you can easily download buttons to the landing page header that allow visitors to download the source of your page and project from Github. The landing page in this context is defined by the `landing_page: true` in the YAML front matter for each page, whereas you need to enable the buttons in your `_config.yml` file by adding the following:

```yml
show_downloads: true
```

### Embedding a twitter feed
Jekyll-pro-theme comes with a twitter layout. The layout uses Bootstrap's grid system to place a twitter feed to the right of the page. The feed uses your twitter handle (see above) to get the correct feed from the twitter API. To include a twitter page, you need to set the following two options in your page's YAML front matter:

```yml
---
layout: twitter
tweet-display: 5
---
```

The `layout` argument tells pro-theme that you want a twitter page, and the `tweet-display` is the number of tweets you want to display. I have found 5 to be a good number.

# Adding blog posts to your site
Adding blog posts to our website is different from adding pages to it. Posts are placed in the `_posts` folder (and its subfolders) as opposed to the root folder of your site. In addition, posts follow a specific naming convention where the post name is always preceded by the date in yyyy-mm-dd format. For details on this, and the difference between posts and pages, please see the [Jekyll documentation](https://jekyllrb.com/docs/).

To get started with creating posts, let us create our first blog post: `2019-12-19-my-first-blog-post.md` and place it in `/_posts/blog/`. `/blog/` is a subdirectory of `_/posts/`. While it is not strictly necessary to use subdirectories for different type of posts, I find it useful to organize my site. As your site grows, a proper file structure can be a life saver.

```yml
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
The YAML front matter of the blog post consists of the `layout`, `title`, `author`, `category`, `image`, and `excerpt`. Only `title` is necessary, but specifying the others avoid reverting to defaults. If you do not specify a post image, pro-theme will default to a stock image. The image is taken from [Pixabay](https://pixabay.com/photos/water-drop-liquid-splash-wet-1761027/) and is distributed under the [Pixabay License](https://pixabay.com/service/license/).

When using jekyll-pro-theme, I would encourage you tou always set the category to be the type of post you are writing, e.g. blog, publication or update. We will see later how we can use this to filter how our blog posts show up in feeds.

Now that we have created our blog post and placed it in the correct folder, we need to make sure that visitors to our website can actually find it and read it. Adding navigation to posts is different to adding navigation to pages. Jekyll-pro-theme currently comes with three different ways of automatically adding, updating and displaying new posts: 1) A post timeline, 2) A post feed and 3) a "card deck" of posts. To see what each of these look like, go to the [examples feed page]({{ site.url }}/feed.html).

The first step to set up a post feed is to create a page (or use an existing one) where we want our blog posts to be displayed. For the purposes of this manual, we will create an empty page called `blog.md` and save it in our root directory.

```yml
---
layout: default
title: Blog posts
---
```

Next, we need to link it to the rest of our pages by modifying `navigation.yml`.

```yml
- name: Home
  link: /
- name: Blog
  link: /blog.html
- name: About
  link: /about.html
```

## Adding a post timeline
The timeline implemented here is modified from Kirby Turner's [timeline-jekyll-theme](https://github.com/kirbyt/timeline-jekyll-theme). To add the timeline, simply add the following include statement to your page where you want the timeline to be, in our case `blog.md`.

{% raw %}
```markdown
  {% include timeline.html %}
```
{% endraw %}

The timeline works best when it is allowed to occupy a the full page on its own. If used in combination with the twitter feed, without additional changes to the templates themselves, the timeline tends to look a little squeezed. I recommend not using it in combination with the twitter feed.

## Adding a post feed
To add the post feed, simply add the following include statement to the page where you want the post to be.

{% raw %}
```markdown
  {% include feed.html %}
```
{% endraw %}

##  Adding a card deck feed
To add the card deck feed, simply add the following include statement to the page where you want the card deck feed to be.

{% raw %}
```markdown
  {% include carddeck.html %}
```
{% endraw %}

##  Adding a postcard feed
To add the postcard feed, simply add the following include statement to the page where you want the postcard feed to be.

{% raw %}
```markdown
  {% include carddeck.html %}
```
{% endraw %}

## Only listing posts of a certain category
By default, when you include a timeline, feed or card deck to display new posts, all posts in `_posts` will be displayed. However, we can pass the catory of posts we want to display throught the include variable `category_to_display`. For example: `category_to_display = "blog"`, means that our feed will only include posts with the category "blog". Hopefully, my recommendation above to always specify the category YAML variable for your posts and keep separate posts in separate sub-folders within the `_posts` folder makes sense. The trick to making this work is that we are using the current `page.category` to filter all posts based on the `site.categories` variable.

##  Listing only the first few posts
By default, when you include a timeline, feed or card deck to display new posts, all posts in `_posts` will be displayed. Just like you might want to only display posts of a certain type, you might want to only display, e.g. the three newest posts. We can specify the number of posts to display by adding the following variable to our include statement: `posts_to_display = 3`.

##  Passing a default image to the feed
If you want to add a default image to show for the posts that do not have a post image attached to them, you can pass that through the `image` variable. For example, for the examples used on this website, I have passed the following through the include statement: `image = "https://github.com/edsandorf/pro-theme/blob/master/assets/img/default-img.jpg?raw=true"`.

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
As your website grows, it is useful to add search functionality. The search functionality allows your readers to quickly find relevant posts based on a set of keywords. Pro-theme uses Christian Fei's [Simple-Jekyll-Search](https://github.com/christian-fei/Simple-Jekyll-Search) with a few minor modifications. To add search functionality to our site, we need to add the following to our `_config.yml`:

```yml
show_search_bar: true
```

Next, we need to create the database to search. Specifically, we need to add `search.json` to our root folder. The `search.json` file contains the following:

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

You should now be able to search all of your sites pages and posts based on title, author, category, tags, url, date and image. The first line defines the default image URL. This will use a default image in the search results if no image is provided with the post.

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

# Other layouts and extensions

## Adding a carousel

While opinions about the usefulness of carousels are [split](http://shouldiuseacarousel.com/), jekyll-pro-theme provides two ways of including carousels on your website. The first, and most common, is a simple picture carousel with a small title and caption at the bottom. This carousel is a direct implementation of the [Bootstrap 4 carousel](https://getbootstrap.com/docs/4.0/components/carousel/). To include a carousel, you need to define a JSON file with the content of the carousel and store it in your `_data` folder. For example, the following JSON file is used to create the carousel [here]({{ site.url }}/examples.html).

```JSON
[
  {
    "title": "First slide title",
    "caption": "A drop falling into water.",
    "source": "https://github.com/edsandorf/pro-theme/blob/master/assets/img/default-img.jpg?raw=true"
  },
  {
    "source": "https://github.com/edsandorf/pro-theme/blob/master/assets/img/default-img-02.jpg?raw=true"
  }
]

```

In this example, the source is a hyperlink to the default pictures used by jekyll-pro-theme. In your use case, this is likely to be the relative path to where the pictures you wish to display are stored. Once we have defined our carousel, we need to include it somewhere on our site. We will do this using the now-familiar `include` tag.

{% raw %}
```txt
{% include carousel.html carousel_id = "carousel_example" carousel_data = site.data.carousel-example carousel_in_header = false layout_default = true %}
```
{% endraw %}

Notice that we are passing several variables through the `include` tag. `carousel_id` must be a unique identifier, `carousel_data` tells jekyll-pro-theme where to get the data from, `carousel_in_header` is a boolean equal to true if the carousel is used in the header and `layout_default` is a boolean equal to true if the default Bootstrap layout is used.

It is possible to include the carousel in the header of your site. Currently, you can only include one carousel in the header, however, it can be included on all of your pages. To do so, we need to make three changes: 1) we need to add `carousel_in_header: true` to our page's YAML front matter, 2) set `carousel_in_header: true` in our `include` statement, and 3) save our JSON file in the `_data` folder and name it `carousel-header`. When including the carousel in the header it may also be desirable to use the alternative layout. This can be easily enabled setting `layout_default = false`.


# Previewing the website locally
Before you can preview your page locally, it is important that you have correctly installed a Ruby environment and Jekyll.

First we need to add the following Gemfile to your root folder

```ruby
source "https://rubygems.org"

gem 'jekyll'
gem "html-proofer"
gem 'bootstrap', '~> 4.3.1'

gem 'github-pages'

group :jekyll_plugins do
  gem 'jekyll-sitemap'
  gem 'jekyll-feed'
  gem 'jekyll-seo-tag'
  gem 'jekyll-remote-theme'
end
```

The key part of the this gemfile is `gem 'jekyll-remote-theme'`. Once you have saved the Gemfile, open the terminal and navigate to the root folder. Now we need to install the Gemfile using the command `bundle install`. Once the bundle is installed, you can host the page locally using the command `bundle exec jekyll serve`.

Note: As of Jekyll v3.8.5, there may be a warning, i.e. a yellow piece of text saying: "Invalid theme folder: _sass" when using remote theme locally. This warning does not appear to have any impact on rendering the website locally. This has been logged as an [issue in v3.8](https://github.com/jekyll/jekyll/issues/7630).
