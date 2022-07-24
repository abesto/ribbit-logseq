public:: true

- Even if we have amazing [[Data Accuracy]], ((62dd6cdb-35f2-44d3-bf44-db49774978dd)) could (attempt to) manipulate data, inject bad data, or just *claim* that these happen. For the data to be useful, we need to be able to prove to a sufficient level of certainty that
	- the data was measured by a known-good untampered Ribbit sensor
	  id:: 62dd8bd9-ed73-44ee-ac54-3f407cd5f6f1
	- was transmitted to central storage with no man-in-the-middle attacks
	  id:: 62dd8bdc-d49f-4d1a-9955-15aefab45798
	- was then not manipulated at rest
	  id:: 62dd8bdf-32a7-4f21-b84f-2307e4ec8a20
	- is then reported correctly to the viewer as it's stored at rest
	  id:: 62dd8be2-0bfe-4c76-af96-fd48000c6857
- I don't know that there's a *solution* as such to these problems, but at the least the measures taken need to be documented and regularly verified.
- # Some Mitigation Ideas
- This is not my main area of competence, but let's give it a go.
- ((62dd8bd9-ed73-44ee-ac54-3f407cd5f6f1))
	- Analyze data
		- For outliers against other nearby sensors? But how about sensors running in courtyards with little air movement? Or how about sensors running near a high-traffic intersection?
		- For outliers against its own historical data? But what about actual real events that can significantly and somewhat-suddenly change readings?
		- Conversely, data that's *too* stable is likely to be malicious ( ((62dd74c5-1219-4252-8ca3-1be9afe72cd2)) )
		- Something something machine learning?
	- [[Device Security]] can provide some level of confidence
	- Hardware checksums? Though sensors need to be field-repairable and field-upgradeable; so maybe introduce an extra step with authentication to accept new hardware?
- ((62dd8bdc-d49f-4d1a-9955-15aefab45798))
	- Two-way TLS authentication and modern encryption should be good enough here
- ((62dd8bdf-32a7-4f21-b84f-2307e4ec8a20))
	- [[Central Infrastructure Security]] is the obvious answer here
	- ((62dd74c5-a14e-4f90-954b-5fd60aa6178f))
		- When taking a new backup, validate historical data in it against previous backup. If there's a mismatch, congratulations, you've been haxored.
			- Except: ((62dd74c5-b31c-41e1-b6e5-4bf2d9bffc6b))
			- So the validation is not necessarily completely trivial
- ((62dd8be2-0bfe-4c76-af96-fd48000c6857)): the approach here should be to set things up such that interested parties can independently verify that the data reported by our visualization is the same data we make available over other trusted channels.
	- Make the actual data source publicly readable. This is a good idea in general, we want people to be able to run whatever analysis they want.
	- Make the visualizations provided by Ribbit Network open source
	- The above two together should make it easy to validate that the visualization layer is not being tampered with.
	- Possibly: provide static downloadable data dumps via well-known third parties with high-quality security measures. Like: a `.tar.gz` on Google Drive.
	  id:: 62dd8ec6-900f-42fb-845d-81372183e934
		- This can then be easily verified about the live data reported by the API.
		- Dumps from different points in time can be compared against each other for inconsistencies, just like backups. Maybe: these *are* the backups.