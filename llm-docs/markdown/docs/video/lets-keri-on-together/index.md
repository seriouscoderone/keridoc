# Let's KERI on together

> [!NOTE]
> okay and I will show slides all right so this is the presentation I did at IIW called 'Let's

0:00:00.080,0:00:00.800 paracore

0:00:03.520,0:00:12.480 okay and I will show slides all right so this is the presentation I did at IIW called 'Let's

0:00:12.480,0:00:20.640 KERI on together'. I did the presentation, I did the card at IIW with instructions on

0:00:20.640,0:00:26.880 how to pull the software and get ready so you could run alongside the demo if you so chose.

0:00:27.600,0:00:33.120 No one did, which was a little bit disappointing, but the repo is here, it's the KERI, right, KERIpy

0:00:33.120,0:00:39.680 repo the web of trust it's a lot of the all of the networking and asynchronous

0:00:41.840,0:00:49.840 I/O is based on co-routines in a library Sam Smith created called 'hio' right now

0:00:49.840,0:00:54.000 what I'll be running today requires Python 3.9.7 but we're now up to 3.10.3

0:00:55.200,0:00:58.960 and these are the instructions if you wanted to follow along let me get clone

0:01:00.000,0:01:04.320 the repo itself check out the future 'iiw' branch and then just run a `pip install`

0:01:05.120,0:01:12.960 of the requirements file, to get all of the dependencies. So most of actually everything

0:01:12.960,0:01:18.720 that we'll be showing today, starts with the KERI command line interface that we call 'kli'.

0:01:18.720,0:01:26.080 It has commands and sub commands much like, if you're familiar with Kubernetes' "kubectl" command line,

0:01:26.080,0:01:29.840 so that for example if you were doing some something with verifiable credentials you would

0:01:29.840,0:01:36.080 start 'kli vc' and then there would be a sub command following after the 'vc' for example 'issue' or 'revoke'

0:01:38.320,0:01:46.640 And then we do have Docker containers that have all of the code pushed and configured

0:01:46.640,0:01:53.440 ready to run so you can pull one of those and do a 'docker run', running a sub shell

0:01:53.440,0:02:00.960 and you can use the kli to perform tasks so the basic structure for the commands in the kli

0:02:01.840,0:02:07.840 the groups that we have, pardon me, the agent group for running our cloud agent which is also run

0:02:09.200,0:02:16.800 in the distributable desktop application we're building using Py installer and

0:02:16.800,0:02:23.200 Electron to bundle KERIpy behind a web-U/I that web-U/I uses the agent

0:02:24.880,0:02:29.600 if you want to perform some delegation commands there's a couple of sub commands under delegate

0:02:29.600,0:02:34.320 if you want to create a distributed multi-sig identifier you would use the multisig commands

0:02:34.320,0:02:38.560 and then the verifiable credentials I mentioned the wallet commands are simply for listing the

0:02:38.560,0:02:44.560 contents of your wallet and by "wallet" I mean verifiable credential wallet and then

0:02:44.560,0:02:50.320 to start witnesses or watchers you would use the watcher group with sub cmnds like 'start'&'demo'

0:02:51.200,0:02:58.640 Steven: So, Phil, all these ..., well everything on this page, is there documentation as to

0:02:58.640,0:03:06.240 what exactly an 'agent' means like do you have the terminology somewhere? Phil: No, there isn't, (Now there is!, ed.)

0:03:06.240,0:03:13.440 but that would be a good thing to add to a getting started I guess. Steven: yeah absolutely, so I mean could

0:03:13.440,0:03:20.880 certainly create like a vocabulary dictionary and then maybe a one-liner description

0:03:20.880,0:03:28.400 of what each like "run cloud agent" does, what delegation means. Phil: yeah that would be great.

0:03:28.400,0:03:30.720 (Available! See the glossary in the Youtube description)

0:03:30.720,0:03:46.800 Look at command line, if you run just 'help' from the top level,   it does list... Steven: can you share the screen?

0:03:47.440,0:03:53.360 Phil: I'm sharing just this spreadsheet, I mean just the presentation on there, let me show that desktop

0:03:56.000,0:03:59.200 there we go, okay can you see the command line now? Steven: yeah

