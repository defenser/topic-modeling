Analysis of Open Source Java Projects
===============
This repository contains code to analyze different versions of Java open source projects such as **Apache Hadoop**. Much of the work is based on a previous paper by [Baldi, Lopes, et. al.](http://dl.acm.org/citation.cfm?id=1449807 "ACM Link") The aim of this project is to characterize developement processes of open source Java projects by computing key summary statistics of the output obtained by running **topic modelling (LDA)** on each version of each open source Java project. For more details regarding the project and the conclusions please read the [project report](https://github.com/abhinavkulkarni/topic-modelling/blob/master/Report.pdf "Project Report").

Code Details
===============
Source code for two sample projects **Apache Thrift** and **Apache Xerces** is downloaded in the directory **data** in the repository. **Eclipse** project **TopicModelling** tokenizes the Java source files and mirrors the structure of data directory to a specified location. Directory **mallet-data** is the output from running **TopicModelling** on the two Apache projects. It looks at Java files and tokenizes them.

The next stage is topic modelling. [**Mallet 2.0.7**](http://mallet.cs.umass.edu/ "Mallet Homepage") is used to run topic modelling on the project versions. Various BASH scripts to run LDA are located in **scripts** directory of **mallet-2.0.7** in the repository. Script **import-data.sh** imports the data in a format that **Mallet** understands. Script **calculate-perplexity** runs the LDA code on selected major versions of each project for a range of number of topics and calculates perplexity for each topic count. From perplexity plots, optimal number of topic counts for major versions can be found out (and can be intra-/extrapolated for other versions of the same project based on LOC/number of files). Once optimal number of topics for each version is know, run **run-LDA.sh** script to output sparce word-doc matrix for each version.

This sparce word-doc matrix is read by **MATLAB** and various summary statistics, both version- and project-wide, can be calculated. Conclusion drawn from these statistics and their interpretation is explained in the project report.

