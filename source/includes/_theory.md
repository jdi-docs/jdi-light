# Theory
## UI Elements
In order to effectively utilize <a href="https://github.com/SeleniumHQ/selenium/wiki/PageObjects" target="_blank">Page Objects pattern</a> we need to place elements on pages. Instead of Selenium `WebElement` objects that basically represent HTML tags, in JDI we introduce _UI Elements_ that represent UI elements interacted with by an actual user.

JDI provides the ability to create your own elements or use standard elements from a rich collection.

### Common elements

```java 
@UI("input[type=text].name") public TextField name;
@UI("h1") public Label label;
@UI("//div[@name='disclamer']") public Text disclaimer;
@UI("textarea[ui=description]") public TextArea description;
@UI("//*[text()='Submit']") public Button submit;
```
- Are used to make your Page Objects more intuitive and clear.
- An element's type and name is displayed in JDI logs and reports, which simplifies test maintenance.
- And, of course, we expect that the actions each UI element provides are specific to its type (for example, `Button` won't allow you to `sendKeys`, unlike `WebElement` or `SelenideElement`).

In JDI we have the following Common elements:

[Label](https://jdi-docs.github.io/jdi-light/?java#label), 
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
In addition to [Common elements](https://jdi-docs.github.io/jdi-light/?java#common-elements), JDI Light features Complex elements: they represent UI elements encompassing the functionality of multiple Common elements.

Some Complex elements may be regarded as sets of similar Common elements (something you would likely implement as `List<WebElement>` in Selenium). Typical examples of such Complex elements are `Menu`, `Checklist`, `RadioButtons`, or `Tabs`. 

_Note: You can still use lists of Common elements like `List<Button>` or `List<Label>` if need be._

Other Complex elements may be regarded as made up of different Common elements. Typical examples would be `Dropdown` or `Combobox`.

In JDI we have the following Complex elements:

[RadioButtons](https://jdi-docs.github.io/jdi-light/?java#radiobuttons),
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
Composite elements represent webpages or webpage sections and are mainly used as containers for elements and actions.
Typical examples of Composite elements are `WebPage` and `Section`.

Composite elements can also have a locator that defines a context for all elements within them. This means that all elements in a composite element will be searched relatively under this locator.

Composite elements might have predefined actions like `fill`, `submit` and `check` for `Form`, or `open()`, `checkOpened()` for `WebPage`.

Remember that you can create your own Composite elements with JDI Light when you need to describe sections like Header, Navigation Bar, Footer, Sidebar, Advertisement Section or the main section of a page.</br>

In JDI we have the following Composite elements:
 
[Section](https://jdi-docs.github.io/jdi-light/?java#section),
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
_UI Objects_ extend the standard <a href="https://github.com/SeleniumHQ/selenium/wiki/PageObjects" target="_blank">Page Objects pattern</a> with [UI Elements](https://jdi-docs.github.io/jdi-light/?java#ui-elements) and allow users to split pages into sections.

A typical UI object structure consists of:

- A ***Site class*** that contains all the pages of an application and its common parts like header, footer or navigation panel.
- ***Page Objects*** extending `WebPage` and representing respective application pages.
- ***Composite elements*** (typically represented by `Section` objects or other [Composite elements](https://jdi-docs.github.io/jdi-light/?java#composite-elements)), acting as containers for other elements and smaller sections.
- ***UI Elements*** representing functional elements on a page utilized by the end user.


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
_Entity Driven Testing (EDT)_ is an approach that implies utilizing Business Entities instead of unnamed test data in the test scenarios.

EDT can be organically combined with Data Driven Testing that uses Business Entities as input with similar scenarios.

JDI Light natively supports EDT with `Form`, `Table` and `DataList`. See the examples in the right panel:

Example scenario:

```html
> Provide List<User> for test
0. Check that there is a user in the database
1. Log in with user data
2. Submit user data in Contact Us form
3. Get actual opening from vacancy table
4. Assert that actual opening equals to expected opening
```
Code example:

```html
@Test(dataProvider = “users")                      //>
public void formTest(User user) {
    DB.users.shouldHave(user);                     //0.
    loginForm.loginAs(user);                       //1.
    contactUsForm.submit(user);                    //2.
    Vacancy vacancy = vacancyTable.getEntity(3);   //3.
    Assert.areEquals(vacancy, expectedVacancy);    //4.
}
```

## Smart Locators
### Smart locators example
Let's assume you have a uniform method to locate most of the elements (for example, most of the elements involved in UI test automation have a predictable id, or a name, or a special attribute used to locate them.)

Let's assume you have `@UI("[ui=last-name]") public TextField lastName`  element in JDI. In this case you can simplify it to `public TextField lastName` and omit the locator.

Now for more complex example. Suppose you have the following HTML:

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
With pure Selenium, Page Object elements for that will look like this: 
</br></br></br></br></br></br>

```java
@UI("[ui=name]") public Textfield name;
@UI("[ui=last-name]") public Textfield lastName;
@UI("[ui=pin-code]") public Textfield pinCode;
@UI("[ui=promo-code]") public Textfield promoCode;
@UI("[ui=accept-conditions]") public Checkbox acceptConditions;
@UI("[ui=submit-button]") public Button submitButton;
```
In JDI Light with standard UI Objects the code gets more descriptive, but there still are duplications in locator and element names:
</br></br></br>

```java
public Textfield name, lastName, pinCode, promoCode;
public Checkbox acceptConditions;
public Button submitButton;
```
But by using smart locators you can write this without any duplications (without locators) in just a few lines.
Looks cool, doesn't it?

### Define smart locator using test.properties

```java
smart.locators="[ui=%s]"
smart.locators.toName=UPPER_SNAKE_CASE
```
You can set up your smart locators in the ***test.properties*** file the following way.</br>

First, assign a value to the `smart.locators` property:

- set it to `#%s` in case your smart locator translates to id </br>
- set it to `.%s` for classname </br>
- set it to `[name=%s]` for name (or swap `name` for any other attribute) </br>

Then, assign a value to the `smart.toName` property. Suppose that you have set `smart.locators` to `[ui=%s]`:

- `kebab-case` will provide `[ui=last-name]` locator for public WebElement `lastName`.</br>
- `camelCase` will provide `[ui=lastName]` locator for public WebElement `lastName`.</br>
- `snake_case` will provide `[ui=last_name]` locator for public WebElement `lastName`.</br>
- `PascalCase` will provide `[ui=LastName]` locator for public WebElement `lastName`.</br>
- `UPPER_SNAKE_CASE` will provide `[ui=LAST_NAME]` locator for public WebElement `lastName`.</br>

...or, if the property looks like `smart.locators=//*[text()='%s']`:

- `First Upper Case` will provide `//*[text()='Submit Form']` locator for public WebElement `submitForm`.</br>
- `ALL UPPER CASE` will provide `//*[text()='SUBMIT FORM']` locator for public WebElement `submitForm`.</br>

### Define a Smart Locator using WebSettings

```java
WebSettings.SMART_SEARCH_LOCATORS = asList("#%s");
WebSettings.SMART_SEARCH_NAME = StringUtils::toKebabCase;
// JDI Light style
WebSettings.SMART_SEARCH = el -> {
  String locatorName = toKebabCase(el.getName());
  UIElement element = $("[auto="+locatorName+"]", el.base().parent));
  element.setName(el.getName());
  return element.getWebElement();
}
// Selenium style
WebSettings.SMART_SEARCH = el -> {
  String locatorName = toKebabCase(el.getName());
  return getDriver.findElement(By.cssClass("[auto="+locatorName+"]"));
}
```
You can also set up Smart Locators in code using `WebSettings.SMART_SEARCH_NAME` and `WebSettings.SMART_SEARCH_LOCATORS` variables:

Or you can define by yourself what should be done when UI Element has no locator using `WebSettings.SMART_SEARCH`.
</br></br></br></br></br></br></br></br></br></br></br></br>

### Smart Annotations 
When your locators follow standard patterns you can use Smart Annotations to mark elements:

For `@UI("#last-name") TextField lastName;`</br>
use `@SId TextField lastName;`</br>

For `@UI(".contact-form") Form<CardData> contactForm;`</br>
use `@SClass Form<CardData> contactForm;`</br>

For `@UI("//*[text()='Submit Card']") Button submitCard;`</br>
use `@SText Button submitCard;`</br>

For `@UI("[name='accept-conditions']") Checkbox acceptConditions;`</br>
use `@SName Checkbox acceptConditions;`</br>

Or use `@Smart` annotation for any specific HTML attribute:

For `@UI("[data-type=data-multi-combobox]") MultiCombobox dataMultiCombobox;`</br>
use `@Smart("data-type") MultiCombobox dataMultiCombobox;`</br>
</br>

### Custom Smart Annotations
You can also always create your own annotation enabling smart behavior.

Let's assume you would like to use smart locators for buttons like `//button[text()='Button Text']`.

First, create a new annotation:

```html
SButton.java
@Retention(RetentionPolicy.RUNTIME)
@Target({ElementType.TYPE, ElementType.FIELD})
public @interface SButton {
}
```
Then set up the behavior for this annotation before you call `initSite`:

```html
@BeforeSuite(alwaysRun = true)
public static void setUp() {
    JDI_ANNOTATIONS.add("Buttons", aRule(SButton.class,
        (e, a) -> e.setLocator(format("//button[text()='%s']", splitCamelCase(e.getName())))));
    initSite(YourAwesomeSite.class);
```
That's all. Now we can write:

```html
@SButton public Button logIn, signIn, cancel, useVipAccess;
```
Instead of:

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
In order to control element behavior in JDI Light you can use the following standard annotations:

**@Root** — ignores all parent sections locators for this element and uses only locator that specified for element (including smart locators).</br>

**@Frame("frame-id")** or **@Frame({"frame-id", "div[name-adv]"})** — in case you have two or more frames above the element, use `driver.switchTo().frame(...)` before searching your element. Or call it multiple times if `@Frame` has list of locators. Can be used together with `@UI` locator.</br>

**@Css("div.dropdown")** — if your element has a CSS locator (deprecated, recommended to use universal `@UI` locator instead.)</br>

**@XPath("//div[text()='Submit']")** — if your element has an XPath locator (deprecated, recommended to use universal `@UI` locator instead.)</br>

**@ByText("Submit")** — used to locate elements by text (uses locator `".//*/text()[normalize-space(.) = %s]/parent::*"`.)</br>

**@WithText("Navigation")** — used to locate elements by text containing given substring (uses locator `".//*/text()[contains(normalize-space(.), %s)]/parent::*"`)</br>

**@ClickArea(...)** — specifies how click will be performed. Allowed values: `SMART_CLICK` (tries to find area where user able to click), `TOP_LEFT` (click top left corner of the element), `TOP_RIGHT` (click top right corner of the element), `BOTTOM_LEFT` (click bottom left corner of the element), `BOTTOM_RIGHT` (click bottom right corner of the element), `CENTER` (standard Selenium click in the center of the element), `JS` (using JS click).</br>

**@GetTextAs(...)** — specifies how getText will be performed. Allowed values: `TEXT` (`getText()`), `VALUE` (`getAttribute("value")`), `INNER` (`jsExecute("innerText")`), `LABEL` (using a label related to the element; good for checkboxes and radio buttons), `SMART_TEXT` (tries smart value search).</br>

**@SetTextAs(...)** — specifies how text input will be performed. Allowed values: `SEND_KEYS` (`sendKeys(...)`), `SET_TEXT` (set `value` attribute using JS), `CLEAR_SEND_KEYS` (`clear()` then `sendKeys(...)`).</br>

**@NoCache** — always get the element from the page. Do not use cache.</br>

**@WaitTimeout(sec)** — set _sec_ seconds implicit wait for the element.</br>

**@NoWait** — no element wait timeout; the element won't be found unless it's present on the page.</br>

**@Name(“Test”)** — sets the name of an element to the provided value.</br>

**@GetAny** — gets element without validation.</br>

**@GetVisible** — returns displayed element.</br>

**@GetVisibleEnabled** — returns displayed and enabled element.</br>

**@GetShowInView** — returns displayed and clickable element.</br>

**@PageName** — sets `pageName` variable for the element.</br>

**@SId** — sets smart ID locator, e.g `“By.cssSelector: #Test”`, where “Test” is the element's `id` attribute.</br>

**@SText** — sets smart text locator, e.g. `“By.xpath: .//*/text()[normalize-space(.) = "S Text"]/parent::*”`, where “SText” is the name of the element. Be aware that it’s creating a locator with white space for words starting with capital letter.</br>

**@SName** — sets smart name locator, e.g. for `“@Name(“Test”) @SName”` it will be `“By.cssSelector: [name='test']”`.</br>

**@Smart** — sets smart locator, e.g. for `“@Name(“Smart”) @Smart(“id”)”` it will be `“By.cssSelector: [id=’smart’]”`.</br>

**@SClass** — sets smart class locator, e.g. for `“@Name(“Test”) @SName”` it will be `“By.cssSelector: .test”`.</br>

**@UI** — for list UI locator, e.g. `@UI("img")`, see more examples in the previous section.</br>

**@FindBy** — an annotation that can have attributes such as: `css`, `tagName`, `linkText`, `partialLinkText`, `xpath`; `text`, `id`, `name`, `className`, `group`. Could be quickly changed to from Selenium `@FindBy` by changing the import line.</br>

**@VisualCheck** — adds the `“(“visualCheck”, “”)”` pair to params.

## JDI Locators (as simple as CSS, as powerful as XPath)

```java
@XPath("//div[contains(@class,'btn')]//*[text()='Submit']")
@UI("div.btn['Submit']")

@XPath("//*[contains(@class,'nav-menu')]//*[@data-role='header']//*[contains(text(),'Navigation menu')]")
@UI(".nav-menu [data-role=header][*'Navigation menu']")

@XPath("//label[text()='Gold status']/..//input[@type='checkbox']")
@UI("label['Gold status']<input[type=checkbox]")

@XPath("//*[contains(@class,'nav-menu')]//*[@data-role='header'][3]")
@UI(".nav-menu [data-role=header][3]")
```

With JDI Light you can use simple and fast CSS-like selectors with the power of XPath locators. Now you can search by text or index with CSS-like syntax or even move up the DOM tree.

See some examples below:

XPath: `//div[contains(@class,'btn')]//*[text()='Submit']`</br>
JDI Locator: `div.btn['Submit']`

XPath: `//*[contains(@class,'nav-menu')]//*[@data-role='header']//*[contains(text(),'Navigation menu')]`</br>
JDI Locator: `.nav-menu [data-role=header][*'Navigation menu']`</br>

XPath: `//label[text()='Gold status']/..//input[@type='checkbox']`</br>
JDI Locator: `label['Gold status']<input[type=checkbox]`</br>

XPath: `//*[contains(@class,'nav-menu')]//*[@data-role='header'][3]`</br>
JDI Locator: `.nav-menu [data-role=header][3]`</br>
