# Michigan Field Atlas

A buildless, mobile-friendly Michigan fishing and hunting map for GitHub Pages.

## Publish

Create a public repository named `michigan-field-atlas`, add these files to its `main` branch, and choose **Settings → Pages → Source → GitHub Actions**. The included workflow publishes `dist/`. No API keys or server are required.

## Features

- DNR trout stream regulation designations and Brook Trout Restoration Areas, with attribute popups.
- DNR boat launch facilities and fishing access points.
- Historical inland lake contours and approximate deepest points (feet).
- NOAA chart display from the MaritimeChartService extension.
- DNR managed land, national forest ownership, wildlife project areas and active Hunting Access Program sites.
- Parcel outlines across all 83 Michigan counties using the public Regrid / Esri Living Atlas raster tile layer, with an 83-county selector. DNR parcel lines and Berrien County’s current parcel attributes are also available.
- Lake, stream and launch name search; topographic, satellite and street basemaps; browser geolocation; shareable views and layer opacity.

## Coverage and interpretation

This is a planning map, not a navigation chart or legal boundary survey. All layers require an internet connection. Loading errors and zoom thresholds are displayed per layer. A successful empty query does not prove absence of features. Source data may lag regulations or site conditions.

Statewide parcel outlines use Regrid USA Nationwide Parcel Boundaries (ArcGIS item a2050b09baff493aa4ad7848ba2fac00), a public raster tile layer covering all US counties. Tiles load at zoom 15–17 and resample at zoom 18–19. No bulk parcel geometry or ownership data is downloaded or redistributed. Parcel taps query separate county ownership services where connected: Barry, Berrien, Eaton, Genesee, Lenawee and Ottawa. Other counties offer an official property-record link. Berrien and Genesee lookups use 2025 source layers. This is partial ownership coverage, not a statewide ownership database. County source dates and completeness vary; recent splits and corrections may lag. Regrid/LOVELAND Technologies attribution and source/license links are displayed. The optional Berrien and DNR feature layers retain their popups. The county selector uses centers calculated from Michigan Geographic Framework county polygons, not parcel boundaries.

Deep-point locations are historical deepest-contour centroids. They are approximate, not surveyed soundings. NOAA depth units follow the chart; inland DNR depths are feet. Verify current DNR regulations and posted property restrictions. Wildlife project boundaries can contain private inholdings. Public ownership does not imply unrestricted hunting or river access.

## Implementation

Leaflet 1.9.4 and Esri Leaflet 3.0.15 via public CDNs. Feature services are queried read-only in the browser. No credentials, analytics, backend or location storage. Search strings go to the relevant DNR service. Basemap tile providers receive normal tile requests. Geolocation only runs on the user's explicit button press.

Source URLs are in `dist/app.js` and linked in the app. The `.openai/hosting.json` file is local preview configuration and is not required by GitHub Pages.

## Verification

JavaScript syntax checked with Node. Browser preview checks performed with Leaflet after replacing a WebGL-dependent renderer. Live source availability is external and may change.

## Stable address

All revisions deploy to https://stumpwizard.github.io/michigan-field-atlas/ from this repository. Preserve the repository name and Pages configuration.

## Owner lookup

`dist/owners.js` lists explicit source fields and county coverage. Clicks at zoom 15+ first resolve the county with Michigan Geographic Framework, then query the county parcel layer at that point. Only owner names, parcel ID, site address and acreage are requested; mailing addresses and tax/valuation fields are excluded. Results highlight the source parcel, show the recorded owner(s), source vintage and direct source/record links. Empty records, unsupported counties and service outages have distinct messages. Requests are aborted when superseded or disabled, preventing stale popups. Ownership names are not bundled, cached or bulk downloaded.
