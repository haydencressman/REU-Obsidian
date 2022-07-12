[[Table of Contents W6]]

## Steps to Take
1. Create the code so that is just does what has been done before. This time though check the [EntropyHub](https://www.entropyhub.xyz) documentation and see how to use the functions they already give us. Also read what Dr. Li said about the tau and what it should be or if it should just stay 1 or whatever it is as default.
2. Ok this might have to come first but use both pandas and glob to grab all the files within that dataset that was given to you by Dr. Li so that you don't have to hand type each and every file path like a dirty ape.
3. Figure out how to *write* this newfound data into an excel spreadsheet and maybe save and label different graphs for later use.

This is going to take a while so just get the part where you get all the files and their data separately first, and worry about the algorithms and output later.

---
so for the finding of the data in the files, try to just get the names of files then append the total filepath and set up a big list of the datasets from pandas. from there maybe generate a few with *this* code and then plug some of those into previous code to see if its correct or if something is wonky. This is going to take a while.

---
7/9/2022
so far so good, got the file names for the control group in not a long amount of time, thought it would take longer. So now all we need to do is get the data into dataframes and then do the same with the ASD data. After that it shouldn't take long to just copy what we've done so far with the rest of the data, and it might even take less time since we now have EntropyHub. 

---
7/11/2022
The code for the control group is good, just need to do the thing with selecting the one with the higher stability. Actually before I start on that I should email Dr. Li about it one sec...
Ok emailed him, just said to compare the areas and path (whichever is shorter has the best stability). I guess we can just show him what we mean on wednesday or tomorrow if we can't figure it out today as to why it's giving us literally ~700 centimeters as the path length on these two subjects because otherwise the area and displacement looks good. Who knows.

Added some stuff on both the control group and the ASD group. For some reason the path length is always acting weird. I have no reason to believe it's wrong, I just feel like it might not be a great data attribute or maybe I am just calculating it wrong. It's weird. I sincerely think it is from the fact that they have more data points in the control group or something or maybe it's just because they're kids. We shall see tomorrow because seriously I am *bushed*. A literal bush. I grow leaves from my thorax.

---