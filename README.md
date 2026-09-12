# GMT NearNeighbor XYZ — Nearest-Neighbour Gridding Scripts

GMT (Generic Mapping Tools) shell scripts for gridding scattered XYZ point data into continuous surfaces using the nearneighbor algorithm, a local interpolation method that assigns each node a weighted average of the nearest points found within a search radius and sectors, leaving nodes empty where no data are present. The gridded surfaces are then contoured and mapped. The scripts have been used to generate figures in the author's marine-geophysical and cartographic publications.

## What the scripts do

Each script builds a complete gridding figure, typically chaining:

- inspection of the XYZ data range (gmtinfo)
- conversion of the ASCII XYZ table to binary for speed (gmt convert)
- nearest-neighbour gridding within a search radius and sectors (nearneighbor -S -I)
- contouring of the resulting grid (grdcontour)
- coastlines, frame, scale bar and directional rose (pscoast, psbasemap)
- annotations describing the input data (pstext), GMT logo (logo)
- export to raster (psconvert) at high resolution

Nearest-neighbour gridding is a local method: unlike a global spline it produces no output where the neighbourhood contains no data, so genuine data gaps remain visible. This repository is the nearneighbor counterpart to the surface (continuous-curvature spline) gridding scripts.

## Data sources

Scattered XYZ point data (topography/bathymetry) exported from global grids (e.g. TOPEX/UCSD, 1-arc-minute). Input as ASCII .xyz tables.

## File naming

Scripts follow GMT-17-JM-NN-XX.sh, where XX is an ocean-trench tag (e.g. KKT = Kuril-Kamchatka Trench, AT = Aleutian Trench, MT = Mariana Trench).

## Requirements

- GMT 6.x (Generic Mapping Tools): https://www.generic-mapping-tools.org
- A POSIX shell (bash/sh)
- The relevant XYZ point table(s) available locally

## Usage

Place the required XYZ table in the working directory, adjust the -I resolution and -S search radius at the top of the chosen script, then run:

    bash GMT-17-JM-NN-KKT.sh

The script writes a PostScript file and converts it to a raster image (JPG/PNG) via psconvert.

## Author and citation

Polina Lemenkova
ORCID: https://orcid.org/0000-0002-5759-1089

These scripts accompany figures in the author's marine-geophysical and cartographic papers; please cite the specific article a given figure appears in. The full publication list is available via the ORCID record above.

## License

See the LICENSE file in this repository.
