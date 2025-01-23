---
layout: essay
type: essay
title: "The Question is in the Details"
date: 2024-09-12
published: false
labels:
  - Questions
  - Answers
  - StackOverflow
---

## What is your experience with asking bad questions?

Personally, I am all too familiar with the stinging rejection of asking an half-baked question and recieving an annoyed and or sarcastic response from a school instructor or a friend. In a perfect world, there are no bad questions, but in the real world, bad questions do exist and they rarely end on a productive note. On open source platforms like Stack Overflow, in the worst case bad questions recieve the dreaded "RTFM" or "STFW", and in the best case, you get an answer, but maybe not as helpful of an answer that you wanted. However, these unfortunate results can be easily avoided with simple principles guiding how we ask questions. 

## What kind of questions do smart software engineers ask? 

The first criteria for a smart question is that it is a well-researched and educated one. It is important to refrain from impulsively blurting out questions to the open source community, so take a deep breath, and do a quick web search first. The chances are, that out of the millions of programmers in the world, someone has already asked a similar or matching question. If you take this step, I can confidently say that your chances of recieving a "STFW" response are lowered, and if you do recieve one still, at least you will feel better that you already did "search the f**ing web." Coupled with your web search, you will also want to put some thinking into your problem before you ask someone else for help. Try to identify what the problem is specifically, and try possible solutions so that if you can't solve your problem, you'll at least know what doesn't work. It is important for software engineers to do this so that you don't waste not only the open source community's time, but also your own. In many cases, you know your problem the best, and you might have a decent shot at using the time you would've spent trying to explain the problem to someone else on directly solving the problem and cutting out the middle person. 

The second criteria for a smart question should come easily once you've spent some time with your issue. Explain it well! This is yet another reason why becoming educated on your problem is such an important step in the problem solving process, because to explain something you must first understand it. Don't hesitate to put in the extra details of what you've tried so far and where the issue is specifically in your code, because that little bit of extra work might result in you getting a response that will save you days or even weeks of struggling with the problem otherwise. 

Finally, be polite to the people that help you. You're already being courteous by not just shoving the issue in their faces but taking the time to write a good question, but a little online manners goes a long way, especially when you're depending on their kindness for your success in the issue. I'm not going to go into detail on this topic, I trust that you will be able to figure it out yourselves. Now that we've discussed some key characteristics of a good question, lets dive into Stack Overflow to find one!

## Smart Question Example

