---
title:  "Basic setup with Leaflet and Mapillary"
date:   2016-07-06 22:04:23
categories: [jekyll]
tags: [jekyll]
markdown: markdown
---
I was looking for some Jekyll template to see if doing a little front page for a local shop is doable with ease I mean with a shop cart. I like the static landing page because you can customize them in a short amount of time vs those big CMS, and well you can handle pretty much everything if you care. I will maybe go through the shopping cart later on but something strikes me into those templates. They all use **Google map** for some some pretty locations. I’m more likely to use the <a href='http://leafletjs.com/' target='blank'>Leaflet</a> library in that case. Let’s see how!

## Simplest script

First of all, I don't want to advertise all customers with Google's cookies, so let's drop that G things.

I just assume you already installed <a href='http://jekyllrb.com/' target='blank'>Jekyll</a> or a template.

Inside your `_includes` directory open the `head.html` file and paste the CDN:

```html
<!-- Leaflet -->
<link rel="stylesheet" href="https://npmcdn.com/leaflet@0.7.7/dist/leaflet.css" />
<script src="https://npmcdn.com/leaflet@0.7.7/dist/leaflet.js"></script>
```

Later on you can also build your Jekyll with NPM or Grunt ect...

Now open your `_config.yml` and add those lines:

```yml
#location

#Leaflet tileLayer
LtileLayer: https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png
```

We will use the OpenStreetMap map render (tiles) to show the map layout. There are many tiles providers like MapBox or Mapzen <a href='http://leaflet-extras.github.io/leaflet-providers/preview/' target='blank'>see</a>. My advise: always use the `https` version.

Now you need to fix a center onto that map. We will use the latitude and longitude and then choose a zoom to focus on. Change with your needs.
To help you to find out the lat/lng you can use <a href='http://geojson.io' target='blank'>GeoJson.io</a> but carefull they print down `[lng, lat]` so think to switch the numbers to `[lat, lng]`.

```yml
#map center
lat: 55.594072054186114
lng: 12.985920310020447
zoom: 18
```

It's always nice to pin down with a marker the very point of interest you want to advertise for your customers. Let's be precise and add the lat and lng of this one.

```yml
#map marker
mlat: 55.5937552
mlng: 12.9859105
```

We will also take care of the popup of that marker, who will reveal your shop address. We could fetch the reverse geocode of the lat/lng but sometimes it's too much or too dry. We will control that. You may also want to update <a href='https://www.openstreetmap.org/' target='blank'>OpenStreetMap</a> if there are no info of your shop. It could be a free Open Data and it's getting more and more use by many collectivities, so let's fill that up! <a href='https://www.openstreetmap.org/login?' target='blank'>edit OSM with iD</a>


```yml
#address
address: 5, Köpenhamnsvägen, <br>21743 Malmö, Sweden<br>
```

Another project i like very much is Mapillary a very neat alternative to Google streetview. You can download the App and capture by yourself with your phone or bigger devices. If you have already edited OSM with iD editor you can call inside OSM a new layer to show Mapillary's pictures and find some good one for you!  

![](../../images/tmp/oms_mapi.png)


Or just open <a href='https://www.mapillary.com' target='blank'>mapillary.com</a> and find or updload some to get the picture of your street. We just need now the `photo_key` provided by Mapillary.

![](../../images/tmp/mapillary.png)

Copy that key like this:

```yml
#mapillary.com streetview
mapillary_photokey: K_crJjwx9Jnamm-PmC070w
```

here your map section call `#location` from the `_config.yml`

```yml
#location

#Leaflet tileLayer
LtileLayer: https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png

#map center
lat: 55.594072054186114
lng: 12.985920310020447
zoom: 18

#map marker
mlat: 55.5937552
mlng: 12.9859105

#address
address: 5, Köpenhamnsvägen, <br>21743 Malmö, Sweden<br>

#mapillary.com streetview
mapillary_photokey: K_crJjwx9Jnamm-PmC070w
```

Ok, we've got all the data to properly render everything. We have to do some simple html/javascripts now. To ease this todo i will enter that into the `index.html` but feel free to do has you want/need. So inside your `index.html` jump to the section where you want the map to appear and paste that code:

*NB: Please note the style of the map div, replace style with class with the "value you want" if you use Bootstrap or W3.*

{% raw %}
```html

<!-- Map -->
<div id="map" style="align:center width: 600px; height: 330px"></div>
<script>
var map = L.map('map').setView([{{ site.lat }}, {{ site.lng }}], {{ site.zoom }});
L.tileLayer('{{site.LtileLayer}}', {
	attribution: '&copy; <a href="https://osmlab.github.io/attribution-mark/copyright/?name={{ site.title }}">OpenStreetMap</a> contributors'
}).addTo(map);

var marker = L.marker([{{ site.mlat }}, {{ site.mlng }}]).addTo(map);

marker.bindPopup(
	"<center><b>{{ site.title }}</b><br>" + "{{ site.address }}" +
	"<a target='_blank' href='http://mapillary.com/map/im/{{site.mapillary_photokey}}'>" +
	"<img src='https://d1cuyjsrcm0gby.cloudfront.net/{{site.mapillary_photokey}}/thumb-2048.jpg'  alt='street view' height='180' width='180'></a></center>"
).openPopup();
map.scrollWheelZoom.disable();
</script>
```
{% endraw %}

Time to build your Jekyll with your setup.

```shell
jekyll build && jekyll serve --watch
```
or

```shell
bundle exec jekyll serve
```

You should see something like this div:

![](../../images/tmp/lmj_combo.png "Here you go!"){: width=300px}

So basically you can pan and zoom around the map and when you click on the mapillary pics, you open a new windows with the Mapillary street view of your street.

Here a live example: <a href="https://fitbounds.github.io/fbcheesy42/" target="blank">Fromagerie 4200</a>. I'am still working on this right now but you can check the code on github:

* <a href="https://github.com/fitBounds/fbcheesy42/blob/master/index.html#L109" target="blank">index.html</a>
* <a href="https://github.com/fitBounds/fbcheesy42/blob/master/_includes/head.html#L19" target="blank">head.html</a>
* <a href="https://github.com/fitBounds/fbcheesy42/blob/master/_config.yml#L42" target="blank">config.yml</a>
