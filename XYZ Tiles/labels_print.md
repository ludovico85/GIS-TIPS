# Print XYZ labels in QIGS

Solution from https://gis.stackexchange.com/questions/309768/qgis-2-18-quickmapservices-basemap-labels-shrink-when-exported-to-pdf-from-print

The size of the labels is baked into each zoom level. When you increase the resolution, the server provides you a more zoomed-in tile, which has: (1) higher resolution and (2) smaller labels. You can't get (1) without (2).

One workaround is to force the tileserver to give you the zoomed-out version of the tiles. The image will be slightly fuzzy/pixelated but the labels will be larger. There are two ways to do this:

Reduce the dpi of your export. This requires some trial and error to find the highest dpi that will still give you the higher zoom level.

Import the WMS layer as an XYZ tile layer. The basemap will still have a low resolution, but the other elements in your map can have as high a resolution as you want.

First, find and copy the service URL from the layer properties > Information > GetMapURL

Next, open the Browser panel, right click on "XYZ Tiles" > New Connection. Paste the URL you found before. Set the max zoom level, and give the layer a name like "This Basemap max zoom 16". Import the layer from the browser.

It takes some trial and error to find the right maximum zoom level for the scale at which you're making maps.

