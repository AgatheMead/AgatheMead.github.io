---
layout: post
title: PageRank - The Graph Theory-based Search Engine Optimization
---
Discorvering knowledge from the web is one of the basic abilities of the most of us. I use Google a lot while I am drafting this. There are variety search engines and people use them to locate the web pages relevant to user queries. However, with the massive volume of information of every variety, and not being organized in any meaningful way, it is not that easy to sort through what we need. 
Wrap up of our first course:
  - ** PageRank ** for discovering the most important pages on the web
  - ** Hubs and Authorities ** a more detailed evaluation of the importance of web pages
  - ** Random Walks ** is the basic definition of PageRank

## A bit of the history
### Search engine optimization (SEO)
Search engines generally have the functions to:
* Locate all web pages.
* Index the data for efficient information retrieval.
* Rate the importance of each page and rank the most important pages on top.

The search engine simply takes input keywords and returns search engine results pages (SERP), with a list of pages ranked by the relativeness of searched keywords. The better optimized your web page is, the more highly ranked it will be in search engine results, and thus your web page will get more traffic from visitors. 
**Search Engine Optimization (SEO)** is the method used to rise the visibility of a web page in the results of a search engine. Good SEO can help drive more relevant traffic to your sites. It was believed that SEO was born in 1991. At that time, the first search engine named _Archie_ gathered information from FTP sites to create lists of index of downloadable files. However, due to limited computational resource, the informational contents for each site could not be used to index pages. By 1994, _Yahoo!Search_ began as a collection of web pages included hand-crafted description with each URL, eventually developing to a searchable index directory. However, engineers still relied on text-based and human-maintained methods to rank relevance retrieval which were expensive to build and slow to improve, even worse, some low-quality web pages attempt to gain higher ranks by using tricks to mislead search engines. More effective web search engines are needed to satifsy the information-needs.

>>Main challenges
>>
>>* Massive volume of dynamic and unorganized data to handle with.
>>* No classification of web pages.
>>* Reduplicated or related contents.

