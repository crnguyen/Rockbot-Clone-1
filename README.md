# Rockbot-Clone

#### Final - Progress Gif
![GIF](https://media.giphy.com/media/G8axfofNOXuCOBKDrl/giphy.gif)

# Sprints
---
## Day One
- Install Vue
- Setup components and styling

## Day Two
- Fetch data from Rockbot API
- Display data on page
- Finish NowPlaying component
#### Progress Pic
<img src="https://i.imgur.com/jvJLmW4.png" alt="imgur" width="450"/>

## Day Three
- Completed NowPlaying and Queue components
- Worked on styling components
- Created event listeners and a counter so user can like artists
#### Progress Pic
<img src="https://i.imgur.com/YK9sLWw.png" alt="imgur" width="450"/>

## Day Four/Five
- Work on Request component including API call
- Figure out how to switch components on button click
- Set up Top Artists component and implement it on the Request component

# Challenges
---
Some challenges that I initially had were installing webpack, including the ability to upvote an artist in the queue and add an artist from a search to the queue, and having components auto refresh every 30 seconds.
#### Webpack
I installed vue without webpack at the start of the project, but that caused alot of errors. I eventually learned that it's better to install webpack and set it up at the beginning of the project. This was my first time working with webpack so it was definitely a learning experience. 
#### Ability to upvote an artist in the queue
As for the ability to upvote an artist, I created a counter which worked. However, I realized my mistake was including the counter as part of the loop. Each time I upvoted one artist in the queue, the counter would add one upvote to all of the artists in the queue. 
#### Add an artist from a search to the queue
I ran out of time on implementing this, but the main challenge was getting a button click event to add a particular artist to the queue. I did not know exactly how to implement this, but the idea was to have the queue be an array and having the button click event push an artist to the queue. This would involve having 2 different components interact with each other, which is something I'm not yet familiar with in Vue.
#### Auto refresh components
This seemed like a pretty easy fix, but I also ran out of time on this as well. I did some research and it seems like the general consensus is that the best way to implement this is to use window.setInterval(). However, I wasn't sure where exactly to add this portion into my code.
# Edits/Features To Add
---
- Webpack
- Ability to upvote a singular artist in the queue
- Ability to add an artist/song from a search to the queue
- Auto refresh Now Playing and Queue section every 30 sec 
- Go back and fix syntax of code/remove white spaces/extra comments

Resources Used
---
- https://mdbootstrap.com/docs/vue/components/buttons-social/