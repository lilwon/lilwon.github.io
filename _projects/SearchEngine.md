---
layout: single
title: Building a Search Engine
toc: true
toc_sticky: true
excerpt: Building a search engine from scratch
author_profile: true
---

The repo for this project can be found [here](https://github.com/lilwon/ICS-Search-Engine).

Learning and building all the features behind a search engine was very fun. 
I took a class in my undergrad about information retrieval 
in Winter 2021 and it changed the way I think about what happens when you type in 
a query on Google. You have to tokenize all of the words that a user types.. 
Then stem those words.. Then match those words to other websites... Man that's 
a lot of work..

We've become so reliant on search engines that it's scary how much information a 
search query can learn about us, which is why Google is such a successful 
search engine. 

I will be breaking down how me and my group developed our search engine. 

## Building an Inverted Index

The first requirement that my group and I had to tackle was creating an inverted 
index for more than 50,000 web-pages/documents. An inverted index is a common 
tool that search engines use to map how many or how frequent terms are in a file. 
More 
information can be found [here](https://en.wikipedia.org/wiki/Inverted_index). 
 
We used the Python library 
[Beautiful Soup 4](https://beautiful-soup-4.readthedocs.io/en/latest/) to pull
information out of HTML files that we were given. So for every document we were 
given, we had to tokenize all the words on that page and put it into a map 
to create our inverted index. 

We were required to split our inverted index into multiple files because 
we had to take into account terabytes of data (like Google). 

After we finished parsing all of the documents, we would have to merge all the
inverted index files together. Once we were able to merge all the files together,
we would than find the [tf-idf](https://en.wikipedia.org/wiki/Tf%E2%80%93idf)
score of each term and build another inverted index based on the tf-idf scores. 

### Building an Index of an Inverted Index 

To make our search engine fast (return results in less than 500ms), we had to
create an index of our inverted index.

We first had to create an external text file that would
hold all the positions of where a term is located in our tf-idf inverted index 
file. This is where the "magic" happens to get fast results from Google or any 
search engine.

From there, we would have open a file reader that would constantly read 
any information to get the line where the term is. The file reader would stay
open until the search engine is closed/finished being used. 

## Building the Search Component

After we created the inverted index, it was time to build the search and retrieval
component. This part wasn't too bad since we only need to get user input, 
tokenize, parse, then stem it and put it into an array. The search component
helped rank the tf-idf scores for a website. The higher the tf-idf score for a
term, the more likely a website or link would be placed on the top of the results.


## The Finale and Future Improvements

We ended up building a simple website with Flask to let users type in a search
query. Most of the queries that a user typed would return results in less than
500ms.

What I will probably do in the future would be to add more features to
creating the inverted index score. For example, calculating the positions where
each term is on a document. Possibily doing a cosine scoring instead of
calculating tf-idf method. 
Implementing Google's [PageRank](https://en.wikipedia.org/wiki/PageRank) to
rank the importance of a website. There's a lot of ways to improve our
search engine! 

I really enjoyed building this project. I was very interested in learning how
Google's search engine was developed and how successful it is. There's so
much information that goes into building a search system. 




