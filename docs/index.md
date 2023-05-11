---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

#layout: home
layout: splash
title: "entroserv"
excerpt: "ein Blog über Wissenschaft und Technik"
header:
  overlay_filter: linear-gradient(rgba(100, 150, 255, 0.5), rgba(255, 255, 255, 0.5))
  overlay_image: /assets/images/entroservsplash.jpg 
  actions:
    - label: "YouTube-Kanal Abonnieren"
      url: "https://www.youtube.com/@Tesla42?sub_confirmation=1"
    - label: "Telegram-Kanal Abonnieren"
      url: "https://t.me/entroproject"
    - label: "Telegram-Gruppe Beitreten"
      url: "https://t.me/entroprojectdiscuss"

feature_row:
  - image_path: assets/images/unsplash-gallery-image-1-th.jpg
    alt: "placeholder image 1"
    title: "Projekte"
    excerpt: "real existierende Dinge in Form von Hard- oder Software; in Umsetzung befindlich oder abgeschlossen"
    url: "/Projekte"
    btn_label: "Mehr dazu"
    btn_class: "btn--primary"
  - image_path: /assets/images/unsplash-gallery-image-2-th.jpg
    image_caption: "Image courtesy of [Unsplash](https://unsplash.com/)"
    alt: "placeholder image 2"
    title: "Ideen"
    excerpt: "was _man_ mal machen könnte; wird vmtl. nie fertig"
    url: "/Ideen"
    btn_label: "Mehr dazu"
    btn_class: "btn--primary"
  - image_path: /assets/images/unsplash-gallery-image-3-th.jpg
    title: "Wissen"
    excerpt: "wie die Welt funktioniert; warum die Dinge so sind, wie sie sind"
    url: "/Wissen"
    btn_label: "Mehr dazu"
    btn_class: "btn--primary"


#layout: collection
#entries_layout: grid
#author_profile: true
#classes: wide


#collection: articles

author: Stefan Helmert
---

mein text

{% include feature_row %}

