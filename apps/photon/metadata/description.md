

# Photon

**Photon** is an open-source geocoder and search server based on [Elasticsearch](https://www.elastic.co/elasticsearch/) and [OpenStreetMap](https://www.openstreetmap.org/) data.  
It provides an API for forward geocoding (searching locations by name) and reverse geocoding (finding the nearest address from coordinates).

This containerized version runs the official [komoot/photon](https://github.com/komoot/photon) server, packaged for easy deployment.

## Features
- **Forward geocoding**: Search for cities, streets, and points of interest by name.
- **Reverse geocoding**: Retrieve the closest address or location from GPS coordinates.
- **OpenStreetMap data**: Uses OSM extracts for global or regional coverage.
- **Elasticsearch backend**: Fast and scalable search index.
- **Dockerized**: Ready to run in containerized environments.

## Usage
By default, Photon listens on port **2322** inside the container.  
You can map this port to your host (e.g., `8080:2322`) to access the API.

Example request:
```bash
# Forward geocoding
curl "http://localhost:8080/api?q=Berlin"

# Reverse geocoding
curl "http://localhost:8080/reverse?lat=52.3879&lon=13.0582"
```

## Volumes
- `/data`: Stores the Photon index and downloaded OSM data.

## Environment Variables
- `PHOTON_HTTP_PORT` (default: `2322`): Port inside the container where Photon runs.
- `PHOTON_JAVA_OPTS`: Java options for tuning memory or performance.
- `OSM_FILE`: Path to the `.pbf` OpenStreetMap data file to import.

## Notes
- First run will download and import OSM data — this can take time depending on dataset size.
- You can provide your own `.pbf` file in `/data` for a custom region.
- For production, ensure adequate memory allocation for Elasticsearch (e.g., via `PHOTON_JAVA_OPTS=-Xms2g -Xmx2g`).

Source: [Photon Docker GitHub Repository](https://github.com/rtuszik/photon-docker)