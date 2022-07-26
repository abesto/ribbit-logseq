public:: true

- # Context
- Assume Ribbit Network sees adoption in line with 80% optimistic guesses. Like, maybe hundreds of sensors in a year, thousands / tens of thousands in 2-5 years. What does this mean for the impact of the project, and what kind of risks would this success create? Doing badly along some of these items would likely limit adoption; I want to explore these risks, _assuming_ adoption goes great.
- ## Why think about this?
- I'm explicitly not proposing solving _all_ of these _now_. You don't get a startup (non-profit or for-profit) off the ground by investing insane engineering into infrastructure for a scale you don't have. If you do, you might never _get_ to that scale. But conversely, by the time you get to that scale, you need to make sure you haven't locked in any then-unfixable errors.
- So the biggest reason to think about this stuff: to identify perspectives that must be kept in mind from day one, on pain of painting ourselves into a corner years down the road. In particular, it'd be good to avoid mistakes that can have disastrous (like, project-killing) impact, AND are prohibitively expensive (in time, money, or both) to fix later.
	- This doesn't need each area to be explored in full depth, but at least up to the point where we can say "this is important to get right whenever we touch it" versus "we can easily change this later".
- There are likely also smaller gains by sorting out, at the high level, what the project needs in each of these areas. This allows steering small day-to-day decisions accordingly, saving small amounts of rework later.
- # Teh Content
- Data Management
	- [[Data Storage]]
	- [[Data Provenance]]
	- [[Data Accuracy]]
- Security
	- [[Threat Model]]
	- [[Central Infrastructure Security]]
	- [[Device Security]]
	- [[Access Management]]
	- [[Secret Management]]
- [[Hardware Changes]]
- [[Privacy]]
- [[Monitoring]]
- [[Debugging at Scale]]