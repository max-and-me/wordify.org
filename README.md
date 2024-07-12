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

##### Screen recording

* Adjust Wordify to a size of ```720x540``` which is 4:3 ratio (keep in mind, on HiDPI screens like Retina this results in a size of ```1440x1080```)
* Open the QuickTime Player (macOS) and record Wordify by selecting a rectangle on screen
* Trim the front and end of the video (```QuickTime Player >> Edit >> Trim```) and save changes

##### Crop and scale recording

* Take a screenshot of the first frame of the video using ```ffmpeg```.

```sh
ffmpeg -i recording.mov -ss 00:00:00 -frames:v 1 -q:v 2 screenshot-%03d.png
```

* Open the snapshot in ```Gimp``` and select the part you want to crop. The selection rectangle **must** be ```720x540``` (resp. ```1440x1080```) in size. Move the selection rectangle to the exact position of the Wordify window.
* Read out the selection ```width```, ```height```, ```x```, ```y``` (e.g. ```1440```, ```1080```, ```32```, ```144```)
* Use ```ffmpeg``` to crop video 

```sh
ffmpeg -i ./recording.mov -vf "crop=width:height:x:y,scale=720:540,setsar=1:1" -r 30 -crf 40 cropped_and_scaled.webm
``` 

Example:
```sh
ffmpeg -i ./wordify_selection_feature_original.mov -vf "crop=1440:1080:32:144,scale=720:540,setsar=1:1" -r 30 -crf 40 wordify_selection_feature.webm
```

(we scale the video down to ```720x540``` in case it is HiDPI recorded, use a rate of 30fps ```-r 30``` and set the quality ```-crf 40```)

### Further links

* https://onemanbro.medium.com/thumbnails-screenshots-using-ffmpeg-3-efficient-techniques-a65c76dda2b1
* https://pixelpoint.io/blog/web-optimized-video-ffmpeg/