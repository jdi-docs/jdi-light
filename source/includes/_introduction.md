# Introduction
## Simple JDI examples
### Create a simple Login test
First of all, let's see how JDI solves typical problems. Let's start with Login, since most tests start with signing in.

You can find a Java code example <a href='https://github.com/jdi-examples/jdi-introduction' target="_blank">here</a>.

**Test Scenario**

```java 
@Test
public void loginTest() {
    homePage.open();
    userIcon.click();
    loginForm.loginAs(DEFAULT_USER);
    homePage.checkOpened();
}
```
1. Open Home Page (<a href='https://jdi-testing.github.io/jdi-light/index.html' target="_blank">https://jdi-testing.github.io/jdi-light/index.html</a>)
2. Click on User Icon (to open login dialog)
2. Log in as a default user:
    - Enter 'Roman' in login text field
    - Enter 'Jdi1234' in password text field
    - Press 'Enter'
3. Verify that Home Page has been opened

```
[22:17.102  STEP] : Open 'Home Page'(url=>https://jdi-testing.github.io/jdi-light/index.html)
[22:23.617  STEP] : Click on 'User Icon'
[22:23.727  STEP] : Login as User (userName:epam; password:1234)
[22:24.516  STEP] : Check that 'Home Page' is opened (url CONTAINS '/index.html'; title EQUALS 'Home Page')
```
So simple! But there's more to it. Try to run this test in your IDE and see what you get...

 - A detailed log in the console output (pictured to the right; nice, isn't it?)
 - Log file containing the same log (*src/test/.logs/*) in case you'd like to view the test execution results separately *(requires **log4j2.xml** file in src/test/resources)*
 - A neat Allure report of your test execution! *(requires proper Allure settings in **pom.xml**)*
![Allure Report](../images/intro/allure-report.png)
![Allure Log](../images/intro/allure-report-log.png)

Just move the *allure-results* folder to your local folder and run ***Maven > Plugins > Allure > allure:serve*** (see picture below). <br>
<img src="images/intro/allure-serve.png" alt="Allure Serve" width="300px">

```java 
@JSite("https://jdi-testing.github.io/jdi-light/")
public class JdiTestSite {
    public static HomePage homePage;
}
@BeforeSuite(alwaysRun = true)
public static void setUp() {
    initElements(JdiTestSite.class);
}

@Url("/index.html") @Title("Home Page")
public class HomePage extends WebPage {
    @Css("form") public static LoginForm loginForm;
    @Css("img#user-icon") public static Icon userIcon;
}

public class LoginForm extends Form<User> {
    @Css("#name") TextField userName;
    @Css("#password")  TextField password;
    @Css("[type=submit]") Button enter;
}
```
### UI PageObjects
Now let's have a look at Page Objects in JDI. For example, we used the following Page Objects in the login test above:

- **Site** — your application entity. It contains all the Pages of your application and can be initiated with a single method call.

- **HomePage** — Pages contain UI elements: *common, complex* and *composite*. Pages also carry meta-information about their URLs and titles and allow executing common actions like `open`,`checkOpened`,<br/>`getUrl`, `getTitle`, `zoom`, `scroll` etc.

- **LoginForm** — Forms and Sections are logical parts of pages; they can include other sections or just UI elements. Forms also offer additional actions like `fill`, `submit`, `check` etc.

- **UI elements** (typified elements) — `Button`, `TextField`, `Checkbox`, `Icon` etc. are simple elements representing the elements of an actual UI.

Below you can find a common JDI project structure:

```java 
@Test
public void nonPageObjectTest() {
    WebPage.openUrl("https://jdi-testing.github.io/jdi-light/index.html");
    $("img#user-icon").click();
    $("form #name").input("Roman");
    $("form #password").input("Jdi1234");
    $("form [type=submit]").click();
    Assert.assertEquals(WebPage.getUrl(), "https://jdi-testing.github.io/jdi-light/index.html");
}
public class LoginForm extends Form<User> {
    TextField userName = $("#name");
    TextField password = $("#password");
    Button enter = $("[type=submit]");
}
```
### Short term non-Page Object style
If you need a quick test (i.e. you don't need Page Objects), you can simply use JQuery/Selenide style without any additional code.

You can also directly initialize UI elements defined in your Page Objects if you don't like annotations.
<br/><br/><br/><br/><br/><br/><br/>
### Smart Test locators

[See details and examples for Smart locators in the documentation](https://jdi-docs.github.io/jdi-light/?java#smart-locators)

```java 
@Test
public void assertTest{
  title.is().text(containsString("jdi"));
  name.assertThat().text(is("Roman"));
  color.has().attr("color", is("red"))
}
@Test
public void chainAssertTest{
  title.assertThat()
    .text(containsString("jdi"))
    .attr("color", is("red"))
    .tag(is("h1"))
}
@Test
public void listAssertTest{
	searchResults.is().notEmpty();
	searchResults.assertThat()		
		.size(equalTo(10))
		.any(e -> e.name.equals("Jdi intro 2"))
		.each(e -> e.name.toLowerCase().contains("jdi"))
		.onlyOne(e -> e.name.contains("Jdi intro 1"))
		.noOne(e -> e.name.contains("Selenide"));
}
@Test
public void tableChainTest() {
	users.assertThat()
		.displayed().size(6).size(greaterThan(3))
		.notEmpty().row(d -> d.user.contains("Ivan"))
		.allRows(d -> d.user.length() > 4)
		.atLeast(3).rows(d -> d.type.contains("User"))       
		.row(SPIDER_MAN)
		.exact(2).rows(d -> d.description.contains(":VIP"))
		.exact(1).rows(SPIDER_MAN);
}
```
### Asserts/Matchers integrated with elements

JDI has a really flexible set of matchers integrated into it.

- To access element matchers, you can use the following methods: <br/>
`is()`<br/>
`assertThat()`<br/>
`has()`<br/>
`waitFor()`<br/>
`shouldBe()`<br/>
All these methods are equivalent. Different names just help making code more descriptive and human-readable. <br/>
- JDI matchers are powered by [Hamcrest](http://hamcrest.org/JavaHamcrest/), the most popular matcher library in the Java world.
And you can chain these matchers to verify multiple conditions.<br/>
- With JDI you won't have to struggle with waits or execute sloppy tests.<br/>
JDI matchers handle most kinds of problems. They will pass when you expect them to and fail whenever there is a real error. <br/><br/>
Really useful, don't you agree?
<br/><br/><br/><br/><br/><br/><br/><br/><br/><br/><br/>

### Custom elements

```java 
public class Checklist extends HtmlElement {
    @Override
    public boolean isSelected() {
        return find("<<").hasClass("active");
    }
}
public class Checklist extends HtmlChecklist {
    @Override
    public boolean isSelected(HtmlElement value) {
        return hasClass("active") && attr("ui").equals("label");
    }
}
public class ContactForm extends Form<Contacts> {
	TextField name, lastName, position, passportNumber, passportSeria;
...
	@UI("['Submit']") public Button submit;

	@Override
	public void fillAction(Field field, Object element, Object parent, String setValue) {
		if (isInterface(field, TextField.class))
			((TextField)element).higlight();
		super.fillAction(field, element, parent, setValue);
	}
}
```
JDI HTML elements can handle typical standard cases, but each application has its unique culture of layout development.

So if your developers are not following common standards, you can easily create a pack of elements specific to your application and use them with JDI.
You can create your own elements or simply extend the existing ones, overriding a couple of methods.

Check these examples:

<a href='https://github.com/jdi-testing/jdi-light/blob/master/jdi-light-html-tests/src/main/java/io/github/com/custom/MenuItem.java' target="_blank">Menu Check item</a> <br/>
<a href='https://github.com/jdi-testing/jdi-light/blob/master/jdi-performance/src/main/java/org/mytests/uiobjects/example/site/sections/ContactForm.java' target="_blank">Contact Form</a>

## Start a new project with JDI
You can start a new test automation project with JDI in mere seconds! <br/>
Just download one of the templates at <a href='https://github.com/jdi-templates' target="_blank">Github JDI template repository</a>. <br/>

### Java + Allure + TestNg (recommended)
<a href='https://github.com/jdi-templates/jdi-light-testng-template' target="_blank">Github link</a> <br/>
### Java + Allure + JUnit
<a href='https://github.com/jdi-templates/jdi-light-junit-template' target="_blank">Github link</a> <br/>

### CSharp + NUnit
<a href='https://github.com/jdi-templates/jdi-light-csharp-template' target="_blank">Github link</a> <br/>


## How to improve your Selenium project with new capabilities in just a few minutes
## Logging and Reporting
