## Base information
### Base Elements
#### UIBaseElement

#### UIElement

```java 

  @Test
  public void click() {
      submit.click();
      assertEquals(sum.getText(), "Summary: 3");
  }

  @Test
  public void isDisplayed(){
      assertTrue(submit.isDisplayed());
  }

  @Test
  public void input(){
      description.input("Hello world!");
      assertEquals(description.getText(), "Hello world!");
      description.clear();
  }

  @Test
  public void hasAttribute() {
      assertTrue(submit.hasAttribute("class"));
      assertTrue(submit.hasAttribute("type"));
  }
  
```

Available methods in Java JDI Light:

|Method | Description | Return Type
--- | --- | --- 
**check()** | Clicks on element if it's not selected | void
**classes()** | Gets all element's classes as list | List<String>
**clear()** | Clears input field | void
**click()** | Clicks on element | void
**click(ElementArea area)** | Clicks on element area (possible ElementArea values are SMART_CLICK, TOP_LEFT, TOP_RIGHT, BOTTOM_LEFT, BOTTOM_RIGHT, CENTER, JS) | void
**click(int x, int y)** | Clicks on point (x, y) | void
**doubleClick()** | Double clicks on the element | void
**dragAndDropTo(int x, int y)** | Drags and drops element to certain coordinates | void
**dragAndDropTo(WebElement to)** | Drags and drops element to another element | void
**focus()** | Focuses on element | void
**getAllAttributes()** | Gets all element attributes | MapArray<String, String>
**getAttribute(String value)** | Gets the value of specified element attribute | String
**getCssValue(String value)** | Gets element CSS value | String
**getLocation()** | Gets element location as point | Point
**getRect()** | Gets element rectangle | Rectangle
**getSize()** | Gets element size | Dimension
**getTagName()** | Gets element tag name | String
**getText()** | Gets element text| String
**getValue()** | Gets element text | String
**hasAttribute(String attrName)** | Returns true if the element has an expected attribute | boolean
**hasClass(String className)** | Returns true if the element has an expected class | boolean
**highlight()** | Highlights element with red color | void
**highlight(String color)** | Scrolls view to element and highlights it with a border of specified color | void
**hover()** | Hovers mouse cursor over the element | void
**input(String value)** | Inputs specified value as keys | void
**isDeselected()** | Checks that element is deselected | boolean
**isDisabled()** | Checks that element is disabled | boolean
**isDisplayed()** | Checks that element is displayed | boolean
**isEnabled()** | Checks that element exists | boolean
**isHidden()** | Checks that element is hidden | boolean
**isNotExist()** | Checks that element does not exist | boolean
**isNotVisible()** | Checks that element is not visible by user | boolean
**isSelected()** | Checks that element is selected | boolean
**isVisible()** | Checks that element is visible by user | boolean
**jsExecute(String jsCode)** | Executes JavaScript code | String
**labelText()** | Gets label text | String
**makePhoto()** | Gets a screenshot of the element | File
**placeholder()** | Gets element “placeholder” attribute value | String
**printHtml()** | Gets element “innerHTML” attribute value | String
**rightClick()** | Right clicks on the element | void
**select()** | Selects item | void
**select(int index)** | Selects item by index | void
**select(String value)** | Selects item by value | void
**select(String… names)** | Selects items by values | void
**sendKeys(CharSequence… value)** | Sends specified value as keys | void
**setAttribute(String name, String value)** | Sets value to the specified attribute | void
**setText(String value)** | Puts value as text | void
**setValue()** | Inputs value | void
**show()** | Scrolls screen view to item | void
**uncheck()** | Clicks on element if selected | void


Aliases in Java JDI Light:

|Method | Description | Return Type
--- | --- | --- 
**attr(String value)** | Gets element attribute | String
**attrs()** | Gets all element attributes | MapArray<String, String>
**css(String prop)** | Gets element css value | String
**text()** | Gets element text | String


#### WebList

### Extended Selenium features
#### Wait After Action


You can annotate a UI element with `@WaitAfterAction`. This tells JDI to wait after executing this element's methods.

`@WaitAfterAction(value = 3, method = "getText")` would mean that JDI will wait 3 seconds after executing the annotated element's `getText()` method.

If the method name is not specified, the wait will be applied to all action methods of the element (like `click`, `check` or `select`, depending on the element), and you can write the annotation like `@WaitAfterAction(3)`.

You can also apply the default `@WaitAfterAction` which sets the wait to 1 second for all action methods.

```java 
   @WaitAfterAction(value = 3, method = "getText")
   public Text colorValue;

   @WaitAfterAction(2)
   public Dropdown detailsButton;
   
   @WaitAfterAction
   public Dropdown colors;
   
   ...  
   
   @Test
   public void selectColor() {
     detailsButton.click()  // will wait 2 seconds after click
     colors.select("Gold");  // will wait 1 second after select 
     assertEquals(colorValue.getText(), "Gold") // will wait 3 seconds after getText 
   }
 ```
