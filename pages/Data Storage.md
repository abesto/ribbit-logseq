public:: true

- Climate data is analyzed at the scale of years to decades. Yes, we want to enable fast feedback and encourage fast action; but it seems to me that choosing to not (or failing to) provide historical data for the whole lifetime of the project would be a missed opportunity.
- This means storing a ridiculous amount of time-series data. The cost can likely be managed by degrading the resolution of past data
  id:: 62dd74c5-b31c-41e1-b6e5-4bf2d9bffc6b
	- Across time (standard feature in time-series storages)
	- Across geography (merge old data of sensors close by)
- A back of the napkin calculation:
	- Assume 1000 sensors / sensor clusters over a year
	- 4 metrics (maybe CO2, humidity, temperature, methane?)
	- Average hourly resolution over the year
	- That comes out to 1000 sensors * 365 days * 24 hours * 4 metrics = 35040000 (~35 million) numeric data points. That's not considering additional metadata like hostnames, longitude / latitude of the sensors, etc; let's assume the storage system can compress and deduplicate those extremely well and so are negligible. A quick Google search suggests InfluxDB uses 64 bits to store floating point numbers, so worst case we're looking at 35040000 data points * 64 bits = 2242560000 bits = 280 MB
- 280MB per year for hourly resolution at 1000 sensors is *very* not concerning, that's almost free basically. Again, this is not accounting for metadata, or indexes; I don't know enough about InfluxDB to estimate those well.
- Conclusion: this is not looking very concerning, but probably good to keep an eye on, to notice early if we're going off the rails, so that we can respond without losing historical data, which would be a Bad Thing.
- [[Threat Model]] says secure, encrypted, off-site backups are more important than one might think.
  id:: 62dd74c5-a14e-4f90-954b-5fd60aa6178f