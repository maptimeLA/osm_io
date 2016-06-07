How to crowd source a map of pretty much anything.
==================================================

Using [OSM](https://openstreetmap.org) as a source/store for my (maybe
very niche) Geo Data.

Examples
--------

Not all of these are using OSM data, but all these tools are leveraging
their users to build up a collaborative data base around some niche
interest.

#### WeTap

http://wetap.org

"""
WeTap improves awareness, access and use of public drinking
fountains, reducing dependence on single-use plastic, and improves
public health.
"""

*iOS App*

- Find nearby fountains
- Report broken fountains

#### Pinball Map

Pinball enthusiasts share local inventory of pinball games.

http://pinballmap.com/la

#### Open Tree Map

Urban forestry tool.

https://www.opentreemap.org/map/

 - Survey of what trees exist (type, size, health)
 - Promotes local stewardship of urban forestry. (e.g. This tree needs water!)

Why
===

How would you go about making a map of all the in Canada?

- Collect it yourself.
- Get it from someone else.

Alernatives
-----------

### Local Data

You can plot your points using some sort of one-off local data storage.

E.g. You can keep a spreadsheet of latitude/longitude points of Pinball
machines, and details about those machines. When a fellow enthusiast
wants to add to the map they can email you the lat/long and details of
the machine.

```
Hey! There's a great Sopranos machine at Barcade in KoreaTown.

fellow pinball enthusiast,
Jacob "the baller" Spumoni
```

#### Pros

- You are in complete control, no one can change the map underneath you.
- Proprietary. You don't have to give your pinball location data to your
  jerk brother and his dumb copy-cat site "http://pinballmaps.io".

#### Cons

- Starting from scratch, no existing database to go from.
- Same goes for updates - If you want the map to stay up to date - you
  either have to build a custom crowd sourcing interface, or do
  everything yourself. This probably doesn't scale very well.
- Your data dies with you.

### Government Open Data Portals

#### Pros

 - "authoratitive" data ("authoritative" != "accurate")
 - permissive licensing (often public domain)

#### Cons

 - Lots of things aren't available (LA has no city inventory of water fountains)
 - Or if they are "available", sometimes it's not easily usable (LADWP
   usage data is a bunch of PDF's, it will require tons of work to get
   it into a machine readable format so we can use it in an interactive
   map)
 - Separate systems across regions (e.g. Los Angeles publishes their fire
   hydrant data in a different format than New York.)

*Best of both worlds*: Get authoritative data from your local
government, and upload it into OSM! Then you and everyone else can use
it alongside the pre-existing OSM data. e.g. LA Buildings Import.

### Lot's of other options

ESRI, Google, Socrata, etc. offer some of the same features (more or
less). We're focusing on OSM in this workshop becuase it's free (gratis
y libre), and because I'm more familiar with it.


So what do we get from OSM?
---------------------------

Two kinds of data in OSM.

- *Where* the thing is - think latitude,longitude, size.
- *What* the thing is - a building, tree, water fountain, etc.

### "etc."?

This description of "what" the thing is, is accomplished with OSM
"tags".
and can actually be *really* extensive.

An example of the kinds of details you can get from OSM

- It's an organic tea farm.
- It's a bus stop for the number 4 bus.
- It's a cafe, and the hours are M-F: 7am-7pm, Sat-Sun: 11am-5pm. It
  serves vegetarian food.

TagInfo is a great way to explore what tags exist in OSM:
http://taginfo.openstreetmap.org/

## TODO: move this to uploading section?
Tags are pretty free form, but there is a rough consensus on how to use
more popular tags.

You are in fact, free to add your own tags. For example, with WeTap we
used the existing `amenity=drinking_water` tag to drinking fountain
locations, but then we augmented the location with our own tags for our
specific application:

  1. Is it functioning? `wetap:status=working` or `wetap:status=broken`
  2. Has a bottle filling station `wetap:bottle=yes` or `wetap:bottle=no`
  3. Does it have a doggie bowl? `wetap:dog`

