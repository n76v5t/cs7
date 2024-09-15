java c
A Google Matrix and PageRank Procedure 
MAT 167 Project 
August 4th, 2024 
Investigating the PageRank Procedure Through A Google and Term-Document Matrix 
Abstract 
Everyday, millions of people people are “Googling.” This raises the question, how does Google decide which web-pages to suggest? Google’s most famous algorithm for solving this problem is fittingly called PageRank. We have implemented the PageRank algorithm on a “small” network of 12 web-pages and demonstrated how it sorts search results. This was done by using the dominant eigenvector of a Google matrix and the power iteration method. Included, are examples of this procedure, showing its effectiveness and efficiency.
Introduction 
In this day and age, most people are using Google (or a subsequent search engine) daily. How do these search engines determine the search result? Which lucky web-page gets to be the top result and the likeliest one to be clicked?
Cleve Moler in his book Numerical Computing with MATLAB, explains the be-ginnings of this technique. In 1998, both Larry Page and Sergey Brin of Stanford University created a way to assign a perceived importance for each page, commonly referred to as the PageRank algorithm (Moler 2004). It uses a stochastic matrix, here referenced as the Google or G matrix, to track the accessibility and catalogs each web-page’s interaction with others. The premise is that each page has a specific rank. The rank of a web-page increases when creditable sources link to it and decreases when the page links to an excessive amount of other pages.
In tandem with the PageRank algorithm, a term-document matrix is necessary to query each web-page. This is a matrix that considers a network of web-pages and its key terms. When a user wants to search for a specific term, a query vector is used to select specific pages with the desired term. The harmony of the two, is that once a query is made from the term-document matrix, the PageRank returns all desired web-pages in a relevant order.
Procedure 
The Google Matrix 
To demonstrate the procedure, consider the following Google network graph.

Note that each letter represents a given website and the arrows indicate in-coming and out-going links. We can represent this specific network as the Google matrix shown below. The matrix is organized such that each row, 1 through 12, represents the web-pages A through L and each column represents in-going links to the subsequent web-page. We can also notice that the rows represent the out-going links.

How to Find the PageRank vector 
Now that we have a matrix representation of our network, we can numerically determine the importance of each node. Ideally, the mathematical model we use would show important web-pages are linked to other important web-pages. PageRank achieves this by assigning a rank r(P) to page P based on a weighted sum of links it has to another page Q:

Here, BP represents the set of pages in-linked to P, and |Q| is the number of out-links from page Q.
For example, in our network, BD = {A} ⇒ r(D) = 2/r(A).
Since the rank of each page depends on the rank of other pages (and vice versa), we need to iteratively calculate rj (Pi), where i indexes the pages (P1 = A, ..., P12 = L) and j tracks the iteration number. r0(Pi) can be any arbitrary initial page ranks so let’s set r0(Pi) = 1/i. Eq(2) becomes:

All of the page ranks can be arranged as a vector: πj:= [rj (P1) ... rj (P12)]T∈ R12≥0. This results in an easy way to sort the pages by level of importance. It is common practice to normalize πj so that πj = πj/∥πj∥1. More importantly, if πj converges as j goes to infinity, then the PageRank vector is defined as π := limj→∞ πj.
Power Iteration Method 
There are several approaches to finding π. One method, Power Iteration, relies on the fact that subsequent πj’s can be computed by multiplying πTj−1 by G. Explicitly:

Eigenvalue Decomposition 
Now, we will look at finding π using Eigenvalue Decomposition. Since πTG = πT implies πGT = π, that would mean πTis the dominant left eigenvector of G, which is the same as saying π is the dominant eigenvector(largest eigenvalue) of GT. Performing an eigenvalue decomposition of our GT matrix yields the following set of eigenvalues λ and eigenvectors v1, ..., v12:

