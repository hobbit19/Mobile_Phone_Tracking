# Mobile_Phone_Tracking
This repository is for source code for some of the attacks defined in this paper (https://arxiv.org/pdf/1703.02874v1.pdf)

The attack takes advantage of phones responding to probe replys with their globally unique MAC address. This can be used to isolate a target and gain information about what their request looks like when defaulting to virtual MAC address probe request broadcasts. Once a fingerprint for the device is created, it can be tracked when on or off WiFi without responding to all requests sniffed on the network.

## Assumptions
This attack assumes the following:
* You know what MAC of the phone you are looking for
* You are in range of your target
* You know if the device is IOS or Android

## Pitfalls
[This paper roughly claims ~80% accuracy on fingerprint techniques.](http://papers.mathyvanhoef.com/asiaccs2016.pdf) Although it does not take into account combining them together OR how good these techniques are for distinguising seperate devices of the same model. That being said, I'm still not sure how much same device types differ from one another in their probe requests.

More testing needs to be done.

## How to use
TBD

## Attack Flow
* If vMAC (Virtual MAC Address) broadcast probe request is sniffed
* Respond with probe response and random SSID-> Get rMAC (Real MAC Address) from their SSID specific Probe Request
* Confirm desired rMAC
* Save vMAC IE tags
* Listen to all vMACs with same tags 
* Start responding to vMACs with confirmed tags in order to track target
