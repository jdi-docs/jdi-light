# Documentation

### 5.32 Lazy

[Vuetify documentation page](https://vuetifyjs.com/en/components/lazy/)

- __Java__: _com.epam.jdi.light.vuetify.elements.complex.Lazy.java_

```java
@Test
public void itemIsLoadedTest() {
lazy.scrollIntoView();
lazy.is().displayed();
lazy.hiddenItem().is().displayed();
lazy.core().find(ITEM_TITLE).has().text("Card title");
lazy.core().find(ITEM_TEXT).is().displayed();
lazy.core().find(ITEM_TEXT).has().text(Matchers.containsString("Aliquam lobortis"));
    }
```

![Lazy example](../../images/vuetify/lazy.png)

The Lazy component is used to dynamically load components based upon an elements visibility.

|Method | Description | Return Type
--- | --- | ---
**hiddenItem()** | Returns hidden item by `item` locator from JDILazy annotation| UIElement
**isHidden()** | Returns true if element is hidden | boolean
**isDisplayed()** | Returns true if element is displayed | boolean
**scrollIntoView()** | Scrolls down until element is displayed | void
**is()** | Returns Assert class | LazyAssert

For examples of usage see: JDI vuetify page tests for lazy.
