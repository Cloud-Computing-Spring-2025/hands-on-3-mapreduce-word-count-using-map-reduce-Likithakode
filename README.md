# Word Count using Hadoop MapReduce

## Project Overview
This project implements a Word Count program using Hadoop MapReduce. The program processes a given text dataset, counts the occurrences of each word, and outputs the results in a distributed manner using Hadoop's MapReduce framework.

## Approach and Implementation
The Word Count program consists of two main components:

### Mapper
- Reads input text line by line.
- Splits each line into words.
- Emits each word as a key with a count of 1.

### Reducer
- Receives word-count pairs from the Mapper.
- Aggregates the counts for each unique word.
- Outputs the word along with its total count.

## Execution Steps
Follow these steps to build and run the Hadoop MapReduce Word Count program:

### 1. Compile the Java Code
sh
hadoop com.sun.tools.javac.Main WordCount.java
jar cf wordcount.jar WordCount*.class


### 2. Create Input Directory in HDFS
sh
hadoop fs -mkdir -p /user/input
hadoop fs -put input.txt /user/input/


### 3. Run the Word Count Job
sh
hadoop jar wordcount.jar WordCount /user/input /user/output


### 4. View the Output
sh
hadoop fs -cat /user/output/part-r-00000


## Challenges Faced & Solutions
- *Handling Large Input Files*: Used Hadoop's distributed storage to efficiently manage large datasets.
- *Data Preprocessing*: Implemented text normalization to remove special characters and convert words to lowercase.
- *Performance Optimization*: Used Hadoop Counters to track the number of processed words and optimize execution.

## Sample Input and Output
### Input (input.txt):

Hadoop is great
Hadoop is powerful
Hadoop is scalable


### Expected Output (part-r-00000):

Hadoop 3
is 3
great 1
powerful 1
scalable 1


This README.md provides a clear understanding of the project, making the repository self-explanatory and well-documented.
