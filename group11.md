---
layout: page
title: Group 11
nav_order: 16
description:
---

# Case citation graph and importance measures


In 1993, Beverly B. Cook published a paper on Measuring the Significance of U.S. Supreme Court Decisions. By analyzing 20 casebooks, term lists, and monographs, she categorized cases of the Burger Court into 5 categories: landmark, major, noteworthy, important, and not significant. Since then numerous political scientists, e.g. (Saul Brenner, Measuring the Importance of Supreme Court Decisions, 1998) and (Clark et. al., Measuring the Political Salience of Supreme Court Cases, 2015), have proposed different ways of quantifying the importance of Supreme Court cases.

We decided take the approach of Fowler et. al. (Network Analysis and the Law: Measuring the Legal Importance of Precedents at the U.S. Supreme Court, 2007) by modeling importance using network analysis, namely centrality measures, on the citation graph of court cases. Our distinguishing factor for a measure of importance is the use of the PageRank algorithm to model the behavior of a lawyer sifting through cases in the citation graph. Furthermore, we propose a method for predicting the importance measure based on the content of the opinions of the cases.

We chose this focus because of its potential to improve the efficiency of both lawyers and judges. Lawyers may present their case through following a similar train of logic as cited cases, appealing to the judge who considers precedence in the legal system when making a final decision. In the courtroom, both the defense and prosecuting attorney build a case based on logic and facts but dependent on the precedence of the legal system. Many cases are won through citation of the results of previous cases; cases that are cited more frequently build rapport over time. Additionally, the importance scores can be aggregated for each judge to measure the importance of his or her verdicts. The data is important for lawyers to target their efforts towards more principle cases, and for lawmakers to look at what impacts their legislation. Other analyses can be conducted on the citation graph that we will build like a community analysis where clusters of cases like “sexual assault” or “IP law” are found.

The data set we use is a set of approximately 183,000 cases from Illinois made accessible by the Caselaw Access Project (CAP) by Harvard Law School Library Innovation Lab. Each case consists of data about the decision date, name, court, attorneys, etc., but pertinent to this project, the cases have zero or more opinions from which we can extract the citation graph.  Looking at the graph below, the  vast majority of cases, luckily for us, have at least one opinion, and some have multiple. This is because they, in addition to the majority opinion, can have dissenting and concurring opinions.

![Distribution of number of opinions](./images/number_opinions.png)

Besides using citations as a proxy for the importance of a case, age is also an a significant factor as older cases have had the time to accumulate citations. Therefore, we also need to understand the number of cases by age in this data set.

![Number of cases by year](./images/cases_by_year.png)

## Quality of keys
To build the citation graph, it is crucial that citation keys are of the highest quality, i.e. we have access to keys for each case, and cases use said keys for citations.
If we first look at the keys given by CAP, we see a few discrepancies, namely that some keys wrongly contain parts of the opinions. If we filter by keys where the first character is a letter, the results are as follows:

| Keys      |
|-------------------|
| GOLDBERG and O’CONNOR, JJ., concur. |
| This claim for property damages and personal injuries is brought against Southern Illinois University, Edwardsville, as a result of a collision between the Claimant’s vehicle and one of the university’s cargo vans.         |
| delivered the opinion of the court: |
| JUSTICE HOPE |
| braint |
| Mr. Justice Hebel |
| delivered the opinion of the court: |
| This is a claim for the return of an automobile or its reasonable value which was allegedly seized illegally from Claimant on December 12, 1978. A hearing was held before a commissioner of the Court on October 21, 1981, wherein the evidence was taken. On March 23, |
| Mr. Justice Wilson |
| delivered the opinion |
| Judgment reversed |
| delivered the opinion of the court. |
| Justice Wolfe |
| Gen. No. 8,835 |

Considering the sheer size of this data set, this is not too bad, but naturally, we cannot use these to establish a citation, so these keys are excluded from the analysis.

