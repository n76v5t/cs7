java c
Math 167
Final Project
Due Friday, Sept 13th at 11:59pm
Main Idea:  You will be assigned to a small group and explore  Google’s Pagerank al- gorithm together on a set of generated data.  This really boils down to finding eigenval- ues/eigenvectors of a matrix and then explaining how this is useful when sorting search results.
Goal: The goal of this assignment is to practice ideas discussed in MAT 167 in a real life scenario and practice independant learning/implmentation of ideas.
Due Date: Your final report, executable file, and sample output are due on Gradescope by Saturday, September 14th at 11:59pm.
Recommended Resources:
•  Naoki Saito’s MAT 167 Lecture Notes (in particular 24 and 25):
https://www.math.ucdavis.edu/~saito/courses/167/lectures.html
•  Cleve Moler’s Numerical Computing in MATLAB Chapter 2: Linear Equations https://www.mathworks.com/moler/chapters.html
• http://www.scholarpedia.org/article/Google_matrix
•  There are dozens of useful resources online, feel free to google them.
What you are turning in:
• A Typeset Report on the PageRank Algorithm
• MATLAB  (or  Python,  R,  etc) file that  can be run by your instructor showing implementation of PageRank Algorithm on data your group is given
• PDF of your code with all outputs you use in your report
Rubric Overview:
• Report Content (50 points) - The mathematics in your report should be correct/accurate. Your explanations should be thorough and written so that a fellow MAT 167 student   could understand them.
• Report Grammar, Clarity, Organization (20 points) - Your report should be readable, meaning include minimal grammatical errors and be organized in a way that makes sense when reading.
•  Code is executable (20 points) - Your instructor should be able to run your code without any alterations.  You will need to include instructions for any files that need to be in the working directory to run your code file.
•  Sample Output (10 points) - You will turn in a PDF file with your code that contains the outputs mentioned in your report.  These should match the output your instructor gets when running the code.
•  Extra Credit (10 points) - For at least 2 pages,discuss an application of the PageRank algorithm that isn’t just to use for a search engine.
Note:  Thank you to  Dr.Jesus de Loera and Dr.  Dowman Varn for the project idea and data creation.
Project Guidelines
1. Your group will be given a hyperlink network, a list of terms that appear on each node in your network and a series of questions you’ll need to implement the PageRank algorithm to answer.
2. Punctuation, spelling, readability, and organization matter.  This should be a paper that makes sense from beginning to end when read straight through.  Think about the order you present information. A common order is Abstract, Introduction, Back- ground Information, Main Body of Report, Results, Bibliography, additional images that didn’t make sense to include in Main Body of Report, but you reference or find useful.
3.  Read up on Google’s PageRank algorithm using the above recommended resources.
4.  Programming wise, this is not an overly complicated process.  Moler’s Chapter 2 con- tains code you can copy paste, or using the suggested Plan of Action below you can run the PageRank algorithm using relatively few and simple MATLAB commands. It is typically easier to code this yourself than using Moler’s code.
5.  Comment your submitted code both for your own group and the grader.  Uncommented code will be marked down.
6. Include a background section or history section to your report.  Say a little about who invented PageRank and how its been used.  If you decide to do the extra credit, find an application of this Algorithm that isn’t about search engines and discuss that for at least 2 pages.
7. In your report, explain how the PageRank algorithm works as if this were a technical interview for a job.   That  is,  assume your reader knows most Linear Algebra  (aka eigenvalues, eigenvectors, eigendecomposition) so you don’t need to explain every little step, but also assume they don’t know how PageRank works or what is does fully. This report is about telling your reader how to apply Linear Algebra not teaching your reader how to do Linear Algebra.
8. In your report, clearly state your queries you are trying to solve and your solutions to those queries.
9. You don’t need to explain each line of your code in your typeset report. You do need to submit your code so the grader can run it.  You should only explain code in your report that you think is unique to your group or especially subtle that you want to explain.
10.  Have an abstract to your report and a conclusion/results section.
11.  CITE ALL SOURCES USED. The difference between a well-researched report and plagiarized report is rigorously citing your sources.   This is a great opportunity to learn about bibtex in LATEX.
12. Your report should include 代 写Math 167 Final ProjectPython
代做程序编程语言any relevant graphics.  Please avoid filler images that don’t contain useful information. For example, the Google Logo or use of Word Art doesn’t contain relevant information and wouldn’t make sense in a technical industry job, but a captioned example hyperlink network would be useful to include.
13. While I’ve given you a suggested Plan of Action below, don’t actually write  “step (a), step (b), step (c) etc” in your final report.
14.  Suggested Plan of Action to answer the questions you’ll be given:
(a) Turn your hyperlink network into a “raw” Google Matrix, G.  Check that all rows add to 1 or 0. If this is not true, you’ve made an error and should start again.
(b) Perform. an Eigenvalue Decomposition on your raw Google Matrix. If you didn’t see this in MAT 22A, you are encouraged to read about it in Elden (textbook on canvas), Moler (textbook linked on page 1 of this document), or Google in- formation about it.  You may also want to read how to perform. an Eigenvalue Decomposition in MATLAB.
https://www.mathworks.com/help/matlab/ref/eig.html
(c)  If you’d like to solve the Eigenvalue Decomposition by hand, you should solve the equation
1 · vT  = vT Gwhere vT  is a row vector whose entries measure the importance of the web page that you are considering and G is the Google Matrix.  This explicitly assumes you have an eigenvalue of λ = 1.
(d)  If you were able to find an eigenvalue eigenvector pair of (λ = 1, v), you are good to go.  If you did not, then consider the eigenvector corresponding to the largest eigenvalue. Does this eigenvector have all non-negative entries?
(e)  If you have issues above, this is because your original Google matrix, G, needs to be altered to have some properties we desire, namely each row should sum to 1 (no rows should sum to 0).To “fix” G, go back to your original hyperlink network.  Are there any dangling web-pages?  (Meaning, are their any web-pages that don’t link to anything/have edges directed away from their node.) If there are, we will “fix” this by adding a edge from that node to every other node in our network. Do this for all dangling web-pages andrecalculate your Google Matrix. This “fixed” Google Matrix should now add to 1 in every row.
(f)  Perform. another eigenvalue decomposition.  We want a  (λ,v) pair where λ =  1 and all entries of v are non-negative.  If you found such a pair, move on.  If not,
you probably have done something wrong above.
(g) We typically normalize v such that ||v|| 1  = 1. Do this.
In documentation online you may see this as vT 1n   =  1  where  1  ∈  Rn ×1   is  a column vector of all 1’s.
(h) The  entries  in  your  normalized  v  are  the  “importance”  factor  of  each  corre- sponding webpage.  Order the entries in v to be monotonically decreasing  (non- increasing/highet to lowest with repetition allowed).
(i) If G is relatively large then it is difficult to compute the eigenvalues by hand.  One way you may want to learn about to find the eigenvector associated to the largest (often called the dominant) eigenvalue is called the power method.  You can find information about this in Naoki Saito’s MAT 167 Lecture 24 notes.
This method has you iterating
1 · πj(T) = πj(T)−1Gtaking π0 to be any unit vector until ||πj −πj−1|| is smaller than a preset “tolerance level” . Here we preset λ = 1.  The most common choice for π0  is 1n.  How many iterations did this take you? Do you get the same eigenvector as before?
(j) Your hyperlink network won’t have this issue, but in general you need to check that your hyperlink network is strongly connected. You should double check this just to be sure.
If your hyperlink network is not strongly connected, then you will need to  “fix” G again by doing the following:
G = αG + (1 − α)E
where α ∈ [0, 1] and E =  1n 1n(T) . This “fix” adjusts for so called “teleportations”where an internet user types a web address into a search bar instead of using hyperlinks to go from one webpage to another. The typically α value is 0.85.
Construct G for your hyperlink network.
(k)  Perform. an eigenvalue decomposition of G using any method.
(l)  Compare the rankings you got from G and G (that is, compare the eigenvectors of the largest eigenvalue). Are these rankings the same?
(m)  Now that you have a handle for how to implement the PageRank algorithm, its time to use the list of keywords associated to each web page.
(n)  Create a term-document matrix, T, from your list of keywords.
(o)  Next, you were told a series of queries involving your keywords.  Turn each query into a query vector, q.
(p)  Compute dT  = qT T.  Using vector d, determine which webpages are responsive to your query.
(q)  Finally, use your webpage ranking you calculated above to rank the responsive webpages in order of importance. Present  these  in  your  final report with  an explanation of how you were able to find them.







         
加QQ：99515681  WX：codinghelp
