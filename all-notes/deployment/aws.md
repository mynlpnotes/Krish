# AWS

* Services 🡪 Compute 🡪 Elastic Beanstalk
* Create new environment
  * Application Name
  * Platform 🡪 Python
  * Branch 🡪 Python 3.7
  * Application Code 🡪 Sample application
* Create Code Pipeline:
  * Create new pipeline
  * Step 1 🡪 Pipeline Name
  * Step 2 🡪 Source Provider 🡪 Github Version 2, Connection Name 🡪 Connect to github
  * Choose repository, Branch Name
  * Start the pipeline on code changes
  * CodePipeline default
  * Step 3 🡪 Build stage 🡪 Skip
  * Step 4 🡪 Deploy stage
  * Deploy provided 🡪 AWS Beanstalk
  * Region
  * Application Name
  * Environment Name
  * Step 5 🡪 Review 🡪 Create Pipeline
* In environment we will get the app link
