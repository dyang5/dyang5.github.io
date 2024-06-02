---
layout: post
title:  REU-CAAR, Week 8
date:   2023-07-30
description: Week 8 of my Summer 2023 experience @ REU-CAAR.
tags: research cs
categories: caar
---

#### <u>Day 50 (July 24th)</u>

Week 8 Day 1: 50 Days

 - 8:30 - 9:00 AM: It's crazy to think that I've been here for 50 days already. We now officially have just three weeks (more like two since the final presentation will be sometime during the last week), so hopefully my group can finalize some presentable results in the next two weeks (I feel good about the way my new Semantic Guidance approach is going). 
 
 I've been a bit lazier than I would like to be with regards to Monday and Friday workouts; from my experience, these are the days when the lane lines at the pools are being moved, and my pool workouts usually get cut in half because of this. I had planned to wake up at 8:30 to go on a morning run, but upon waking up, I made the decision to take the extra hour of sleep; as I figured out later, this may have made me more tired.

 - 10:00 AM - 12:00 PM: With the program ending soon and our advisor out in Hawaii for a big ML conference, it is really go time for our group, and it's kind of up to us to get as much done as we can. XG said he wasn't feeling good and couldn't make it in today, so it was me, SS, and AF holding down the fort. Continuing off my work from last week, I have been working on an approach that uses Semantic Guidance for fair image generation. This morning, I focused a bit more on actually getting individual fairness to work, and the success was noticeable, which is great! Though the approach for individual fairness is very similar to the one presented in the following [Fair Diffusion](https://arxiv.org/pdf/2302.10893.pdf) paper (hence why we want to focus on group fairness in this project), it is good to see some progress being made and for the images to be generally more fair. 
 
 - 12:00 - 1:30 PM: We had another Monday lunch talk hosted by Professor Jon Katz of UMD CS. Though Bill titled the talk as "Security and Crypto," the talk ended up being more about Jon's experience working in industry and academia. The talk itself was quite insightful, and I was reminded of how, just like in previous weeks, I've felt like all these speakers, whether they are tenured professors or industry people, are all very well-spoken as well as knowledgable. From a personal perspective, there's a lot to consider when applying to grad programs, but if I can matched up with advisors like these speakers, I think I'll be in a good spot (by the way, if you're a professor of mine reading this due to some of the emails I sent out recently, hello!).

 - 1:30 - 4:00 PM: The next step in the semantic guidance approach is to work on solving the problem of group fairness. My idea is to use the results of the gender and race classifier I was working with previously (DeepFace), especially the classification confidences, to weight the guidance of each photo. At its current state, if we give a guidance prompt like "middle eastern" to get the people in an image to look more middle eastern, every person will become more middle eastern. Consequently, I'm hoping that if I can use the "average" confidences (in terms of race and gender) to support the semantic guidance across an entire image, the overall output can be more fair than the original generated one. (Note that the guidance is sort of inversely proportional to overall confidence -- if the classifier is very sure that the people in the image are white, then ideally the generated image will have greater representation of other races). In the afternoon, I started setting up (using previous code I've written) a pipeline to generate an image, classify the people in the image, get the gender/race confidences, and use that to "guide" a more fair image -- I'm hoping the results will be successful but at the very least, I'm happy that I'm beginning to work on an approach that I'm much more enthusiastic/excited about compared to before.

 After research, I went down to the second floor to pick up a check for my last few weeks of research. I then walked back to the dorm, felt quite tired, and proceeded to take a much-longer-than-anticipated nap. I had originally planned to head to the pool after research but I didn't think I would make it back to the Student Union by 7 if I did do that, so I ended up going for a pretty breezy 2 mile run around campus. Grabbing some CFA from STAMP, I went back, ate dinner, worked on some CodeForces (I finished up 1850H, which means that I've now "solved all" -- missing A, B, and C which are typically much easier-- of the problems from the most recent Div 4, which is the first contest I've fully solved), and did some laundry to close out the night.

 #### <u>Day 51 (July 25th)</u>

