WLED JUCE Controller as a VST3 plugin for a DAW (such as Cubase)

A C++ / JUCE application to control WLED LED controllers. This software can communicate with WLED devices (https://kno.wled.ge/) via both HTTP JSON requests and the real-time UDP DNRGB/DNRGBW protocol.

Features
Various working modes:

Single Colour (JSON): Send a manual or automated colour and brightness to a specific WLED segment.

Multi-Controller UDP (DNRGB/DNRGBW): Efficiently send solid colours to multiple WLED controllers simultaneously via UDP (without HTTP overhead).

Presets: Directly switch between WLED presets (0-250) including brightness control.

Segment Mixers: Manage multiple segments simultaneously via an 8-channel mixer or a detailed 1-channel view.

Automatic Record Reaction: Optionally have a segment automatically react to an active recording state (for example during recording in a DAW) with a configurable colour and brightness.

Connection Diagnostics: Built-in ping and status check to instantly verify if the WLED controller is reachable and which firmware version is running.

Technical Components
The codebase is built around the following main components:

LightsAudioProcessor & LightsAudioProcessorEditor: The core logic and graphical interface built with JUCE.

WledLookAndFeel: Custom styling for sliders, buttons, and segments.

WledSegmentSender & WledPresetSender: Background threads for handling HTTP POST requests to the WLED JSON API.

WledDnrgbSender: UDP real-time sender that automatically splits large LED strips into packets within the protocol limit (max 489 LEDs per packet).

WledStateFetcher & WledConnectionTester: Background threads for fetching the current status and testing the network connection.

All is still very basic but in a working state..
The interface is mostly in Dutch, will change that later...
