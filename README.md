How to crowd source a map of pretty much anything.
==================================================

Using [OSM](https://openstreetmap.org) as a source/store for my (maybe
very niche) Geo Data.

You can follow along with the [presentation
here](http://maptimela.github.io/osm_io/presentation).

### Prerequisites

- Install a text editor which we'll use to edit the code for your web  map. Like toothpaste, there are too many choices, and they are all  pretty much fine. For example https://www.sublimetext.com/3

- Install Python which we'll use as a local server so you can see the  web map your code generates. https://www.python.org/downloads/ (try  the 3.5.1 version, but any version should be fine)  If you get hung up, no worries, just ask. =)

- Set up a GitHub account (https://github.com/) and install git. Git  comes in a graphical flavor for pointing and clicking: https://desktop.github.com/  and a command line flavor: https://git-scm.com/. Either is fine.  We'll use it to publish your map and share the code that powers it. Having trouble? Just ask. =)

Getting Started / Sanity Check
------------------------------

Clone this repository to get started. Don't know what that means? Ask =)

    git clone https://github.com/maptimeLA/osm_io.git

Do you have python installed?
If so, you can start your local webserver to make sure everything is rigged up.

    cd osm_io
    python -m SimpleHTTPServer
    
Don't know if you have python installed? Ask =)
You can install it here. https://www.python.org/downloads/



If that looks like it's working, you should be able to go to your
browser and go to localhost:8000.

Hopefully you'll see "Greatest Map Of Stuff" and an empty map.

If you get this far, help a neighbor who's not there yet.


Let's do it!
------------

### First, use Tag Info to describe the features you want

Go to http://taginfo.openstreetmap.org/ and go find the tags you want. e.g.  `emergency=fire_hydrant`, or
`diet=vegetarian`.

Click on the "overpass turbo" link at the top right.

### [Overpass Turbo](http://overpass-turbo.eu/) is a way to extract data from OSM using tags

Once in overpass, you should see some code on the left. This represents
the features you specified. Try to make sense of it. Adjust the map to
encompass the area you're interested in and **hit "Run"**.

Note: This might take a while (up to 30 seconds). Overpass Turbo stands
up to pretty big queries, but if you are trying to extract a *really*
big data set (e.g. every parking lot in the world) you might have to use
a more [heavy weight tool](http://wiki.openstreetmap.org/wiki/Osmosis).
To speed it up, just extract from a smaller region.

Once you're query is completed, you should see some dots on the map
representing your features. **Click "Export", then "raw data"** to
download the data.

**Note**: Do *not* use the "GeoJson" export. OSM's version of GeoJSON
doesn't play nice with Leaflet.

### Move the downloaded file into your web map project.

Move the file into the base folder this project and rename it to
"export.json".  Make sure it's in just the right spot, otherwise your
webmap won't know how to find it.

If everything went well, you should just be able to reload and see the
extracted OSM data on your map. Click on a point to see all the
associated attributes we fetched.

If you've gotten to this point, look around and see if a neighbor needs
help.

### Extra Curricular: Customize your map

Now you've got a good basemap that you can customize to your liking.

Did you attend an earlier webmap workshop? Apply those skills! Use
CSS/JS/HTML to Show/Hide the attributes you care about using JS. Change
the font to comic sans! Go wild!

