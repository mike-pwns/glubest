**note:** this project is part of my 'carryover' projects, meaning they were written a while ago. I just sanitized this project and put it on this public GitHub profile. Point is, this README may not be as detailed or accurate as from my contemporary projects. 


# GLUBEST (SPRING 2025, CARRIED OVER FALL 2026)  

Project for learning websockets n such. Was tasked with writing a project that involved web.. but being a nerd and all I already knew some stuff and found "just-web" to be boring.. so.. I ended up playing around with servers and getting this to work, an IoT cat feeder!

But this is really more-so a proof of concept - a MVP. A modernized, and less nuanced version has already crossed my mind many times, and is due for a v2! More details in the 'What's Next' section somewhere below.

## What is this actually  

As mentioned, this is an Internet of Things (IoT) cat feeder. I myself never fully got what IoT is, so for you dear reader - whether you're a script kiddie, or a seasoned veteran of cyberspace - let me try to explain it: big picture is that an "internet" isnt unique to the the "internet" as we call it in everyday terms. "internet" is literally just "inter-network", ie a network among objects (like "interpersonal leadership" - leadership among people, and "intrapersonal leadership" - the leadership of oneself). IoT would then literally mean "a network of things". In this case, a web-client to a physical agent which feeds my (glutenous) cats through an AWS instance. And do why we called the internet, the internet? I don't know - it makes sense, sure - but isn't it also just an internet of things? Ahh whatever - that's not what we're here for!

The real bulk of the project was in the cat feeding system, where a user could:
- see the cats in real-time thanks to a live camera feed of the premises; and
- feed the cats with a click of a button using an arduino-controlling agent.

