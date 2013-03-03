Hey folks,

I was chatting with Kate over dinner tonight about Marca (how romantic, I know--but I have a wonderful wife!), and I had a stroke of insight as to how to improve our Doc Markup UI.

Step 1:
![Markup overall changes](https://f.cloud.github.com/assets/867379/213806/e4306c2e-83bb-11e2-87df-1b924a7ebc02.jpg)

Add a tabbed nav to our right-hand menu, using this bit of [Bootstrap](http://twitter.github.com/bootstrap/javascript.html#tabs). The three tabs would be Markup, Feedback, and Info.

(Also, as a side note, I've pulled the Save and Cancel buttons to the far right. And, in an ideal world, I'd love to add 15-20px more space above the doc title, but I can't figure out how to do this due to the margin corrections currently in place).


Step 2:
![Markup feedback-grading view](https://f.cloud.github.com/assets/867379/213807/e43bb110-83bb-11e2-8cd7-906425178c36.jpg)

This new Feedback tab would take the place of the "Respond" functionality we had before. The Respond/Review distinction was a confusing one for many of my students. We keep the functionality, but relocate it here. This makes it so you're either a) looking at the document or b) commenting on it. Removing Respond as a separate workflow has two main benefits: 1) reduces confusion for students wishing to comment on a peer's doc 2) reduces confusion for students searching for peers' feedback.

As a secondary bonus (as the photo shows), this also opens up the possibility for a simple initial grading workflow. Only if you're an instructor in the current class, you'd see beneath the "Share feedback" box a second box in which you could insert a grade. (Perhaps inserting a grade would add the label "Graded" to a doc? Also, perhaps our initial gradebook for instructors, then, could be a list of all docs labelled "Graded" with the value from this box displayed? We could withhold this view from students to keep grades contextual for them.)

The grading bit is secondary to this discussion, though I think this might be an elegant solution.


Step 3:
![Markup info view](https://f.cloud.github.com/assets/867379/213808/e43ac39a-83bb-11e2-8544-933a177e77e5.jpg)

The Info panel would be a convenient catchall for all the stuff we'd like to know about a document but that would clutter up the interface to display all the time: Doc Author, Created / Updated, Word Count, Project, Labels, etc. (am I forgetting anything?)



These panels could be mirrored in the doc display: the Markup panel would still show notes (Sara, I know you're against numbered marginal notes as the default, but sometime I'd like to make a strong UI case for them :-), the feedback panel would display feedback given (including, potentially, a grade--this could be the way to keep grades contextual for students), and then the Doc Info panel would be essentially the same (though potentially there could be a button to invoke the "Update Listing" modal).

I think that making these changes would a) keep all the functionality we currently have while b) dramatically simplifying and clarifying the user experience and c) not require too much development overhead.

I'm willing and ready to get started on the work (though I'll likely need a bit of help for the more complex bits), but I wanted to share this with everyone and gather feedback first.