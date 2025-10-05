# Lazy block arrays in numpy

tags: numpy, python, arrays, lazy, performance

The ability to block and concatenate arrays is really useful,
but when the array size gets larget than 1MB, concatenation
is slow and often not required.

Sometimes it is just about keeping track of the subarrays in a
cohesive manner.

Consider:

1. You have 10 different arrays each 2048x2048 (a 4MP grayscale image)
2. You want to to put them in a (5x2x2048x2048) array
3. That would involve a total of 40MB for the source, 40MB for the destination.
4. That copy isn't cheap.


However, it would be great if we could create a container that could:

1. Take in the arrays
2. Create a new "lazy" array with the right shape.
3. Implement lazy slicing and indexing operations.
4. If the indexing reduces itself to one of the original arrays, just return it.

One of the interesting aspects is that we don't need to coerce arrays if they
expose the array protocol from numpy (or has it evolved as dataapis now??)


# Alternatives

* Wrap everything in a Dask Array. This is actually a pretty good start but I
  think that dask has too much overhead.
