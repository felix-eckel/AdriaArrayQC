# AdriaArrayQC

This repository tracks data quality test of the AdriaArray network using noise level analysis at station level.

## What this test is and what it is not

Data quality can be evaluated by many different criteria. There is no single criterion that can determine data quality of a recording in every aspect. This applies also to the results shown in this repository. Here, data quality is measured as a noise level. This allows for comparisons with neighboring stations to identify outliers. The noise levels can highlight stations that report wrong orders of magnitude in the amplitude levels or generally noise or quiet stations. The test does not make any assumptions about the results. These remain to be made by an interpreter.

## How this test works

For every station, **24 h of raw waveform** data are downloaded and **response corrected**. This implies that possible errors in the measured amplitudes can also be caused by erroneous response functions in the meta data. The response corrected data are **filtered** individually around a set of center frequencies. Finally, the **95th percentiles** of all **absolute amplitudes** are determined for each station and color coded on a map.

![Example of a raw data trace](https://github.com/felix-eckel/AdriaArrayQC/blob/main/.img/exmpl_unfiltered_cr_ston.png "raw_data")
Example of a raw data trace

![Example of a trace filtered around 3 Hz](https://github.com/felix-eckel/AdriaArrayQC/blob/main/.img/exmpl_filtered3Hz_cr_ston.png "filtered data")
Example of a trace filtered around 3 Hz

![Example of a 95th percentile trace](https://github.com/felix-eckel/AdriaArrayQC/blob/main/.img/exmpl_95percentile_cr_ston.png "95th percentile")
Example of the 95th percentile of the absolute amplitudes in a trace

### center frequencies

- **3 Hz on the vertical component**: This frequency band is sensitive to local noise. It can highlight stations with noisy station sites.
- **5 s on the vertical component**: This frequency band is affected by microseism. It showcases stations that are very sensitive or insensitive to microseism. It also highlights stations in sedimentary basins where amplitudes are generally higher.
- **20 s on the horizontal component**: This frequency band allows for a more absolute comparison between stations. Site effects play a minor role in this frequency band.

## Products

### Histograms

Histograms of all stations are available for each frequency band. There, regions with unreasonable noise levels are indicated. Noise levels below 0.1 nm/s or above 10e6 nm/s are unrealistic and are labeled "invalid"

![Example for a histogram](https://github.com/felix-eckel/AdriaArrayQC/blob/main/histograms/histogram_Z_3Hz.png "Histogram")
Example for a histogram plot

### Maps

Maps with the color coded noise levels are available for each frequency bands. The stations with noise levels that are in the "invalid" regions of the amplitude range are colored in magenta. The color axis is logarithmic because the noise levels span over multiple order of magnitudes.

![Example for a noise map](https://github.com/felix-eckel/AdriaArrayQC/blob/main/noise_maps/noise_map_Z_3Hz.png "Map")
Exampel for a noise map

### csv files

All values are available as .csv levels together with a very simple category label, indicating high (H), medium (M), low (L) noise levels or amplitudes below (B) or above (A) the valid range.
