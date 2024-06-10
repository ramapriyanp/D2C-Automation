## **# playwright NI framework - SF UI**

#### **_NOTE_**: By Default this framework is using "src/test/resources/uat.properties" prop file.

1. To change prop file, add in the CLI command property, e.g.:

**_-DBUNDLE_TYPE=preprod_**


To run tests, create a file inside "nisfappui/src/test/resources/" folder with a name "uat.properties" and add rows:

- BASE_URL= Sandbox url
- USER_EMAIL= login email
- USER_PASSWORD= password
- USER_PASSWORD_WRONG=<some wrong numbers, required for tests>.


2. This framework is using mvn wrapper (mvn -N wrapper:wrapper -Dmaven=3.8.5). To run command via maven, use "mvn"
   instead of "./mvnw".


3. TestNG files are located here: "nisfappui/src/test/resources/testNgSuites"



4. To run module tests use "-pl" option:

`mvn clean test  -Dtest=AuthenticationTest -Dthread.count=3 -pl nid2cui`

OR 


`./mvnw clean test -DsuiteXmlFile="PosNgAppCreationSmoke.xml" -pl nisfappui`

=================================================================================================================

#### **--->>> To run TestNG suite with parameters  (e.g. BROWSER_TYPE=firefox) - run command:**

`./mvnw -DBROWSER_TYPE=chrome -DTRACE_FLAG=false -DsuiteXmlFile="PosNgAppCreationSmoke.xml"  clean test`
`mvn clean test -DBROWSER_TYPE=firefox -DsuiteXmlFile="CreateApp.xml"`

OR

`./mvnw -DBROWSER_TYPE=msedge -DTRACE_FLAG=true -DsuiteXmlFile="EcomAppCreationSmoke.xml"  clean test"`

=================================================================================================================

#### --->>> **_To run test report Allure - run command:_**

`mvn allure:serve`


`mvn allure:generate`


=================================================================================================================

#### --->>> **_To run PlayWright trace report zip archive (change .zip archive name) - run command:_**

`mvn exec:java -e -D exec.mainClass=com.microsoft.playwright.CLI -D exec.args="show-trace traces/createSoftPosApplicationTest.zip"`

=================================================================================================================

#### --->>> **_To run tests via Docker - run commands:_**

1. Run docker compose file (and open after that http://localhost:4444/ui/index.html#/):

`docker compose up`

2. Export PlayWright variable to the project:

export SELENIUM_REMOTE_URL=http://localhost:4444
export PLAYWRIGHT_SKIP_BROWSER_DOWNLOAD=1

OR

set SELENIUM_REMOTE_URL=http://localhost:4444
set PLAYWRIGHT_SKIP_BROWSER_DOWNLOAD=1

and check the export:

echo %SELENIUM_REMOTE_URL%

OR

echo $SELENIUM_REMOTE_URL

3. Run tests for chrome:

`mvnw -DBROWSER_TYPE=chrome -DsuiteXmlFile="PosNgAppCreationSmoke.xml"  clean test`

4. Check video record or test execution via UI http://localhost:4444/ui/index.html#/ (default UI pass: "secret")

OR

open ./logs/chrome folder with video



## **# playwright NI framework - SOB API**

#### **_NOTE_**: By Default this framework is using "src/test/resources/uatApiConfig.properties" prop file.

1. To change prop file, add in the CLI command property, e.g.:

**-DAPI_CONF_TYPE=XXXApiConfig.properties**


To run tests, create a file inside "nisobapi/src/test/resources/" folder with a name "uatApiConfig.properties" and add rows:

- password=
- grant_type=password
- client_secret=
- client_id=
- username=

Credentials info here: https://networkinternational.atlassian.net/wiki/spaces/NAACE/pages/2590736431/Integration+users

2. This framework is using mvn wrapper (mvn -N wrapper:wrapper -Dmaven=3.8.5). To run command via maven, use "mvn"
   instead of "./mvnw".


3. TestNG files are located here: "nisobapi/src/test/resources/testNgSuites"


=================================================================================================================

#### --->>> **_To run SOB Application creation API (POST request) and Get application info API (GET request), run:_**

`./mvnw -DsuiteXmlFile="SOBAppApiTest.xml"  clean test`

=================================================================================================================

#### --->>> **_To run test report Allure - run command:_**

`mvn allure:serve`

=================================================================================================================