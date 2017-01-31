---
layout: post
title: Bloc-Jams
thumbnail-path: "img/bloc-jams.png"
short-description: Spotify Replica - Music Player

---

{:.center}
![]({{ site.baseurl }}/img/bloc-jams.png)

## Explanation

The Bloc-Jams project was my first project using HTML, CSS, and JavaScript. This project's aim was to familiarize myself with these concepts, and build a responsive site.

## Problem

The assignment was to build a Spotify replica using HTML, CSS, and Javascript.  The site was to be responsive by implementing our own grid system.  It had a player bar, basic music player functions like *play*, *pause*, *next* buttons, and *seek bars*. This site had a landing page with simple animations.

## Solution

In order to accomplish the given assignments, there was much to learn. First, making a site responsive was necessary as it could be viewed on a number of different devices.  While grid systems like bootstrap exist, I had to implement my own. This involved a series of classes that corresponded to different page widths. This enabled a class called `column.fourth` to have a width of `25%`.

 In order to have a functioning, interactive player bar I used JavaScript.  This involved having `click` events, `hover` events, as well as event bubbling and capturing. One particular interesting point of this project was making it so that if a child class was hovered over, the event would bubble up and trigger a response from the parent class.   For example, if a row was hovered over, part of the view would change, having a *play* button appear. This was made possible with this line of code.

``` javascript
var onHover = function(event) {
      var songNumberCell = $(this).find('.song-item-number');
      var songNumber = parseInt(songNumberCell.attr('data-song-number'));

      if (songNumber !== currentlyPlayingSongNumber) {
          songNumberCell.html(playButtonTemplate);
      }
    };
```

This is just one of the ways that events were used. It showed me first hand how to make a simple feature more interactive for the user.
## Results

The site was a success in the end.  It was responsive with the use of the grid, and had an interactive player bar that could control music.  JavaScript proved to be a powerful tool in this project, as it made interactions feel fluid and happen real-time. The **buzz** music player library was used in conjunction with this project. It had useful functions that could control different audio files.  

## Conclusion

In conclusion, I think the biggest lessons learned from this project was the use of CSS, and JavaScript with making it interactive.  I learned about grid systems, making sure the site looked good on multiple browsers and devices, as well as CSS fundamentals.  JavaScript events showed me how open could implement JavaScript into a project to enhance the user experience. Without it, the site would feel static and uninteresting to the user.
