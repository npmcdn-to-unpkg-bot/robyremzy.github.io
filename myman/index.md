---
layout: page
title: Linux My Man
modified: 2014-07-31T13:23:02.362000-04:00
excerpt: "Instructions on how to install and customize your linux"
image:
  feature: gnu-linux.jpg
  credit: Momez
  creditlink: http://momez.deviantart.com/
---

<section id="table-of-contents" class="toc">
  <header>
    <h3>Overview</h3>
  </header>
<div id="drawer" markdown="1">
*  Auto generated table of contents
{:toc}
</div>
</section><!-- /#table-of-contents -->


SUMMARY
============


# Bash_aliases Exemple #
The file `bash_aliases` have to be store inside your `/home/user/.bash_aliases`
<br>
To understand more about Bash and alias, i suggest you to check this page [Bash Aliases ex on Wikipedia](https://en.wikipedia.org/wiki/Alias_%28command%29)

{% highlight bash %}
#!/bin/bash
# ~/.bash_aliases

## Navigation ##
alias ..='cd ..'
alias ...='cd ../..'
alias ....='cd ../../..'
alias .....='cd ../../../..'
alias ......='cd ../../../../..'
alias .......='cd ../../../../../..'
alias ........='cd ../../../../../../..'

## UBUNTU ##
alias agu='sudo apt-get update'
alias agg='sudo apt-get upgrade'
alias agc='sudo apt-get clean'
alias distro='uname -m && uname -a && lsb_release -a'

alias cp='cp -i'
alias mv='mv -i'

## NETWORK ##
alias wget='wget -c'
alias ping='ping -c 4'
alias myip='dig +short myip.opendns.com @resolver1.opendns.com'

## pass options to free ##
alias meminfo='free -m -l -t'
alias ram='sudo dmidecode | grep -B 1 "Form Factor: DIMM" && print MORE WITH: sudo dmidecode -t memory'

## get top process eating memory ##
alias psmem='ps auxf | sort -nr -k 4'
alias psmem10='ps auxf | sort -nr -k 4 | head -10'

## get top process eating cpu ##
alias pscpu='ps auxf | sort -nr -k 3'
alias pscpu10='ps auxf | sort -nr -k 3 | head -10'

## Get server cpu info ##
alias cpuinfo='lscpu && lscpu | grep bit && cat /proc/cpuinfo'

## get GPU ram on desktop / laptop ##
alias gpumeminfo='lspci | grep "VGA compatible controller" && grep -i --color memory /var/log/Xorg.0.log && lspci -v | grep -A 12 VGA && lshw -enable pci -class display && grep /drivers/ /var/log/Xorg.0.log'

## set some other defaults ##
alias df='df -H'
alias du='du -ch'

## top is atop ##
alias top='atop'

## extract ##
extract () {
  if [ -f "$1" ] ; then
    case "$1" in
      *.tar.bz2)   tar xvjf "$1"    ;;
      *.tar.gz)    tar xvzf "$1"    ;;
      *.tar.xz)    tar xvJf "$1"    ;;
      *.bz2)       bunzip2 "$1"     ;;
      *.rar)       unrar x "$1"     ;;
      *.gz)        gunzip "$1"      ;;
      *.tar)       tar xvf "$1"     ;;
      *.tbz2)      tar xvjf "$1"    ;;
      *.tgz)       tar xvzf "$1"    ;;
      *.zip)       unzip "$1"       ;;
      *.Z)         uncompress "$1"  ;;
      *.7z)        7z x "$1"        ;;
      *.xz)        unxz "$1"        ;;
      *.exe)       cabextract "$1"  ;;
      *)           echo "'$1': unrecognized file compression" ;;
    esac
  else
    echo "'$1' is not a valid file"
  fi
}



{% endhighlight %}





Sparkleshare SSH GitHub
------

To run Sync on GitHub Project install sparkleshare and creat an ssh key as describe here
https://help.github.com/articles/generating-ssh-keys/
[help](http://doc.ubuntu-fr.org/git)

___


Host WebSite on GitHub
------

{% highlight bash %}
$ sudo apt-get install git, rake, gem, ruby-dev, rubygems, nodejs-dev, (jekyll), (ssh-import-id)
{% endhighlight %}

Check the install of  [git](http://doc.ubuntu-fr.org/git) with the creation of  `.gitconfig`

Follow the [jekyll-quick-start](http://jekyllbootstrap.com/usage/jekyll-quick-start.html)

Go to your [https://github.com](https://github.com) and create a new repository named USERNAME.github.com

{% highlight bash %}
$ git clone https://github.com/plusjade/jekyll-bootstrap.git USERNAME.github.com
$ cd USERNAME.github.com
$ git remote set-url origin git@github.com:USERNAME/USERNAME.github.com.git
$ git push origin master
{% endhighlight %}

After GitHub has a couple minutes to do its magic your blog will be publicly available at [http://USERNAME.github.com](http://USERNAME.github.com) or here [http://USERNAME.github.io](http://USERNAME.github.io)

Edit your _config.yml [Help here for the advenced config](http://jekyllrb.com/docs/configuration/) with

{% highlight bash %}
$ git pull
{% endhighlight %}

{% highlight yaml %}
author: notdamhere
  name: here
  email : here@here.here
  github : here
  twitter : mayhere
  feedburner : mayhere
{% endhighlight %}

{% highlight bash %}
$ cd USERNAME.github.com
$ git add .
$ git commit -m "Add new content"
$ git push origin master
{% endhighlight %}

verify your installation is clean by run it localy [see help about Jekyll](https://help.github.com/articles/using-jekyll-with-pages/#installing-jekyll)

{% highlight bash %}
$ gem install jekyll
$ cd USERNAME.github.com
$ jekyll serve
{% endhighlight %}

See it in action at [http://localhost:4000](http://localhost:4000)

To update the git

{% highlight bash %}
$ git add .
$ git commit -m "Add new content"
$ git push origin master
{% endhighlight %}

Check this help:

http://robyremzy.github.io/index.html#start-now

http://jekyllrb.com/docs/installation/

Befor editing a file or document check you are working on the last update by doing a

{% highlight bash %}
$ git pull
{% endhighlight %}

Jekyll Boostrap Themes and Mods

I personaly choose to save some works with the `.zip` found inside the terrific site of [http://mademistakes.com/](http://mademistakes.com/)
* unzip the file
* merge the docs and the files
* mod `config.yml`
* mod some other files [like the pages you want to appears](http://mmistakes.github.io/minimal-mistakes/theme-setup/)

to install all dependencies

{% highlight bash %}
$ sudo apt-get install bundler
$ cd USERNAME.github.com
$ bundle install
$ jekyll serve
{% endhighlight %}

Help yourself to check if everythings don't go side ways there [http://localhost:4000](http://localhost:4000) befor doing a `push origine master`.

An easy way to update posts and pages is to use  [octopress](https://github.com/octopress/octopress) optional here but cool...

{% highlight bash %}
$ sudo gem install octopress --pre
$ octopress `new post "New Post Title" --dir posts`
$ octopress new page new-page/
{% endhighlight %}

It will create a new post in that folder and populate the categories: `YAML` with the same value.
This will create a page at `/new-page/index.md`

