---
layout: post
title: Bloc Jams
thumbnail-path: "img/BJ_landing.png"
short-description: Bloc Jams is a pseudo-Spotify replica, intended for viewing and listening to music.
---

{:.center}
![]({{ site.baseurl }}/img/BJ_album.png)

#### Summary

Music websites seem to be ubiquitous these days.  However, many of them are design nightmares, making
it difficult to navigate and consume information.  Bloc Jams attempts to solve this problem with an
easy-to-navigate, straight-forward design that incorporates a landing page, thumbnail icon album views
and a floating music player.

#### Why?

Bloc Jams is a proof of concept, designed to be the foundation for users that need a customizable website
for the management of audio assets.  As a music supervisor and audio engineer for the past 15 years, I've
seen the problems that can stem from media mismanagement first-hand.  Bloc Jams attempts to solve these
problems through simplicity, with a compatibility footprint as wide as possible.

#### Challenges

It goes without saying that a website focused around organizing and displaying music albums should also
be able to play said music.  Instead of re-inventing the wheel, Bloc Jams uses the [Buzz Audio Library](http://buzz.jaysalvat.com/) to play audio.  Buzz takes care of the audio heavy-lifting across
the website, allowing us to plug into it's JavaScript methods to check for compatibility and play
the actual audio objects used across the site.

Bloc Jams also tries to be as lightweight as possible, so the entire site is written using JavaScript and AngularJS.  The music player itself had a couple problems that needed to be solved: the actual functionality of navigating and playing the content, and displaying that information back to the user in real-time.  

The seek bars in particular were a challenge, and the solution to their display uses offsets from the edge of the webpage itself.


```javascript
function seekBar($document) {
  var calculatePercent = function(seekBar, event) {
    var offsetX = event.pageX - seekBar.offset().left;
    var seekBarWidth = seekBar.width();
    var offsetXPercent = offsetX / seekBarWidth;
    offsetXPercent = Math.max(0, offsetXPercent);
    offsetXPercent = Math.min(1, offsetXPercent);
    return offsetXPercent;
  }
```

#### Results

Bloc Jams is functional and light-weight, forming the basis for customization and additional functionality.  Despite its basic nature, the site can power large collections of assets in any browser that supports HTML5.
