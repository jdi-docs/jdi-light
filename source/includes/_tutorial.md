# Tutorial
In this tutorial we’ll take a glance at [JDI Light](https://github.com/jdi-testing/jdi-light), a library that simplifies test automation, makes test run results stable, predictable and easy to maintain.<br/>

1. **Quick Start** — a short instruction on how to add JDI Light to your project and perform its basic configuration.<br/>
2. **JDI Light at a glance** — a few simple test examples with and without Page Objects. Typified UI Elements and logs in JDI Light.<br/>
3. **JDI Light Forms** — a small complex element example that showcases the primary benefits of using JDI Light.<br/>
4. **UI Elements and optimization** — a more sophisticated example elaborating on types of elements in JDI Light and demonstrating their capabilities.<br/>
5. **Reduce the amount of code with JDI Light** — a concise example of how JDI Light can decrease the amount of code threefold compared to Selenium.
Demonstrates that you can write clear and stable tests with 3 times less effort.<br/>

## 1. Quick Start
1. Adding JDI Light to your projects
2. A brief configuration overview <br/>

Let’s start from the beginning by adding JDI Light to our test project and going through the setup step by step.<br/>

_Note: JDI Light ships with a [template project](https://github.com/jdi-templates/jdi-light-testng-template) that helps to save setup time._
### Maven Dependencies

```java 
<dependency>
    <groupId>com.epam.jdi</groupId>
    <artifactId>jdi-light-html</artifactId>
    <version>RELEASE</version>
</dependency>
```
First, we need to add JDI Light to the _dependency_ section of our ***pom.xml*** file: <br/>

_The latest version can be found in the [Maven Central Repository](https://search.maven.org/classic/#search%7Cga%7C1%7Cjdi-light)_.
<br/><br/>

### Configuration

That’s all! We don’t need to explicitly configure anything else to start working. By default, JDI Light will download Chrome driver automatically, set it up and run it as soon as we try to access the first page.

We can change the default settings by altering the ***test.properties*** file (located within *src/test/resources* directory).

```java
src/test/resources/test.properties
driver=chrome
#driver.version=2.23 | LATEST
#timeout.wait.element=10
#timeout.wait.page=30
domain=https://jdi-testing.github.io/jdi-light/
#page.load.strategy=normal | eager | none
#browser.size=MAXIMIZE | 1024x762
...
```
Let’s have a detailed look at some options:

- **driver** — we can specify the driver used to run our tests. Common options include `chrome`, `firefox`, `ie`; we can also just put `${driver}` here and read the driver name from the command line.<br/>
- **driver.version** — by default, JDI Light will download the latest version of a driver for us, but if we need a specific version we can put it here (in which case the framework will find and download exactly this version).<br/>
- **timeout.wait.element** — the maximum amount of time in seconds that will be spent waiting for an element on the opened page to load. The default element loading timeout is 10 seconds.<br/>
- **timeout.wait.page** — JDI Light automatically defines a newly opened page and uses this value as page loading timeout (it is usually greater than the element loading timeout). The default is 30 seconds.<br/>
- **domain** — web application root URL (used when our tests work with a single application). Can also be read from the command line if set up as `${domain}.` <br/>
- **page.load.strategy** — similarly to Selenium, page loading strategies are: `normal`, `eager`, `none`. <br/>
- **browser.size** — browser window size. By default, JDI Light will maximize the browser window, but we can set the exact size.<br/>
- **screenshot.strategy** = `off` | `on failure` | `on assert` | `new page` — determines when screenshots are taken; it's used by AllureLogger.class and its sub/superclasses. Can be overwritten in test project.<br/>
- **html.code.strategy** = `off` | `on failure` | `on assert` | `new page` — logs the last processed element HTML code.<br/>
- **requests.strategy** = `off` | `on failure` | `on assert` | `new page` — logs 4ХХ, 5ХХ errors in the console.<br/>
- **allure.steps** = `true` — turn on the steps for Allure.<br/>


_Note: you can find more examples in the [documentation](https://jdi-docs.github.io/jdi-light/#driver-settings)._

<a href="https://github.com/jdi-tutorials/01-jdi-light-intro/blob/master/src/test/resources/test.properties" target="_blank">See the examples on Github</a>

## 2. JDI Light at a glance
1. Simple Open page test
2. No Page Objects test example
3. Page Objects test example

### Let's start

```java
@Test
public void openJDITestSite() {
    openUrl("https://jdi-testing.github.io/jdi-light/");
}
```
OK, now let’s write our first test case. We can open the [JDI test site](https://jdi-testing.github.io/jdi-light) by using a static method `openUrl()` of the `WebPage` class.

`WebPage` provides essential methods to work with a browser: `getUrl()`, `getTitle()`, `back()`, `forward()`, `getHtml()`, `refresh()`. It also provides methods that allow to _scroll up / down / left / right / to page top / to page bottom_ or _zoom_ the page.

### Simple test scenario
```java
@Test
public void loginSimpleTest() {
    openUrl("https://jdi-testing.github.io/jdi-light/");
    $("img#user-icon").click();
    $("#name").sendKeys("Roman");
    $("#password").sendKeys("Jdi1234");
    $("#login-button").click();
    $("#user-name").is().displayed();
}
```
Now we can write a more involved typical test: log in to a page.

Every test should contain an assertion, so let’s add it to our test.

Code like this is easy to write. However, it will inevitably become **hard to maintain** as the number of tests grows and elements used get repeated throughout the tests.

For example, if we have an element found by `$(".menu-about a")` locator in more than 10 tests and its locator gets changed, we must go through all the tests and adjust the locator.

Page Objects are here to help us!

<a href="https://github.com/jdi-tutorials/01-jdi-light-intro/blob/master/src/test/java/nopageobjects/tests/JDILightExample.java" target="_blank">See the examples above on Github</a></br>

### Page Objects

```java
public class HomePage extends WebPage {
    @FindBy(css = "img#user-icon") public WebElement userIcon;
    @FindBy(id = "name") public WebElement name;
    @FindBy(id = "password") public WebElement password;
    @FindBy(id = "login-button") public WebElement loginButton;
    @FindBy(id = "user-name") public WebElement userName;
}
public class HomePage extends WebPage {
    @UI("img#user-icon") public static Link userIcon;
    @UI("#name") public static TextField name;
    @UI("#password") public static TextField password;
    @UI("#login-button") public static Button loginButton;
    @UI("#user-name") public static Text userName;
}
```
Let’s develop our first simple Page Object and see how the test case will look like. We have our Home Page with several elements on it:

- **user icon** — clicking on it opens the login form. </br>
- **name, password** — two text fields in the login form. </br>
- **login button** — clicking on it starts a login attempt. </br>
- **user name** — element that will appear after a successful login. </br>

In order to make the code simple, in JDI Light we can use a unified annotation, `@UI("...")`. It handles both CSS and XPath locators, thus reducing the amount of code.

It's also a good use case for one of the main JDI Light features: typified elements like `TextField`, `Button` and `Text`.

The other great news is that we can make our Page Object elements `static` and keep tests clearer and more obvious. <br/>

```java
@JSite("https://jdi-testing.github.io/jdi-light/")
public class SiteJdi {
    @Url("/") public static HomePage homePage;
    @Url("/contacts") @Title("Contact Form")
    public static ContactsPage contactPage;
}
```
Page Objects in JDI Light are called **UI Objects** and extend standard Selenium Page Objects' capabilities with typified elements like `TextField`, `Button`, `Text` etc. They also carry additional meta-information about a page, like URL and title. 
Pretty simple and obvious, isn’t it?

Page URLs are relative to the site domain specified in the `@JSite` annotation or in ***test.properties*** file.

_Note: We won't be calling `ContactsPage` methods in this example; it is put here to demonstrate the usage of `@Url` and `@Title` annotations._ 

```java
public interface TestsInit {
    @BeforeSuite(alwaysRun = true)
    static void setUp() {
        initElements(SiteJdi.class);
    }
}
```
And the last thing to consider before writing a test: all UI Objects of our application are initialized at once. We can do it with just a single line of code in the setup method that runs before all tests.

_Note: in other frameworks we have to call `initElements()` for each Page Object._

```java
public class PageObjectExample implements TestsInit {
    @Test
    public void loginTest() {
        homePage.open();
        userIcon.click();
        name.sendKeys("Roman");
        password.sendKeys("Jdi1234");
        loginButton.click();
        userName.assertThat().displayed();
    }
}

[ STEP 09:30.825] : Open 'Home Page'(url=https://jdi-testing.github.io/jdi-light/) (SiteJdi.homePage (url=https://jdi-testing.github.io/jdi-light/; title=))
[ STEP 09:37.188] : Click on 'User Icon' (HomePage.userIcon (css='img#user-icon'))
[ STEP 09:37.291] : Input 'Roman' in 'Name' (HomePage.name (css='#name'))
[ STEP 09:37.539] : Input 'Jdi1234' in 'Password' (HomePage.password (css='#password'))
[ STEP 09:37.756] : Click on 'Login Button' (HomePage.loginButton (css='#login-button'))
[ STEP 09:37.860] : Assert that 'User Name' is displayed (HomePage.userName (css='#user-name'))

[ STEP 11:16.923] : Open 'Home Page'(url=https://jdi-testing.github.io/jdi-light/)
[ STEP 11:22.983] : Click on 'User Icon'
[ STEP 11:23.088] : Input 'Roman' in 'Name'
[ STEP 11:23.369] : Input 'Jdi1234' in 'Password'
[ STEP 11:23.598] : Click on 'Login Button'
[ STEP 11:23.688] : Assert that 'User Name' is displayed
```
Now we can write our test using these UI Objects and execute it.

- This test scenario is pretty clear and references the actual UI elements.<br/>
- We can easily update elements placed in UI Objects without going through all the tests.<br/>
- We have all metadata about pages in one place and can open and validate pages without URL and title duplication in the test code.<br/>
- JDI Light tests are stable and will not fail in cases where Selenium throws exceptions (like _StaleElementException_ or _NoSuchElementException_)<br/><br/>
- We get the following text in the log: <br/>

It lists exactly what we do in our test with all the details and without any extra effort on our part. Fabulous! <br/>

We can change the log level to `STEP` (just add `logger.setLogLevel(STEP)` to the `setUp()` method) and remove the details. The resulting log will be fit to share with a Customer, a Business Analyst or a Manual QA to let them know what our automated tests verify.

<a href="https://github.com/jdi-tutorials/01-jdi-light-intro" target="_blank">See PageObject examples in PageObjectExample.java on Github</a>

## 3. JDI Light Forms
1. Simple login test example. DataClass example<br/>
2. Login Form in Data Driven Test approach<br/>
3. Page Objects test example<br/>

### Standard Login form

```java
public class LoginForm extends Form<User> {
    @UI("#name") TextField name;
    @UI("#password") TextField password;
    @UI("#login-button") Button loginButton;
}
public class JDISite {
    @Url("/") public static HomePage homePage;
    public static LoginForm loginForm;
    ...
}
@Test
public void loginTest() {
    userIcon.click();
    loginForm.loginAs(ROMAN);
    userName.is().displayed();
}
public class User extends DataClass<User> {
    public String name, password;
}
```
Now we will optimize the previous example using *forms*. <br/>
Let's move the login form elements to a separate UI Object — `LoginForm`.<br/>
Then we'll set `LoginForm` as a root UI Object in our `JDISite` class.<br/><br/><br/><br/><br/><br/>

Now we can rewrite our test in the following way:

<a class="github-button" href="https://github.com/jdi-testing/jdi-light" data-icon="octicon-star" data-size="large" data-show-count="true" aria-label="Star jdi-testing/jdi-light on GitHub">I Like it!</a><br/>

`ROMAN` is a business entity of class `User` associated with Login Form. `User` class is a simple data class with two `String` fields that have the same names as `TextField` elements in `LoginForm`.

Aligning data class field names with form field names works for every kind of form field that supports fill-like interaction: `TextField`, `TextArea`, `Checkbox`, `DropDown` etc.

_This gets covered more in depth in <a href="https://jdi-docs.github.io/jdi-light/?java#ui-elements-on-contact-form" target="_blank">Contact Form example</a>._<br/>

```java
  User ROMAN = new User().set(c -> {
      c.name = "Roman"; c.password = "Jdi1234";
  } );
Output: ROMAN.toString() --> User(name:Roman; password:Jdi1234)
new User().equals(new User());
```
Any class can be used as data class, but extending it from *DataClass* (`User extends DataClass<User>` in this case) gives us additional benefits:

- It won't be necessary to keep the same order of fields in the data class and the form.<br/>
- Two data class instances will be compared by equality of their fields and not by reference (so NOT like it would have been with the `equals()` method). <br/>
- There will be a good-looking `toString()` representation of the data class instance based on its fields.<br/>

<a href="https://github.com/jdi-tutorials/01-jdi-light-intro" target="_blank">See this example in LoginExample.java on Github</a>

### Cover Login Form with Data-Driven tests

```java
public class UsersDataProvider {
    public static User NO_PASSWORD = new User().set(c -> c.name = "Roman");
    public static User NO_CREDENTIALS = new User().set(c -> {
        c.name = ""; c.password = "";}
    );
    public static User WRONG_CREDENTIALS = new User().set(c -> {
        c.name = "Alex"; c.password = "Password";}
    );
    ...
}

public class LoginExample implements TestsInit {
    @BeforeMethod
    public void before() {
        loggedOut();
        loginFormShown();
    }
    @Test
    public void failedLoginTest1() {
        loginForm.loginAs(NO_PASSWORD);
        userName.is().hidden();
    }
    @Test
    public void failedLoginTest2() {
        loginForm.loginAs(WRONG_CREDENTIALS);
        userName.is().hidden();
    }
    @Test
    public void failedLoginTest3() {
        loginForm.loginAs(NO_CREDENTIALS);
        userName.is().hidden();
    }
    ...
}
```
This lets us easily increase the amount of different tests.

Let's cover login functionality with tests checking the following cases:

1) No password; 2. Wrong credentials; 3. No credentials.

In order to do this we will create a separate file (***UsersDataProvider.java***) for our test data and put `User` entities with the corresponding field values there.

_Note: if you leave some fields `null`, this data will not be provided._
_Since we would like to validate empty values in fields for `NO_CREDENTIALS` user we'll have to set them as empty strings._

Now we can write our tests:

_Note: we don't need to write any other code except test scenarios. Already written UI Objects will be enough._

_Note: In order to be sure that_ **the user is logged out** _and_ **login form is opened** _before each test we can add these conditions as `loggedOut()` and `loginFormShown()`States in `@BeforeMethod`._

<a href="https://github.com/jdi-tutorials/02-jdi-light-forms-elements" target="_blank">See this example in LoginExample.java on Github</a>
<br/><br/><br/><br/><br/><br/><br/><br/><br/>
### Failed Login Form tests with Data Provider

```java
public class UsersDataProvider {
    ...
    @DataProvider(name = "failedUsers")
    public static Object[][] failedUsers() {
        return new User[][]{{NO_PASSWORD}, {NO_CREDENTIALS}, {WRONG_CREDENTIALS}};
    }
```
But the scenarios in previous example are pretty much the same. The only difference is the test data. We can simplify our tests using _DataProvider_.<br/>
Let's add `failedUsers()` method that returns test data for our cases as a 2D array of `User` instances to our ***UsersDataProvider.java*** file, then mark this method with `@DataProvider(name = "failedUsers")`.<br/>

```java
public class UsersDataProvider {
    ...
    @Test(dataProvider = "failedUsers", dataProviderClass = UsersDataProvider.class)
    public void dataFailedLoginTest(User user) {
        loginForm.loginAs(user);
        userName.is().hidden();
    }
```
As a next step, we will create one common test scenario that accepts `User` instance as a parameter. <br/>

And the last step is just to link our test to the data provider method using `@Test` annotation attributes.<br/>

That's it! If we run this scenario, it will execute 3 tests that validate different cases of login failure. This way you can easily manage same scenarios with different test data, increase testing coverage, add new data sets or update them without changing the actual tests. It's that simple!

<a class="github-button" href="https://github.com/jdi-testing/jdi-light" data-icon="octicon-star" data-size="large" data-show-count="true" aria-label="Star jdi-testing/jdi-light on GitHub">I Like it!</a><br/> 
<a href="https://github.com/jdi-tutorials/02-jdi-light-forms-elements" target="_blank">See this example in LoginExample.java on Github</a>

## 4. UI Elements and optimization
1. Main UI Element types in JDI Light and a few examples.<br/>
2. Complex Contact Form example.<br/>
3. Check and verify Form methods. Errors in logs.<br/>
4. 5 Ways to describe Form with a complex Selenium example (17 lines) to 1 line Form<br/>

### UI Elements on Contact Form
We've had a quick look at JDI Light; now let's look closer at UI Elements. In JDI we have 3 kinds of elements:

1. **Common Elements**: `Button`, `TextField`, `Text`, `Checkbox` etc. Some of them we have already used in Login Form. All of these elements have simple structure and can be described using one locator or Selenium element.</br></br>
_Note: See the full list and more details in <a href="https://jdi-docs.github.io/jdi-light/?java#common-elements">Documentation</a>_<br/></br>
2. **Complex elements** like `Dropdown`, `Checklist`, `RadioButtons`, `MultiSelect`, `DataList` etc. They represent actual UI elements that encompass the functionality of multiple Common Elements. For example, `Dropdown` may be regarded as combination of elements that represent _value_, _caret (expand dropdown) arrow_ and _list of options_;
`Checklist` is basically a list of `Checkbox` elements.<br/></br>
_Note: See the full list and more details in <a href="https://jdi-docs.github.io/jdi-light/?java#complex-elements">Documentation</a>_<br/></br>
3. **Composite elements** are typified Page Objects. These are `WebPage`, `Form`, `Section`: classes having Common, Complex Elements or sub-sections as their fields.<br/></br>
_Note: See the full list and more details in <a href="https://jdi-docs.github.io/jdi-light/?java#composite-elements">Documentation</a>_<br/>

Let's look at an example: Contact Form on <a href="https://jdi-testing.github.io/jdi-light/contacts.html" target="_blank">Contacts page</a>.

This form, compared to the Login Form, has more different UI elements. Let's describe it.<br/>

```java
public class ContactForm extends Form<ContactInfo> {
    @UI("#passport") Checkbox passport;
    @UI("#name") TextField name;
    @UI("#last-name") TextField lastName;
    @UI("#position") TextField position;
    @UI("#passport-number") TextField passportNumber;
    @UI("#passport-seria") TextField passportSeria;
    @UI("#accept-conditions") public Checkbox acceptConditions;
    @UI("#description") TextArea description;
    @UI("button[type=submit]") Button submit;
    ...
}
```
Here we have <b><u>Common</u></b> elements:

5 `TextField` elements (`name`, `lastName`, `position`, `passportNumber`, `passportSeria`)<br/>
<img src="images/tutorial/textfield.png" alt="TextField" width="200px"><br/>
2 `Checkbox` elements (`passport`, `acceptConditions`)<br/>
<img src="images/tutorial/checkbox.png" alt="Checkbox" width="100px"><br/>
1 `TextArea` (`description`)<br/>
<img src="images/tutorial/textarea.png" alt="TextArea" width="200px"><br/>
1 `Button` (`submit`)<br/>
<img src="images/tutorial/button.png" alt="Button" width="100px"><br/>

```java
public class ContactForm extends Form<ContactInfo> {
    ...
    @UI("#gender") Dropdown gender;
    @UI("#religion") Combobox religion;
    @UI("#weather") MultiDropdown weather;
}
// Selenium implementation that takes 21 lines of code instead of 1 line in JDI Light, namely:
// @UI("#weather") MultiDropdown weather
@FindBy(css ="#weather .caret") WebElement weatherExpand;
@FindBy(css ="#weather label") List<WebElement> weatherList;
@FindBy(css ="#weather button") WebElement weatherValue;
@FindBy(css ="#weather ul") WebElement weatherIsExpanded;
private boolean weatherIsExpanded() {
    return weatherIsExpanded.getAttribute("style").equals("display: block;");
}
public void select(String value) {
    if (!weatherIsExpanded())
        weatherExpand.click();
    String[] values = value.split(", ");
    for (String val : values) {
        for (WebElement listOption : weatherList) {
            if (listOption.getText().trim().equals(val))
                listOption.click();
        }
    }
}
public String getValue() {
    return weatherValue.getText();
}
```
And <b><u>Complex</u></b> elements:

`Dropdown` (gender) — An element with one selectable value, expand arrow and a list of options. <br/>
<img src="images/tutorial/dropdown.png" alt="Dropdown" width="200"><br/>
`Combobox` (religion) — Mix of `Dropdown` and `TextField`. You can select a value from a list of options or enter your own value.<br/>
<img src="images/tutorial/combobox.png" alt="Combobox" width="200"><br/>
`MultiDropdown` (weather) — Dropdown that allows selection of multiple options. We also provide an example of Selenium implementation of equivalent functionality for comparison.</br>
<img src="images/tutorial/multiselect.png" alt="MultiDropdown" width="200"><br/>

```java
@Url("/contacts") @Title("Contact Form")
public class ContactPage extends WebPage {
    @UI("#contact-form") public static ContactForm contactForm;
}
```
And the Contact Form itself is a <b><u>Composite</u></b> UI Object (PageObject with additional capabilities in JDI).

We will call the Contact Form placed on another Composite Page Object a **Contact Page**.

Pay attention to the fact that Contact Form and Contact Page have the additional meta-information:

- `@Url` and `@Title` for Contact Page. <br/>
- Locator for Contact Form specified with the `@UI` annotation. It ensures that all elements that belong to Contact Form Page Object are searched only within the context of Contact Form: in case when there are multiple elements with a locator like `"button[type=submit]"` on the webpage (for example, this locator is valid for the logout button on Contact Page), it will be the element belonging to Contact Form that gets found.<br/>

```java
public class ContactInfo extends DataClass<ContactInfo> {
    public String passport, name, lastName, position, passportNumber, 
        passportSeria, gender, religion, weather, acceptConditions, description;
}
```  
The next important points of attention are `ContactPage extends WebPage` and `ContactForm extends Form<ContactInfo>` inheritance declarations. They grant these Page Objects webpage and form functionality and allow access to their meta-information.<br/>
`ContactInfo`, the data class to be used with `ContactForm`, looks pretty much the same as the data class for Login Form. Each field that is used when filling the form is a `String`.</br>

```java
@UI("img#user-icon") public static Link userIcon;
@UI("#user-name") public static Text userName;
@UI(".sidebar-menu span") public static Menu sideMenu;
```  
We also have a few <u>Common</u> elements that are placed directly in Site:

1. `Link` element `userIcon` and `Text` element `userName`; we have already been using them in earlier tests.</br>
2. One new <u>Complex</u> element, `Menu`, representing the list of links in the left sidebar. This element is also found by one locator but contains 16 menu items, and you can also select the item you need by its name defined in `MenuOptions` enum (found in _src/main/java/jdisite/enums_).</br>

### Contact Form test scenario
```java
@Test
public void simpleContactFormTest() {
    sideMenu.select("Contact form");
    contactPage.checkOpened();
    contactForm.submit(FULL_CONTACT);
    contactForm.check(FULL_CONTACT);
}
```
Now let's write a complex test that:

- Opens the Contacts Page by selecting a corresponding menu option<br/>
- Verifies that this page has the correct URL and title<br/>
- Fills all 11 different elements in the Contact Form with some values<br/>
- And verifies that the form has been filled correctly<br/>

This is just as simple as filling the Login Form! </br>
<a class="github-button" href="https://github.com/jdi-testing/jdi-light" data-icon="octicon-star" data-size="large" data-show-count="true" aria-label="Star jdi-testing/jdi-light on GitHub">Amazing!</a><br/>

```java
public static ContactInfo FULL_CONTACT = new ContactInfo().set(c -> {
    c.name = "Roman"; c.lastName = "Full Contact"; c.position = "ChiefQA"; 
    c.passportNumber = 4321; c.passportSeria = 123456; 
    c.description = "JDI - awesome UI automation tool";

    c.gender = "Female"; c.religion = "Other"; c.weather = "Sun, Snow";
    c.acceptConditions = true; c.passport = true;
    }
);
```
The most complicated part is creating the test data that we would like to utilize:

```java
public static ContactInfo SIMPLE_CONTACT = new ContactInfo().set(c -> {
    c.name = "Roman"; c.lastName = "Iovlev"; c.position = "ChiefQA";
    c.passportNumber = 4321; c.passportSeria = 123456; }
);
@Test
public void simpleContactFormTest() {
    sideMenu.select(ContactForm);
    contactPage.checkOpened();
    contactForm.submit(SIMPLE_CONTACT);
    contactForm.check(SIMPLE_CONTACT);
}
```
Now if we would like to fill only the `TextField` elements, we only need to change our test data.

_Note: In the second example we use `MenuOptions` enum value (`ContactForm`) to select a `sideMenu` item. It reduces the chance of making a mistake by limiting the choice of options. The enum is found at ***src/main/java/jdisite/enums***._

<a href="https://github.com/jdi-tutorials/03-jdi-light-forms-ui-elements" target="_blank">See this example in ContactFormExamples.java on Github</a><br/><br/><br/><br/><br/><br/><br/><br/><br/>

### Failed form example in logs

```java
@Test
public void failCheckExample() {
    sideMenu.select(ContactForm);
    contactPage.checkOpened();
    contactForm.fill(FULL_CONTACT);
    contactForm.acceptConditions.uncheck();
    contactForm.submit();
    List<String> result = contactForm.verify(FULL_CONTACT);
    assertThat(result, Matchers.hasSize(1));
    assertThat(result, hasItem("Field 'acceptConditions' (Actual: 'false' <> Expected: 'true')"));
}
```
Now let's fail the validation of our form and see how JDI Light will display the failure results. We can build upon the previous example and just change some field before the check. Let's write a test that does this, execute it and observe the results. 

Forms in JDI have two methods which verify the entered data:

- `check` — commonly used verification that validates a form, then throws an exception indicating all the incorrect values if there are any.<br/>
- `verify` — has the same behavior as `check`, but instead of throwing an exception this method returns a string list containing messages with expected/actual values for each incorrectly filled field, so it's up to you to decide how to manage the result.

In our example we revert one field, `acceptConditions`, to an unchecked state, and the resulting exception gets presented in a clear way (pictured to the right):<br/>
> "Field 'acceptConditions' (Actual: 'false' <> Expected: 'true')"

<a href="https://github.com/jdi-tutorials/03-jdi-light-forms-ui-elements" target="_blank">You can find this example in ContactFormExamples.java on Github</a><br/>

### Using Forms in different ways

```java
    @BeforeMethod
    public void before() {
        loggedOut();
        if (loginForm.isHidden())
            userIcon.click();
    }
```
We've had a first look at UI Elements in JDI Light and at the capabilities of Forms, and now we can look deeper at Form initialization and see how it can help you write less code.

Let's start with a simple Form — Login.

We're planning to have a lot of tests with the preconditions _"User is logged out"_ and _"Login form is opened"_, so let's write a corresponding `@BeforeMethod` state for this set of test cases.<br/><br/>

```java
//Example 1
public class SeleniumLoginForm {
    @FindBy(id = "name") public WebElement name;
    @FindBy(id = "password") public WebElement password;
    @FindBy(id = "login-button") public WebElement loginButton;
    
    public void loginAs(User user) {
        name.sendKeys(user.name);
        password.sendKeys(user.password);
        loginButton.click();
    }
}
//Example 2
public class SeleniumLoginForm {
    ...
    // 3 lines for Elements
    public void loginAs(User user) {
        if (user.name != null) {
            name.clear();
            name.sendKeys(user.name);
        }
        if (user.password != null) {
            password.clear();
            password.sendKeys(user.password);
        }
        loginButton.click();
    }
}
//now we should add the class SeleniumLoginForm on JDISite.java:
public static SeleniumLoginForm seleniumLoginForm;

public class SelenideLoginForm {
    UIElement name = $("#name"), 
          password = $("#password"), 
       loginButton = $("#login-button");
    // + Same 11 rows for methods like in Selenium
    ...
}
//now we should add the class SelenideLoginForm on JDISite.java:
public static SelenideLoginForm selenideLoginForm;

public class LoginForm extends Form<User> {
    @UI("#name") TextField name;
    @UI("#password") TextField password;
    @UI("#login-button") Button loginButton;
}
//now we should add the class LoginForm on JDISite.java:
public static LoginForm loginForm;

public class LoginFormSmart extends Form<User> {
    TextField name, password;
    Button loginButton;
}
//now we should add the class LoginFormSmart on JDISite.java:
public static LoginFormSmart loginFormSmart;
```
In JDI Light we can describe a Form in different styles:

**Selenium** — a typical Page Object with `WebElement`s and `@FindBy` annotations, Selenium actions upon Web Elements and no inheritance from JDI Light classes. Code like that will still work in pure Selenium projects without JDI.<br/>

See _Example 1_<br/>

But for cases <a href="https://jdi-docs.github.io/jdi-light/?java#cover-login-form-with-data-driven-tests" target="_blank">where we would like to fill a form with different values</a>, but it's not guaranteed that all form fields are empty, we need to extend our `loginAs` method and make it more complex and stable. <br/>

See _Example 2_<br/>

<a href="https://github.com/jdi-tutorials/04-jdi-light-different-forms/blob/master/src/main/java/jdisite/sections/SeleniumLoginForm.java" target="_blank">See the example in Selenium LoginForm.java on Github</a><br/><br/><br/><br/><br/><br/><br/><br/><br/><br/><br/><br/><br/>

**JQuery/Selenide** — Selenide or jQuery-like style, where instead of `@FindBy` annotations you can use direct initialization.<br/>
<a href="https://github.com/jdi-tutorials/04-jdi-light-different-forms/blob/master/src/main/java/jdisite/sections/SelenideLoginForm.java" target="_blank">See the example in SelenideLoginForm.java on Github</a><br/><br/><br/><br/>

**Regular JDI Light Form** — typical JDI Forms with *typified elements*, `@UI` annotations, extending from Form without overriding `fill`/`check` methods.<br/>
<a href="https://github.com/jdi-tutorials/04-jdi-light-different-forms/blob/master/src/main/java/jdisite/sections/LoginForm.java" target="_blank">See the example in LoginForm.java on Github</a><br/><br/><br/>

**JDI Light Form with smart locators** — If it's possible to align field names with locators, you can use smart locators for elements and remove locator annotations from Forms. This also allows you to declare form fields with the same type in one line, separated by commas.

[See more details and examples for Smart locators in documentation](https://jdi-docs.github.io/jdi-light/?java#smart-locators)<br/>
<a href="https://github.com/jdi-tutorials/04-jdi-light-different-forms/blob/master/src/main/java/jdisite/sections/LoginFormSmart.java" target="_blank">See example in LoginFormSmart.java on Github</a>

```java
on JDISite.java >> public static Form<User> lightLoginForm;
```
**If your Form has only `TextField` elements and buttons**, instead of describing a UI object you can simply write a single line in the corresponding page class or in the root Site class:<br/>

This allows us to construct Login Forms in 1 line instead of 17!<br/>

<a class="github-button" href="https://github.com/jdi-testing/jdi-light" data-icon="octicon-star" data-size="large" data-show-count="true" aria-label="Star jdi-testing/jdi-light on GitHub">Nice job man!</a>

## 5. Reduce the amount of code with JDI Light
1. Initialize Driver in Selenium and JDI Light
2. Page Objects code
3. Compare Login Form code
4. Reduce Complex Contact Form Page Object code from 97 lines (Selenium) to 8 lines of code (JDI Light)
5. Test Data in Selenium and JDI Light
6. Discuss example results

Now we know enough about Forms, so let's see how this can help us write code faster (by writing less code).

Let's try to code in Selenium the same [Fill Contact Form test scenario](https://jdi-docs.github.io/jdi-light/?java#contact-form-test-scenario) that we have already covered with JDI Light:

- Open Home Page by URL.<br/>
- Open Contact Page by selecting a menu item.<br/>
- Validate that this Page has the correct URL and title.<br/>
- Fill all 11 different elements in the contact form with values.<br/>
- And verify that the form is filled correctly.<br/>

_Note: You can find all the Selenium code <a href="https://github.com/jdi-tutorials/05-jdi-light-forms-selenium" target="_blank">here</a>.<br/>_
_The same scenario with JDI Light is found <a href="https://github.com/jdi-tutorials/05-jdi-light-forms-reduce-code" target="_blank">here</a>.<br/>_

In this example I will develop Selenium code solution as effectively as possible while trying to keep the same look and feel of the test scenario.

At the same time, we will see how this code can be optimized using knowledge we got from [Use Forms in different ways](https://jdi-docs.github.io/jdi-light/?java#use-form-in-different-ways) topic.<br/>

I will list the amount of lines of code we wrote for each action in brackets.<br/>

### 1. Set up and run Chrome driver

```java
public static WebDriver DRIVER;
public static void runChromeDriver() {
    System.setProperty("webdriver.chrome.driver", "C:\\Selenium\\chromedriver.exe");
    DRIVER = new ChromeDriver();
    DRIVER.manage().window().maximize();
}
```
**Selenium:** (6 lines of code)<br/>
Here it is done with a simple method, `runChromeDriver()`.

_Note: To run the driver in Selenium you need to download the latest version from <a href="https://chromedriver.storage.googleapis.com/index.html" target="_blank">the official site </a> and put it in Selenium folder._<br/>

**JDI Light:** (0 lines of code)<br/> 
You don't need to write any code for this. By default, the latest version of ChromeDriver will be downloaded automatically.

### 2. Create Page Objects for Home and Contact pages

```java
public class HomePage {
    public static final String URL = "https://jdi-testing.github.io/jdi-light/";
    @FindBy(id ="user-icon") public static WebElement userIcon;
    @FindBy(id ="user-name") public static WebElement userName;
}
public static HomePage homePage = initElements(DRIVER, HomePage.class);

public class ContactPage {
    public static final String URL = "https://jdi-testing.github.io/jdi-light/contacts.html";
    public static final String TITLE = "Contact Form";    
    public static ContactForm contactForm = initElements(DRIVER, ContactForm.class);
}
public static ContactPage contactPage = initElements(DRIVER, ContactPage.class);
```
**Selenium:** (12 lines of code)<br/>
Using `PageFactory.initElements()`, we can create simple Page Objects with minimum code like in the example.<br/>

If you want to have cool pages in Selenium, you can use <a href="https://github.com/jdi-tutorials/05-jdi-light-forms-selenium/blob/master/src/main/java/jdisite/pages/BasePage.java" target="_blank">BasePage</a>, which handles all the standard stuff related to opening and checking pages.

_Note: I hope this "BasePage" approach will be useful for your Selenium projects._<br/><br/><br/><br/><br/><br/><br/><br/>

```java
@Url("/")
public class HomePage extends WebPage {
    @UI("#user-icon") public static Link userIcon;
    @UI("#user-name") public static Text userName;
}
public static HomePage homePage;

@Url("/contacts") @Title("Contact Form")
public class ContactPage extends WebPage {
    @UI("#contact-form") public static ContactForm contactForm;
}
public static ContactPage contactPage;
```
**JDI Light:** (11 lines of code)<br/> 
In JDI Light we already have all the functions related to webpages. You can find them in the `WebPage` class, so you just need to extend your Page Object from it and use `@Url` and `@Title` annotations to set page metadata.

The code for UI Objects in Selenium and JDI Light in this case looks pretty much the same.<br/> 
However, there are several points worth noting:

- Locators are a little bit shorter thanks to `@UI` annotations.<br/> 
- Forms can have root locators, so their sub-element locators can be simplified.<br/> 
- We don't have to initialize each page with the `PageFactory.initElements()` method, like Selenium does it.<br/> 

```java
public class LoginForm {
    @FindBy(id = "name") WebElement name;
    @FindBy(id = "password") WebElement password;
    @FindBy(id = "login-button") WebElement loginButton;

    public void loginAs(User user) {
        if (user.name != null) {
            name.clear();
            name.sendKeys(user.name);
        }
        if (user.password != null) {
            password.clear();
            password.sendKeys(user.password);
        }
        loginButton.click();
    }
    public boolean isHidden() {
        return !name.isDisplayed();
    }
}
public static LoginForm loginForm = initElements(DRIVER, LoginForm.class);
```
### 3. Create a simple Login Form

**Selenium:** (21 lines of code)<br/> 
This form contains WebElements (`name`, `password`, `loginButton`) and actions like `loginAs()` and `isHidden()`.

<a href="https://github.com/jdi-tutorials/05-jdi-light-forms-selenium/blob/master/src/main/java/jdisite/sections/LoginForm.java" target="_blank">Code example</a><br/>
<br/><br/><br/><br/><br/><br/><br/><br/><br/><br/><br/>

**JDI Light**(1 line of code)<br/> 

```java
public static Form<User> loginForm;
```
In JDI Light you don't need to create a UI Object for such a simple form. Just declare it in your site class.

_Note: And, of course, you don't need to initialize this form._

### 4. Creating a complex Contact Form
In total, we have 97 lines of code for Selenium and only 8 lines of code in JDI Light, but let's go step by step and see the difference in details.

<a href="https://github.com/jdi-tutorials/05-jdi-light-forms-selenium/blob/master/src/main/java/jdisite/sections/ContactForm.java" target="_blank">Selenium Contact Form code (97)</a><br/>
<a href="https://github.com/jdi-tutorials/05-jdi-light-forms-reduce-code/blob/master/src/main/java/jdisite/sections/ContactForm.java" target="_blank">JDI Light Contact Form code (8)</a><br/>

_Note: Unfortunately, we can't use one-liner Form in this case because the form has elements of different kinds, but we still can use short form descriptions with Smart locators. Just describe element types and names and use one-line initialization with your root `"#contact-form"` locator._<br/>

```java
    @FindBy(css ="#contact-form #name") WebElement name; 
    // +4 more TextFields
    @FindBy(css ="#contact-form #accept-conditions") WebElement acceptConditionsCheckbox;
    @FindBy(css ="#contact-form #passport") WebElement passportCheckbox;
    @FindBy(css ="#contact-form #description") WebElement descriptionText;
    @FindBy(css ="#contact-form [type=submit]") WebElement submitButton;
```
**Selenium:** (9 lines of code)<br/> 
In Selenium we have to describe all elements of the form. This is easy to do for simple elements like `TextField`, `Checkbox`, `TextArea` and buttons.

_Note: You must add **#contact-form** to some element locators._

And because `WebElement` doesn't give us any clues about the type of element, it is a good practice to denote an element type in a variable name.
<br/><br/>

```java
    TextField name, lastName, position, passportNumber, passportSeria;
    Checkbox passport, acceptConditions;
    TextArea description;
```
**JDI Light:** (3 lines of code)<br/> 
In JDI Light we just need to describe the types of elements and list them for each type. In this example, locators align with field names, so we can utilize Smart locators without writing explicit ones.<br/><br/>

```java
    // Dropdown
    @FindBy(id = "gender") WebElement gender;
    private Select gender() { 
        return new Select(gender); 
    }
    // Combobox
    @FindBy(id = "religion") WebElement religion;
    // MultiDropdown
    @FindBy(css ="#weather .caret") WebElement weatherExpand;
    @FindBy(css ="#weather label") List<WebElement> weatherList;
    @FindBy(css ="#weather button") WebElement weatherValue;
    @FindBy(css ="#weather ul") WebElement weatherIsExpanded;
    private boolean weatherIsExpanded() {
        return weatherIsExpanded.getAttribute("style").equals("display: block;");
    }
    private void selectWeather(String value) {
        if (!weatherIsExpanded())
            weatherExpand.click();
        String[] values = value.split(", ");
        for (String val : values) {
            for (WebElement listOption : weatherList) {
                if (listOption.getText().trim().equals(val))
                    listOption.click();
            }
        }
    }
```
**Selenium:** (23 lines of code)<br/> 
The situation with Complex elements is more interesting:

Instead of `Dropdown` we can use `Select` class from _selenium-support_ package and `WebElement` + `gender()` method. These are enough to handle all actions.

Instead of `Combobox` we can use a one-line `WebElement` (just using it as a standard `TextField`).

But instead of `MultiDropdown` we'll need to add 4 WebElements and a few methods: `select` and `isExpanded`.
The general problem with Complex elements in standard Selenium approach is that we have to create methods like these for every equivalent of `Dropdown`, `MultiDropdown` etc. JDI Light allows to define an element once (or pick one from element library) and then just use it in one line in all Page Objects.

<a href="https://github.com/jdi-tutorials/05-jdi-light-forms-selenium/blob/master/src/main/java/jdisite/elements/MultiDropdown.java" target="_blank">MultiDropdown example</a>

```java
    Dropdown gender;
    Combobox religion;
    MultiDropdown weather;
```
**JDI Light:** (3 lines of code)<br/> 
In JDI Light it is as simple as for Common elements. 

_Note: They are so short that we could write them in one line, but let's keep each on its own line._<br/><br/>

```java
public void submit(ContactInfo contact) {
    if (contact.name != null) {
        nameTextField.clear();
        nameTextField.sendKeys(contact.name);
    }
    // +6 more elements, 4 lines each including Combobox and TextArea
    // Dropdown
    if (contact.gender != null) {
        gender().selectByVisibleText(contact.gender);
    }
    // MultiDropdown
    if (contact.weather != null) {
        selectWeather(contact.weather);
    }
    // Checkboxes
    if (contact.passport && !passportCheckbox.isSelected() ||
            !contact.passport && passportCheckbox.isSelected())
        passportCheckbox.click();
    if (contact.acceptConditions && !acceptConditionsCheckbox.isSelected() ||
            !contact.acceptConditions && acceptConditionsCheckbox.isSelected())
        acceptConditionsCheckbox.click();
    submitButton.click();
}
public void check(ContactInfo contact) {
    //  20 lines to validate contact
}
```
**Selenium:** (65(37) lines of code)<br/> 
We'll need to write two methods: `submit` and `check`.

Like with the Login Form, in order to manage different test data fed into the Contact Form we'll have to check values for `null`. We can avoid this check in only one case (for example, just fill all fields with `null` and save a few lines of code).<br/>
Using a flexible approach, we need 43 + 22 = 65 lines of code.

We can improve this code by using a common method that clears and sends keys to an abstract WebElement: this will reduce our code to 55 lines.

If we remove `null` validations, it will make our methods less universal, but will save additional 18 lines and reduce the code to 37 lines for Form methods.<br/>

<a href="https://github.com/jdi-tutorials/05-jdi-light-forms-selenium/blob/master/src/main/java/jdisite/sections/ContactForm.java" target="_blank">Selenium Contact Form code (97)</a><br/>
<a href="https://github.com/jdi-tutorials/05-jdi-light-forms-selenium/blob/master/src/main/java/jdisite/sections/ShortContactForm.java" target="_blank">Short Selenium Contact Form code (69)</a><br/><br/><br/><br/><br/><br/><br/>

**JDI Light:** (0 lines of code)<br/> 
In JDI Light we don't need methods for these typical actions. Standard Form actions are flexible and allow to operate with any kind of data.<br/>
<a href="https://github.com/jdi-tutorials/05-jdi-light-forms-reduce-code/blob/master/src/main/java/jdisite/sections/ContactForm.java" target="_blank">JDI Light Contact Form code (8)</a><br/>

### 5. Test Data

```java
public class User {
    public String name, password;
    // + 3 lines constructor
    // + 8 lines set methods
    // + 16 lines to Override equals, hashCode and toString
}
public class ContactInfo {
    public String name, lastName, position, gender, religion, weather, description;
    public int passportNumber, passportSeria;
    public boolean passport, acceptConditions;
    // + 16 lines constructor
    // + 44 lines set methods
    // + 30 lines to Override equals, hashCode and toString
}
public static User ROMAN = new User("Roman", "Jdi1234");
public static ContactInfo SIMPLE_CONTACT = new ContactInfo()
    .setName("Roman").setLastName("Iovlev").setPosition("ChiefQA")
    .setPassportNumber(4321).setPassportSeria(123456)
    .setDescription("JDI - awesome UI autoamtion tool");
public static ContactInfo FULL_CONTACT = new ContactInfo(
    "Roman", "Full Contact", "ChiefQA", "Female", "Other", 
    "Sun, Snow", "JDI - awesome UI automation tool",
    4321, 123456, true, false
);
```
**Selenium:** (134 lines of code)<br/> 
For a simple `User` entity with two fields we should have at least one constructor, but it would be nice to override `equals()`, `hashCode()` and `toString()` methods in order to have a log-friendly representation of an entity and ability to compare the actual and expected results by class fields. Additionally, if we want to have the ability to set up different data, we have to create setter methods for each field.

You can generate all of these methods using "Generate" option in IntelliJ IDEA (right-click the data class and select "Generate").

We need at least 7 lines of code, but for a reusable entity we should write 31 lines of code.<br/>
The same holds true for `ContactInfo` and for any Data entity in the standard approach. For `ContactInfo` the full declaration is more important because we plan to make use of more fields, and it will take more lines of code.

After these manipulations, we can create transparent test data.

<a href="https://github.com/jdi-tutorials/05-jdi-light-forms-selenium/blob/master/src/main/java/jdisite/entities/User.java" target="_blank">User data</a><br/>
<a href="https://github.com/jdi-tutorials/05-jdi-light-forms-selenium/blob/master/src/main/java/jdisite/entities/ContactInfo.java" target="_blank">ContactInfo data</a><br/>
<a href="https://github.com/jdi-tutorials/05-jdi-light-forms-selenium/blob/master/src/main/java/jdisite/entities/DefaultData.java" target="_blank">User Roman</a><br/>
<a href="https://github.com/jdi-tutorials/05-jdi-light-forms-selenium/blob/master/src/test/java/com/jdi/test/data/DefaultDataProvider.java" target="_blank">Full and Simple Contact info</a><br/>


```java
public class User extends DataClass<User> {
    public String name, password;
}
public class ContactInfo extends DataClass<ContactInfo> {
    public String name, lastName, position, gender, religion, weather, description;
    public int passportNumber, passportSeria = -1;
    public boolean passport, acceptConditions;
}
public static User ROMAN = new User().set(c -> {
    c.name = "Roman"; c.password = "Jdi1234";}
);
public static ContactInfo SIMPLE_CONTACT = new ContactInfo().set(c -> {
    c.name = "Roman"; c.lastName = "Iovlev"; c.position = "ChiefQA";
    c.passportNumber = 4321; c.passportSeria = 123456;
    c.description = "JDI - awesome UI autoamtion tool"; }
);
public static ContactInfo FULL_CONTACT = new ContactInfo().set(c -> {
    c.name = "Roman"; c.lastName = "Full Contact"; c.position = "ChiefQA";
    c.religion = "Other"; c.weather = "Sun, Snow"; c.acceptConditions = true;
    c.gender = "Female"; c.passportNumber = 4321; c.passportSeria = 123456;
    c.passport = true; c.description = "JDI - awesome UI automation tool"; }
);
```
**JDI Light:** (22 lines of code)<br/> 
To create Test Data in JDI Light, we can use `DataClass`. It allows us to create different test data, compare data entities, print their meaningful representations and at the same preserve code clearness.

No constructors, no method overriding and with all functions in place thanks to `DataClass`.

<a href="https://github.com/jdi-tutorials/05-jdi-light-forms-reduce-code/blob/master/src/main/java/jdisite/entities/User.java" target="_blank">User data</a><br/>
<a href="https://github.com/jdi-tutorials/05-jdi-light-forms-reduce-code/blob/master/src/main/java/jdisite/entities/ContactInfo.java" target="_blank">ContactInfo data</a><br/>
<a href="https://github.com/jdi-tutorials/05-jdi-light-forms-reduce-code/blob/master/src/test/java/com/jdi/test/data/DefaultDataProvider.java" target="_blank">Test Data</a><br/>
<br/><br/><br/><br/><br/><br/><br/><br/><br/>

### 6. Conclusion 

```java
// Selenium Init
@BeforeSuite(alwaysRun = true)
static void setUp() {
    runChromeDriver();
    DRIVER.navigate().to(HomePage.URL);
}
// JDI Light Init
@BeforeSuite(alwaysRun = true)
static void setUp() {
    initElements(JDISite.class);
    homePage.open();
}
// Selenium Test Scenarios
@BeforeMethod
public void before() {
    loggedIn();
    selectInMenu("Contact form");
}
@Test
public void submitContactDataTest() {
    assertEquals(DRIVER.getCurrentUrl(), ContactPage.URL);
    assertEquals(DRIVER.getTitle(), ContactPage.TITLE);
    contactForm.submit(FULL_CONTACT);
    contactForm.check(FULL_CONTACT);
}
@Test
public void submitContactSimpleDataTest() {
    assertEquals(DRIVER.getCurrentUrl(), ContactPage.URL);
    assertEquals(DRIVER.getTitle(), ContactPage.TITLE);
    contactForm.submit(SIMPLE_CONTACT);
    contactForm.check(SIMPLE_CONTACT);
}
// JDI Test Scenarios
@BeforeMethod
public void before() {
    loggedIn();
    sideMenu.select("Contact form");
}
@Test
public void submitContactFormTest() {
    contactPage.checkOpened();
    contactForm.submit(FULL_CONTACT);
    contactForm.check(FULL_CONTACT);
}
@Test
public void simpleContactFormTest() {
    contactPage.checkOpened();
    contactForm.submit(SIMPLE_CONTACT);
    contactForm.check(SIMPLE_CONTACT);
}
```
As a result, we have test scenarios that look pretty much the same in Selenium and JDI Light, but the amount of code and time spent writing the code is significantly different.

You can find the complete project code in the _"result"_ branch of <a href="https://github.com/jdi-tutorials/05-jdi-light-forms-selenium/tree/result" target="_blank">Selenium</a> and <a href="https://github.com/jdi-tutorials/05-jdi-light-forms-reduce-code/tree/result" target="_blank">JDI Light</a> example repositories.<br/>

**Statistical results:**<br/>
<img src="images/tutorial/selenium-results.png" alt="Selenium Statistic" width="400"><br/>
<img src="images/tutorial/jdi-light-results.png" alt="JDI Light Statistic" width="400">

In our example, we wrote **3 times less amount of code with JDI Light**.

This means that if a regular Test Automation engineer writes these tests using **Selenium**, it will take about **1 working day**, while using **JDI Light** this work will only take **2-3 hours**. In other words, an engineer can **automate 3 times more test cases** in the same period of time.

_Note: You can try to automate this test scenario by yourself from scratch without clues and check how much time this will take in your case._

But JDI Light does not only save your time. Less amount of code **increases code clearness**.

In addition, if you run test scenarios with JDI Light, you will **get logs of all your actions** in a readable format. If you would like to have the same format of logs in Selenium, you need to write additional 30-50 lines of code for this example and spend 5-10% of your total effort on logs.

_Note: JDI Light removes only waste code and keeps all the business-relevant parts in place._ <br/><br/>
**Lesser amount of code, stable tests and clear logs will reduce maintenance effort during regression testing** and **increase the credibility of your tests**, because with JDI Light, once tests are written, they will only fail in case of real application changes or performance issues, but not because of test instability.<br/>

## JDI Light in BDD Style (even for Manual QA)
<font color="olive">TBD</font>

## Create Custom controls
<font color="olive">TBD</font>

## JDI settings at a glance
<font color="olive">TBD</font>

## Test Framework structure
<font color="olive">TBD</font>
