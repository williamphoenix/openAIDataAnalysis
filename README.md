# Project Motivation & Methodology
This is some of the code that I used on an undergraduate research project that ran from August of 2024 to January of 2025. 
The goal of the project was to identify what employees of hedgefund companies do as their job, as well as their level of seniority using openAI's API.
We began with data all of LinkedIn accounts created before 2020, and filtered for people working jobs that matched certain induestries relevant to hedge funds.
Then, we further narrowed our data by only including jobs which were associated with certain known hedgefund companies.
With this data, we manually categorized jobs names who were very common, such as financial advisor, and submitted the rest to openAI for an AI analysis.
In total, the product was data of hedge fund employees and their jobs, with an analysis of what the function of the job is, and what level of seniority the job holds.
The methodology of this project can easily be extended to other projects as well.

## Attached code
The annotated code in this repository is the final code that I used in order to process the data & submit it to openAI.
In the code, I explain how it can be used, what requirements are needed to run it, and the motivation behind why the code was written and what it accomplishes.
The next section explains, in chronological order of how the code was run on the project, what the purpose of each file is.

### filterData.ipynb
This file explains the first round of filtering, in which data that does not fit predefined industry categories are stripped away.
In addition, the code also filters the data for certain company ID's, ommiting any job that is not a member of one of the companies.

### dataFormatting.ipynb
The code in this file further reduces how many lines of data we need to submit to openAI in order to reduce costs.
An algorithm to find the most popular job names is provided, as well as one which splits the jobs into two categories: those that are among the top 10 most popular jobs and those that aren't.
The popular jobs were very easy to categorize manually while maintaining accuracy, and therefore did not need to be submitted to the AI. This reduced how much data was submitted by ~60%.

In addition, the file contains code that formats our data into a jsonl file that can be submitted to openAI, as they have specifications for how their data can be submitted.

Lastly, there is a tokenizer algorithm in this file which allows the user to get a close approximation to how many tokens a set of data contains.
This is useful for ensuring that submissions remain under rate limits, and estimating cost before submission.

### batchSubmission.ipynb
The code in this file contains the most important step of the project, the submisison of data to openAI.
There are 2 main parts of the code: uploading files to get upload IDs & batch submisison IDs, and collecting the finished data.
Additionally, code to query a batch submission is provided, as well as an explanation of what data is required to do so.
