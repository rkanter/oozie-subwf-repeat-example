How to: Shorten Your Oozie Workflow Definitions
===============================================

Blog Post: http://TODO


== Description ==
The worklow in the subwf-repeat dir is an example of using the subworkflow action to re-use the same action multiple times.  It's been adapted from a few of the examples included with Oozie.  
It doesn't do anything particularly useful, but you can see that in the workflow.xml we have two subworkflow actions.  The first one runs the mr-action.xml workflow and specifies an input and output directory.  The second one then takes the output from the first one and uses it as the input for running the mr-action.xml workflow to a new output dir.
You'll notice that the subworkflow action in workflow.xml is shorter than the mapreduce action in mr-action.xml.  This would be more noticable if the mapreduce action required more properties.  


== Preparing the Workflow ==
1) Adjust subwf-repeat/job.properties as necessary
2) If not using CDH 4.4.0, replace subwf-repeat/lib/oozie-examples-3.3.2-cdh4.4.0.jar with the corresponding oozie-examples jar for your version of Oozie
3) Upload the "subwf-repeat" dir to your home directory in HDFS
    hadoop fs -put subwf-repeat subwf-repeat


== Running the Workflow ==
1) Submit the workflow to Oozie
    oozie job -config subwf-repeat/job.properties
