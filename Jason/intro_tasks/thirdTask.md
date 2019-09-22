# Summary of the SPICE-Detector algorithm

*Your third task is to re-run SPICE-Detector under Jingwu/SPICE-Detector, read through the code and make sense of the output files. Write your summary of the SPICE-Detector algorithm and your interpolation of the output files.*

The SPICE-Detector algorithm first reads a detector parameters settings file, which controls whether the low and/or high resolution detector is run, the bandpass filter range, minimum amplitude threshold, and other detection threshold parameters. Then it reads the XWav header and builds a filter.

It opens and reads in data segments from a WAV file, running a band-pass filter that allows frequencies within a certain range, as defined in the detector settings, and rejects frequencies outside that range.

Next, the low resolution detector runs and identifies click candidates by finding all events exceeding a threshold and returning the times of these events.

Afterwards, the high resolution detector expands the click regions and selects valid clicks using a window around the detected peak.

Pruning then takes place on detections with overly high amplitudes that could be clipped.

Finally, click parameters are computed to decide if the detection should be kept.

# Interpolation of the output files
The output files consist of a list of start and end times for each detected click. The `dt_postproc` function iterates through the vector of click times and discards solo clicks, duplicate clicks, and clicks that are too far apart from their neighboring clicks.
