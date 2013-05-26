---
layout: post
title: "Blogging with existing Octopress blog on Windows"
date: 2013-05-26 18:07
comments: true
categories: [octopress setup]
---

I mostly use Windows 8 now, but there's no official documentation from Octopress for Windows.

Here are the steps to set everything up. 

#### Prerequisites: There's an existing Octopress repository on your Github Page. If you want to set up a fresh Octopress blog, use the [official documnetnation](http://octopress.org/docs/setup/)

1. Install and run [RailsInstaller](http://railsinstaller.org/)

Note: Default folder is *C:\Sites*. You may want to use another directory. For example, I'm using *C:\Users\Hung\Github* for all my Github repositories
```
cd C:\Users\Hung\Github
```

2. Setup Octopress

Note: For ```git clone``` I use the GitHub-recommended HTTPS instead of SSL.
```
git clone https://github.com/imathis/octopress.git <your_github_username>.github.io
cd <your_github_username>.github.io
ruby --version # Should be Ruby 1.9.3
rake --version # Should be 0.9.2.2
bundle install
```

3. Configure Octopress
Since this is an existing Octopress blog, you do **NOT** need to run ```rake setup_github_pages```
```
git remote add octopress https://github.com/imathis/octopress
git branch -d master
git config --global credential.helper cache
git config --global credential.helper 'cache --timeout=3600'
```

4. Write your awesome blog and then commit
```
git add .
git commit -m "Your commit message"
```

5. Deploy
```
rake generate && rake deploy
```