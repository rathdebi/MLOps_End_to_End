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


error analysis of model:-
=========================
the first time you build any model will not hit the right performance mark as we discussed. In another words
you can not guarantee that it will not work from the first time. Being an iterative process by definition, ML 
modelling phase would need to pass throough error analysis phase to produce desired results, and so it be. So,
then doing a proper error analysis will become the heart of ML modelling process by letting us know what is the
best way to use time so as to improve modelling performance.

let us take one example of speech recognition to illustrate error analysis. once after model returned out
some predictions any one can take a handful number of examples like 100 to compare level of predictions. In
first case you noticed that the word "I went to village" is predicted as "I wanna to village" could be due to
tag "external noise". In another set of example of "Please return back" is predicted as "plea return back" , looks
almost identical still some error with a tag "low bandwidth". With these two set of examples and then running all
examples through a human level inspection will definitely hint towards a possible new tag to be created or to find
a new tag that better fits any of these input prediction level. in simpler terms an example with "external noise" tag
can occur due to a "low bandwidth" tag or any new tag like "people noise". This analysis will help us identify what
are possible tags that are more worthy of creating such errors and thus put more attention to those errors.

As known previously, ML modelling is a completely iterative process, deploying a model is an iterative process,and 
quite not so surprise to say that error analysis is also an iterative process. 

iterative process of error analysis:-
=====================================
during error analysis phase, one must inspect few set of examples to propose new tags that might be used iteratively
to improve upon. 

referring to visual inspection example,

	- defining new labels to product ( scratched, dent)
	- image properties ( blurry,dark, light)
	- other data property ( product model, factory/manufacturing unit)


useful metrics for each tag:-
=============================
in order to perform a better error analysis process it is essential to find what fraction of errors that tag
consitutes. similiarly another check would be to find out how many data points were misclassified or mislabelled
with that tag. On the same note out of all data how many data points were having that same tag. Finally is there 
any room of improvement on all data with those tag. these specific questions will help preparing a more human level
inspection on data to better size and improve upon accordingly. these insightful task tells us that creating 
specific tags will not only identify different segments in data but also ask questions on what to priorotize working upon.


using tags that are relevant to segment data properly will definitely set the context of what work to priorotize. let us
set those tick mark as mentioend below,
	
	- with defined tags as per our visual inspection example will identify exact tags that needs attention to improve
          at first. for instance tags with a "blurry image" will differ from human level inspection prediction gap will be
	  in prime focus to improve and thus improving an overall accuracy of model.

	- other focus point would be to revisit what percentage of data falls in that defined tag with human level inspection
	  prediction gap to that of model and tweak it accordingly so as to size a quality improvement that of earlier iteration.
	
	- in simpler terms to understand , say that a "blurry image" has attained 85 % accuracy from model perediction which is 
	  is validated against human level inspection prediction as 93%. Adding on the total data that corresponds to a "blurry
	  image" tag is around 60 %. This implies that with a human level inspection prediction gap of 8 % (93% - 85%) the model is
	  going to size with a better accuracy of 4.8 % is the next iteration subject to improve upon "blurry image" tag.

To make it more easy to understand here is a quick summary,
	
	- so in general, one should always look for any room of improvement , if any, there is always

	- frequency of tag or category that appears, find required specific about it, if any, always good

	- if there exists any way, do improve upon accuracy that tag or category, put that on priority

	- for instance in case of visual inspection example, a strong case would be to improve accuracies
	  of "blurry image" tag due to the phone and image quality it renders.
	  
	  

skewed dataset:-
================
in general , dataset that are very far from postive to negative case apart from being 50% in both or relatively equal,
are called as skewed dataset. being able to make modelling look better urge you to handle skewed data in detail. Let
us say a manufacturing unit produces product out of which 99 % are no defect(Y=0) and 1% or less are tagged as defecttive
pieces (Y=1). Then a simple print("0") would do the same task of a model that always predicts Y=0. In this specific
case model does well on accuracy but did not generalize well when there is a case of "defective piece", which is true
as we have 1 % product with defetctice pieces. That means a defective piece is predicted as non defective piece by
the model that is trained on skewed data and so often this prediction can go horribly wrong.

