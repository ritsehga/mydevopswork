.bar override property file for each target environment should be placed here.
File Name Pattern:
   <Product Name>-<Business Process Name>-<Client Code>-ACE-Configuration-<Target Environment>.properties

Examples:
	eCollection-Intimation-3044-ACE-Configuration-sit.properties
	eCollection-RemitterValidationCurrentAccount-RILX-ACE-Configuration-uat.properties
	eCollection-RemitterValidationIntermediaryAccount-ADAN-ACE-Configuration-prod.properties

Dev-Ops should ignore files that do not conform to the given naming convention.