---
title:  "Welcome to Jekyll!"
date:   2016-01-08 15:04:23
categories: [jekyll]
tags: [jekyll]
---
Voilà! J'ai mis en place une landing page avec Jekyll avec un theme très simple `jekyll-uno`. J'ai eut un petit souci pour générer le site. J'ai utilisé la "CLI" `bundle exec jekyll serve` plutôt que `jekyll serve --watch`.

Je devrais poster de manière très éparce avoisinant le néan.

But Hey! this is done with:

``` ruby
def print_hi(name)
  puts "Hi, #{name}"
end
print_hi('Jekyll')

config => {{ site.title }} by {{ site.author.name }}
curently hosted on => {{ site.url }}

```

### Plugins

simple [twitter](https://github.com/kzykbys/JekyllPlugins/blob/master/tweet.rb) should try also this [one](https://github.com/rob-murray/jekyll-twitter-plugin)


enable emoji on [gh-pages](https://help.github.com/articles/emoji-on-github-pages/)
<center>:octocat: :gem: :leaves: :space_invader:</center>



Display github gists easily [anywhere](https://github.com/jekyll/jekyll-gist)

{% gist RobyRemzy/803d0d4bed379633d760c64f860e1d14 index.html %}

<!-- {% gist 803d0d4bed379633d760c64f860e1d14 %} -->


### About Jekyll

Check out the [Jekyll docs][jekyll] for more info on how to get the most out of Jekyll. File all bugs/feature requests at [Jekyll’s GitHub repo][jekyll-gh]. If you have questions, you can ask them on [Jekyll’s dedicated Help repository][jekyll-help].

[jekyll]:      http://jekyllrb.com
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-help]: https://github.com/jekyll/jekyll-help