let us navigate through this issue to derive a better understanding using a confusion matrix.

considering the same example let us say in total we collect 1000 sample prediction result. a confusion matrix
is designed on both actual lables and prediction on those labels. it looks like a grid of 2*2 axis having 4 celss
where rows represents prediction and column represents actuals. A confusion matrix will have four specific types of 
values mentioned as below,
	
	- TRUE POSITIVE ( actual 1 and model predicted also 1)
	- TRUE NEGATIVE ( acual 0 and model predicted also 0)
	- FALSE POSTIVE ( actual 0 and model predicted as 1)
	- FALSE NEGATIVE ( actual 1 and model predicted as 0)

Total number of examples in any case would sum upto values present in each of the 4 cells. For instance let us say
905 records from total obs. are actually non detective product and model also predicted the same (TN). Similarly
let us say that 68 obs. are actually defective product and model also predicted the same (TP). Besides that 18 obs.
which are wrongly classified as negative but those are actually postive (FN). And likewise, there are 9 obs.
which are wrongly classified as positive but  those are actually negative (FP). 

evaluation metrics using confusion matrix:-
===========================================

The precision of model in this case ,
	
	P = TP/(TP+FP) = 68/(68+9) = 88.3 %

it means that out of all predictions as 1's (positive) how many of them are actually 1's

The recall of model in this case ,

	R = TP/(TP + FN) = 68/(68+18) = 79.1 %

it means that out of all actuals as 1's (positive) how many of them are predicted as 1's

It turns out that the use precision and recall looks more convienient then that of overall accuracy.

Any learning algorithm that always predicts 0 no matter what input example is given meaning that FP and TP
does not have any prediction at all. In this case Precision can not be calculated and recall would become 0
based on the formula given above. So a model that is able to produce good precision might not be good with recall 
score. That is the reason why we should be looking at another parameter that in a way combine both precision and 
recall equally, a.k.a F1 score.


	F1 score = 2/(1/P + 1/R) 

It means model that has a high precision and low recall would definitely get adjusted using F1 score and 
can be used in more efficiently to select a better model from a group of models. Essentially F1 score will help
business to identify right set of evaluation metrics in model iterattion instead just looking at precision and 
recall. more precisely to say , if you have multi class classification problem using F1 score will give a single
number metric to select the best model with differenet classes. More importantly you can pick the class with high F1
score and priorotize that class to meet human level performance.


audit performance:-
===================
even when your model is doing all good with accuracy, F1 score and all it is worth doing performance audit
that could save a lot of time during post deployment task. By enlarge a ML system follows an iterative process
to develop a good learning algorithm. 

Here is a framework to double check your system on accuracy,fairness/bias and other problems that might be a blocker going forward.
	
	- brainstom the ways subject to which your system might go wrong
	- does your algorithm perform well on different subsets ( dev/validation/test)
	- how common are certain FP and FN , get a better grab on it
	- performance on rare classes

Afterwards, establish metrics to assess performance against these issues on differenet sets of data. It is always
a good practice to inform business/product owner aware (buy-in) of all these issues prior, and accordingly do the 
necessary change/update in system before deploying it to production.

example:-
==========
let us discuss about our visual inspection use case on these issues,

	- what is the accuracy of model on different images (blurry,high/low resolution and etc.)
	- accuracy on different kinds of dpi level of image
	- any relevance of image orientation

establish metrics to assess performance against these issues,
	
	- mean accuracy among all kinds of images
	- mean accuracy among all kinds of dpi level images
	- relevance of any output that is not accepted (wrong)

