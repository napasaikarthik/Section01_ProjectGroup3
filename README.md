# Section01_ProjectGroup3
# Data Mining

# TWITTER ANALYSIS

# OVERVIEW

Twitter is one of the popular social network where people post their views on everything from their personal problems to social issues. They also discuss about all the topics in the world. 7168 tweets are produced every second. All the predictions on sports, politics and all the data for analysis on social issues are taken form twitter posts. By using this data, we can represent what people are thinking.

# DATASETS:

+ Finding data using twitter is very simple because each topic is mentioned using a hashtag. Every hash tag helps the users to follow them and retweet accordingly. In our project we are going to use hash tags to track down the user post on the topic.
The data we collect from twitter is not structured. So we try to retrieve only location, timestamp, message, and hashtag used. We can use different tools to represent the data some of the potential tools I have explored are Splunk and microstrategy. These tools are even used in bigdata applications
We collect all this data using the twitter API, which help us to retrieve the data using the Java code.

# RESEARCH QUESTIONS

Now we are going to retrieve the tweets on the present presidential elections.
•	Which states in the country are showing interest in the presidential elections?
•	Which candidate is being more popular in the discussions?
•	How many users are active on a particular GOP?
•	What is the time period where the users are active?

# Models and Analysis

1. Model is prepared using 2 data files 
   1.1 USA Candidate list 
   1.2 State list of USA 

2. Model make we used only java regex. Using Java Regex   we classified data according to  2 above files (state list and candidate list )

3. When we got tweets then we first we classify data according to candidate for this we are applying java regex . One candidate can have more hashtags or name so we put all names for all candidate corresponding. 

Like for  Donald J. Trump twiter users use @trump , #trump , #trump2016 , @realdonaldjtrump , #donaldjtrump  . so we counting all tweets for trump which have these hashtags or handler .


4. For state wise classification we have list of USA states. When we are getting data then we first we are checking tweet location if tweet location is not null then classifying data state wise using java regex . if tweet location is null then we are check twitter user location then we are classifying according state wise . Twitter user most probably does not on GPS so tweet location come null, thats why we also considered user location which is provided when user created account.


5. Location wise active user count also based on tweet count. 

6. Time period also done using tweets based first we are stored data in cassandra and then counting which time period have more tweets 


7. We done below four analysis using tweet count based 
   
   1. Which states in the country are showing interest in the presidential elections?
   2. Which candidate is being more popular in the discussions?
   3. How many users are active on a particular GOP?
   4. What is the time period where the users are active?

Above four analysis done based on only tweets count based . 
like if state texax have more tweets than other states then texas is more interested in  election .

# Requirmennts and Installation Notes
Installation
-----------

```
1. Requirement

1.1 Apache Cassandra(version >= 2.1.8)

1.2 Java (version>1.7)

1.3 Maven (version >= 2)

1.4 eclipse

2. Introduction

Twitter Data mining take data according to hashtags using twitter streaming api . So it will

collect data real time and store in cassandra using some custom classification methods and

data cleansing operation .

After user can see some analytics based on stored data into cassandra . like popular usa

presidential candidate , states those showing interest into election .

3. Intallation

3.1 Java Install

By default window have java only path have to set for java . use following link to set path

https://java.com/en/download/help/path.xml

3.2 Apache cassandra install

First download tar file of apache cassandra from below link

http://cassandra.apache.org/download/

After this extract tar file on one location .this will provide one apache cassandra folder .

Run :- user first have to go apache-cassandra-*.*.*/bin by cd command

WINDOW USER can run by directly writing cassandra

UBUNTU USER have to run this command ./casssandra

After run on cassandra user have to run command line tool to create keyspace and tables

WINDOW USER can run by directly writing cqlsh

UBUNTU USER have to run this command ./cqlsh

After this user have to create database and table by following script user can create database and tables

for this application

CREATE KEYSPACE twitter WITH replication = {'class': 'SimpleStrategy', 'replication_factor': '1'}

AND durable_writes = true;

use twitter ;

CREATE TABLE twitter.keywords (

keyword text PRIMARY KEY

CREATE TABLE twitter.mentionperson (

name text,

id bigint,

interest counter,

PRIMARY KEY (name, id)

CREATE TABLE twitter.states (

state text PRIMARY KEY,

interest counter

CREATE TABLE twitter.activeusertimeperiod (

state text,

date text,

endtime text,

starttime text,

PRIMARY KEY (state, date)

CREATE TABLE twitter.tweets (

country text,

year int,

month int,

day int,

hour int,

second int,

tweetid bigint,

retweetid bigint,

created_at timestamp,

tweet text,

PRIMARY KEY (country, year, month, day, hour, second, tweetid, retweetid)

3.3 Maven install

To install maven on Window use following link reference

http://www.avajava.com/tutorials/lessons/what-is-maven-and-how-do-i-install-it.html

4. UI OF THIS APPLICATION

4.1 UI have streaming start and stop button . By this button user can start get data and stop also.

4.2 Submit button insert new hashtag to track using streaming api .

4.3 Analysis Button will give all analysis .
```



