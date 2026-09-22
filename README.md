# Tarapoto public telemetry mirror

Disposable, read-only snapshots of the existing public environmental observations:

- https://cascadecreate.github.io/tarapoto-public-data/6h.json
- https://cascadecreate.github.io/tarapoto-public-data/24h.json
- https://cascadecreate.github.io/tarapoto-public-data/7d.json
- https://cascadecreate.github.io/tarapoto-public-data/30d.json

The workflow checks each https://ecosystem.cascadecreate.com/public-data/tarapoto/{range} page and fetches its existing JSON download. Only these four fixed ranges are supported. All four must pass validation before a Pages deployment replaces the previous snapshots. Unknown fields, annotations, redirects, invalid measurements, and oversized responses stop publication. No source credentials, InfluxDB connection, journal content, or write API is used.

Scheduled at minutes 7, 22, 37 and 52 each hour, and on pushes to main or manual runs. GitHub schedules are best-effort and can be delayed. GitHub may disable scheduled workflows in public repositories after 60 days without repository activity; re-enable the workflow in Actions if that happens. No snapshot commits or accumulating telemetry history are stored in Git.

Check `generatedAt` and observation timestamps on every retrieval. `freshness.ageSeconds` describes freshness at source generation time, not at the time you download this mirror. A failed refresh leaves the previous deployment available; review Actions for failures. Use Actions > Refresh public telemetry > Run workflow for an immediate refresh.

GitHub Pages must use GitHub Actions as its publishing source. The published artifact contains only the four JSON files. The existing application and source endpoints are unchanged.