0:03:59.200,0:04:04.480 Phil: OK, so if you run 'kli --help' you get a list of the commands and sub commands and they do have

0:04:05.440,0:04:10.000 one liners not all of them are accurate at this moment but that's something that...

0:04:10.000,0:04:15.840 Steven: doesn't matter, it'll be a placeholder in the worst case scenario.

0:04:16.400,0:04:21.360 okay, so for key management the top level commands the the very first thing you almost always do

0:04:21.360,0:04:27.920 is do an 'init' which initializes both your data store and your encrypted key store, 'incept' for

0:04:27.920,0:04:32.960 creating a single-sig identifier, technically you can create multi-sig identifiers with that as well,

0:04:33.600,0:04:37.120 but they're not all that interesting. Because all the keys are stored in the same key store

0:04:39.440,0:04:44.400 the different key events that you can create an interaction event or a rotation event

0:04:45.040,0:04:48.480 are handled with the next two commands 'interact' and 'rotate' and they each take

0:04:48.480,0:04:54.160 parameters, 'rotation' for example, specifying your signing thresholds number of keys rotating in

0:04:54.160,0:05:00.000 and out witnesses all the things that you can do when rotating and 'purge' just deletes your key store

0:05:01.600,0:05:09.040 so then the miscellaneous commands querying for creating witnesses for a KEL. Sending your

0:05:09.040,0:05:14.240 KEL to another agent; we don't use that very much anymore because we use OOBIs to accomplish that now.

0:05:15.120,0:05:23.120 Signing, pardon me, you can just sign our arbitrary data and it will return the signatures based on

0:05:23.120,0:05:27.520 the identifier that you used and we'll be done I'll be demoing that in a little bit. Verifying

0:05:27.520,0:05:32.000 those signatures and if you're you know if you're just exchanging signed data with someone via an

0:05:32.000,0:05:36.800 e-mail this will accomplish that for you. Then 'list'ing the identifiers that

0:05:36.800,0:05:42.880 you're creating and giving a 'status' of a single identifier. So it's important to point out that

0:05:44.240,0:05:51.840 with the most recent updates to KERIpy, we now have first class support (ringing silenced)

0:05:57.040,0:06:02.480 We now have first class support for multiple identifiers multiple local identifiers,

0:06:03.760,0:06:07.040 so that's why we have the 'list' command so you can create in you can run

0:06:07.040,0:06:10.560 'init' once create a single data store and key store and then run 'incept' as

0:06:10.560,0:06:13.600 many times you want to create other identifiers and you use those for

0:06:13.600,0:06:20.320 like peer-to-peer communications and things like that, so that you can't be correlated. All right

0:06:22.640,0:06:29.120 so each of the three top level runnable components an agent a witness or a watcher each have

0:06:31.280,0:06:39.520 various startup commands. You have the 'bootstrap' command to start an empty agent or to run a single

0:06:39.520,0:06:44.800 agent against one that's already been started. You can run 'start' and then both for witnesses and for

0:06:44.800,0:06:50.480 agents we have these 'demo' commands which we make heavy use of for local testing. So, for example

0:06:50.480,0:06:55.920 under the witness this starts up three well-known witnesses and by "well-known" I mean we use salts

0:06:55.920,0:07:02.720 to initialize their key stores so that the you can predict what identifiers will be created and

0:07:02.720,0:07:09.760 again that's not anything that you'd want to do in a production environment,

0:07:09.760,0:07:14.240 but for running tests, and we'll be using particularly the 'demo' witness command later on

0:07:15.120,0:07:19.200 to start witnesses so that other commands that need witnesses know where to find them.

0:07:20.320,0:07:26.720 And then we have similar commands for watchers. Part of the demo today is running through a

0:07:26.720,0:07:31.920 series of scripts that we've created in the demo directory located in keripy/scripts/demo

0:07:33.360,0:07:38.960 and the most basic one is just 'demo-script' which starts off and runs all the really basic commands

0:07:39.520,0:07:43.840 'demo-witness-script' runs through some of the same commands but requiring witnesses to be running

0:07:44.720,0:07:50.160 and then we get into the more interesting stuff: delegation and multi-sig

