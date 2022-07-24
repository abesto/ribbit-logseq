public:: true

- The obvious first question is: what's our [[Threat Model]]? Click through for my current best idea.
- Let's then investigate the main (?) central pieces of infrastructure for the Ribbit Network:
	- Fleet Management, Software distribution channels
		- AFAICT the plan is to depend on an existing solution here, so likely not much to do beyond 1. audit that we're happy with their security posture 2. set up correct [[Access Management]]
		- This is obviously a great target for both ((62dd66f0-1d6e-4bef-8548-a3e85a8ecc1d)) and ((62dd6668-ed05-472a-ab09-e5df148b5f5b))
		- Here's a possibly great idea: validate that the hostname reported by the sensor matches the hostname by reverse-lookup via Balena. Block measurements (and notify Ribbit Network / device owner) if there's a mismatch, or if the reported hostname / IP is unknown to Balena.
		  id:: 62dd84e0-ba3b-43ee-a0f3-4e02538d9808
			- For extra defense in depth: generate unique client certificates for each device. Verify the certificate matches the identifying data sent by the sensor. It should not be possible to send data using the certificate from any host that is *not* the sensor the cert was issued for.
			  id:: 62dd89dc-2107-4e95-a7d9-0a9a6faf9f15
	- Data visualization
		- What we *store* doesn't matter if a bad actor controls what we *show*. This is standard web application security, probably not worth going into much detail here.
	- CI
		- AFAICT the plan is to use an existing solution here (i.e. GitHub Actions, or whatever the flavor of the month is in the future), so again:  1. audit that we're happy with their security posture 2. set up correct [[Access Management]]
	- [[Data Storage]]
		- This is the most obviously critical piece. Only interesting for ((62dd6cdb-35f2-44d3-bf44-db49774978dd)). Worth going the extra mile.
			- Maybe: client certificates only issued on extra checks. See [[Device Security]].
			- Definitely two-factor authentication for arbitrary write, admin access.
			- Make extra double super-duper sure the sensors only ever have enough access to append rows of data.
			  id:: 62dd74c6-7d82-457e-ab4e-ebb43d9ba37a
			- Maybe take away metadata reporting control from sensors (hostname? We'll look you up in the Balena database by IP. Longitude / Latitude? We'll use the data the owner told us when purchasing the sensor, and let them know if there's a discrepancy, and drop data until it's fixed.)
	- [[Monitoring]]
		- Not typically an attack surface / target, but should have appropriate [[Access Management]] to ensure [[Privacy]] - this will likely include information we don't make publicly available.