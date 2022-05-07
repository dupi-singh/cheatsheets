# Interpreting the frequency axis of MATLAB FFT function when the length of time series (N) is even or odd
------------------------------

`F = FFT(x);`

### 1. If N is even
| Type | Address | comment
|--|--|--|
| Nyquist frequency (fs) | F(end/2+1) | #
| Positive frequencies | F(2:end/2) | Ascending order
| Negative frequencies | F(end/2+2:end) | mirrored to +ve frequency


### 2. If N is odd
| Type | Address | comment
|--|--|--|
| Nyquist frequency (fs) | not included | Highest feequency is fs-df/2 at F(ceil(end/2)), where df is the frequency spacing. Next element is the corresponding negative frequency
| Positive frequencies | F(2:ceil(end/2)) | Ascending order
| Negative frequencies | F(ceil(end/2)+1:end) | mirrored to +ve frequency

