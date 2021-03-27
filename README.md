# iR-APRSISD
## Garmin/DeLorme inReach (or possibly other) KML feed to APRS-IS  forwarding daemon

### Hwaet

This is a KML-feed to APRS-IS forwarding daemon. It was written for Garmin/DeLorme inReach devices, but might work elsewhere too. It polls a KML feed in which it expects to find a point in rougly the form that the inReach online feeds use, with attendant course, speed, and elevation data. It synthesizes an APRS position report for each point found there, complete with course, speed, and elevation data, and sends it to APRS-IS.  If the packet came with an attached SMS message (this happens when you send a message to "mapshare" from your device), the text from that message is included in the APRS comment field.
 
This makes it possible to track an Iridium-based satellite device, say, on aprs.fi with all of the amateur radio stuff.  All you need is a machine -- with the aprslib Python module installed -- attached to the internet to run the daemon, and a device that's publishing a KML feed.

### Set up of Garmin Mapshare

 In order to use this software, you must have a KML feed that gets location information from your device.  Garmin can be told to publish it for you if you have an inReach.  Roughly, the KML feed is available on the "social" tab of your Garmin account.  You'll probably need to enable Mapshare.  You can set a password or not.  if you do set one, you well need to provide this password in the configuration file or on the command line to access your feed.  Once it's turned on, you can click the "feed" link to see the feed URL and a few other things.
 
 ### Set up of the forwarding daemon


 First, download the files here to your Unix machine of choice.  Just cloning the repository would do fine.  You must have or be willing to get Python 3 and the Python aprslib.  Most new enough installs will have Python 3.  With luck, you may be able to install aprslib with something like:
 
 ```
 pip3 install aprslib
 ```
 ... or:
 ```
 pip install aprslib
 ```
 Then do these things:
 
   * Edit the configuration file to contain your inReach username, your inReach IMEI's, APRS SSIDs, and your APRS-IS passcode.  Make any other changes you see fit.  
 
   * Optionally, install the config file in /etc.  You can otherwise leave it in the current directory.
 
   * Run the daemon.  it should begin to scan your KML feed.
 
 
