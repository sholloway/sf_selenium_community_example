# Web Driver Cheatsheet

---

Tips and tricks for effective web scripting.

## Resources
* [Selenium Javascript Bindings JSDocs](https://selenium.dev/selenium/docs/api/javascript/module/selenium-webdriver/)

## JMeter/Selenium Considerations

The script is authored in Javascript which JMeter uses the Rhino Javascript engine to run.
Rhino and JMeter are both being ran by Java on a JVM instance. This in turn allows Java
classes to be leveraged by the test scripts. Additionally variables on the JVM can be
access by the scripts.

Varibles set by JMeter are accessed as JVM Varibles.

## Useful WebDriver Functions

| Command  | Purpose                   | Example                                          |
| -------- | ------------------------- | ------------------------------------------------ |
| WDS.log  | Log to the console        | WDS.log.info('SF URL: '+WDS.vars.get('SF_URL')); |
| WDS.vars | Get and Set JVM Variables | WDS.vars.get('SF_URL');                          |
| |Wait for the page.||

## Hello World

```javascript
```