Next is the question of whether cases are cited appropriately, which is a very interesting issue.
To answer this, we build a regex with fuzzy string matching where we allow up to 5 edits in the reporter name of the citation key. The reason for not allowing edits in the volume and page is evident as it would match far too many other cases, and thus result in false positives. Doing this for 5 cases, we see the following:

| Key | Match | Count |
|-------------------|
| 176 Ill. 2d 160 | 176 Ill. 156, 160 | 1 |
|  | 176 Ill. 160 | 15 |
|  | 176 App. 160 | 4 |
| 176 Ill. 2d 217  | 176 Ill. 2d 217 | 45 |
|  | 176 S. W. 217 | 1 |
| 176 Ill. 2d 261  | 176 Ill. 2d 217, 261 | 2 |
|  | 176 Ill. 2d 261 | 22 |
| 176 Ill. 2d 401  | 176 111. 2d 401 | 1 |
|  | 176 Ill. 2d 401 | 31 |
| 176 Ill. 2d 414 | 176 F.2d 414 | 1 |
|  | 176 Ill. 2d 401, 414 | 2 |
|  | 176 Ill. 2d 414 | 25 |
|  | 176 Ill. 2d at 414 | 1 |

It is evident that we have false positives but it is clear that cases are not always cited by the right key. However, the majority are cited correctly.

## Building the citation graph
The next step is to build the citation graph from the list of court cases. The idea for doing so is as follows:
  1. Construct a dictionary of case citation to id
  2. Regex escape all case citations and join using a `|` to build a single regex
  3. For each case in corpus:
  4. &emsp;For each opinion in case:
  5. &emsp;&emsp;Find all matches of regex and add to list of citations for this case
  6. &emsp;&emsp;Convert citations to case id using dictionary from step 1

Using the resulting graph, we can analyze the number of case citations each case contains:

![Distribution of number of cases cited](./images/cites.png)

and the number of cases citing each case:

![Distribution of number of citations](./images/cited_by.png)

## Importance analysis
To analyze the importance, we need to establish a common frame of reference for what is important and which assumptions this entails.

The first key observation is that cases can establish new practice of the law and newer cases have precendence over older cases. When a case is principal, it establishes a principle for the interpretation of law and the execution of that law in practice. When cases follow this principle, they have to cite either the principal case or another case where this principle is applied. Thus a chain of citations towards the principal case is created. To discover if a case is principal, we can use the number of citations as an approximation. Since the principality is a reasonable proxy for importance, we can compute importance as a correlation with the number of citations. Additionally, since principality can be established through a chain of citations, any cited case citing an additional case will amplify the importance of the additional case more than an uncited case citing the additional case.

The second key observation is that citations accumulate over time so that older cases have had more time to collect their citations compared to newer cases. Therefore, the importance of a case degrades over time.

To summarize, the underlying assumptions for this analysis are:
- Number of citations correlates with importance.
- When an important case cites another case that case has some importance as well.
- Age is negatively correlated with importance.

