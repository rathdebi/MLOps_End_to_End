# MLOps_End_to_End
machine learning project lifecycle---

Many a times , very oftern once after tarining a model , the obvious ask would be to make
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
in accordance with the ML project deplyment following cases take into account mentioned below.
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


# MLOps_End_to_End
