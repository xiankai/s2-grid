# s2-grid
Generate a labelled S2 grid from a rectangular selection

Separated from https://github.com/xiankai/pokemongo-tools because of its dependence on v6 of node

# Installation
This assumes basic knowledge of `node`, `npm` or `yarn`.

1. `yarn add s2-grid`
2. `yarn` to install dependencies

This depends on https://github.com/mapbox/node-s2, which is a somewhat abandoned project that does not properly compile on versions of node greater than 6. As a result you may need to downgrade node temporarily to install the dependencies.

If you are sure it will work regardless, you can do `yarn --ignore-engines` to disable the node version check.

# s2.js
This will generate a GeoJSON file for a cell level (12 by default). You should only need to run this once.

Given 2 coordinates to define a rectangular boundary for your desired area, it will produce a GeoJSON file labelled with a grid with A-Z for columns and numbers for rows.

## Input

### coordinates.txt
```
1.2404, 104.0152
1.4714, 103.6318
```

### Usage (For L12 cells by default)
`node s2.js`

### Generate for a different cell level
`node s2.js 10`

### Optionally use a different key (default is `order`) for the GeoJSON property
`node s2.js 10 s2Cell`

# s2-parks.js
Do not use. For archival purposes only.

Originally I made this script to filter gyms if the center of the L20 cell gym they belonged to, was in an OSM park area. However this naive implementation runs very slowly due to a lack of complete support from the S2 library.

For a much better alternative, look at https://github.com/MzHub/osmcoverer
