---
layout: post
title:  REU-CAAR, Week 6
date:   2023-07-16
description: Week 6 of my Summer 2023 experience @ REU-CAAR.
tags: research cs
categories: caar
---

#### <u>Day 36 (July 10th)</u>

Week 6, Day 1

 - 8:30 - 9:00 AM: Week 6 here we go! Unfortunately, lane lines were being moved at the pool (again) and so my morning workout started closer to 8:40/8:45 than 8:30. Regardless, I managed to make the most out of the situation by going for 40 laps in just around 20 minutes, which is a much quicker pace (close to 2:00/100yd) than I have been going.

 - 10:00 AM - 12:00 PM: To start off this week, I wanted to wrap up my work with the confusion matrices that I've been coding (the confusion matrices show us which genders/races our classifier outputs compared to the true genders/races for all our images). Over the weekend, I was able to get the confusion matrices to show percentages, but I also wanted to show the raw numbers (in terms of how many examples it classified for each of the given predicted/true race and gender combos). In the morning, I managed to get the code working for our smaller testset example. As I've been doing throughout the last week, I always code up a sample, get it working on the testset, and then replicate the code for the entire FairFace validation set.

 - 12:00 - 1:00 PM: We had our weekly REU lunch talk. This time, Jim Purtilo, a Professor at UMD, talked about Software Engineering (what is it, what is important to succeed, etc.) and we got free catering from Q-Doba (note: important to get there early to make sure food does not run out). Overall, I thought it was a fun, interactive talk -- and the ideals stressed to succeed in Software Engineering obviously apply to research as well (effective communication)!

- 1:00 - 4:00 PM: The afternoon session was a bit less productive for me. I ran my updated confusion matrix code on my FairFace validation program, which takes a while. I've currently set it up so that the classifier results are saved in a CSV (so I can theoretically read the CSV for the results and save the time that the classifier takes to run on each of the 10,000 images in the FairFace validation set), but for now, I've just been running the classifier on the same set of images. I think this will change (the code to read the CSV is not terribly difficult) as I continue to run more tests, but since my work today essentially closed the chapter (for now) of testing the DeepFace classifier on the FairFace dataset, I will hold off on that front. Tomorrow, I'm hoping to start researching/looking into how I can implement the Linear Head approach I've been discussing throughout these notes. When I get the time, I'll also happily share the confusion matrices I generated (essentially the product of my last week and a half which is cool yet a bit sad as I think I could have done it faster) here.

After research, PM and MA finally decided to purchase gym passes (their timing lines up with the start of the second summer session at the gym, meaning they pay less than what most of us paid at the start of the program -- when it was the middle of the first summer session), so PM, MA, DS, SS, and I went to play basketball. SS wanted to get a healthier dinner (than CFA), so DS and I decided to join her at Yahentimisi, one of the main dining halls on campus, where we ran into CK. Afterwards, I went back to the dorm to relax, work on some CodeForces, and read. I'm starting the book "Atomic Habits," which my parents brought over per my request when they came to visit. I think it'll be good to get some reading in as it will mean less screentime before bed and more learning. 

#### <u>Day 37 (July 11th)</u>

