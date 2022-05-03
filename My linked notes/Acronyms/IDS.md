**Intrusion detection system**

 is a means of using software tools to provide real-time analysis of either network traffic or system and application logs.

**network-based IDS** ([[NIDS]]) captures traffic via a packet sniffer, referred to as a sensor.

- **analysis engine** is the component that scans and interprets the traffic captured by the sensor with the purpose of identifying suspicious traffic. 
	- Determines how any given event should be classed, with typical options to 
		- ignore
		- log only
		- alert
		- Block 
		- The analysis engine is programmed with a set of rules that it uses to drive its decision-making process. There are several methods of formulating the ruleset.
			- Signature-based detection (or pattern-matching)
			- Behavioral-based detection means that the engine is trained to recognize baseline "normal" traffic or events. 
				- User and entity behavior analytics [[UEBA]] **anomalies**(anomaly)
				- Network traffic analysis [[NTA]]
				- Often behavioral- and anomaly-based detection are taken to mean the **same thing** (in the sense that the engine detects anomalous behavior). Anomaly-based detection can also be taken to mean specifically looking for irregularities in the use of protocols.
#PBQ
[[Intrusion]]