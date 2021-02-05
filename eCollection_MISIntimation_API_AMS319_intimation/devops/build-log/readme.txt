Build logs go here. Each build should collate logs the following logs pertaining to each build / deployment.
1) mqsipackagebar: packaging the customized code.
2) mqsiapplybaroverride: overriding application properties 
3) mqsideploy: deploying .bar file to the target environment
4) jmeter: deployment verification tests 

For each build / deploy create a new log file under the "~/devops/build-log" with the following naming convention
	build-<build-timestamp>-<build id>-<target environment>.log

Example:
	build-20200228093055-32833-uat.log
				