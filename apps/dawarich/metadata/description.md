# Dawarich

**Dawarich** is a self-hosted alternative to Google Timeline (Location History).  
View your trips on a map, import your data (Google Takeout, OwnTracks, GPX/GeoJSON, Strava, EXIF), analyze statistics, and organize journeys.

## Containers
- `dawarich_db`: PostgreSQL **PostGIS** (spatial data storage)
- `dawarich_redis`: Redis (cache & job queue)
- `dawarich_sidekiq`: Sidekiq (background jobs)
- `dawarich_app`: Ruby on Rails web application

## Access
- Default port: **3000**
- Can be exposed via Traefik/Runtipi (configurable in the dashboard)

## Default credentials
- **Email**: `demo@dawarich.app`
- **Password**: `password`  
*Change these immediately after installation.*

## Volumes (app data directory)
- `db`: PostgreSQL data
- `shared`: shared space
- `public`: public assets
- `watched`: watched import folder
- `storage`: application files

## Useful environment variables
- `TIME_ZONE` (e.g. `Europe/Zurich`)
- `APPLICATION_HOSTS` (comma-separated list, **without** protocol)
- `APPLICATION_PROTOCOL` (`http` or `https`)
- For geocoding: `PHOTON_API_USE_HTTPS`, `PHOTON_API_HOST`, `GEOAPIFY_API_KEY` (optional)

## Notes
- Dawarich has used **PostGIS** since v0.23.6.  
- For ARM/AMD64, the PostGIS image used here works fine.  
- Check release notes before upgrading.

Sources: Runtipi documentation (dynamic compose / custom app store) and Dawarich official documentation.