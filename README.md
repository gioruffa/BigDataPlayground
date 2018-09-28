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

## Various
Why not using [Terraform](https://www.terraform.io/)? Because sometimes I prefer
a bottom-up approach. I think that for system and networks stuff it is much better
to know how the nuts and bolts works and then build a car factory.

# Prerequisites
## EC2 Limits
Default configuration for free tier members is to have at most 1 EC2 running instance.
You can check this limit in the [EC2 console limit section](https://us-west-2.console.aws.amazon.com/ec2/v2/home?region=us-west-2#Limits:).

If that is the case you will have to request an increase of the limit using the
appropriate form that can be reached from the aforementioned limit tab.
Not very "elastic" as an approach...

## Users and credentials
It is a good idea to create a dedicated user for this project. To create a user
go to the IAM service console and follow the wizard. It is very important to
give the user full acces to the EC2 service. And don't forget to generate the
programmatic access credentials, you will need them later.

More info on this topic here:
* [Academind IAM video](https://www.youtube.com/watch?v=9CKsX6MOPDQ&list=PL55RiY5tL51pgPovJKg6HFMFqiGNSZtQ5&index=3)
* [IAM Documentation](https://docs.aws.amazon.com/general/latest/gr/aws-sec-cred-types.html#access-keys-and-secret-access-keys)

## AWS CLI
It is a good idea to have the AWS cli console up and running.

I am mainly following this official [EC2 tutorial](https://docs.aws.amazon.com/cli/latest/userguide/tutorial-ec2-ubuntu.html)

First create a virtualenv and activate it
```bash
$ virtualenv virtualenv
$ source virtualenv/bin/activate
```
Then install aws cli using pip
```bash
$ pip install awscli --upgrade
```

Now configure the aws cli with the credentials obtained before.
```bash
$ aws configure
AWS Access Key ID [None]: AKIAIOSFODNN7EXAMPLE
AWS Secret Access Key [None]: wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY
Default region name [None]: us-east-2
Default output format [None]: json
```

You can now check if the cli client is properly configured issuing the command:
```bash
$ aws ec2 describe-regions --output table
----------------------------------------------------------
|                     DescribeRegions                    |
+--------------------------------------------------------+
||                        Regions                       ||
|+-----------------------------------+------------------+|
||             Endpoint              |   RegionName     ||
|+-----------------------------------+------------------+|
||  ec2.ap-south-1.amazonaws.com     |  ap-south-1      ||
||  ec2.eu-west-3.amazonaws.com      |  eu-west-3       ||
||  ec2.eu-west-2.amazonaws.com      |  eu-west-2       ||
||  ec2.eu-west-1.amazonaws.com      |  eu-west-1       ||
||  ec2.ap-northeast-2.amazonaws.com |  ap-northeast-2  ||
||  ec2.ap-northeast-1.amazonaws.com |  ap-northeast-1  ||
||  ec2.sa-east-1.amazonaws.com      |  sa-east-1       ||
||  ec2.ca-central-1.amazonaws.com   |  ca-central-1    ||
||  ec2.ap-southeast-1.amazonaws.com |  ap-southeast-1  ||
||  ec2.ap-southeast-2.amazonaws.com |  ap-southeast-2  ||
||  ec2.eu-central-1.amazonaws.com   |  eu-central-1    ||
||  ec2.us-east-1.amazonaws.com      |  us-east-1       ||
||  ec2.us-east-2.amazonaws.com      |  us-east-2       ||
||  ec2.us-west-1.amazonaws.com      |  us-west-1       ||
||  ec2.us-west-2.amazonaws.com      |  us-west-2       ||
|+-----------------------------------+------------------+|
```
... Coming soon ...
