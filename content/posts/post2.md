---
author: Enoch Yu
title: Building My Blog With Hugo and GitHub
date: 2025-12-14
categories: ["Miscellaneous"]
---

When I first decided to write my blog, I was thrown into bunch of options. I noticed that many of my favorite mathematicians including professor Terence Tao uses *wordpress.com*. However, I noticed that *wordpress.com* would generally give less control over my blog, and must pay to utilize many of the features. There I wondered, *why don't I build one myself?*

## Static Site Generator (SSG)

I had two options of hosting via CMS (Content Management System) or hosting through SSG (Static Site Generator). The main difference is that CMS like Wordpress creates contents dynamically, whereas SSG is simply showing the users a pre-built sites. Here, I realized that most of my blogs would be text based, and does not require dynamic features such as user accounts. Moreover, sites created with SSG is much faster and secure compared to ones created with CMS since no server-side processing is required when accessing.

Now there are multiple Static Site Generators. I personally found Hugo as the ideal SSG since I will have large amounts of posts, and Hugo is known to be fast with Go's performance.

After generating the blog, there must be a hosting platform to actually deploy it. There are multiple options out there, but I chose to use GitHub Pages because it is free and I store my source codes in GitHub anyway. Here is a link to the [sources](https://github.com/enochyu-official/blog) for those who are interested.


## Installing Hugo and Making Repository in GitHub

To install Hugo, please refer to the official [installation guide](https://gohugo.io/installation/). If you are on Windows, copy and paste `winget install Hugo.Hugo.Extended` to your terminal to install. For Mac users with Homebrew, `brew install hugo` will do the job. I don't think I need to include one for Linux users :))

For code editors, I personally use terminal text editor NeoVim due to its speed and flexibility. Here is the official [installation guide](https://neovim.io/) for your interest. However, I believe other code editors are perfectly fine!

If you have Hugo and code editor ready to go, we need to create a repository in GitHub. I personally made a public repository named **blog**. Next, we need to enter following commands in terminal.
```bash
cd BLOG-NAME
git init
git add .
git commit -m "Initial commit"
git remote add origin
git push -u origin main
```
Sometimes, you many need to create a token in GitHub to run the final command. When creating, "repo" section must be checked!

## Theme

As for my theme, to be free from copyright issues, I decided to create my own theme. My Hugo theme was created by merging and reading multiple themes from [Hugo Themes](https://themes.gohugo.io/).

If you wish to implement the theme as a submodule, we must run the following commands in your project.
```bash
git submodule add https://github.com/enochyu-official/EnochBlogTheme themes/EnochBlogTheme
git submodule update --init --recursive
```

To integrate the theme, please update your `hugo.toml`. It should include the following.
```toml
baseURL = 'https://YOUR-GITHUB-ID.github.io/YOUR-REPOSITORY-NAME/'
languageCode = 'en-US'
title = "NAME OF YOUR BLOG"
theme = 'EnochBlogTheme'

[params]
  author = "YOUR NAME"
  avatar = "/images/avatar.png"
  mainSections = ["posts"]
  favicon = "favicon.ico"

[taxonomies]
category = "categories"
tag      = "tags"
```

## Creating Initial Post

To write a post, create a Markdown file `YOUR-POST.md` in `BLOG-NAME/content/post`. For users on Unix-based operating system, `touch YOUR-POST.md` creates the empty file.

In your Markdown file, it should include the following.
```markdown
---
author: YOUR NAME
title: YOUR TITLE
date: DATE
categories: ["YOUR CATEGORY"]
---

YOUR CONTENTS
```

After writing your initial post, the following commands must be ran to update the GitHub repository.
```bash
git add .
git commit -m "YOUR-CHANGE"
git push
```
Next, in GitHub repository, please check "Actions" for the published blog.

Your blog is successfully published!!


{{< comments-note >}}




