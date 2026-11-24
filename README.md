# Fuel Consumption Pattern Recognition — Dataset

Data recorded for the B.Sc. thesis *Development of a Recognition Model for Vehicle Fuel Consumption Pattern in a Controlled Spatiotemporal Environment* (Abayomi, O. S., Department of Computer Engineering, Obafemi Awolowo University, Ile-Ife, 2026).

Vehicle: 2014 Lexus RX350 (petrol, V6). Route: Road 1, Obafemi Awolowo University campus, Ile-Ife, Nigeria. Logger: ESP32 + SN65HVD230 + NEO-6M (see the code repository: https://github.com/timibacco/fuel-pattern-recognition-code).

## Layout
| Path | Contents |
|---|---|
| `sessions/<session>/timeseries.csv` | One row every 100 ms: GPS position, altitude, speed and fix flag; polled engine speed, vehicle speed and mass air flow; validity flags (thesis Table 3.4). |
| `sessions/<session>/raw_can.csv` | Every CAN frame received: timestamp, identifier, DLC and data bytes. |
| `sessions/<session>/status.log` | Logger status messages. |
| `merged_feature_table.csv` | Analysis table used by the evaluation code, with segment labels. |
| `landmarks/landmarks.csv` | Surveyed landmarks and the segment class of each (thesis Table 3.5). |

## Sessions
All sessions were recorded on 1 October 2026. Each folder is named `session_<date>_<time>_<logger boot id>`, as written by the receiver program.

| Session | Folder | Description | Rows | Duration (s) | Rows with GPS fix |
|---|---|---|---|---|---|
| – | `session_20261001_041538_5D52F49B` | Preliminary stationary test | 723 | 72.2 | 723 |
| 001 | `session_20261001_044622_7D124663` | Stationary bench test | 474 | 47.3 | 373 |
| 002 | `session_20261001_070034_62B7CBB2` | Drive | 4 715 | 471.4 | 0 |
| 003 | `session_20261001_071208_62B7CBB2` | Drive | 1 406 | 140.5 | 0 |
| 004 | `session_20261001_071612_C20123AB` | Idle check | 139 | 13.8 | 0 |
| 005 | `session_20261001_072334_D1208EC3` | Drive (the labelled drive) | 11 082 | 1 108.1 | 3 736 |
| 006 | `session_20261001_074352_D1208EC3` | Drive (SSL validation) | 2 525 | 252.4 | 0 |

`merged_feature_table.csv` combines sessions 002, 003, 005 and 006 (19 728 rows).

## Columns of `timeseries.csv`
`timestamp_ms, latitude, longitude, gps_altitude_m, gps_speed_kmph, gps_valid, rpm, vehicle_speed_kmph, maf_g_s, fuel_level_pct, fuel_rate_lph, rpm_valid, speed_valid, maf_valid, fuel_level_valid, fuel_rate_valid`

Fuel level and fuel rate were not answered by this vehicle's ECU, so those columns are invalid throughout.

## Licence
MIT — see [LICENSE](LICENSE).
