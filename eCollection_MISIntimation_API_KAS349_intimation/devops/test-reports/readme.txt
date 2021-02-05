This is where all build and build verification reports go. Each build / DevOps cycle should create a new folder for the generated log.
The folder should be named as under
	 test_report-<build-timestamp>-<build id>-<target environment>.txt

The build timestamp should be in yyyyMMdd-HHmmss format.
Target environments will be sit / uat / prod.

Example:
	20200119-214000-37272-uat
