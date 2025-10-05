# Improved support for FastLED in TeensyToAny

tags: hardware, c++

We made a little teensy general purpose debugging tool at Ramona.

We added FastLED support very quickly, however it doesn't support "teardown" routines.

Intead, we simply "declare" the maximum number of LEDs in the strip we want to support and
move on.

However, there should be lower level support for declaring, and removing LED strips in FastLED.

https://github.com/ramonaoptics/teensy-to-any
