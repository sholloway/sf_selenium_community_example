# Salesforce Lightning Community Selenium Example

---

This project demonstrates how to test the Salesforce Lightning UX and a hosted
Lightning Community with Selenium.

## Demonstrations

### Salesforce Lightning UX

- [ ] Login into Salesforce.
- [ ] Open a Lightning App.
- [ ] Search for a record via the global search.
- [ ] Navigate Lightning Console Tabs

### Salesforce Lightning Community

- [ ] Navigate to a public page.
- [ ] Search for a knowledge article.
- [ ] Log a request/case/ticket.

## Getting Started

### Project Dependencies

- NPM and Node.js
- The Salesforce CLI
- Apache JMeter
- Apache JMeter [Web Driver Plugin](https://www.blazemeter.com/blog/jmeter-webdriver-sampler/)
- The Firefox Gecko Driver `brew install geckodriver`

### Setup

1. Install dependendencies.

```shell
npm install
```

2. Deploy the Scratch Org

```shell
npm run scratch
```

3. Setup the Lightning Community in the Scratch Org
   A. Open the Org: `sfdx force:org:open`
   B. Publish the Community:
   - Setup -> All Communities -> Click the _Builder_ link for the help_center community.
   - Click the _Publish_ link in the upper right hand corner.
You should get an email that the site has been published. Grab the URL for the community. 
We need if to point the tests at.

### Setting Up JMeter to Run Selenum Tests

1. Open JMeter.
2. Options -> Plugin Manager
3. Install the _Selenium/Web Driver Support_ plugin.
4. Click _Apply Changes and Restart JMeter_.

### Running The Tests

The load tests are implemented by combining Selenium Web Driver with JMeter.
When running the tests, you must provide the URL for the community. This is 
different every time a new scratch org is provisioned.

JMeter can be ran in GUI mode or headless via the terminal. When ran from the terminal
it can generate a web dashboard of test results. The below snippet demonstrates how to do this.

The tests can be ran with the below command.

```shell
jmeter -n \
  -t ./jmeter_tests/HelloWorldRestTests.jmx \
  -Jsf_url=<the community url>
  -l results.csv \
  -e -o ./report

# Open the report
cd report
open index.html

# you can also run the test, output the results to a CSV file and then 
# generate the HTML report from the file.

jmeter -g results.csv -o ./report

https://sandbox-agility-efficiency-2850-dev--170268109f8.cs78.force.com/help/s/
```

## Resources
[JMeter Web Driver Plugin Docs](https://jmeter-plugins.org/wiki/WebDriverTutorial/)
[JMeter Web Driver Sampler Docs](https://jmeter-plugins.org/wiki/WebDriverSampler/)
[Explaination about the Gecko Driver Error](https://stackoverflow.com/questions/38676719/selenium-using-java-the-path-to-the-driver-executable-must-be-set-by-the-webdr)
