# PL_MPEG - MPEG1 Video decoder, MP2 Audio decoder, MPEG-PS demuxer

Single-file MIT licensed library for C/C++

See [pl_mpeg.h](https://github.com/phoboslab/pl_mpeg/blob/master/pl_mpeg.h) for
the documentation.

## Example Usage

- [pl_mpeg_extract_frames.c](https://github.com/phoboslab/pl_mpeg/blob/master/pl_mpeg_extract_frames.c)
extracts all frames from a video and saves them as PNG.
 - [pl_mpeg_player.c](https://github.com/phoboslab/pl_mpeg/blob/master/pl_mpeg_player.c)
implements a video player using SDL2 and OpenGL for rendering.



## Encoding for PL_MPEG

Most [MPEG-PS](https://en.wikipedia.org/wiki/MPEG_program_stream) (`.mpg`) files
containing MPEG1 Video ("mpeg1") and MPEG1 Audio Layer II ("mp2") streams should
work with PL_MPEG. Note that `.mpg` files can also contain MPEG2 Video, which is
not supported by this library.

You can encode a video in a suitable format using ffmpeg:

```
ffmpeg -i input.mp4 -c:v mpeg1video -c:a mp2 -format mpeg output.mpg
```

## Limitations

- no error reporting. PL_MPEG will silently ignore any invalid data.
- the pts (presentation time stamp) for packets in the MPEG-PS container is
ignored. This may cause sync issues with some files.
- no seeking.
- bugs, probably.