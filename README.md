# oioi(おいおい) - Single-file public-domain QOI reader.

See qoiformat.org for the specification and refrence implementation.

## Why?

The reference decoder loads the whole image into RAM, which is bad if you want
to load a big image into a system with low memory.  

This implementation uses a small buffer (512B) to read the file and decode it on-the-fly.  

## Usage

```
#define OIOI_IMPLEMENTATION
#include "oioi.h"

int width, height;
unsigned char* data = oioi_read(file, &width, &height, channels);
```

I'd suggest using the -O3 flag if you do care about speed.  

## Limitations

This implementation won't do anything to the size of the decoded image.  
It is a little slower than the reference decoder, but still faster than stbi.  
It does NOT include a encoder.  
