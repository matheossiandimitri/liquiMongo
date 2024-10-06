# Source

https://kristylgomes.medium.com/getting-started-guide-how-to-install-liquibase-and-run-operations-against-a-mongodb-database-18a890efa4b9

# Start Mongo DB

docker-compose up -d
MongiDB compass : https://www.mongodb.com/try/download/compass

# Liquibase

# Install
https://docs.liquibase.com/start/install/home.html

Download liquibase-4.29.2.zip

Next download (or you will have error when "liquibase status"):
liquibase-mongodb-4.29.2.jar
mongodb-driver-sync-5.2.0.jar
bson-5.2.0.jar
mongodb-driver-core-5.2.0.jar

Put them into liquibase-4.29.2/lib
Create path variable to liquibase-4.29.2 folder

# Questions

Test update before execution
Rollback
Migration
Property file:
	https://docs.liquibase.com/concepts/connections/creating-config-properties.html
Structure:
	https://docs.liquibase.com/concepts/bestpractices.html
		-> We recommend that you use an increasing numerical sequence that starts at 1
		-> 1 root changelogs

## Some doc

changeset = basic unit which contains Change Types
	- It is a best practice to specify only one type of change per changeset
	- https://docs.liquibase.com/concepts/changelogs/changeset.html
	- logicalFilePath attribute is required when moving or renaming changelogs to prevent Liquibase from redeploying the corresponding changesets
		* https://docs.liquibase.com/concepts/changelogs/attributes/logicalfilepath.html
	
Change Types = database-independent to update DB
	- CREATE/ADD/DROP Table Column, index, view, procedure, sequence
	- ADD/DROP default value, foreign key, not null, primary & unique key
	- some pro functionnalities needs $$
	- https://docs.liquibase.com/change-types/home.html
	
Changelog = multiple changesets

Master/Root Change Log = central file that references other change log files, acts as a roadmap for all the changes that need to be applied to the database, ensuring they are applied in the correct order.


DATABASECHANGELOG (DBCL) table
	- track which changesets have been run
	- table is auto created
	- filename should be a relative path	
	
Release notes: https://docs.liquibase.com/start/release-notes/liquibase-release-notes/home.html
