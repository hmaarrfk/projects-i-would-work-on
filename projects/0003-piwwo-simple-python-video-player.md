# A very simple video player for scientific applications in Python

tags: python, video

Many video player exist but few provide two key functionality:

1. The ability to move frame by frame.
2. The ability to zoom in.

One should be able to write a quick video player with these two
functionalities using:

* PyAV -- to open the video stream.
* PyGFX -- to display the video using hardware acceleration
* IMGUI -- to create sliders and inputs to control the video.

Cross platform support is critical.
And perhaps even remote support through PyGFX's jupyter-rfb (remote frame buffer).

## Alternatives considered

* VLC -- This is a very strong video player, however VLC4 has been
  seriously delayed, making it much less attractive. Integration
  within larger python applications is also very hard.

## Future extensions

* Labelling of I, P, and B frames.
   * I frames provide VERY fast "seeking" and thus are very advantageous when
   * trying to study a video. Thus it would be good to label them in the interface
   * so that users can readily seek to them.
* Integration within Napari (napari doesn't use PyGFX or IMGUI so the knowledge would be "lateral").
