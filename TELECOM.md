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
