# Create a comparive benchmark for video encoders

In the context of microscopy, the "3D" can come from either
an additional spatial dimension or the time dimension.

The benchmark would aim to address the following:

* Given a image over time (t), how much space can I save? What tradeoffs do I make?
* Given an image over space (z), how much space can I save? What tradeoffs do I make?

It would be interesting to study how different video compression algorithms
work along the following axes:

1. Do they even apply? Sometimes if the frame is of a wrong shape, too large, too small, odd number of pixels, the compression tool simply fails.
2. Startup time? Sometimes the hardware accelerators, or even software encoders, take time to startup, and this isn't always negligeable.
3. Compression time? Is there a normalizing metric we can provide, like "for 5000 frames".
4. Decompression startup time?
5. Decompression time -- software only?
6. Decompression time -- hardware accelerated?
7. Compression fidelity? How well is the compression working. For example "red" is notoriously bad in H264. Are there ways to turn off this color dependent loss.
8. Does video work well for "axial" data?

## Existing work

I think that imageio's interface to FFMPEG is quite good for this kind of exploration.
It will be limiting in its performance but can give a good sense of size tradeoff.

## Open questions

* Compatibilility with multi-channel images (5 - 7 different acquisition
  channels) is a concern. Videos are made for "3" channels, though they are often
  unevenly represented with "green" being overly represented.

* High bit depth video is an other concern. Since visual perception over 8 bits
  is a litle dubious, I have a feeling that strong sacrifices to accuracy
  might be made.
