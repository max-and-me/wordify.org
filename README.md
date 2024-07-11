# Wordify.org homepage

## Introduction

These are the sources of wordify.org.

## Getting Started

```sh
git clone https://github.com/max-and-me/wordify.org
```

## Getting Help

### Record feature video

The feature videos which can be seen on the website are screen captures of Wordify. 

#### Instructions

* Adjust Wordify to a size of 720x540 which is 4:3 ratio (keep in mind, on HiDPI screens like Retina this results in a size of 1440x1080)
* Open the QuickTime Player (macOS) and record Wordify by selecting a rectangle on screen
* Trim the front and end of the video (QuickTime Player >> Edit >> Trim) and save changes
* Open the video in VLC, right mouse click and "Snapshot" (/home/user/Pictures)
* Open the snapshot in Gimp and select the part you want to crop. The selection rectangle must be 720x540 (or 1440x1080) in size. Move the selection rectangle to the exact position of Wordify.
* Read out the selection width, height, x, y
* Use ffmpeg to crop video ```ffmpeg -i ./recorded.mov -vf "crop=width,height,x,yscale=720:540,setsar=1:1" output.mov``` (we scale the video down to 720x540 in case it is HiDPI recorded)
* Use ```Handbrake``` (macOS) to convert the video to ```webm```, ```Preset: Fast 720p30``` and choose ```Format: WebM```.