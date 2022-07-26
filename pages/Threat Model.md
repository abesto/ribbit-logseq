public:: true

- # Strategic Bad Actors
  id:: 62dd66f0-1d6e-4bef-8548-a3e85a8ecc1d
- Why would anyone want to hurt the Ribbit Network? Well, anyone whose goals are not aligned with the project, AND feeling like the project sufficiently threatens their interests. What are the relevant goals of the Ribbit Network project then? To provide data to steer and measure the impact of local action and policy.
- I don't think we need to be overly concerned about the "local action" category of bad actors; grassroots movements tend to be on the pro-green side. However, we _may_ worry about government / industrial action at a local level
- ## Local Strategic Bad Actors
  id:: 62dd74c5-2688-4c6e-9b4a-c3821f34e867
	- Physically locate sensors ([[Privacy]] and [[Device Security]] become important here), and
		- Compel the owner to disconnect them
		- Interfere with its operation in some hard-to-detect way
		- Steal it (and then possibly run it in a controlled environment to green-wash the area)
		  id:: 62dd74c5-f4c9-4117-9fa5-4521d1ea2795
			- There should be a **reporting channel** in place for stolen sensors, which should then be possible to **block** in a way impossible to circumvent by a motivated adversary
		- Just smash it up with a baseball bat
	- Outlaw the sensor?
	- Block communications of the sensor at the network (ISP) level
		- Balena gives us a VPN? Fine, block all access to all Balena IP ranges. Run them through a custom VPN? OK, but where's the OOB control channel then?
- ## Global Strategic Bad Actors
  id:: 62dd6cdb-35f2-44d3-bf44-db49774978dd
- Some industries (coal, oil, etc.) and some state actors obviously have the resources, and the incentives to discredit, falsify the data, or outright destroy the data of the Ribbit Network (or the network itself).
- The easiest way for bad actors to eliminate the impact of the project is to discredit its data:
	- Just claim that it doesn't have sufficient [[Data Accuracy]]
		- At its most basic, doesn't even need to provide justification, unless there's a significant amount of proof of data accuracy already available
		- Take a dig at the methodology, the quality of hardware used, custom software used, or any other individual component that seems even remotely suspect
	- Provide competing data. Surely if this serious-sounding scientific institute (that just happens to be quietly and obliquely completely state-sponsored) says THIS data set is accurate and THAT data set is accurate, then it must be so?
		- An obviously good response to that is "yes but the serious-sounding scientific institutes of these twelve other countries think THIS data set is actually accurate"
- If a strategic bad actor is incentivized to take more direct action, there are a few different approaches we may expect:
	- Inject bad data
		- Reverse-engineer the network protocol, inject arbitrary measurements (mitigation: [[Data Provenance]], [[Secret Management]], [[Device Security]] )
		  id:: 62dd74c5-60d8-4e60-ae82-0b7a76efca19
		- Purchase Ribbit sensors, and tamper with them (mitigation: even harder [[Data Provenance]], including at the hardware level)
		- Purchase Ribbit sensors, and run them in environment-controlled rooms
		  id:: 62dd74c5-1219-4252-8ca3-1be9afe72cd2
			- Mitigation: outlier / spam detection methods maybe? This can rapidly turn into an arms race (e.g. detect many sensors in the same location -> fake the GPS location -> detect many sensors on the same IP -> route them through different networks, physically move them to many separate locations)
			- The big question here is: **how would we notice**?
	- Change existing data (again, [[Data Provenance]] can at least partially help here)
		- Infiltrate Fleet Management, CI, or software distribution channels to inject code to "green-wash" reported data
		- Infiltrate central data store and green-wash data at rest
		- Man-in-the-middle at data reporting (assume TLS auth / encryption between the device and central infra is good enough?)
	- Destroy existing data ([[Data Storage]], off-site backups become important here)
- # Opportunistic Bad Actors
  id:: 62dd6668-ed05-472a-ab09-e5df148b5f5b
- These are risks not specific to the Ribbit Network project, but apply to any IoT / distributed home-computing application. The Ribbit Network is technically a bot-net. We should make *very* sure that it doesn't wall into the wrong hands, either directly (an exploit across some / most sensors) or indirectly (via software distribution / fleet management)
- Presumably the sensors would have _some_ access to the private networks of most owners - we don't expect most owners to configure a DMZ and run the sensors there? In which case: we want to avoid being the weak link that allowed hackers access to, dunno, the network storage device with all the kinky videos of that one particular Ribbit sensor owner (or even something actively harmful, instead of just embarrassing)
- Remember: the S in IoT stands for Security