### Hyperlinks structure information: improve the quality of web search engines
More than 20 years ago, two Standford computer science candidates, named Sergey Brin and Larry Page, created one of the most visited sites as part of a rsearch project. These two guys were the Google co-founders, and nicknamed as the "Google boys". They picked the name _Google_ because googol (10e100) is a very large number which well represented their goal of building very large-scale search engines. The power that initiated Google's (Its beginning was called _BackRub_ and eventually became Google as a domain in 1997) meteoric was the Google Search Engine based on **PageRank**. SEO has rapidly evolved since then.
A hyperlink consists of two simple parts: 
* Uniform Resource Locator (URL): address of the web page and is hidden under the hypertext
* Anchor text: is visible to users in the browser window, can be text, graphics, etc.
Linking Page URL | Achor Text
---------------- | -----------
Hyperlink        | Hypertext
`<a href="http://YOUR_WEB_PAGE_ADDRESS"> | YOUR_WEB_PAGE_ANCHOR_TEXT</a>`
Brin and Page realized that the hyperlink graph of the web is an important resource and has gone unused in existing dominated web search engines. The idea was inspired by the "citation factor" of published papers. That is, by looking at the citation number that other papers referencing them. 
Format: ![High Level Google Architecture from Brin and Larry's paper](https://www.researchgate.net/profile/Nureni_Azeez/publication/255644944/figure/fig1/AS:285567700615168@1445096053801/High-Level-Google-Architecture.png)
You can infer from this figure that PageRank was not the sole factor for sorting the search results, it works with other text-matching techniques for search queries. The ranks score is computed at indexing time and not at query time. So we say PagaRank a query-independent algorithm.
Long story short, Google accounts for three factors in its PageRank algorithm, which are:
* The quantity and quality of inbound linking pages.
* The number of outbound links on each linking page.
* The PageRank of each linking page.

The algorithm ranks pages from 0-10. Normally it was believed that a Google PageRank of 5 is enough for your site to show on the first page of search results. 

### Google Retired the PageRank Toolbar
Format: ![Google Toolbar PageRank](https://cdn.cognitiveseo.com/blog/wp-content/uploads/2018/05/Google-toolbar-pagerank.jpg)
Things went well in the beginning, everyone can check PageRank for their website and compare their website to others. The rules of PageRank were loose. In theory, as long as people know the ranking mechanism, they will continue to be manipulated, which eventually leading to link spam. Toolbar PagaRank score has long been seemed as the most useful factor of SEOs because it was the only visible gauge for users.

PageRank was officially axed from Google Toolbar in 2016 after the launch of Chrome. This move was basically due to the the buying and selling of ‘high PageRank links’ which eventually damage the ‘true’ PageRank of a webpage. As the Internet and our understanding of the Internet have grown in complexity, people should stop considering Toolbar PageRank score as a single isolated metric. Matt Cutts gave an answer in 2013 to the question 'Why don't you turn off the PageRank feature in the Google Toolbar?', saying that they wanted to stop spammers that used PageRank as a way to spread misleading information. 

### Why it still matters in 2020
PageRank is still in use internally as a part of Google's ranking algorithm but invisible to the customers. More than that, Google updated the new patent regarding to the PageRank. If you are intersted in PagaRank update, here is a post written by Bill Slawski, Google Patent guru. 

No replica of PageRank exists as a suitable replacement for the public PageRank score. Period. But there are a few similar metrics around. Ahrefs' URL Rating (UR) is one of the decent alternative (you can check this out if you are interested). 

## Understanding graph theory
We mentioned above that the PageRank is a graph theory-based optimization algorithm. 
In mathematics, graph theory is used to model the relations between pair-wise objects. We define that 
* A graph is made up of vertices and edges. 
* A graph may be undirected, meaning that there is no distinction between two vectices associated with each edge, or its edges may be directed from one vertex to another vertex.

Format: ![Figure from Graph Theory concepts for Layman - AnKur's Blog](https://datafreakankur.com/wp-content/uploads/2018/12/image-37.png)
Format: ![Figure from Graph Theory concepts for Layman - AnKur's Blog](https://datafreakankur.com/wp-content/uploads/2018/12/image-39.png)

### Understanding how PageRank is relative to graph theory
For web users, a search engine serves as the user interface that accepts queries and returns the search results. So how PageRank algorithm is relative to graph? Graph theory can model how information spreads within a graph, and this is insteresting for information retrieval systems.
In a directed graph, there are two types of 'importance': authority (pointed to by incoming vertices) and hub (with outgoing vertices), similar to 'fans' and 'centers', which are metrics to measure the node influence. 
Format: ![An authoritive web page is pointed to by many hub pages.](https://sentinelvisualizer.com/SocialNetworkAnalysis/SocialNetworkAnalysis_HubAuthority.gif)

> **_NOTE:_** Definition of importance in PageRank: A page is importance if important pages link to it.

For the PageRank algorithm, the graph is made of all of the WWW pages as nodes and hyperlinks on the pages as edges. Hyperlinks are used to show the popularity of a web page, if we compare two websites with the same numbers of edges, PageRank will give the site with more links to credible sources a better rank. Thus, if websites linking to your webpage have a ranking factor of 0, then those links will not help to boost your PageRank. Also, the more edges on the pages tend to have better ranks. High quality sites receive a higher PageRank. However, important pages mean nothing to you if they don’t match your query.
Finally, when searching for a query, the search engine will parse the strings and retrivel the websites containing the matched strings and those sites will be ranked by PageRank. 

You might be wondering how to drive the initial PageRank of each web page. Since there are millions of pages, how does Google overcome this problem? From the original PageRank paper we came across this:
>> PageRank can be calculated using a simple iterative algorithm and corresponds to the principal eigenvector of the normalized link matrix of the web. By the time of Brin and Page's publication, a PageRank for million-level web pages can be computed in a few hours on one workstation. 

Nailed it. It means that Google PageRank calculates the ranking of a page without knowing the absolute ranking of the linking pages. PageRank was designed as a relative measure of a webpage quality compared to every to every other page on the link-graph. 

For interative graph-based algorithms like PageRank, the complexity is all about the number of paths and iterations. In every iteration we do matrix multiplication in O(n^2) time with n being the number of graph nodes until we reach the stationary status. If we see the whole graph as a very large matrix, we will find this matrix is rather sparse with on average k (k << n) non-zero entries on every row, the calculation can instead be done in O(kn) time. The In practice the amount of backlinks in a web page does not change with the grow of the total webs pages on the web, this means we essentially have a linear time algorithm O(n). Accounting for the iterations, the final PageRank complexity thus becomes O(log(n)).

## Takeaways
- The Google Search Engine uses PageRank as a way of measuring the importance of website.
- No alternative for PageRank by so far.
- PageRank computes rank score on indexing time and not at query time.

## Externel links
[1] https://www.google.com/intl/en_uk/search/howsearchworks/algorithms/ 

[2] https://backlinko.com/google-ranking-factors 

[3] https://www.coursera.org/lecture/networks-illustrated/pagerank-example-summary-K3NRM 

[4] https://www.coursera.org/lecture/python-data-visualization/page-rank-overview-Yz0EK 

[5] https://www.coursera.org/learn/linear-algebra-machine-learning 

[6] https://www.wordstream.com/articles/internet-search-engines-history 

[7] http://ilpubs.stanford.edu:8090/361/1/1998-8.pdf

[8] https://www.seobythesea.com/2018/04/pagerank-updated/ 

----
****