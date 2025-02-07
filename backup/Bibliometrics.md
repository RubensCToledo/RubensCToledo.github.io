# Bibliometric Analysis

The bibliometric analysis is a meta-analysis, that by definition, tries to find conclusion from analysing data. In my case I was trying to see the metrics of the field of research of my PhD. There are other software available like VOSviewer that have a ready solution for this type of analysis, but I wish to conduct some analysis that weren't implemented and decided to develop a code with my wife and a friend, you can check [here](https://rubensctoledo.github.io/Codes_examples/Bib_git.ipynb) (I'm aware that part of the code is breaking due to changes in libraries, I might revisit it on future but for now I have no plans to update it) or the papers that used this code (or the variation one my wife used) [here](https://www.mdpi.com/1996-1073/16/9/3623) and [here](https://journals.sagepub.com/doi/abs/10.1177/14644207241240048).

I wish to say that this code was meant to be a work in progress, which was thought to be an open software to use. However people around me by the time didn't shared the same instusiam on the results and for this reason I stopped after the first version, which didnt come close to a V1.0.

I believe this analysis is very useful for a begining of any research as it gives you a broad overview of your research field. IN this analysis is possible to indetify the revelant people and works, highlights the promissing journal used by your peers for your future paper and visualize the topic size and growth.

## Pre data treatment

In this situation I wished to review a certain topic and I wanted to get all or most of the work that was relevant to my research.  I've put togheter two of the largest database on academia: Scopus and Web of Science. The problem with those Databases are the difficulty of filtering the relavant paper from the batch. Both Databases work with keyword combination that might match with specific areas of a paper. However people are not consistent where to put the information, which if you restric you search you lose information or if you are too broad, you get a lot of information that is not matched with the search. 

The pipeline of data treatment follows:
1 - Comparioson of both database and remove equals;
2 - Manual scan of the remaining batch to ensure relevancy;
3 - Extract of key information relevant to the analysis (Material information, experimental setup and condition, key finds, year, country, names, citation number recieved, citation made and journal);
4 - Treament of language differences, spelling, missing information and such;
5 - Results.

## Analysis

### Publications and Citations by Country
The analysis that I wished to make are number of publication per country and their citation:
![country_cita](https://github.com/user-attachments/assets/3ce0a25d-1c03-472f-b299-55bb5f385cf5)
For this analysis every paper attributed a single unit of publication for every country in the author's name. THe same thing was made with the cumulative citation number, if two author of the same country were present in a peper, only a single unit of paper number and citation number was used.
The main difficulty here was to extract the information of country name due to the inconsistency of some journal, missing information and differences between databases. Also, different spelling of countries and abreviations had do be dealt with.

This analysis was tought to help identify which countries produce more paper (which somewhat translate to how much investment in the fild they have) and how relevant are the paper produced (number of citation).

### Cumulative Documents and Citations by Year

Next analysis was cumulative number of documents and citation per year:
![doc-cita_year](https://github.com/user-attachments/assets/28da4c83-528d-4394-963a-1732da602020)
Chalanges here are about the same of the other analysis and went way smoother. This analysis sought to identify which year have the most relevant work to help to understand the context of the fild and also to identify technology defining discovery (if you have few paper in a year and lots of citation, higher chance of having a pretty important paper there).

To highlight the importance of the manual filtering, here is a comparision of same analysis with and without the manual analysis for relevance. You can see how misleading the analysis become without it:
With manual filtering | Without manual filtering|
----------------------|-------------------------|

![doc-cita_year](https://github.com/user-attachments/assets/28da4c83-528d-4394-963a-1732da602020)|![doc-cita_year_comparison](https://github.com/user-attachments/assets/97b23663-fe30-4bde-8996-d0654dba63af)|

### Author Analysis
The next analysis was meant to be a extrapolation of the previous analysis:
![primeiro](https://github.com/user-attachments/assets/f53c1d07-7acb-4087-a099-9ed8090e8dae)
This analysis consisted of atribuying citation of every paper to each author and ranking them. After that the first five first author with the higher number of citation were ranked and the the previous analysis was conducted for each one of them as observed on the above figure. The ideia was to identify their most relevant work. The code also feature the same analysis not taking account the first author and for the last author as well.

### Journal Analysis
This analysis was different analysis of the author, only this time instead of the author I looked to the journal.
![journal-cita](https://github.com/user-attachments/assets/4388ef7c-1523-4a0b-a21a-5eb966161f99)
My goal was to identify what journal have the highest ration of citation/publication. This result should be used as reference to where to send you paper. As a researcher you would like to have a good exposition of your work and chosing the right journal might help people to get to know your work. Eventhoguh there a lot more to it, this is indead an value guide that you could use to weight your decision.

### keyword analysis
Which leads us to the next analysis which is which keyword used inside of the paper that have the higher number of citation.
![kw](https://github.com/user-attachments/assets/5b7d9ae8-5b1b-45c1-a8d4-02ac5904feab)
Instead of journal or author, the citation of each paper were attributed to every keyword inside the paper. Those keyword for all the database were them ranked and the result is the image above. Still on the topic of visivility, I have found that the best way to identify a work in those databases is using keyword or in title, abstract or keyword field. Eventhough this analysis is limited to the keyword field, it also server as a termometer to see which keyword your peers are using which you might want use if you want more visibility.
English is the main language of academia, but the majority of the researcher are not native to the English language. This might leads to different word being used. Also, a commom thing that I have noticed is the use of acronym which you might have to pay attention.

### co-citation web

The last (and coolest) analysis is the co-citation web, where you can verify the relation of which author is working with author.
![bang](https://github.com/user-attachments/assets/8d2b6946-2f98-482a-a40a-f3400fe62a94)
The final and most visually striking analysis is the co-citation web, which maps relationships between authors. Unfortunately, I can’t explain this in detail, as my wife developed this analysis independently.


[back](https://rubensctoledo.github.io)
