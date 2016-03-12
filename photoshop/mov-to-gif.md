[back]: https://github.com/rafaelrinaldi/til/tree/master/photoshop
[cloudconvert]: http://cloudconvert.com
[ffmpeg]: https://ffmpeg.org
[gist-original]: https://gist.github.com/rafaelrinaldi/5542653d0bc56c887bde
[gist]: https://gist.github.com/dergachev/4627207
[licecap]: https://github.com/lepht/licecap
[recordit]: http://recordit.co

# `.mov` to `.gif`

This is my preferred way to create GIF animations using Photoshop and QuickTime.

## Requirements

* QuickTime 10
* Adobe Photoshop CC 2015

It might work in lower versions tho.

## Steps

1. QuickTime » File » New Screen Recording
  1. Select area to record » Start recording your thing
  2. File » Export » Select max resolution available » Save
2. Photoshop » Import » Video Frames to Layers (no need to follow step `2` if not on retina screen)
  1. Select your .mov file » Select range to import » Make sure "Limit to Every `N` Frames" is unchecked » <kbd>OK</kbd>
  2. Image » Image Size » Make sure the ![chains](https://cldup.com/JENmtHhThO-3000x3000.png) icon is selected (to keep aspect ratio) » Set width to half of its size » <kbd>OK</kbd>
  3. File » Export » Save for Web (Legacy)
    1. Make sure file format is GIF (right below "Preset")
    2. Looping options » Forever
    3. <kbd>Save</kbd>

## Adjust speed

1. Photoshop » Window » Timeline
2. Timeline » Select All Frames
3. Right below the frame thumbnail, click on the frame delay » Other » Set the frame delay you want
4. Follow step `2.3` under [**Steps**](#steps)

## Other options

Options that I've tried in the past:

* [LICEcap][licecap]: decent UI, bad output (weird square shapes floating around)
* [Recordit][recordit]: best UI of all the options, bad output (tiny pixel dots spread across the image)
* [CloudConvert][cloudconvert]: essentially _[ffmpeg][ffmpeg] as a service_, bad defaults (if you got the skills to customize it, might be a good fit)
* [OS X Screencast to animated GIF (Gist :octocat:)][gist]: guide to generate a GIF using ffmpeg on OSX, interesting stuff but kinda overwhelming

## Is there a better way?

This is the best way that I found so far for creating decent quality GIF animations. If you know a better way to do it that doesn't involve installing `ffmpeg`, `coreutils`, `cmake` and recompiling the kernel, please let me know.

---

[← Back][back]
