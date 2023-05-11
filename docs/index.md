---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

#layout: home
layout: splash
titel: "Titel"
excerpt: "ein Blog über Wissenschaft und Technik"
header:
  overlay_filter: linear-gradient(rgba(100, 150, 255, 0.5), rgba(255, 255, 255, 0.5))
  overlay_image: /assets/images/entroservsplash.jpg 
  actions:
    - label: "YouTube-Kanal Abonieren"
      url: "https://www.youtube.com/@Tesla42?sub_confirmation=1"
    - label: "Telegram-Kanal Abonieren"
      url: "https://t.me/entroproject"
    - label: "Telegram-Gruppe Beitreten"
      url: "https://t.me/entroprojectdiscuss"

feature_row:
  - image_path: assets/images/unsplash-gallery-image-1-th.jpg
    alt: "placeholder image 1"
    title: "Placeholder 1"
    excerpt: "This is some sample content that goes here with **Markdown** formatting."
  - image_path: /assets/images/unsplash-gallery-image-2-th.jpg
    image_caption: "Image courtesy of [Unsplash](https://unsplash.com/)"
    alt: "placeholder image 2"
    title: "Placeholder 2"
    excerpt: "This is some sample content that goes here with **Markdown** formatting."
    url: "#test-link"
    btn_label: "Read More"
    btn_class: "btn--primary"
  - image_path: /assets/images/unsplash-gallery-image-3-th.jpg
    title: "Placeholder 3"
    excerpt: "This is some sample content that goes here with **Markdown** formatting."


#layout: collection
#entries_layout: grid
#author_profile: true
#classes: wide


#collection: articles

author: Stefan Helmert
---

mein text

{% include feature_row id="intro" type="center" %}

