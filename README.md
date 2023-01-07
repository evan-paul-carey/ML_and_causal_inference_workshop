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

I will be demonstrating concepts using R, with a focus on the MLR3 packages and h2o.aiYou will be able to follow along without an R installation, but if you wish to run the code provided you will need the following:

Install R from here:  
https://cran.rstudio.com/

Install RStudio from here:

https://posit.co/download/rstudio-desktop/

I will be using DuckDB, MLR3, and H2O during this workshop. I have listed the links to these packages below, as well as an overall R scripts showing example installation at the end of this document.

The installation instructions for MLR3 are detailed at the website below:

https://mlr3.mlr-org.com/The h2o installation instructions are here:

https://docs.h2o.ai/h2o/latest-stable/h2o-docs/downloading.html#install-in-r

The DuckDB installation instructions are here:

https://duckdb.org/docs/installation/index

Below are the R commands I have compiled to install and check these different libraries: 

```
##################################################
## Installation script examples for ICHPS Workshop
##################################################

###### install duckDB #########
install.packages(c("DBI","duckdb"))
library("DBI")
con = dbConnect(duckdb::duckdb(), ":memory:")
dbWriteTable(con, "iris", iris)
dbGetQuery(con, 'SELECT "Species", MIN("Sepal.Width") FROM iris GROUP BY "Species"')

###### install mlr3 ###########
mlr3_package_list <-
  c('mlr3verse','mlr3pipelines','mlr3measures',
    'paradox','bbotk','mlr3misc','mlr3fselect',
    'mlr3hyperband','mlr3tuning','smotefamily','mlr3data',
    'mlr3tuningspaces','OpenML','future',
    "glmnet", "caret", "Hmisc", "AER", "mlbench",
    "kernlab","caTools", "randomForest", "MASS")
install.packages(mlr3_package_list)
## demo code to be sure mlr3 works:
library(mlr3)
# create learning task
task_penguins = as_task_classif(species ~ ., data = palmerpenguins::penguins)
task_penguins # if you see output here describing the task classification, it is working 

###### install h2o ############
## h2o requires JAVA JDK or JRE with JAVA_HOME set correctly (openJDK works here)
##  - install version (one of these): 17, 16, 15, 14, 13, 12, 11, 10, 9, 8
##  - you can use the MS link to install openJDK: https://www.microsoft.com/openjdk
##  - <Windows>: Ensure JAVA HOME is set corrrectly:  https://confluence.atlassian.com/doc/setting-the-java_home-variable-in-windows-8895.html
##  - <MAC>: Ensure JAVA HOME is set corrrectly: https://stackoverflow.com/questions/22842743/how-to-set-java-home-environment-variable-on-mac-os-x-10-9
## After this, install h2o
# The following two commands remove any previously installed H2O packages for R.
if ("package:h2o" %in% search()) { detach("package:h2o", unload=TRUE) }
if ("h2o" %in% rownames(installed.packages())) { remove.packages("h2o") }

# Next, we download packages that H2O depends on.
pkgs <- c("RCurl","jsonlite")
for (pkg in pkgs) {
  if (! (pkg %in% rownames(installed.packages()))) { install.packages(pkg) }
}

### Now we download, install and initialize the H2O package for R.
# If you have RTOOLS, you can build from source with this method:
# install from source, requires RTOOLS and build, but version will be newer
install.packages("h2o", type="source", repos=(c("http://h2o-release.s3.amazonaws.com/h2o/latest_stable_R")))

## if you do not have RTools, then install from CRAN (slightly older version, but you do not have to build!)
install.packages("h2o")
# Finally, let's load H2O and start up an H2O cluster to test if working 
library(h2o)
h2o.init()
## run demo to test
demo(h2o.glm)

```

