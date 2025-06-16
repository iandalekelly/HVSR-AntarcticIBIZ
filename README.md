# HVSRs for the Antarctic IBIZ

This repository supports **KELLY ET AL. (????)**, providing:

1. Example Python scripts implemented in a Jupyter notebook to compute and analyse HVSRs from Antarctica, using [`hvsrpy`](https://github.com/jpvantassel/hvsrpy);
2. Additional figures summarising the HVSR observations at each of the 82 Antarctic stations analysed by **KELLY ET AL. (????)**.

We note that the forward modeling component of **KELLY ET AL. (????)** is not demonstrated here - this was implemented in Matlab, using the Windows executables provided in the supplementary material provided by [Albarello et al. (2023)](https://doi.org/10.1093/gji/ggad109).

## 1. Example Python code

The Jupyter notebook `ExampleWorkbook.ipynb` provides an example Python workflow as to how one downloads seismic data from an Antarctic station (using [`obspy`](https://docs.obspy.org/)), perform data quality checking and pre-processing, and computes HVSRs (using [`hvsrpy`](https://github.com/jpvantassel/hvsrpy)). 

For the data pre-processing and quality checking, we have developed a few useful functions:

- `RotateWaveforms`: If the component traces downloaded from [`obspy`](https://docs.obspy.org/) are in [1, 2, Z] format, this function will automatically rotate them into [E, N, Z] format, using the station information.
- `GetTimeSeries`: From the [E, N, Z] traces for a station, create 3-component timeseries of variable length and step across the downloaded recording period, to feed as .mseed files into [`hvsrpy`](https://github.com/jpvantassel/hvsrpy). This function also has options to visualise any data gaps found (using `http://plotly.com/`) and to merge any of a set length, or to skip over them (so that the timeseries produced are full of data and consistent across the 3-components).

The HVSR data processing via `hvsrpy` is then performed for both merged horizontal components and across an azimuthal surface.

## 2. Summary of HVSR observations

For those interested in the HVSR observations made at every station analysed by **KELLY ET AL. (????)**, we provide a figure for each station that includes:

- Metadata regarding the station and local subsurface conditions, supported by a map of surrounding bed topography and associated error from [BedMachine](https://nsidc.org/data/nsidc-0756/versions/3);
- Temporal trends in the horizontally-averaged median HVSRs, either over a selected yearly period (for the permanent installations at CCD and QSPA, and the long-term POLENET/ANET, GAMSEIS and TAMNET networks), or over an available austral summer period (for the TAMSEIS network);
- The horizontally-averaged and azimuthally-mapped HVSRs for 3 selected timeseries over the recording period, illustrating the variation in wavefield conditions and the performance of the frequency-domain window-rejection algorithm implemented in `hvsrpy` (and for stations N092, N108, N132, TIMW, GM07, the clear indicators of contamination from instrumental issues or local fieldwork activity).

## Citing this repository & author contact

If you make any use of this code or results for a publication or presentation, please acknowledge the work that went into developing it by citing the associated publication of **KELLY ET AL. (????)**, i.e.,

- **KELLY ET AL. (????)** 

For any questions, please either post an issue or reach out to me directly via ian.kelly@utas.edu.au.