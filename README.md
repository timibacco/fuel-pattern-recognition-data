# Fuel Consumption Pattern Recognition — Dataset

Data recorded for the B.Sc. thesis *Development of a Recognition Model for Vehicle Fuel Consumption Pattern in a Controlled Spatiotemporal Environment* (Abayomi, O. S., Department of Computer Engineering, Obafemi Awolowo University, Ile-Ife, 2026).

Vehicle: 2014 Lexus RX350 (petrol, V6). Route: Road 1, Obafemi Awolowo University campus, Ile-Ife, Nigeria. Logger: ESP32 + SN65HVD230 + NEO-6M (see the code repository: https://github.com/timibacco/fuel-pattern-recognition-code).

## Layout
| Path | Contents |
|---|---|
| `sessions/<session>/timeseries.csv` | One row every 100 ms: GPS position, altitude, speed and fix flag; polled engine speed, vehicle speed and mass air flow; validity flags (thesis Table 3.4). |
| `sessions/<session>/raw_can.csv` | Every CAN frame received: timestamp, identifier, DLC and data bytes. |
| `sessions/<session>/status.log` | Logger status messages. |
| `merged_feature_table.csv` | Analysis table used by the evaluation code (19 728 rows from sessions 002, 003, 005 and 006). |
| `landmarks/landmarks.csv` | Surveyed landmarks and the segment class of each (thesis Table 3.5). |

## Sessions
| Session | Description | Rows | Duration (s) | GPS fix |
|---|---|---|---|---|
| 001 | Stationary bench test | – | – | not in analysis table |
| 002 | Drive | 4 715 | 471.4 | none |
| 003 | Drive | 1 406 | 140.5 | none |
| 004 | Idle check (14 s) | – | – | not in analysis table |
| 005 | Drive | 11 082 | 1 108.1 | 33.7% of rows (3 736 rows) |
| 006 | Drive (SSL validation) | 2 525 | 252.4 | none |

## Columns of `timeseries.csv`
`timestamp_ms, latitude, longitude, gps_altitude_m, gps_speed_kmph, gps_valid, rpm, vehicle_speed_kmph, maf_g_s, fuel_level_pct, fuel_rate_lph, rpm_valid, speed_valid, maf_valid, fuel_level_valid, fuel_rate_valid`

Fuel level and fuel rate were not answered by this vehicle's ECU, so those columns are invalid throughout.
