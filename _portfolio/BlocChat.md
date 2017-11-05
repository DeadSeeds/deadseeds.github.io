---
layout: post
title: Bloc Chat
thumbnail-path: "img/BC_list.png"
short-description: Talk to anyone, anywhere about anything.
---

{:.center}
![]({{ site.baseurl }}/img/BC_main.png)

#### Summary

Let's chat!  Have you ever wanted to quickly communicate with multiple people in realtime over the web?  Bloc Chat is here to help.  Simply enter a username upon loading the site, and you'll be able to chat with anyone, anywhere.

#### Why?

Sometimes simplicity is more important than excessive functionality that will never even be utilized by the average user.  Bloc Chat has two important functions: make a place for users to have a discussion, and allow them to have that discussion.

#### Challenges

Built from the ground up in Angular JS, Bloc Chat uses [Google's Firebase](firebase.google.com) as a backend to store all messaging objects.  The objects store basic information such as usernames and timestamps, but can be customized to hold any information.

The main challenge to building Bloc Chat was how to make new rooms, and how to save the message objects to Firebase.  Google helps us out here quite a bit, as they supply a method for converting the database to an array.  Perfect!  This allows us to add and display our messages and chat rooms in order (among other things).  

The Firebase database also has methods for ordering and adding items to the database.  Leveraging these methods reduces the verbosity of the code.


```javascript
function Message($firebaseArray) {
  var Message = {};
  var ref = firebase.database().ref().child("messages");
  var messages = $firebaseArray(ref);

  Message.getByRoomId = function(roomId) {
    var ref = firebase.database().ref().child('messages').orderByChild('roomId').equalTo(roomId);
    var messages = $firebaseArray(ref);
    return messages;
  };

  Message.send = function(newMessage) {
    //var newMessage = {};
    var ref = firebase.database().ref().child('messages').orderByChild('roomId').equalTo(newMessage.roomId);
    var messages = $firebaseArray(ref);
    messages.$add(newMessage);
  };
```

#### Results

Communication is key!  Bloc Chat is a simple yet powerful solution to easy, platform agnostic communications.
