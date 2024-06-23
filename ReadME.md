# RadarIngestSystem

## Overview

RadarIngestSystem is a project written in Dyalog APL designed for ingesting and managing ADS-B raw data from multipule antenna sources. The system allows for the parsing and agrigation of multipule antenna sources. Written the help of [The 1090 Megahertz Riddle](https://mode-s.org/decode/misc/preface.html).

## Opening RIS

1. Open Dyalog APL.
2. Navigate to the project folder.
3. Run the following usercommand to open the project:
    ```apl
    ]cider.openproject .
    ```

## Running RIS

To start the RadarIngestSystem, run the following:
```apl
RadarIngestSystem.main 30001
```
This starts a new server thread and initializes it on port `30001`.

## Stopping RIS

To stop all threads of the RadarIngestSystem, run the following:
```apl
RadarIngestSystem.end
```

## Database Schema

The database of planes is stored in a matrix format, where each row represents a plane. The columns correspond to different parameters as described below:

| Index | Column Name                          | Description |
|-------|--------------------------------------|-------------|
| 0     | ICAO                                 | Transponder Hex Code |
| 1     | cs                                   | Plane's call sign |
| 2     | ct                                   | Vector of two numbers that are indices in `genCatTable` |
| 3     | clate                                | Even Latitude Computing Value |
| 4     | clato                                | Odd Latitude Computing Value |
| 5     | clone                                | Even Longitude Computing Value |
| 6     | clono                                | Odd Longitude Computing Value |
| 7     | et                                   | Even time |
| 8     | ot                                   | Odd time |
| 9     | lat                                  | Latitude |
| 10    | lon                                  | Longitude |
| 11    | alt                                  | Altitude |
| 12    | gclate                               | Ground clate |
| 13    | gclato                               | Ground clato |
| 14    | gclone                               | Ground clone |
| 15    | gclono                               | Ground clono |
| 16    | get                                  | Ground et |
| 17    | got                                  | Ground ot |
| 18    | track                                | Track |
| 19    | speed                                | Speed |
| 20    | tracktype                            | Track type (1: Magnetic, 0: GNSS) |
| 21    | speedtype                            | Speed type (0: GS, 1: IAS, 2: TAS) |
| 22    | ifrcap                               | IFR Capability |
| 23    | vertrate                             | Vertical rate |
| 24    | diffGNSSBaro                         | Difference between GNSS and Barometric altitude |

Note that the even and odd information contained within the database is for computational purposes, as one needs both an even and odd frame to calculate the latitude and longitude. 

To check the database, you can use:
```apl
RadarIngestSystem.db
```

In the future, a proper GUI could be implemented, however the main purpose of this will be to create a REST API to use as the backend of RadarPlane.com. 

## License

This project is licensed under the MIT License. See the LICENSE file for details.