Here is an example of a smart question in Stack Overflow. Here is a link to the question for your reference: [Stack Overflow](https://stackoverflow.com/questions/6802483/how-to-directly-initialize-a-hashmap-in-a-literal-way/6802512#6802512)

```
Q: How to directly initialize a HashMap (in a literal way)?

Is there some way of initializing a Java HashMap like this?:

Map<String,String> test = 
    new HashMap<String, String>{"test":"test","test":"test"};

What would be the correct syntax? I have not found anything regarding this. Is this possible? I am looking for the shortest/fastest way to put some "final/static" values in a map that never change and are known in advance when creating the Map.

```
After reading through the question, a few things might stand out to other programmers that would encourage them to answer this person's question. First of all, the asker says that they have not found anything regarding their question. This means that they have been thinking about their issue and have already tried looking for an answer elsewhere. Secondly, they asked a very specific question about the functions that they are looking for in a HashMap Initialization which allows other programmers to provide a detailed and accurate answer. Finally, the writer of this question is reasonably polite about their question. They don't necessarily go out of their way to be polite, but they definitely are not demanding help and do not act entitled about their question. 


```
A: In case you happen to need just a single entry: There is Collections.singletonMap("key", "value").

For Java Version 9 or higher:
Yes, this is possible now. In Java 9 a couple of factory methods have been added that simplify the creation of maps :

// this works for up to 10 elements:
Map<String, String> test1 = Map.of(
    "a", "b",
    "c", "d"
);

// this works for any number of elements:
import static java.util.Map.entry;    
Map<String, String> test2 = Map.ofEntries(
    entry("a", "b"),
    entry("c", "d")
);
In the example above both test and test2 will be the same, just with different ways of expressing the Map. The Map.of method is defined for up to ten elements in the map, while the Map.ofEntries method will have no such limit.

Note that in this case the resulting map will be an immutable map. If you want the map to be mutable, you could copy it again, e.g. using mutableMap = new HashMap<>(Map.of("a", "b"));. Also note that in this case keys and values must not be null.

(See also JEP 269 and the Javadoc)

For up to Java Version 8:
No, you will have to add all the elements manually. You can use an initializer in an anonymous subclass to make the syntax a little bit shorter:

Map<String, String> myMap = new HashMap<String, String>() {{
    put("a", "b");
    put("c", "d");
}};
However, the anonymous subclass might introduce unwanted behavior in some cases. This includes for example:

It generates an additional class which increases memory consumption, disk space consumption and startup-time
In case of a non-static method: It holds a reference to the object the creating method was called upon. That means the object of the outer class cannot be garbage collected while the created map object is still referenced, thus blocking additional memory
Using a function for initialization will also enable you to generate a map in an initializer, but avoids nasty side-effects:

Map<String, String> myMap = createMap();

private static Map<String, String> createMap() {
    Map<String,String> myMap = new HashMap<String,String>();
    myMap.put("a", "b");
    myMap.put("c", "d");
    return myMap;
}
```

Here you can see that the asker recieved a clear and detailed response to their question regarding multiple ways to approach the problem for different cases regarding Java version and desired use. The educated nature of the asker's question provided the responder with enough material and encouragement for them to produce an appropriate response to the question. Besides this response, there were 21 other answers that the asker could choose from. That's quite a positive response!

## Bad Question Example

The following question clearly has some issues with it, and the response clearly outlines the mistakes that the person asking made. Here is a link to the question for your reference as needed: [Stack Overflow](https://stackoverflow.com/questions/54032781/check-tls1-2-for-sql-server-connection)

```
Q: Check TLS1.2 for SQL Server Connection
I want to check if the connection between my application and SQL Server is used TLS1.2. I disabled TLS1.2 but the connection still happened. I checked via wireshark and saw nothing about TLS1.2.
```

The first thing that you might notice when reading this question, is that the person asking did try to solve the problem on their own. They tried disabling the service and also used wireshark to analyze the traffic for TLS 1.2. However, they included very few details about their issue, which makes it hard for other people to provide an appropriate answer. Additionally, the person asking did not mention doing any research on the issue, which strongly encourages a "stfw" response. Luckily the person who responded to them was polite and as helpful as they could be, but it is clear that they wanted a more clear question for them to work with. 

```
A: Please tell us whether your SQL Server is 2012 as the tag displayed. If so, firstly, please check whether the patch for enabling TLS 1.2 is installed.

Next please check whether the update for client components and drivers are installed.

Please refer to the article: TLS 1.2 support for Microsoft SQL Server.

SQL Server in Windows also supports TLS1.0 and TLS1.1. If you want to use only TLS 1.2 for client-server communication, please disable TLS 1.0 and 1.1.

Please try to disable TLS1.0 1.1 and 1.2, then reboot your machine and test whether the connection can do well.

By the way, you can see the blog to verify if a connection to SQL Server is Encrypted.
```

The question was missing important information like what year the SQL server is, and the mention of different articles and blogs with information on the issue is a clear indicator that the question was wasting the person responding's time a little bit as the person asking could've read those articles before moving on to the open source community. The question is a little rude, and for a less polite person, would have elicited an equally rude response back. 

## Putting it into practice

When working with people, the concept of giving and taking is ever present. Online open source communities are no different. If you want someone to put a lot of effort in their response to your question, it helps to put a lot of effort into asking your question! One thing I have noticed while going through questions on Stack Overflow is that the more details and specifications one can include in their question, the more precise and clear the response is. Because even if there are kind people out there who are willing to sit and think about a vague question for a while, they will have to still ultimately give a vague response because that's what they're basing their answer off of.So make it easier for yourself and them, and ask detailed, smart questions! 
