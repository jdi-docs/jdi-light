# Theory
## UI Elements
In order to effectiviely utilize <a href="https://github.com/SeleniumHQ/selenium/wiki/PageObjects" target="_blank">Page Objects pattern</a> we need to use elements on the pages. Instead of tag-like Selenium ```WebElement``` s that represents tag in html in JDI we introduce UI Elements that represrent element on UI used by real user.</br>
JDI provides an ability to create your own element or reuse standard element from our rich collection</br>

### Common elements

```java 
@UI("input[type=text].name") public TextField name;
@UI("h1") public Label label;
@UI("//div[@name='disclamer']") public Text disclaimer;
@UI("textarea[ui=description]") public TextArea description;
@UI("//*[text()='Submit']") public Button submit;
```
- Used to make your Page Objects more intuitive and clear
- In addition we use elements type and name in our logs and reports that simplifies tests maintanance
- And of course we expect from UI elements only actions that are relevant to them (e.g. you can't sendKeys in ```Button``` but this is possible with ```WebElement``` or ```SelenideElement```)

In JDI we have the following Common elements:</br>
- [Label](https://jdi-docs.github.io/jdi-light/?java#label)</br> 
- [Button](https://jdi-docs.github.io/jdi-light/?java#button) ...


### Complex elements

```java 
@UI(".colors") public Dropdown colors;
@UI("input[type=checkbox].conditions") public Checklist acceptConditions;
@JDropdown(root = ".colors", value = ".dropdown-value", list = "li", expand = ".caret")
public Dropdown colors;
@UI("[ui=label] li") public JList<Labels> tabs;
@UI("//button[text()='%s']") public JList<Button> buttons;
```
In addition to [Common elements](https://jdi-docs.github.io/jdi-light/?java#common-elements) features Complex elements helps to combine list of different elements in one UI element</br>
Typical example of Complex element is ```Dropdown```, ```Combobx```, ```Table``` etc.</br>
Other examples are lists of similar elements like ```List<WebElement>``` in Selenium. Typical examples are: ```Menu```, ```Checklist```, ```RadioButtons```, ```Tabs``` etc.
Also you can use list of Common elements as ```List<...>``` e.g. ```List<Button>``` or ```List<Label>```

In JDI we have the following Complex elements:</br>
- [Dropdown](https://jdi-docs.github.io/jdi-light/?java#dropdown)</br>
- [Combobox](https://jdi-docs.github.io/jdi-light/?java#combobox)</br> 
- [Checklist](https://jdi-docs.github.io/jdi-light/?java#checklist) ...

### Composite elements

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
Composite elements represents part of page and often used just as container for elements and actions</br>
Typical examples are ```WebPage``` and ```Section```.</br>
In the same time composite elements also can have a locator that defines a context for all elements inside. That means that all elements in composite element will be searched relatively under this locator.</br>
Composite elements also can have predefined actions like fill(...), submit(...) and check(...) for ```Form``` or open(), checkOpened() for ```WebPage```.</br>
Remember that you can create your own Composite elements with JDI Light for example for Header, Navigation bar, Footer, Left sidebar, advertisement or main part ofr the page.</br>

In JDI we have the following Composite elements:</br>
- [WebPage](https://jdi-docs.github.io/jdi-light/?java#webpage)</br> 
- [Section](https://jdi-docs.github.io/jdi-light/?java#section)</br>
- [Form](https://jdi-docs.github.io/jdi-light/?java#form) ...


## UI Object Pattern

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
UI objects extend the typical <a href="https://github.com/SeleniumHQ/selenium/wiki/PageObjects" target="_blank">Page Objects pattern</a> with [UI Elements](https://jdi-docs.github.io/jdi-light/?java#ui-elements) and allow users to split pages into sections.</br>
A typical UI object structure consists of:</br>
- A ```Site class``` that contains all pages and common parts of application like header, footer or navigation panel</br>
- ```Page Objects``` extending from ```WebPage``` and representing respective application pages</br>
- Composite elements typically represented by ```Sections``` or other [Composite elements](https://jdi-docs.github.io/jdi-light/?java#composite-elements), acting as Containers for other elements and smaller sections</br>
- UI Elements representing functional elements on page utilized by end user


## Entity Driven Testing

```java
(1)
public class LoginForm extends Form<User> {
    public TextField name, password;
    @UI("//*[text()='Submit']") public Button submit;
    ...
}
public class User extends DataClass<User> {
    public String name, password;
}
@Test(dataProvider = "users")
public void loginTest(User user) {
    loginForm.loginAs(user);
}
(2)
@UI("#user-table")
public static DataTable<?, UserInfo> userTable;
public class UserInfo extends DataClass<UserInfo> {
    public String number, type, user, description;
}
@Test
public void userInfoTest() {
    usersListPage.open();
    userTable.has().value(SPIDER_MAN, inRow(2));
    userTable.assertThat()
      .all().rows(d -> d.user.length() > 4)
      .no().rows(d -> isBlank(d.user))
      .atLeast(3).rows(d -> d.type.contains("User"))
      .exact(1).rows(SPIDER_MAN);
    assertEquals(userTable.dataRow("Wolverine").type, "Admin");
}
(3)
@UI(".search-results li") public DataList<?, Result> resultsList;
public class Result extends DataClass<Result> {
    public String name, description, link;
}
@Test
public void resultsTest() {
        resultsList.assertThat().value(containsString(
            "name:JDI FACEBOOK GROUP; description:English Community Facebook group"))
            .any(e -> e.description.toLowerCase().contains("jdi"))
            .each(e -> e.name.toLowerCase().contains("jdi"))
            .onlyOne(e -> e.name.contains("OWNER"))
            .noOne(e -> e.name.equalsIgnoreCase("Selenide"));
            
        resultsList.assertThat(not(empty()))
            .and(hasSize(greaterThan(2)))
            .and(hasItem(CORRECT))
            .and(hasItems(CORRECT, CORRECT_2, CORRECT_3))
            .and(not(hasItem(CORRUPTED)))
            .and(not(hasItems(CORRUPTED, CORRUPTED_2)));
}
```
Entites Driven Testing(EDT) is approach where Business Entites going through test scenarios instead of unnamed data.</br>
EDT can be orgnically combined with DDT that use Business Entites as input to similar scenarios.
JDI Light natively supports EDT with Forms, Tables and DataLists. See more examples in the right panel.

## Smart Locators
### Smart locators example
Let's assume you have some typical way to locate most of the elements for example most of elements has id or name or special attribute to locate ui elements valuable for automation. </br>
Let's asume you have `@UI("[ui=last-name]") public TextField lastName;`  element in JDI. In this case you simplify it to `public TextField lastName;` and omit locator</br>
See more complex example below and in code panel at the right:</br>
For example you have following html</br>
```html
<input type="text" ui="name"/>
<input type="text" ui="last-name"/>
<input type="text" ui="pin-code"/>
<input type="text" ui="promo-code"/>
<input type="checkbox" ui="accept-conditions"/>
<a href="..." ui="external-link">External link</a>
<button ui="submit-button">
```

```csharp
public class UserCard : Form<User>
{
    [FindBy(Css = "#name")] public TextField Name;
    [FindBy(Css = "#last-name")] public TextField LastName;
    [FindBy(Css = "#submit-button")] public Button SubmitButton;
}
SmartSearchLocator = "#{0}";
SmartSearchName(string name) => StringExtensions.SplitHyphen(name);
public class UserCard : Form<User>
{
    TextField name; 
    TextField LastName;
    Button SubmitButton;
}
```
```java
Selenium
@FindBy(css = "[ui=name]") 
public WebElement name;
@FindBy(css = "[ui=last-name]") 
public WebElement lastName;
@FindBy(css = "[ui=pin-ncodeame]") 
public WebElement pinCode;
@FindBy(css = "[ui=promo-code]") 
public WebElement promoCode;
@FindBy(css = "[ui=accept-conditions]") 
public WebElement acceptConditions;
@FindBy(css = "[ui=submit-button]") 
public WebElement submitButton; 
```
In standrd way in Selenium in Page Objects you need to write following code for this elements.
</br></br></br></br></br></br></br></br></br></br></br></br>

```java
@UI("[ui=name]") public Textfield name;
@UI("[ui=last-name]") public Textfield lastName;
@UI("[ui=pin-code]") public Textfield pinCode;
@UI("[ui=promo-code]") public Textfield promoCode;
@UI("[ui=accept-conditions]") public Checkbox acceptConditions;
@UI("[ui=submit-button]") public Button submitButton;
```
In JDI Light with standard UI Objects code be more obvious but still has duplications in locator and element name.
</br></br></br></br></br></br>

```java
public Textfield name, lastName, pinCode, promoCode;
public Checkbox acceptConditions;
public Button submitButton;
```
And using smart locators you can write this without any duplications (without locators) just in few lines</br>
Isn't this looks cool?</br></br>

### Define smart locator using test.properties

```java
smart.locators="[ui=%s]"
smart.locators.toName=UPPER_SNAKE_CASE
```
You can setup your smart locators in `test.properties` in following way:</br>
Setup `smart.locators=`</br>
put `#%s` in case you smart locator is id</br>
put `.%s` for class</br>
put `[name=%s]` for name or other attribute</br>
</br>
For example you set `smart.locators=[ui=%s]`</br>
Setup `smart.toName=`</br>
`kebab-case` will produce `[ui=last-name]` locator for public WebElement lastName;</br>
`camelCase` will produce `[ui=lastName]` locator for public WebElement lastName;</br>
`snake_case` will produce `[ui=last_name]` locator for public WebElement lastName;</br>
`PascalCase` will produce `[ui=LastName]` locator for public WebElement lastName;</br>
`UPPER_SNAKE_CASE` will produce `[ui=LAST_NAME]` locator for public WebElement lastName;</br>
or if you have `smart.locators=//*[text()='%s']`</br>
`First Upper Case` will produce `//*[text()='Submit Form']` locator for public WebElement submitForm;</br>
`ALL UPPER CASE` will produce `//*[text()='SUBMIT FORM']` locator for public WebElement submitForm;</br>

### Define smart locator using WebSettings

```java
WebSettings.SMART_SEARCH_LOCATORS = asList("#%s");
WebSettings.SMART_SEARCH_NAME = StringUtils::toKebabCase;
JDI Light like
WebSettings.SMART_SEARCH = el -> {
  String locatorName = toKebabCase(el.getName());
  UIElement element = $("[auto="+locatorName+"], el.base().parent));
  element.setName(el.getName());
  return element.getWebElement();
}
Selenium like:
WebSettings.SMART_SEARCH = el -> {
  String locatorName = toKebabCase(el.getName());
  return getDriver.findElement(By.cssClass("[auto="+locatorName+"]"));
}
```
From other hands you can setup Smart Locators in code using `WebSettings.SMART_SEARCH_NAME` and `WebSettings.SMART_SEARCH_LOCATORS` variables</br>
Or you can define by yourself what should be done in case of UI Element has no locator using `WebSettings.SMART_SEARCH` function

## JDI Locators (simple as css powerful as xpath)
With JDI Light you can use simple and fast css selecctors with power of xpath locators. Now you can search by text or index in css or even move up and down in html tree.</br>
See some examples below:</br>
XPath: `//div[contains(@class,'btn')]//*[text()='Submit']`</br>
JDI Locator: `div.btn['Submit']`

XPath: `//*[contains(@class,'nav-menu')]//*[@data-role='header']//*[contains(text(),'Navigation menu')]`</br>
JDI Locator: `.nav-menu [data-role=header][*'Navigation menu']`</br>

XPath: `//label[text()='Gold status']/..//input[@type='checkbox']`</br>
JDI Locator: `label['Gold status']<input[type=checkbox]`</br>

XPath: `//label[text()='Gold status']/..//input[@type='checkbox']`</br>
JDI Locator: `label['Gold status']<input[type=checkbox]`</br>

XPath: `//*[contains(@class,'nav-menu')]//*[@data-role='header'][3]`</br>
JDI Locator: `.nav-menu [data-role=header][3]`</br>