# CODE AND APPLICATION
+ Code is posted in the GitHub link.

# Final Results
-----------

```
State interested in election
"Florida"
"Texas"
"Georgia"
"New York"
"California"
"Virginia"
"Washington"
"Pennsylvania"
"Indiana"
"Oklahoma"
"Kansas"
"North Carolina"
"Arizona"
"South Carolina"
"Missouri"
"Ohio"
"Mississippi"
"Michigan"
"Maryland"
"Colorado"
"Louisiana"
"Illinois"
"Kentucky"
"Tennessee"
"Massachusetts"
"Delaware"
"Alabama"
"Vermont"
"New Jersey"
"Iowa"
"Minnesota"
"Oregon"
"Arkansas"
"Wisconsin"
"West Virginia"
"Nevada"
"Connecticut"
"Maine"
"New Mexico"
"Idaho"
"New Hampshire"
"Nebraska"
"North Dakota"
"Utah"
"Wyoming"
"South Dakota"
"Hawaii"
"Montana"
"Alaska"
Candidate famouns in election
realdonaldtrump":1094
"tedcruz":79
"hillaryclinton": 76
"sensanders": 58
"johnkasich:6
Active user count state wise
"Florida":398
"Texas":341
"Georgia":292
"New York":280
"California":266
"Virginia":251
"Washington":233
"Pennsylvania":227
"Indiana":208
"Oklahoma":140
"Kansas":123
"North Carolina":122
"Arizona":111
"South Carolina":108
"Missouri":107
"Ohio":93
"Mississippi":90
"Michigan":89
"Maryland":89
"Colorado":87
"Louisiana":85
"Illinois":84
"Kentucky":76
"Tennessee":73
"Massachusetts":71
"Delaware":69
"Alabama":67
"Vermont":52
"New Jersey":44
"Iowa":44
"Minnesota":41
"Oregon":39
"Arkansas":38
"Wisconsin":34
"West Virginia":32
"Nevada":31
"Connecticut":23
"Maine":22
"New Mexico":20
"Idaho":16
"New Hampshire":12
"Nebraska":10
"North Dakota":8
"Utah":8
"Wyoming":8
"South Dakota":7
"Hawaii":2
"Montana":2
"Alaska":1
Time period for user active date wise :-
"South Carolina=2016-4-26":"From 9-48-37 TO 9-52-45"
"Maine=2016-4-24":"From 11-11-35 TO 17-6-14"
"Maine=2016-4-26":"From 9-48-50 TO 9-51-47"
"Kansas=2016-4-26":"From 9-48-28 TO 9-52-39"
"Kansas=2016-4-24":"From 11-4-38 TO 17-6-33"
"Nebraska=2016-4-24":"From 11-11-2 TO 17-5-4"
"Pennsylvania=2016-4-26":"From 9-48-28 TO 9-52-48"
"West Virginia=2016-4-26":"From 9-48-44 TO 9-52-47"
"Colorado=2016-4-24":"From 11-4-37 TO 17-3-56"
"Florida=2016-4-24":"From 11-4-37 TO 17-6-28"
"Nebraska=2016-4-26":"From 9-48-54 TO 9-48-54"
"Connecticut=2016-4-26":"From 9-48-29 TO 9-51-23"
"Colorado=2016-4-26":"From 9-48-29 TO 9-52-45"
"Florida=2016-4-26":"From 9-48-38 TO 9-52-50"
"Connecticut=2016-4-24":"From 12-52-33 TO 17-5-38"
"Pennsylvania=2016-4-24":"From 11-11-5 TO 17-6-3"
"South Carolina=2016-4-24":"From 11-4-40 TO 17-6-26"
"Oklahoma=2016-4-24":"From 11-10-56 TO 17-6-10"
"North Dakota=2016-4-26":"From 9-51-48 TO 9-51-48"
"Oklahoma=2016-4-26":"From 9-48-34 TO 9-52-42"
"North Dakota=2016-4-24":"From 15-55-30 TO 16-54-43"
"Illinois=2016-4-24":"From 11-4-34 TO 17-5-4"
"Texas=2016-4-24":"From 11-4-35 TO 17-6-27"
"Illinois=2016-4-26":"From 9-48-34 TO 9-52-50"
"Oregon=2016-4-26":"From 9-48-55 TO 9-52-41"
"Texas=2016-4-26":"From 9-48-28 TO 9-52-49"
"Oregon=2016-4-24":"From 11-10-56 TO 16-56-59"
"Arizona=2016-4-26":"From 9-48-51 TO 9-52-46"
"Arizona=2016-4-24":"From 11-4-35 TO 17-5-58"
"Virginia=2016-4-26":"From 9-48-32 TO 9-52-47"
"Virginia=2016-4-24":"From 11-4-34 TO 17-6-22"
"Wisconsin=2016-4-24":"From 11-12-9 TO 17-5-3"
"North Carolina=2016-4-26":"From 9-48-28 TO 9-52-50"
"Wisconsin=2016-4-26":"From 9-48-29 TO 9-52-19"
"Tennessee=2016-4-26":"From 9-48-43 TO 9-52-39"
"Tennessee=2016-4-24":"From 11-4-36 TO 17-3-21"
"Louisiana=2016-4-26":"From 9-48-31 TO 9-52-49"
"Utah=2016-4-26":"From 9-48-53 TO 9-52-39"
"Iowa=2016-4-24":"From 11-11-14 TO 17-6-19"
"Iowa=2016-4-26":"From 9-48-40 TO 9-52-42"
"Utah=2016-4-24":"From 11-11-34 TO 16-20-41"
"California=2016-4-26":"From 9-48-31 TO 9-52-49"
"Ohio=2016-4-24":"From 11-4-35 TO 17-6-6"
"Massachusetts=2016-4-24":"From 11-11-7 TO 17-6-16"
"California=2016-4-24":"From 11-4-36 TO 17-6-31"
"Ohio=2016-4-26":"From 9-48-36 TO 9-52-49"
"Wyoming=2016-4-26":"From 9-49-18 TO 9-51-43"
"Massachusetts=2016-4-26":"From 9-48-58 TO 9-52-42"
"Louisiana=2016-4-24":"From 11-11-2 TO 17-6-10"
"New Hampshire=2016-4-24":"From 11-12-32 TO 17-6-3"
"New Hampshire=2016-4-26":"From 9-51-46 TO 9-51-46"
"Hawaii=2016-4-26":"From 9-49-14 TO 9-49-51"
"Wyoming=2016-4-24":"From 12-50-12 TO 16-50-9"
"North Carolina=2016-4-24":"From 11-11-9 TO 17-5-19"
"Washington=2016-4-26":"From 9-48-33 TO 9-52-48"
"Washington=2016-4-24":"From 11-4-35 TO 17-6-27"
"New Jersey=2016-4-24":"From 11-11-15 TO 17-6-10"
"New Jersey=2016-4-26":"From 9-48-39 TO 9-52-42"
"Nevada=2016-4-26":"From 9-48-36 TO 9-52-29"
"Maryland=2016-4-24":"From 11-10-56 TO 17-5-25"
"Michigan=2016-4-24":"From 11-11-15 TO 17-6-23"
"Nevada=2016-4-24":"From 11-10-55 TO 17-4-55"
"Montana=2016-4-26":"From 9-51-35 TO 9-51-35"
"New Mexico=2016-4-24":"From 11-11-42 TO 17-5-32"
"Michigan=2016-4-26":"From 9-48-28 TO 9-52-42"
"New Mexico=2016-4-26":"From 9-48-34 TO 9-52-7"
"South Dakota=2016-4-24":"From 11-11-0 TO 16-27-52"
"South Dakota=2016-4-26":"From 9-51-29 TO 9-52-40"
"Alabama=2016-4-24":"From 11-4-35 TO 17-3-56"
"Vermont=2016-4-24":"From 15-54-2 TO 17-5-31"
"Alabama=2016-4-26":"From 9-48-38 TO 9-52-42"
"Indiana=2016-4-26":"From 9-48-33 TO 9-52-48"
"Idaho=2016-4-24":"From 11-4-40 TO 16-54-56"
"Kentucky=2016-4-24":"From 11-11-0 TO 17-5-47"
"Maryland=2016-4-26":"From 9-48-54 TO 9-52-38"
"Idaho=2016-4-26":"From 9-48-36 TO 9-52-27"
"Kentucky=2016-4-26":"From 9-48-45 TO 9-52-48"
"Alaska=2016-4-26":"From 9-51-15 TO 9-51-15"
"Indiana=2016-4-24":"From 11-10-57 TO 17-6-22"
"Georgia=2016-4-26":"From 9-48-28 TO 9-52-46"
"Georgia=2016-4-24":"From 11-4-37 TO 17-6-23"
"Minnesota=2016-4-24":"From 11-11-4 TO 17-5-0"
"Minnesota=2016-4-26":"From 9-50-3 TO 9-52-21"
"New York=2016-4-26":"From 9-48-28 TO 9-52-44"
"West Virginia=2016-4-24":"From 11-10-58 TO 17-5-59"
"Arkansas=2016-4-26":"From 9-48-42 TO 9-51-57"
"Delaware=2016-4-26":"From 9-48-41 TO 9-52-44"
"New York=2016-4-24":"From 11-4-36 TO 17-6-33"
"Missouri=2016-4-24":"From 11-4-35 TO 17-6-12"
"Arkansas=2016-4-24":"From 11-4-34 TO 17-3-44"
"Missouri=2016-4-26":"From 9-48-33 TO 9-52-38"
"Mississippi=2016-4-24":"From 11-11-8 TO 17-6-22"
"Delaware=2016-4-24":"From 11-11-31 TO 17-6-10"
"Mississippi=2016-4-26":"From 9-48-31 TO 9-52-44"
COMPLETE
```
# Project Team Managment:

We are four members in the group shared the work equally SAI KARTHIK NAPA is doing the testing and API development work and AKHILA KATKAM is working on data analysis and API development, Avinash is also working on data analysis and documentation and  Mallikarjuna provides Data Analysis and testing.


# Project Team and Management

     Team Member                                Roles                                        Contributions
 
   
     Sai karthik Napa (0270)	          testing and APi developmentData     collection for model (state and candidate list)             
  
     Akhila Katkam (0736)	           Data Analysis and API development      Backend part (Data collection)
   
     Manepalli Mallikarjuna (1620)	     Data Analysis and testing          Backend (Data analysis and storing in cassandra )
     
     Avinash Chowdary Koganti (1474)	Data Analysis , documentation        Analized data Sending client side,Data consuming and showing                                                                         on UI 


# DELIVERABLES AND CHECKPOINTS
| Checkpoint Date | Expected Deliverable | Responsible Team Member(s) |
| --------------- | -------------------- | -------------------------- |
| 04-08-2016 | Project Proposal | Team Members |

