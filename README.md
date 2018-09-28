# Big Data Playground
A shy attempt to document what is needed to make a Big Data playground on AWS.

## Goals
The goal is to create a small cluster running a bunch of Big Data tools.

## Software Packages
The idea is to run the following frameworks/tools/solutions/whatever you want to
call them:
* HDFS/Hadoop mapreduce, because is the basis of everything
* HBase, because I have done some projects using it
* Spark, because I am doing some projects using it
* Kafka, because it is cool
* [maybe] Cassandra
* [maybe] Flink

## General Design
The cluster will be composed by three AWS EC2 instances. Why this number? Because
you should always test for three. That is a rule that I try to apply as much as
possible, and especially to production stuff.

**If it works for 3 it works for more...**

Besides this dogmatic approach, I will use one node as a master and worker and
the remaing nodes as workers only. This is not applicable to fully decentralized
systems like cassandra where all nodes will be used

## WHY?
Because it is the most effective way to learn something. And I wanted to play more
with AWS.
