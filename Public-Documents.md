jweath said:

So today I had a slightly magical moment: because we have persistent URLs, I was able to email a student a link to a Doc on Marca that they had access to (they can open the link if they're logged in / are asked to log in).

I think this is a really significant feature. Obviously, we've talked about making Docs shared with the world. Is this something that's feasible to build, or does it open up a can of security worms (the wiggliest kind of worms, from my understanding)?

Also, just the functionality as it stands today is pretty potent. I'd love to chat about how to implement this (for example, a "Share" link or "Ask for Review" link that sends an email with a link to the Doc to a peer in the class) for a few minutes, either on Issues or during a dev meeting.

What do you think?
***
From afamiglietti 02/04/13 

Hey John, 

I think this is a good idea. It would be pretty trivial to create a controller for public docs, have that controller only access docs that have been flagged as public, and display them in a read-only way. Then we could move routes for this controller outside the firewall in the security.yml et voila. Public docs. 

I guess the only concern is not so much technical security as making sure student users understand and consent to sharing work publicly, and perhaps designing in ways to allow instructors to allow/forbid public sharing for specific classes of document (say docs in a particular project or with a particular tag). 


