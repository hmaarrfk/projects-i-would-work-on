# Streamed PNG reader

One challenge with PNG files is that for very large files, the
decompression and unfiltering steps can require a lot of time.

Thus it would be advantageous to be able to read PNG files in a streamed
fashion so that we can report a progress bar.

There are generally a few steps in reading a PNG file:

1. Read the PNG signature (8 bytes)
2. Read chunks (length, type, data, CRC)
3. For IDAT chunks, decompress the data (zlib)
4. Unfilter the decompressed data
5. Reconstruct the image from the unfiltered data

We would want to be able to report progress at each of these steps with TQDM.

One challenge is that the Paeth unfiltering step requires access to the
previous row of pixels. So it isn't readily vectorizable, and it
makes the pure python implementation slow.

numba and njit can help speed up the unfiltering step, but it would require
a compiler and those aren't always available on mac or windows.

So it might be that we simply implement a paeth unfiltering step in C and
use ctypes to call it from python.

As for zlib decompression, we must use a streaming decompressor, which
is available in the standard library.
