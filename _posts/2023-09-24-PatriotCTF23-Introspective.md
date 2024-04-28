---
layout: post
title: PatriotCTF 2023 - Introspective
excerpt: "Earlier this month, September 8th-10th marked this years PatriotCTF. We had over 3000 users from over 30 different countries play with us this year. This was my first year hosting it as Vice President of the GMU Cyber Security Club, MasonCC. I wanted to write a post about the infrastructure behind the CTF and some of the challenges we faced."
categories: [Learn]
tags: [Infrastructure]
---
<p align="center">
  <img src="https://competitivecyber.club/images/transparent.png" alt="MasonCC Logo" width="175px" height="175px">
</p>
> This site is now archived. Please visit [https://jax.dev/blog](https://jax.dev/blog) for the latest content.
Earlier this month, September 8th-10th marked this years PatriotCTF. We had over 3000 users from over 30 different countries play with us this year.  This was my first year hosting it as Vice President of the GMU Cyber Security Club, MasonCC. I wanted to write a post about the infrastructure behind the CTF and some of the challenges we faced.

## CTF Design
Design was very important to us this year, PatriotCTF has always been a beginner focused CTF and we wanted to make sure that was reflected in the design. 

### Challenge Difficulty
We wanted to make sure that the challenges were not too difficult, but also not too easy. It was our goal to make sure that the challenges were accessible to beginners, but also had some challenges that would be interesting to more advanced players. We projected that the CTF would have around ~2000 players, so we wanted to make sure that we had enough challenges to keep everyone busy, without diluting the quality of the challenges. 

As a lot of our expected players would be getting introduced to CTFs through PatriotCTF our primary objective was to guarantee that the challenges could be successfully solved using the provided information, while also ensuring they were not excessively cryptic. Regrettably, we encountered a challenge in the realm of hints, as we had implemented a points-based system for hints, a decision we now regret as it had unintended consequences on the scoring system.

Moving forward, we are committed to ensuring that our challenges strike the right balance of complexity without veering into obscurity. Additionally, we will be reevaluating our approach to hints, with the intention of providing them at no cost if deemed necessary.

### Team Size
We decided to go with the controversial decision of allowing teams of any size. Regrettably, we've found from past events of ours that limiting team size does little to prevent cheating by sharing accounts, and only serves to discourage new players from participating. We wanted to make sure that we were as inclusive as possible, and we felt that allowing teams of any size was the best way to do that.

### Challenge Categories
We wanted to make sure that we had a good mix of challenges, so we decided to go with the following categories:
- Web
- Pwn
- Reverse Engineering
- Forensics
- Open Source Intelligence
- Cryptography
- Miscellaneous

We wound this to be a good mix for all of the challenges we had planned, and we were able to get a good mix of beginner and advanced challenges in each category. We did have a few categories that were filled with more challenges than others, but we were able to get a good mix overall.

### Communication
We wanted to make sure that we were able to communicate with our players as much as possible, so we decided to go with Discord as our main communication platform. We had a Discord server set up for the CTF, and we had a channel for each category, as well as a general channel for questions and announcements. We also had a channel for players to open tickets if they had any issues with any of the challenges. 

From some feedback, we received after the CTF, we found that some players were not aware of the Discord server, so we will be making sure that we make more use of the inbuilt notification system in CTFd to make sure that players are aware of any announcements we make. 

## Infrastructure
In the orchestration of PatriotCTF 2023, our technical infrastructure served as the backbone of the event, consisting of two distinct servers, each contributing to the seamless execution of the competition:

### CTFd Server
The first server, exclusively dedicated to the Capture The Flag platform (CTFd), was instrumental in housing challenges, managing submissions, and administering the core functionalities of the CTF. It formed the primary interface through which participants interacted with the event.

### Remote Instances Server
Our second server, devoted to remote instances, played a pivotal role in hosting challenges that necessitated a remote environment(pwn, web). In a pursuit of optimal performance and security, we initially employed custom services. However, in a strategic pivot aimed at refining our approach, we transitioned to the redpwn remote binary jail solution.

### Unveiling the Enigma
Intriguingly, the challenges we encountered during the event did not stem from the choice of server infrastructure or the remote solutions deployed. Rather, the issue was rooted in a seemingly innocuous technical detail—the failure to flush standard output (stdout) before initializing the binary.

The stdout flushing oversight, although inconspicuous, held the key to ensuring the smooth operation of the event. Both our original custom services and the later-adopted redpwn solution were technically sound and would have operated flawlessly had it not been for this seemingly trivial omission.

### CTFd Challenges: Unveiling MongoDB Bottlenecks
On the CTFd side of our infrastructure, we encountered a more tangible challenge. The MongoDB connections, pivotal for managing data and submissions, were strained beyond the existing server's capacity. This bottleneck manifested as latency and performance issues, affecting the overall user experience.

To address this, we initiated a comprehensive overhaul. This included upgrading the server to bolster its capabilities, augmenting the worker limit to increase concurrent database interactions, and raising the overflow limit to accommodate spikes in traffic.


## Business 
The success of PatriotCTF'23 would have remained a distant dream if not for the invaluable support of our sponsors, CACI and GMU Volgenau School of Engineering. Their unwavering commitment to not only this event, but our club in general has been instrumental in making this event a reality, and we deeply appreciate their generosity. We look forward to the prospect of forging lasting partnerships with them in the days to come.

Additionally, we offered our sponsors the chance to contribute challenges to the CTF, and CACI eagerly accepted this opportunity. Their valuable contributions led to the creation of numerous thought-provoking challenges that significantly enhanced the event. We wish to reiterate our heartfelt appreciation for their support and eagerly look forward to the possibility of collaborating with them on future projects.


## Lessons Learned
The success of PatriotCTF'23 undoubtedly marked a significant milestone in our journey, but it also provided us with invaluable insights and valuable lessons to carry forward into the future. These lessons will serve as the cornerstone of our preparations for next year's event, ensuring that PatriotCTF continues to evolve and improve.

### Continuous Improvement
Success is a journey, not a destination. PatriotCTF'23 was a resounding achievement, but it also ignited our passion for continuous improvement. We recognize that every CTF presents unique challenges and opportunities, and we are committed to learning and evolving with each iteration. Our goal is to make each successive CTF even better than the last.

### Effective Communication
Effective communication is the lifeblood of any event, and we are committed to enhancing it further. While Discord served as our primary communication platform, we understand that there is always room for improvement. We will leverage the experience gained to ensure that participants are well-informed and have a seamless experience.

### Technical Resilience
Our technical infrastructure played a pivotal role in PatriotCTF'23's success, but it also exposed areas for enhancement. We have learned the importance of meticulous planning and redundancy to ensure uninterrupted operations. Strengthening our technical capabilities will remain a top priority.

### Sponsorship and Collaboration

The support of our sponsors, CACI and GMU Volgenau School of Engineering, was instrumental in PatriotCTF'23's success. We value these partnerships deeply and are committed to further collaboration. We will explore avenues to deepen our connections and continue enriching the CTF experience.

## Conclusion
In conclusion, PatriotCTF'23 was not just an event but a profound learning experience. We are grateful for the opportunities it presented and the community it brought together. With these lessons in mind, we look forward to PatriotCTF'24 with a sense of purpose and excitement, eager to create an even more engaging, educational, and enjoyable experience for all participants. 

I would like to thank the entire PatriotCTF team for all of their hard work, Tanner for staying up a bit longer than he should have to answer tickets (and doing a lot of the infra), Dylan for carrying the pwn category on his back, and everyone else who helped make this event possible.

Thank you for being a part of our journey, and we can't wait to see you next year!