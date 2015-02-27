#OpenHistoricalMap Changes

This document describes the changes made to this instance of iD. *This document was last updated for version 1.7.0.*

## Imagery

On `id.data.load()`->`.imagery()` should be set to our preferred imagery formated as JSON(for schema see [OSMLab](https://github.com/osmlab/editor-imagery-index/blob/gh-pages/schema.json)).

Current imagery:

```
[{
    "name": "MapQuest Open Aerial",
    "type": "tms",
    "template": "http://oatile{switch:1,2,3,4}.mqcdn.com/tiles/1.0.0/sat/{zoom}/{x}/{y}.png",
    "default": true
},
{
    "name": "OpenHistoricalMap",
    "type": "tms",
    "description": "The default OpenHistoricalMap layer.",
    "template": "http://www.openhistoricalmap.org/ohm_tiles/{zoom}/{x}/{y}.png",
    "scaleExtent": [
        0,
        19
    ],
    "terms_url": "http://openhistoricalmap.org/",
    "terms_text": "© OpenHistoricalMap contributors",
    "id": "MAPNIK",
    "default": true
}]
```

## Remove iD.ui.SourceSwitch()

All code in `index.html` related to `SourceSwitch()` has to be removed, currently this is line 247-261.

## Disable Translations
Delete all `array` contents in `data/locales.json`.

## Footer Links

In `js/ui.js` replace the two links pointing to the OpenStreetMap/iD repo.

## API

All API URLs and keys should be replaced in both `js/id/core/connection.js` and `test/spec/core/connection.js`.

## Disabling Mapillary

Disabling Mapillary is done because of legal issues.

Add the following CSS to `css/app.css`:

```
#bar > div.map-controls > div.map-control.map-data-control > div > .filters:nth-child(3) > ul:nth-child(1) {
    display: none;
}

.mapillary-image {
    display: none;
}
```

## Disabling Walkthrough

Walkthrough is broken when no Bing layer exists. Add the following to `css/app.css`:

```
li.walkthrough {
    display: none;
}

.col6.walkthrough {
    display: none;
}

.col6.start {
    width: 100%;
}
```

## Rebranding/Help

This is done in `data/core.yaml` and `dist/locales/en.json`, all links and OpenStreetMap text should be replaced.
