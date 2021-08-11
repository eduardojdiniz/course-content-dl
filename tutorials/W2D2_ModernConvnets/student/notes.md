# Tutorial 1

Channel-wise convolution == depthwise convolution: each channel is processed separately then they are combined with a 1x1 filter across channels. The 1x1 filter across channels prevents capture interactions like pixel (1,1) in channel 1 and pixel (1,2) in channel 2.

Look-up ossificaton.