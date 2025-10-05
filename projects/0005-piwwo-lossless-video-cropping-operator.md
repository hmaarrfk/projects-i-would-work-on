# Lossless video operators

Recompressing video can be terrible for scientfic applications.

However the MP4 file format and video codecs such as H264, HEVC and AV1 provide
ways to describe many operations such as:

* Presentation time
* Cropping in x-y
* specifying I frames
* Color corrections????


Thus it would be interesting to see how far we can go in the list above.


### Lossless time crop

There is an application called LosslessCut that does this.
It would good to have the ability to replicate this in a python library.

### Cropping in x-y

This is one thing that I don't have too much experience with, but I feel like
there are spatial transforms that we can specify as side-data.

If the video crop is 90% of the original video, it would be very interesting to 
simply do this in a "metadata transformation".

If the crop becomes really small, it would be interesting to consider the tradeoff of re-encoding the whole thing

1. Start with lossless video cropping in time. There is an application called LosslessCut that has a GUI for this.
2. Attempt to open it in various video players.
