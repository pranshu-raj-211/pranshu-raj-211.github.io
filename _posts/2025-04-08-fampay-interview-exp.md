# I had an interview with Fampay

For an SDE internship role, sometime in early-mid March.

I applied to this last year, got an assignment I didn't do in Jan (health reasons), and was given another chance in Feb.

I did some really sloppy work with it, partly due to health reasons, but I documented my process, reasons and tradeoffs in extreme detail. I built the thing using FastAPI and MongoDB, which I recommend if you're trying to make backends in Python (great docs, style).


### Assignment

A simple assignment related to the nature of the role (backend) was given. Tech stacks were restricted to Python and Go; I chose Python because I hadn't learnt Go then (and it's more natural to me). They prefer Django (a large part of their tech stack), but I used FastAPI since I'm more familiar with it, and it takes no time to set up, compared to Django, which should be used in more long-term projects.

It was basically a few APIs combined with a background cron job, where you had a lot of freedom in implementing things. This generated a lot of talking points for me, such as the choice of Database, cursor vs offset pagination, FastAPI internals, cron and automation (celery was new to me).

I had considered not using a monolith, which might be an issue in the interviews, but I did it anyway since the expected load would not be taking the app down anytime soon.

### First round
Technical round (both were technical; you interact with HR a lot with emails and phone calls, though).

This was primarily based on the assignment that I did. 

We discussed how I built the system, tradeoffs for the design decisions, bottlenecks, data modelling, etc. There were quite a few differences in our approach  (MongoDB vs Postgres usage), which we discussed in detail (indexing implementation, pagination and random database internals). 

There was a detailed discussion on data modelling and scaling, which I did decently. Identifying bottlenecks with the growing scale of users (scale backend) and time (data growth - shard) were the main themes of the latter part of the interview.

I briefly touched upon my interest in learning about observability, the issues I have had while debugging, and how it could have made my life much easier. We discussed how Fampay handles this, their stack and how it's changing.

This interview taught me a lot about Postgres internals, Sentry and Temporal. In retrospect, I should have focused on scaling and data modelling a lot better.


### Second (Final) round

I got a call the next day that I had passed the first round (they move fast), and the team was eager to go on to the final round with me. It was a technical discussion round, where I would discuss what I've done so far in tech.

The interviewer was a senior member of the organization, and after introducing ourselves, he jumped into my resume and asked me about the project I'm most proud of.

I picked the trading system that I built in July 2024, explaining the reason for building it (terrible experience with Pinescript and Metatrader, no way to setup logs, debug and test without running it on actual data, lack of documentation and obscure language, small community).

This made me want to build a trading system to execute algorithmic trading strategies written in Python on real-time data. No, it's not a remote code execution thing (like Pinescript). Yes, the algorithms are hard coded and can only be accessed through the source code. This is probably a bad way of doing things, but my use case at the time dictated that I could leave out user-submitted scripts.

I talked about the ingestion pipeline (web socket-based), Pubsub (GCP) and downstream services that were part of this system. I went into depth about each of them, explaining why I built each one of them the way I did. The decisions I made while building the system were terrible, mainly due to my not knowing about stuff back then, and I stated how I would go about creating it now.

After that, it was basically system design questions, which I did not realize because of the context of the interview and failed to answer sufficiently. I was asked to build a feature that supports the RCE (Remote code execution) thing and how it would scale. This was new to me; I got stuck and could not answer.



Quite naturally, I failed this round.

I got to learn a lot from it despite this. This interview taught me how to design things before building (yes, I had not designed the trading system before building it; I didn't understand the backend, and I was an ML guy). I learned to think about how systems would scale, how to do calculations for that, identify bottlenecks in distributed systems, and most importantly, that I don't know anything.



Sometimes, all you need is just a deep conversation with an excellent engineer to get yourself going.


I thank the people at Fampay for allowing me to interview with them and teaching me so much in two short interviews. 

I thank Arpit Bhayani, Hussain Nasser and Gaurav Sen for getting me interested in the internals of systems and giving me the push to go and learn wacky stuff and understand things at a granular level to truly appreciate their beauty.

I thank my friends Chahat Sagar and Ritu Raj for helping me discover tech that I wouldn't have explored otherwise, leading me to learn a lot.