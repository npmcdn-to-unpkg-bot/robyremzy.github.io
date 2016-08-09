---
layout: mapost
title:  "Welcome to Jekyll!"
date:   2016-01-08 15:04:23
categories: [jekyll]
tags: [jekyll]
LtileLayer: https://cartodb-basemaps-{s}.global.ssl.fastly.net/dark_all/{z}/{x}/{y}.png
lat: 37.77896
lng: -122.39790
zoom: 16
icon: xmarker
mlat: 37.778891
mlng: -122.3975811
mpop: Search 'GitHub' on OpenStreetMap!
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
to be hosted on => {{ site.url }}

```

### Plugins

enable emoji on [gh-pages](https://help.github.com/articles/emoji-on-github-pages/)

<p><center>:octocat: :gem: :leaves: :space_invader:</center></p>


Display github gists easily [anywhere](https://github.com/jekyll/jekyll-gist)

{% gist RobyRemzy/803d0d4bed379633d760c64f860e1d14 index.html %}

Diplay map with [leaflet](http://leafletjs.com/)

<!-- Map -->
<div id="map" style="align:center width: 100%; height: 230px"></div>

---

*Possible updates du code ci-dessous: <a href="https://github.com/RobyRemzy/robyremzy.github.io/blob/master/_layouts/mapost.html#L14" target="blank">_layouts/mapost.html</a>*

{% raw %}
```js
var map = L.map('map').setView([{{ page.lat }}, {{ page.lng }}], {{ page.zoom }});

L.tileLayer('{{page.LtileLayer}}', {
	attribution: '&copy; <a href="https://osmlab.github.io/attribution-mark/copyright/?name={{ site.title }}">OpenStreetMap</a> contributors'
}).addTo(map);

var xmarker = L.icon({
	iconUrl: '{{ "images/carto/marker.svg" | prepend: site.baseurl }}',
	iconRetinaUrl: '{{ "images/carto/marker.svg" | prepend: site.baseurl }}',
	iconSize: [37, 50],
	iconAnchor: [18.5, 50],
	popupAnchor: [0, -51]
});

{% if page.mlat %}
var marker = L.marker(
	[{{ page.mlat }}, {{ page.mlng }}]
).addTo(map);
{% endif %}

{% if page.icon %}
var marker = L.marker([{{ page.mlat }}, {{ page.mlng }}], {
	icon: {{ page.icon }}
}).addTo(map);
{% endif %}

{% if page.mpop %}
marker.bindPopup("{{ page.mpop }}").openPopup();
{% endif %}

map.scrollWheelZoom.disable();
```
{% endraw %}


### About Jekyll

Check out the [Jekyll docs][jekyll] for more info on how to get the most out of Jekyll. File all bugs/feature requests at [Jekyll’s GitHub repo][jekyll-gh]. If you have questions, you can ask them on [Jekyll’s dedicated Help repository][jekyll-help].

[jekyll]:      http://jekyllrb.com
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-help]: https://github.com/jekyll/jekyll-help
