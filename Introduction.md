# Introduction #

Alright, so, this project is focused more on demonstrating good design, and ideally we'll all learn a bit out of it.

# Details #

I've initially started with some things I like to do in XNA. First off, the "draw loop" - I found with some of my XNA projects I would have concurrency issues between the update and draw methods (this would cause "drifting" of objects). As such, I implemented a simpler, more abstract draw function - I pass it "draw commands", which are then drawn, rather than calling draw functions of underlying objects. I generate a list of current draw commands in the update function. This permits me to "lock" the changes of matricies and other information into the draw command - thus, if the update function is called one and a half times to one draw function call, it doesn't matter - the objects that were updated in the half do not affect the information the draw function is looking at.