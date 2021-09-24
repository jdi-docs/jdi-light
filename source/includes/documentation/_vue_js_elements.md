## Vue.js elements

### Subheaders

```java
  @Test
  public void insetTest(){
      insetSubheader.is().displayed();
      insetSubheader.is().lightTheme();
      insetSubheader.is().inset();
      insetSubheader.is().text("Subheader");
  }
```

Subheader is located in the following class:

- __Java__: _com.epam.jdi.light.vuetify.elements.common.Subheader.java_
 
[Vuetify documentation page](https://vuetifyjs.com/en/components/subheaders/)

![Subheaders example](../../images/vuetify/subheader.png)

The Subheader component is used to separate sections of lists.

[Here you can find Subheaders tests](https://github.com/jdi-testing/jdi-light/blob/vuetify-develop/jdi-light-vuetify-tests/src/test/java/io/github/epam/vuetify/tests/common/SubheaderTests.java)
.
