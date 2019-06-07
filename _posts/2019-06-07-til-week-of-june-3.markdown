---
layout: post
title:      "TIL: Week of June 3"
date:       2019-06-07 10:53:33 -0500
permalink:  til_week_of_june_3
---

Mon. June 3

Olga and I continued to work on our client project for the front-end in React Native. We are running into a lot of errors, seeming to do with Expo. Expo SDK is a set of libraries that are supposed to make programming in React Native a lot easier and faster, but it does not seem to make testing any easier. There is a `jest-expo` preset, but it seems to set off a bunch of issues with the Babel compiler.


Tues. June 4

We continued to work on trying to set up tests for the client project, but it was another day of going around in circles trying to configure jest. Towards the end of the day, I tried using Jest & Enzyme instead, and I was able to get a snapshot generated within minutes. We still want to try to get it working with the jest-expo preset that the client already set up in `package.json`.


Wed. June 5

We were able to put in tests today, but we are unable to get the iOS simulator to run on localhost. It seems to have to do with Expo not rebuilding the `shell-app-manifest.json` file with the staging URL that we specify. The workaround that Connor figured out so far, is to remove the `ios` directory and detach expo again with the ExpoKit setting. It requires us to install pods again and link tipsi-stripe to it again.


Thurs. June 6

We finally made an MR for the front-end, and since tomorrow is _supposed_ to be the last day working on the client project, we hope to get some feedback so that we can make an ammended MR before we are done with it. I also worked on trying to finish my TTT game in C#, but I'm not yet too happy about the PR I made today. It was hard to try and manage doing both client work and my personal project, but I'm glad I was able to make the PR and gain some feedback. Hana asked me to try to think of a pattern to check for win patterns without explicitly checking each win combination. I agree the code that I had was quite repetitive, but I didn't even think I could come up with any logic. Hana told me to compare a 2x2 and 3x3 grid board, and how the wins are calculated for them. It took me a couple minutes, but I was able to see some type of pattern after she gave me this hint! I've pushed another commit to address this and am curious to see if I was heading towards the right direction.