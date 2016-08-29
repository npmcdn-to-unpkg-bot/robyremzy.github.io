---
title:  "Share Mapillary captures on Jekyll"
date:   2016-08-26 19:42:42
categories: [map]
tags: [map, mapillary]
img: https://robyremzy.github.io/images/tmp/jekyllary.png
mapillary: ok
mapbox: ok
mlat: 48.84276533352345
mlng: 2.4358856678009033
zoom: 15
mly_pkey: jwT0dFh8hN5PpGakkiWfmg
---

Capture the world around us involve some fun aspects and sometime it's an adventure worth sharing. To explain how we captured or just share a street level environment. Find here how to include Mapillary into a static web blog.

![Jekyllary]({{ "images/tmp/jekyllary.png" | prepend: site.baseurl }})
include mapillary photo key, into your Jekyll post with mapillary-js
{: style="text-align: center;"}

Static web site like Jekyll is often used to quickly support and share our posts, like on GitHub or on your own server with basically zero knowledge in web coding. Jekyll's contributors have already made some templates and occasionally with Google map ready to use. Of course, we can customize that with Leaflet or Mapbox too if we wish but here we will focus on the Mapillary part. Other blog framework should keep the same approche with some adjustments. Jekyll is famous for its easy [liquid templating](https://shopify.github.io/liquid/) and YAML data [front matter](https://jekyllrb.com/docs/frontmatter/).

### First things to setup
To use the Mapillary API you need to [register an application](https://www.mapillary.com/app/settings/developers) into your Mapillary account. We will use the **Client ID** later.

![appmapillary]({{ "images/tmp/regappmapi.png" | prepend: site.baseurl }})
every field are required and the domain should to be correct.
{: style="text-align: center;"}

Now to embed street level imagery we will use [mapillary-js](https://github.com/mapillary/mapillary-js). The whole mapillary-js is available via CDN here hosted on "npmcdn". To keep it simple we will use that solution but it's possible to use it with "NPM" as well. We may by time to time check back on the version number and update the CDN.

It will be also a good idea to load mapillary-js only when our post or article need it. To do that we have to edit our `post.html` inside the `_layouts` directory. Edit like the example under, just after the layout front matter. We have to basically copy the CDN script and add an `if` tag condition relative to the **key: value** of `mapillary: ok` inside the post/page front matter.

{% raw %}
```html
---
layout: default
---
{% if page.mapillary %}
<!-- Loading Mapillary -->
<script src='https://npmcdn.com/mapillary-js@1.6.0/dist/mapillary-js.min.js'></script>
<link href='https://npmcdn.com/mapillary-js@1.6.0/dist/mapillary-js.min.css' rel='stylesheet' />
{% endif %}
```
{% endraw %}

Now, mapillary-js will be loaded everytime we will add `mapillary: ok` to the post front matter. We can just paste some html inside our post content to render Mapillary.

{% raw %}
```html
---
title:  "Mapillary inside a post"
date:   2016-06-23 13:37:00
categories: [mapillary]
tags: [jekyll, mapillary]
mapillary: ok
---

A Mapillary blog post...

<div id='mly' style='width: 640px; height: 480px;'></div>

<script>
  var mly = new Mapillary.Viewer(
    'mly',
    '<your client id>',
    '<your photo id for initializing the viewer>',
  );
</script>

some other stuff going on here!

```
{% endraw %}

### Post enhancement
Things could be a little tiresome after a while. To keep some readability, our code should blend as much as possible inside the post. We can drop the client id straight into the the code but why not paste it inside the `_config.yml` file. With Jekyll we can use also the liquide object **\{** **\{** **include** **\}** **\}** to call some file from the `_includes` directory.

Create a new file `jk_mapillary.html` inside `_includes` and copy/paste maybe customize the content under.

{% raw %}
```html
{% if page.mapillary %}
<div id="mly" style='width: 640px; height: 480px;'></div>
{% endif %}>

<script>
{% if page.mapillary %}
var mly = new Mapillary.Viewer(
  'mly',
  '{{ site.mapillary_id }}',
  '{{ include.mly_pkey }}',
  {
    // see options: http://mapillary.github.io/mapillary-js/interfaces/ivieweroptions.html
    "cover": true,
    "renderMode": Mapillary.RenderMode.Fill,
    "basePanoramaSize": Mapillary.ImageSize.Size2048,
    "baseImageSize": Mapillary.ImageSize.Size320,
    "maxImageSize": Mapillary.ImageSize.Size2048,
  }
);
{% endif %}
</script>
```
{% endraw %}

Few notes here:

- **\{** **\{** **page.mapillary** **\}** **\}** will check the key value of `mapillary` inside our blog post/page front matter.
- **\{** **\{** **site.mapillary_id** **\}** **\}** will check the key value of `mapillary_id` inside `_config.yml`.
- **\{** **\{** **include.mly_pkey** **\}** **\}** is special, it's an option of a liquid include object, here our *Photo Key* aka **mly_pkey** this time as a needed option when including the Mapillary tag into our post.

We need to include our Client ID inside `_config.yml`. Replace the `mapillary_id:` value with your new app **Client ID**.

```yml
mapillary_id: 4m4p1ll4ry1Dk3y42
```

Don't forget to include `mapillary: ok` or any other value you want, into your post/page front matter.

We can find the photo key of our choice on Mapillary map.

![photokey]({{ "images/tmp/photo_key.png" | prepend: site.baseurl }})
copy the photo key
{: style="text-align: center;"}

Now, inside our post content we have to drop our Mapillary liquide tag with the photo key option where it should be render inside our post.

{% raw %}
```js
---
title:  "Mapillary inside a post"
date:   2016-06-23 13:37:00
categories: [mapillary]
tags: [jekyll, mapillary]
mapillary: ok
---

A Mapillary blog post...

{% include jk_mapillary.html mly_pkey='bXINQNk4Mrud8NrAZrM_ew' %}

some other stuff going on here!
```
{% endraw %}


### Final render
These last days I was <s>capturing</s> mapillaring by feet with my phone, a castle in France ["Le château de Vincennes"](https://en.wikipedia.org/wiki/Ch%C3%A2teau_de_Vincennes). In fact when people saw me with my phone like this! They actually throught i was capturing stuff but not mapping!

{% include jk_mapillary.html mly_pkey='jwT0dFh8hN5PpGakkiWfmg' %}
See more street level captures [nearby on Mapillary](https://www.mapillary.com/app/?lat={{ page.mlat }}&lng={{ page.mlng }}&z=15)
{: style="text-align: center;"}

If you find this nice to do or even interesting you can check/share on how to mix it with a map with something of your taste...

- [Gist: Mapbox GL JS Map with Mapillary Request](http://bl.ocks.org/RobyRemzy/raw/d1480060fd9492796b8529b357cb2426/)
- [GitHub: more mapillary examples](https://github.com/mapillary/mapillary-js-examples)

{% include jk_mapbox.html mb_tile='mapbox://styles/mapbox/bright-v9' %}
Here, Mapbox simply calling the Photo Key to set the center of the map.
{: style="text-align: center;"}

**Thanks To:** [@RatZillaS](https://twitter.com/RatZillaS) and [@zimmy](https://twitter.com/JLZIMMERMANN) for the first and seconde picture from their work on Mapillary and for their inspirations.
