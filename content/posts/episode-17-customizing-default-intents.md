---
date: 2019-11-11
title: Episode 17 – Customizing Default Intents
category: podcast
---

Voice experiences have a number of default intents, such as yes/no, stop, cancel, and others. It is important for experiences to customize these default intents in ways that make sense for the context the user is in. Guest Dustin Coates shares a lot of ideas for how to customize these intents and what to consider to make optimal user experiences.

<!--more-->

{{< podcast-embed src="Customizing-Default-Intents---Dustin-Coates-e6njc2" >}}

### Guest – Dustin Coates

{{< figure src="/images/dustin-coates.jpg" class="guest-photo" >}}

Dustin Coates is the Voice Search Lead at Algolia, author of Voice Applications for Alexa and Google Assistant (Manning Publications, 2019), and co-host of the VUX World Podcast. A Texan, he lives in Paris.

### Links

*   [Twitter](https://twitter.com/dcoates)
*   [LinkedIn](https://www.linkedin.com/in/dustincoates/)
*   [Voice Applications for Alexa and Google Assistant by Dustin Coates](https://amzn.to/2MwjpXL)
*   [Voice Interaction Design: Crafting the New Conversational Speech Systems by Randy Allen Harris](https://amzn.to/2IIJdPn)

### Transcript

Jeremy Wilken  
Welcome to design for voice. In this episode, we're going to be looking at the default intense that exists in many voice experiences and how you may want to customize them for your particular experience. Today, I'm joined by Dustin coats, who's the voice search lead at algolia. Welcome to the show.

Dustin Coates  
Hey, Jeremy, thanks so much for having me.

Jeremy Wilken  
Why don't you give us a bit of your background and how you got into working with voice?

Dustin Coates  
Yeah, I am the voice search lead at a company called algolia. You've used us before, even if you don't know us, we power search and discovery inside apps and inside sites as well. So if for example, if you've ever searched on Twitch, you've actually used us because we power their search. And what we're seeing is that increasingly, our customers don't just want search inside their websites or inside their mobile apps. They also want it inside their voice apps as well. And so that's How I got to work on voice at algolia. But I've been in voice for a couple of years before that it's been a long standing interest of mine, I blog about it for developers. I host a podcast as well called VUX world and have written a book on how to build this as a well for for developers and developer minded people, and have been lucky to combine all that together. And so what I do today,

Jeremy Wilken  
I like this, because this is something very tactical for everybody, we need to always bring these default intense to the table because they're often there by default already in the platform. And there's some cases where we need to really understand how they behave in case we need to modify their behavior for our own needs. So I wanted to start asking you first just at a high level, why would you want to customize some of these high level intense and maybe describe a bit about how it actually works?

Dustin Coates  
Yeah, you'll want to customize These high level intense, because what people are asking for are is going to be different depending where they are in the conversation or in the interaction. They might be using the same words that they used earlier or in a different states, but they want completely different information. Or at the very least, you should want them to have different information. So we'll certainly look at the specific ones. And how you do this will depend on what you're wanting to do. And some situations, you are simply changing what you're saying back to the user. While in other situations, you might change the behavior entirely. And that intent might be doing one thing in one state and doing a completely different thing and another state.

Jeremy Wilken  
Great. So we know that this is a One thing that you can do through the platform itself, there's depending on which platform you're using. And there's different tools that the technical implementation of it's more or less the same. But there's nuances there. Could you describe, though a little bit more about how you can override these defaults? And what what the limits are?

Dustin Coates  
Yeah, in most situations, and most of these platforms, you're actually expected to so called overwrites the intense you're supposed to define how your application response. So certainly, we have the two big ones. We have the Alexa we have Google Assistant. And so if you think of it from that different kind of perspective, you have these intense and you have these different handlers in your code, where you're saying, This is what my intent, how I'm going to respond to this intent for this given state or this given situation. So with the

Jeremy Wilken  
list that we've built up, there's a couple of different ones, they will be very obvious generally about these high level intense. And I'll list a few of them real quick. But then I want to dive a little bit deeper into the nuances of some of these, especially how they become customized in, as you say, in these different states or in these different scenarios. So a couple of them are help intent or cancel or stop intent. There may be a yes and no intent to, you know, confirm or deny a user's preference or answer questions. So those are the kinds of high level intense that we're talking about. They're often simple utterances that someone might say, like help versus a long drawn out request. And so that's why they tend to be high level and default already inside of the platform. So let's take a look at the first one, which is help and when we talk about the help utterance and and providing help and assistance to the user. What kinds of things should people consider? And when should that be applied?

Dustin Coates  
Help is an interesting intense because if you come from a web background or an application development background, you generally have one help. You generally have that one central area where people go search for intense you think about a websites, you think about a mobile app, someone clicks on help. It's not dependent on where they are within that website or within that web app. And it doesn't have to be and we think about this from a conversational perspective and say, How can we do better? So you are going to want to tailor that help intent, based on what you know about the user. The most obvious thing that you know about the users where that user has been recently, what's the last intent that that user has seen were in that country. Is the user to give you a specific example. If I start off the interaction, and I say, help, or if I say what can you do or what is possible? In that case, you're going to want to give a very general idea of what the user can do. If we change it, though, and the user is already in the application, if the user, let's say, within a banking skill, and the user is transferring money in that situation, when the user asks for help, you want to provide information want to provide help, that is tailored toward transferring money. And that way you're taking into account. Hey, this is what I know about the users conversation. Let me tell her that Another thing that you can do as well is you can also bring in information that you know about the user's lifetime experience with your skill or your action. What I mean by this is, if you find that the user is asking for help multiple times, you can use that opportunity to get more precise about the kind of help that you're offering. This is the same thing that you would do with a fallback intent or an error state, this progressive disclosure where you're going to say, Okay, well, clearly the help that I have given you so far, isn't what you need right now. How can I be more specific or tailor it to you? And that way, if someone comes and says help, or what can I do, and you know that they've interacted with the transfer money, functionality, and they've With the gets balanced functionality, you can remove those from what you're going to say. And you can instead say, Well, here's what you can do. You can, you can deposit money, you can ask for money from someone else. So you're not telling them something that they already know.

Jeremy Wilken  
So there's the context of all right, I need help in this very moment, which you can detect based on their, the progression through the scalar action or capsule or whatever. And then there's more general broad type things. And both of those can still be informed by what the user has done. And I think that makes a lot of sense. I want to be able to tell them about things they haven't discovered yet, versus informing them of the base thing that they already have recently just been through unless they're actually in it and struggling with it at that moment. So there's the other things I think we mentioned, like the ability to check for different utterances to map to the correct type of Help. And so that may mean you expand your help veterans, an intense lyst to more than one thing, instead of just help you might have I'm confused. And that might handle a different type of help from what can I do type help?

Dustin Coates  
Yeah. And you could even split these off into different intense and handle them differently based on where the user is, let's say help my and tell Help. Help me, I'm going to fuse. Those are your base help utterances that will map to the help intense, but then you might have a different intense called the functionality intense or what can I do and in that situation, you might indeed have a general response for what can I do no matter where the user is in the flow, however, you're allowing the help one To change based on where the users and the flow, so if you're in that base state as a user help, and what can I do might be the same. Whereas if you branch off and you're in the process of transferring money, help might be specific to transferring money. And what can I do might be general about the application. It depends really on what you're trying to build. But that is something you can do, where you don't have to say, you know, what these intense are always going to be the or these utterances are always going to be the same intent, just because they match the same functionality in the base case.

Jeremy Wilken  
I think this is a very good nuance, and it's really the core of much of our discussion today is the nuance of what these different simple utterances mean in different contexts throughout the application. So let's take a look at another pair of utterances which are cancel and Stop. And knowing that in some cases, there's a good reason why those are essentially the same thing. And then in other cases, they'll be completely different. So give us a bit more of the detail around the the role of cancel and stop as a global intense. And then we'll talk about how we want to customize them.

Dustin Coates  
Yeah, this in my mind is the canonical example of two intense, that can be grouped together. But they can also be broken out as well. In that global state in the sort of bear states, cancel and stop are probably going to be the same think if a user says launch the voice application. And then the voice application respond says What do you want to do this? This is what you can do, etc, etc. And the user responds with cancel or the user response was stop. We can assume that those are the same thing. Those are going to exit out of the skill. However, once you get into the experience once the user starts doing something, stop and cancel can mean very different things.

Jeremy Wilken  
Yeah, when one of the examples we talked about was earlier was the bank transaction. So let's talk through an example using the bank transaction sometimes saying cancel sometimes saying stop and what the differences would be.

Dustin Coates  
Yep. So this is an interesting one, because this might be a situation where even in the global state, cancel means something different than stop, right, you can cancel a transfer that's already out there that you've already initiated. And in that situation, if somebody comes and hasn't done anything else, but says cancel, you might actually want to move them down into the user flow there. However, you can also So think about it in regards to, I'm in the process of setting up an account. If I say cancel in the middle of that, that might mean or likely means that I want to start over I want to go to the lobby, so to speak of this voice application. However, if I say stop, that probably means that I, I want to exit out of there I want I want to leave. And you can think of it in a gaming situation as well. When you say stop in a gaming situation. That might not actually mean leave. If you are saying doing a wheel of fortune type skill, and someone says stop, that might just mean stop spinning the wheel.

Jeremy Wilken  
Yeah, so we have to think through there's cases where that maps perhaps to an action which is like cancel something, cancel a transaction, for example, or cancel meaning. Get me out of this flow and bring you back to the starting point. or cancel is I just want to get out totally close it and thing as designers, we have to be able to call that out. Because a lot of time in development that stuff can be easily glossed over and missed. Because if you're just building these generic, intense do you think, okay, anytime someone says stop, they want to get out of it? Well, you have to really identify these cases. And it's probably never going to be completely perfect, but that that intent can shift over the course of the experience from meaning exit to stop the spinning wheel or, you know, whatever the case is. So these are like moving targets depending on the situation and scenario that we're in in that particular moment. And designers really need to be the first to try and call that out. But even as you do testing and usability checks with actual users, you'll likely see them use these common utterances in ways that you didn't expect. And that's why if you can catch them early, it's It should help you build a better experience from the beginning.

Dustin Coates  
Right. And it really requires you to get out of your own head in a lot of ways. It's so dangerous when you're building anything and code really that users are going to end up interacting with. You knows so much about the internals and how things should work, that if you aren't able to step away from that, then you're going to miss these nuances.

Jeremy Wilken  
Speaking of more nuances, there's the back and next pair. So the next one we want to take a look at is sometimes people say back or next, and there's cases where that's obvious what they want to do. In other cases that may be less less clear. So what cases are those most applicable to and what do we need to consider when using them?

Dustin Coates  
Yeah, I listed these in the list of intense that you should customize. Because this is one where back especially you need To be keeping track of what users are doing as they go along with it. And this is not something that is built in automatically, right? It's not something that Alexa or assistants will give you and say, Oh, this is the entire flow that they've been in and just step back, as you need to know this is something where you might need to keep track of that flow as the user goes through it for that session. Whether you do it one step two steps, three steps, or all of the steps doesn't really matter. But if you have a situation where the user can go back, and they might not be going through a predefined and rigid flow, you need to keep track of where the user is. Then next one is interesting because this is one that isn't really applicable to all voice applications. You may have a situation you likely have a situation where It does not make sense to say next, or it's not very clear where the user wants to go when they go next. And now, if you do have a situation where you understand what the user means when they say next, that's again, where you need to define that in code and say, this is where they were. They said next, this is where that means they should go. However, if it's not at all clear, just you're going to fall back to ask him a user. You said next, where do you want to go? What do you want to do? Or you just say I, it doesn't really make sense. You're not going to use this language, of course, but it doesn't really make sense to say next era, what is that you want it to do?

Jeremy Wilken  
It sounds these are both examples of wanting to navigate, right? You want to go somewhere you want to, if we think in physical terms and real space, we that's how we usually use language. Even on the web, we go to a place We, we go forwards and backwards in our browsers, we kind of translate that same language into voice. And so it's probably not just going back or next or previous. But also, you know, go to go to home, go to help, you know, these kinds of statements indicate movement and transition into a new place, so that you can get you to take a new action or start over, but they might be voicing that thought, in movement language. And so that might be another thing to add into the mix. It may not be a it's not a default, high level intent. But it could certainly be a way that you think about listing some of your utterances that might be applicable to matching either help or, you know, stop or back next, those things might be the actual intent, but some of the utterances might be very movement oriented.

Dustin Coates  
Yeah, and one thing that's actually interesting here, is that this might very well be a signal And you should certainly test it. But this might be a signal that you are being too wordy and you're giving too much information. This might be a user actually telling you, you know, you don't really care about what you're saying right now, give me to the next piece of information, especially if it's a situation where it's a voice search type of situation. They might be saying what you've given me isn't what I'm looking for.

Jeremy Wilken  
That makes total sense. And you know how well you can barge in and override what the system is saying that the time is dependent on on the scenario but another big set of intense are yes and no intense which do exist typically at a high level and yes or no, it's fun, because it makes such an interesting challenge when you're trying to engage with the user because yes and no, are often utilized in ways that you weren't necessarily expecting and you got to be ready to at any moment's notice to figure out what exactly does a yesterday And this question. So with this, how, how do we want to handle the so no type responses and customize them throughout the lifecycle?

Dustin Coates  
The yes or no really depends. This is, in my mind the most obvious that you need to customize the response here. And that's because generally when someone is saying yes or no, you expect them to say yes or no, and that's moving the conversation in the in a specific direction. It's it's branching off, based on whether they're saying yes or no, certainly, you know, you have not heard a VUX related talk without someone mentioning, the, the situation where you say, do you want to do X or do you want to do y? And the user says yes or no, I'm a little skeptical that this is really happens. I think people are smart enough, or not necessarily smart enough, but they're tuned enough to what that question really was asking that they'll generally pick that up. But nonetheless, we do know that, that people act in ways that we don't expect. And in situation, yes or no. You need to understand anytime you ask a question that in may simply mean, I need to repeat this because I wasn't very clear the first time.

Jeremy Wilken  
Yeah, the questions are really important, because the way that you phrase questions can easily reduce the cognitive load on the user to understand what is it that I need to say in order to generate the next turn in the conversation? Where yes and no tend to be default fallbacks? But if you could listen to people's tone, they might be like, yes, but the question was vague. They're just trying to affirm that they'd like to do something. So they'll say yes, no, and you get the maybe the tonality and human interaction, which you don't necessarily get through the systems, at least not today. So those yes and no intense might be unexpected and Some cases because of poor language and prompts or in the conversational flow that you've written, so paying attention to those at the beginning, should help reduce the need for yes and no. I think On the flip side, we talked about a little bit before the show about how you could get a little irritated by constantly asking yes or no type questions. unary want to overload questions or prompts or turns that are simply just stating Yes, no back and forth. Otherwise, it feels like an interrogation.

Dustin Coates  
Yeah, yeah, absolutely. And

there are certainly better ways to split up if you need to find a lot of information. There's better ways to split that up, where you might have a free form type of answer and between a couple yes and no so that it doesn't become so monotonous,

Jeremy Wilken  
certainly, and then those are the a lot of the high level ones. There's a few more that sort of linked to some of the other ones. One being startup Which I think is similar to like, cancel, but could be more nuanced in some cases. So what do you think about using start over as a high level?

Dustin Coates  
I think start over makes sense. And again, it depends on what your voice application is. This is a so called one shot where I asked for information I get information back sort over may not make sense. But you probably still want to account for it anyway, just because people might get used to it. But certainly, in situations where you're getting a lot of information, or there's a number of different steps, then start over can make sense. The interesting thing is, so this all came about, I posted this on LinkedIn and someone commented. Unfortunately, I'm going to Mangle the name but Richard was just was just so I believe the name is and he said Good luck determining exactly where the start of the conversation or sub conversation is for the various users. And this is a good point, if you are not doing a flow chart based application, which increasingly people are seeing that this doesn't work for most situations, then start over might not make a lot of sense. Or rather, it might be difficult to determine what start over actually means. On the other hand, a lot of times when you're building applications that don't shoot to a flowchart, they do whew, two more frames, and then start over can be within the context of that frame. I want to start over this specific, more soul of the overall application.

Jeremy Wilken  
Right, I want to start over the transaction I you know, I don't want to cancel, I just want to start over and reset the data because maybe I put the wrong value in at the beginning. And it's just easier to start over than it is trying to like navigate through and edit one piece of that information right. There was another one around answering questions like, what or did I hear that right? or general questions that might lead to help related content, but could also just be misunderstanding on the user's part trying to ask for clarification? Do we have any suggestions for those?

Dustin Coates  
Yeah, I think that's something where there might be its own separate intent when we were discussing earlier. Yes. And no. I could also see, and I don't know, I don't know how often users are going to say, I don't know to, to a voice assistance. But if you're asking for a piece of information, especially if it's a piece of information that they might not have at hand, so let's say for example, I'm getting a lot of podcasts advertisements lately about life insurance. And so let's say that one of these companies decides to create a get a life insurance quote on on one the on these voiceprint Arms. You can easily imagine where they say, Okay, what was your BMI? And the user says, I don't know. In that situation, you want to handle that. Because either you ask other questions that will still get you to the same end goal. Or you say, Well, here's how to define your BMI. You take your height, you take your weight, etc. And so in that situation, I don't know or what or I'm not sure. Those might be grouped together to be a type of help. Help signal even if it's not the classic Help Help signal.

Jeremy Wilken  
Yeah, it could be clarification better prompting slightly longer explanation or could even be things like people lost focus for just a moment, and they're coming back and saying, I'm sorry, what and we do that Is all the time in regular human human conversation. So those things can occur as well and invoice assistance, although that happens more likely in longer form experiences where there's a lot going on, which is still I think fairly nascent in the way that we utilize our smart speakers today. All right, we need to get close to the end here. So I wanted to ask one kind of high level question with any kind of situation that you might not actually want to override these default answers is something that everybody should always be doing.

Dustin Coates  
I would say generally, it's it's what everyone should be doing. Again, generally, these platforms are, they're rolling up the utterances for you. So they have the built in intense but it's incumbent upon you to actually respond in a way that is that is valid for your application. So generally, you are going to be overriding this and let's say that One of the platforms does have a built in responses, right? In that situation, I would still recommend going through the effort of overriding is because you want your application to be your application. You don't want it to be Google's application. You don't want it to be Amazon's application without overriding these that's similar to using. Again, if you come from a web development background, that you similar to using bootstrap and not applying any customizations there, or using material design, CSS and not applying any customizations, it works, and you can do it and you'll get a site up and quick that you can put out there, but it's not your site is not your application.

Jeremy Wilken  
Right. So and that makes a lot of sense to me where we want to promote the best practices. Of course, there may be cases that don't apply to your scenario which the best And next week's ideas may not apply. So it's not that everything has to be totally built. And I think some people may feel a little apprehensive about, oh my goodness, there's now these extra things to do to build a single skill or an action. But a lot of this is fairly easy to reason through really quickly, until you get into more complex flows, then you need to rethink critically about them. So if you do it, for smaller skills and actions, I don't think it adds a whole lot of overhead to actually go out and do it. It's a matter of bringing it together in a way that works well with your brand and your your flow rather than just defaulting to whatever Alexa Google or whoever provides out of the box. Alright, final part of the show here we call endpoint detection. I wanted to start by asking you Dustin, what is the key takeaway you'd like to share from today?

Dustin Coates  
I would say that the key takeaway is that your responses and how you respond to users either what you say or what you do, and your voice applications, those needs. needs to be tailored to the user where the user is where the user has been, how much of an expert the user is in your application, it should really be tailored to that user and that conversation.

Jeremy Wilken  
Totally agree makes everybody's experience that much more professional and clean and crisp. So next question. Have you had any interesting voice experiences lately that you'd like to share?

Dustin Coates  
I would always share a couple of them very quickly. One is a very small piece of voice UX that I saw recently, which was on the Google Assistant. And this is where I was asking for weather. And Google Assistant came back to me and said, By the way, I can tell you this in Celsius or Fahrenheit, and I liked that nice piece of customization where I could easily say, hey, the way you're going to speak with me, I want that to be Different from now on, I want it to be really tailored to me. And so that's that's one of the most interesting things that I've seen recently, just this nice little touch that says, we're hearing you, and we want to be your assistance.

Jeremy Wilken  
Also, yeah, I like some of the little touches that I've seen over time too. And those are good ideas to bring into your experience when they make sense as well. Next question, do you have any suggestions or Reese design resources that you particularly find useful? That would be useful to someone learning voice design.

Dustin Coates  
There's a number of them I will put in a plug for my own book, which I think is tailored well towards people who are more beginning out its voice applications for Alexa google assistant. And something that I didn't write but I find quite interesting. And I don't think a lot of people have read it or they tend to overlook it because it's from 2004 is Voice interaction design by Randy Allen Harris. It's a fantastic book, I believe it's a textbook. And despite being written 2004, it's still very, very useful. And in fact, I'm looking on Amazon right now it has zero customer reviews. So it's it's a bit of a shame that this isn't more prevalent because it is a fantastic book.

Jeremy Wilken  
Great. I'm going to add that to our list of resources on the website. So if you want to find it, it'll certainly be also in the show notes for this this week, as well as in the resources list. Then finally, last question, how can people learn more about you and your work?

Dustin Coates  
Yeah, you can find me at on Twitter, Twitter slash D coats of Find me on LinkedIn. Dustin coats is my name. Those would be the two best ways to connect with me or if you have any specific questions also, feel free to reach out just Dustin ID coach. com.

Jeremy Wilken  
Excellent. Well, thank you so much. Much for Sharing This is a really important and everybody has to deal with base intense and then should have some level of customization and thought put into them instead of just taking them in by default. So I really appreciate some of your insights and sharing that with us today.

Dustin Coates  
Thanks for having me Jeremy.

Jeremy Wilken  
Thank you for listening to today's episode and if you liked the show, please rate us on your favorite podcast player. All the show notes are available on design for voice com
