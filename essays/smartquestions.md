---
layout: essay
type: essay
title: "Questions with Style!"
date: 2024-09-12
published: false
labels:
  - Questions
  - Answers
  - StackOverflow
---

<img width="300px" class="rounded float-start pe-4" src="../img/smart-questions/rtfm.png">

## What is your experience with asking bad questions?

Personally, I am all too familiar with the stinging rejection of asking an half-baked question and recieving an annoyed and or sarcastic response from a school instructor or a friend. In a perfect world, there are no bad questions, but in the real world, bad questions do exist and they rarely end on a productive note. On open source platforms like Stack Overflow, in the worst case bad questions recieve the dreaded "RTFM" or "STFW", and in the best case, a poor kind soul has to decode the asker's labrynthine question to produce a response that aims to at least partially answer the vague and undefined question parameters. However, these unfortunate results can be easily avoided with simple principles guiding how we ask questions. 

## What kind of questions do smart software engineers ask? 

The first criteria for a smart question is that it is a well-researched and educated one. It is important to refrain from impulsively blurting out questions to the open source community, so take a deep breath, and do a quick web search first. The chances are, that out of the millions of programmers in the world, someone has already asked a similar or matching question. If you take this step, I can confidently say that your chances of recieving a "STFW" response are lowered, and at least you will feel better that you already did "search the f**ing web." Coupled with your web search, you will also want to put some thinking into your problem before you ask someone else for help. Try to identify what the problem is specifically, and try possible solutions so that if you can't solve your problem, you'll at least know what doesn't work. It is important for software engineers to do this so that you don't waste not only the open source community's time, but also your own. In many cases, you know your problem the best, and you might have a decent shot at using the time you would've spent trying to explain the problem to someone else on directly solving the problem and cutting out the middle person. 

The second criteria for a smart question should come easily once you've spent some time with your issue. Explain it well! This is yet another reason why becoming educated on your problem is such an important step in the problem solving process, because to explain something you must first understand it. Don't hesitate to put in the extra details of what you've tried so far and where the issue is specifically in your code, because that little bit of extra time might result in you getting a response that will save you days or even weeks of struggling with the problem otherwise. 

Finally, be polite to the people that help you. You're already being courteous by not just shoving the issue in their faces but taking the time to write a good question, but a little online manners goes a long way, especially when you're depending on their kindness for your success in the issue. I'm not going to go into detail on this topic, I trust that you will be able to figure it out yourselves. Now that we've discussed some key characteristics of a good question, lets dive into Stack Overflow to find one!

## Smart Question Example

In the following example, the programmer 

```
Q: python date of the previous month

I am trying to get the date of the previous month with python. Here is what i've tried:

str( time.strftime('%Y') ) + str( int(time.strftime('%m'))-1 )

However, this way is bad for 2 reasons: First it returns 20122 for the February of 2012 (instead of 201202) 
and secondly it will return 0 instead of 12 on January.

I have solved this trouble in bash with:

echo $(date -d"3 month ago" "+%G%m%d")

I think that if bash has a built-in way for this purpose, then python, much more equipped, should provide something 
better than forcing writing one's own script to achieve this goal. Of course i could do something like:

if int(time.strftime('%m')) == 1:
    return '12'
else:
    if int(time.strftime('%m')) < 10:
        return '0'+str(time.strftime('%m')-1)
    else:
        return str(time.strftime('%m') -1)
        
I have not tested this code and i don't want to use it anyway (unless I can't find any other way:/)

Thanks for your help!
```

While the heading of his question could be better, it does convey what he’s trying to figure out. Usually something as brief as “python date of previous month” is what other users would enter in as search terms on Google, making it easily found. Another good thing about the question is that it’s not just a question. The asker shows what he or she has done and that he or she has put in some effort to answer the question. And while it may not be as important as the question itself, the asker shows courtesy, which does increase the chance of getting an answer.

```
A: datetime and the datetime.timedelta classes are your friend.

1. find today
2. use that to find the first day of this month.
3. use timedelta to backup a single day, to the last day of the previous month.
4. print the YYYYMM string you're looking for.

Like this:

 >>> import datetime
 >>> today = datetime.date.today()
 >>> first = datetime.date(day=1, month=today.month, year=today.year)
 >>> lastMonth = first - datetime.timedelta(days=1)
 >>> print lastMonth.strftime("%Y%m")
 201202
 >>>

```
 
The asker received six possible answers, and he or she was successful in inciting discussion from multiple users. The answers themselves were clear and were devoid of the rumored sarcasm and hostility of “hackers.” Since I myself have referenced this page and found it useful, I can confidently say that it is a good question.

## The foolproof way to get ignored.

While there are decent questions that benefit everyone, there are those one can ask to create an entirely different effect. In the following example, a user asks how he would, in short, create a desktop application with Facebook.

```
Q: Facebook Desktop Notifier

I am a beginner programmer that have never used anything other than what's included in a language.

I am trying to create a desktop application that notifies me anytime I get an update onfacebook. 
How should go about doing this? Thanks in advance.

edit Sorry I was not clear. Is there any way to make a DESKTOP application with facebook?
```

A simple “yes” would have answered the question, but we know that’s not the sort of answer he or she is looking for. Fortunately, someone kindly responded with a link to Facebook’s developer website. The asker should have done more research on his or her potential project. Then further down the road, he or she could have asked more specific and detailed questions that wouldn’t require a thousand-paged response for a sufficient answer.

## Conclusion

When we rely on others’ generosity and expertise to provide answers to our questions, it should hold that the question we ask should be one that leads to efficient and effective help that not only benefits us, but also the people we ask and others who might ask the same question in the future. Thus, if you have a question… make it a smart one! Asking questions may not always get you the best answer, but asking them in a way that will make others want to answer them will increase the success of finding a good solution and make it a positive experience on all sides.
