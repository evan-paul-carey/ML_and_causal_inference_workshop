# ML_and_causal_inference_workshop
This is the repository for files for a workshop on ML and Causal Inference.


## Files not yet posted

The finalized files are not yet available. I will update this text once they are posted and you will be able to download them from this repository. 

## Workshop Description

* What are high capacity predictive models (machine learning)? 
* How do they differ from classical multivariable inferential models? 
* How can I use them to make robust causal inference with observational data?

Understanding machine learning is essential to implementing modern causal inference in observational datasets – however, machine learning has not traditionally been taught in biostatistics or epidemiology graduate programs. This workshop will give an applied overview of the process of developing high-capacity predictive models (machine learning classification/regression models) with hands on applications using the R programming language. 

This workshop will be two hours in length. 

The first portion of the course will cover fundamental concepts in the context of healthcare data applications, including: 

* managing overfitting
* choosing performance metrics
* differentiating hyperparameters from model parameters
* implementing cross validation strategies to optimize hyperparameters
* comparing algorithm performance

Commonly used algorithms as well as a stacked ensemble model will be introduced. Model development will be demonstrated using R MLR3, an efficient framework for efficiently conducting in-memory model development. We will additionally demonstrate the use of h2o.ai through the R API, which enables automated machine learning (autoML) on large datasets. 

The second portion of the course will cover the intersection of high-capacity predictive model output and causal inference. This includes generation of propensity scores from these models (and subsequent use) as well as the prediction of counterfactual states. 

Attendees will learn the fundamentals of developing these ML models with the subsequent application of these techniques in the context of causal inference.

## Software used 

I will be demonstrating concepts using R, with a focus on the MLR3 packages and h2o.ai

You will be able to follow along without an R installation, but if you wish to run the code provided you will need the following: 

Install R from here:  
https://cran.rstudio.com/

Install RStudio from here:  
https://posit.co/download/rstudio-desktop/

Follow the install instructions for MLR3 from here:  
https://docs.h2o.ai/h2o/latest-stable/h2o-docs/downloading.html#install-in-r

Follow the install instructions for h2o here:  
https://docs.h2o.ai/h2o/latest-stable/h2o-docs/downloading.html#install-in-r