Week 8 Day 2

 - 8:30 - 9:00 AM: Back to the morning swims I go! I was really not feeling it this morning -- despite the nap I took yesterday evening and a solid 8ish hours of sleep, I was feeling tired and my arms felt like jelly. I managed to push through for 25ish minutes of swimming and finished with around 40 laps.

 - 10:00 AM - 12:00 PM: Continuing my work from yesterday, my goal today was to build on the Semantic Guidance approach using results from the DeepFace gender/race classifier. After taking some time to set up the relevant analysis (reading the classifier results and storing it in a dictionary, then looping through the dictionary to get the average confidence), I took a while to think about how I could weight the guidance based on the average confidence. My first idea, however, turned out hilariously bad, with the resulting images getting completely changed by the edit guidance weights/hyperparameters. I had a good laugh with XG, SS, and AF about how bad the results were, and then went back to thinking about how I could make the guidance a bit better (more thinking is needed on this front).

 - 1:15 - 4:00 PM: In the afternoon session, I built on my work from the morning. After a bit more experimentation and generation yielded slightly better but not by much results (images were a bit more clear than the morning but the faces/people looked nothing like the original images), I decided to refrain from guiding race and gender with prompting and instead focus on just guiding gender (male or female). Using similar ideas with the average confidence, I generated a few slightly better images. LH joined us in our conference room, and so SS, LH, and I got sidetracked talking about grad school expectations, life, and applications -- these conversations, though they kind of distract us from research for a bit, are in my opinion really insightful and rewarding, and I'm glad that they are happy to just chat so openly and honestly. This is one of the aspects I like the most about an REU compared to research at Swarthmore -- since we all live close together, are part of the same program, and come from different backgrounds/schools, it's easier to have a honest conversation with different perspectives, and I'm really grateful for that. In terms of research, I think the SEGA approach I've been working on still has some serious promise, which is great.

 I've been feeling quite tired after research, so I mainly relaxed until 6, when I decided to go do laundry, grab CFA for dinner, and then move my clothes from the washer to the dryer. I came back, did some quick CodeForces, reading, and more relaxing. I like hanging out with the other REU students but it's always good to have some days of solo time to decompress. A few of us were initially planning to watch a movie at night but LH had a headache, so we'll have to wait another day for that.

#### <u>Day 52 (July 26th)</u>

Week 8 Day 3

 - 8:30 - 9:00 AM: I woke up today to some stomach problems -- my stomach didn't feel great when I went to sleep yesterday and these problems continued a bit into the morning. This is my second time in as many weeks with stomach problems, so I was kinda concerned about this. Instead of risking anything, I decided to skip on a morning swim or run; though I have really wanted to be consistent with my exercise, I didn't think that exacerbating potential stomach issues would be worth it. 

 - 10:00 AM - 12:00 PM: My main worry in the morning was making sure my stomach issue would go away. I called my dad before research and he advised me to get it checked with a doctor, so I quickly got an appointment for later that afternoon. Similarly, I asked AF to bring some Pepto Bismal to IRB and she clutched up on that front; however, the pepto didn't really seem to do the trick. After the issues subsided slightly, I discussed my SEGA approach and what I was working on figuring out (a good way to modify the edit weights to get the distribution of male and female identified images to be close to 50-50) with AF and SS to hear their suggestions/thoughts. After some further discussion, I think we came to the consensus that the current SEGA approach is related to the Fair Diffusion paper (mentioned above) and the [Debiasing via Biased Prompts](https://arxiv.org/abs/2302.00070) paper (one of the other papers we read very on in the research process). Though parts of my current approach, like running an additional classification to determine the proper guidance weights, are costly in terms of generation time and may not be as effective as the Debiasing paper, I still think it's worthwhile to continue working on my approach to get something working. I am a firm believer in first getting an approach to work and then improving it, so I think I'll continue to do that -- and after the REU ends, we may want to look further into the Debiasing paper's approach and apply their work to group fairness.

 - 1:00 - 1:15 PM: I had a quick appointment at the UMD Health Center to talk about my stomach issues -- the doctor gave me some advice and mainly said that he didn't think it was too serious (and told me to get another appointment if the issues keep recurring), which is good to hear. In the remaining twoish weeks, I'll be sure to more closely look out for the food I'm eating...

 - 1:30 - 4:00 PM: I quickly grabbed some lunch before heading back to IRB to work in our afternoon research session. PM and MA came to our room and we talked a bit about our research, before they dispersed and we got back to working on our project. I talked to SS and AF a bit more, extending the discussion we had in the morning, about how we might use the confidence estimates from our classifier to get proper guidance weights -- in the remaining time, I began implementing the first of the approaches we talked about, before running into out of memory errors caused by CUDA (so I will run these again tomorrow). Since I've just been experimenting, I've only been generating three images at a time but I imagine I'll need to generate a lot more to get a better sense of whether or not the distribution of male-female generated images is balanced.

 After research, I took a bit of a break before heading out to play some soccer with NL, PM, MA, and SS. I went to STAMP to get some CFA and had dinner with LH, with SS and AF joining later. She talked a bit about trying to get SWE internships next year and we talked a bit about a Sliding Windows Leetcode problem she was thinking about, which was fun. I think it's really fun to be able to connect to some of these REU students; for the younger ones, I've been telling them that I'd love to be able to help them in any way I can, especially since I wish I had some mentorship or upperclassmen friends to talk with when I was just starting out at Swarthmore. So for anyone who's younger (or older) and may be curious about anything/want guidance, feel free to reach out!

 I went for a late-night run around the Main Quad to get some extra exercise for the day -- this felt great and I didn't feel any stomach issues, so I was quite happy about that.


