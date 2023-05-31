---
title: Create Static Website using Jekyll Chirpy Github Pages
date: 2023-05-05 12:00:00
categories: [ website]
tags: [github, website, jekyll, git]
math: true
mermaid: true
image:
  path: https://jekyllrb.com/img/jekyll-og.png
  alt: Responsive rendering of Chirpy theme on multiple devices.
---
# Create Static Website using Jekyll Chirpy Github Pages

Jekyll is a static site generator that converts plain text into visually appealing static websites and blogs. It is versatile and can be used for various purposes such as documentation sites, blogs, event sites, or any other type of website you prefer. Jekyll is known for its speed, security, user-friendliness, and open-source nature. I personally use it to maintain my open-source documentation site. In this tutorial, we will install and set up Jekyll using the Chirpy theme. We will configure the site, create markdown pages, automate the build process with a GitHub action, and take advantage of the free hosting provided by GitHub Pages.

To create a static website using Jekyll, Chirpy theme, and host it for free on GitHub Pages, follow these steps:

## Install Jekyll
Refer [https://jekyllrb.com/docs/installation/macos/](https://jekyllrb.com/docs/installation/macos/) for updated installation steps

### Step 1: Install Homebrew
Homebrew makes it easy to install development tools on a Mac.

```shell
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```
### Step 2: Install chruby and the latest Ruby with ruby-install
Install chruby and ruby-install with Homebrew:
```shell
brew install chruby ruby-install xz
```
Install the latest stable version of Ruby (supported by Jekyll):
```shell
ruby-install ruby 3.1.3
```
This will take a few minutes, and once it’s done, configure your shell to automatically use chruby:
```shell
echo "source $(brew --prefix)/opt/chruby/share/chruby/chruby.sh" >> ~/.zshrc
echo "source $(brew --prefix)/opt/chruby/share/chruby/auto.sh" >> ~/.zshrc
echo "chruby ruby-3.1.3" >> ~/.zshrc # run 'chruby' to see actual version
```
If you’re using Bash, replace .zshrc with .bash_profile. If you’re not sure, read this external guide to find out which shell you’re using.

Quit and relaunch Terminal, then check that everything is working:
```shell
ruby -v
```
It should show ruby 3.1.3p185 (2022-11-24 revision 1a6b16756e) or a newer version.
### Step 3 Install Jekyll
After installing Ruby with chruby, install the latest Jekyll gem:
```shell
gem install jekyll
```

# Install Chirpy - A text-focused Jekyll theme

Refer https://chirpy.cotes.page/posts/getting-started/#option-1-using-the-chirpy-starter

### Install using the Chirpy Starter


- Sign in to GitHub and browse to Chirpy Starter

https://github.com/cotes2020/chirpy-starter

- Click the button <button>Use this template</button> >  <button> Create a new repository</button>

- Name the new repository USERNAME.github.io, where USERNAME represents your GitHub username.

Then go to the new created repo and copy link to clone the repo

![clone repo image]
```shell
[~]$ git clone https://github.com/ahmdnzm/ahmdnzm.github.io.git
```
Go to the created directory
```shell
[~]$ cd ahmdnzm.github.io/
```
Open VSCode
```shell
[~]$ code .
```
Install Chirpy dependency
```shell
[~]$ bundle
```
Run Chirpy default site
```shell
[~]$ bundle exec jekyll s
```
Goto [http://127.0.0.1:4000/](http://127.0.0.1:4000/) to verify the site is accessible

![jekyll default website]

Customize Chirpy global setting by editing `_config.yml` accordingly

After customizing the `_config,yml`, restart the server to make sure the setting is take effect.

Press <button>crtl-c</button> to stop the website server.

Start the website server again
```shell
[~]$ bundle exec jekyll s
```

Create content

In the `_posts` folder, create a file with the following format **YYYY-MM-DD-TITLE.EXTENSION**

Example
```
2305-05-01-hello-world.md
```
In this file, create a [Front Matter](https://jekyllrb.com/docs/front-matter/) at the top of post
```yaml
---
title: TITLE
date: YYYY-MM-DD HH:MM:SS +/-TTTT
categories: [TOP_CATEGORIE, SUB_CATEGORIE]
tags: [TAG]     # TAG names should always be lowercase
---
```
_example_
```yaml
---
title: Hello Markdown
date: 2023-05-01 12:00:00 +0800
categories: [Website, Markdown]
tags: [website, markdown]     # TAG names should always be lowercase
---
```

For details how to write a post in Chirpy template, can refer Chirpy [Writing a New Post](https://chirpy.cotes.page/posts/write-a-new-post/)

List of [Markdown](/posts/hello-markdown) syntax

After complete creating a post. Next, we need to commit and push the files to Github repository.

git status to check current updated, untracked files
```shell
[~]$ git status
```
Run git add to change the files to staging area
```shell
[~]$ git add .
```
Run git status again to check all files have been included

Run git commit
```shell
[~]$ git commit -m"first commit"
```

Run git push to upload local repository content to Github
```shell
[~]$ git push
```

Then, open Github repository and click `Actions`. Here can see all workflows running in this repo.
```url
https://github.com/ahmdnzm/ahmdnzm.github.io
```
![workflows](/assets/img/23-05-04-workflows.png)
_workflows_

After confirm, all actions completed, can open the url in browser