0:07:50.160,0:07:54.800 multi-sig delegation where both parties of the delegation are a multi-sig identifier

0:07:54.800,0:07:59.920 and then credential issuance and multi-issuance. During the demo at IIW we did not get to these.

0:08:00.720,0:08:05.360 We only got this far and in an hour. I'm not sure we'll even get to these, but we will see.

0:08:08.320,0:08:15.760 Oh, I forgot to point out the all of the sample JSON files are also located in keripy/tests/app/cli,

0:08:15.760,0:08:25.360 which contains the ..., when you do a 'kli incept' command, it takes a file for all the properties

0:08:25.360,0:08:30.560 that you want to pass in for the creation of that identifier, for example how many signature or how

0:08:30.560,0:08:34.880 many public keys to create, what's your signing thresholds, how many / what witnesses to use, whether

0:08:34.880,0:08:39.840 it's transferable or not, et cetera and I'll show these as we go through them today

0:08:42.320,0:08:47.360 and then finally another big enhancement in this most recent round of changes to KERIpy

0:08:47.920,0:08:53.840 was the addition of out-of-band introductions or OOBIs. They are files,

0:08:54.560,0:09:00.400 these are startup files that contain bootstrap OOBIs. So for example when we use the 'demo'

0:09:00.400,0:09:04.800 command for witnesses, like I said: they're well-known identifiers, they also start up

0:09:04.800,0:09:08.720 on well-known ports and they publish those ports via a series of OOBIs. This is a

0:09:08.720,0:09:14.880 configuration file that any other agent can run and know exactly how to contact those witnesses

0:09:16.000,0:09:19.120 and this is the configuration file for those witnesses, so we'll get to those in a minute.

0:09:20.000,0:09:26.080 So that's it for the, pardon me, that's it for the presentation there's not slides anyway

0:09:26.080,0:09:30.240 there's not that much in terms of slides, here's just enough to get this kick-started.

0:09:32.720,0:09:38.560 So now we'll go over to our first script today. Oh, one thing I didn't point out, but I wanted to

0:09:38.560,0:09:44.000 make clear: because we have the kli which you can do everything you need to do with KERI

0:09:44.640,0:09:48.640 in KERIpy with the kli on a command line and that's for running in a mode where you're

0:09:48.640,0:09:54.640 not always on the internet. But as I pointed out also, we have an agent that can run.

0:09:54.640,0:09:58.800 That could be a continuous or persistent connection to the internet. So a cloud agent for example.

0:10:00.240,0:10:05.760 And in that case the cloud agent exposes a series of REST APIs that perform the exact same

0:10:05.760,0:10:11.680 functionality as all the kli things that we'll be going through today. And in the demo scripts

0:10:11.680,0:10:17.440 that you see here for every script starting with 'delegate', there is a sister script next to it,

0:10:17.440,0:10:22.320 '-agent', that is the exact same command but with a series of CURL POSTs, I'm sorry, the

0:10:22.320,0:10:28.560 exact same functionality, but executed as a series of CURL POSTs against an agent, or PUTs

