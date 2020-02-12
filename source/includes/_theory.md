# Theory
## UI Objects Pattern (Extend your PageObjects with UI elements)
TBD

## Entity Driven Testing
TBD

## Smart Locators
```csharp
public class UserCard : Form<User>
{
    [FindBy(Css = "#name")]
    TextField Name; 
    
    [FindBy(Css = "#last-name")]
    TextField LastName;
    
    [FindBy(Css = "#submit-button")]
    Button SubmitButton;
}

//If Smart locator rule is id:
    SmartSearchLocator = "#{0}";
    
//and the conversion rule is 'hyphen-to-csharp-name':
    SmartSearchName(string name) => StringExtensions.SplitHyphen(name);
    
//So you can write:

public class UserCard : Form<User>
{
    TextField name; 
    TextField LastName;
    Button SubmitButton;
}
```
```java 
public class UserCard extends Form<User> {
    @Css("#name") TextField name; 
    @Css("#last-name") TextField lastName;  
    @Css("#submit-button") Button submitButton; 
}















//So you can write:
public class UserCard extends Form<User> {
    TextField name;
    TextField lastName;
    Button submitButton; 
}






//in test.properties:
smart.locators = "#%s"
smart.locators.toName = UPPER_SNAKE_CASE

public class UserCard extends Form {
    TextField name;
    TextField lastName;
    TextField passportCode;
}

//Then JDI will be using the following locators for the elements:
name -->#NAME
lastName --> #LAST_NAME
passportCode --> #PASSPORT_CODE, etc



/* You don't need to set values for WebSettings class fields.
   This code is just for illustrating how the default locator
   value and the default locator naming rule are set 
   in WebSettings class*/

//Smart locator rule is id:
  WebSettings.SMART_SEARCH_LOCATORS = asList("#%s");
   
 

//and the conversion rule is 'hyphen-to-java-name':
  WebSettings.SMART_SEARCH_NAME = StringUtils::splitHyphen;
```
```html
<input type="text" id="name">
<input type="text" id="last-name">
<button id="submit-button">
```
<br>

If you have your developers following some standard way of marking UI elements or you have
an agreement to add special attributes, you can even avoid writing locators for elements,
thus making your page objects much more compact.


E.g. let's say we have an agreement on naming elements and their ids in the following way:<br>
a Button element *submitButton* should have id equal to *submit-button*, a text field
element *lastName* should have id equal to *last-name*, and so on.

In this case we can save time on adding a UI annotation for each element e.g.:<br>
 *@Css("#last-name")<br>
  Text lastName*
 
Instead, we just write:<br>
 *Text lastName*
  
and allow JDI Light framework to transform the variable name from "lastName"
 to "last-name" and find an element with such id. 
  
###How to define a smart locator

Smart locators can be set in JDI framework via a config file named *test.properties*.
There are two properties that we need: *smart.locators* and *smart.locators.toName*.

*smart.locators* property is a string representing locators separated by ";" (e.g. "#%s;name=%s")
that are going to be used for searching for an element.

*smart.locators.toName* property should contain one of the following values:<br>
kebab-case | camelCase | snake_case | PascalCase | UPPER_SNAKE_CASE that tells to JDI how to create a locator form a given variable name.

<br>
  
*test.properties* file is processed via **WebSetting.java** class:
  
- **WebSettings.SMART_SEARCH** - method invoked if you have an element with no locator

- **WebSettings.SMART_SEARCH_LOCATORS** - it is either the list of locators taken from smart.locators property
or "#%s" if that property is empty

- **WebSettings.SMART_SEARCH_NAME** -  method to create locator name from field name
 (this value will be passed as a %s parameter to SMART_SEARCH_LOCATORS). By default,
  kebab-case will be used



## JDI Locators (simple as css powerful as xpath)
JDI locators can be used to perform search with the help of css locators, but with extended possibilities, that are not available within the css element search:
- Search by element's full text - ['text']
```java
public void fullTextTest() {
    bys = searchBy(By.cssSelector("#contact-form['Last Name']"));
    assertEquals(bys.size(), 2);
    assertEquals(getElement(bys).getTagName(), "label");
    assertEquals(getElement(bys).getAttribute("for"), "last-name");
}
```

- Search by element's part of the text - [*'text']
```java
public void partTextTest() {
    bys = searchBy(By.cssSelector("#contact-form[*'Last N']"));
    assertEquals(bys.size(), 2);
    assertEquals(getElement(bys).getTagName(), "label");
    assertEquals(getElement(bys).getAttribute("for"), "last-name");
}
```

- Search by element index - [3]

```java
public void cssIndexTest() {
   bys = searchBy(By.cssSelector("input[type=text][4]"));
   assertEquals(bys.size(), 2);
   assertEquals(getElement(bys).findElement(By.xpath("..")).getText(), "Last Name");
}
```
- Search by element's parent - <
```java
public void indexAndParentTest() {
    bys = searchBy(By.cssSelector("input[type=text][4]<"));
    assertEquals(bys.size(), 3);
    assertEquals(getElement(bys).getText(), "Last Name");
    assertEquals(getElement(bys).getTagName(), "div");
}
```

