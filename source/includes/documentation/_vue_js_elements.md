## Vue.js elements

### Alerts

[Vuetify documentation page](https://vuetifyjs.com/en/components/alerts/)

- __Java__: _com.epam.jdi.light.vuetify.elements.common.Alert.java_

![Alerts example](../../images/vuetify/alerts.png)

```java
  @Test
  public void alertsWithPropsHaveProperCssProps(){
      redAlert.has().text("I'm an alert with a top border and red color");
      redAlert.has().css("background-color", Colors.RED_LIGHTEN_2.value());
      redAlert.has().cssClass("v-alert--border-top");
  }
```

For examples of usage see: [Custom vuetify alert example](https://github.com/jdi-testing/jdi-light/blob/3118-implement-alerts/jdi-light-vuetify-tests/src/main/java/io/github/com/custom/CustomAlert.java)
and [JDI vuetify page tests for alerts](https://github.com/jdi-testing/jdi-light/blob/3118-implement-alerts/jdi-light-vuetify-tests/src/test/java/io/github/epam/vuetify/tests/common/AlertsTests.java).
