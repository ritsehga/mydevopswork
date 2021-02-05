This is where all scripts required to build this application should go.
Build scripts will know the nature of the application and everything needed to build an application 
	- Sourcing dependencies
	- Running tools / utilities to package & build the applications
	- Applying configurations

If .sh, run it in the target environment.
If .mqsc run it in the target environment using the following command
runmqsc -m <Target Queue Manager> < mqsc file name

Example: 
	runmqsc -m LQM.IXC < eCollection-ibm-mq.mqsc