Here lies a problem. Our dominant eigenvalue λ = 0.884 is less than 1. The Power Iteration method would converge to zero becuase multiplying a matrix and its eige代 写MAT 167 A Google Matrix and PageRank ProcedureMatlab
代做程序编程语言nvector results in the eigenvector scaled by its corresponding eigenvalue. If πj approaches an eigenvector of GT, that would mean subsequent iterations will keep shrinking that vector until πj = 0.
Iterating through πj’s can be thought of as finding the new probability distribution of where a web-surfer would be after following j links. Take a moment to look at web-page C. There are only links going TO C but none going FROM C! This means users jumping between web-pages would be able to reach C, but not leave it. In a sense, our pages “lose” rank with every πjiteration because users that previously linked to C can no longer move to a new page and no longer considered. For this problematic behavior, web-pages (such as C) with no out-going links are noticed and dubbed dangling nodes. To remediate this issue, let’s consider that the user at website C has the ability to then pick any other site in our network by random, in essence have the ability teleport. This will be denoted in the new (stochastic) G matrix.

Our new λ and v1, v2, ..., v12 become:

Normalizing v1 so that π = − ∥v1∥1/v1, we get:
πT = [0.029 0.060 0.106 0.023 0.207 0.076 0.072 0.152 0.061 0.074 0.088 0.053]
Setting π0 = [1/12 ...1/12], Power Iteration with π50 = π0G50 yields
πT = [0.029 0.060 0.106 0.023 0.207 0.076 0.072 0.152 0.061 0.074 0.088 0.053]
Guaranteeing Strongly Connected Network 
When dealing with web-page networks, a potential obstacle that can come up is that the network is not strongly connected. A strongly connected network is one where a path of links can be found between any two nodes. This is cause by one of two scenarios: there are dangling nodes (which we already addressed) or the network is really 2 or more sub-networks lacking bi-directional links (not the case for us). Luckily, the idea we used for addressing our dangling node can be scaled up to force any network G to be a strongly connected network ˜G.
˜G := αG + (1 − α)E                                              (8)
Where α ∈ [0, 1] and E := 12/1 ✶12✶T12.
Essentially, what this addition of matrices does is allow every node to be able to teleport to any other node. In our case, we generate the same π whether we use G or ˜G.
Term-Document Matrix 
The PageRank algorithm is also dependent on a query, or a way to retrieve de-sired web-pages. For our 12 web-pages, we are going to use a term-document matrix. Consider the following web-pages and their keywords:

Table 1: Webpage-Keyword
We can use this table to construct a term-document matrix. A term-document matrix is a way to represent the presence of terms (in this case, car brands) across a set of documents (web-pages). Each row of the matrix corresponds to a unique term, and each column corresponds to a document. The entry in the matrix indicates whether a particular term is present in a particular document. This is shown in the following table.

Table 2: Term-Document
The matrix can also be constructed by the following: Let W be the set of web pages and C be the set of car brands. We define a binary matrix M of size |C| × |W| where each entry Mij is 1 if the i-th car brand is present on the j-th web page, and 0 otherwise.

Either way, the resulting matrix will be:

Constructing the Queries 
The term-document matrix itself can look daunting, especially with a large matrix. In order to efficiently utilize this matrix, all someone needs to do is consider the list keywords.
1.Alfa Romeo, 2.Audi, 3.Cadillac, 4.Dodge, 5.Hyundai, 6.Jaguar, 7.Lexus, 8.Mazda, 9.Mercedes, 10.Nissan, 11.Porsche, 12.Tesla, 13.Toyota, 14.Volkswagen
These keywords can be thought of as a vector comprised of 14 elements. For any desired keyword, one needs to make that index of the keyword equal to one, while undesired keyword are zero. Take the transpose of the term-document matrix and multiplying it by the vector and the result will be all the web-pages with the desired term(s). This can be even more elaborate if you want multiple keywords in each document, you can set the vector indexed at the desired keywords 1/# of desired keywords and look for ones in the resulting vector. If there is a keyword one wants excluded in the return, one can set the index of those numbers to negative one. To read the output vector, the reader just needs to look at the index of where the ones are. These are the desired web-pages that then go on to the PageRank vector π.

         
加QQ：99515681  WX：codinghelp
