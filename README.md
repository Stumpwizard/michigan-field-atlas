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
- DNR parcel lines and Berrien County's current parcel service.
- Lake, stream and launch name search; topographic, satellite and street basemaps; browser geolocation; shareable views and layer opacity.

## Coverage and interpretation

This is a planning map, not a navigation chart or legal boundary survey. All layers require an internet connection. Loading errors and zoom thresholds are displayed per layer. A successful empty query does not prove absence of features. Source data may lag regulations or site conditions.

Statewide private tax parcel boundaries are not public through Michigan's state open-data portal. The app includes DNR parcels and a clearly labeled Berrien County dataset, plus a link to the state's county parcel-viewer directory. Other counties are not represented as statewide private parcel coverage.

Deep-point locations are historical deepest-contour centroids. They are approximate, not surveyed soundings. NOAA depth units follow the chart; inland DNR depths are feet. Verify current DNR regulations and posted property restrictions. Wildlife project boundaries can contain private inholdings. Public ownership does not imply unrestricted hunting or river access.

## Implementation

Leaflet 1.9.4 and Esri Leaflet 3.0.15 via public CDNs. Feature services are queried read-only in the browser. No credentials, analytics, backend or location storage. Search strings go to the relevant DNR service. Basemap tile providers receive normal tile requests. Geolocation only runs on the user's explicit button press.

Source URLs are in `dist/app.js` and linked in the app. The `.openai/hosting.json` file is local preview configuration and is not required by GitHub Pages.

## Verification

JavaScript syntax checked with Node. Browser preview checks performed with Leaflet after replacing a WebGL-dependent renderer. Live source availability is external and may change.
