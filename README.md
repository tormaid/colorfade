# colorfade

A simple Vapoursynth script for doing bi-directional, mathematically-correct linear blending of a single frame over a specified range with a target color. Useful for re-creating static fades.

The internal dissolve function, which is based in part on kageru's Crossfade, is linear, and blends the target, frozen frame from completely opaque to completely transparent over the specified range. That means that, in the 'forward' direction, the 'start' frame will be completely unchanged, and the 'end' frame will be the exact specified color.

Illustration: The following are frame numbers for a range of 5-9, followed by their weights in the internal Merge function.
  
[5, 6, 7, 8, 9]  
[0, .25, .5, .75, 1]
	

Requires YUV input.

# Usage:

    colorfade(clip, start, end, direction='forward', YUV=[])

* start, end [int]: Determine the beginning and end of the fade range.

* direction [str, default='forward']:
  * forward = Fades *to* the specified color
  *	backward = Fades *from* the specified color

* YUV [lst]: The YUV color code of the color you wish to fade to/from. Scale is based on the bit-depth of the input clip. 

  eg. [76, 84, 255] (Red, 8-bit Scale)

  Hint: Use the color picker in the VapourSynth Editor.
