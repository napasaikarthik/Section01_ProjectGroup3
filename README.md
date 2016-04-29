# Section01_ProjectGroup3
# Data Mining

# TWITTER ANALYSIS

# OVERVIEW

Twitter is one of the popular social network where people post their views on everything from their personal problems to social issues. They also discuss about all the topics in the world. 7168 tweets are produced every second. All the predictions on sports, politics and all the data for analysis on social issues are taken form twitter posts. By using this data, we can represent what people are thinking.

# DATASETS:

+ Finding data using twitter is very simple because each topic is mentioned using a hashtag. Every hash tag helps the users to follow them and retweet accordingly. In our project we are going to use hash tags to track down the user post on the topic.
The data we collect from twitter is not structured. So we try to retrieve only location, timestamp, message, and hashtag used. We can use different tools to represent the data some of the potential tools I have explored are Splunk and microstrategy. These tools are even used in bigdata applications
We collect all this data using the twitter API, which help us to retrieve the data using the python code.

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