To compute the importance based on the above assumptions, we use the PageRank algorithm over the citation graph built during the data exploration. PageRank is an algorithm developed by the Google founders Larry Page<sup>1</sup> and Sergey Brin as [research](http://ilpubs.stanford.edu:8090/422/1/1999-66.pdf) at Stanford University with the purpose of improving search engines. Their key insight was that an important page, let's say the New York Times, would have many links pointing to it, but also that if some page like the New York Times links to a page, this page is more likely to be important than if our personal homepage would link to it. This is transferable to the judiciary system with cases instead of pages and citations instead of links.

The main idea of the algorithm is to model webpages as nodes in a Markov chain with transitions being links from one webpage to another. You then simulate a person surfing the web through these links where he or she starts at some node chosen at random from a uniform distribution, and randomly selects a transition from this node with equal probability. From this node, another transition is selected, and this process continues infinitely. The value that the PageRank algorithm assigns to each node is the probability of being at a given node at any time and is a proxy for the popularity or importance of a page. The figure below illustrates this behavior.

<sub>1: The algorithm is named after Larry Page and no the fact that it was use to rank webpages.</sub>

![PageRank example graph](https://upload.wikimedia.org/wikipedia/en/8/8b/PageRanks-Example.jpg =600x*)
<!--- The image is in Public Domain so no need to cite it --->

In addition to the infinite surfing, the PageRank algorithm also includes a probability of a web surfer stop, but it is modelled as the probability of continuing from a particular page and is called the dampening factor $\alpha$. These two concepts together can mimic a lawyer preparing their arguments by looking through cases. They start at some case related to the topic at hand, and they will look at its citations to see if this case is more useful in this context. They will perhaps go up another citation level, but rarely more than this. We can compute the probability of stopping a given node with different dampening factors to select the appropriate $\alpha$ for our scenario.

![Probability of stopping by dampening factor and transitions](./images/dampening.png)

Two extensions of the PageRank algorithm are utilized in our analysis. The first extension is the usage of weights on transitions. The selection of the random transition $t \in T$ is then biased by a weight $w$ with the following formula

$$ P(t) = \frac{w(t)}{\sum_{t_i \in T} w(t_i)}$$

When a case $a$ cites another case $b$ multiple times, we assume that the argument of $a$ is more heavily based on $b$ than other cases it cites.

The other extension changes the other uniform distribution of the original PageRank algorithm by selecting the initial node non-uniformly. The idea is that we can personalize the PageRank algorithm to reflect the bias of each individuals preferences regarding webpages. For our purpose, the personalization of a case is $0.75^{age}$, which corresponds to a lawyers starting at a newer case rather than older case with a probability loss of 25% per year.

__People v. Enoch (1998)__

According to our measure, this case is the most important, and it is not difficult to see why when it has 1450 citations. However, an urgent question is why this case has so many citations, and if it warrants such a high importance score.

A summary of the case is that Willie Enoch was charged with four counts of murder, and one count each of aggravated kidnapping, attempted rape, and armed robbery.
After a jury trial in a circuit court, the charges of armed robbery and murder in the course of armed robbery were waived, but he was convicted of all other charges.
At the death penalty hearing, Enoch waived a jury, and he was found eligible for the death penalty.

A major issue of this case is that the defendant failed to file a post-trial motion, and the question is whether this results in waiving the rights to appeal any trial issues.
The Supreme Court of Illinois decided that it does result in waiving the rights to appeal trial issues.
Without having this post-trial motion, the Supreme Court noted, the appeal is open-ended, and thus place a needless burden on the defense, prosecution, and court.

Since this issue is applicable to cases in general and establishes precedence for what should happen if the defendant fails to file a post-trial motion, this case is of great importance.

__People v. Herron (2005)__

To look at the importance of a more recent case, we will dive into why People v. Herron establishes precedence. As a summary, the defendant was convicted of first degree murder and armed robbery. In the appeal, he raised an issue of whether the trial court properly instructed the jury about eyewitness identification testimony, but did not object during trial or post-trial motions.

The Supreme Court of Illinois had to decide whether to maintain a two-part test for plain error, which is when one party has committed an obvious mistake, or to adopt the four-part test as the federal court system does.

The two-part test used in the judiciary system of Illinois allows a reviewing court to declare a plain error if
1. the jury's verdict may have resulted from the error and not the evidence, or
2. the defendant is denied a substantial right due to the seriousness of the error.

The four-part test used by the federal court system allows appeal court to correct the error if
1. it is an error,
2. it is plain or obvious,
3. it affects substantial rights, _and_
4. it seriously affects the fairness, integrity, or PR of the judicial proceedings.

It is obvious from this that the two-part test is less strict, and since the Illinois Supreme Court declined the request to change to the four-part method, it is evident that this case establishes precedence for declaring an error in future cases in the Illinois judiciary system. It is fair to say that this case is important.

__Conclusion:__
A natural question is whether this score reflects importance of a case. The analysis of People v. Enoch and People v. Herron showed that these are indeed important as they establish precedence for parts of the judiciary process. Obviously, this measure needs more assessment than 2 cases to see if it is valid, but so far the measure seems solid.

It is unclear whether cases important to a subfield of law are properly scored. If they are underestimated, a solution would be to make different importance scores where networks are constructed and analyzed for each subfield, and thus, each case would have a score for overall importance and for subfield importance. Topic modelling could be used to determine the subfield of each case.

__Discussion:__
One thing that this measure does not account for is if a case overrules another, e.g. due to changes in society. A way to detect an overruling would be to use computational text analysis for classification.

A big latent issue of this analysis is that the network is inherently incomplete. This is because we do not include every American court from which cases can be cited. PageRank relies on the network to propagate importance, and therefore, it would result in a more accurate analysis of importance. Also, unpublished cases can still cite published cases, and therefore, contribute to the importance, but that is not accounted for here.

## Prediction of importance score

With a measure of importance based on citations, we can tell if a case _IS_ important but it is also interesting to predict if a case _WILL BE_ important because new cases have no or few citations but they may become really important by establishing some precedence.
Our idea is to look at the opinions of each case and use this data to predict the importance scores.

To check if this is feasible, we can use t-SNE to visualize the high dimensional data of the TF-IDF matrix for the tokenized and lemmatized opinions in 2D with a color map for representing the target variable. The way t-SNE works is that it tries to mimic in 2D-space the relative distance distribution between the points in high dimensional space (van der Maaten, L. & Hinton, G. (2008), 'Visualizing Data using t-SNE').

 A nice property of t-SNE is that it also accounts for local density variance in high dimensional space when deciding how to represent these in 2D space. The axes are less interpretable unfortunately, but clusters in 2D space represent clusters in high dimensional space, which means if clusters share the same color, the cluster info is usable in the prediction of the target variable. Additionally, the distance between clusters also try to mimic the distance between these in high dimensional space.

![t-SNE of the TF-IDF matrix for the tokenized and lemmatized opinions](./images/tsne.png)

We use a random forrest instead of a linear regression. The theory of why this is better is that we will have different types of cases, e.g. IP law or family law, and perhaps also different eras of law, where each tree regressor will be good at a predicting one or few of these categories.

To improve accuracy, we employ a document embedding for encoding the text into a vector. A document embedding is similar to a word embedding in that it captures a concept by a fixed length vector in semantic latent space. We want to use this method because we're interested in making semantically similar cases be close in the latent vector space. This way, we should capture topics and other details about each document.

The concrete document embeddding we're using is called Distributed Memory (Le, Q. V. and Mikolov, T. (2014), 'Distributed Representations of Sentences and Documents'), which is similar to the continuous bag-of-words model for word embeddings. The difference is that it includes a paragraph id in the input, which essentially acts as memory to help associate words with paragraphs.

![Prediction vs actual](./images/prediction.png)

An  R2  score of 0.72 for the test set means the the regressor is fairly good at predicting the importance score. However, as we can see from the graph of actual / prediction, there are also outliers for both under- and overestimation. However, given the task, we are suprised by the predictive power.

A concern is whether the language over the 240 years of cases in this dataset is changing and how it affects the predictive performance. Looking at the colors, we can see that many yellow, green, and blue shades follow along the line y=0 showing the predicted value is 0 while the actual value is something greater. This shows that cases 75 years or older are underestimated, but for more recent cases shown in pink and orange tones, we do not see any clear pattern of bias.

## Conclusion
To summarize, using the Illinois court cases data set, which contains approximately 183,000 cases over a period of 240 years, we can construct a citation graph. Using said graph, various metrics of importance can be used, and ours is based on the PageRank algorithm. A clear behavior is that a significant amount of cases will be of little importance and a minority will be considered very important.

Furthermore, a prediction of importance score reveals that the content of the opinions is a strong indicator for noteworthy cases. This can be a result of a multitude of things: a judge listed in the opinion, a particular style of writing revealing the judge or the type of case, the topics of the opinions, or even individual words.
