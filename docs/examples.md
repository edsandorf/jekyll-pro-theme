---
layout: default-boxed
header-image: "https://github.com/edsandorf/pro-theme/blob/master/assets/img/default-img.jpg?raw=true"
title: Page element examples
subtitle: A page with examples of how various page elements look with Jekyll-Pro-Theme

carousel_in_header: true
---

![Placeholder1080p](https://dummyimage.com/1920x1080/dcdcdc/fff.jpg)

# Header 1

Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Et sollicitudin ac orci phasellus egestas.

Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Elementum tempus egestas sed sed risus.

> This is a blockquote
>
> Sometimes I say important things, although, let's be honest: It is usually someone else who says the important things.


## Header 2

It is easy to create good looking lists when writing your website using Markdown.

### Unordered list

* List item
* List item
* List item

### Ordered list

1. List item
2. List item
3. List item

### Nested lists

- List item
  - Nested list item
  - Nested list item
    - Nested list item
- List item
- List item


### Header 3

Writing documents in markdown allows the author to include blocks of code with syntax highlighting. 

```r
# This is some R code
x <- 1:5

squared <- function (x) {
  x^2
}

squared(x)
```

#### Header 4

We can also include smaller images throughout the text

![Placeholder480p](https://dummyimage.com/640x480/dcdcdc/fff.jpg)


##### Header 5

The theme is based on [Bootstrap 4](https://getbootstrap.com/) and makes use of the [Font Awesome](https://fontawesome.com/) icon set.


# Including a carousel

{% include carousel.html carousel_id = "carousel_example" carousel_data = site.data.carousel-example carousel_in_header = false layout_default = true %}


