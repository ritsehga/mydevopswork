This folder will contain 4 files listed below. Each file will have an git URI to pull the dependencies from.

dependencies-shared-lib-ext.txt
dependencies-shared-lib-ixc.txt
dependencies-static-lib-ext.txt
dependencies-static-lib-ixc.txt

If the file is not present or is empty, do not take any action and proceed with the next file.

Dependency types:

	- shared-lib-ext: 	Library (.jar) files not custom built for ICICI Xpress Connect but
									meant to be shared across IBM ACE integration applications (.bar deployments). 
									Typically these would be libraries from open-source projects (e.g. JSON 
									parser library Jackson, JDBC/ODBC drivers etc.).
	
	- shared-lib-ixc: 	Library (.jar etc.) files custom built for ICICI Xpress Connect and shared
									across IBM ACE integration applications (.bar deployments).
	
	- static-lib-ext:		Library (.jar) files not custom built for ICICI Xpress Connect but local to 
									the IBM ACE application. 
									
	- static-lib-ixc: 		Library files custom built for ICICI Xpress Connect and local to the 
									IBM ACE application.

Rules to deploy dependencies:
shared-lib-ext: 	Manual deployment  or through IBM ACE image extension. [29-Feb-2020]: Deferred for now.
shared-lib-ixc: 		Check if the shared library is deployed on the IBM ACE server. 
								If no, then deploy using mqsideploy in the manner similar to deploying the main application (.bar). 
								If yes, manual deployment or through IBM ACE image extension. [29-Feb-2020]: Deferred for now.
static-lib-ext:		Deploy to "shared-classes". Will need pod restart. [29-Feb-2020]: Deferred for now.
static-lib-ixc: 		Use -l option with mqsipackagebar when packaging the application.