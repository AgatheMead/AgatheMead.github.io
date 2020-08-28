---
layout: post
title: PageRank - The Revolution of Graph Analysis in Web Search Engine
---
Discorvering knowledge from the web is one of the basic abilities of the most of us. I use Google a lot while I am drafting this. There are variety search engines and people use them to locate the web pages relevant to user queries. However, with the massive volume of information of every variety, and not being organized in any meaningful way, it is not that easy to sort through what we need. At the time of 1990, the first search engine named _Archie_ gathered information from FTP sites to create lists of index of downloadable files. However, due to limited computational resource, the informational contents for each site could not be used to index pages. By 1994, _Yahoo!Search_ began as a collection of web pages included hand-crafted description with each URL, eventually developing to a searchable index directory. However, engineers still relied on text-based and human-complied methods to rank relevance retrieval. More effective web search engines are needed to satifsy the information-needs.
There are two approaches of web search that we are looking into:
  - ** PageRank ** for discovering the most important pages on the web
  - ** Hubs and Authorities ** a more detailed evaluation of the importance of web pages

> **_NOTE:_** Definition of importance in Page Rank: A page is importance if important pages link to it.

## A bit of the history
### Search engine optimization
The search engine simply takes input keywords and returns the ranked results. 
Search Engine Optimization (SEO) is the method 

### Hyperlinks structure information: improve the quality of web search engines
More than 20 years ago, two Standford computer science candidates, named Sergey Brin and Larry Page, created one of the most visited sites as part of a rsearch project. These two guys were the Google co-founders, and nicknamed as the "Google boys". They realized that the authority of web pages The power that initiated Google's (Its beginning was called _BackRub_) meteoric was the Google Search Engine based on **PageRank**. 
Google also introduced **Authority**, or trustworthiness, to 

### Google Retired the PageRank Toolbar
Things went well 

Toolbar PageRank was officially removed in 2016, this move was due to the the buying and selling of ‘high PageRank links’ which eventually damage the ‘true’ PageRank of a webpage. As long as people know the ranking mechanism, they will continue to be manipulated. The PageRank algorithm is still in use but invisible to the customers.

### Main challenge

* Massive volume of dynamic data to be handled with. Unlike information in the database, 
* No classification of web pages.
* Reduplicated or related contents.

### Why it still matters in 2020
PageRank is still in use in Google's backend after they've removed the toolbar. 
No replica of PageRank exists. Period. 

## Understanding how PageRank works
For web users, a search engine serves as the user interface that accepts queries and returns the search results. So what is actually happending inside a search engine?

Well, graph. 
In mathematics, graph theory is used to model the relations between pair-wise objects. 

PageRank is a graph theory-based optimization algorithm. The graph is made of all of the WWW pages as nodes and hyperlinks on the pages as edges. Hyperlinks are used to show the popularity of a web page, if we compare two websites with the same numbers of edges, PageRank will give the site with more links to credible sources a better rank. Also, the more edges on the pages tned to have better ranks. Finally, when searching for a query, the search engine will parse the strings and retrivel the websites containing the matched strings. Then, the those sites will be ranked by the PageRank algorithms. 


It is true that the accuracy of PageRank can be attributed to the weights and categorization of the edges. Thus, in theory, if websites linking to your webpage have a ranking factor of 0, then those links will not help to boost your PageRank. 


### PageRank as Votes
High quality sites receive a higher PageRank. Of course, important pages mean nothing to you if they don’t match your query. Google search engine interprets a link from A to B as a vote, and B has this vote casted by A. Besides, the importance of A is counted 




## Takeaways
- The Google Search Engine is based on **PageRank**.
- 

## Toy examples 

## Externel links

[1] https://www.semrush.com/blog/pagerank/ 
[2] https://ahrefs.com/blog/google-pagerank/ 
[3] Graph Analysis and its application: https://zhuanlan.zhihu.com/p/28298952 
[4] https://searchengineland.com/what-is-google-pagerank-a-guide-for-searchers-webmasters-11068 
[5] https://www.google.com/intl/en_uk/search/howsearchworks/algorithms/ 
[6] https://backlinko.com/google-ranking-factors 
[7] https://www.coursera.org/lecture/networks-illustrated/pagerank-example-summary-K3NRM 
[8] https://www.coursera.org/lecture/python-data-visualization/page-rank-overview-Yz0EK 
[9] https://www.coursera.org/learn/linear-algebra-machine-learning 
[10] https://www.wordstream.com/articles/internet-search-engines-history 


- _italics_
- **bold**
- `code()`

> Blockquote
>> Nested Blockquote
![graph] (/images/graph.png)
Format: ![Alt Text](url)
----
****