Having said all these performance audit can be really shaping your system to a desirable state by removing out
all noise and inconsistencies before time. it is seen that rather than one person doing the brainstorming session performance 
auditing process should be conducted within the team to navigate through these issues and thus making system more 
efficient and robust with its prediction power.


data centric ai development:-
=============================
in the rise of ai one of the most crucial aspect is to build a model that possess very good prediction power.
to achieve that supremacy there are two ways one needs to follow. The first one is model centric developement 
meaning that data is fixed and model is tuned with best possible way to make things happen. in contrast data 
centric approach takes model as fixed and work on data side to bring that shift. eventually you will notice that 
working with the later one (data centric) will lead you to develop a better system in place.

well, this is due to the fact that running a model on the same data tends to overfit once it attains a level of 
competence. for instance using a complex neural netwrok with several tweaks can increase accuracy of model ever 
so slightly, no denial. perhaps a better counter intuitive approach would be to know specifics of data, enrich it
 with right set of attributes such that model will consume high quality data from its previous run. The possible 
outcome will be a significant increase in accuracy as we would have desired for,so it be.


data augmentation:-
====================
a concept of data augmentation can improve performance of a learning algorithm. any ML system ever built will pass 
through series of performance audit to meet human level expectation and improve upon. During this process model
performance will get compared with human level performance. From performance across all such tags or categories 
available in data one thing is clear that there is always a room for improvement. say that a tag or category that 
is not making good performance can be adjusted with more quality data so as to improve. this is so true in case of 
unstructured data and thus a quality improvement will guarantee significant  improvement in respective other tag or 
category as well courtesy of data augmentation technique. needless to say whether you apply data augmentation or 
collect more data around, performance of your model would eventually tend to be a better function of all spaced tags or 
categories as input.


data augmentation can be an efficienet way to help improve performance of your learning algorithm by adding
more synthetic data as input. while carrying out data augmentation step there are a lot things to look after like
what are the parameters, how to design the augmentation process and what not.

let us discuss about few key pointers that will guide us through the best practices.

	- create realistic examples where model will perform poor than human level inspection
	- X->Y mapping should be expected (using synthetic data can human recognize output)
	- does the algorithm work poorly on this ?

if you put these as a checklist at present and try to retrain learning algorithm with new set of synthesized 
data then higher chances are that the learning algorithm will perform well.

to understand it in a easy way let us consider visual inspection,
	
	1- say we added different types of background images (using tools and techniques)
	2- it is to ensure that we added images where a scratch mark can be visible (by human)
	3- if not , then find a way or prepare data accordingly so that product scratch mark can be spotted
	4- try to verify human level performance on synthesized data, if yes, then model eventually does well

you have heard saying model iteration loop and similarly its like data iteration loop can be used as well in 
data centric ai development. The loop will start with adding/modifying data, training and then performing error 
analysis in a cycle until we find a better learning algorithm subject to condition that we fixed model constraints.
this will ensure that it is worth using data augmentation ( synthetic data) not only performance is improved but 
internally saves a lot of time tweaking models and hyperparameters.


adding more data:-
==================
often times it is advised that one should generate good amount of data using data augmentation process, if required,
to ensure generative algorithm has enough data to train. well this will create a new problem out of thin air,and to
be specific it is about data distribution. almost all machine learning algorithm uses a same distribution of dev and
validation/test to go along. with data augmentation you are adding a lot of new examples to the dev set which will have
a different data distribution than validation/test set. Honestly the answer to this is a NO.

let us iterate through to make a better understanding. say if,

	- you are working on a unstructured data problem
	- your learning algorithm is large (low bias, a complex neural network) 
	- with a clear mapping of X->Y ( a human can predict easily on any given input X)

Then in this case adding more of synthetic data rarely hurts performance.
	
	- say earlier you have 20 % of data labelled with a specific tag
	- using data augmentation it got increased to 50% for that tag
	- now as long as our model is large with a clear mapping X->Y
	- performance will improve not only for that tag but for other tags as well

