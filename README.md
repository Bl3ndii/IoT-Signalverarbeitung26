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

## Signal Tools Description

| Method | Parameters | Returns | Description |
| --- | --- | --- | --- |
| `loadSignalFromCSV(file_path)` | `file_path`: path to a CSV/text file with one numeric sample per line. | `list[float]` | Reads the input file line by line, converts each value to `float`, prints the number of loaded samples, and returns the signal samples. |
| `plotSignal(t, signal)` | `t`: time values for the x-axis; `signal`: signal amplitudes for the y-axis. | `plotly.graph_objects.Figure` | Creates an interactive Plotly line-and-marker chart of the signal with time and amplitude axes, unified hover labels, and a visible x-axis range slider. |
| `computeFFT(signal, sample_rate)` | `signal`: input samples; `sample_rate`: sampling frequency in Hz. | `tuple` containing `frequencies` and `magnitude` arrays. | Computes the one-sided Fast Fourier Transform spectrum for the signal and returns the corresponding frequency bins and scaled magnitudes. |
| `plotFFT(frequencies, fft_magnitude)` | `frequencies`: frequency bins in Hz; `fft_magnitude`: FFT magnitude values. | `plotly.graph_objects.Figure` | Creates an interactive Plotly line chart for the FFT spectrum with frequency and magnitude axes. |
| `calculateSNR(input_signal, signal_frequency=10, sample_rate=50)` | `input_signal`: signal samples; `signal_frequency`: expected signal frequency in Hz; `sample_rate`: sampling frequency in Hz. | `float` | Estimates the target sinusoidal component with least squares, treats the residual as noise, and returns the signal-to-noise ratio in decibels. |

## References

- [Online FIR Filter Design Tool](http://t-filter.engineerjs.com/)
