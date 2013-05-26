---
layout: post
title: "Blogging with existing Octopress blog on Windows"
date: 2013-05-26 18:07
comments: true
categories: [octopress setup]
---

I mostly use Windows 8 now, but there's no official documentation from Octopress for Windows.

Here are the steps to set everything up. 

##### Prerequisites: There's an existing Octopress repository on your Github Page. If you want to set up a fresh Octopress blog, use the [official documnetnation](http://octopress.org/docs/setup/)


#### 1. Install [RailsInstaller](http://railsinstaller.org/)


#### 2. Install [Python 2.7.5](http://www.python.org/download/releases/2.7.5/). 

**Note:** Octopress is not compatible with Python 3.x and above.

**Note:** Change the system PATH variable to include python executable: 
```
Windows + X -> System -> Advanced system settings -> Advanced -> Environment variables -> System variables -> Path.
Add ;C:\Python27 at the end
```


#### 3. Setup Octopress

``` bash
git clone https://github.com/imathis/octopress.git <your_github_username>.github.io
cd <your_github_username>.github.io
ruby --version # Should be Ruby 1.9.3
rake --version # Should be 0.9.2.2
bundle install
```
	
**Note:** For ```git clone``` I use GitHub-recommended HTTPS instead of SSL.

**Note:** For ```ruby``` and ```rake```. if you don't have the correct version, try to install it using gem. For example, with ```rake``` the current version is ```10.0.4```:

``` bash
gem install rake --version=0.9.2.2
gem list rake
gem uninstall rake --version=10.0.4
```


#### 4. Configure Octopress
	
**Note:** You do **NOT** need to run ```rake setup_github_pages``` since this is an existing Octopress blog.

``` bash
git remote add octopress https://github.com/imathis/octopress
git branch -d master
git config --global credential.helper cache
git config --global credential.helper 'cache --timeout=3600'
```


#### 5. Write your awesome blog, preview and commit frequently to local. 

``` bash
rake generate && rake preview
git add .
git commit -m "Your commit message"
```

**Note:** The preview blog is available at [http://localhost:4000](http://localhost:4000)


#### 6. Push the source to the remote repository

``` bash
git push origin source
```


#### 7. Deploy to your GitHub Page

``` bash
rake generate && rake deploy
```