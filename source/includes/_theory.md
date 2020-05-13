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
- [Label](https://jdi-docs.github.io/jdi-light/?java#label), 
[Button](https://jdi-docs.github.io/jdi-light/?java#button),
[Checkbox](https://jdi-docs.github.io/jdi-light/?java#checkbox),
[ColorPicker](https://jdi-docs.github.io/jdi-light/?java#colorpicker),
[DateTimeSelector](https://jdi-docs.github.io/jdi-light/?java#datetimeselector),
[FileInput](https://jdi-docs.github.io/jdi-light/?java#fileinput),
[Icon](https://jdi-docs.github.io/jdi-light/?java#icon),
[Image](https://jdi-docs.github.io/jdi-light/?java#image),
[Link](https://jdi-docs.github.io/jdi-light/?java#link),
[Menu](https://jdi-docs.github.io/jdi-light/?java#menu),
[NumberSelector](https://jdi-docs.github.io/jdi-light/?java#numberselector),
[ProgressBar](https://jdi-docs.github.io/jdi-light/?java#progressbar),
[Range](https://jdi-docs.github.io/jdi-light/?java#range),
[Text](https://jdi-docs.github.io/jdi-light/?java#text),
[TextField](https://jdi-docs.github.io/jdi-light/?java#textfield),
[TextArea](https://jdi-docs.github.io/jdi-light/?java#textarea),
[Title](https://jdi-docs.github.io/jdi-light/?java#title).


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
- [RadioButtons](https://jdi-docs.github.io/jdi-light/?java#radiobuttons),
[Table](https://jdi-docs.github.io/jdi-light/?java#table),
[DataTable](https://jdi-docs.github.io/jdi-light/?java#datatable),
[Dropdown](https://jdi-docs.github.io/jdi-light/?java#dropdown),
[MultiDropdown](https://jdi-docs.github.io/jdi-light/?java#multidropdown),
[DataList](https://jdi-docs.github.io/jdi-light/?java#datalist),
[Checklist](https://jdi-docs.github.io/jdi-light/?java#checklist),
[MultiSelector](https://jdi-docs.github.io/jdi-light/?java#multiselector),
[Combobox](https://jdi-docs.github.io/jdi-light/?java#combobox).

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
 
- [Section](https://jdi-docs.github.io/jdi-light/?java#section),
[Form](https://jdi-docs.github.io/jdi-light/?java#form),
[WebPage](https://jdi-docs.github.io/jdi-light/?java#webpage).


## UI Objects

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
  resultsList.assertThat()
    .value(containsString("name:JDI FACEBOOK GROUP; description:English Community Facebook group"))
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
EDT can be orgnically combined with DDT that use Business Entites as input to similar scenarios.</br>
JDI Light natively supports EDT with Forms, Tables and DataLists. See more examples in the right panel.</br>
</br>
Example scenario:</br>

```html
> Provide List<User> for test
0. Have user in DB
1. Login with user
2. Submit Contact Us Form for user
3. Get Act. Opening from Vacancy table
4. Assert Act. Opening equals to Exp. Opening
```
Code example:</br>

```html
@Test(dataProvider = “users")                      //>
public void formTest(User user) {
    DB.users.shouldHas(user);                      //0.
    loginForm.loginAs(user);                       //1.
    contactUsForm.submit(user);                    //2.
    Vacancy vacancy = vacancyTable.getEntity(3);   //3.
    Assert.areEquals(vacancy, expectedVacancy);    //4.
}
```

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
In standard way in Selenium in Page Objects you need to write following code for this elements.
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
  UIElement element = $("[auto="+locatorName+"]", el.base().parent));
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

### Smart Annotations 
In case you have few standart patterns for locators you can use Smart Annotations in order to mark the elements with this locators.</br>
For `@UI("#last-name") TextFiled lastName;`</br>
use `@SId TextField lastName;`</br>
For `@UI(".contact-form") Form<CardData> contactForm;`</br>
use `@SClass Form<CardData> contactForm;`</br>
For `@UI("//*[text()='Submit Card']") Button submitCard;`</br>
use `@SText Button submitCard;`</br>
For `@UI("[name='accept-conditions']") Checkbox acceptConditions;`</br>
use `@SName Checkbox acceptConditions;`</br>
or use @Smart annotation for any specific html attribute
For `@UI("[data-type=data-multy-combobx]") MultiCombobox dataMultyCombobx;`</br>
use `@Smart("data-type") MultiCombobox dataMultyCombobx;`</br>
</br>

### Custom Smart Annotation
Or you always can create your own annotation for smart behaviour</br>
Let's assume you would like to use smart locators for buttons like `//button[text()='Button Text']`</br>
1. Create new annotation</br>

```html
SButton.java
@Retention(RetentionPolicy.RUNTIME)
@Target({ElementType.TYPE, ElementType.FIELD})
public @interface SButton {
}
```
2. setup behaviour for this annotations before you call initSite(...)

```html
@BeforeSuite(alwaysRun = true)
public static void setUp() {
    JDI_ANNOTATIONS.add("Buttons", aRule(SButton.class,
        (e, a) -> e.setLocator(format("//button[text()='%s']", splitCamelCase(e.getName())))));
    initSite(YourAwesomeSite.class);
```
Thats all. Now we can write</br>

```html
@SButton public Button logIn, signIn, cancel, useVipAccess;
```
instead of </br>

```html
@FindBy(xpath = "//button[text()='Log In']")
public WebElement logIn;
@FindBy(xpath = "//button[text()='Sign In']")
public WebElement signIn;
@FindBy(xpath = "//button[text()='Cancel']")
public WebElement cancel;
@FindBy(xpath = "//button[text()='Use Vip Access']")
public WebElement useVipAccess;
```

## JDI Annotations
In order to control elements behaviour in JDI Light you can use following standard annotations:</br>
**@Root** - ignores all parent sections locators for this element and uses only locator that specified for element (including smart locators)</br>
**@Frame("frame-id")** or **@Frame({"frame-id", "div[name-adv]"})** - in case you have two or more frames above element - use driver.switchTo().frame(...) before searching your element. Or call it multiple times if @Frame has list of locators. Can be used together with @UI locator</br>
**@Css("div.dropdown")** - if your element has Css locator (deprecated, recommended to use universal **@UI**)</br>
**@XPath("//div[text()="Submit"]")** - if your element has Xpath locator (deprecated, recommended to use universal **@UI**)</br>
**@ByText("Submit")** - is used for elements that can be found by text (uses locator `".//*/text()[normalize-space(.) = %s]/parent::*"`)</br>
**@WithText("Navigation")** - is used for elements that can be found as text contains(uses locator `".//*/text()[contains(normalize-space(.), %s)]/parent::*"`)</br>
**@ClickArea(...)** - specify how click will be performed. Allowed values: SMART_CLICK(try to find area where user able to click), TOP_LEFT(click top-left corner of the element), TOP_RIGHT(click top-right corner of the element), BOTTOM_LEFT(click bottom-left corner of the element), BOTTOM_RIGHT(click bottom-right corner of the element), CENTER(Selenium standard click in the center of the element), JS(using JS click)</br>
**@GetTextAs(...)** - specify how getText will be performed. Allowed values: TEXT(getText()), VALUE(getAttribute("value")), INNER(jsExecute("innerText")), LABEL(using label related to element - good for checkboxes and radio), SMART_TEXT (try to find value smart)</br>
**@SetTextAs(...)** - specify how input text will be performed. Allowed values: SEND_KEYS(sendKeys(...)), SET_TEXT(set `value` attribute using JS), CLEAR_SEND_KEYS(clear(); sendKeys(...))</br>
**@NoCache** - always gets element from page. Not use cache</br>
**@WaitTimeout(sec)** – waits element for sec seconds implicitly</br>
**@NoWait** – doesn’t wait element to appear, so to be found it should be already on page</br>
**@Name(“Test”)** – sets name of element to e.g. “Test” like in example</br>
**@GetAny** – gets element without validation</br>
**@GetVisible** – returns displayed element</br>
**@GetVisibleEnabled** – returns displayed and enabled element</br>
**@GetShowInView** – returns displayed and clickable element</br>
**@PageName** – sets pageName variable for element</br>
**@SId** – sets smart Id locator, e.g `“By.cssSelector: #Test”`, where “Test” is name of the element</br>
**@SText** – sets smart text locator, e.g. `“By.xpath: .//*/text()[normalize-space(.) = "S Text"]/parent::*”`, where “SText” is name of the element. Pay attention that it’s creating locator with white space for words staring with capital letter</br>
**@SName** – sets smart name locator, e.g. for `“@Name(“Test”) @SName”` it will be `“By.cssSelector: [name='test']”`</br>
**@Smart** – sets smart locator, e.g. for the variant `“@Name(“Smart”) @Smart(“id”)”` it will be `“By.cssSelector: [id=’smart’]”`</br>
**@SClass** – sets smart class locator, e.g. for `“@Name(“Test”) @SName”` it will be `“By.cssSelector: .test”`</br>
**@UI** – for list UI locator, e.g. @UI("img"), see more examples in previous section</br>
**@FindBy** – annotation that could have fields: css, tagName, linkText, partialLinkText, xpath; text, id, name, className, group. Could be quickly changed to from Selenium @FindBy by changing import line</br>
**@VisualCheck** – adds pair “(“visualCheck”, “”)” to params

## JDI Locators (simple as css powerful as xpath)

```java
@XPath(`//div[contains(@class,'btn')]//*[text()='Submit']`)
@UI(`div.btn['Submit']`)

@XPath(`//*[contains(@class,'nav-menu')]//*[@data-role='header']//*[contains(text(),'Navigation menu')]`)
@UI(`.nav-menu [data-role=header][*'Navigation menu']`)

@XPath(`//label[text()='Gold status']/..//input[@type='checkbox']`)
@UI(`label['Gold status']<input[type=checkbox]`)

@XPath(`//*[contains(@class,'nav-menu')]//*[@data-role='header'][3]`)
@UI(`.nav-menu [data-role=header][3]`)
```

With JDI Light you can use simple and fast css selecctors with power of xpath locators. Now you can search by text or index in css or even move up and down in html tree.</br>
See some examples below:</br>
XPath: `//div[contains(@class,'btn')]//*[text()='Submit']`</br>
JDI Locator: `div.btn['Submit']`

XPath: `//*[contains(@class,'nav-menu')]//*[@data-role='header']//*[contains(text(),'Navigation menu')]`</br>
JDI Locator: `.nav-menu [data-role=header][*'Navigation menu']`</br>

XPath: `//label[text()='Gold status']/..//input[@type='checkbox']`</br>
JDI Locator: `label['Gold status']<input[type=checkbox]`</br>

XPath: `//*[contains(@class,'nav-menu')]//*[@data-role='header'][3]`</br>
JDI Locator: `.nav-menu [data-role=header][3]`</br>
