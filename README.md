# Power of blackman window

In the research Finding the best methods for image scaling (https://github.com/garamond13/Finding-the-best-methods-for-image-scaling) I presented the garamond window, and in then I presented the raised version of it (power of garamond - https://github.com/garamond13/power-of-garamond-window). Now I will present the new window, the power of blackman window. Which is just blackman window raised to some power. Raising blackamn window to some power will give us the greater control over its properties in the same way raising the garamond window did.

First some properties of blackman window: \
w(x) = `(1.0 - a) / 2.0 + 0.5 * cos(M_PI * x / R) + a / 2.0 * cos(2.0 * M_PI * x / R)`, where (a) is a free parameter and (R) is the kernel radius, M_PI=pi constant 
at a=0.0, w(x)=hann window \
at a=0.16, w(x)=the common blackman window

Now, the power of blackman window

w(x) = `x < R : pow((1.0 - a) / 2.0 + 0.5 * cos(M_PI * x / R) + a / 2.0 * cos(2.0 * M_PI * x / R), n) : 0.0`, where (a) is a free parameter and (n) is in the range [0.0, +inf], and (R) is the kernel radius, M_PI=pi constant \
at n=1.0, w(x)=blackman window \
at n=0.0, w(x)=box window \
at a=0.0 n=1.0, w(x)=hann window \
at a=0.0 n=0.5, w(x)=cosine window

Similarly to the generalized normal window (gnw) (https://ieeexplore.ieee.org/document/6638833), the said window (https://www.hpl.hp.com/techreports/2007/HPL-2007-179.pdf) and the power of garamond window, it can approximate other windows. In contrast to the gnw and the said window, approxiations can be scaled to any radius. Here, I will show the test results of approximating some windows using the same settings for all kernels (base=sinc, kernel-blur=1.0, kernel-radius=5.0, antiringing=0.0, light=gamma). The test image, 960x540 will be upscaled to 1920x1080. The table below shows mesured differences in psnr (dB) between a native window and its power of blackman approximation at some (a) and (n).

| approximation | psnr |
| --- | --- |
| (lanczos) a=0.045 n=0.571 | 60.3842 |
| (welch) a=-0.037 n=0.464 | 63.0054 |
