# intensidad_espiras_VLC — Hourly intensity by measurement point / loop (València)

Historical archive of **traffic intensity by measurement point (loops /
espiras)** for València, from the municipal open-data portal (now
decommissioned). This is the long loop-sensor series, complementary to the
spot capture in `espiras_2020_VLC`.

## Source

- **Publisher:** València City Council — *mapas.valencia.es* portal
  (`lanzadera/opendata/.../tra_espiras_p`).
- Decommissioned service; this repository is the backup copy of the history.

> Note: the original files are named with the `trafico_*` prefix (a quirk of the
> collector's naming), but the payload is the measurement-point hourly intensity
> (`idpm`/`ih`), **not** the per-segment intensity (`idtramo`/`lectura`) of
> `traffic_VLC`.

## Period

- **1499 days** between **2015-02-06** and **2024-10-24**.

## Repository layout

- One ZIP file per day: `DD-MM-YYYY.zip`, holding that day's snapshots.
- One commit ("new day") per day, dated with the real date of the data.

## Format and fields

The format changed over time:

### 2015–2019 — GeoJSON

GeoJSON `FeatureCollection` in **CRS84 / WGS84** (longitude-latitude). Each
*Feature* is a measurement point (`Point` geometry) with properties:

| Field                 | Meaning                                              |
|-----------------------|------------------------------------------------------|
| `idpm`                | Measurement-point identifier.                        |
| `ih`                  | Hourly intensity (vehicles/hour).                    |
| `angulo`              | Sensor orientation / angle.                          |
| `fecha_actualizacion` | Date of the last update.                             |
| `hora_actualizacion`  | Time of the last update.                             |

### 2020–2024 — CSV

CSV with `;` separator. Columns:
`X;Y;angulo;fecha_actualizacion;hora_actualizacion;idpm;ih`

| Column                | Meaning                                              |
|-----------------------|------------------------------------------------------|
| `X`, `Y`              | Coordinates in **UTM EPSG:25830**.                   |
| `angulo`              | Sensor orientation / angle.                          |
| `fecha_actualizacion` | Date of the last update.                             |
| `hora_actualizacion`  | Time of the last update.                             |
| `idpm`                | Measurement-point identifier.                        |
| `ih`                  | Hourly intensity (vehicles/hour).                    |
