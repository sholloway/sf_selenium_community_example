# Running the Rest Examples
- - -

## Authenticating a REST Endpoint
Authentication can be done in two way. Via a Session ID or with OAuth 2.0.

## URL Format
https://<instance>.salesforce.com/services/apexrest/<packageNamespace>/<MyMethod>/

## Data Access Considerations
https://developer.salesforce.com/docs/atlas.en-us.apexcode.meta/apexcode/apex_rest_exposing_data.htm

## Setting up the Tests to Run
Every time a new scratch org is created, the tests must be updated to use the new 
Salesforce domain and an auth token must be grabbed from the Salesforce CLI.
These can then be used to update the JMeter properties sf_domain and auth_token.
Use the auth helper script to simplify this.
```shell
# First source the script
source ./scripts/bash/auth_helper.sh

# then run the helper function
doItAll testing_example
```

## Running the Load Test and Generating HTML Reports
JMeter can be ran in GUI mode or headless via the terminal. When ran from the terminal
it can generate a web dashboard of test results. The below snippet demonstrates how to do this.

```shell
# Assuming the terminal is in the directory of where the jmeter test plan is.
jmeter -n -t ./HelloWorldRestTests.jmx -l results.csv -e -o ./report

# Open the report
cd report
open index.html

# you can also run the test, output the results to a CSV file and then 
# generate the HTML report from the file.

jmeter -g results.csv -o ./report
```

## Resources
* [Salesforce REST Endpoint Docs](https://developer.salesforce.com/docs/atlas.en-us.apexcode.meta/apexcode/apex_rest.htm)
* [REST Example with Session ID](https://developer.salesforce.com/docs/atlas.en-us.apexcode.meta/apexcode/apex_rest_code_sample_basic.htm)
* [JMeter Docs](https://jmeter.apache.org/)
* [JMeter Tutorial Videos](https://www.youtube.com/playlist?list=PLhW3qG5bs-L-zox1h3eIL7CZh5zJmci4c)
* [JMeter Plugins](https://jmeter-plugins.org/)
* [BeanShell Scripting](https://jmeter.apache.org/usermanual/best-practices.html#bsh_scripting)
* [Using Groovy in Test Plans](https://www.blazemeter.com/blog/writing-jmeter-functions-in-groovy/)