# ONOS Controller in CORE

## This is the implemetation and documentation for implenemting ONOS SDN controller in CORE emulator  for Master project

### The followings is the architectural overview of SDN network implementation

Finally, another experiment is taken into account for realizing the attachment of BGP network over SDN based
data plane. Network infrastructure for this experiment is described in Figure. There are five autonomous
system interconnected to each other over BGP protocol and SDN technique. The entire data plane of the SDN
network is considered as a single internal autonomous system, which is given as AS number of 100. Rest of the
four autonomous system with AS number 200, 300, 400 and 500 is connected from their respective external
router to Open vSwitches 1,6,7 and 8 respectively.

![Onos](https://user-images.githubusercontent.com/57096728/145960306-b3ee7374-6fb3-4706-8954-b7aa04e791b5.JPG)


ONOS SDN controller runs on the same machine which runs CORE emulator, and all the nine Open vSwitches
are connected to the **ONOS** controller from their eth0 interface. One extra router within the SDN data plane
connected to the Open vSwitch 3 is providing the functionality of internal BGP speaker for the SDN network.
The Internal **BGP** speaker is connected to the SDN controller through **iBGP** peering using the TCP port 2000,
which is default for ONOS controller. ONOS controller application creates intents, which is the border switches
connected to external router of other autonomous systems. These intents allow the external **BGP** routers to establish a eBGP peer using physical devices of the SDN data plane to the BGP speakers that reside in the data plane.
The creation of those intents’s network configuration is done by the **REST API** with a json information. Inside
the json information, there is a section called port, which defines the IP addresses and mac address of the intents
by mentioning the DPID of Open vSwitch and port number connected to the border router of other ASes. Another section in the json information is called app, is used to provide information of internal **BGP speaker**. In this
section, connection point of BGP speaker to the data plane, which is switch 3 and external peering connection
addresses are indicated.
The internal BGP speakers take advantage of eBGP peering to share BGP route information with the border
routers of the neighboring external networks, and iBGP peering to propagate that information to ONOS application instances.

For the Implementation of the network check the documentation: 

[a link](https://github.com/sudo-riyad/ONOS-SDN-Controller_BGP-in-CORE-/blob/042e051c7c38ef6c3e93a98cb1a45815bc38dd18/Documentation/IndividualProject_Islam_Riyad-Ul-_1324662.pdf)


