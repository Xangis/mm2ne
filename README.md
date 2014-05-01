mm2ne
=====

Utility to convert the ISO 3166-2 country codes used by MaxMind GeoIP to/from
those used by Natural Earth. This can be useful when using GeoIP in conjunction
with maps created using the Natural Earth dataset.

Contains a LibreOffice Calc document used to generate Python and JavaScript
code.

This was created specifically for use with the "map units" downloads from NE and
integrating them with D3 based on the "Let's Make a Map" tutorial by Mike Bostock
available here:

http://bost.ocks.org/mike/map/

I have not looked at the "countries" download and whether this would be useful
with it, but would be happy to support that if there were any extra/other
effort required.

Nothing has been done to compensate for entries that don't correspond. They have
been left blank.

Typical usage would include something like this JavaScript snippet in a Django
template iterating over a collection of name/color pairs in a "countries" var
and tagging the D3 geometry SVG items with different colors:

    document.write('<style>');
    {% for country in countries %}
    document.write('.geometry.' + geoIPToNaturalEarth['{{country.0}}'] + ' { fill: {{country.1}}; } ');
    {% endfor %}
    document.write('</style>');

If you can improve this or make it more complete I would be happy to take pull
requests. That includes expanding it to other languages, such as Ruby.
