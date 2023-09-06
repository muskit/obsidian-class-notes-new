# Wireless
wireless hosts
- ie. laptop, smartphone, IoT
- these hosts run **applications**
- can be stationary or mobile; **wireless does not imply mobility!**

base stations
- typically connected to a wired network
- acts as **relay**: sends packets between wired network and wireless hosts in an *area*
	- ie. Wi-Fi, cell towers

*SNR (Signal-power to Noise-power Ratio; dB)*
- larger SNR = easier to extract signal; **desirable**
	- higher power = higher SNR = decrease *BER (Bit Error Rate)*

CDMA (Code Division Multiple Access)
- unique *code* is assigned to each user
- all users share a frequency, but each user has a unique *chipping* sequence to en-/de-code data
- users can transmit simultaneously with little interference

*802.11*- the IEEE standard for *Wi-Fi*
- **access points** advertise, along with other info, their *SSID*
- hosts scan for access points on specific channels
- hosts can then *associate* with a desired access point

Collision Avoidance: RTS (req. to send)-CTS (clr to send) exchange
 - reserves frequency for the single sender
 - if collision occurs, sender waits it out
 - once CTS received, try sending