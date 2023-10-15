# Linear_Predictive_Analysis_for_Phones

## Introduction

The Linear Predictive Analysis code provided here focuses on audio and signal processing. It includes several functions for pre-emphasis, autocorrelation, Levinson-Durbin algorithm, pole-zero plotting, LPC spectrum analysis, inverse filtering, and fundamental frequency estimation. This code can be used to analyze audio signals, extract relevant features, and estimate parameters like fundamental frequency.

## Dependencies

Before using the code, you need to make sure you have the following libraries installed:

- `librosa`: Used for audio and music analysis.
- `matplotlib`: Required for creating plots and visualizations.
- `numpy`: Used for numerical computations.
- `scipy`: A library for scientific and technical computing.
- `control`: Used for transfer function modeling and pole-zero plotting.
- `IPython`: Required for display functions in Jupyter Notebook.

You can install these libraries using `pip` if you don't have them already:

```
pip install librosa matplotlib numpy scipy control ipython
```

## Functions

Here's a brief overview of the key functions in the code:

### Pre-emphasis

The `pre_emphasis` function applies pre-emphasis to an input signal to enhance higher-frequency components. Pre-emphasis is achieved by subtracting a fraction of the previous sample from the current one.

### Autocorrelation

The `autocorrelation` function calculates the autocorrelation of a signal, providing insights into temporal dependencies and patterns within the data.

### Levinson-Durbin Algorithm

The `levinson_algorithm` function efficiently estimates the coefficients of an autoregressive (AR) model. It minimizes the prediction error step by step to derive reflection coefficients and AR model coefficients.

### Linear Predictor

The `linear_predictor` function combines the autocorrelation and Levinson-Durbin algorithm to estimate the prediction error, prediction gain, and predictor coefficients.

### Pole-Zero Plot

The `plot_pole_zero` function generates pole-zero plots for transfer functions.

### LPC Spectrum Analysis

The `LPC_spectrum` function performs LPC spectrum analysis, plotting the magnitude spectra of the original signal and estimated LPC filters for different orders.

### Inverse Filtering

The code includes an `fundamental_frequency` function that uses inverse filtering to estimate the fundamental frequency of a signal.

### Generating Triangular Excitation

A function called `generate_triangular_excitation` generates triangular excitation signals with specific pitch, duration, pulse sample width, and sampling frequency.

## Usage

You can use the provided functions for various audio and signal processing tasks. For example, you can estimate the fundamental frequency of an audio signal using the `fundamental_frequency` function or analyze the LPC spectrum of a signal using the `LPC_spectrum` function.

To use these functions in a Jupyter Notebook, copy and paste the code into your notebook. Make sure to install the required dependencies as mentioned above.

## Example

Here's an example of how to use the code to estimate the fundamental frequency of an audio signal:

# Load an audio signal (e.g., using librosa)
audio_signal, sampling_rate = librosa.load('audio.wav', sr=None)

# Perform linear prediction
error, gain, a = linear_predictor(audio_signal, p)

# Estimate the fundamental frequency
inverse_filter, F0, r_inverse, r_signal = fundamental_frequency(gain, a[p], audio_signal)
```

