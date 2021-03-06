GeoHopper Multi-User Virtual Presence Updater for Hubitat
=======
<br>
GeoHopper is an app for iOS and Android that uses either device GPS or
Bluetooth LE to GeoHopper [iBeacons](http://store.twocanoes.com/collections/ibeacons). This device
driver and SmartApp will allow you to use Bluetooth on your mobile
device to set presence in SmartThings. This means you can now get accurate
presence without using GPS and without using a presence sensor.

Requirements
------------
To get started you'll need:
- [GeoHopper](https://itunes.apple.com/us/app/geohopper/id605160102?mt=8).
- An iBeacon (Optional; or you can use GPS in the GeoHopper App). 
- Hubitat Hub
	- [A Virtual Presence Device](https://github.com/ajpri/STApps/blob/master/devicetypes/ajpri/virtual-mobile-presence.src/virtual-mobile-presence.groovy)
	- A Hubitat app assigned to your Virtual Presence Device

Installation
--------------------
1. Go to Drivers Code and create a new device using [virtual-mobile-presence.groovy](https://github.com/ajpri/STApps/blob/master/devicetypes/ajpri/virtual-mobile-presence.src/virtual-mobile-presence.groovy).
2. Go to Devices and create a new virtual device '''name it whatever the location name will be called in
GeoHopper with a - and a USER after it'''. Mine are called "Virtual Presence-Brian" and "Virtual Presence-Spawn1".  Network Device ID can be
'''VIRTUAL_PRESENCE_1''' for the first. Device Type will be
the type you configured in step 1. For this example, mine is named "Virtual Presence-Brian" and my
Geohopper location in #8 below is named "Virtual Presence". You can create multiple
virtual devices and give them different names after the "-" then you can
reference them after the location below in #5 and use that new webhook in #8.
<b>There should be no space before and after the "-" in the device name!</b>
3. Go to Apps Code and
create a new App from code geohopper-presence.groovy. Save it. Click Oauth.
4. Grab the API Token and Endpoint URL from the install window.
5. Copy the Endpoint URL and alter it to have your name after /location/. This will be your URL to configure in GeoHopper.  It should look 
something like this (without the []): https://cloud.hubitat.com/api/xxx-xxx-xx-xxx/apps/xx/location/[your user]?access_token=adafae03-0330-4aeb-b15e-xxxxxxxxx.  For the example in #2 above, [your user] is Brian. <b>If  have "me?access_token=xxxx</b>
6. Now paste this URL into your browser and make sure you get the following
response:
<code>["Yep, this is the right URL, just put it into GeoHopper Web Hook, set to POST and do a test. Make sure your GeoHopper location name matches the device '<location>-Brian'"]</code>
7. Install GeoHopper app and your iBeacon (optional).  In the app, go to Settings->Web
Service and configure a new web service using the URL above and 
select "Post" (text yourself the url and copy/paste it). You can
select Execute Locally if the server will be on the same network your mobile
device is on when the triggers need to run, but I always use the external URL
in situations where location will be outside my wifi range. 
8. Configure a GeoHopper location or rename your iBeacon to be whatever the
name of your device was in step 2 (minus the "-Name" part since that will get
passed on your webhook URL).  For this location, enable your web service
and perform a test.  It should perform the "On" or "Present" action (check your
 Hubitat device to make sure you see the logs rolling in.  If not, make sure
you have your URL correct in the GeoHopper app. Make sure step 7 completed
correctly.
9. You should now have a virtual presence sensor that you can tie to
Hubitat actions. 

Bugs/Contact Info
-----------------
Bug me on Twitter at [@brianwilson](http://twitter.com/brianwilson) or email me [here](http://cronological.com/comment.php?ref=bubba).


