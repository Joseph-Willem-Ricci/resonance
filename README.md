# RESONANCE

- Using rebuild of Low-tech Magazine's Solar theme with Hugo

## Setup
```
brew install hugo
```
```
pip install git+https://www.github.com/hbldh/hitherdither
```

## Local Development
```
python utils/dither_images.py --directory content/
hugo server --config config/config.toml
```

## Organizing content

Content is organized as [Hugo Page Bundles](https://gohugo.io/content-management/page-bundles/).

That means that each post is a directory which contains: 

* the article (`index.md`)
* the translations (`index.lang.md`)
* the images in the article (`images/`)
* dithered versions of the images (`images/dithers/`)
* comments in various languages (`comments.en.md`) 

Example:

```
how-to-build-a-low-tech-internet/
├── comments.en.md
├── images
│   ├── air-jaldi-epostman.png
│   ├── dithers
│   │   ├── air-jaldi-epostman_dithered.png
│   │   ├── freifunk-wifi-node_dithered.png
│   │   ├── node-air-jaldi-network_dithered.png
│   │   ├── node-spanish-guifi-network_dithered.png
│   │   ├── node-tegola_dithered.png
│   │   ├── sneakernet-on-rails_dithered.png
│   │   ├── tegola-project-low-tech-internet_dithered.png
│   │   ├── wifi-link_dithered.png
│   │   └── wireless-links-spanish-guifi-network_dithered.png
│   ├── freifunk-wifi-node.jpg
│   ├── node-air-jaldi-network.png
│   ├── node-spanish-guifi-network.png
│   ├── node-tegola.jpg
│   ├── sneakernet-on-rails.jpg
│   ├── tegola-project-low-tech-internet.png
│   ├── wifi-link.jpg
│   └── wireless-links-spanish-guifi-network.jpg
├── index.de.md
├── index.en.md
├── index.es.md
└── index.fr.md
```
At least one article is required: `index.md` or `index.lang.md`.

## Formatting articles

The design relies on the following [front matter](https://gohugo.io/content-management/front-matter/) fields:

```
---
title: "How to Build a Low-tech Internet"
date: "2015-10-26"
summary: "If we want the internet to keep working in circumstances where access to energy is more limited, we can learn important lessons from alternative network technologies."
slug: "how-to-build-a-low-tech-internet"
language: "en"
authors: ["Kris De Decker" ]
categories: ["Low-tech Solutions"]
tags: ["ICT" ]
featured_image: "tegola-project-low-tech-internet.png"
draft: false
---
```
 
### Image shortcodes

The design relies on shortcodes for images rather than markdown image tags:

`{{% figure src="yutampo2.png" %}} Una borsa d’acqua calda giapponese detta yutampo, fatta di plastica rigida. Fonte: All About Japan. [https://allabout-japan.com/en/article/6244/](https://allabout-japan.com/en/article/6244/) {{% /figure %}}
`

### Internal links
To link to other articles on the solar website, we use a hugo specific shortcode to call the article folder. This has several advantages: 
1. The url will not break if the article `title` or `date` change, since we are calling the file itself. 
2. When used in a transaltion, the shortcode automatically points to the translated article, if it exists, or defaults to english. 
- _Sytnax:_
```go
[Text]({{< ref "/path-to-folder" >}})
``` 
- _Examples:_
```go
[Donate]({{< ref "/donate" >}})
[here]({{< ref "/posts/power-water-networks/" >}})
```


# Additional utilities

In `utils` there are various utilities to be used before or after site rendering. 

## dithering tool

`dither_images.py` recursively traverses folders and creates dithered versions of the images it finds. These are stored in the same folder as the images in a folder called "dithers".

`python utils/dither_images.py --directory content/`

### Installation & Depedencies

depends on [Pillow](https://pillow.readthedocs.io) and [hitherdither](https://github.com/hbldh/hitherdither)

`pip install Pillow git+https://www.github.com/hbldh/hitherdither`

### Usage

Dither all the images found in the subdirectories of `content` 
`python3 utils/dither_images.py --directory content/`

Colorize the dithers as well based on the LTM categories:
`python3 utils/dither_images.py --directory content/ --colorize`

Run the script with more debug output:
`python3 utils/dither_images.py --directory content/ --colorize --verbose`

Remove all dithered files in the subdirectories of `content`:
`python3 utils/dither_images.py --remove --directory content/`

## build_site.sh

This is a script to build the hugo site and run the various support scripts. It assumes you generate and deploy the site on the same machine.

It can be used in `cron` to make a daily build at 12:15 and log the output. 

`15 12 * * * /bin/bash /path/to/repo/utils/build_site.sh > /path/to/build.log 2>&1`

# Contributions

The Solar v.2 theme was made by

* [Marie Otsuka](https://motsuka.com/)[^1]
* [Roel Roscam Abbing](https://test.roelof.info)[^1]
* [Marie Verdeil](https://verdeil.net/)

With contributions by
* [Erhard Maria Klein](http://www.weitblick.de/)

# Donations

If Low-Tech Magazine or this theme has been useful to your work, please support us by making a one time donation [through Paypal](https://www.paypal.com/paypalme/lowtechmagazine) or a recurring one [through Patreon](https://solar.lowtechmagazine.com/donate/) 

[^1]: Marie and Roel created the [original Pelican theme](https://github.com/lowtechmag/solar) for the first version of https://solar.lowtechmagazine.com
