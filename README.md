# MLOps_End_to_End
machine learning project lifecycle---

It is prudent practice that once after training a model , the obvious ask would be to make
it production ready..

a typical deployment example:-
==============================

let us take one example where our task is to build a model that predicts a product(new one or  used one)
by using visual inspection. More formally this belongs to computer vision problem statement. once the model
is ready, it will be used to generate predictions on a machine hosted in edge device/cloud/on-prem. The model
artifacts and solution would be packaged in a prediction server and predictions will be made using a api endpoint.
Often times it is noticed that models predictions are way off from what is expected out of them due to fact that
data distribution used in training and inference pipeline differs significantly from each other. This is also 
coined as data drift. That means delpoyed model is not able to generalize well to make correct or appropriate
predictions as such.

machine learning in production:-
================================

let us imagine that a machine leanring model(y=f(x)) from above deployment strategy find its way to production
system. if you really try to surface around the amount of code it takes to make it production ready will be around 5-10 %.
In essesnce your machine learning code would be 5 to 10 % of total ML project infrastructure related code base
to avail a smooth conduct. The remaining 90 % code includes data colletion, cleansing , data preparation, feature 
extraction in the of making data pipleine ready. Furthermore it includes codes to set up ML resource and process 
management, service infrastructure and monitoring that surrounds ML code in order to make it alive in production.

- scope (define project, what is y = f(x))
- data (define data baseline and create labels, organize)
- models (build, select, train model and run error analysis)
- deployment ( run in production and monitor)


accepting challenges of deployment:-
====================================
Once after deploying model in production there could be two challenges that may arise or pop up. 

To discuss about first challenge, a.k.a data drift and the other one is model drift. let us discuss about both of them in detail.

