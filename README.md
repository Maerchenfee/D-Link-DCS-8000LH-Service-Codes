# D-Link-DCS-8000LH-Service-Codes
## D-Link DCS-8000LH Service Codes / Date / Time / IR on-off e.t.c.
The User is: Admin - with no password

In the D-Link forums, people have always wondered how to set the time and date on the camera locally.
To do this, they always tried by mistake method=1 from the 'service codes'.
After a few attempts, I managed to do this under method=2. And BOOM. 

## Before doing so, the correct TIMESERVER (replace the XXXXXXX) should be set:

https://192.168.178.20/config/datetime.cgi?timeserver=XXXXXXX

## The next step for the command date/time is
exchange the timezone (Number) for your Area (google it) ande Time and Date:

http://192.168.178.20/config/datetime.cgi?method=2&timezone=53&date=2026-02-20&time=08:33:30&dstenable=no&dstauto=no

## Now you can open the camera's video stream in VLC Player with your Time and Date.

rtsp://admin@192.168.178.20/live1.sdp

# ––––––––––––––––––––––––––––––––––––––––––––––––––––

## COMMANDS –

## Camera info
/common/info.cgi

## Check wifi networks and signal strength
/config/wlansurvey.cgi
/config/wireless.cgi

## Get stream informations
/config/stream_info.cgi
vprofile1=H264
vprofileurl1=/video/ACVS-H264.cgi?profileid=1

## Network config, e.g. change port
/config/network.cgi?httpport=XXXX&httpexternalport=YYYY

## Camera name, location
/config/camera_info.cgi

## Change wifi
/config/wireless.cgi?essid=Name&passphrase=Password

## Microphone, its gain
/config/mic.cgi?enable=no&volume=0

## Add/delete user or group, change password
The command changes the admin’s password successfully. However, it is not possible then to use that password to log in. I could create a new user in the group Users but only with a blank password.

/config/user_mod.cgi?name=UserName&password=XXXX&group=Users
/config/user_del.cgi?name=UserName

/config/user_list.cgi
/config/user_list.cgi?name=admin
/config/user_list.cgi?name=UserName
/config/group_list.cgi

## UPNP disable
/config/upnp.cgi?upnpav=off&upnpcp=off

## Contrast, brightness, saturation, flip, mirror, etc.
/config/sensor_info.cgi
/config/sensor.cgi?flicker=50&sharpness=40

## Disable motion detection
/config/motion.cgi?enable=no

## Disable audio detection
/config/audio_detection.cgi?enable=no

## LED on/off
/config/led.cgi?led=off

## Infrared off, day mode
/config/icr.cgi?mode=day&night_irled=off

## Reboot, reset
/config/system_reboot.cgi?reboot=go
/config/system_reset.cgi?reset=go

## Get a JPEG image
/image/jpeg.cgi

## Check Date, time
/config/datetime.cgi

## Get URL entry of specified profile 
/config/rtspurl.cgi?profileid=1

## Check video profile
/config/video.cgi?profileid=1

## Change codec of profile 1 to MJPEG stream and back to H264
/config/video.cgi?profileid=1&codec=MJPEG
/config/video.cgi?profileid=1&codec=H264

Watch MJPEG stream, after the codec change, in web browser
http://UserName:Password@CameraIP:Port/video/mjpg.cgi
