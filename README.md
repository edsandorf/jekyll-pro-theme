# The pro-theme theme

pro-theme is a simple and minimalist Jekyll theme to use with GitHub pages. The idea for the theme was borne out of a need to have a uniform look to my professional web site and the project websites of my Github projects. The theme will receive regular updates for the forseeable future. 

The theme is based on [Bootstrap 4](https://getbootstrap.com/) and makes use of the [Font Awesome](https://fontawesome.com/) icon set.

For an example of what the theme looks like, please visit [the website for the theme](https://pro-theme.edsandorf.me). 

# How to use the pro-theme

To use the pro-theme you need to add the following line to your site's `_config.yml`:

```yaml
remote_theme: edsandorf/pro-theme
```

# Customize the pro-theme

##  Changing the title and description of your website
You can override the default title and description (pulled from Github) by specifying the variables in your site's `_config.yml`. 

```yaml
title: [Title appearing in the banner on the landing page]
description: [A short description appearing below the title]
```

Alternatively, you can add separate titles on each page by specifying a YAML section at the top of your markdown file (e.g. index.md).

```markdown
---
title: [Title of the page]
---

This is my page.
```

Note that only the landing page has a description in the banner.

## Adding Google Analytics

You can add Google Analytics by adding the following to your `_config.yml`.

```yaml
google_analytics: [Your Google Analytics tracking ID]
```

##  Add multiple pages and navigation to your site

## Add social media icons and links to the footer
You can add social media icons to the footer of the web site by specifying the following variables in your site's `_config.yml`. 

```yaml
e_mail: [Your e-mail address]
github_handle: [Your Github handle]
linkedin_handle: [Your LinkedIn handle]
twitter_handle: [Your Twitter handle]
```

At the moment only E-mail, Github, LinkedIn and Twitter are supported.

# Previewing your website locally

When building your website it is useful to be able to test your web site locally. To do so:

1. Clone the repository and make a local copy on your machine `git clone https://github.com/edsandorf/pro-theme`
2. Navigate to the folder
3. Run the `install.sh` script in `/script/`. NOTE: You must have Ruby installed on your machine.
4. Check that you have configured `_config.yml` to use the default theme.
5. Your main sites should be in the root folder, while blog posts, news and publications should be in their respective folders.
6. Run `serve.sh` in `/script/`, or use the command line by navigating to your site's root folder and run `bundle exec jekyll serve`.
7. To see your website locally go to: `localhost:4000`

For more information on how to set up your `_config.yml` correctly, please see the [Jekyll docs site](https://jekyllrb.com/docs/).


# Acknowledgements
I have taken inspiration from the clean look of the Cayman theme. If you inspect the source code of the current theme, you will see code chunks and variable names that are similar. 