In the pursuit of collaboration, you should always prefer to use
existing tags when possible, but don't be afraid to introduce your own
if it's useful to you.

Getting Data Out of OSM
=======================

Big Picture
-----------

[4. My Map.js] <-- [3. My Local Data] <-- [2. Overpass Turbo] <-- [1. OSM]

We are going to copy down just some of the data from OSM into our own
project. There are some nice web based tools that help you get just the
information you need on your map.


Let's do it!
------------

### First, use Tag Info to describe the features you want

Go to http://taginfo.openstreetmap.org/ and find the tags you want. e.g.  `emergency=fire_hydrant`, or
`diet=vegetarian`.

Click on the "overpass turbo" link.

### [Overpass Turbo](http://overpass-turbo.eu/) is a way to extract data from OSM using tags

You should see a blob of text on the left. This represents the features
you want, alongside a map. Adjust the map to encompass the area you're
interested in and hit "Run".

Note: This might take a while (up to 30 secondw). Overpass Turbo stands
up to pretty big queries, but if you are trying to extract a *really*
big data set (e.g. every parking lot in the world) you might have to use
a more [heavy weight tool](http://wiki.openstreetmap.org/wiki/Osmosis).

Once you're query is completed, you should see some dots on the map
representing your features. Click "Export", then GeoJSON to download a
file with all these points.

### Move the downloaded file into your web map project.

Make sure it's in just the right spot, otherwise your webmap won't know
how to find it.

Is your web server still running? Good. If everything went well, you
should just be able to reload and see the extracted OSM data on your
map. Click on a point to see all the associated attributes we fetched.

### Customize your map

Now you've got a good basemap that you can customize to your liking.

Did you attend an earlier webmap workshop? Apply those skills! Use
CSS/JS/HTML to Show/Hide the attributes you care about using JS. Change
the font to comic sans. Or, you can save that for an extra-curricular
lesson.

Licensing
---------

Obligatory Caveat about licensing restrictions - data pulled from OSM is
subject to the "Open Database License (ODbL)".

I'm not a lawyer.

Don't be scared of a license!

This a pretty permissive license. Essentially, you can use this data for
free for whatever purpose you want (personal/profit, good/evil)
provided:

- Somewhere on your map/website/app you say "Contains information from
  OpenStreetMap, which is made available here under the Open Database
  License (ODbL)."

This means that if someone asks you for your map *data*, you may have to
share it with them (yay sharing!).

It's OK to build businesses/for-profit products on top of OSM data.
Apple did it with Apple Maps!

I'm not a lawyer.

Some of the data is pretty sparse.
==================================

Anyone can add data to OSM.

You just need to create an
[account](https://www.openstreetmap.org/user/new) and start editing at
[openstreetmap.org](https://openstreetmap.org). They have an easy-to-use
web app for adding and editing features in the map.

There are also lots of unofficial tools for editing open street map
built by the community.

Apart from the in browser editor, there are two broad categories of
editors:

- Desktop Editors: like [JOSM](http://wiki.openstreetmap.org/wiki/JOSM):
  They require some setup but have some really nice tools if you are
  going to be doing a lot of editing.

Mapping On the Go
-----------------

Take a walk (or bicycle ride) and map what you see using an OSM App on
your mobile device.

### iOS: Go Mapp!

https://itunes.apple.com/us/app/go-map!!/id592990211?mt=8

### Android: Vespucci OSM Editor

https://play.google.com/store/apps/details?id=de.blau.android

Never used it, but it seems similar in functionality, most popular OSM
editor I could find, and has decent reviews 4/5 stars.

### Notes

- This is not an exhaustive survey of apps. There are a bajillion
  others.
- I'm talking about apps for *editing* OSM. Don't be confused by the
  apps for *viewing* OSM.
- These aren't "official" apps created by the OSM project, rather people
  in the greater OSM community have made them. Quality varies. Buyer
  Beware, etc.


