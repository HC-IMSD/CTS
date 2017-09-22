_________________________________
Pentaho Transformations and Jobs
__________________________________

Installed libraries
--------------------

TODO: confirm if all needed, think the httpcore are not.
common-lang3-3.6.jar
ojdbc6.jar
okio-1.13.0.jar
okhttp-3.8.1.jar 
httpcore-ab-4.4.6.jar (not needed?)
httpcore-nio-4.4.6.jar (not needed?)
org.apache.httpcomponents.httpclient_4.5.3.jar

Common
--------

get_credentials - gets the access token
post_xml_file_cts - Calls the post web service to load an xml file. Uses java lib files

COUNTRY
- load_dpd_countries_from_csv -maps the DPD countries to the CTS countries. Filters countries that don't match. Now gets the DPD countries from prod DB.


LOC_STATE (country + region)
----------

dev_loc_state -creates country/ province  to CTS from Apotex company records
	-TODO redo this. Get all the provinces from DPD and create the records for them
	-TODO - replace the Javascript step with Java?




LOC_NAME (country_city)
----------

create_LOC_NAME_xmlData
	-Creates the City/Country records as a column (one record per row)
	TODO: Need to change from javascript step to Java. Will not handle extended character set.
	
create_LOC_NAME_file2
	-Creates the LOC_NAME xml file
	-TODO needs to be refactored to ensure xml files with 100 records only (see substance)
	-TODO change the text file output to a java implementation? Potential encoding issues?
	-TODO change the file path so it is in a special folder
load_LOC_NAME_to_cts	
	Loads LOC_NAME XML files to CTS
	TODO load multiple files from a path
	TODO Better error handling?
	
get_LOC_NAME_from_cts
	Gets all the LOC_NAME records from CTS
	
	
LOC_STATE
----------

	
	
	