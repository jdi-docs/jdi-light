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
**classes()** | Gets all classes as list | List<String>
**clear()** | Clears input field | void
**click()** | Clicks on element | void
**click(Element area)** | Clicks on element area(Element area could be SMART_CLICK, TOP_LEFT, TOP_RIGHT, BOTTOM_LEFT, BOTTOM_RIGHT, CENTER, JS) | void
**click(int x, int y)** | Clicks on point (x, y) | void
**doubleClick()** | Double clicks on the element | void
**dragAndDropTo(int x, int y)** | Drags and drops it to certain coordinates | void
**dragAndDropTo(WebElement to)** | Drags and drops it to another element | void
**focus()** | Focuses on element | void
**getAllAttributes()** | Gets all element’s attributes | MapArray<String, String>
**getAttribute(String value)** | Gets the attribute value | String
**getCssValue(String value)** | Gets element css value | String
**getLocation()** | Gets element location as point | Point
**getRect()** | Gets element rectangle | Rectangle
**getSize()** | Gets element size | Dimension
**getTagName()** | Returns tag name | String
**getText()** | Gets text of the element | String
**getValue()** | Gets text | String
**hasAttribute(String attrName)** | Returns true if element has expected attribute | boolean
**hasClass(String className)** | Returns true if element has expected class | boolean
**highlight()** | Highlights element with red color | void
**highlight(String color)** | Scrolls view to element and makes a border around with specified color | void
**hover()** | Hovers mouse to element | void
**input(String value)** | Inputs specified value as keys | void
**isDeselected()** | Checks that element is deselected | boolean
**isDisabled()** | Checks element is disabled | boolean
**isDisplayed()** | Checks the element is displayed | boolean
**isEnabled()** | Checks element exists | boolean
**isHidden()** | Checks element is hidden | boolean
**isNotExist()** | Checks element doesn’t exist | boolean
**isNotVisible()** | Checks element is not visible by user | boolean
**isSelected()** | Checks that element is selected | boolean
**isVisible()** | Checks element is displayed | boolean
**jsExecute(String jsCode)** | Executes java script call | String
**labelText()** | Gets label text | String
**makePhoto()** | Gets element’s screenshot | File
**placeholder()** | Gets attribute ‘placeholder’ | String
**printHtml()** | Gets the element attribute “innerHTML” value | String
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
**text()** | Gets text | String
**uncheck()** | Clicks on element if selected | void


Aliases in Java JDI Light:

|Method | Description | Return Type
--- | --- | --- 
**attr(String value)** | Gets attribute | String
**attrs()** | Gets all attributes | MapArray<String, String>
**css(String prop)** | Gets css value | String
**text()** | Gets text | String


#### WebList

### Extended Selenium features
#### WaitAferMethod


You can specify the timeout that JDI will wait ater actions<br>
@WaitAfterAction("getText", 3) - will wait after action getText() for 3 seconds<br>
default timeout = 1 second so you can mit it<br>
if methodName is empty it will be applied to all "action" methods (taht not get something). List of methods depend on element, for example click() or check("Gold") or select("blue")<br>

```java 
   @WaitAfterMethod("gettext", 3)
   public Text colorValue;

   @WaitAfterMethod(2)
   public Dropdown detailsButton;
   
   @WaitAfterMethod
   public Dropdown colors;
...  
   @Test
   public void selectColor() {
     detailsButton.click() - will wait ater click 2 seconds
     colors.select("Gold"); - will wait ater select 3 seconds
     assertEquals(colorValue.getText(), "Gold") - will wait ater getText 1 seconds
   }
 ```
