---
title: "Create a Blog With Hugo and Github Pages"
date: 2020-10-13T20:03:40+02:00
draft: false
---

These are the minimal steps I've found to be needed in order to create a blog on GitHub Pages using Hugo (provided Git works already):

1. Install Hugo (just download it from https://github.com/gohugoio/hugo/releases)

2. Create an account on GitHub (if you don't have one)

3. Create a new repository matching your USERNAME.github.io

4. Once you have the repositories created (and hugo in your path):

~~~
#:> mkdir USERNAME.github.io
#:> cd USERNAME.github.io
#:> hugo new site .
~~~

5. Select a Theme from https://themes.gohugo.io/ and then "install" it:

~~~
#:> git init
#:> git submodule add https://github.com/vaga/hugo-theme-m10c.git themes/m10c
~~~

6. Edit the config.toml file to set some parameters (and copy an avatar image into the static folder)

~~~
baseURL = "https://USERNAME.github.io/"
languageCode = "en-us"
title = "Your blog's title"
theme = "m10c" <-- your theme
publishDir = "docs" <-- this one is very important for the last step!

[params]
  author = "Your Name"
  avatar = "your-avatar.png" <-- put it into the 'static' folder
  description = "a little description..."
  menu_item_separator = " - "
  [[params.social]]
    name = "github"
    url = "https://github.com/USERNAME"
  [[params.social]]
    name = "twitter"
    url = "https://twitter.com/USERNAME"
~~~

7. Create a first post

~~~
#:>  hugo new posts/my-first-post.md
#:>  vi content/posts/my-first-post.md <-- add some cool content here!
~~~

8. Run the Hugo local server and validate that the first version of your site is ready
~~~
#:> hugo -D server (with the -D flag you will also see those pages which are still in draft status)
~~~

9. Once you are happy, generate the "public" content (it's going to be in the 'docs' folder):
~~~
#:> hugo
~~~

10. Add everything into version control and perform the first commit and push:

~~~
#:> git add .
#:> git commit -m "Initial commit"
#:> git remote add origin https://github.com/USERNAME/USERNAME.github.io.git
#:> git push origin master
~~~

11. Once everything is in GitHub, go to 'Settings' and under 'GitHub Pages' establish the publishing directory to be the 'docs' folder

These steps are also (more or less) explained here: https://gohugo.io/hosting-and-deployment/hosting-on-github/, although I have introduced some simplification (only one repo needed, and changed publishing directory to the 'docs' folder).

Your blog should now be accessible at https://USERNAME.github.io

Note: git does not commit empty folders and when checking out / cloning the repository the **--recursive** flag needs to be used in order to include the theme submodule (otherwise *hugo* will not work)
