# SIEM Lab
## Objective
I was tasked to be a security analyst working for an e-commerce store that is is supposed to identify possible security issues with the mail server. To do so I had to take the data given and sort through it to find fialed SSH logins for the root account occuring and report suspicious findings. I used Splunk Cloud to upload a zip file of data, performed a series of searches to analyze key patterns, and documented a report summarizing my findings.

### Skills Learned

- Understanding of SIEM concepts and practical application.
- Proficiency in analyzing and interpreting network logs patterns.
- Ability to query through a repository for data based on hosts, IP addresses, and root logins
- Efficiency in locating failed SSH logins for the root acount on a network host


### Tools Used

- Security Information and Event Management (SIEM) platform Splunk Cloud for log ingestion, search, and analysis.
  
## Steps

1.Upload data into Splunk through Settings and Add Data icon to drop the zip file in and set Host selection to Segment in Path:1

2.Went to Search and Reporting section where I queried the events in the index called main with index="main" and set time range to All Time to pull up all of the results.

3.Specified the host field of mailsv to examine events only through the companies mail server and named two keywords first fail* with that wildcard * to find similar words like failure and failed, and second being root for any events containing root to make the final query  index="main" host=mailsv fail* root. Found a list of events with only a few out of the normal.

4.Lastly I had to find any suspicious patterns of repeat sources attempting to log in while still failing. I found one IP addresses attempting to log in at the same time obscure at 1:39am on two seperate occasions. I narrowed the search and added the IP address to the query making it   index="main" host=mailsv fail* root "109.169.32.135"   and found 4 similar events of failed SSH logins for the root account at the same time 1:39am which is out of business hours. I reported my findings and recommended for that IP addresses to be blocked.  

## Screenshots

*Ref 1: Network Diagram*
