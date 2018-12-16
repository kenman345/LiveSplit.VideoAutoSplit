# Video Auto Splitter

## How to use

### Requirements

* [LiveSplit](http://livesplit.org/)
* An existing game profile.
  * If a profile for the game you want to use the video auto splitter for has not been made and you are willing to make one yourself, visit [Creating a Profile](#creating-a-profile).
* A DirectShow output of the video feed.
  * For OBS, this can be done with the [Virtual Cam plugin](https://obsproject.com/forum/resources/obs-virtualcam.539/). See [FAQs](#how-do-i-use-virtual-cam-for-obs) for how to install and use the plugin for this component.
  * XSplit also has a [Virtual Camera feature](https://www.youtube.com/watch?v=WxPJdUtEae8).
  * You can use the direct video feed from your capture device, but it may prevent your capturing software from recognizing it too.

### Installation

1) Download the [latest version](https://github.com/ROMaster2/LiveSplit.VideoAutoSplit/releases) of the component.
2) Find your LiveSplit folder and extract the contents into the Components folder. If you are updating from a previous version, replace the existing files.
3) Start LiveSplit.
4) Add the component to your layout. The component will be available in Layout Settings under Control.
5) Open the component's settings.
6) Click on the Browse... button and locate the game profile you wish to use.
7) Select the video capture. You will most likely want to use OBS-Camera or XSplitBroadcaster, if they're available.
8) Verify the video capture by selecting the "Scan Region" tab. If it doesn't include the feed you're expecting, try another video capture. If none of the options have the feed, visit [Help](#help) to diagnose the problem.
9) Set the capture area of the feed. Your video feed will likely not be one-to-one with the profile and has to be cropped to fit it. Use the preview type 'Feature' with the preview feature dropbox to help with aligning.

Unfortunately, because of how component settings are saved, **the settings are tied to the layout file**. This will be changed at a later date.

## Creating a Profile

Creating a profile is very similar to creating a regular [Auto Splitter script](https://github.com/LiveSplit/LiveSplit/blob/master/Documentation/Auto-Splitters.md), but instead of monitoring memory values, it monitors regions of a video feed and compares it against an image, or in some cases, the previous frame, and returns a confidence value. The VAS file used to hold the game profiles contain three important parts: The structure, the script, and the images.

###### Don't let the file extension confuse you, it's just a zip.

### Finding static reference points

Before *any* of that can be made, the references the component will told to watch for must be found. The difficulty in finding reliable references vary greatly between games. Generally, big references that change abruptly to and/or from a compared image are the most reliable.

###### A video with examples should be here. Text makes it difficult to really explain the process.

The same base screen reference must be used throughout making the profile. This is so users only need to align the screen with their video feed to have all the references automatically fit into place.

Raw, high quality gameplay footage is recommended when extracting the reference images 

### Structure File

###### Note: A user interface will later be made to help with creating this file. For now, it's requires manually editing an XML file.

## Contributing

Any and all help with development, be it with finding or squashing bugs or adding new features, would be awesome.

### How to Compile

 1. Create a clone of LiveSplit following [its instructions](https://github.com/LiveSplit/LiveSplit#contributing).
 2. In the `/LiveSplit/Components` folder of the above, create a clone of the VAS component: `git clone https://github.com/ROMaster2/LiveSplit.VideoAutoSplit.git`
 3. Inside Visual Studio, right click the `Components/Control` folder, hover over Add, and select "Existing Project...". Go through the folders to `/LiveSplit/Components/LiveSplit.ScriptableAutoSplit` and select `LiveSplit.VideoAutoSplit.csproj`.

You should now be able to debug and compile the component with LiveSplit.