#### <u>Day 53 (July 27th)</u>

Week 8 Day 4: Stomachache

- 8:30 - 9:00 AM: Woke up in the morning and to put it simply, stomach felt terrible. The pain was a bit different from previous days though -- it's closer to the chest area and more of a nagging rather than a off-and-on-cramping. I decided to get some extra sleep and not risk any strenuous activity.

- 10:00 AM - 12:00 PM: Really not much to report here, research wise. I was not feeling good after waking up and decided to work from home. This mainly meant staying in bed and grabbing at my stomach. The few tests I tried to run ended up getting CUDA out of memory errors...

- 1:00 PM - 2:30 PM: I grabbed some lunch from PE and met up with the other REU students eating at STAMP. Lunch didn't go too well either with me feeling quite out of it and my stomach still hurting. I attempted to head back to IRB and work there but at around 2:30 decided against working for longer and went back to the dorm to sleep.

- 4:00 - 5:00 PM: I had intended on going to Emily Kaplitz's talk on "Neurodiversity" but my stomach didn't feel good enough to make the walk over to the Math building. I heard the talk was great so it sucks that two of the talks I've wanted to go to the most (Emily's and Evan's) are the only ones I've missed. 

After "research" today, I carried up six (!) 40 packs of water my parents ordered from Costco for me, grabbed dinner at CFA (but got a healthier wrap today due to stomach pain) and talked briefly with AB, LH, and SS. To get my mind off my stomach and jumping in bed (laying down kind of hurts my stomach), I agreed to go to the library to work with LH and AF. After leaving the library when it closed and some more debugging, I managed to get the CodeForces problem I was working on, so that's probably the highlight of my day. I think if my stomach still hurts tomorrow, I'll get another appointment with the doctor... this is probably the worst stretch of the REU thus far so sorry for any new readers who have to read through this stretch...


#### <u>Day 54 (July 28th)</u>

