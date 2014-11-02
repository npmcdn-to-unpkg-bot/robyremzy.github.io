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



INSTALLS ON DEBIAN AND UBUNTU
------

Check your CPU

{% highlight bash %}
$ if [[ $(sed -n '/flags/{/ lm / p;q}' /proc/cpuinfo) ]] ; then echo "Compatible 64 bits" ; else echo "Non-compatible 64 bits" ; fi
$ lscpu | grep bit
$ cat /proc/cpuinfo
{% endhighlight %}

Check RAM

{% highlight bash %}
$ sudo dmidecode | grep -B 1 "Form Factor: DIMM"
$ sudo dmidecode -t memory
{% endhighlight %}

Check Graphique card

{% highlight bash %}
$ lspci -v | grep -A 12 VGA
$ lspci | grep "VGA compatible controller"
$ lshw -enable pci -class display
$ grep /drivers/ /var/log/Xorg.0.log
{% endhighlight %}

Check your distribution

{% highlight bash %}
$ uname -m
$ uname -a
$ lsb_release -a
{% endhighlight %}

Basic need

{% highlight bash %}
$ sudo apt-get install install build-essential sysinfo hardinfo geany links2 markdown sparkleshare gThumb synaptic 
{% endhighlight %}

PACKAGES
------

* [Master PDF](http://code-industry.net/free-pdf-editor.php)
* [PortableSigner](http://sourceforge.net/projects/portablesigner/files/portablesigner/2.0-Release/)
* [BitTorrent Sync Desktop GUI Package](http://www.yeasoft.com/site/projects:btsync-deb:btsync-gui)
* [Atom Editor](https://github.com/atom/atom/releases/latest) or [Atom with Git](https://github.com/atom/atom/blob/master/docs/build-instructions/linux.md)

___

Make you own certificat for Authentification in PDF email and server
======

	http://www.flatmtn.com/article/creating-pkcs12-certificates#SSLCert-1

	https://launchpad.net/ubuntu/precise/+package/cryptonit

	PortableSigner-Generic-2.0.38c0573



___


VirtualBox
------

Install by Oracle deposit, update sources.liste, install virtualbox4.3

{% highlight bash %} 
$ echo "deb http://download.virtualbox.org/virtualbox/debian `lsb_release -sc` contrib" | sudo tee -a /etc/apt/sources.list.d/virtualbox.list && wget -q http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc -O- | sudo apt-key add - && sudo apt-get update && sudo apt-get install virtualbox-4.3
{% endhighlight %}

Make also sure that you are part of the `vboxusers` group.
{% highlight bash %}
$ sudo usermod -G vboxusers -a $USER
{% endhighlight %}

install `DKMS` module?
{% highlight bash %}
$ sudo apt-get install virtualbox-dkms
{% endhighlight %}

Compiles VirtualBox kernel modules each time a new kernel update is available.
{% highlight bash %}
$ sudo /etc/init.d/vboxdrv status
$ sudo /etc/init.d/vboxdrv setup
{% endhighlight %}


___


Ubuntu VPN avec Open VPN
------

[VpnGate](http://www.vpngate.net/en/)

Select an **OpenVPN** '(Windows, Mac,iPhone, Android)' server, download the config file, TCP *(prefer this one)* or UDP. you will get this : `vpngate_xxx.xxx.xx.xx_udp_xxxx.ovpn`

    # geany vpngate_xxx.xxx.xx.xx_udp_xxxx.ovpn

**Cut** the The certificate file of the destination VPN Server in betwin the `<ca></ca>` save it as a `ca.crt` do the same thing for the The client certificate file '(dummy)' inbetwin the `<cert></cert>`
save it a a `ca-user.crt` and finaly for the BEGIN RSA PRIVATE KEY in betwin the `<key></key>` save it as a `ca-key.crt`
So now you `vpngate_xxx.xxx.xx.xx_udp_xxxx.ovpn` is smaller with just the needed info and assuming you got already that

    # sudo apt-get install openvpn network-manager-openvpn

Click Network Connections icon -> VPN Connections -> Configure VPN, then Add -> Import a saved VPN connection (in the scroll down menu), then Create, 
now select your downloaded and chopped OpenVPN config file .ovpn as well as the `ca.crt, ca-user.crt` and the `ca-key.crt`

	username: vpn
	password: vpn

Now save and Close Network Connections.
To run the newly created anonymous VPN, Click again on Network Connections icon -> VPN Connections -> `vpngate_xxx.xxx.xx.xx_udp_xxxx`

___


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

____

GeanyMotion
======

Dependancie with `VirtualBox`

Go to the [Genymotion download page](https://cloud.genymotion.com/page/launchpad/download/).

{% highlight bash %}
$ chmod +x <Genymotion installer path>/genymotion-<version>_<arch>.bin
$ cd <Genymotion installer path>
$ ./genymotion-<version>_<arch>.bin -d <Genymotion installer path>
{% endhighlight %}

Run Genymotion using the following command:
{% highlight bash %}
$ cd <Genymotion installer path>
$ ./genymotion
{% endhighlight %}


_______


SSH connection
======


________


OSM and MapBox
======


>PRO: frontiere, lease, satelitte, temperature alias meteo, integration stylé.



>PERSO: lieux perso, direction, secret spot, 


[osm-bright-ubuntu-quickstart](https://www.mapbox.com/tilemill/docs/guides/osm-bright-ubuntu-quickstart/)


While get throught this steps, i had difficulties to load

{% highlight bash %}
$ psql -U postgres -d osm -f /usr/share/postgresql/9.1/contrib/postgis-1.5/postgis.sql
$ psql -U postgres -d osm -f /usr/share/postgresql/9.1/contrib/postgis-1.5/spatial_ref_sys.sql
{% endhighlight %}

I had to follow [How to install PostGIS 2.0 on Ubuntu 12.04 LTS (precise) from source](http://trac.osgeo.org/postgis/wiki/UsersWikiPostGIS20Ubuntu1204src)

NB: `/usr/share/postgresql/9.1/contrib/postgis-2.0/`

After the install of PostGIS2.0, keep going with:

{% highlight bash %}
$ psql -U postgres -d osm -f /usr/share/postgresql/9.1/contrib/postgis-2.0/postgis.sql
$ psql -U postgres -d osm -f /usr/share/postgresql/9.1/contrib/postgis-2.0/spatial_ref_sys.sql
{% endhighlight %}

futher more becarefull at:

{% highlight bash %}
config["land-high"] = path.join(getcwd(),"/home/USER/WHATEVPATH/shp/land-polygons-split-3857/land_polygons.shp")
config["land-low"] = path.join(getcwd(),"/home/USER/WHATEVPATH/shp/simplified-land-polygons-complete-3857/simplified_land_polygons.shp")
{% endhighlight %}



_To import some project pbf files_


With a PBF file downloaded, you can import it with Imposm. Assuming you downloaded the PBF to your Downloads folder, run the following command in the Terminal:

{% highlight bash %}
$ imposm -U postgres -d osm -m /path/to/osm-bright/imposm-mapping.py \ --read --write --optimize --deploy-production-tables <data.osm.pbf>
{% endhighlight %}


After you have to modify your `/mapbox-osm-bright/configure.py/` 

{% highlight python %}
config["name"] = "NameProject"
{% endhighlight %}

{% highlight bash %}
cd ~/Downloads/mapbox-osm-bright-*
./make.py
{% endhighlight %}


**To import some layers shp files**

Basicly it's all about adding some layers:

Importing some point with lat/long and more datas inside a project:

[https://www.mapbox.com/tilemill/docs/crashcourse/styling/](https://www.mapbox.com/tilemill/docs/crashcourse/styling/)

Importing some bundarys or ShapeFiles `shp` ex:for Texas 

[http://txsdc.utsa.edu/Data/Tiger/2009/CountyShapeFiles.aspx](http://txsdc.utsa.edu/Data/Tiger/2009/CountyShapeFiles.aspx))


	https://github.com/Citytracking/CountyOSM/blob/master/counties-48-texas.sh
	https://github.com/Leaflet/Leaflet
	http://geojsonlint.com/
	https://github.com/mapbox/geojson.io


_____




