# Generic-Video-Camera
Generic Video Camera Live Streaming Video in SmartThings Tile View

Install the 2 smartapps and devicetype in IDE.

Add SmartApp Connect app to your mobile install
Go into SmartApps, Generic Video Camera Connect App
Add Cameras
Either use drop down and edit in the child smartapp in IDE for your cameras
or
use the custom url to add any url to stream.

## Developer Notes

After a week of hacking around while waiting for support to respond to my ticket, I finally figured out how to do local http GET and parse the response for cameras.

So I wrote this nice little generic camera device that I have tested with Panasonic Cameras and D-Link cameras and should work for any camera that has a url to retrieve the latest image.

Requirements:
Code here... https://github.com/pstuart/smartthings-ps/blob/master/devicetypes/generic_camera.groovy1.6k

Edit preferences after install in devices in IDE or on App on phone:

-IP of the camera, this is your local ip, does NOT need to be publicly accessible
-Port of the camera, typically 80 but could be anything
-Path to image, different for each camera
Panasonic Camera is "/SnapshotJPEG?Resolution=640x480&Quality=Clarity"
D-Link is "/image/jpeg.cgi"
Foscam is "/snapshot.cgi?user=${username}&pwd=${password}"
-Requires Authentication or not (if you are going to embed the username and password in the path, do not set this to true)
-Uses GET or POST (defaults to GET)
-Username for authentication
-Password for authentication

Plug in all these values and press the take button and viola, locally access camera will return an image.
