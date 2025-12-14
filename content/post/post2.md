---
author: Enoch Yu
title: Building My Blog With Hugo and GitHub
date: 2025-12-12
categories: ["Miscellaneous"]
---

When I first decided to write my blog, I was thrown into bunch of options. I noticed that many of my favorite mathematicians including professor Terence Tao uses *wordpress.com*. However, I noticed that *wordpress.com* would generally give less control over my blog, and must pay to utilize many of the features. There I wondered, *why don't I build one myself?*

## Static Site Generator (SSG)

I had two options of hosting via CMS (Content Management System) or SSG (Static Site Generator). The main difference is that CMS like Wordpress creates contents dynamically, whereas SSG is simply showing the users a pre-built sites. Here, I realized that most of my blogs would be text based, and does not require dynamic features such as user accounts. Moreover, sites created with SSG is much faster and secure compared to ones rated with CMS since no server-side processing is required when accessing.

Now there are multiple Static Site Generators. I personally found Hugo as the ideal SSG since I will have large amounts of posts, and Hugo is known to be fast with Go's performace.

After generating the blog, there must be a hostig platform to actually deploy it. There are multiple options out there, but I chose to use GitHub Pages because it is free and I store my source codes in GitHub anyway. Here is a link to the [sources](https://github.com/enochyu-official/blog) for those who are interested.


## Installing Hugo and Making Repository in GitHub

To install Hugo, please refer to the official [installation guide](https://gohugo.io/installation/). If you are on Windows, copy and paste `winget install Hugo.Hugo.Extended` to your terminal to install. For Mac users with Homebrew, `brew install hugo` will do the job. I don't think I need to include one for Linux users :))

For code editors, I personally use terminal text editor Neovim due to its speed and flexibility. Here is the official [installation guide](https://neovim.io/) for your interest. However, I believe other code editors are perfectly fine!

If you have Hugo and code editor ready to go, we need to create a repository in GitHub.

## Choosing Theme

To avoid headaches from css and javascript, I decided to use a theme from [Hugo Themes](https://themes.gohugo.io/). There are great themes in the link to make our life easier, so I chose a theme called [Stack](https://themes.gohugo.io/themes/hugo-theme-stack/).

To implement the theme as a submodule, we must run the following commands.
```
git submodule add https://github.com/CaiJimmy/hugo-theme-stack/ themes/hugo-theme-stack
git submodule update --init --recursive
```

## My Custom Codes

