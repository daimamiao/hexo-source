---
title: Research directions for IOT
date: 2016-07-20 08:57:18
tags: 物联网
categories: 物联网
thumbnail: https://pic.36krcnd.com/avatar/201607/24004958/8a6l5hjpfmw743bg.jpg
---
As each individual system has its own assumptions and strategy to control the physical world variables without much knowledge of the other systems,<!-- more --> which leads to conflicts when these systems are integrated without careful consideration.
### 1.What`s the problem of dependency in IOT?
As each individual system has its own assumptions and strategy to control the physical world variables without much knowledge of the other systems, which leads to conflicts when these systems are integrated without careful consideration. Such problems arise in the cyber part mainly because each application has assumptions on the physical world entities without knowing how other applications work. 

**Let's use an example to better illustrate "what the problem of dependency" are:**

a home health care application may detect depression and decide to turn on all the lights. On the other hand, the energy management application may decide to turn off lights when no motion is detected. Detecting and resolving such dependency problems is important for correctness of operation of interacting IoT systems.

**The problem of dependencies are:**
1. **App interdependency:**  It arises when one app relies on another app. If the independent app makes an error, the error may propagate and affect all the dependent apps and may cause a lot of conflicts in the system.t
2. **Control dependency for the sensors and actuators:**  It arises when multiple apps want to control a sensor in different ways.For example, App1 wants to run a humidifier and App2 wants to run a dehumidifier at the same time.
3. **Missing dependency:**  It arises when app developers forget to specify the dependency information of their apps. For example, App1 forgets to specify its dependency on light L1 in its meta data., but at runtime it tries to control L1.



### 2.What`s the major technologies to address the dependency issues in IOT?
#### Cyber Physical system(CPS)
We can propose a integrated CPS, a utility sensing and actuation system  that provides comprehensive strategies to specify, detect, and resolve conflicts.This system  consideres a comprehensive spectrum of dependencies and treating each system as an app. Each system communicates with its sensors and actuators and performs computations for taking appropriate control decisions to actuate on the physical world entities.

App developers specify dependency  information as meta data within their apps and their apps are put in an app store. Users can choose and install apps from the app store. This system can use the meta-data to detect and resolve conflicts at app installation time and at run-time.

Let`s take some examples to introduce this ststem:

1. **addressing requirement dependency:**  This system reqiures developers to specify the requirement of each app in a manifest file written in XML.just like this : 
``` vbscript-html
<requirement>
	<device>
		<device_type> x10_motion_sensor </device_type>
		<container> room </container>
		<level> strict </level>
	</device>	
	<device>
		<device_type> x10_contact_sensor </device_type>
		<container> window, door </container>
		<level> strict </level>
	</device>	
</requirement>
```
Requirements can be either strict or loose. The motion sensor requirement is strict, which means that the app will not work without the motion sensors.But the app will still work without the contact sensors.

2. **adderssing actuator control dependency: ** Resolving control dependency of the actuators in a wrong way may cause death, e.g, granting an app's request to turn off the breathing machine to save energy while it is being used by another health app.therefore, this system will detect such conflicts when two apps try to access the same device at the same time and resolve the conflict in favor of the higher priority app.It requires app developers to specify in XML`effect`,`emphasis`, and `condition` for each actuator that app wants to control.
* **Effect**
Effect specifies the effect of an app on the environment when using a particular device.Two apps may be using completely different devices, but are conflicting with each orher by causing opposite effects.The XML tags can be increase, decrease, and change.For example, App1 may specify:
```
<device>
	<device_name> humidifier </device_name>
	<effect>
		<humidity> increase </humidity>
	</effect>
</device>
```
On the other hand, App2 mey specify:
```
<device>
	<device_name> humidifier </device_name>
	<effect>
		<humidity> increase </humidity>
	</effect>
</device>
```
When  two apps have an opposite effect, they will not conflict. When two apps have an opposite effect, there is a chance that they will conflict at runtime. When two apps have the same effect, or mixed effect, system will look into `emphasis` and`condition`to determine whether these apps will conflict or not.
* **Emphasis**
Emphasis is based on the insight that not all control operations are equally important to an app, and emphasis allows an app to specify which device operation is more important than others.
The security app mentioinsed above specifies its emphasis for controlling lights:
```
<emphasis>
	<operation> On() </operation>
</emphasis>
```
The energy app mentioned above specified above specifies its emphasis for controlling lights:
```
<emphasis>
	<operation> On() </operation>
	<operation> Off() </operation>
