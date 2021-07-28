# text-summarization
This is a artificial intelligence based project that produces the summary of the
given text.

## Authors
* Akhilesh Kumar Verma
* Akhil
## Introduction
The text Summarizer it is meant for a software that extracts various moods of
the extract and provide a consise and complete idea of the extract without going
through whole text.

Summarization is mainly useful because it condenses information for easier
consumption and analysis.

We have provided two methods to the user for generating summary. They can either
browse and open a file whose summary they want to see or they can directly write
into the text box and generate summary of the article they have written in the
section provided. The program provides a graphical user interface.

## Theory
In general, there are two types of summarization:
1. Extractive summary
2. Abstractive summary
### Abstractive summary
Abstractive methods select words based on semantic understanding, even those words
did not appear in the source documents. It aims at producing important material in
a new way. They interpret and examine the text using advanced natural language
techniques in order to generate a new shorter text that conveys the most critical
information from the original text.

It can be correlated to the way human reads a text article or blog post and then
summarizes in their own word.

Block diagram of this type of summarization is given below:

    input document ⟹ understanding contents ⟹ semantics ⟹ create own summary
### Extractive summary
Extractive methods attempt to summarize articles by selecting a subset of words
that retain the most important points.

This approach weights the important part of sentences and uses the same to form the
summary. Different algorithm and techniques are used to define weights for the sentences
and further rank them based on importance and similarity among each other.

Block diagram of this type of summarization is given below:

    Input document ⟹ determine similarity among the sentances ⟹ assign weight to sentances ⟹ select sentances with higher rank

### Abstractive vs Extractive Summarization
Purely extractive summaries often times give better results compared to automatic
abstractive summaries. This is because of the fact that abstractive summarization methods
cope with problems such as semantic representation, inference and natural language
generation which is relatively harder than data-driven approaches such as sentence extraction.

Further, we need not to train some model for extractive summarization because we can devise
an algorithm for extractive summarization so no need to have a lot of data set. Nor our summary
then relies on the data and is free from biases that arise due to limited data.

## Methodology
### Sentence similarity
We are using cosine similarity[1] to find similarity between two sentences. One of choice apart
from it is O. Jaccard similarity.[2]
### Cosine similarity
Cosine Similarity is a measurement that quantifies the similarity between two or more vectors.
The cosine similarity is the cosine of the angle between vectors. The vectors are typically
non-zero and are within an inner product space.
Cosine Similarity is a value that is bound by a constrained range of 0 and 1. The similarity
measurement is a measure of the cosine of the angle between the two non-zero vectors A and B.
Suppose the angle between the two vectors was 90 degrees. In that case, the cosine similarity
will have a value of 0; this means that the two vectors are orthogonal or perpendicular to each
other. As the cosine similarity measurement gets closer to 1, then the angle between the two
vectors A and B is smaller.
Quantification of the similarity between two sentences can be obtained by converting the
sentences or phrases within the article into a vectorized form of representation. The
vector representations of the sentences can then be used within the cosine similarity
formula to obtain a quantification of similarity.
#### Stopwords
We have used ‘stopwords’ to prevent the articles and the modals and helping verbs to
influence the vector of the document or the sentence in our case.
Stopwords: Stopwords are the English words which does not add much meaning to a sentence.
They can safely be ignored without sacrificing the meaning of the sentence. For example,
the words like the, he, have, etc.
### Sentence ranking
We are using PageRank[3][4] algorithm for ranking the sentences based on the similarity
of sentences.
### PageRank Algorithm
PageRank (PR) is an algorithm used by Google Search to rank web pages in their search
engine results. PageRank was named after Larry Page, one of the founders of Google.
PageRank is a way of measuring the importance of website pages. According to Google:
> PageRank works by counting the number and quality of links to a page to determine
a rough estimate of how important the website is. The underlying assumption is
that more important websites are likely to receive more links from other websites.

Currently, PageRank is not the only algorithm used by Google to order search
results, but it is the first algorithm that was used by the company, and it
is the best known. As of September 24, 2019, PageRank and all associated
patents are expired.
The PageRank algorithm outputs a probability distribution used to represent
the likelihood that a person randomly clicking on links will arrive at any
particular page. PageRank can be calculated for collections of documents of
any size. It is assumed in several research papers that the distribution is
evenly divided among all documents in the collection at the beginning of the
computational process. The PageRank computations require several passes,
called "iterations", through the collection to adjust approximate PageRank
values to more closely reflect the theoretical true value.

## Innovative work
We have created a method of ranking that will increases the chances of inclusion of all types of
sentences in the summary.

We apply page rank algorithm to rank the sentences then remove the top ranked sentence, after adding
its index to ranking list, from the adjacency matrix, then again apply page rank algorithm to rank the
leftover sentences and add the top ranked sentence’s index in ranking list and then remove the top
ranked sentence. We have repeated this process till the adjacency list stores only one sentence.

This method ensures that the summary contains crux points from each section of the article, and gives
the reader a summary that covers all the aspect of the article. It does so by preventing the similar
sentences from influencing the summary.

## References
[1] 	C. S. Perone, “Machine Learning :: Cosine Similarity for vector space Models (Part III) | Terra Ingcognita,” Terra Incognita, 12 September 2013. [Online]. Available: https://blog.christianperone.com/2013/09/machine-learning-cosine-similarity-for-vector-space-models-part-iii/. [Accessed 20 October 2020].

[2] 	A. Sieg, “Text similarities: Estimate the degree of similarity between two texts | by Adrien Sieg | Medium,” Medium, 5 July 2018. [Online]. Available: https://medium.com/@adriensieg/text-similarities-da019229c894. [Accessed 13 October 2020].

[3] 	“PageRank - Wikipedia,” Wikipedia: The Free Encyclopedia, 23 September 2020. [Online]. Available: https://en.wikipedia.org/wiki/PageRank#:~:text=%20Algorithm%20%201%20Simplified%20algorithm.%20Assume%20a,Apache%20Spark%20RDDs%20to%20iteratively%20compute...%20More%20. [Accessed 15 October 2020].

[4] 	American Methamatical Society: Advancing Research. Creating connections, December 2006. [Online]. Available: http://www.ams.org/publicoutreach/feature-column/fcarc-pagerank. [Accessed 21 October 2020].

[5] 	“python constructors - javatpoint,” javaTpoint, [Online]. Available: https://www.javatpoint.com/python-constructors#:~:text=Note%3A%20The%20constructor%20overloading%20is%20not%20allowed%20in,value%20to%20the%20specific%20attribute%20of%20an%20object.. [Accessed 2020].

[6] 	“20 Applications of Automatic Summarization in Enterprise | The Frase Blog,” frase, 2020. [Online]. Available: https://blog.frase.io/20-applications-of-automatic-summarization-in-the-enterprise/#Summarization_the_basics. [Accessed 21 November 2020].
