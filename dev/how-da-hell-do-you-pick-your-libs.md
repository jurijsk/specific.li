![fish](../images/fish.png)

Will try to give some context. The thing I'm building is a browser plugin (because the browser is a new OS and you need to be where your clients already are). I expect that users might have a couple of instances running simultaneously in different tabs. Plus, updates might come from the server, as your collection can be edited by someone else.

I'm struggling to make sense of the JS zoo you people created in 6 short years while I was moving rectangles in Sketch and Figma!
When I was leaving my IDE and magnetic keyboard behind, I was thinking: "jeez, this `webpack` thing makes me want to lick post stamp for leaving, I'm outa here!".

And now I do not even know where to start my 'nmp', 'yarn' or `yank` it all together!

 Library fatigue is settling in on me.

I understand the purpose of GraphQL, it's SQL for cool kids and you do not need to create a gazzilion of endpoints. Then I need to have something on the backend. I think I can get away with JSON file in azure storage and call it a day. One file per user, yank it to the client-side on first request, and then update as needed. I'm not expecting it to be huge. Later I will figure out something more sophisticated, cos I want to have a change history so that users could roll back the changes. Can I do that with GraphQL? Btw, who should deal with auth?

Then I need something to consume, as one might say, that GraphQL API. `Rxdb` looks promising, tick a lot of boxes, but then 'React Query' shows its face in my browser and is like 'hey kid, wanna read this 42 articles'.

How do you decide on libs, bruh?

I'm not looking for a 'batteries included' solution, that would be nice though. I can deal with some 'assembly required', but boy this is a lot!

Does anyone have a solution? People? Anyone? 

Help, I need help.
