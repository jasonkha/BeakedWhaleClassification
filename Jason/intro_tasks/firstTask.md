# Preparatory Steps

*1. Write a high level summary of click descriptions including the following terms: click detector, click spectra, inter-click-interval, click bout, peak-to-peak amplitude, and click time series.*

Whales and dolphins can be classified based on the underwater sounds they emit, called echolocation clicks. An individual species of beaked whales could be more closely associated with a particular pattern of clicks, which can be analyzed using standard signal processing algorithms like FFT. Clicks were collected from five different sites from the Gulf of Mexico after the Deepwater Horizon oil spill from 2010 to 2012.

A **click detector** is a device that looks at properties of a signal and classifies the click based on features like frequency, duration, and amplitude.

**Click spectra** is click's sound pressure level as a function of its frequency.

The **inter-click-interval** is the time between the lead and lag click.

The **click bout** is a bunch of detected clicks in a short period of time associated with a species.

**Peak-to-peak amplitude** is the difference between the maximum and minimum amplitudes of the waveform.

**Click time series** is the series of clicks during an interval indexed by time.

To classify echolocation clicks, time series were transformed into click spectra with DFT. The waveform and spectra are input features to the clustering algorithm, as well as the ICI interval and peak-to-peak amplitude.
