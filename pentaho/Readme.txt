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
_________

get_credentials - gets the access token
post_xml_file_cts - Calls the post web service to load an xml file. Uses java lib files

COUNTRY
-------
- load_dpd_countries_from_csv -maps the DPD countries to the CTS countries. Filters countries that don't match. Now gets the DPD countries from prod DB.


LOC_STATE (country + region)
_________

dev_loc_state 
--------------
	-creates country/ province  to CTS from Apotex company records
	-TODO redo this. Get all the provinces from DPD and create the records for them
	-TODO - replace the Javascript step with Java?

create_LOC_STATE_file
-----------------------
	- creates the LOC_STATE xml file
	- TODO: make it handle batches of 100
	-TODO :change text file save to java custom object? Encoding issues?
	
load_LOC_STATE_to_cts
-----------------------
	-loads as LOC_STATE xml file to CTS
	-TODO: refactor to handle multiple files


LOC_NAME (country_city)
_______________________

create_LOC_NAME_xmlData
------------------------
	-Creates the City/Country records as a column (one record per row)
	TODO: Need to change from javascript step to Java. Will not handle extended character set.
	
create_LOC_NAME_file2
-----------------------
	-Creates the LOC_NAME xml file
	-TODO: needs to be refactored to ensure xml files with 100 records only (see substance)
	-TODO: change the text file output to a java implementation? Potential encoding issues?
	-TODO: change the file path so it is in a special folder
load_LOC_NAME_to_cts	
-------------------
	Loads LOC_NAME XML files to CTS
	-TODO: load multiple files from a path
	-TODO: Better error handling?
	
get_LOC_NAME_from_cts
-----------------------
	Gets all the LOC_NAME records from CTS
	

SUS_SUBISIDIARY (company + address)
___________________________________

create_SUS_SUBSIDIARY_xmlData
-------------------------------

- creates the Company xml file. Likely this will have to change based on refactoring requirements for IDMP compliance
- TODO: refactor so makes batches of 100 files

load_SUS_SUBSIDIARY_to_cts
-------------------------------
- loads a single xml file for subsidiary to cts.
- transforms the data from xml to 
- TODO: allow ability to load multiple files to CTS
- 

SUS_PERSON
______________

Gets person data from the selected companys
- TODO:  This will need to be redone after the New Lorenz data model has been deployed (April 2018).

create_SUS_PERSON_xmlData
--------------------------
- creates the person xml data records. Divides into groups of 100
- attaches one person to a company record

create_SUS_PERSON_file
------------------------
- creates the person xml file. Adds the header and body decoration tags

Load SUS_PERSON to CTS
------------------------
- Job to load person xml files to cts. Will handle multiple files. Calls appropriate transformations

Get XML Filenames
------------------

- Gets all the file names from the SUS_PERSON
- TODO: needs to be renamed since specific to person OR genericized


SUB_REFSOURCE
_______________
Creates the reference source data record. Required for substance aliases

create_ref_source_xml
------------------------
-Creates the REF Source xml fragment (content). For now hard coding the reference source as DPD. External Key is set to DPD

save Sub_REFSOURCE to xml (job)
--------------------------------
-Creates the xml files for REFSOURCE and save the xml files to the file system

Create_SUB_REFSOURCE
---------------------
-Creates the REFSOURCE xml file, adds the header information. -Saves to filesystem

Load SUB_REFSOURCE to cTS (job)
--------------------------------
Loads the SUB_REFSOURCE files to the cts system




SUB_SUBSTANCE
_______________________
-Creates the substance XML records and loads them to cts. Gets teh necessary record dependencies

Save SUB_SUBSTANCE to XML files (job)
-------------------------------
- Gets the xml content and saves the appropriate xml files. Each input row represents 100 content entries to comply to the schema

create_SUB_SUBSTANCE_xml
---------------------------

-creates XML Content for substances with aliases, CAS, Comments, french name. Splits into recordSets of 100
-gets the language key from CTS to apply to the translations

create_SUB_SUBSTANCE_file
--------------------------
-Adds the header, content and outputs the xml to the filesystem


Load Substance XML to CTS (job)
-------------------------
-Loads xml files for substance to  CTS, usese the postAPI transaformation

Get Substance Filenames and credentials.ktr
--------------------------------------------
I-n the specified folder, gets the filenames (xml) and the access token from CTS


get_DOC_LANGUAGE_from_cts
----------------------------
- Gets  all the languages in CTS and the internal ids.  


 



 
	



	
	
	