---
title:  "Welcome to Jekyll!"
date:   2016-06-23 12:02:02
categories: [jekyll]
tags: [jekyll]
leaflet: ok
lat: 37.77896
lng: -122.39790
zoom: 16
icon: xmarker
mlat: 37.778891
mlng: -122.3975811
mpop: Search 'GitHub' on OpenStreetMap!
---

Bonjour! Welcome on my new Jekyll blog!
I'd like to use OpenStreetMap, Leaflet, Mapillary and other mapping toys!
I enjoy home maid food with some craft beers!

Voilà! I use Jekyll `jekyll-uno`.

Posting by time to... well when i can/want/don't forget about it! or in french
Je devrais poster de manière très éparce avoisinant le néan :cake:.

But Hey! this is done with:

``` ruby
print "Hello Ruby! Hi liquid!"
print "Hi, {{ site.title }}, {{ site.description }}"

config => {{ site.title }} by {{ site.author.name }}
to be hosted on => {{ site.url }} about things i like to share!

last render: {{ site.time }}

```

### Plugins

enable emoji on [gh-pages](https://help.github.com/articles/emoji-on-github-pages/)

<p><center>:octocat: :gem: :leaves: :space_invader:</center></p>


Display github gists easily [anywhere](https://github.com/jekyll/jekyll-gist)

{% gist RobyRemzy/803d0d4bed379633d760c64f860e1d14 index.html %}

Diplay map with [leaflet](http://leafletjs.com/)

{% include jk_leaflet.html leaflet_tile="Carto" %}
---

*Possible updates du code ci-dessous: <a href="https://raw.githubusercontent.com/RobyRemzy/robyremzy.github.io/master/_layouts/post.html" target="blank">_layouts/post.html</a>*

{% raw %}
```html
---
layout: default
---
{% if page.leaflet %}
<!-- Loading leaflet -->
<script type="text/javascript" src="{{ "js/leaflet.js" | prepend: site.baseurl }}"></script>
<link rel="stylesheet" href="{{ "css/leaflet.css" | prepend: site.baseurl }}">
{% endif %}

{% if page.mapbox %}
<!-- Loading Mapbox -->
<script src='https://api.tiles.mapbox.com/mapbox-gl-js/v0.22.1/mapbox-gl.js'></script>
<link href='https://api.tiles.mapbox.com/mapbox-gl-js/v0.22.1/mapbox-gl.css' rel='stylesheet' />
{% endif %}

{% if page.mapillary %}
<!-- Loading Mapillary -->
<script src='https://unpkg.com/mapillary-js@1.6.0/dist/mapillary-js.min.js'></script>
<link href='https://unpkg.com/mapillary-js@1.6.0/dist/mapillary-js.min.css' rel='stylesheet' />
{% endif %}

{% if page.mapzen %}
<!-- Loading Mapzen-->
<script src='https://mapzen.com/js/mapzen.js'></script>
<link href='https://mapzen.com/js/mapzen.css' rel="stylesheet" />
{% endif %}
```
{% endraw %}


### About Jekyll

Check out the [Jekyll docs][jekyll] for more info on how to get the most out of Jekyll. File all bugs/feature requests at [Jekyll’s GitHub repo][jekyll-gh]. If you have questions, you can ask them on [Jekyll’s dedicated Help repository][jekyll-help].

[jekyll]:      http://jekyllrb.com
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-help]: https://github.com/jekyll/jekyll-help
