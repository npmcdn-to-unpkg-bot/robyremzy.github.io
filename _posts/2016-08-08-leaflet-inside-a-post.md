---
title:  "Leaflet inside a Jekyll post"
date:   2016-08-08 13:37:00
categories: [jekyll]
tags: [jekyll, map]
leaflet: Loading
lat: 45.84924956447676
lng: 6.705093383789062
zoom: 12
img: https://robyremzy.github.io/images/tmp/leafkyll.png
---

Leaflet is pretty cool and easy to use. I manage a simple way to render a map inside a Jekyll post. I want to keep it step by step and not too fancy but usefull.

{% include jk_leaflet.html leaflet_tile="Thunderforest" c_layer="cycle" %}

### Mod some files
To manage a map like the one above is very straight forward.
First, i want to load the leaflet libs only when a post need it. So let's mod the post layout.

Open the `post.html` inside your `_layouts` directory. Using the default layout is still ok here, but we need to load the leaflet libs asap. I just droped the `leaflet.js` file inside a custom folder `/js` and `leaflet.css` to my `/css` folder. Leaflet come with some default images, you absolutly need <a href='https://github.com/Leaflet/Leaflet/tree/master/dist/images' target='blank'>those</a> and i moved them inside my `/images/carto` folder so i can tell later to leaflet where they are now with the `L.Icon.Default.imagePath` variable.

the `post.html` look like this at that time look here for potential update: [on GitHub](https://github.com/RobyRemzy/robyremzy.github.io/blob/master/_layouts/post.html)
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
```
{% endraw %}

Now, i have to create a new ready to use template `jk_leaflet.html` inside the `_include` directory. This file will contain many basemap and some `if` liquid tag.

the `jk_leaflet.html` again look here for potential update: [on GitHub](https://github.com/RobyRemzy/robyremzy.github.io/blob/master/_includes/jk_leaflet.html)
{% raw %}
```html
<div id="map" class="leafmap"></div>
<!-- <script src='{{ "js/myscript.js/" | prepend: site.baseurl }}'></script> -->

<script>
{% if page.leaflet %}
L.Icon.Default.imagePath = '{{ "images/carto/" | prepend: site.baseurl }}';

var viirs = 'VIIRS_SNPP_CorrectedReflectance_TrueColor';
// var modis = 'MODIS_Terra_CorrectedReflectance_TrueColor';

var basemap = {
  'OpenStreetMap': L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
    'attribution': '&copy; <a href="https://osmlab.github.io/attribution-mark/copyright/?name={{ site.title }}">OpenStreetMap</a> contributors',
    'minZoom': 2,
    'maxZoom': 19
  }),
  'Thunderforest': L.tileLayer('https://{s}.tile.thunderforest.com/' + '{% if include.tf_layer %}{{ include.tf_layer }}{% else %}outdoors{% endif %}' + '/{z}/{x}/{y}.png', {
    'attribution': 'Maps &copy; <a href="http://www.thunderforest.com/">Thunderforest</a>, &copy; <a href="https://osmlab.github.io/attribution-mark/copyright/?name={{ site.title }}">OpenStreetMap</a> contributors',
    'minZoom': 2,
    'maxZoom': 19
  }),
  'Carto': L.tileLayer('https://cartodb-basemaps-{s}.global.ssl.fastly.net/' + '{% if include.c_layer %}{{ include.c_layer }}{% else %}dark_all{% endif %}' + '/{z}/{x}/{y}.png', {
    'attribution': '&copy; <a href="http://cartodb.com/attributions">CartoDB</a>, &copy; <a href="https://osmlab.github.io/attribution-mark/copyright/?name={{ site.title }}">OpenStreetMap</a> contributors',
    'minZoom': 2,
    'maxZoom': 19
  }),
  'Esri': L.tileLayer('https://server.arcgisonline.com/ArcGIS/rest/services/World_Imagery/MapServer/tile/{z}/{y}/{x}', {
    'attribution': 'Tiles &copy; Esri, &copy; <a href="https://osmlab.github.io/attribution-mark/copyright/?name={{ site.title }}">OpenStreetMap</a> contributors',
    'minZoom': 3,
    'maxZoom': 18
  }),
  'Gibs': L.tileLayer('https://map1.vis.earthdata.nasa.gov/wmts-webmerc/' + viirs + '/default/' + '{{ page.date| date: "%Y-%m-%d" }}' + '/GoogleMapsCompatible_Level9/{z}/{y}/{x}.jpg', {
    'attribution': 'Maps &copy; <a href="http://earthdata.nasa.gov">Gibs</a>, &copy; <a href="https://osmlab.github.io/attribution-mark/copyright/?name={{ site.title }}">OpenStreetMap</a> contributors',
    'minZoom': 3,
    'maxZoom': 9
  })
};

var map = L.map('map', {
  {% if page.lat %}
  'center': [{{ page.lat }}, {{ page.lng }}],
  'zoom': {{ page.zoom }},
	{% else %}
	'center': [40, -25],
	'zoom': 3,
  {% endif %}
  {% if include.leaflet_tile %}
  'layers': [basemap.{{ include.leaflet_tile }}]
  {% else %}
  'layers': [basemap.OpenStreetMap]
  {% endif %}
});
map.scrollWheelZoom.disable();
{% endif %}

{% if page.mlat %}
var marker = L.marker(
  [{{ page.mlat }}, {{ page.mlng }}]
).addTo(map);
{% endif %}

{% if page.icon %}
var xmarker = L.icon({
  iconUrl: '{{ "images/carto/marker.svg" | prepend: site.baseurl }}',
  iconRetinaUrl: '{{ "images/carto/marker.svg" | prepend: site.baseurl }}',
  iconSize: [37, 50],
  iconAnchor: [18.5, 50],
  popupAnchor: [0, -51]
});

var marker = L.marker([{{ page.mlat }}, {{ page.mlng }}], {
  icon: {{ page.icon }}
}).addTo(map);
{% endif %}

{% if page.mpop or page.icon %}
marker.bindPopup("{{ page.mpop }}").openPopup();
{% endif %}
</script>
```
{% endraw %}

Ok, now we just have to add some YAML data `key:value` into our front matter of our post/page.

Here, what can be done with that `jk_leaflet.html`. Inside the `_posts` directory, create a new post with containing front matter:

{% raw %}
```yaml
---
layout: mapost #need
title: #need
date: #need
categories: #need
tags: #need
leaflet: wateveryouwant #can be empty and leaflet will not be load
lat: your map latitude #need
lng: your map longitude #need
zoom: your map zoom #need
icon: custom marker #can be empty
mlat: your marker latitude #can be empty
mlng: your marker longitude #can be empty
mpop: your marker popup #can be empty
---
```
{% endraw %}
{% raw %}
```html
your post content...

at some point you need to render the map with this:

{% include jk_leaflet.html leaflet_tile="Thunderforest" c_layer="cycle" %}
```
{% endraw %}

There is a restriction tho! we can only have one map container per post. So next time it could be awesome to work on how to master mutliple markers and data representations inside that map.
