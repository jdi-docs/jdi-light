---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - java
  - csharp
  - python  
  
toc_footers:
  - <a href='https://www.facebook.com/groups/jdi.framework/' target="_blank">Facebook</a>
  - <a href='https://github.com/jdi-testing/jdi-light' target="_blank">Java Github</a>
  - <a href='https://github.com/jdi-testing/jdi-light-csharp' target="_blank">C# Github</a>
  - <a href='https://join.skype.com/u2Cel0MWHkAO' target="_blank">Skype EN</a>
  - <a href='https://join.skype.com/clvyVvnZvWqc' target="_blank">Skype RU</a>
  - <a href='#'>Youtube</a>
  - <a href="mailto:roman.iovlev.jdi@gmail.com?Subject=JDI question" target="_blank">Send Mail</a>

includes:
  - introduction
  - tutorial
  - theory
  - faq
  - documentation

search: true
---

# JDI Light Framework
JDI Light is a powerful Test Automation Framework that helps to make your tests fast, sustainable and provides obvious and predictable test run results.

<font color="red">!!! ATTENTION: Only works properly with <strong>JDK 8</strong>. There may be some problems when using <strong>JDK 12</strong> or later.</font>

JDI Light powered by Selenium and has simple integration with Selenium based projects
![Allure Log](images/intro/allure-report-log.png)

# Highlights
- Has simple integration with any Selenium based project, which allows to increase overall project stability, add user action logs and enrich standard WebElement capabilities with new features in just minutes (TBD add Guide)
- Extends the Page Objects pattern with powerful UI Elements: Buttons, TextFields, Forms, Tables etc... ( TBD add good links to examples)
- Enables you to write stable and predictable tests that fail only because of business logic or layout changes. No more waits, thread sleeps and other flaky stuff.
- Increase your overall test execution speed, especially for complex cases, like searching big tables, dropdowns with hundreds elements or entering text comprised of thousands of lines.
- Get detailed logs and well-readable reports of all user actions with no additional effort.
- All UI elements have assertions/matchers powered by Hamcrest and a wait with expected condition during timeout.
- Easy integration with all modern Automation tools: CI (Jenkins, TC etc.), Logging (Log4j or any other slf4j based logs), Reporting (Allure or Report Portal); Browser/Device farms (Selenium Grid, Browser Stack, Selenoid etc.), Test Runners (TestNG, JUnit) etc.
