# How to record material for virtual presentations

Please report any issues with these instructions [here on github](https://github.com/devconfcz/virtual-presentations/issues).


  - [Using OBS Studio to Record Video](#using-obs-studio-to-record-video)
  - [Alternatives](#alternatives)
    - [Using wf-recorder (for Wayland)](#using-wf-recorder-for-wayland)
    - [Using QuickTime Player (for macOS)](#using-quicktime-player-for-macos)
    - [Using external video camera and screen recording](#using-external-video-camera-and-screen-recording)
    - [Recording audio separately](#recording-audio-separately)

## General instructions

1. Upload your video recording to YouTube (preferably) or any other web storage with reasonable uplink
    - Be sure your video title contains following information: `Talk name - 1st Speaker name - 2nd speaker name`. Please, use mp4 video format.
2. We advise you to use a external microphone (_not_ your laptop's microphone). The audio quality is usually better when using external one.
3. Once you have uploaded your video, go to 'Accepted proposals' on the [CfP site](https://cfp.devconf.info/acceptedproposals/28) to submit the link to your recorded video.
4. If you experience any issues, send us email at [speakers@devconf.cz](speakers@devconf.cz) and we will work with you to figure out alternate options.

_ _ _ _

## Using OBS Studio to Record Video

1. Download the installer for your system and install OBS Studio: [OBS Installation Instructions](https://obsproject.com/wiki/install-instructions)
2. Open OBS Studio and run through the _AutoConfig Wizard_
    1. Select `Optimize for recording` as the focus is on recording our screen.
    2. Select `1920x1080` for the Base Resolution, and `30` for the FPS.
    ![Resolution Settings](./media/resolution_settings.png).
    3. Once it is done testing, click on `Apply Settings`.
3. Next, we will be configuring the OSB settings. Start by click on `Settings`
    1. Click on `Output`
        - Select an output path.
        - Select `mp4` as the Recording Format
        - Select `x264` for the Encoder
        - The bitrate is a fine balance between video size and quality. Generally the default of 2500 Kbps is enough for most demos. If your recording requires a higher resolution/framerate the  Youtube's [Recommended upload encoding settings](https://support.google.com/youtube/answer/1722171) provide a good guide.
        ![Output Settings](./media/output_settings.png)
    2. Click on `Audio`
        - Select your microphone under the `Mic/Auxiliary Audio` setting
    3. Click on `Video`
        - Set the `Base resolution` to 1920x1080
        - Set the `Output resolution` to 1920x1080
        - Set the `FPS` to 30
    4. Note: You can also setup hotkeys via the `Hotkeys` tab to start/stop recordings if you find using the keyboard simpler.
4. Scene and Source Setup
    1. Add the `Screen Capture` Source by clicking the + in the Sources box
    2. Pick the screen you are looking to capture (if you have additional monitors)
        - Right click on the live screen capture with OBS and choose Transform -> Center. Then, right click on the capture and choose Transform -> Fit to Screen
        - Note: Wayland users may run into an issue with OBS showing a black screen. Switching to Xorg is a quick fix for the issue.
5. Alternative to using a standalone camera
    1. Add your webcam to the corner if you want.
        - To do so, you can just click on the `+` and adding a video capture device. Resize as desired.
    2. OBS Studio makes it easy to switch between scenes. If you would like to record a different ‘thing’ for your recording you might want to add scenes and flip through them while recording live.

_ _ _ _

## Alternatives

If the OBS studio does not work for you (e.g. because you're running on Wayland), there are some alternatives.

### Using wf-recorder (for Wayland)

1. Install wf-recorder using your package manager.
    1. For Fedora Linux, and similar
        - You need to enable [rpmfusion-free](https://rpmfusion.org/Configuration) first.
        - Afterwards, install it using: `$ dnf install wf-recorder`.
    2. For other, see installation instructions on the [project page](https://github.com/ammen99/wf-recorder).
2. Set the microphone
    1. Either in your system setings, set the default microphone to the desired one.
    2. Alternatively, on Fedora and similar, you can use `Pulse Audio Volume Control` to setup your microphone.
        - To install: `$ dnf install pavucontrol`
        - To run: `$ nohup pavucontrol &`
        - Ensure your device is available and working in the `Input Devices` tab.
        - For troubleshooting: you can switch your device to appropriate mode in `Configuration` tab.
        - After starting the recording you can set the input on the `Recording` tab.
3. Start the recording.
    1. Run a terminal in a directory you want to save the video in.
    2. Type into the terminal, and confirm the following command to start the recording of both your screen and audio (microphone+from computer).
        `wf-recorder -a -f "my-talk.mp4"`
        - If you have multiple monitors, please select the one you want to record. Type the number and enter to confirm.
        - If you want the recording to end on its own after 20 minutes, you can prefix the command with `timeout -s INT 1200 wf-recorder ... `
        - If you want to start the recording after 5 seconds, you can prefix the above command with `sleep 5 ; wf-recorder ... `
        - E.g. the combination of the above would look like: `sleep 5 ; timeout -s INT 1200 wf-recorder -a -f "my-talk.mp4"`
4. End the recording by pressing `CTRL+C` in the terminal.


### Using QuickTime Player (for macOS)

1. [Download instructions](https://support.apple.com/downloads/quicktime).
2. For recording, follow these [Instructions](https://support.apple.com/en-us/HT208721#quicktime).
    - You need to allow microphone in System preferences.
    - Select correct microphone (please check its output).
    - Please select whole screen for recording (to preserve width/height ratio)

### Using external video camera and screen recording

1. Additionally to screen recording, you can use an external camera and microphone (even from a phone), and we'll put them together.
    - In such case, make sure you record audio (voice) in each recording, so we can match them properly.
    - We'll put the two recordings into a common template ([example](https://www.youtube.com/playlist?list=PLU1vS0speL2Z08BeKSwSqfxPEl3ta5UK3)).
2. We can also make some video/audio adjustments for you if necessary (raise audio volume, wide angle cropping, start-end trimming).
    - If you have any wishes, please mention them in CfP portal form.


### Recording audio separately

Prefered way is for audio to be recorded both together, but it's possible to send your audio track separately (or mix it yourself). You can use [this guide](https://github.com/devconfcz/virtual-presentations/blob/master/Recording-us.md#using-audacity-to-record-audio) for that.
