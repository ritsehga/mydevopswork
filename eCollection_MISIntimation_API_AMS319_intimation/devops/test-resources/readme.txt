This is where the build verification test scripts and everything needed to run those will go. Each API service would 
have a separate test script to validate if the deployment succeeded. The test script would do the following.

1) Line up the test data, pre-process if needed. 
2) Execute the main script.
	2.0) Perform pre-test setup steps (optional)
	2.1) Use each test data record and invoke the API (main application endpoint).
	2.2) Collect the API response.
	2.3) Validate (Assert) the API response.
	2.4) Perform post-test cleanup / validation / data-collation ("tear down") steps (optional).
3) Collect test logs, perform other validations that are required, but not a part of the main script.	

There could be a single script configured such that it would run test-cases specific to the build. Or there could be 
build specific scripts.

JMeter test script command: 
Refer to readme-jmeter-properties.txt for JMeter script properties.

Option 1:
				jmeter -n -t <JMeter JMX Script File Name> -l <Log File Name> -J<Property Name>=<Property Value>
				
				Example:

					jmeter -n -t eCollection-jmeter-build-verification.jmx -l log.jtl 
						-JClientCode=ADAN
						-JSubscriptionProductName=eCollection
						-JTotalUserCount=1
						-JUserRampUpTime=1
						-JTestDataFileName=ecollection-testdata-ADAN-sit.csv
						-JRecordCount=10
						-JTestReportFileName=ecollection-testdata-ADAN-sit-202008152131.xml
					
Option 2:
				jmeter -n -t <JMeter JMX Script File Name> -l <Log File Name> -p <JMeter Properties File Name>

				Example:

					jmeter -n -t eCollection-jmeter-build-verification.jmx -l log.jtl -p jmeter-ecollection-example.properties


Difference in options 1 and 2 is in the way JMeter properties are supplied to JMeter. 
In case of option 1, the each property is supplied to JMeter through the -J option where as in case of option 2, 
the properties are bundled in a properties file and the filename is passed to JMeter using -p option.

[EOF]