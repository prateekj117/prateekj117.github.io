---
layout: post
title: Make your own portfolio using Jekyll and Github Developer Pack
image: 2.jpg
date: 2019-07-26 17:27 +0530
tags: [portfolio, Github]
categories: profile
---

In this blog we will be creating a portfolio using Github developer pack and Jekyll.
So, let's first talk about what is Github developer pack and what is jekyll.

> **_NOTE:_**  Where ever curly brackets `{}` are used, it has a variable inside it with actual value corresponding to the name of the variable.

### What is Github developer pack?
{: style="color:#505050; text-align: center;"}
![]({{site.baseurl}}/images/gdpack.png){: .center-image }

It is a program under [**Github Education**](https://education.github.com/) in which Github provides free tools and services to students.
To apply to [Github Developer Pack](https://education.github.com/pack), all you have to do is submit a proof that you are a student at the time 
of applying to the program. And answer a small question: "**How you are planning to use Github?**". After filling the details, you will receive
a mail within five days when your application is approved.

##### Some important things which you get in Github Developer Pack:
* Free credits in AWS Educate
* A free license for Bootstrap Studio
* $50 in platform credit in DigitalOcean for new users (In case you ever plan to learn SSH or sys-admin)
* Unlimited Private Repositories on Github
* A free subscription to all Jetbrains IDEs (I survive because of this.)
* $100 credits free with Microsoft Azure
* A free `.me` domain name with SSL certificate
* Travis CI for private builds
  
  and the list goes on. Now let's talk about Jekyll.

<br/>
### What is Jekyll?
{: style="color:#505050; text-align: center;"}
![]({{site.baseurl}}/images/jekyll.jpg){: .center-image }

[**Jekyll**](https://jekyllrb.com) is a simple, blog aware, static site generator for personal, project, or organization sites. 
In simple words, you won't require writing HTML, CSS or JS to build your static website, just simple Markdown. All you need to do is follow some basic instructions given in the [**docs**](https://jekyllrb.com/docs). 
But don't start just yet, we will be going through everything step by step. I will try to keep this blog self sufficient.

Now let's make a list of steps involved in making the portfolio, and after that go through those steps one by one.
<br/><br/>
**Steps involved in making the website:**
1. Choose a theme
2. Fork the theme, then clone it and run it locally
3. Make it personal and host it
4. Get a `.me` domain
5. Add CNAME
6. Further improvements

<br/>
#### 1. Choose a theme:
For those who are choosy, this is going to be the longest step. I myself took days searching for themes before finally settling on this one.
[Here](https://jekyllthemes.io/free) is the list of free themes by Jekyll. You can also find some extra on [Github](https://github.com/search?q=jekyll+themes). 
And some more [here](https://github.com/search?q=portfolio+theme). These are all the resources I scrapped. All the best. May you find your theme.

#### 2. Clone the theme and run it locally
After choosing a theme, fork it on Github, and then clone it so that the remote `origin` points to the directory on your Github Profile. 
Most repositories of jekyll themes include the documentation for running the jekyll theme locally. If they don't, here are some steps you can follow:
`cd` into your blog directory and run the following commands: 

```console
foo@bar:~$  gem install jekyll bundler
foo@bar:~$  gem install github-pages
foo@bar:~$  bundle install
foo@bar:~$  bundle exec jekyll serve
```
Now in your browser go to: [http://localhost:4000](http://localhost:4000) and bam!!! Here's what your website will look like.

#### 3. Make it personal and host it
Now, go to the `_config.yml` and fill the fields accordingly. Don't forget to edit the field named `baseurl` to `""`. It is used in 
delivering your css and images. I faced an error where my hosted website didn't load it's css and images while everything was working
fine locally. It turns out `baseurl` was the culprit.  
Now, push these changes using:
```console
foo@bar:~$  git push origin master
``` 
Now go to the settings tab of your Repo and rename your Github Jekyll theme Repo to `{your_username}.github.io` and you will see that github will host 
your website to the Url `{your_username}.github.io`.

#### 4. Get a `.me` domain
Go to Github Developer Pack page, and from there, open Namecheap, and activate your Namecheap account using Github, and select a `.me` domain 
of your choice. After selecting a Domain, purchase it for free (Thanks to Github Developer Pack). 

#### 5. Add CNAME
On your Domain Dashboard on Namecheap, then go to `Advanced DNS` 
and add a CNAME record. Something like this:
<br/>
![]({{site.baseurl}}/images/dnsr.png){: .center-image }
<br/>
In Target, replace `prateekj117.github.io` with `{your_username}.github.io`.
After that, in the root directory of your theme project, make a file named `CNAME` and enter the value `{your_domain_name}.me` in it.
Commit the change and again push the commit using:
```console
foo@bar:~$  git push origin master
``` 
After that, you website is hosted on `{your_domain_name}.me`.  Congratulations !!!

#### 6. Further improvements
After all the above steps are done, now you can add an additional functionality of comments if not already integrated in your theme using [Disqus](https://disqus.com/).
And a subscribe button functionality as below which will send updates to the emails subscribed to your blogs using [Mailchimp](https://mailchimp.com/).
For the Mailchimp functionality, you will need to add a RSS feed to your blogs which you can add using [jekyll-feed](https://github.com/jekyll/jekyll-feed).
You should also add `gem 'jekyll-compose', group: [:jekyll_plugins]` to your Gemfile and run:
```console
foo@bar:~$  bundle install
``` 
The use of [jekyll-compose](https://github.com/jekyll/jekyll-compose) is that you can directly add a blog post using command:
```console
foo@bar:~$  bundle exec jekyll post "My New Post"
``` 

An an example, you can also see the code of this website [here](https://github.com/prateekj117/prateekj117.github.io). 

For now, that's all. Do comment if you get any error or get stuck somewhere. Subscribe to the blogs. I will be posting a guide to 
**How to contribute to Open Source** next.
### Happy Coding !!!
{: style="text-align: center;"}
