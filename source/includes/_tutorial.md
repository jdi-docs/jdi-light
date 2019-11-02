# Tutorial
In this tutorial we’ll take a glance at [JDI Light](https://github.com/jdi-testing/jdi-light), a library that simplifies test automation, makes test run results stable, predictable and easy to maintain.<br/>
1. **Quick Start** - a short instruction on how to add JDI Light to your project and perform its basic configuration.<br/>
2. **JDI Light at a glance** - a few simple test examples with and without Page Objects. Typified UI Elements and logs in JDI Light.<br/>
3. **JDI Light Forms** - a small complex element example that shows JDI Light basic benefits.<br/>
4. **UI Elements and optimization** - a more complex example elaborating on types of elements in JDI Light and demonstrating their capabilities.<br/>
5. **Reduce the amount of code with JDI Light** - a concise example of how JDI Light can decrease the amount of code three-fold compared to Selenium.
Shows that you can write clear and stable tests with 3 times less effort.<br/>

## 1. Quick Start
1. Adding JDI Light to your projects <br/>
2. A brief configuration overview <br/>

Let’s start from the beginning by adding JDI Light to our test project and going through the setup step-by-step.<br/>
_Note: JDI Light ships with a [template project](https://github.com/jdi-templates/jdi-light-testng-template) that can be used to save us some time for the setup._
### Maven Dependencies

```java 
<dependency>
    <groupId>com.epam.jdi</groupId>
    <artifactId>jdi-light-html</artifactId>
    <version>RELEASE</version>
</dependency>
```
First, we need to add JDI Light to the <i>dependency</i> section of our <b>pom.xml</b> file: <br/>
_The latest version can be found in the [Maven Central Repository](https://search.maven.org/classic/#search%7Cga%7C1%7Cjdi-light)_<br/>
<br/><br/>
### Configuration
That’s all! We don’t need to set anything up. By default, JDI Light will download Chrome driver automatically, set it up and run once we try to access the first page.<br/>
We can change the default settings placed in the <b>test.properties</b> file (<i>src/test/resources</i>)

```java
src/test/resources/test.properties
driver=chrome
#drivers.version=2.23 | LATEST
#timeout.wait.element=10
#timeout.wait.page=30
domain=https://jdi-testing.github.io/jdi-light/
#page.load.strategy=normal | eager | none
#browser.size=MAXIMIZE | 1024x762
...
```
Let’s look at some of them in details: <br/>
- **driver** –  we can set up where we would like to run our tests. Some common options are: <i>chrome</i>, <i>firefox</i>, <i>ie</i>… or we can just replace it with _${driver}_ and read the exact driver name from command line<br/>
- **drivers.version** – by default JDI Light will download the latest version of a driver for us, but if we need a specific version we can put it here (in this case the framework will find and download exactly the version specified)<br/>
- **timeout.wait.element** – timeout in seconds to wait for an element on the opened page. The default is 10 seconds<br/>
- **timeout.wait.page** – JDI Light automatically defines a newly opened page and in this case will use this timeout (usually it is more than for an element). The default is 30 seconds<br/>
- **domain** – web application root URL (used if we work with a single application in tests). Can be also read from the command line in the following way: _${domain}_ <br/>
- **page.load.strategy** – similarly to Selenium, strategies to load the page are: _normal, eager, none_ <br/>
- **browser.size** – the size of the tested browser. By default, JDI Light will maximize the browser, but we can set exact values
_Note: you can find more examples in the documentation._ <br/>
<a href="https://github.com/jdi-tutorials/01-jdi-light-intro/blob/master/src/test/resources/test.properties" target="_blank">See examples on Github</a>

## 2. JDI Light at a glance
1. Simple Open page test <br/>
2. No Page Objects test example<br/>
3. Page Objects test example<br/>

### Let's start

```java
@Test
public void openJDITestSite() {
    openUrl("https://jdi-testing.github.io/jdi-light/");
}
```
Ok, now let’s write our first test case. We can open the JDI Test Site (<u>https://jdi-testing.github.io/jdi-light/</u>) using a simple static method **openUrl()** in _WebPage_ class.<br/>
In _WebPage_ we can find other common methods that help us operate with browser:**getUrl(), getTitle(), back(), forward(), getHtml(), refresh()**.<br/>
And some not so widespread, e.g. **scroll up / down / left / right / top / bottom** and **zoom** the page.

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
Now we can write a more complex typical test: login to a Page.<br/>
Every test should end with an assertion, so let’s add it to our test. </br>
Code like this is easy to write, <b>but!</b> it will be hard to maintain as the number of tests will be growing and elements used in tests would have to be reused. <br/>
For example, if we have a **$(“.menu-about a”)** element in 10+ tests and its locator is changed, we must go through all the tests and correct the locator...</br>
<a href="https://github.com/jdi-tutorials/01-jdi-light-intro/blob/master/src/test/java/nopageobjects/tests/JDILightExample.java" target="_blank">See examples above on Github</a></br>
Page Objects will help us!

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
Let’s develop our first simple Page Object and see how the test case will look like. We have our Home Page with a few elements on it: <br/>
- **user icon** - to open Login Form <br/>
- **name, password** - two textfields in Login form<br/>
- **login button** - button for Login<br/>
- **user name** - element that will appear after successful login<br/>

In order to make the code simple in JDI Light, we can use a unified annotation, **@UI("...")**. It handles both Css and XPath locators, thus reducing the length of the code. <br/>
And of course, we can use one of the main JDI Light features: Typified elements like **TextField, Button** and **Text**. <br/>
And some more good news. We can make elements Page Object elements static and keep tests clearer and more obvious. <br/></br>

```java
@JSite("https://jdi-testing.github.io/jdi-light/")
public class SiteJdi {
    @Url("/") public static HomePage homePage;
    @Url("/contacts") @Title("Contact Form")
    public static ContactsPage contactPage;
}
```
Page Objects in JDI Light are called **UI Objects** and extend standard Selenium Page Objects' capabilities with typified elements like **Textfield, Button, Text** etc. and additional meta information for pages like **Url** and **Title**. 
Pretty simple and obvious, isn’t it? <br/>
<a class="github-button" href="https://github.com/jdi-testing/jdi-light" data-icon="octicon-star" data-size="large" data-show-count="true" aria-label="Star jdi-testing/jdi-light on GitHub">Nice!</a><br/>
Page urls are relative to the site domain written in the **@JSite** annotation or in the _test.properties_ (see section 2.2 of this article). <br/>
_Note: We don't need ContactsPage in this example but in order to illustrate **@Url** and **@Title** annotations it is placed here_ 

```java
public interface TestsInit {
    @BeforeSuite(alwaysRun = true)
    static void setUp() {
        initElements(SiteJdi.class);
    }
}
```
And the last thing before writing a test. It should be done only once – initialize all UI Objects for our application. We can do it in the setup method that runs before all tests, just in one line. <br/>
_Note: in other frameworks we should call initElements() for each Page Object_ <br/>
<br/><br/><br/>

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
Now we can write our test using these UI Objects and execute it<br/>
- This test scenario is pretty clear and based on real UI elements<br/>
- We can easily update UI Objects elements without going through all tests<br/>
- We have all meta data about pages in one place and can open them and validate them from tests without url and title duplication in code <br/>
- JDI Light tests are stable and will not fail in cases where Selenium throws exceptions (like _StaleElement_ or _NoSuchElement_)<br/><br/><br/><br/>
- We will get the following text in the log: <br/>
Exactly what we do in our test with all the details and without any effort from our side. Fabulous! <br/>
<br/>
We can change the log level to **STEP** (just add <i>logger.setLogLevel</i>(STEP) to the _setUp()_ method) and remove details. This log we can share with a Customer, a Business Analyst or a Manual QA and let them know what our Automated tests verify.<br/>
<a href="https://github.com/jdi-tutorials/01-jdi-light-intro" target="_blank">See PageObject examples in PageObjectExample.java on Github</a>

## 2.1 Non-Static Site initialization sample
1. Simple non-static Page Object
2. Automated test cases structure

### Simple non-static Page Object
```java
@JSite("https://jdi-testing.github.io/jdi-light/")
public class NonStaticSite {

    @Url("/index.html")
    @Title(value = "Home", validate = CheckTypes.CONTAINS)
    private HomePage homePage;

    @XPath("//*[@ui='label']")
    private UIElement userName;

    private WebElement userIcon;

    @Css("form")
    private LoginForm loginForm;


    public static String getUrl() {

        return getDriver().getCurrentUrl();
    }

    public void login() {

        if (!getUserName().isDisplayed()) {
            getUserIcon().click();
            getLoginForm().submit(DEFAULT_USER, "enter");
        }
    }

    public void shouldBeLoggedIn() {

        if (!getUrl().contains("https://jdi-testing.github.io/jdi-light/"))
            getHomePage().open();

        login();
    }

    public HomePage getHomePage() {
        return homePage;
    }

    public UIElement getUserName() {
        return userName;
    }

    public WebElement getUserIcon() {
        return userIcon;
    }

    public LoginForm getLoginForm() {
        return loginForm;
    }
}
```

### Automated test cases initialization sample
```java
public class NonStaticTestsInit {

    protected NonStaticSite nonStaticSite;

    @BeforeSuite(alwaysRun = true)
    public void setUp() {

        nonStaticSite = new NonStaticSite();
        PageFactory.initElements(nonStaticSite);

        nonStaticSite.getHomePage().open();
        WebSettings.logger.toLog("Non Static site page opened");
    }


    @AfterSuite(alwaysRun = true)
    public void cleanUp() {
        WebDriverUtils.killAllSeleniumDrivers();
    }
}
```

### Automated test case sample
```java
public class NonStaticSiteTests extends NonStaticTestsInit {

    @BeforeMethod
    public void before() {
        nonStaticSite.shouldBeLoggedIn();
        nonStaticSite.getHomePage().shouldBeOpened();
    }

    @Test
    public void isOpenedTest() {
        nonStaticSite.getHomePage().isOpened();
    }
}
```

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
Now we will optimize the previous example using forms. <br/>
Let's move elements placed in Login Form to a separate UI Object -  _LoginForm_<br/>
And set LoginForm as a root UI Object of our **JDI Site** class<br/><br/><br/>

Now we can rewrite our test in the following way:<br/>
_Note: **ROMAN** is a business entity User associated with Login Form<br/>_
<a class="github-button" href="https://github.com/jdi-testing/jdi-light" data-icon="octicon-star" data-size="large" data-show-count="true" aria-label="Star jdi-testing/jdi-light on GitHub">I Like it!</a><br/>

User class is a simple data class with two String fields that have the same names as TextFields in LoginForm. <br/>
This way you can fill any fillable Form elements: TextField, TextArea, Checkbox, DropDown etc. <br/>
_We will go through this in <a href="https://jdi-docs.github.io/jdi-light/?java#ui-elements-on-contact-form" target="_blank">Contact Form example</a>._<br/>

```java
  User ROMAN = new User().set(c -> {
      c.name = "Roman"; c.password = "Jdi1234";
  } );
Output: ROMAN.toString() --> User(name:Roman; password:Jdi1234)
new User().equals(new User());
```
For data class we can use any class but if we add **extends DataClass** we will get additional pros:<br/>
- Ability to fill User fields in any order and numbers without **set()** method constructors<br/>
- Compare two users by equality of their fields and not by reference (i.e. NOT using **equals()** method) <br/>
- Have a good **toString()** for User based on its fields<br/>
<a href="https://github.com/jdi-tutorials/01-jdi-light-intro" target="_blank">See this example in LoginExample.java on Github</a>

### Cover Login Form with Data Driven tests

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
And we can easily increase the amount of different tests<br/>
Let's cover login functionality with tests:<br/>
1. No Password<br/>
2. Wrong Credentials<br/>
3. No data<br/>
<br/>
In order to do this we will create a separate file (UsersDataProvider.java) for our Test Data and put User entities with required values there<br/>
_Note: if you leave some fields null, this data will not be provided_<br/>
_Because we would like to validate empty values in fields for NO_CREDENTIALS we should set them as empty strings_<br/>
<br/>
Now we can write our tests <br/>
_Note: we don't need to write any other code except test scenarios. Already written UI Objects is enough_<br/>
_Note: In order to be sure that before each test user **logged out** and **Login form is opened** we can add this as States in **@BeforeMethod**_<br/>
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
But scenarios in previous example are pretty much the same. The only difference is Test Data. We can simplify our tests with <i>DataProvider</i>.<br/>
Let's add a method to our UsersDataProvider.java file that returns test data for our cases in the form of a 2D array of Users and marks it with **@DataProvider** annotation with name **failedUsers**<br/>

```java
public class UsersDataProvider {
    ...
    @Test(dataProvider = "failedUsers", dataProviderClass = UsersDataProvider.class)
    public void dataFailedLoginTest(User user) {
        loginForm.loginAs(user);
        userName.is().hidden();
    }
```
As a next step, we will create one common test scenario and pass User as a parameter to it. <br/>
And the last step is just to link our test to the dataprovider method using **@Test** annotation parameters.<br/>
That's it!<br/>
If we run this scenario, we will get 3 tests that validate different cases of failed login.<br/>
This way you can easily manage same scenarios with different test data, increase testing coverage, add new data sets or update them without changing the actual tests<br/>
So simple! <a class="github-button" href="https://github.com/jdi-testing/jdi-light" data-icon="octicon-star" data-size="large" data-show-count="true" aria-label="Star jdi-testing/jdi-light on GitHub">I Like it!</a><br/> 
<a href="https://github.com/jdi-tutorials/02-jdi-light-forms-elements" target="_blank">See this example in LoginExample.java on Github</a>

## 4. UI Elements and optimization
1. Main UI Element types in JDI Light and a few examples.<br/>
2. Complex Contact Form example.<br/>
3. Check and verify Form methods. Errors in logs.<br/>
4. 5 Ways to describe Form with a complex Selenium example (17 lines) to 1 line Form<br/>

### UI Elements on Contact Form
We've had a quick look at JDI Light and now let's look closer at UI Elements. In JDI we have 3 kinds of elements:<br/>
1. **Common Elements**: Buttons, TextFields, Text, Checkbox etc. Some of them we have already used in Login Form. All of these elements are simple and can be described with one locator or Selenium element<br/>
_Note: See full list and more details in <a href="https://jdi-docs.github.io/jdi-light/?java#common-elements">Documentation</a>_<br/>
2. **Complex elements** like Dropdown, Checklist, RadioButtons, MultiSelect, DataList etc.. These elements work with the List of Common Elements of one or different types. E.g. Dropdown has _value_, _expand arrow_ and _list of options_;
Checklist - just a list of Checkboxes<br/>
_Note: See full list and more details in <a href="https://jdi-docs.github.io/jdi-light/?java#complex-elements">Documentation</a>_<br/>
3. **Composite elements** are typified Page Objects. These are WebPage, Form, Section and they are just simple classes with lists of UI Elements or sub-sections<br/>
_Note: See full list and more details in <a href="https://jdi-docs.github.io/jdi-light/?java#composite-elements">Documentation</a>_<br/>

Let's look at an example: Contact Form on <a href="https://jdi-testing.github.io/jdi-light/contacts.html" target="_blank">Contacts page</a> <br/>
This Form, contrary to Login Form, has more different UI elements. Let's describe it.<br/>

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
Here we have <b><u>Common</u></b> elements: <br/>
5 **TextField**s (name, lastName, position, passportNumber, passportSeria)<br/>
<img src="images/tutorial/textfield.png" alt="TextField" width="200px"><br/>
2 **Checkbox**es (passport, acceptConditions)<br/>
<img src="images/tutorial/checkbox.png" alt="Checkbox" width="100px"><br/>
1 **TextArea** (description)<br/>
<img src="images/tutorial/textarea.png" alt="TextArea" width="200px"><br/>
1 **Button** (submit)<br/>
<img src="images/tutorial/button.png" alt="Button" width="100px"><br/>

```java
public class ContactForm extends Form<ContactInfo> {
    ...
    @UI("#gender") Dropdown gender;
    @UI("#religion") Combobox religion;
    @UI("#weather") MultiDropdown weather;
}
// 21 Selenium lines of code that should be implemented instead of 1 line in JDI Light
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
And <b><u>Complex</u></b> elements:<br/>
**Dropdown** (gender) -  Element with one value, expand arrow and a list of options <br/>
<img src="images/tutorial/dropdown.png" alt="Dropdown" width="200"><br/>
**Combobox** (religion) - Mix of Dropdown and TextField. You set value from list of options or enter your own<br/>
<img src="images/tutorial/combobox.png" alt="Combobox" width="200"><br/>
**MultiDropdown** (weather) - Dropdown with ability to select a few options<br/>
As an example check the amount of code that should be implemented in Selenium for one Complex element<br/>
<img src="images/tutorial/multiselect.png" alt="MultiDropdown" width="200"><br/>

```java
@Url("/contacts") @Title("Contact Form")
public class ContactPage extends WebPage {
    @UI("#contact-form") public static ContactForm contactForm;
}
```
And the **Contact Form** itself is a <b><u>Composite</u></b> UI Object (PageObject with additional capabilities in JDI)<br/>
Contact Form placed on another Composite Page Object is called **Contact Page**<br/>
Pay attention to the fact that Contact Form and Contact Page have additional meta information: <br/>
- Already known **@Url** and **@Title** for WebPage and <br/>
- Locator in **@UI** annotation. This means that all elements placed in this Page Object will be found only in its context and even if their simple locator <u>"button[type=submit]"</u> is present on this page multiple times, it will be found correctly for this form<br/>

```java
public class ContactInfo extends DataClass<ContactInfo> {
    public String passport, name, lastName, position, passportNumber, 
        passportSeria, gender, religion, weather, acceptConditions, description;
}
```  
Next important points are **extend WebPage** and **extend Form\<ContactInfo\>**. They let these Page Objects perform actions to operate with elements on them and their related meta-info.<br/>
Data entity for this form (ContactInfo) looks pretty much the same as for Login Form. All fields that can be managed by Form are Strings.</br>

```java
@UI("img#user-icon") public static Link userIcon;
@UI("#user-name") public static Text userName;
@UI(".sidebar-menu span") public static Menu sideMenu;
```  
We also have a few <u>Common</u> elements directly on Site: <br/>
1. Already used <u>userIcon</u> **Link** and <u>userName</u> **Text** element</br>
2. And one new <u>Complex</u> element - **Menu** - a list of links in the left sidebar. This element is also described by one locator but returns 16 items and you can call the one you need by its name defined in <u>MenuOptions</u> enum</br>

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
Now let's write a complex test that:<br/> 
- Opens Contact Page from the menu<br/>
- Validates that this Page has correct url and title<br/>
- Fills all 11 different elements in this Complex form with some values<br/>
- And validates that the form has been filled correctly<br/><br/>
This is just as simple as filling the Login Form! <a class="github-button" href="https://github.com/jdi-testing/jdi-light" data-icon="octicon-star" data-size="large" data-show-count="true" aria-label="Star jdi-testing/jdi-light on GitHub">Amazing!</a><br/>

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
The most complex part is to create test data that we would like to utilize<br/>
<br/><br/><br/><br/><br/><br/><br/><br/>

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
Now if we would like to fill only TextFields, we should just change our test data.<br/>
_Note: In the second example we use select by enum value for sideMenu. It works the same as by text but allows us to choose from a limited list of options and reduce the chance of making a mistake_<br/>
<a href="https://github.com/jdi-tutorials/03-jdi-light-forms-ui-elements" target="_blank">See this example in ContactFormExamples.java on Github</a><br/><br/><br/><br/><br/>

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
Now let's fail the validation of our form and see how JDI Light will display the failure results. For this reason we can use the example above and just change some field before the check.<br/>
Let's write test code emulating this behaviour and then observe the results. Forms in JDI have two methods which verify data entered.<br/>
**check** - commonly used verification that validates forms and throws an exception at the end with all the wrong fields.<br/>
**verify** - has the same behaviour as _check_, but instead of throwing exxeption this method returns a list of failures for each failed field, and it is up to you to decide how to manage the result.<br/>
In our example we change one field, _acceptConditions_, to "uncheck", and the result of the test returns this exception in a clear way:<br/>
> "Field 'acceptConditions' (Actual: 'false' <> Expected: 'true')"

<a href="https://github.com/jdi-tutorials/03-jdi-light-forms-ui-elements" target="_blank">You can find this example in ContactFormExamples.java on Github</a><br/>

### Using Form in different ways

```java
    @BeforeMethod
    public void before() {
        loggedOut();
        if (loginForm.isHidden())
            userIcon.click();
    }
```
We've had a first look at UI Elements in JDI Light and at Form's capabilities and now we can look deeper at Form initialization and how this can help you write less code.<br/>
Let's start from a simple Form - Login.<br/>
We're planning to have a lot of tests which start from the point where a <u>User is logged out</u> and <u>Login form is opened</u>, so let's write a @BeforeMethod state for this set of test cases.<br/><br/>

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
In JDI Light we have different ways to describe a Form: <br/>
**Selenium** - a typical Page Object with **WebElement**s and **@FindBy** annotations, actions with them and without extending from something. Indeed, this code will work in original Selenium projects without JDI.<br/>
See Example 1<br/>
But for cases <a href="https://jdi-docs.github.io/jdi-light/?java#cover-login-form-with-data-driven-tests" target="_blank">where we would like to fill form with different values</a> and not always form fields are empty we need to extend our loginAs method an make it more complex and stable. <br/>
See Example 2<br/>
<a href="https://github.com/jdi-tutorials/04-jdi-light-different-forms/blob/master/src/main/java/jdisite/sections/SeleniumLoginForm.java" target="_blank">See example in Selenium LoginForm.java on Github</a><br/><br/><br/><br/><br/><br/><br/><br/><br/><br/><br/><br/><br/><br/><br/><br/>

**JQuery/Selenide** - Selenide or JQuery-like style, where instead of @FindBy annotations you can use direct initialization<br/>
<a href="https://github.com/jdi-tutorials/04-jdi-light-different-forms/blob/master/src/main/java/jdisite/sections/SelenideLoginForm.java" target="_blank">See example in SelenideLoginForm.java on Github</a><br/><br/><br/><br/><br/><br/>

**JDI Light Forms** - typical Forms in JDI with **typified elements**, **@UI** annotations, extending from Form and without **fill/check** methods<br/>
<a href="https://github.com/jdi-tutorials/04-jdi-light-different-forms/blob/master/src/main/java/jdisite/sections/LoginForm.java" target="_blank">See example in LoginForm.java on Github</a><br/>

**Smart JDI Forms** - If you can get a locator from a variable name, you can use Smart locators for elements and remove locator annotations from Forms. This also allows you to combine UI Fields with the same Type like **TextField**s in example<br/>
[See more details and exampels for Smart locators in documentation](https://jdi-docs.github.io/jdi-light/?java#smart-locators)<br/>
<a href="https://github.com/jdi-tutorials/04-jdi-light-different-forms/blob/master/src/main/java/jdisite/sections/LoginFormSmart.java" target="_blank">See example in LoginFormSmart.java on Github</a>

```java
on JDISite.java >> public static Form<User> lightLoginForm;
```
**Light Forms** - if your Form consists of only TextFields and buttons, you can avoid UI Object at all and just write one line in the respective page or in the root Site class<br/>
This allows us to construct Login Forms in 1 line instead of 17!<br/>
<a class="github-button" href="https://github.com/jdi-testing/jdi-light" data-icon="octicon-star" data-size="large" data-show-count="true" aria-label="Star jdi-testing/jdi-light on GitHub">Nice job man!</a>

## 5. Reduce the amount of code with JDI Light
1. Initialize Driver in Selenium and JDI Light
2. Page Objects code
3. Compare Login Form code
4. Reduce Complex Contact Form Page Object code from 97 lines (Selenium) to 8 lines of code (JDI Light)
5. Test Data in Selenium and JDI Light
6. Discuss example results

Now we know enough about Forms, so let's see how this can help us write code faster (less code)<br/>
Let's try to write a code in Selenium for the same scenario [Fill Contact Form test scenario](https://jdi-docs.github.io/jdi-light/?java#contact-form-test-scenario) what we done on JDI Light before<br/>
- Open Home Page by url<br/>
- Open Contact Page from menu<br/>
- Validate that this Page has correct url and title<br/>
- Fill all 11 different elements in this Complex form with some values<br/>
- And validate that form is filled correctly<br/>

_Note: You can find all the Selenium code <a href="https://github.com/jdi-tutorials/05-jdi-light-forms-selenium" target="_blank">here</a>.<br/>_
_The same scenario with JDI Light you can find <a href="https://github.com/jdi-tutorials/05-jdi-light-forms-reduce-code" target="_blank">here</a>.<br/>_

In this example I will develop Selenium code as effectively as possible while trying to keep the same look and feel of the test scenario.<br/>
In parallel, we will see how this code can be optimized using knowledge we got from [Use Form in different ways](https://jdi-docs.github.io/jdi-light/?java#use-form-in-different-ways) topic.<br/>
In brackets you can find the amount of lines of code we wrote for each action<br/>

### 1. Setup and run Chrome driver. ###

```java
public static WebDriver DRIVER;
public static void runChromeDriver() {
    System.setProperty("webdriver.chrome.driver", "C:\\Selenium\\chromedriver.exe");
    DRIVER = new ChromeDriver();
    DRIVER.manage().window().maximize();
}
```
**Selenium:** (6 lines of code)<br/>
Here it is done with a simple method - _runChromeDriver();_<br/> 
_Note: To run the driver in Selenium you need to download the latest version from <a href="https://chromedriver.storage.googleapis.com/index.html" target="_blank">the official site </a> and put it in **C:\Selenium** folder_<br/>

**JDI Light** (0 lines of code)<br/> 
You don't need to write code for this. The latest version of ChromeDriver will be downloaded automatically.

### 2. Create Page Objects for Home and Contact pages ###

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
Using _PageFactoryinitElements()_, we can create simple PageObjects with minimum code like in the example.<br/>
If you want to have cool pages in Selenium, you can use <a href="https://github.com/jdi-tutorials/05-jdi-light-forms-selenium/blob/master/src/main/java/jdisite/pages/BasePage.java" target="_blank">BasePage</a>, which handles all the standard stuff related to opening and checking pages.<br/>
_Note: I hope this "BasePage" approach will be useful for your Selenium projects.<br/><br/><br/><br/><br/><br/><br/><br/>

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
**JDI Light** (11 lines of code)<br/> 
In JDI Light we already have all the functions related to Pages. You can find them in the **WebPage** class, so you just need to extend your PageObject from it and use _@Url_ and _@Title_ annotations for setting Page metadata.<br/> 
Code for UI Objects in Selenium and JDI Light in this case looks pretty much the same.<br/> 
Just a few points for your attention.<br/> 
- Locators are a little bit shorter thanks to @UI annotations<br/> 
- Forms can have root locators that will simplify locators for subelements<br/> 
- In Selenium we must initialize each page with the _PageFactory.initElements()_ method<br/> 

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
### 3. Create a simple Login Form ###

**Selenium:** (21 loc)<br/> 
This form contains WebElements (name, password, loginButton) and actions like _loginAs()_ and _isHidden()_<br/>
<a href="https://github.com/jdi-tutorials/05-jdi-light-forms-selenium/blob/master/src/main/java/jdisite/sections/LoginForm.java" target="_blank">Code example</a><br/>
<br/><br/><br/><br/><br/><br/><br/><br/><br/><br/><br/><br/><br/><br/>

**JDI Light**(1 line of code)<br/> 

```java
public static Form<User> loginForm;
```
In JDI Light you don't need to create a UI Object for such a simple form. Just declare it in your site class.<br/>
_Note: And of course you don't need to initialize this form_

### 4. Creating a complex Contact Form ###
In total we have 97 lines of code for Selenium and only 8 lines of code in JDI Light, but let's go step-by-step and see the difference in details.<br/>
<a href="https://github.com/jdi-tutorials/05-jdi-light-forms-selenium/blob/master/src/main/java/jdisite/sections/ContactForm.java" target="_blank">Selenium Contact Form code (97)</a><br/>
<a href="https://github.com/jdi-tutorials/05-jdi-light-forms-reduce-code/blob/master/src/main/java/jdisite/sections/ContactForm.java" target="_blank">JDI Light Contact Form code (8)</a><br/>
_Note: Unfortunately, we can't use one string Form in this case because form has elements of different kinds, but we still can use short form descriptions with Smart locators. Just describe element types and names and one string initialization with your root locator **"#contact-form"**_<br/>

```java
    @FindBy(css ="#contact-form #name") WebElement name; 
    // +4 more TextFields
    @FindBy(css ="#contact-form #accept-conditions") WebElement acceptConditionsCheckbox;
    @FindBy(css ="#contact-form #passport") WebElement passportCheckbox;
    @FindBy(css ="#contact-form #description") WebElement descriptionText;
    @FindBy(css ="#contact-form [type=submit]") WebElement submitButton;
```
**Selenium:** (9 lines of code)<br/> 
In Selenium we should describe all elements of the form. This is easy to do for simple elements like TextFields, Checkboxes, TextArea and buttons.<br/>
_Note: you must add **#contact-form** to some element locators._<br/>
And because we have no idea about what UI element this WebElement represents, it is a good practice to add type as a part of its names
<br/><br/>

```java
    TextField name, lastName, position, passportNumber, passportSeria;
    Checkbox passport, acceptConditions;
    TextArea description;
```
**JDI Light** (3 lines of code)<br/> 
In JDI Light we just need to describe Types of elements and list them for each type. In this example we have well-written locators, so there's no need to write them for form.<br/><br/>

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
**Selenium:** (23 loc)<br/> 
More interesting situation with Complex elements: <br/>
For Dropdown we can use Select class from **selenium-support** package and WebElement + gender() method. These are enough to handle all actions.<br/>
For Combobox we can use a one-line WebElement just using it as a standard TextField.<br/>
But for MultiDropdown we'll need to write 4 WebElements and a few methods: select and isExpanded.
The general problem with Complex elements in standard Selenium approach is that we have to create such methods for every Dropdown, MultiDropdown etc. JDI Light allows to define an element once (or use it from the library) and then just use it in one line in all PageObjects<br/>
<a href="https://github.com/jdi-tutorials/05-jdi-light-forms-selenium/blob/master/src/main/java/jdisite/elements/MultiDropdown.java" target="_blank">Multidropdown example</a><br/><br/><br/><br/><br/><br/><br/><br/><br/><br/><br/><br/>

```java
    Dropdown gender;
    Combobox religion;
    MultiDropdown weather;
```
**JDI Light** (3 lines of code)<br/> 
In JDI Light it is as simple as for Common elements. 
_Note: They are so short that we can write them in one line, but let's keep each on its own line_<br/><br/>

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
For our needs we should write two methods: submit and check<br/>
As for the Login Form, in order to manage different Test Data via Contact Form we should check values for null. For only one case we can avoid this check (for example, just fill all fields with null and save a few lines of code).<br/>
Using a flexible approach, we need 43 + 22 = 65 lines of code.<br/>
We can improve this code by using a common method to clean and sendKeys for an abstract WebElement - this will reduce our code to 55 lines.<br/>
If we remove null validations, it will make our methods less common but will save additional 18 lines and reduce the code to 37 lines for Form methods.<br/>
<a href="https://github.com/jdi-tutorials/05-jdi-light-forms-selenium/blob/master/src/main/java/jdisite/sections/ContactForm.java" target="_blank">Selenium Contact Form code (97)</a><br/>
<a href="https://github.com/jdi-tutorials/05-jdi-light-forms-selenium/blob/master/src/main/java/jdisite/sections/ShortContactForm.java" target="_blank">Short Selenium Contact Form code (69)</a><br/><br/><br/><br/><br/><br/><br/>

**JDI Light** (0 lines of code)<br/> 
In JDI Light we don't need methods for these typical actions. Standard Form actions are flexible and allow to operate with any kind of data.<br/>
<a href="https://github.com/jdi-tutorials/05-jdi-light-forms-reduce-code/blob/master/src/main/java/jdisite/sections/ContactForm.java" target="_blank">JDI Light Contact Form code (8)</a><br/>

### 5. Test Data ###

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
For a simple User entity with two fields we should have at least one Constructor, but it would be nice to Override equals(), hashCode() and toString() methods in order to have the ability to log entity and compare the actual and expected results by their data.<br/>
Additionally, if we want to have the ability to setup different data, we should create set methods for each field.<br/>
You can generate all of these methods using "Generate" option in IntelliJ IDEA (Right-Click the data class and select "Generate").<br/>
We need at least 7 lines of code, but for a reusable entity we should write 31 lines of code.<br/>
The same holds true for ContactInfo and for any Data entity in standard approach. For ContactInfo the full declaration is more important because we plan to manipulate with more fields and it will take more lines of code.<br/>
After that manipulations we can create clear TestData<br/>
<a href="https://github.com/jdi-tutorials/05-jdi-light-forms-selenium/blob/master/src/main/java/jdisite/entities/User.java" target="_blank">User data</a><br/>
<a href="https://github.com/jdi-tutorials/05-jdi-light-forms-selenium/blob/master/src/main/java/jdisite/entities/ContactInfo.java" target="_blank">ContactInfo data</a><br/>
<a href="https://github.com/jdi-tutorials/05-jdi-light-forms-selenium/blob/master/src/main/java/jdisite/entities/DefaultData.java" target="_blank">User Roman</a><br/>
<a href="https://github.com/jdi-tutorials/05-jdi-light-forms-selenium/blob/master/src/test/java/com/jdi/test/data/DefaultDataProvider.java" target="_blank">Full and Simple Contact info</a><br/>
<br/><br/><br/>

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
**JDI Light** (22 lines of code)<br/> 
To create Test Data in JDI Light, we can use DataClass. It allows us to create different test data, compare, print it and at the same time preserve its clearness.<br/>
No constructors, no method overriding and with all functions in place with **DataClass**.<br/>
<a href="https://github.com/jdi-tutorials/05-jdi-light-forms-reduce-code/blob/master/src/main/java/jdisite/entities/User.java" target="_blank">User data</a><br/>
<a href="https://github.com/jdi-tutorials/05-jdi-light-forms-reduce-code/blob/master/src/main/java/jdisite/entities/ContactInfo.java" target="_blank">ContactInfo data</a><br/>
<a href="https://github.com/jdi-tutorials/05-jdi-light-forms-reduce-code/blob/master/src/test/java/com/jdi/test/data/DefaultDataProvider.java" target="_blank">Test Data</a><br/>
<br/><br/><br/><br/><br/><br/><br/><br/><br/>

### 6. Conclusion ###

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
As a result, we have Test scenarios that look pretty much the same in Selenium and JDI Light, but the amount of code and time spent writing the code is significantly different.<br/>
You can find the complete project code in the _"result"_ branch of <a href="https://github.com/jdi-tutorials/05-jdi-light-forms-selenium/tree/result" target="_blank">Selenium</a> and <a href="https://github.com/jdi-tutorials/05-jdi-light-forms-reduce-code/tree/result" target="_blank">JDI Light</a> example repositories.<br/>

Statistical results:<br/>
<img src="images/tutorial/selenium-results.png" alt="Selenium Statistic" width="400"><br/>
<img src="images/tutorial/jdi-light-results.png" alt="JDI Light Statistic" width="400"><br/>
In our example, we wrote **3 times less amount of code with JDI Light**. <br/>
This means that if a regular Test Automation engineer writes these tests using **Selenium**, it will take him about **1 working day**, while using **JDI Light** this work will only take him **2-3 hours**. **Or** he can **automate 3 times more test cases** in the same period of time.<br/>
_Note: You can try to automate this test scenario by yourself from scratch without clues and check how much time this will take you personally._<br/><br/>
But JDI Light does not only save your time. Less amount of code **increases code clearness**.<br/>
In addition, if you run test scenarios on JDI Light, you will **get logs of all your actions** in a readable format. If you would like to have the same level of logs in Selenium, you need to write additional 30-50 lines of code for this example and spend 5-10% of your effort on logs.<br/>
_Note: JDI Light removes only waste code and keeps all the important business parts in place._ <br/><br/>
**Less amount of code, stable tests and clear logs will reduce maintanance efforts during regressive testing** and **increase respect to your tests**, because with JDI Light, once tests are written, they will only fail in case of real application changes or performance issues, but not because of test instability.<br/>

## JDI Light in BDD Style (even for Manual QA)
TBD

## Create Custom controls
TBD

## JDI settings at a glance
TBD

## Test Framework structure
TBD
