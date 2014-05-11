Makefile
==========

**Action:** When run, this `administrative.makefile` download administrative L0 (countries), L1 (subunits), and cities (places) GIS sources, process them (unzip, crop, filter), to output an elegant composite stack of your target L1 district upon L0 backgrounds, as topojson and WP styled SVG files.

**Output:** 

* 3 administrative layers:
 * countries
 * subdivisions (of the target country)
 * places (with population above a given number):

**Direct command:**

    make -f administrative.makefile ITEM=India WEST=67.0 NORTH=37.5  EAST=99.0 SOUTH=05.0 SELECTOR_L1="admin IN ('INDIA')"

**Parameters:**
* `SELECTOR_L1=`... (SQL selector, default value `"admin IN ('France')"`) selects and keeps L1 administrative areas respecting SQL query.
* `SELECTOR_PLACES=`... (SQL selector, default value `ADM0NAME = '$(ITEM)' AND POP_MAX > '$(POP_MIN)'`) selects and keeps places administrative areas respecting SQL query.
* `SELECTOR_POP_MIN=`... (integer > 0, default value `200000`) selects and keeps places (towns and cities) with populations **above (>)** value. Easier than `SELECTOR_PLACES=`.
Derivated from `ogr2ogr` and `topojson.js`.

[1]: If not there, the download task will automatically download the NaturalEarth `countries`, `subunits`, and `places` archive files totaling about 30MB. This may take from few minutes.

**See also:**
* [Topojson > Command Line References](https://github.com/mbostock/topojson/wiki/Command-Line-Reference) —— to understand current topojson commands or and some more.
* [Topojson > The Distillery](http://herrstucki.github.io/distillery/) —— to visualize your topojson

**Suggestions?** Drop me a suggestion/command line [@hugo_lz](http://twitter.com/hugo_lz)