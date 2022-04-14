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

# MLOps_End_to_End