Week 8 Day 5: Recovery

 - 8:30 - 9:00 AM: No morning swim or run today -- just trying to recover fully. I slept with my head on an incline (padded more pillows) and my stomach felt a lot better than when I woke up yesterday (whether or not that is related, who knows). 

 - 10:00 AM - 12:00 PM: I told my group members that I would likely be working from home again today since I didn't feel fully recovered. The pain was still there throughout the morning as well, which made me a bit concerned. Research wise, XG reported that his Reinforcement Learning approach was looking promising, which is great. I tried to run my code, got a few out of memory errors, and so I decided to work on a general Python file that will generate images with the proper prompts instead of working in my typical Jupyter Notebooks. Afterwards, I moved on and began working on my group's final presentation, which we're making in Beamer. 

 - 1:00 - 1:30 PM: I decided to get another doctor's appointment since my stomach pain symptoms were a bit different than the ones on Wednesday. The doctor didn't seem to think the pain was any serious, long-term problem, which was good to hear. I think I will just have to be more careful about what I eat and I think this stomach pain is likely due to some continuation of the effects from last week's. 

 - 1:30 - 4:00 PM: In the afternoon, I kept working on the final presentation slides. I made a slide outlining the presentation and began working on the background/motivation slides. I think I will need to do a slightly better job of explaining the basics of a diffusion model, but the presentation making has been relatively easy so far since we already have a few good baseline slides from our group presentations.

 Post-research, I took a nap before heading over to CVS to get some of the over-the-counter medication the doctor recommended. After walking back to drop off the medication (and some Gatorade), I quickly showered and met SK, SS, CD (one of last year's students visiting), AF, and LH outside to take an Uber to Taqueria Habanero. We got a nice dinner and due to some heavy rain and thunder outside, decided to Uber back. It's always good to talk and hang out with the other REU students -- the best part of it was that my stomach was and has been feeling a lot better. Fingers crossed it stays feeling good throughout the remainder of the REU!

#### <u>Day 55 (July 29th)</u>

Week 8 Day 6: Weekend Recovery pt. 1

- 10:30 AM - 1:00 PM: My big goal this weekend is to recover well from all the stomach pain I've been having. After a good night's rest, I woke up this morning and decided to enter in the CodeForces content being hosted. At the start of the REU, my goal was to keep practicing (at least a problem a day) and to enter in as many competition as I could, and I've been doing this to varying success (I've been doing my daily problems but haven't been doing the competitions as seriously as I would have liked). Despite a subpar performance (solving A in 3 minutes, B in 45ish minutes, and then not getting C1 -- a difficult but doable problem), I'm happy to have at least participated in the contest formally, which is my first formal participation since the REU.

After the contest, I made myself some scraps for lunch. This included a mumbo jumbo of all the food my parents ordered for me due to my stomachaches, including Bananas, Graham Crackers, and Ramen/Noodles. I then upsolved C1 after understanding the solution and mainly lounged around until dinner. There was a rough thunderstorm outside, so I had some noodles and a banana for dinner. 

No stomachache so far, so it's already a good day considering how I've been feeling lately. My parents told me to lay low on heavy exercise for a bit so no running or swimming again today (the bad weather out made other sports a no-go too).

After dinner, AB, DS, LH and I "watched" the movie "My Dinner with Andre." I got kind of lost in the beginning and didn't pay too much attention after a bit, but I thought the overall message was quite nice (in my opinion, to generally enjoy the little things in life).

#### <u>Day 56 (July 30th)</u>

The End of Week 8: Two to Go

It was an eventful morning today -- after initially waking up at 8 and hearing that some of LH's friends (who we were scheduled to meet) were delayed in traffic, I decided to go back to sleep to get an extra thirty minutes of sleep. After waking up, I showered and got ready to meet her friends, grad students studying in the US at Yale, Caltech, and UChicago that she knows from her high school in Vietnam. After some parking problems (we did not know the nearest available parking), we finally met and subsequently decided to head directly to the movie theater. This involved corraling AF and SK out of their suite about 10-15 minutes earlier than expected, so that we could head out on an Uber to the Regal movie theater to watch Oppenheimer. Oppenheimer itself was a great movie -- I very much enjoyed it but also thought it was funny that from about halfway onwards, one of my main thoughts was to hold it in and not use the bathroom (not thinking about using the bathroom for the last thirty minutes turned out to help tremendously). After Oppenheimer, we walked around Silver Springs, MD (where the movie theater was) and decided to head to a nearby sushi place for lunch. AF, SK, and I then Ubered back to let LH hang out some more with her friends on her own. For dinner, I made noodles and ramen for the third time in two days. Post-dinner, DS, AB, SS, and I played some board games in the basement before retiring for the night.

We now really only have 2 (or a week and a half of actual research time) left in the program. I feel like any research progress we can eke out now is incremental, so I've been trying to make the most of the time I have left with everyone before we disperse into our respective collegs and out into the world again...