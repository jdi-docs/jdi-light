# Theory
## UI Elements
In order to effectiviely utilize <a href="https://github.com/SeleniumHQ/selenium/wiki/PageObjects" target="_blank">Page Objects pattern</a> we need to use elements on the pages. Instead of tag-like Selenium ```WebElement``` s that represents tag in html in JDI we introduce UI Elements that represrent element on UI used by real user.</br>
JDI provides an ability to create your own element or reuse standard element from our rich collection</br>
### Common elements
* Used to make your Page Objects more intuitive and clear
* In addition we use elements type and name in our logs and reports that simplifies tests maintanance
* And of course we expect from UI elements only actions that are relevant to them (e.g. you can't sendKeys in ```Button``` but this is possible with ```WebElement``` or ```SelenideElement```)

In JDI we have following Common elements:</br>
[Label](https://jdi-docs.github.io/jdi-light/?java#label) 
[Button](https://jdi-docs.github.io/jdi-light/?java#button) ...

```java 
@UI("input[type=text].name") public TextField name;
@UI("h1") public Label label;
@UI("//div[@name='disclamer']") public Text disclaimer;
@UI("textarea[ui=description]") public TextArea description;
@UI("//*[text()='Submit']") public Button submit;
```

### Complex elements
In addition to [Common elements](https://jdi-docs.github.io/jdi-light/?java#common-elements) features Complex elements helps to combine list of different elements in one UI element</br>
Typical example of Complex element is ```Dropdown```, ```Combobx```, ```Table``` etc.</br>
Other examples are lists of similar elements like ```List<WebElement>``` in Selenium. Typical examples are: ```Menu```, ```Checklist```, ```RadioButtons```, ```Tabs``` etc.
Also you can use list of Common elements as ```List<...>``` e.g. ```List<Button>``` or ```List<Label>```

In JDI we have following Common elements:</br>
[Dropdown](https://jdi-docs.github.io/jdi-light/?java#dropdown) 
[Combobox](https://jdi-docs.github.io/jdi-light/?java#combobox) 
[Checklist](https://jdi-docs.github.io/jdi-light/?java#checklist) ...

```java 
@UI(".colors") public Dropdown colors;
@UI("input[type=checkbox].conditions") public Checklist acceptConditions;
@JDropdown(root = ".colors", value = ".dropdown-value", list = "li", expand = ".caret")
public Dropdown colors;
@UI("[ui=label] li") public JList<Labels> tabs;
@UI("//button[text()='%s']") public JList<Button> buttons;
```

### Composite elements
Composite elements represents part of page and often used just as container for elements and actions</br>
Typical examples are ```WebPage``` and ```Section```.</br>
In the same time composite elements also can have a locator that defines a context for all elements inside. That means that all elements in composite element will be searched relatively under this locator.</br>
Composite elements also can have predefined actions like fill(...), submit(...) and check(...) for ```Form``` or open(), checkOpened() for ```WebPage```.</br>
Remember that you can create your own Composite elements with JDI Light for example for Header, Navigation bar, Footer, Left sidebar, advertisement or main part ofr the page.</br>

In JDI we have following Common elements:</br>
[WebPage](https://jdi-docs.github.io/jdi-light/?java#webpage) 
[Section](https://jdi-docs.github.io/jdi-light/?java#section) 
[Form](https://jdi-docs.github.io/jdi-light/?java#form) ...

```java
public class LoginForm extends Form<User> {
    public TextField name, password;
    @UI("//*[text()='Submit']") public Button submit;
    ...
}
public class TopPanel extends Section {
    @UI("form.login") public LoginForm loginForm;
    @UI("h1") public Label label;
    @UI(".colors") public Dropdown colors;
    ...
}
@Url("/login.html") @Title("Login to JDI")
public class LoginPage extends WebPage {
    @UI(".top-panel") public TopPanel topPanel;
    ...
}
```

## UI Objects Pattern
UI objects extend typical <a href="https://github.com/SeleniumHQ/selenium/wiki/PageObjects" target="_blank">Page Objects pattern</a> with [UI Elements](https://jdi-docs.github.io/jdi-light/?java#ui-elements) and add ability to fragmentize pages to sections.</br>
Typical UI objects structure consists of:</br>
* Site class that collects all pages and common parts of the application like header, footer or navigation panel
* Page Objects that extends from ```WebPage``` and represents logical application pages
* Composite elements that typically represented by ```Sections``` or other [Composite elements](https://jdi-docs.github.io/jdi-light/?java#composite-elements) and acts as Containers for other elements and smaller sections
* UI Elements that represents functional elements on page used by application user

```java
public class AwesomeApplication {
    public LoginPage loginPage;
    @UI(".nav li") public Menu navigation;
}
@Url("/login.html") @Title("Login to JDI")
public class LoginPage extends WebPage {
    @UI(".top-panel") public TopPanel topPanel;
    ...
}
public class TopPanel extends Section {
    @UI("form.login") public LoginForm loginForm;
    @UI("h1") public Label label;
    @UI(".colors") public Dropdown colors;
    ...
}
```

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

```java
//Here's simple test to find 4th text element's parent element
public void indexAndParentTest() {
    bys = searchBy(By.cssSelector("input[type=text][4]<"));
    assertEquals(bys.size(), 3);
    assertEquals(getElement(bys).getText(), "Last Name");
    assertEquals(getElement(bys).getTagName(), "div");
}
```

JDI locators can be used to perform search with the help of css locators, but with extended possibilities, that are not available within the css element search:

- Search by element's full text - **['text']**

- Search by element's part of the text - **[*'text']**

- Search by element index - **[3]**

- Search by element's parent - **<**

You can also use them apart or altogether


