# Need to revise & format this page

So just to give you an overview, we have 2
communication systems on the rover
2.4 ghz for small data and long ranges, and 5 ghz for
larger data and short ranges
We use 5 ghz mainly for video transmission, but let's
talk about 2.4 because that's how we send control
commands
So for 2.4, you need 2 antennas: one on the rover and
the other one is on the base station
Besides this, you need to create a local network. How
do you do that?
Well think about how we are communicating. You
have a router at your house (I assume) and if you look
into it, it either has a..255 or .…0 format depending on
your network mask, indicating the router is your
gateway
So this gateway gives a private ip address to all of the
devices that're connected to it. That way, when I send
you a message, it goes to your router, and the
intended ip address and not someone else's ip
address on the network

You're gonna be doing the same thing. You need a
gateway. Now last year we used a raspberry pi to give
ip addresses to different devices, but midway through
the competition we switched to a router
You'd have to do a bit of research but you can always
ask we how to do all of this if you had a problem, but
essentially, once you hook up the antennas into your
local network with your chosen gateway, they then
have an ip address and so you can send commands


# Drive feed
So yes the Odrives were connected to the fenrir
The camera feeds go from Zed to a pi, to the antenna, to your another antenna in the base station, to your code (Qt is used here)
You’d be using camera transmitters if you’re not going with the zed camera
Haeri knows how to set them up
It’s fairly simple
But if you decide to you with the zed, I highly encourage you to have a 5ghz antenna on the rover and get the camera feed into a pi or Xavier
This is the flow:
Camera streams -> pi or Xavier -> 5 ghz antenna on the rover -> 5ghz antenna on the base station -> another machine (someone’s PC)
Once you set up everything on your local network, all the raspberry pi’s on your rover should be visible from your local machine
If you look at the rover, all the pis are connected to a switch and the antennas are also connected to that switch
Once everything is set up, your last touch is to use ROS domain to set all the nodes that’re communicating with each other one the same domain
So the messages get across, and goes to the correct node


## Ymir static ip address
192.168.1.120


## Set-up 
https://docs.google.com/document/d/1vr03kDDL_s_B2WyPbN4qNAjE8rEJLGopE-6Ka7-C4K8/edit