Week 6, Day 2

 - 8:30 - 9:00 AM: Got my morning swim in today, going for 50 laps in just under 30 minutes. My arms and legs felt like jelly after playing basketball and swimming yesterday, but it was good to power through this morning.

 - 10:00 AM - 12:00 PM: I was hoping to start working on the linear head approach today. I started working on a related topic (one that we need to have working before we can even train a linear head) by combining my work over the last week with our previous "detect and classify program." More specifically, we need to set up an image to classification pipeline which we will need to train a linear head. After running into some small errors, I took a break and joined the GatherTown (online environment where the virtual conference is held) for the [ACL: Association for Computational Linguistics Conference](https://virtual2023.aclweb.org/index.html), a conference that SS was planning to attend but cannot due to a visa situation. It turns out that another one of my friends who is a PhD student at UPenn is actually there in person as well, which is a cool coincidence. For some reason, the GatherTown is publically available, meaning I can interact with virtual participants/look at their posters; this was a nice "break" from research and it was definitely cool to look at all the work being done at this NLP conference.

 - 1:15 - 4:00 PM: I have to start by admitting that these last few afternoon sessions have not felt as productive as normal for me. After finishing up the image to classification pipeline that I had started in the morning (it was not too hard to fix this up), I mostly spent some time looking into how we can get Stable Diffusion (or really any other diffusion model) to run locally. The general pipeline we will need is Text-to-Image into Image-to-Classification into updating a Linear Head. Since we've solidified the first pipeline, we will need to work with the first one (Text-to-Image, essentially a diffusion model) before we start building out the third one.

 After research, I took a nap (my first one of the REU) before grabbing some CFA for dinner. There were plans to watch a movie earlier (but still after research) but nothing materialized, but after waking up from my nap, I tried to get something going. I ended up watching "Taken" with the typical group (SS, DS, and AB). Tomorrow night, we'll have a meeting with our advisor to update her on progress and to talk about next steps -- I think this will be really useful as I orient myself for the second half of the REU.

 #### <u>Day 38 (July 12th)</u>

Week 6, Day 3 -- Meeting Day #5

 - 8:30 - 9:00 AM: Got to the pool at around the right time today and got in a solid workout -- 50+ laps in just around 30 minutes. I've been feeling a bit out of it this week but it's been good to push through and stay consistent with the swimming workouts.

 - 10:00 AM - 12:00 PM: As I wrote yesterday, my goal for now is to get Stable Diffusion (or really any diffusion model) working locally, so that I can start to generate images, pass it to the image-to-classifier pipeline, and then start to train a linear head on these results. After finding some tutorials on [Stable Diffusion rom HuggingFace](https://huggingface.co/blog/stable_diffusion) and others, I began with some starter code and attempted to get it working. First, I copied over the work I've done to a `nexus-scratch` local directory (that has 200 GB of memory compared to the 20 GB on our personal accounts), so that I can generate images with Stable Diffusion (which takes quite a bit of space). Unfortunately, this led to a debugging spiral -- running the Stable Diffusion model in the scratch directory somehow used my local disk space (which there is not enough of) rather than the `nexus-scratch` space that I have an abundance of. Heading into lunch, I was definitely frustrated as a number of attempts I had to fix the issue did not work.

- 1:00 - 4:00 PM: After asking AF and XG for some suggestions on how to fix the storage issue, I followed some ideas given by AF (and StackExchange), finally fixing the issue. It turns out that I had to set three different shell environment variables to move my cache directory from my personal to my local `nexus-scratch` directory. Finally, after some long and frustrating debugging, my issue had been fixed. In the remaining time, I experimented with negative prompts to try and get the diffusion generated images (especially the faces on people) to be less deformed/blurry. I will continue to work on this tomorrow and start to extend this towards the linear head idea.

I've been feeling quite tired after research these last few days. I think part of this may be because I am a bit bummed about not having that much research progress, but I may also have to sleep earlier/swim less or not as intensively. I'm hoping this is just a bit of a rut I'm in but will continue to evaluate and prioritize my well-being.

- 8:00 - 9:00 PM: Our group had originally planned to meet up in the basement and join the meeting, but plans fell through and we all ended up Zooming in from individual rooms. Our advisor showed up a bit late so we started closer to 8:10. I mainly discussed the DeepFace classifier results I had on the FairFace validation set and upcoming plans for the Linear Head approach. SS discussed her Erasing Concepts approach, AF her Domain Translator approach, and XG his Reinforcement Learning approach. Overall, I think we all have some work to do on our approaches -- our advisor offered some suggestions but we all need to build on our approaches and experiment some more.


#### <u>Day 39 (July 13th)</u>

Week 6, Day 4

- 8:30 - 9:00 AM: I decided to skip my typical morning swim as I've been feeling a bit tired during morning workouts/in general this week. My plan was to go for a swim after a REU-planned talk (so after 5 PM -- more on this later). I actually didn't end up getting any extra sleep in since I set my normal alarms to see if I would feel okay about going out for a swim, but I did head over to Vigilante Coffee to grab some breakfast before the work day.

- 10:00 AM - 12:00 PM: Just like I always do on Thursday mornings, I started off the day by attending my advisor's graduate student meetings. Today, there was a talk about Diverse Reinforcement Learning that was pretty theory-heavy but still good to listen to. The meeting went short since there was only one presenter, leaving me some more time to work on the Stable Diffusion pipeline. I was running into the same problems as yesterday with the cache (for some reason, it seems like I have to run the commands I did every time I start up the server). To fix this, I added the commands to my `~/.bashrc` files and started to test some more. My goal over these next few days will be to improve the Stable Diffusion outputs on group images. I started working with some negative prompting (and it seemed to work relatively well yesterday), but after further testing today, the faces are still relatively deformed/blurry. Obviously, we want our generated images to be as good/high-quality as possible, so hopefully we can improve this a bit more.

- 1:30 - 4:00 PM: My group ran into some problems with card access on Conference Rooms so we ended up working in a general working area. Any work progress, however, got quickly derailed by the news that someone in my dorm suite had tested positive for COVID, making me and others (including my other suitemates and their research groups) at risk. We were called down to take COVID tests (we all tested negative) and later told to isolate until Monday. For now, I feel okay and this seems to be more of an incovenience than a serious problem (the best case is that this is all it is), but it means that I will be working "from home" tomorrow and isolating in my room.

- 4:00 - 5:00 PM: There was a research talk by Evan Golub on "How to Do Bad Science" that I was looking forward to (we were told to watch a TED talk and read some comics in preparation for the talk and ensuing discussion, and both of these were interesting), but obviously with the COVID situation, I had to miss out on the talk.

Post-research plans to go get my swimming workout in were obviously also derailed, but I did end up going for a quick 2-mile run before grabbing CFA dinner for the third day in a row (I was wearing a mask for this). For the rest of the week, I'll be isolating and grabbing food with a mask on while working from home. This is a bit of a bummer but I'm hoping my REU friend recovers quickly and that no one else has COVID/becomes symptomatic. Fingers crossed!

#### <u>Day 40 (July 14th)</u>

Week 6, Day 5 -- Work from Home Day 1

 - 10:00 AM - 12:00 PM: Since I'm self-isolating, I am not able to go for morning swims -- instead, I get an extra hour of sleep. Today is the first and hopefully last day of working from home. I started the day by continuing my work from previous days -- trying to get better diffusion model output for group pictures. For some reason, I was getting the same out of storage issues as I've been getting the past few days, and my `.bashrc` file was completely empty! I quickly added the commands from before into the file and ran them in the terminal as well to set my cache to my scratch directory. It's a bit annoying to have to deal with the same problems every time, but hopefully I won't have to do this for much longer. After some basic experimentation with negative prompting and group images, I didn't find any improvement in the stable diffusion generated images. For the remainder of the morning, I thought about some limitations of our project and added them to a slideshow for our next meeting. Some problems include:

  > In our generative process, our stable diffusion generated images yield deformed/blurry faces for people in group photos. Obviously, we want the faces to be as normal/human-like as possible. (This is what I've been experimenting with the past few days, to not much progress).
  > In our general pipeline, we use stable diffusion generated images (see above), then pass those generated images to a face detector/gender and race classifier. As I've written before, the gender/race classifier is itself imperfect/faulty (it especially has trouble separating Middle Eastern people from Latino Hispanic people). Since we are using this classifier in an attempt to get "fair image generation", our "fair images" may also be affected...

These are two big areas that we will need to further think about/address. We don't have immediate answers for either of these yet either, but we will need to work on both of these areas (and others).

- 1:00 - 4:00 PM: It turns out that the HVAC (water, air conditioning system) in Iribe, the main CS building where the rest of my group and other non-quarantined research groups are working, went out in the morning. From what I heard, everyone dispersed back to the Student Union for an early lunch, and my research group didn't end up working together in the afternoon session. It sounds like it's been a rough few days overall for the REU with the COVID positive case and the HVAC system going out. Overall, though, nothing really changed in my afternoon plans since I was working from home. I did a bit more experimentation with Stable Diffusion -- it turns out that giving the prompt "give me a portrait photo of a doctor" (i.e. asking for a single person image output) along with negative prompts generates a much more realistic photo than the group image prompts. In the future, I'm hoping to test the classifier on the single-person generated images to get a sense of the problems we may have look more into. 

It has sucked not being able to do much outside of stay in my room due to the protocol for COVID isolation. Though I was planning to go for a run right before dinner, the minute I stepped outside, it started raining, which sucks. I went back to grab my umbrella and head over to grab some dinner from the Ramen shop nearby. On the way back, I also noticed that my umbrella is kind of broken, which double sucks. After letting my dinner digest for a bit, I went out for a three mile run around campus; it was a lot cooler than previous days, especially later at night, so the run felt quite nice. It's definitely felt good to get a bit of exercise after staying in my room all day.

#### <u>Day 41 (July 15th)</u>

Week 6 Day 6

Today was definitely a more chill day for me. In the morning, I worked on some CodeForces problems. For an early lunch, I finally finished the tub of Greek Yogurt I got a week or two ago (along with the Frozen Strawberries, Granola, etc). In the afternoon, I ended up going for a run to get in some exercise. I went on the Paint Branch Trail before running around a really nice lake (Lake Artemesia), where there are 1.3 mile loops around the lake. The run ended up being 3 miles (I had planned to run longer but was really tired), and I walked another loop around the lake before heading over to Playa Bowls to get some water and an acai bowl. I usually run later in the day (closer to dinner) but the weather report said it was going to thunder at 4 PM -- it did not. Today was definitely a pretty basic yet relaxing Saturday; I'm feeling good health-wise as well and don't appear to have any COVID-like symptoms.


#### <u>Day 42 (July 16th)</u>

The End of Week 6

I woke up earlier today hoping to head out to grab some breakfast and then participate in the CodeForces contest. I'd say I kind of did both of these things -- I heated up some Bagel Bites before the contest and ended up doing the problems concurrently (but not submitting anything since both the first two problems were tedious/long/tricky). I keep telling myself that I should be actually participating and submitting in these contests but honestly, both problems took me a while to solve. I am happy that at least I made the effort to participate in the contest/try the problems despite the fact that self-isolating has sort of sucked mentally (not meeting others, staying in the room, no swimming exercise). 

Post contest, I ended up submitting and debugging my work for B and reading a bit about a simple solution for A (some people said A was harder than C or D), which was a tough problem to get if you hadn't seen it before. I also watched the Wimbledon Tennis finals, which was cool and motivating for me to play more tennis (unfortunately, not today even though I typically swim -> tennis on Sundays since I'm supposed to be isolating for at least another day).

In the afternoon, I mainly read and relaxed since all the screen time from the morning hurt my eyes. I went for a quick run around campus and then to Potomac Pizza, where I beasted 5 pieces of a Large Combo pizza down (I am realizing now that I had pizza-like food for both "meals" today). After a long, tiring walk back home (I was so full), I ended up cutting and eating up some of the watermelon my parents brought over. 

This was a good day to wrap up the sixth week. The only sad part of the day was that the monitor I ordered on Amazon for Prime Day seemed to not get delivered despite two attempts (all other Amazon packages I've ordered here have come perfectly fine), but it'll hopefully arrive tomorrow. In terms of research, I'm back to some serious work tomorrow -- I think I will work more on diffusion model output and analyze the results on the DeepFace classifier.