In contrast if you are adding data that does not define a clear mapping, then performance might be impacted badly.
for instance adding images where a human can not surely tell that whether or not there is a scratch mark in product
then algorithm find it very difficult to learn as well, as it is not sure about it. 


adding features:-
=================
unlike unstructured data creating synthetic new data is very difficult as in case of structured data. but there is 
another way to tackle this by creating meaningful features instead adding more data points. let us take one example
to make it clear,
	
	- say a neural network uses people info. and restaurats nearby to recommend products
	- let us say for vegetarians the model predicts non-veg products as well, not so good
	- in this case using data augmentation people and restaurants info can not be created
	- rather we can think of possible features like,

		- food preferences (veg or non-veg) given by restaurant as a new feature
		- vegetarian food options available in a restaurant

As product team needs to improve performance, ML team needs to ask all these relevant questions on how these features
can help make better decisions. over these years product recommendations are being given basis on two different 
algorithms known as collaborative filtering and content based filtering.
	
	- collborative filtering focus on users information
	- content based filtering focus on user, preferences and all other information

the advantage of content based filtering is to effectively recommend prodcucts even if it is not liked
by users or it is not used at all unlike collaborative filtering that takes users association into account.


as structured data accounts for adding new features and thus data iteration loop in this case will eventually
iterate through add/modify(features) , model, train and error analysis phase. error analysis in case of structured 
data would be very difficult if we do not have a very good baseline. a good baseline is difficult as humans can not 
easily predict well. the only way to perform error analysis is to collect feedback and competitors info that provides
a way to add more creative features.


experiment tracking:-
=====================

now that we are working iteratively to improve learning algorithm one thing that stands out is to record 
experiement tracking. having a better tracking system in place helps us in finding set of models and hyperparameters
that fits well on data. experiment tracking will be in place to track,

	- algorithm versioning
	- data used
	- hyperparameters
	- output/results

several tools and techniques are available to keep a tab on, however a simple text file can be used to save
data synthesis steps and algorithm tweak or data drift/model drift and error analysis. this will help us navigate 
through and back track model run logistics at times of need, and thus save a lot of time. experiment tracking
tools like sagemaker studio, azure ml studio and tensrflow can automate this process to a large extent by providing
a detail report of respective model run. do remember that a experiment tracking system is a must to have and remember
that it is going to help find our what models you have selected, what data analyis you have performed in oder to
replicate  results going forward.


big data to good data:-
==========================
we have seen all about data iteration loop in detail. but then there is this concept of big data to good data
as a shift. in  modern ai era consistently getting high quality data in all phases of ML project has become utmost
priority. 

Now what is good data ? let us deep dive into it,

	- covers importnat cases meaning that X's coverage is good
	- defined consistently meaning Y's unambigious
	- receive timely feedback from production that covers data drift and model drift
	- sized appropriately
	


data definition:-
=================
it is so true to say that data sets the tone for model training and evaluation process. however, data definition 
can be a really hard task depending upon the strategy that you follow to collect data. let us consider our visual
inspection example which requires a lot of images and so a couple labllers collected data and labelled it.any image 
that contains a clear scratch mark spots can be tagged as a single boundix box whereas the same can be tagged as 
differently using two bounding box, one for scratch mark and other one is for spots. between these data labellers 
probably the one who has does it with more scrunity and sanity checks strikes a mark on data definition. this process
examines that if you consistently labelled the data then learning algorithm is going to perform well on future. more
importantly data stage is all set to create correct data  and labels (X's,Y's), organize data which will be
used in modelling phase to produce good results.

common data defintion questions to be asked,

	- what are my X's? high resolution, low resolution image
	- what features need to be included? a collective effort
	- what should be target lable Y? consisent labelling 
































 




 






 


 






 
		

















# MLOps_End_to_End