Some other minor features of this project:
- an adaptive web-ui for both computers and on-the-go monitoring/feeding (added this because I'd forget to feed the cats when I'm not home, so I'd feed using my phone when I was headed back)
- auditing system (contains logs.. I'm 70% sure, I don't remember entirely) to just know who feeds the cats, etc. (security purposes maybe.. who knows?)
- A main page which plays some music and has some cat photos to cycle through. But all this is really filler - extra amenities I had the time for to code in.

## Tech stack
- Networking: **AWS, WebSockets and REST APIs.** 
- **Java** for server and agent logic.
- **Arduino (logic in C++)** for motor control.
- **HTML/CSS/JS** for web ui.

## screenshots 

**Main page**: 
- swipe through some cat photos taken during the development of the projects
- vibe to some custom made music
<img width="1378" height="775" alt="main_menu" src="https://github.com/user-attachments/assets/3469b021-2386-427f-a8b1-6278d7712393" />


**Feed page (with a live example!)**
- pretty obv, feed the cat!!!
- also.. see the cat!!!


![glubest-demo (3) (1)](https://github.com/user-attachments/assets/0641dea9-6a79-4217-8315-bdfa69cc35bf)

## Running the program  

Err.. You think you can run the program?

Well, silly past me hardcoded a bunch of things. You're better off waiting for v2..

okay okay! Even though I don't remember EXACTLY what you gotta do, heres a psuedo-guide:

**1. Server setup:** Get a globally accessible server instance with an IP (or get a mesh vpn or something that allows you to connect devices over the internet) --> compile and run the `ServerManager.java` on it.

**2. Agent setup** Get a computer with an arduino connected via serial, and a webcam. Find the addresses and change them in `Agent.java`. Make sure the arduino wiring matches that outlined in `stepper-logic.ino`. 

**3. Wiring the client and agent:** in the `Agent.java` and `feeder.js` add the server IP (when sanitizing, I marked them with "TODO" and a comment about adding the server IP). Then run it! 

Ideally (big ideally) this should work. If you're desperate, just ask claude to read over and identify the points where you oughta make changes. 

But really dude.. I know you're dying to try out this revolutionary tech.. but I'd just wait for me to just make a v2 with custom 3d printed designs and bunch of optimizations; I've learned a lot since then yknow? That's worth sticking around for.

## inspiration  

This project was just me solving a problem I was having. A treacherous one in which everyday when I get home, my cats would storm me and annoy the hell out of me to give them food. Guess you could call me an engineer - the way I identify and solve problems - but that was just a tool I made for survival!

Additionally, as previously mentioned, I wanted to learn websockets yknow?

## challenges 

I frankly could not write a no-bs report here.. I just forgot what challenges I was having at the time yknow? Sue me!

## what id do differently (project-planning wise for future projects)  

Same as above, except for the whole: "idk how to run this from scratch". 
Going forward, I'd like to do my best to write programs that can be setup and run by other people (or future me yknow?).

## Credits / Sources

Some of the libraries I used (just pasted the 'libraries' dir):
- bridj-0.7.0.jar
- gson-2.10.1.jar
- Java-WebSocket-1.6.0.jar
- jSerialComm-2.11.0.jar
- slf4j-api-1.7.36.jar
- slf4j-simple-1.7.36.jar
- webcam-capture-0.3.12.jar

My sources for learning specifically.. I don't remember. Forgive me guys!

This being the credits and all.. for testing my genius prototype, shoutout to my cats! 

(There will be photos in the bonus section!!)

## What's next  

I mentioned a v2! Yes yes, an actual v2. 
Truth is, I'm not certain when exactly I intend to do this.. (but it is something I intend on doing - not just "maybe someday")

However, don't fret.. Here is the outline for a revamped version 2 of this project to satiate your curiosity for now!

### GLUBEST VERSION 2 DESIGN MANIFEST

**self hosting architecture (building around a user-base)**
Being a new self hoster and all, being able to pass requests through a local server base and all that jazz with mesh vpns - thatd be a huge improvement on what we got now. Especially given that this kind of service is a personal one - having a video feed just be shot out to some random server instance (but hey lets not hate on past me too much, I wasn't enlighted of the ways of self hosting back then!!). That reminds me of a ring doorbell incident.. hm.

**more optimizations**
This really is a simple project in theory - its not rocket science yknow?
I reckon some things can really be cleaned up; like..
- only sending a feed when someone is watching
- optimize sending data (maybe have a "feed only" mode with plain [FEED CONFIRMED] feedback, so no feed)
- make the logic flow simpler (even though admittedly it should be pretty simple as of now)

**security (dont wanna have randoms overfeed your sweet katz do ya?)**
One obvious improvement on this end could deal with the frontend changing to an env file setup (idk.. just a thought!). Then theres parts like perhaps a key a user would need to actually perform any action other than see the live feed. Otherwise, a "bad actor" could just overfeed a cat! And yeah, fat cats are fluffy and cute and amazing and sweet and squishy and etc etc, but! Not everybody is trying to overfeed their cats, so being able to deliberately control their feeder would be important!

**a mobile application**
yes, there is a web-ui - but a native app would be better, no? Easier for on-the-go.

**better arduino-controlling**
This is split into 2 parts: raspberry pi as the agent, and a better design for the physical components. The goal is to be able to 3d print some of the more intricate details, be able to assemble the whole thing from zero (well, maybe for some of the structure use carton, but like for the.. whatever. Maybe the whole thing will be 3d printed - don't know for sure - but thats an idea. Point is - with a better mechanical system, theres a lot more reliability on the whole project. Embarrassing story: when I was presenting this, it failed the first rotation (dont you worry, it worked after, but the idea is: the way it was put together was very primitive - I didn't have the proper resources or time to do something full-scale).

**additional features**
- being able to set an auto-feed system
- monitor when cats are swarming around the feeder (maybe an alert "hey cat is probably hungry")
- cat identifying (like this is a stretch, but maybe a local ai that recognizes and sends alerts "yo cat #2 is in the area!" or "cat #1 is eating!"..But if you're in a meeting and you get this, like what are you doing about it anyway?)

## bonus: cat photos!!!!!!
Now as a reward for reading through all my yapping: cat photos!!!

<img width="468" height="507" alt="cat_using" src="https://github.com/user-attachments/assets/0c6a4e53-98c0-46a3-883f-680a18ac4df8" />

<img width="959" height="615" alt="cat_building" src="https://github.com/user-attachments/assets/7d42c3ad-f973-4f6e-ac66-17a48b24fa01" />

