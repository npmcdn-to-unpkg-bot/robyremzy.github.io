---
layout: mapost
title:  "Leaflet inside a post"
date:   2016-08-08 13:37:00
categories: [jekyll]
tags: [jekyll, map]
LtileLayer: https://{s}.tile.thunderforest.com/outdoors/{z}/{x}/{y}.png
lat: 45.84924956447676
lng: 6.705093383789062
zoom: 13
---
Leaflet is pretty cool and easy to use. I manage a simple way to draw a map inside a Jekyll post. I want to keep it step by step and not too fancy but usefull.

<div id="map" style="align:center width: 100%; height: 230px"></div>

## Mod some files
To manage a map like the one above is very straight forward.
First, i want to load the leaflet libs only when a post need it. So let's create a new layout for some post with a leaflet map.

Inside your `_layouts` directory copy the `post.html` and remane it to `mapost.html`. Using the default layout is still ok here, but we need to load the leaflet libs asap. I just droped the `leafet.js` file inside a custom folder `/js` and `leaflet.css` to my `/css` folder. Leaflet come with some default images, you absolutly need <a href='https://github.com/Leaflet/Leaflet/tree/master/dist/images' target='blank'>those</a> and i moved them inside my `/images/carto` folder and tell to leaflet where it is now with `L.Icon.Default.imagePath`.

{% raw %}
```html
---
layout: default
---

<!-- Loading leaflet... -->
  <script type="text/javascript" src="{{ "js/leaflet.js" | prepend: site.baseurl }}"></script>
  <link rel="stylesheet" href="{{ "css/leaflet.css" | prepend: site.baseurl }}">
  <script>
    L.Icon.Default.imagePath = '{{ "images/carto/" | prepend: site.baseurl }}';
  </script>
```
{% endraw %}

Now, check the section:

{% raw %}
```html
<section class="post">
  {{ content }}
</section>
```
{% endraw %}

Ok, we just need to do some happy javascript one time for all. After that we will just have to add some `key:value` into the parmas of our post. So i mod this section like this:

{% raw %}
```html
<section class="post">
  {{ content }}
  <script>
  var map = L.map('map').setView([{{ page.lat }}, {{ page.lng }}], {{ page.zoom }});

  {% if page.LtileLayer %}
  L.tileLayer('{{page.LtileLayer}}', {
    attribution: '&copy; <a href="https://osmlab.github.io/attribution-mark/copyright/?name={{ site.title }}">OpenStreetMap</a> contributors'
  }).addTo(map);
  {% else %}
  L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
    attribution: '&copy; <a href="https://osmlab.github.io/attribution-mark/copyright/?name={{ site.title }}">OpenStreetMap</a> contributors'
  }).addTo(map);
  {% endif %}

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
  </script>
</section>
```
{% endraw %}

I just created some `key:value` layouts. Here, what can be done with that mapost. Inside the `/_posts` directory, create a new markdown post with this options:

{% raw %}
```html
---
layout: mapost #need
title: #need
date: #need
categories: #need
tags: #need
LtileLayer: #can be empty
lat: your map latitude #need
lng: your map longitude #need
zoom: your map zoom #need
icon: custom marker #can be empty
mlat: your marker latitude #can be empty
mlng: your marker longitude #can be empty
mpop: your marker popup #can be empty
---
your post content...

at some point you need to draw the map div with this:

<div id="map" style="align:center width: 100%; height: 230px"></div>

```
{% endraw %}

Now, there is a restriction, we can only have one map div per post. So next time it could be awesome to work on how to master mutliple markers and data representations inside that map div.