data drift:-
============
More technically, Y = f(X's) , it refers to change in input X.
Meaning that our input value X's distribution has changed over time that is unknown to the model.
Let us understand this with a simple example down below.

sometimes data might change very gradually and not very often nor very drastcally. for instance in speech
recognition engine english langauge appeared to be including gradual shift in its grammar and several other ways
how people are pronouncing it now-a-days.

sometimes data might change drastically or accidentally due to some unwanted circumstances. for instance when pandemic
hit a lot of people started using oline shopping to a large extent. this clearly seems to be a sudden change in data
that gets plugged into a credit card buying behavior modelling process.

model drift:-
=============
With notation, Y = f(X's) with a different change in mapping (earlier a linear function is fitted,
now a complex non linear mapping is introduced).

Meaning that our mapping that does prediction will now generate output value way far from that is expected,
or prior to earlier iteration.

After deployment of any model the most important aspect is to manage or mitigate these two issues carefully.
In addition to this there exists software engineering issues that needs to be fixed as well. Let us discuss about
these challenges,

	- how data is supposed to come (real time or batch process)
	- where model is going to run (edge device or cloud)
	- what compute is required (cpu, gpu, tpu, memory)
	- performance of any operation (latency, throughput)
	- logging (log as much data as you can for analysis and debugging) 
	- security and privacy (model application with bank internal data)

Having said this, it turns out that any ML model project can suffer from the concept of model drift and data drift.
In peculiarity, ML project with maintainence lifecycle activity might suffer from the concept of model drift where
a new develpment team has changed model mapping(Y = F(X's) from linear to non linear one.
 
Accordingly a complete new ML project lifecycle activity might suffer from the concept of data drift, if any way 
data distribution has changed in test or validation set.

common deployment cases:-
=========================
in accordance with the ML project deployment following cases own their account as mentioned below.
	- offering a new product capability
	- automate or assist new task
	- replace old/unproductive ML system

let us detail down each one case with specifics. 
Being able to develop a new problem statement like the one with visual inspection of products would demand 
an end to end deployment strategy in order to make things work.

With an ongoing ML system in place there might be chances that set of tasks needs to be automated. however
at times a specific task could be to add a new task to existing workflow. These types of requirements will
demand a deployment strategy of its own.

Following feedback and response loop of any ML project question may arise to replace a decade old , inefficient
application with an efficienet ML system in place. to negotiate this requirement a deployment strategy is required
as well.

one thing to keep in mind here is that all the cases related deployment performs two specific task,
	- gradual monitoring/shift operation
	- rollback operation

As per deployment cases different types of deployment strategy attain its meaning. let us delve into each of them.
	
	- shadow mode:-
	---------------
		
		it allows a visual inspection (in this case) that examines output from ML model and to that
		of a human to run through. in essence this will indeed help that runs in parallel and gather more 
		understaning on data and performance by not doing any decisions on data.

	- canary mode:-
	----------------
		it seems like when a ML model is ready to be tested in real time, a common deployment strategy that
		fall in place , a.k.a canary deployment with a minimum of traffic( around 5 to 10 %). Then it starts
		predicing output with a gradual shift in trafiic to be monitored. Only when the system acruires
		enough confidence on prediction then it is allowed to ramp up with more traffic in a gradual manner.

	- blue green mode:-
	--------------------
		in blue green mode, ML model is routed to an old/base application and new/enhanced application. depending
		upon performance of applied ML model traffic is allowed to make predictions using new model or else 
		router will use old/base model. This will enable an easy way to rollback of something goes wrong.
		in typical scenario, one can use a complete traffic shift or a gradual shift of traffic.


degrees of automation:-
=======================
as of now it is evident that ML model can be used to automate tasks by using different modes of deployment
strategy. but the real challenge how are we going to automate ? many ML system gradually starts from human 
in loop till it finds that suitability of using full AI automation to make data driven decisions completely.

let us discuss about different types automation.
	- human only ( visually inspect all by human)
	- shadow mode ( use both human and AI to go side by side)
	- AI assistane ( helps human to a greater degree)
	- partial automation ( consider ML model predictions confidence, if not send it to human)
	- full automation ( ML model is taking every single decision)


monitoring a ML system:-
========================
A ML system should be monitored throughly to make sure that it meets required performace expectation. Well, how
can we ascertain all kinds of monitoring parameters in a ML system ? Most commnly, a ML system can be monitored
by building a dashboard with all parameters over time. Let us delve into this discussion.

Broadly speaking, monitoring can be done in following aspects,
	- server load ( ideally keeps a track of server load in ML system) 
	- missing input values
	- not null outputs

And therefore proper data understanding should be always handy, in fact a brainstorming session in order to 
understand what could possibly go wrong with your data over time. Always keep a tab on data that will be used 
to run your ML system in each iteration and put all checks to safeguard. Besides that brainstorming with a few 
statistics will help the team to decide what went wrong, and stuffs like that.

To help us get more details around monitoring aspect here are a few key metrics to put a call,
	- software metrics ( latency, throughput, server load, memory )
	- input metrics ( input distribtion of X's, like avg. input length, total missing values)
	- output metrics ( output as null, user search, user web search)

This is in continuation with the fact that most ML system are iterative process and hence input and output data 
plays a vital role to meet expected performance. That clearly states that a ML system will have to be stringently
monitored with input and output metrics. Like modelling, deployement is also a iterative process as well from traffic
to attain effetive performance. Adding all these checks and balances (thresholds) to ML system will definitely help, navigate through issues with 
a root cause analysis. These set up will eventually trigger all possible issues before you hit a roadblock or a deadend.

Most of ML systems in place are equipped with automated retraining or manual retraining. For many applications manual
retraining looks more in action and in some consumer based applications there may be complete automated training in 
place to fix any kinds of alerts or change.


pipeline monitoring:-
=====================
as part of our earlier example of visual inspection model that predicts a product either damaged or new one 
from its image.

here the model will take an example image of of product, run the model and predits whether or not any given
product image is damged or new one. 

product image ----> generative model -------> damaged or new one


product image ----> generative model -------> better resolution and product screening ----> generative alorithm ----> damaged or new one

actually speaking the way these ML system works might be complex in real time. for instace a specific product image
cane be screened or labelled properly before getting it used via the generative model. on a senond thought any 
product can be fed to another model that reshapes the product into a better resolution product which in turn gets 
consumed via the generative model. so the point here is that a simple looking ML system from eyeballing does not 
seem to be that easy, instead it has a series of complex steps running in sequence to produce desired result. 

This is an example of a ML pipeline followed by steps, where there is one step that performs a specific task 
(using a model) and output of that step will be the input for the next step (another model). However, in reality
metrics to monitor a pipeline remains intact with our ML system monitoring phase meaning that one can very well
perform all prescribed metrics like software metrics (for each step or whole pipeline), input and output metrics 
in this case as well. 



best practices to build ML models:-
===================================
From project to project building production ready ML system offers different set of challenges. This will start
from receiving suggesstions till improve model using error analysis. 

the way ML system grown up these days by correcting models rather than data with complex neural network architecture. However , it has been found that 
in practicality using a data centric view makes it more efficinet and improved in so many ways. 

For instance while designing a complex neural network the focus can be shifted to provide the model high quality data than just to
tweak model all the time. But then feeding only high quality data would not suffice, a time consuming process, 
and therefore tools  can be used to enrich data with very little less time. 


ML System:--
============
ML system is basically made up of model/code and data. In this time, the ask is to build a very good ML system that
often demands a very good model to make good predictions on data. Another way, specific use cases will do pretty well
with some baseline models (from github) available but providing high quality data can surely enhance its performance
to a new level.

Model Development is an itertaive process where a model, data and tuned hyperparameters yield a very good X-->Y 
mapping. Then why is model building is such a diffiult task? refer below

	- model does well on training set
	- model does well on dev/validation/test set
	- model does well as per specified business metrics or project goals

A typical problem that looks so minute often carry a lot of risk is that a defined ML system in place produces
less error on dev/test/validation sets still it fails to meet business metrics or goals in outline. Many a times in a many projects there has
been quite a lot of discussions on ML system can not be approved for production due to so and so reason.
As ML engineer our task is not just to build models that does very good on test set, well that is to be celebrated,
but defining that as the final would not deliver the justice to production application. Above all a ML engineer would
need to build models that truly delivers business expectations instead just to hold on to high test set accuracy. 
Let us delve into all these bullet points where ML system can not be approved,

	- performance on disproportionate input set:-

		if any ML system that does very well on test set is not able to produce expected business metrics
		goals then it is not to be used in production. a common example in this case is a loan approval 
		system which is predicting very diffrerently with cast, gender, ethinicity. by no means this ML
		system is going to be in production as it exhibits a lot of bias around and hence not approved.
	
	- skewed data proportion:-
	
		specifically a rare class that holds true in a skewed data distribution eventually not going to 
		solve the problem where the challenge would be to predict well on rare class input. in a medical 
		diagnosis system any rare class input prediction result would be equally likely to that of majority
	        class prediction. well this is very weird, at life risk for any patient and no way this system 
		should be in production and hence not approved.

estiblish a baseline:-
======================
Any ML system in place will have to start with a baseline first to ensure that it uses prior baseline artifacts in 
order to improve upon. A baseline model will help improve further based on its prior performance as a toolkit.

considering our visual inspection example where ML system consumes several types of input such as good image ,
slanted image, blurr image and image with good resolution. These images are used to predict whether or not any 
given image is a new product or a damaged one. With subsequent model iterations you have come to a conclusion 
that different image type suffers from accuracy level. 

All types of input image accuracies will now cross-verified with a human level inspection to figure out degree of 
improvement. let us just say, using a blurr image model is giving accuracy around 83 % to that of 89 % human level 
accuracy. Remaining all checks looks more or less in prescribed accuracy level both from model and human level 
inspection point of view. it is so clear that using a baseline model as a rough version will keep focus shifted
to the area of improvement (improving blurr image quality) in need, and so it be. 

why baseline is required:-
==========================
generally any ML system used structured data or unstructured data to genetate prediction result. we as humans
evolved through a process to interpret unstuctured data more efficiently. that is why measuring model accuracy
with human level inspection could be a very good way to establish a baseline.

in contrast if any ML system uses giant structured data to generate prediction result then using a human level
inspection to define a baseline would not help that much cause of the fact that humans are not very good at
interpret huge amount of structured data.

to boil it down into more granular piece let us churn out few pointers that help us creating a robust baseline of
any model,

	- use human level inspection , mentioned as above.
	- use state-of-the-art implementation in open source
	- use a quick and dirty implementation ( using various references from point 2)
	- use performance of any older system ( use a pre built model accuracy to the starting point)

In nutshell baseline helps to identify what might be possible or impossible from model stand point. besides that
it also offers what are possible errors to be encountered,a.k.a irreducible error. 


getting started with ML model:-
===============================
we all know that building a model is a completely iterative process. as stated earlier process of modelling starts 
with data, hyperparameters to build a model, make it learnable in training over time and then  perform error analysis.
once we are satisfied with a good enough model and its performance then defined model can be taken for performace 
audit trails in order to make it production ready. More precisely building a model or even getting started with it
as the first step might help to iterate through the process a lot faster.

now the task is to how to get started with modelling. well to get started pay attentionto below pointers,
	
	- literature search:-

		the idea is to not get derailed by thinking latest trend, innovation and cutting edge technology, 
		instead spend some quality time to get literature of the use case or project. For instance spend 
		few days to collect similar use cases, its overview and gain momentum with a sound understaning.

	- find open source implementation:-
		
		after doing a descent amount of literature search, now search for any open source implementation
		if any. Finding a solution in many ways will help to get going quickly, if needed.

	- reasonable algorithm:-
		
		it is always recommended that instead of having a complex function with not so good data, a reasonable
		algorithm with quality data will outperform most often. so do not get carried away by the fancy stuff,
		that are used in latest conferences of ai community. of course knowledge is always enlighting. 

once modelling is started a quick question pops up in mind, shoud we consider looking for deployment constaints
when selecting a model. well the answer to this quite simple a yes or a no. let us see it as per case,

	- yes, consider deployment constraint:-
		
		ML system with a baseline established already should look for deployment constraints to build and
		deploy.

	- no, always an optional choice:-

		if baseline is not yet established, not sure this ML system will work or not or in question then
		ignore the idea of build and delploy. in this case the focus is to know what is possible
		in this project, that might help a lot to establish a  baseline.

finally when trying out a learning algorithm, it is prudent practice to perform all sanity checks. at first
always try to overfit a small amount of training data before training a larger or huge data set. In case of 
image classification a training example of 10 to 100 will be used in traing to build a model and test accuracy.
say if model accuracy is not upto the mark, then clearly using a million images from that distribution would not
be making sense. this will pave the path in a right direction rather than wasting a lot of time training a 
overfitted dataset.






 
		

















# MLOps_End_to_End
