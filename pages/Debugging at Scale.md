public:: true

- Assume there are 5k sensors out there. If just 1% of them has a hiccup at any given time, then individual support for will quickly become a nightmare. This is not a technology problem, this is a culture problem. Of course we should implement as much self-healing as possible (auto-reprovision sensors in the most extreme case), but with experimental hardware deployed who-knows-where under who-knows-what conditions, there will always be a need to solve novel problems.
- Being able to quickly identify the sensor a user is talking about is step zero. Print a QR code with the hostname / some other stable ID on the device? In some way that will not be destroyed by weather?
	- This enables automatically checking how long the given device has been offline, and so automatically triaging support requests by that.
- Community support / self-help will always scale better than a core team, we should encourage that as much as possible. Think: StackOverflow.
- A curated knowledge base of common issues and debugging techniques can be super useful: some users may be able to fix the issues themselves. Plus, both core-team and community helpers can easily point at known procedures.
- Searchable, archived, open logs of debugging sessions are useful as low-effort documentation themselves, so retention + searchability of chat logs matters.
- Much later, there can be value in building automated detection and remediation specifically based on failure modes and manual remediations often identified / applied by humans.