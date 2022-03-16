**test access port**

- **Passive** [[TAP]]
	- Is a box with ports for incoming and outgoing network cabling and an inductor or optical splitter that physically copies the signal from the cabling to a monitor port. 
	- Two types
		- copper 
		- fiber optic cabling. 

- Unlike a [[SPAN]], **no logic decisions are made so the monitor port receives every frame corrupt or malformed or not and the copying is unaffected by load.**
- **Active** TAP—this is a 
	- powered device that performs signal regeneration
	- Copper and fiber variants
	- Gigabit signaling over copper wire is too complex for a passive tap
	- Some types of fiber links may be adversely affected by optical splitting.
	- An active function, the TAP becomes a point of failure for the links in the event of power loss. 
	- When deploying an active TAP, it is important to use a model with internal **batteries or connect it to a UPS**.
- TAPs usually output **two streams** to monitor a full-duplex link(One up, one down)
- Alternatively, there are **aggregation** TAPs, which rebuild the streams into a single channel, but these can drop frames under very heavy load.