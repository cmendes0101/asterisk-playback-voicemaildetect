asterisk-playback-voicemaildetect
=================================

This is a modified version of `BackgroundDetect()`. It works just like `Playback()` with passive voicemail detection. This is useful in the case of automated calling and playing an audio file on answer. The audio will continue to play unless it detects a voicemail(multiple seconds of chatting on the other line), which will trigger to another extension.
Currently only available for Asterisk 1.6 and 1.8. Might work in later versions but not tested.

Detailed Description
--------------------

By default will playback an audio file and if within 5 sec of answering the call hears 3+ sec of continuous talking forwards the call over to "voicemail" context. If less then 3sec of talk or past the initial 5 sec marker will just keep playing the audio till it ends like Playback().

Installation
============

Copy the VoicemailDetect.c file in to your /ASTERISK-SRC/app/ directory.
Configure asterisk and check `makemenuselect` that the VoicemailDetect module has been added to the list.
Make and Make install.
`VoicemailDetect()` should be available in the `show modules` command in asterisk CLI.

Syntax
======

    VoicemailDetect(filename[,sil[,min[,max[,analysistime]]]])
    
Arguments
---------
*filename - Audio file to playback
*sil - If not specified, defaults to 1000. *Not really used*
*min - If not specified, defaults to 100. *Not really used*
*max - If not specified, defaults to 3000.
*analysistime - If not specified, defaults to 5000.