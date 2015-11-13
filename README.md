# How to: Shorten Your Oozie Workflow Definitions

Blog Post: http://blog.cloudera.com/blog/2013/11/how-to-shorten-your-oozie-workflow-definitions


## Description

----
The worklow in the subwf-repeat dir is an example of using the subworkflow action to re-use the same action multiple times.  It's been adapted from a few of the examples included with Oozie.  
It doesn't do anything particularly useful, but you can see that in the workflow.xml we have two subworkflow actions.  The first one runs the mr-action.xml workflow and specifies an input and output directory.  The second one then takes the output from the first one and uses it as the input for running the mr-action.xml workflow to a new output dir.
You'll notice that the subworkflow action in workflow.xml is shorter than the mapreduce action in mr-action.xml.  This would be more noticable if the mapreduce action required more properties.  


## Building the Workflow

----
1. In pom.xml, set the "oozie.version" property to your version of Oozie; it should work with just about any version
1. Build the project: `mvn clean package assembly:single`

The workflow directory is now called "subwf-repeat" and is under the `target/Subworkflow-Repeat-1.0/` directory.  There is also a tarball of the same in `target/`


## Preparing the Workflow

----
1. Upload the "subwf-repeat" dir to your home directory in HDFS: `hadoop fs -put subwf-repeat subwf-repeat`
1. Adjust `subwf-repeat/job.properties` as necessary for your cluster (i.e. `jobTracker` and `nameNode`)


## Running the Workflow

----
1. Submit the workflow to Oozie: `oozie job -config subwf-repeat/job.properties -run`