</emphasis>
```
when two apps have the same emphasis, then they are not conflicting with each other. if the emphasis of two apps is different, then they may be conflicting(also depends on conditions).
* **Condition**
Two apps are not conflicting if they operate on a device with a mutually exclusive condition.The conditions can be categorized into two groups: (1)conditions based on time.(2)conditions based on event. Here are some example:
```
<start_time> 20:00:00</start_time>
<end_time> 21:00:00 </end_time>
<night> duration </night>
<sunset> begin </sunset>
```
### 3.What's the questions and gaps that need to be filled in IoT system with examples?
####Security
A fundamental problem that must be solved in IOT is dealing with security problem.It worth to think about 3 security problem as follow:
1. **dependency issues – Do you know when something goes wrong?**
The aforementioned paragraph suggests that resolving control dependency of the actuators in a wrong way may cause death, e.g, granting an app's request to turn off the breathing machine to save energy while it is being used by another health app.
2. **Data Encryption – Is your data protected?**
At a glance, many developers may be inclined to use SSL for secure communications. However, this can be problematic in an M2M application due to the additional processing power and memory required in a device to support SSL, and the increased wireless data costs that are a product of the increase in network communications overhead.
3. **Controlling access – Who can access your data/system?**
While encryption is demanded for private information, in some instances, confidentiality may be far less important than access and authentication. For example, the data transmitted with a wireless command to open your car door may not be confidential, but it is critical that no unauthorized parties have access to unlock the door through that system.

#### Privacy
Despite the immense potential of IoT in the various spheres, the whole communication infrastructure of the IoT is flawed from the security standpoint and is susceptible to loss of privacy for the end users. Some of the most prominent security issues plaguing the entire developing IoT system arise out of the security issues present in the technologies used in IoT for information relay from one device to another. As such some of the prominent security issues stemming out from the communication technology are the following:
**( Wireless Sensor Networks (WSN) )**
1. **DoS attack on the physical layer:**
The physical layer of a wireless sensor network carries out the function of selection and generation of carrier frequency, modulation and demodulation, encryption and decryption, transmission and reception of data. This layer of the wireless sensor network is attacked mainly through 
*  Jamming: In this type of DoS attack occupies the communication channel between the nodes thus preventing them from communicating with each other. 
* Node tampering: Physical tampering of the node to extract sensitive information is known as node tampering.
2. **DoS attack on the link layer:**
The link layer of WSN multiplexes the various data streams, provides detection of data frame, MAC and error control. Moreover the link layer ensures point-point or pointmultipoint  reliability . The DoS attacks taking place in this layer are: 
* **Collision**: This type of DoS attack can be initiated whentwo nodes simultaneously transmit packets of data on the same frequency channel. 
* **Unfairness**: As described in , unfairness is a repeated collision based attack. It can also be referred to as exhaustion based attacks.
* **Battery Exhaustion**: This type of DoS attack causes unusually high traffic in a channel making its accessibility very limited to the nodes. Such a disruption in the channel is caused by a large number of requests (Request To Send) and transmissions over the channel.
3. **DoS attack on the network layer:**
The main function of the network layer of WSN is routing. The specific DoS attacks taking place in this layer are:
* Spoofing, replaying and misdirection of traffic.
* Hello flood attack: This attack causes high traffic in channels by congesting the channel with an unusually high number of useless messages. Here a single malicious node sends a useless message which is then replayed by the attacker to create a high traffic.
* Homing: In case of homing attack, a search is made in the traffic for cluster heads and key managers which have the capability to shut down the entire network.
4. **DoS attack on the transport layer:**
This layer of the WSN architecture provides reliability of data transmission and avoids congestion resulting from high traffic in the routers. The DoS attacks in this layer are:
* Flooding: It refers to deliberate congestion of communication channels through relay of unnecessary messages and high traffic.
* De-synchronization: In de-synchronization attack, fake messages are created at one or both endpoints requesting retransmissions for correction of non-existent error. This results in loss of energy in one or both the end-points in carrying out the spoofed instructions. 

####Data Challenge
The technologies to address the big data challenge already exist, like Hadoop or NoSQL, providing horizontal scalability, high capacity and parallel processing at prices that make them affordable and economical.With the development of wearables for consumers and the emerging use of smart machines the portion of IoT as a subset of big data will grow quickly forcing enterprises to think their infrastructure to enable scalability and to make them cost effective.

####Server Technologies
The impact of IoT on the server market will be largely focused on increased investment in key vertical industries and organizations related to those industries where IoT can be profitable, or add significant value.
Some organizations that manage and consume data collected from a huge array of devices will require additional compute capacity and may well increase server budgets if there is a business case for it.

####Data Center Network
Existing data center WAN (Wide Area Network) links have been built for moderate-bandwidth requirements created by our current use of technology. However, as the amount of data being transferred is set to increase dramatically, the need for expanded bandwidth grows.The result of all this, the research points out, is that because of the scale of the data being created it will no longer be economically feasible to store data at a single location.
#### Reference
[1] S. Munir and J. Stankovic, “DepSys: Dependency aware integration of systems for smart homes,” in Proc. ACM/IEEE Int. Conf. Cyber Phys. Syst.,Apr. 2014.
[2] J. Stankovic, “When sensor, and actuator networks cover the world,invited keynote article,” ETRI J., vol. 30, no. 5, pp. 627–633, Oct. 2008.
[3] Security. http://embedded-computing.com/guest-blogs/5-security-questions-for-your-next-iot-deployment/
[4] Tuhin Borgohain,  Uday Kumar,  Sugata Sanyal. "Survey of Security and Privacy Issues of Internet of Things“.  Fri, 9 Jan 2015.
[5] "7 Big Problems with the Internet of Things". http://www.cmswire.com/cms/internet-of-things/7-big-problems-with-the-internet-of-things-024571.php