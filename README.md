# IoT Signal Processing: FFT and FIR Filtering

This repository contains a Jupyter Notebook that demonstrates basic signal processing techniques using Python. The focus is on analyzing and filtering signals, which are common tasks in IoT applications.


## Installation

Requires Python 3.12 or higher. 

### Windows / PowerShell

```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
python -m pip install --upgrade pip
python -m pip install -r requirements.txt
```

### macOS / Linux

```bash
python3 -m venv .venv
source .venv/bin/activate
python -m pip install --upgrade pip
python -m pip install -r requirements.txt
```

## IoT Tutorial

The python notebook `iot_tutorial.ipynb` provides a step-by-step tutorial on how to load, analyze, and filter signals. It includes examples of using Fast Fourier Transform (FFT) for frequency analysis and Finite Impulse Response (FIR) filters for signal filtering.

## Signal Tools Description

This section describes the functions provided in the `signal_tools.py` module, which are used for loading, plotting, and analyzing signals.

### `loadSignalFromCSV`

| Item | Description |
| --- | --- |
| Signature | `loadSignalFromCSV(file_path)` |
| `file_path` | Path to a CSV/text file with one numeric sample per line. |
| Returns | `list[float]`: the loaded signal samples. |
| Description | Reads the file line by line, converts each value to `float`, and prints the number of loaded samples. |

### `plotSignal`

| Item | Description |
| --- | --- |
| Signature | `plotSignal(t, signal)` |
| `t` | Time values for the x-axis, in seconds. |
| `signal` | Signal amplitudes for the y-axis. |
| Returns | `plotly.graph_objects.Figure`: an interactive signal chart. |
| Description | Creates a line-and-marker chart with time and amplitude axes, unified hover labels, and an x-axis range slider. |

### `computeFFT`

| Item | Description |
| --- | --- |
| Signature | `computeFFT(signal, sample_rate)` |
| `signal` | Input signal samples. |
| `sample_rate` | Sampling frequency in Hz. |
| Returns | A tuple of NumPy arrays: frequency bins in Hz and scaled FFT magnitudes. |
| Description | Computes the Fast Fourier Transform and returns the first `N // 2` bins, with magnitudes scaled by `2.0 / N`, where `N` is the sample count. |

### `plotFFT`

| Item | Description |
| --- | --- |
| Signature | `plotFFT(frequencies, fft_magnitude)` |
| `frequencies` | Frequency bins in Hz. |
| `fft_magnitude` | FFT magnitude values. |
| Returns | `plotly.graph_objects.Figure`: an interactive FFT spectrum chart. |
| Description | Creates a line chart with frequency and magnitude axes and unified hover labels. |

### `calculateSNR`

| Item | Description |
| --- | --- |
| Signature | `calculateSNR(input_signal, signal_frequency=10, sample_rate=50)` |
| `input_signal` | Input signal samples. |
| `signal_frequency` | Expected signal frequency in Hz. Defaults to `10`. |
| `sample_rate` | Sampling frequency in Hz. Defaults to `50`. |
| Returns | A floating-point signal-to-noise ratio in decibels. |
| Description | Fits a sinusoidal component at the expected frequency using least squares, treats the residual as noise, and computes the ratio of signal power to noise power in decibels. |

## References

- [Online FIR Filter Design Tool](http://t-filter.engineerjs.com/)
