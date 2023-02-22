## Text analytics code

### Gaining Early Insights from a Text Collection

[CreateDFforHSS.ipynb](https://github.com/spotka/DHanalytics/blob/main/CreateDFforHSS.ipynb): Given a text collection (e.g. [txts.zip](https://github.com/spotka/DHanalytics/blob/main/txts.zip)), it does a word frequency analysis, then it builds word maps based on frequency as well as TFIDF scores. 

---

### Document Similarity

[tfidf_createvecs.ipynb](https://github.com/spotka/DHanalytics/blob/main/tfidf_createvecs.ipynb): Given a document collection (e.g. [txts.zip](https://github.com/spotka/DHanalytics/blob/main/txts.zip)), it creates normalized TFIDF vectors. There will be a vector for each document in the collection. The vectors will be stored all together in a pandas dataframe, then to a csv file (e.g. [docvecs.csv]https://github.com/spotka/DHanalytics/blob/main/docvecs.csv)). The notebook also creates a csv file of docnames: [docnames.csv](https://github.com/spotka/DHanalytics/blob/main/docnames.csv).

[tfidf_cos_sim.ipynb](https://github.com/spotka/DHanalytics/blob/main/tfidf_cos_sim.ipynb): Given a document name, it finds the top similar documents to the given one. It uses cosine similarity on TFIDF vectors. For normalized vectors cosine similarity amounts to dot-product. It outputs the top similar documents in terms of their similarity score, docid, and docname. E.g. if we input docname 'txts/Arbuckle-Christie-Siemens_IntroductionSRC7.2_11-15-16.txt', it outputs

<pre>
scoremult docid docname
0.351171 7 txts/Arbuckle-Mauro-Siemens_Intro-Sydney-Whist...
0.270747 6 txts/Arbuckle-Crompton-Mauro_SRC-intro_Dec14.txt
0.184882 5 txts/Arbuckle-Christie_Intersections-Between_S...
0.183604 12 txts/Arbuckle-et-al-2020-Introduction-Open-Sch...
0.150295 99 txts/Siemens-2016-Faster-Alone-Further-Togethe...
</pre>

[txts.zip](https://github.com/spotka/DHanalytics/blob/main/txts.zip): Text collection from HSS Commons, 130 text files extracted from PDFs. This collection is only used to evaluate different similarity measures.

[docnames.csv](https://github.com/spotka/DHanalytics/blob/main/docnames.csv): CSV file containing docname, docid pairs. Created by [tfidf_createvecs.ipynb](https://github.com/spotka/DHanalytics/blob/main/tfidf_createvecs.ipynb). The structure of the file is as follows: 

<pre>
docname,docid
txts/03_Jensen_Its-not-Personal_WJS_Vol13_No-2_Fall-2017_pp-140-https://github.com/spotka/DHanalytics/blob/main/tfidf_createvecs.ipynb166.txt,0
txts/ACH-ALL-2005-Conference-Proceedings.txt,1
txts/Abstract.txt,2
txts/Arbuckle-2020-How-Can-We-Broaden-and-Diversify-Humanities-Knowledge-Translation.txt,3
</pre>

[docvecs.csv](https://github.com/spotka/DHanalytics/blob/main/docvecs.csv): CSV file containing docvecs. Created by [tfidf_createvecs.ipynb](https://github.com/spotka/DHanalytics/blob/main/tfidf_createvecs.ipynb). The structure of the file is as follows: 

<pre>
docid,termid,score,term
0,41217,0.7963703814049661,pratt
0,29708,0.26072073508329247,james
0,44505,0.18392130794771977,religion
0,44509,0.1782887684728951,religious
</pre>

--

[sim_eval.ipynb](https://github.com/spotka/DHanalytics/blob/main/sim_eval.ipynb): Evaluates different similarity measures for DH documents. Please see the thesis for more details. 


---



### Network Analysis of a Text Collection

[doc_sim_graph.ipynb](https://github.com/spotka/DHanalytics/blob/main/doc_sim_graph.ipynb): Given a text collection, it creates a graph of documents based on document similarities. 

It creates the graph of similarities starting from a zip file of documents, e.g. 2022txt.zip
 
Then, it computes communities (clusters) using the Louvain algorithm for modularity maximization.

It also computes network measurements, such as community cohesion.

Finally, the text of all the documents from the top three communities is extracted and Non-Negative Matrix Factorization (NMF) is used to find topics used in each of the communities. 

For more details, please see the thesis. 

--

[year_com_areas.ipynb](https://github.com/spotka/DHanalytics/blob/main/year_com_areas.ipynb): Builds wordmaps for the areas once they are mapped to topics extracted from NMF. 

--

[dhwikinet.ipynb](https://github.com/spotka/DHanalytics/blob/main/dhwikinet.ipynb): Builds a network of Wikipedia pages starting from a given page (e.g. Digital Humanities) and collecting its ego-net. It saves the graph to [dh_wikipedia.gexf](https://github.com/spotka/DHanalytics/blob/main/dh_wikipedia.gexf). 
This is not used in the thesis. 

--

---