0:10:31.600,0:10:35.440 (and I'll show when we launch) the agent we also expose a swagger U/I,

0:10:35.440,0:10:42.000 which allows you, if you wanted, to execute commands against it. I'll show that towards the end.

0:10:44.880,0:10:47.280 So let's start with the basic 'demo' script.

0:10:49.840,0:10:55.920 I'll zoom in here a little bit, is that legible for you? Steven: yeah, I'm much better now.

0:10:57.760,0:11:05.760 Okay so, the very first thing this does is create a key store within it. Currently KERI now supports

0:11:06.560,0:11:11.360 the ability to create a key store and data store for that matter with a passcode and when you

0:11:11.360,0:11:16.400 do that, it becomes an encryption key. like it's stretched into an encryption key that is used for

0:11:17.440,0:11:24.160 encrypting the key store so that no one else can gain access to your private keys

0:11:24.800,0:11:29.040 that passcode is never stored anywhere within KERIpy or the agent

0:11:29.040,0:11:33.520 so it has to be protected by the user because otherwise you can't get access to your keys

0:11:34.400,0:11:41.840 Steven: Sorry Phil give me one sec there's just something going on in here, one second

0:11:45.000,0:11:55.000 (What a perfect break for a small quiz!:) (How many new terms has Phil introduced so far?)

0:11:55.500,0:12:05.520 (The answer is: 55 terms that need explanation!) (Most of which are available; see description.)

0:12:07.520,0:12:08.960 Steven: sorry about that! Phil: no worries

0:12:15.840,0:12:20.240 Okay so, for all of the commands that we're gonna be running today, we just pass in the

0:12:20.240,0:12:23.200 flag '--nopasscode' so the keystore isn't encrypted. And that's just to make things

0:12:23.200,0:12:27.120 easier, so we're not passing passcodes around to every other command but anywhere where you

0:12:27.680,0:12:32.640 run a subsequent command after 'init' you can pass in '--passcode' and it'll unlock

0:12:32.640,0:12:38.400 the keystore if it's indeed locked so the very first thing that this does is create a database

0:12:38.400,0:12:43.680 and key storage you can see from the comments the name of the database, the name of this

0:12:44.480,0:12:48.240 instance that you're creating, is called 'test' and that is used to create

0:12:48.240,0:12:53.440 the directory structure for the databases that support both the wallet and the key store.

0:12:55.520,0:13:00.800 Those databases can go in one of three places. When configured properly you can

0:13:00.800,0:13:06.640 create a database and key store in '/temp' which obviously is used just for testing and

0:13:06.640,0:13:13.360 we use that heavily when running all of our unit tests. If you have a directory called

0:13:14.080,0:13:18.720 '/user/local/var/keri', and the current user has write access to that directory it'll create

0:13:18.720,0:13:22.480 all the databases under there. And then they're prefixed with the name that you give it here.

0:13:23.680,0:13:28.720 If you don't have that directory the last place that KERIpy attempts to create the data stores

0:13:28.720,0:13:34.960 is in your 'home directory.keri' and then it would begin with 'test' for this one after that.

0:13:35.600,0:13:38.160 So those are the three places you want to go look for your key stores

0:13:41.280,0:13:44.240 So after it creates the key store, we're creating... Steven: Sorry, can you, when you

0:13:45.760,0:13:51.280 would you define which one of those three places to look for here? Phil: No. Steven: or it's just the way

0:13:51.280,0:13:56.320 you're installed, you're just, you're set up Phil: that's correct, it's the way your system is set up

0:13:56.320,0:14:01.760 there. we don't support the creation of temporary from the command line. We could add it as a flag,

0:14:01.760,0:14:06.400 I guess, but we don't currently support that. So this will ...,from the command line, this will

0:14:06.400,0:14:09.920 create the key stored in either '/user/local/var/keri', if it exists and you have

0:14:09.920,0:14:16.720 write access to it, or under '.keri' in your own directory if you don't have that other one.

0:14:20.080,0:14:20.580 Uhm...

0:14:23.600,0:14:28.240 Yeah, we could we could definitely add the ability to create a 'temp'(orary ed.) from here but that would

0:14:28.240,0:14:32.960 just be another flag so the first thing we create is a non-transferable identifier after you give

0:14:32.960,0:14:37.520 the name of the data stored you give a local human readable alias to this identifier and as

0:14:37.520,0:14:41.360 i mentioned you can support you can create multiple identifiers so you would give them

0:14:41.360,0:14:43.920 per a single key store so you can give them whatever aliases you want

0:14:43.920,0:14:47.600 So that you can remember what you're using that particular identifier for

0:14:48.880,0:14:52.480 So this is creating a non-transferable identifier. We'll start by opening that

0:14:56.560,0:15:04.320 So, 'transferable=false' obviously and a transferable identifier ( ) okay, if I'm instructing clients who want to build

0:29:42.240,0:29:46.400 SSI infrastructure, do I tell him "he is KERI" do I tell him "he's a ledger" what do I tell him?

0:29:48.160,0:29:51.280 And it was great to clear up a lot of misconceptions because people think:

0:29:52.000,0:29:56.400 "oh, you can't use a ledger with KERI". No that's not true, you don't have to use a ledger with KERI. We

0:29:56.400,0:30:01.200 don't think it's, we don't think it's needed at all, but as Sam as what Sam pointed out during

0:30:01.200,0:30:05.920 the talk, is if you already have an investment in ledger infrastructure for other reasons,

0:30:06.640,0:30:10.720 you can then leverage that ledger as an additional trust threshold,

0:30:10.720,0:30:14.640 or security threshold for your identifiers instead of using witnesses.

0:30:17.200,0:30:22.800 So no, we're not, I mean the vLEI won't be using anything to do, with cryptocurrencies or tokens but

0:30:22.800,0:30:29.280 if you, you know, if for example a lot of people are using SSI systems based on Indy networks, right,

0:30:29.280,0:30:34.320 now if you want to transition to using KERI, you could do that by anchoring your KERI identifiers

0:30:34.320,0:30:39.040 in your Indy ledger. And then you, and the neat thing about it is, you could then transfer them

0:30:39.040,0:30:43.600 off, off the ledger and have non-ledger based identifiers, so that's what's great about

0:30:43.600,0:30:47.760 KERI: it's portable, you can be anchored to any one ledger at a time, or you could move it to a

0:30:47.760,0:30:53.040 different ledger, or you could move to using just witnesses, all with the same identifier by just

0:30:53.040,0:30:58.880 doing rotation events and changing your anchor, your backers here. Steven: but could you also do, if

0:31:02.080,0:31:09.520 could you be anchored, let's say to multiple Indies or Ethereum? Phil: you could be only anchored in one at a

0:31:09.520,0:31:16.160 time, because that's the source of truth for that identifier at that given point in time.

0:31:16.160,0:31:21.440 You can then rotate to a different one, but you you can't have two ledgers at the same time.

0:31:23.200,0:31:30.320 Steven: So when people, well what maybe they misunderstood, so I understood that

0:31:30.320,0:31:33.360 okay one of the problems in blockchain is that you're all you have to be committed to all use

0:31:33.360,0:31:39.120 the same network which is not practical unless you're running an ICO scam, so

0:31:40.960,0:31:46.880 I understand KERI is digital ledger technology agnostic. And that you could

0:31:46.880,0:31:52.080 use it..., it could interoperate with existing ledgers like Aries or Indy whatever it's called,

0:31:54.800,0:31:57.760 but it's only that one network. You couldn't, you couldn't connect

0:31:59.280,0:32:07.520 Ethereum and Indy to the KERI ledger ( ) This is the identifier, because there's an inception event, the SAID of this is the same,

0:49:49.680,0:49:57.840 so these are the two, and here's a sequence number '0'. So now, if we take a look at the delegator

0:50:02.400,0:50:09.280 you can see his rotation event here, this is the approval and that 'EY7'

0:50:09.280,0:50:15.040 is the identifier as well as the SAID or digest of the event that he approved and

0:50:15.040,0:50:20.640 he has anchored that data; thus approving the delegation request from the other guy.

0:50:24.240,0:50:29.520 All right so that makes sense? Steven: Maybe one day, yeah, that's what I'm feeding,

0:50:31.200,0:50:35.200 it's so inspiring. Phil (laughing): "yes there's a lot, there's a lot here.

0:50:37.040,0:50:41.360 All right we have eight minutes I will try and get through multisig actually you know what no

0:50:41.360,0:50:45.920 Steven: No rushing in my account, I mean, I understand you're on vacation here, but don't worry

0:50:45.920,0:50:51.440 about my time. Phil: Yeah, I know, I have another meeting, I have to get to. Steven: Oh okay, not only

0:50:51.440,0:50:57.120 for visiting the family? Phil: yeah exactly, yeah but not only that, but I'm out here buying a house,

0:50:57.120,0:51:08.240 because we're moving out here, so all that, as well as work, it's been very very busy.

0:51:08.240,0:51:09.920 All right, so let me show you the agent really quickly.

0:51:12.640,0:51:21.840 So here we start actually. I don't need the witnesses but anyway so we will run 'kli'

0:51:25.760,0:51:31.200 So I'm running 'kli agent demo', just like the demo command down here, he starts,

0:51:32.480,0:51:37.040 except in this case, he starts four well-known agents and that's because, well I needed to test

0:51:37.040,0:51:43.440 multi-sig delegation with two participants in the delegator, and two participants in the delegatee.

0:51:44.320,0:51:52.960 delegation coordination I start him with a ... (that's not gonna work) Well that's fine, I

0:51:52.960,0:51:59.840 started him with a configuration file that tells him where these three witnesses are and he starts

0:51:59.840,0:52:05.200 four agents on these well-known ports again with actually he doesn't have well-known salts because

0:52:05.840,0:52:12.720 you do those via the CURL commands so once you start those agents, let's see, here we go,

0:52:14.960,0:52:22.640 you get on each of those ports a Swagger U/I which contains the available API calls.

0:52:22.640,0:52:29.200 For the agent depending on his state. Every agent initially starts off in a locked state.

0:52:29.200,0:52:33.280 so think of a ..., remember when we did the 'kli init' commands and created the data store

0:52:34.880,0:52:38.160 that data store is now encrypted and locked, if you gave it a passcode.

0:52:38.720,0:52:43.200 So in this case we don't have any data stores yet, so you can start an agent with no data stores

0:52:43.200,0:52:51.840 around and that's when you end up in this state. So in order our passcode requirement for creating an

0:52:51.840,0:52:56.800 encrypted key store is a 22 character passcode we give you just a little helper function. This isn't

0:52:56.800,0:53:01.600 really part of KERI, but we give you a little helper function for, (my grandson is really unhappy),

0:53:04.320,0:53:09.520 for just generating random passcodes if you need that, you can also use "OnePass" or whatever to

0:53:09.520,0:53:16.640 create them and then store them in OnePass, so now just like 'kli init' that creates a key store

0:53:16.640,0:53:23.600 we have a POST to '/boot' which will create a key store for you, you call it, let's try it

0:53:23.600,0:53:29.920 out, let's not type into the sample I did that during the demo too, 'Agent0', and spell agent right

0:53:32.320,0:53:35.440 and give it the passcode, that you saved and execute,

0:53:36.720,0:53:44.160 and you can see the 'agent0' and key store created and he resolved a whole bunch

0:53:44.160,0:53:47.920 of OOBIs, that's part of the configuration file, I guess I do have running the ...,

0:53:48.720,0:53:54.800 So, one thing to note about here, is several of the OOBIs are actually data OOBIs. And we can also

0:53:54.800,0:53:59.440 use OOBIs to resolve things like credential schema. So that's a whole separate topic.

0:54:01.520,0:54:06.880 So, now that we've created the key store the next step is to unlock it, and so this is like

0:54:07.600,0:54:12.560 if you ..., so we ran this demo at IIW after doing our demo hour where we demo-ed the U/I

0:54:12.560,0:54:15.680 that we have sitting on top of this to Keep, and so when you get into the Keep,

0:54:15.680,0:54:19.280 you get a nice screen that says "hey, create your passcode", which is that first API call.

0:54:19.280,0:54:23.840 And it uses the top API called to generate random keystore keys for people who want samples

0:54:24.480,0:54:29.040 to use and then we do a PUT against '/boot' for unlocking. And that's the next

0:54:29.040,0:54:33.040 nice block in the U/I that says "now unlock your key store" Every time you come back into the agent,

0:54:33.040,0:54:37.840 because you already have a key store, you just have to unlock, right, because you've already created it

0:54:41.680,0:54:46.240 So we're going to try it out, here we called him 'agent0',

0:54:48.400,0:54:53.600 and there's the passcode that we use, and we're going to execute this and he says "'agent0' is

0:54:53.600,0:54:58.560 now unlocked", and the cool thing about unlocking an agent, is you just reload and you now have a

0:54:58.560,0:55:03.360 whole new set of APIs for doing all the things you would want to do with an agent, and these all

0:55:03.360,0:55:09.520 marry up very nicely with the 'kli' commands that we've been running. Get your list of identifiers,

0:55:11.360,0:55:15.280 get information about a specific identifier, you can create a new identifier, this would be

0:55:15.280,0:55:23.600 like 'kli incept', you can update, so again not part of KERI but to support a user interface, a wallet

0:55:23.600,0:55:26.960 for example, where you're going to have a ton of different identifiers, you need to associate

0:55:26.960,0:55:32.160 metadata with those. You give yourself context to remember, you know what organization, who ...,

0:55:32.160,0:55:36.560 Just think of a standard contact book; that's what this API is for us; for updating that.

0:55:37.600,0:55:42.160 And because we're "zero trust", all that data is signed at REST, so that if you lose control of

0:55:42.160,0:55:47.680 your database, people can't put in like, you know, change the name of the contact and fake you out,

0:55:47.680,0:55:52.960 because we verify the data when we reload it, and then you can do a rotation or an interaction event.

0:55:53.840,0:55:58.400 This is for creating and listing your credential registries so the public transaction event logs

0:55:58.400,0:56:03.520 for anchoring issuance and revocation events a presentation request, you can generate

0:56:03.520,0:56:07.520 your own OOBI or resolve other people's OOBIs. This is like the 'kli oobi' commands

0:56:08.400,0:56:13.360 these are the this is challenge response so one of the requirements of the Keep is that you do a

0:56:13.360,0:56:18.160 two-factor auth, so this is for generating like a list of challenge words, that's what this guy does.

0:56:18.160,0:56:23.040 Which is just randomly generated challenge words. You would then take those, send them to another

0:56:23.040,0:56:29.280 person using this command. They would then get a notification that someone has challenged them.

0:56:29.280,0:56:33.040 They sign it with that identifier and send it back and now you have proven that they have

0:56:33.040,0:56:38.000 control of your identifier, and that was actually a big part of the demo, that we did during demo hour.

0:56:41.360,0:56:45.600 This is more information about getting, about getting an updating contact information.

0:56:45.600,0:56:49.680 We also support images. We don't sign those yet and Samuel (Smith, ed.) says to me that we have to sign them.

0:56:49.680,0:56:54.720 ( some domestic situation itemised :) ) And then this is for getting the schema, that we loaded via the

0:56:54.720,0:56:59.200 OOBIs, that I showed you at the beginning, this is diagnostics we're taking a look at, the escrow

0:56:59.200,0:57:03.120 status, because all events are asynchronous, passing events around, you can get them out

0:57:03.120,0:57:06.560 of order, you can get them without full signatures, without full witness receipts, and we have a whole

0:57:06.560,0:57:12.560 series of escrows, that the events just sit in, that we constantly check for any other event to come in,

0:57:12.560,0:57:19.920 to resolve them out of their current state, this is for mailbox notifications, so this is a 'server-

0:57:19.920,0:57:26.400 sent events', streaming service for the agent U/I,   to get notifications from the KERI system itself,

0:57:28.320,0:57:33.680 these are all the APIs for performing multisig and these are APIs for doing credentialing with

0:57:33.680,0:57:37.040 a multi-sig identifier. And the reason why these have to be different, is because there's

0:57:37.040,0:57:43.120 communication involved. Someone leads the process that would be with a POST, and then others call PUT

0:57:43.120,0:57:48.720 to participate in the process. And so, for example if I have an identifier, if you and I are sharing

0:57:48.720,0:57:54.480 an identifier, where you have a private key and I have a private key, I would initiate it and then

0:57:54.480,0:57:58.400 send, the system would send the credential to you, you would look at the credentials, say "Yep, this is

0:57:58.400,0:58:03.120 the one we agreed to issue". You would then do a PUT with that credential and your signature, and then

0:58:03.120,0:58:08.240 it would become a valid credential. And we do have scripts, and all that, we can go through that

0:58:08.240,0:58:13.120 Maybe you and I can schedule something next week, and we can go forward and do the multi-sig stuff

0:58:13.920,0:58:21.200 Okay, all right, so that's most of what I did. We had an hour and a half, when I was at

0:58:21.200,0:58:27.920 at IIW. Because I did it over the working lunch session (which meant I didn't get to eat) and we

0:58:27.920,0:58:32.800 went on through the next set of scripts, which is multi-sig and then multi-sig delegation on both

0:58:32.800,0:58:36.560 the delegator and the delegatee. And that was fun because you get four windows running, and they're

0:58:36.560,0:58:40.880 all waiting for each other. And when you're to finally fire off the final one, they all just resolve,

0:58:40.880,0:58:45.440 with signed events everywhere, It's really cool so maybe we can do that sometime next week. Steven: okay