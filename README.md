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


# CODE AND APPLICATION
+ Code is posted in the GitHub link.

# Project Team Managment:

We are four members in the group shared the work equally SAI KARTHIK NAPA is doing the testing and API development work and AKHILA KATKAM is working on data analysis and API development, Avinash is also working on data analysis and documentation and  Mallikarjuna provides Data Analysis and testing.


# Project Team and Management

     Team Member                        Roles & Contributions
 
   
     Sai karthik Napa (0270)	          testing and APi development             
  
     Akhila Katkam (0736)	          Data Analysis and API development
   
     Manepalli Mallikarjuna (1620)	     Data Analysis and testing
     
     Avinash Chowdary Koganti (1474)	Data Analysis , documentation


# DELIVERABLES AND CHECKPOINTS
| Checkpoint Date | Expected Deliverable | Responsible Team Member(s) |
| --------------- | -------------------- | -------------------------- |
| 04-08-2016 | Project Proposal | Team Members |

