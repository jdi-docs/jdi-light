# Documentation
## Extended Selenium features
TBD

## Common elements

### Label 
 **Label** – Elements' caption for a big number of JDI common elements 
 
![Label](../images/colorpicker.png) 

Label's implementation is located in the following classes: 

   - __Java__: _com.epam.jdi.light.elements.base.BaseUIElement_
   - __C#__: _JDI.Light.Elements.Base.UIElement_

  ```java
   
  //In the next test Label is found from 'name' and 'disabledName' locators:
   
  @UI("#name") // @FindBy(css = "#name")
 public static TextField name;
	
  @UI("#disabled-name") // @FindBy(css = "#disabled-name")
 public static TextField disabledName;
	
 //By default Label is found by locator 
 By.cssSelector("[for="+getAttribute("id")+"]")
   
  @Test
  public void labelTest() {
      assertEquals(name.label().getText(), "Your name:");
      name.label().is().text(containsString("Your"));
      disabledName.label().is().text(equalToIgnoringCase("Surname:"));
  }
	
@Test
  public void getLabelTextTest() {
      assertEquals(colorPicker.labelText(), "Select a color");
  }
  
 ```

 ```csharp 
  	
 In the next test Label is found from NameTextField locator:
  
 [FindBy(Css = "div.main-content #name")]
 public TextField NameTextField { get; set; }
	
 By default Label is found by locator By.CssSelector($"[for={WebElement.GetAttribute("id")}]")

 [Test] 
 public void LabelTest() 
 { 
     Assert.AreEqual(TestSite.Html5Page.NameTextField.Label().GetText(), "Your name:");
     TestSite.Html5Page.NameTextField.Label().Is.Text(ContainsString("Your"));
     Assert.AreEqual(TestSite.Html5Page.SurnameTextField.Label().GetText(), "Surname:");
     TestSite.Html5Page.SurnameTextField.Label().Is.Text(ContainsString("Surname:")); 
 }	 
	
 [Test] 
 public void GetLabelTextTest() 
 { 
     AreEqual(TestSite.Html5Page.ColorPicker.LabelText(), "Select a color"); 
 } 
 
  ``` 
 
 Available methods in C# JDI Light: 

|Method | Description | Return Type 
--- | --- | --- 
**Label()** | Creates label for element using the element's Id | Label 
**LabelText()** | Gets the text of a label | string 
 
[C# test examples](https://github.com/jdi-testing/jdi-light-csharp/blob/master/JDI.Light/JDI.Light.Tests/Tests/Common/TextFieldsTests.cs) 

[Java test examples](https://github.com/jdi-testing/jdi-light/blob/master/jdi-light-html-tests/src/test/java/io/github/epam/html/tests/elements/simple/TextFieldTests.java) 


### Button
**Button** – Element that represents a clickable button

![Button](../images/button.png)

Button is located in the following classes:
 
  - __Java__: _com.epam.jdi.light.ui.html.common.Button_
  - __C#__: _JDI.Light.Elements.Common.Button_

```java 
@UI("[value*='Red Button']") // @FindBy(css = "[value*='Red Button']")
public static Button redButton;

@Test
public void clickTest() {
    redButton.click();
    assertEquals(getAlertText(), "Red button");
    acceptAlert();
}

@Test
public void getTextTest() {
    assertEquals(redButton.getText(), "Big Red Button-Input");
}
```
```csharp

[FindBy(Css = ".red")]
public Button RedButton;

[Test]
public void ClickTest() 
{
    RedButton.Click();
    Assert.AreEqual(GetAlert().GetAlertText(), "Red button");
    GetAlert().AcceptAlert();
}

[Test]
public void GetTextTest() 
{
    Assert.AreEqual(RedButton.GetText(), "Big Red Button-Input");
}

```

Here is an example with provided HTML code:

![Button example](../images/html/button_html.png)

Available methods in Java JDI Light:

|Method | Description | Return Type
--- | --- | ---
**click()** | Click the button  | void
**getText()** | Get button text | String
**is()** | Assert action | TextAssert 
**assertThat()** | Assert action | TextAssert

[Java test examples](https://github.com/jdi-testing/jdi-light/blob/master/jdi-light-html-tests/src/test/java/io/github/epam/html/tests/elements/simple/ButtonTests.java)

Available methods and properties in C# JDI Light:

|Method/Property | Description | Return Type
--- | --- | ---
**Click()** | Click the button  | void
**GetText()** | Get button text | string
**Is** | Assert action | TextAssert 
**AssertThat** | Assert action | TextAssert

[C# test examples](https://github.com/jdi-testing/jdi-light-csharp/blob/master/JDI.Light/JDI.Light.Tests/Tests/Common/ButtonTests.cs)

### Checkbox
**Checkbox** – Element allows you to select single value for submission.

![Checkbox](../images/checkbox.png)

Checkbox is located in the following classes:
 
  - __Java__: _com.epam.jdi.light.ui.html.common.Checkbox*_
  - __C#__: _JDI.Light.Elements.Common.CheckBox*_

```java 
@UI("#accept-conditions") // @FindBy(id = "accept-conditions")
public static Checkbox acceptConditions;

@Test
public void checkTest() {
    acceptConditions.check();
    assertEquals(acceptConditions.isSelected(), true);
}

@Test
public void uncheckTest() {
    acceptConditions.uncheck();
    assertEquals(acceptConditions.isSelected(), false);
}
```
```csharp

[FindBy(XPath = "//*[@id='elements-checklist']//*[text()='Water']")]
[IsChecked(typeof(CustomCheck), nameof(CustomCheck.CheckFunc))]
public CheckBox CbWater;

[FindBy(Css = "#accept-conditions")]
public CheckBox AcceptConditions { get; set; }

[Test]
public void CheckSingleTest()
{
     Assert.DoesNotThrow(() => TestSite.MetalsColorsPage.CbWater.Check(true));
     Jdi.Assert.Contains(TestSite.ActionsLog.Texts[0], "Water: condition changed to true");
}

[Test]
public void UncheckSingleTest()
{
     TestSite.MetalsColorsPage.CbWater.Click();
     TestSite.MetalsColorsPage.CbWater.Uncheck();
  	 Jdi.Assert.Contains(TestSite.ActionsLog.Texts[0], "Water: condition changed to false");
}

[Test]
public void IsCheckTest()
{
     Assert.IsFalse(TestSite.MetalsColorsPage.CbWater.IsChecked);
     TestSite.MetalsColorsPage.CbWater.Click();
     Assert.IsTrue(TestSite.MetalsColorsPage.CbWater.IsChecked);
}

[Test]
public void MultipleUncheckTest()
{
     TestSite.MetalsColorsPage.CbWater.Click();
     TestSite.MetalsColorsPage.CbWater.Uncheck();
     TestSite.MetalsColorsPage.CbWater.Uncheck();
     Jdi.Assert.Contains(TestSite.ActionsLog.Texts[0], "Water: condition changed to false");
}

[Test]
public void ClickTest()
{
     TestSite.MetalsColorsPage.CbWater.Click();
     Jdi.Assert.Contains(TestSite.ActionsLog.Texts[0], "Water: condition changed to true");
     TestSite.MetalsColorsPage.CbWater.Click();
     var texts = TestSite.ActionsLog.Texts;
     Jdi.Assert.Contains(texts[0], "Water: condition changed to false");
}

[Test]
[TestCaseSource(typeof(CheckBoxProvider), nameof(CheckBoxProvider.InputData))]
public void SetValueTest(bool value, bool expected)
{
     if (!expected) TestSite.MetalsColorsPage.CbWater.Click();
     TestSite.MetalsColorsPage.CbWater.Value = value;
     var resultMsg = "Water: condition changed to " + expected.ToString().ToLower();
     Jdi.Assert.Contains(TestSite.ActionsLog.Texts[0], resultMsg);
}

[Test]
public void IsValidationTest()
{
    TestSite.Html5Page.Open();
    TestSite.Html5Page.AcceptConditions.Is.Selected();
    TestSite.Html5Page.AcceptConditions.Click();
    TestSite.Html5Page.AcceptConditions.Is.Deselected();
    TestSite.Html5Page.AcceptConditions.Is.Enabled();
    TestSite.Html5Page.AcceptConditions.Is.Displayed();
}

[Test]
public void LabelTest()
{
    TestSite.Html5Page.Open();
    Assert.AreEqual("Accept terms and conditions", TestSite.Html5Page.AcceptConditions.Label().GetText());
    TestSite.Html5Page.AcceptConditions.Label().Is.Text(ContainsString("terms and conditions"));
    TestSite.Html5Page.AcceptConditions.Label().Is.Text(EqualTo("accept terms and conditions"));
}

[Test]
public void AssertValidationTest()
{
    TestSite.Html5Page.Open();
    TestSite.Html5Page.AcceptConditions.AssertThat.Selected();
}

[Test]
public void BaseValidationTest()
{
    TestSite.Html5Page.Open();
    BaseElementValidation(TestSite.Html5Page.AcceptConditions);
}

```

Here is an example with provided HTML code:

![Checkbox example](../images/html/checkbox_html.png)

Available methods in Java JDI Light:

|Methods | Description | Return Type
--- | --- | ---
**click()** | Click the checkbox  | void
**check(String)**| Set to checked on "true" (case insensitive) or unchecked otherwise | void
**check()**| Set to checked | void
**uncheck()**| Set to unchecked | void
**isSelected()** | Verify value | boolean 
**assertThat()** | Assert action checkbox | CheckboxAssert
**is()** | Assert action checkbox | CheckboxAssert

Available methods in C# JDI Light:

|Method | Description | Return Type
--- | --- | ---
**Check(bool checkEnabled = true)** | Checks a checkbox | void
**Uncheck(bool checkEnabled = true)** | Unhecks a checkbox | void
**IsChecked** | Determines whether a checkbox is checked | bool

Available assert methods in C# JDI Light:

|Method | Description | Return Type
--- | --- | ---
**Selected()** | Checks whether a checkbox is selected | CheckBoxAssert
**Deselected()** | Checks whether a checkbox is deselected | CheckBoxAssert
**Enabled()** | Checks whether a checkbox is enabled | CheckBoxAssert
**Displayed()** | Checks whether a checkbox is displayed | CheckBoxAssert
**Is** | Gets assert for checkbox | CheckBoxAssert
**AssertThat** | Gets assert for checkbox | CheckBoxAssert


[Java test examples](https://github.com/jdi-testing/jdi-light/blob/master/jdi-light-html-tests/src/test/java/io/github/epam/html/tests/elements/simple/CheckboxTests.java)

[C# test examples](https://github.com/jdi-testing/jdi-light-csharp/blob/master/JDI.Light/JDI.Light.Tests/Tests/Common/CheckBoxTests.cs)

### ColorPicker
**ColorPicker** – Elements of this type provide a user interface element that lets a user specify a color, either by using a visual color picker interface or by entering the color into a text field in "#rrggbb" hexadecimal format. Only simple colors (with no alpha channel) are allowed. The values are compatible with CSS.

![ColorPicker](../images/colorpicker.png)

Colorpicker is located in the following classes:

  - __Java__: _com.epam.jdi.light.ui.html.common.ColorPicker*_

```java 
@UI("#color-picker") // @FindBy(id = "color-picker")
public static ColorPicker colorPicker;

@Test
public void getColorTest() {
    assertEquals(colorPicker.color(), "#3fd7a6");
}

@Test
public void setColorTest() {
    colorPicker.setColor("#432376");
    assertEquals(colorPicker.color(), "#432376");
}

@Test
public void getLabelTextTest() {
    assertEquals(colorPicker.labelText(), "Select a color");
}
```
```csharp
[FindBy(Css = "#color-picker")]
public ColorPicker ColorPicker;

[Test]
public void GetColorTest() 
{
    Assert.AreEqual(ColorPicker.Color(), "#3fd7a6");
}

[Test]
public void SetColorTest() 
{
    ColorPicker.SetColor("#432376");
    Assert.AreEqual(ColorPicker.Color(), "#432376");
}
 
```

Here is an example with provided HTML code:

![ColorPicker](../images/html/colorpicker_html.png)

Here is the list of some available methods in Java:

|Methods | Description | Return Type
--- | --- | ---
**color()** | Returns color code in  hexadecimal format ("#rrggbb") | String
**setColor(String)** | Set color from string hex representation ("#rrggbb") | void
**is()** | Assert acton color | ColorAssert
**assertThat()** | Assert acton color | ColorAssert 

[Java test examples](https://github.com/jdi-testing/jdi-light/blob/master/jdi-light-html-tests/src/test/java/io/github/epam/html/tests/elements/simple/ColorPickerTests.java)

Here is the list of some available methods in C#:

|Methods | Description | Return Type
--- | --- | ---
**Color()** | Returns color code in  hexadecimal format ("#rrggbb") | string
**SetColor(String)** | Set color from string hex representation ("#rrggbb") | void
**Is()** | Assert acton color | ColorAssert
**AssertThat()** | Assert acton color | ColorAssert 

[Test examples in C#](https://github.com/jdi-testing/jdi-light-csharp/blob/master/JDI.Light/JDI.Light.Tests/Tests/Simple/ColorPickerTests.cs)

### DateTimeSelector

**DateTimeSelector** is used for Input Type Date and its derivatives and allows users to set the value of date and/or time.

The list of supported elements:

 - Input Type Date
 - Input Type Week
 - Input Type Month
 - Input Type Time
 - Input Type DateTime-Local

There are the following classes represent this type of elements:

 - __C#__: _JDI.Light.Elements.Common.DateTimeSelector_
 - __Java__: _com.epam.jdi.light.ui.html.common.DateTimeSelector_

Here is the list of some available methods in C#:

|Method | Description | Return Type
--- | --- | ---
**SetDateTime(string/DateTime value)** | Sets a date or time | void
**GetDateTime()** | Returns the set date or time | DateTime
**Value()** | Returns value attribute | string
**Min()** | Gets attribute with name min | string
**Max()** | Gets attribute with name max | string
**Is()** | Assert action of DateTimeSelector | DateTimeSelectorAssert
**AssertThat()** | Assert action of DateTimeSelector | DateTimeSelectorAssert

And here are some of the methods available in Java:

|Method | Description | Return Type
--- | --- | ---
**setDateTime(string value)** | Sets a date or time | void
**value()** | Returns the set date or time | String
**min()** | Gets attribute with name min | String
**max()** | Gets attribute with name max | String
**is()** | Assertion | DateTimeAssert
**assertThat()** | Assertion | DateTimeAssert

__In the following sections there are examples of different implementations of such fields.__

__Input Type Date__

```java 
@UI("#birth-date") //@FindBy(css = "#birth-date") 
public static DateTimeSelector birthDate;

@Test
public void setDateTimeTest() {
    birthDate.setDateTime("2018-11-13");
    assertEquals(birthDate.value(), "2018-11-13");
}

@Test
public void maxTest() {
    assertEquals(birthDate.max(), "2030-12-31");
}
```
```csharp 
[FindBy(Css = "#birth-date")]
public IDateTimeSelector BirthDate { get; set; }
        
[Test]
public void SetBirthDateTest()
{
    TestSite.Html5Page.BirthDate.Format = "yyyy-MM-dd";
    TestSite.Html5Page.BirthDate.SetDateTime(_dateTime);    
    TestSite.Html5Page.BirthDate.AssertThat().SelectedTime(Is.EqualToIgnoringCase("2019-04-01"));	
}
```
**Input Type Date** – a graphical control element, that allows users to set the value of date.

![InputTypeDate](../images/html/inputTypeDate_html.png)

[Test examples in C#](https://github.com/jdi-testing/jdi-light-csharp/blob/master/JDI.Light/JDI.Light.Tests/Tests/Common/DateTimeTests.cs)

[Test examples in Java](https://github.com/jdi-testing/jdi-light/blob/master/jdi-light-html-tests/src/test/java/io/github/epam/html/tests/elements/simple/DateTests.java)

__Input Type Week__

```java 
@UI("#autumn-week") //@FindBy(css = "#autumn-week") 
public static DateTimeSelector autumnWeek;

@Test
public void minTest() {
    assertEquals(autumnWeek.min(), "2018-W35");
}

@Test
public void setDateTimeTest() {
    autumnWeek.setDateTime("2018-W12");
    autumnWeek.show();
    assertEquals(autumnWeek.value(), "2018-W12");
}
```
```csharp 
[FindBy(Css = "#autumn-week")]
public IDateTimeSelector AutumnDateTime { get; set; }
        
[Test]
public void AutumnDateTimeTest()
{
    var calendar = new GregorianCalendar();
    var weekNum = calendar.GetWeekOfYear(_dateTime, CalendarWeekRule.FirstFullWeek, DayOfWeek.Monday);
    TestSite.Html5Page.AutumnDateTime.Format = "yyyy-" + $"W{weekNum}";

    TestSite.Html5Page.AutumnDateTime.SetDateTime(_dateTime);
    var setValue = TestSite.Html5Page.AutumnDateTime.GetValue();
    Assert.AreEqual(setValue, "2019-W13");
}
```
**Input Type Week** – a graphical control element, that allows users to set the value of week and year.

![InputTypeWeek](../images/html/inputTypeWeek_html.png)

[Test examples in C#](https://github.com/jdi-testing/jdi-light-csharp/blob/master/JDI.Light/JDI.Light.Tests/Tests/Common/DateTimeTests.cs)

[Test examples in Java](https://github.com/jdi-testing/jdi-light/blob/master/jdi-light-html-tests/src/test/java/io/github/epam/html/tests/elements/simple/WeekTests.java)

__Input Type Month__

```java 
@UI("#month-date") //@FindBy(css = "#month-date") 
public static DateTimeSelector monthDate;

@Test
public void maxTest() {
    assertEquals(monthDate.max(), "2020-12");
}

@Test
public void setDateTimeTest() {
    monthDate.setDateTime("2018-10");
    monthDate.show();
    assertEquals(monthDate.value(), "2018-10");
}
```
```csharp 
[FindBy(Css = "#month-date")]
public IDateTimeSelector MonthOfHolidays { get; set; }
        
[Test]
public void SetMonthTest()
{
    TestSite.Html5Page.MonthOfHolidays.Format = "yyyy-MM";
    TestSite.Html5Page.MonthOfHolidays.SetDateTime(_dateTime);
    var setValue = TestSite.Html5Page.MonthOfHolidays.GetValue();
    Assert.AreEqual(setValue, "2019-04");
}
```
**Input Type Month** – a graphical control element, that allows users to set the value of month and year.

![InputTypeMonth](../images/html/inputTypeMonth_html.png)

[Test examples in C#](https://github.com/jdi-testing/jdi-light-csharp/blob/master/JDI.Light/JDI.Light.Tests/Tests/Common/DateTimeTests.cs)

[Test examples in Java](https://github.com/jdi-testing/jdi-light/blob/master/jdi-light-html-tests/src/test/java/io/github/epam/html/tests/elements/simple/MonthTests.java)

__Input Type Time__

```java 
@UI("#booking-date") //@FindBy(css = "#booking-time") 
public static DateTimeSelector bookingTime;

@Test
public void minTest() {
    assertEquals(bookingTime.min(), "9:00");
}

@Test
public void setDateTimeTest() {
    bookingTime.setDateTime("05:00");
    bookingTime.show();
    assertEquals(bookingTime.value(), "05:00");
}
```
```csharp 
[FindBy(Css = "#booking-time")]
public IDateTimeSelector BookingTime { get; set; }
        
[Test]
public void SetTimeTest()
{
    TestSite.Html5Page.BookingTime.Format = "H:mm";
    TestSite.Html5Page.BookingTime.SetDateTime(_dateTime);
    var setValue = TestSite.Html5Page.BookingTime.GetValue();
    Assert.AreEqual(setValue, "15:00");
}
```
**Input Type Time** – a graphical control element, that allows the user to set the value of time.

![InputTypeTime](../images/html/inputTypeTime_html.png)

[Test examples in C#](https://github.com/jdi-testing/jdi-light-csharp/blob/master/JDI.Light/JDI.Light.Tests/Tests/Common/DateTimeTests.cs)

[Test examples in Java](https://github.com/jdi-testing/jdi-light/blob/master/jdi-light-html-tests/src/test/java/io/github/epam/html/tests/elements/simple/TimeTests.java)

__Input Type DateTime-Local__

```java 
@UI("#party-time") //@FindBy(id = "party-time")
public static DateTimeSelector partyTime;

@Test
public void setDateTimeTest() {
    partyTime.setDateTime("2017-05-10T00:00");
    assertEquals(partyTime.value(), "2017-05-10T00:00");
}
```
```csharp 
[FindBy(Css = "#party-time")]
public IDateTimeSelector PartyTime { get; set; }

[Test]
public void SetPartyTimeTest()
{
    TestSite.Html5Page.PartyTime.Format = "yyyy-MM-ddTHH:mm";
    TestSite.Html5Page.PartyTime.SetDateTime(_dateTime);
    var setValue = TestSite.Html5Page.PartyTime.GetDateTime();
    Assert.AreEqual(setValue, _dateTime);
}
```
**Input Type DateTime-Local** – a graphical control element, that allows the user to set the value of time and date.

![InputTypeDateTime](../images/html/inputDateTimeLocal_html.png)

[Java test example](https://github.com/jdi-testing/jdi-light/blob/master/jdi-light-html-tests/src/test/java/io/github/epam/html/tests/elements/simple/DateTimeTests.java)

[C# test examples](https://github.com/jdi-testing/jdi-light-csharp/blob/master/JDI.Light/JDI.Light.Tests/Tests/Common/DateTimeTests.cs)

### FileInput

**FileInput** - a grafical control element, that allows the user to upload documents on the web site

![FileInput](../images/fileinput.png)

FileInput element is located in JDI Light in:

  - __Java__: _com.epam.jdi.light.ui.html.common.FileInput_
  - __C#__: _JDI.Light.Elements.Composite.FileInput_

```java 
@UI("#avatar") // @FindBy(id = "avatar")
public static FileInput avatar; 

@Test
public void uploadTest() {
    avatar.uploadFile(mergePath(PROJECT_PATH,"/src/test/resources/general.xml"));
    avatar.is().text(containsString("general.xml"));
    assertTrue(avatar.getText().contains("general.xml"));
    assertTrue(avatar.getValue().contains("general.xml"));
}
```
```csharp
[Test]
public void FileInputTest()
{
    FileInput.SelectFile(CreateFile(filename));
}

[Test]
public void DisabledUploadTest()
{
    Sleep(2000);
    try
    {
         TestSite.Html5Page.DisabledFileInput.SelectFile(CreateFile(_fileName));
    }
    catch (Exception e)
    {
         Logger.Exception(e);
    }
    Sleep(2000);
    TestSite.Html5Page.DisabledFileInput.Is.Text(EqualTo(""));
}

[Test]
public void LabelTest()
{
    AreEqual(TestSite.Html5Page.FileInput.LabelText(), "Profile picture:");
    TestSite.Html5Page.FileInput.Label().Is.Text(ContainsString("picture"));
}

[Test]
public void BaseValidationTest()
{
    BaseElementValidation(TestSite.Html5Page.FileInput);
}

```

Here is an example with provided HTML code:

![FileInput example](../images/html/fileinput_html.png)

Available method in Java JDI Light:

|Method | Description | Return Type
--- | --- | ---
**uploadFile(String)** |Select file to upload  | void

Available method in C# JDI Light:

|Method | Description | Return Type
--- | --- | ---
**SelectFile(string filepath)** |Select file to upload  | void

Available assert methods in C# JDI Light:

|Method | Description | Return Type
--- | --- | ---
**IsDownloaded()** |Checks whether a file is downloaded  | FileAssert
**Text(Matcher<string> value)** | Checks whether an occurence of a text is contained in a text file | FileAssert
**HasSize(Matcher<long> size)** | Checks that a file has a particular size according to the matcher | FileAssert
**CleanupDownloads()** | Cleans the directory | void

[Java test examples](https://github.com/jdi-testing/jdi-light/blob/master/jdi-light-html-tests/src/test/java/io/github/epam/html/tests/elements/simple/FileUploadTests.java)

[C# test examples](https://github.com/jdi-testing/jdi-light-csharp/blob/master/JDI.Light/JDI.Light.Tests/Tests/Common/FileInputTests.cs)

### Icon
```java 
@UI("#jdi-logo") 
// same as FindBy(css = "#jdi-logo")
public static Icon jdiLogo;

    @Test
    public void isValidationTest() {
        WebPage.refresh();
        jdiLogo.is().src(containsString("jdi-logo.jpg"));
        jdiLogo.is().alt(is("Jdi Logo 2"));
        jdiLogo.assertThat().height(is(100));
        jdiLogo.assertThat().width(is(101));
    }
```
```csharp 
[FindBy(Css = "#jdi-logo")]
public IIcon LogoImage;

   [Test]
   public void GetSourceTest()
   {
     Jdi.Assert.AreEquals(LogoImage.GetSource(), Src);
   }

   [Test]
   public void GetTipTest()
   {
     Jdi.Assert.AreEquals(LogoImage.GetAlt(), Alt);
   }
```
**Icon** – is a simple element type that represents icons and graphic images.

![Icon](../images/html/image_html.png)

Icons are represented by the following classes:
 
  - __Java__: _com.epam.jdi.light.ui.html.common.Icon , com.epam.jdi.light.ui.html.common.Image_
  - __C#__: JDI.Light.Interfaces.Common.IIcon, _JDI.Light.Elements.Common.Image


 
Icon in JDI is a descendant of Image. It inherits all Image's methods and serves as its wrapper. Here are Java methods for Icon inherited from Image interface:

|Method | Description | Return Type
--- | --- | ---
**click()** | click on the image| void
**src()** | get value of src attribute | String
**height()** |get value of height attribute| String
**width()** | get value of width attribute| String
**alt()** |get value of alt attribute | String
**is()** | method for building assertions | ImageAssert
**assertThat()** |method for building assertions  | ImageAssert

Here is a list of available methods in C#:

|Method | Description | Return Type
--- | --- | ---
**Click()** | click on the image| void
**Src** | get value of src attribute | string
**Height** |get value of height attribute| string
**Width** | get value of width attribute| string
**Alt** |get value of alt attribute | string
**Is()** | method for building assertions | ImageAssert
**AssertThat()** |method for building assertions  | ImageAssert

[Test examples in Java]
(https://github.com/jdi-testing/jdi-light/blob/master/jdi-light-html-tests/src/test/java/io/github/epam/html/tests/elements/simple/ImageTests.java)

[Test examples in C#]
(https://github.com/jdi-testing/jdi-light-csharp/blob/master/JDI.Light/JDI.Light.Tests/Tests/Simple/ImagesTests.cs)

### Image
```java 
@UI("#jdi-logo") 
// same as FindBy(css = "#jdi-logo")
public static Image jdiLogo;

    @Test
    public void isValidationTest() {
        WebPage.refresh();
        jdiLogo.is().src(containsString("jdi-logo.jpg"));
        jdiLogo.is().alt(is("Jdi Logo 2"));
        jdiLogo.assertThat().height(is(100));
        jdiLogo.assertThat().width(is(101));
    }
```
```csharp 
[FindBy(Css = "#jdi-logo")]
public IImage LogoImage;

   [Test]
   public void GetSourceTest()
   {
     Jdi.Assert.AreEquals(LogoImage.GetSource(), Src);
   }

   [Test]
   public void GetTipTest()
   {
     Jdi.Assert.AreEquals(LogoImage.GetAlt(), Alt);
   }
```
**Image** – is a simple element type that represents graphic images.

![Image](../images/html/image_html.png)

Images are represented by the following classes in Java and C#:
 
  - __C#__: _JDI.Light.Elements.Common.Image_
  - __Java__: _com.epam.jdi.light.ui.html.common.Image_
  
Here is a list of available methods in C#:

|Method | Description | Return Type
--- | --- | ---
**Click()** | click on the image| void
**Src** | get value of src attribute | string
**Height** |get value of height attribute| string
**Width** | get value of width attribute| string
**Alt** |get value of alt attribute | string
**Is()** | method for building assertions | ImageAssert
**AssertThat()** |method for building assertions  | ImageAssert

[Test examples in C#](https://github.com/jdi-testing/jdi-light-csharp/blob/master/JDI.Light/JDI.Light.Tests/Tests/Simple/ImagesTests.cs)

And here are methods available in Java:

|Method | Description | Return Type
--- | --- | ---
**click()** | click on the image| void
**src()** | get value of src attribute | String
**height()** |get value of height attribute| String
**width()** | get value of width attribute| String
**alt()** |get value of alt attribute | String
**is()** | method for building assertions | ImageAssert
**assertThat()** |method for building assertions  | ImageAssert

[Test examples in Java](https://github.com/jdi-testing/jdi-light/blob/master/jdi-light-html-tests/src/test/java/io/github/epam/html/tests/elements/simple/ImageTests.java)

### Icon
```csharp 
[FindBy(Css = "#jdi-ico")]
public IIcon LogoIco;

   [Test]
   public void GetSrcTest()
   {
       Jdi.Assert.AreEquals(LogoIco.Src, Text);
   }

   [Test]
   public void GetAltTest()
   {
       Jdi.Assert.AreEquals(LogoIco.Alt, "");
   }
```
**Icon** – is a simple element type that represents small graphic images (icons).

Icons are represented by the following class in C#:
 
  - __C#__: _JDI.Light.Elements.Common.Icon_
   
Here is a list of available methods in C#:

|Method | Description | Return Type
--- | --- | ---
**Src** | get value of src attribute | string
**Height** |get value of height attribute| string
**Width** | get value of width attribute| string
**Alt** |get value of alt attribute | string
**Is()** | method for building assertions | ImageAssert
**AssertThat()** |method for building assertions  | ImageAssert

[Test examples in C#](https://github.com/jdi-testing/jdi-light-csharp/blob/master/JDI.Light/JDI.Light.Tests/Tests/Simple/IconTests.cs)

### Link
**Link** – a graphical control element, that allows the user to link from one page to other web pages, files, locations within the same page, email addresses, or any other URL.

Link are represented by the following class:
 
  - __Java__: _com.epam.jdi.light.ui.html.common.Link_
  - __C#__: _JDI.Light.Elements.Common.Link_
  
  
```java 
@UI("[ui=github-link]") 
// equal to @FindBy(css = "[ui=github-link]") 
public static Link githubLink;

@Test
public void getTextTest() {
        assertEquals(githubLink.getText(), text);
    }
```
```csharp 
[FindBy(Css = "[ui = github-link]")]
public ILink GithubLink;

[Test]
public void GetTextTest()
{
    Assert.AreEqual(GithubLink.GetText(), Text);
}

[Test]
public void GetUrlTest()
{
     Assert.AreEqual(GithubLink.Url(), "https://epam.github.io/JDI/html5.html");
}
```


![Link](../images/html/link_html.png)

Here is the list of available methods in Java:

|Method | Description | Return Type
--- | --- | ---
**click()** |Follow the link | void
**getText()** |Returns the link text  | String
**ref()** |Returns the reference  | String
**url()** |Returns the URL  | URL
**alt()** |Returns the alternate text | String
**is()** | Returns object for work with assertions | LinkAssert
**assertThat()** | Returns object for work with assertions | LinkAssert

[Java test examples](https://github.com/jdi-testing/jdi-light/blob/master/jdi-light-html-tests/src/test/java/io/github/epam/html/tests/elements/simple/LinkTests.java)

Here is the list of available methods in C#:

|Method | Description | Return Type
--- | --- | ---
**Click()** |Follow the link | void
**GetText()** |Returns the link text  | string
**Ref()** |Returns the reference  | string
**Url()** |Returns the URL  | string
**Alt()** |Returns the alternate text | string
**Is()** | Returns object for work with assertions | LinkAssert
**AssertThat()** | Returns object for work with assertions | LinkAssert

[C# test examples](https://github.com/jdi-testing/jdi-light-csharp/blob/master/JDI.Light/JDI.Light.Tests/Tests/Common/LinkTests.cs)

### Menu

**Menu** - a list of links, which leads to different pages or sections of website

Menu element is located in JDI Light in:

  - __Java__: _com.epam.jdi.light.ui.html.complex.Menu_
  - __C#__: _JDI.Light.Elements.Composite.Menu_

```java 
@UI(".sidebar-menu span<[*'%s']<<") 
public static Menu leftMenu;
@Url("/metals-colors.html") @Title("Metal and Colors")
public static MetalAndColorsPage metalAndColorsPage;

@Test
public void selectEnumTest() {
    leftMenu.select(MetalsColors);
    metalAndColorsPage.checkOpened();
}
```
```csharp
[FindBy(Css = "ul.sidebar-menu")]
public Menu SidebarMenu;

[Test]
public void SelectEnumTest()
{
     TestSite.SidebarMenu.Select(Navigation.MetalsColors);
     TestSite.MetalsColorsPage.CheckOpened();
}

[Test]
public void IsValidationTest()
{
     TestSite.SidebarMenu.Select("Elements packs", "HTML 5");
     TestSite.SidebarMenu.Is.Selected("HTML 5")
}

[Test]
public void AssertValidationTest()
{
     TestSite.SidebarMenu.Select("Elements packs", "HTML 5");
     TestSite.SidebarMenu.AssertThat.Selected("HTML 5");
}

```

Here is an example with provided HTML code:

![Menu example](../images/html/menu.png)

Available method in Java JDI Light:

|Method | Description | Return Type
--- | --- | ---
**void select(String...)** | Select menu element and subelement | void
**void select(String)** | Select menu element | void
**void select(TEnum...)** | Select menu element and subelement | void
**void select(TEnum)** | Select menu element | void
**void select(int...)** | Select menu element by index | void
**void select(int)** | Select menu element and subelements by index | void    
**String selected()** | Returns selected menu item | String
**List<String> values()** | Returns selected menu item and subitems | List<String>
**void hoverAndClick(String...)** | Hovers and clicks menu item and subitems | void
**void hoverAndClick(String)** | Hovers and clicks menu item | void

Available method in C# JDI Light:

|Method | Description | Return Type
--- | --- | ---
**void Select(string[])** | Select menu element and subelements by string values | void
**void Select(string)** | Select menu element | void
**void Select(int[])** | Select menu element and subelements by index | void
**void Select(int)** | Select menu element and subelements by index | void 
**void Select(Enum[])** | Select menu element and subelements by getting values of enum | void
**void Select(Enum)** | Select menu element | void
**string Selected()** | Returns selected menu item | string
**List<string> Values()** | Gets values of all options | List<string>
**void HoverAndClick(string[])** | Hovers and clicks menu item and subitems | void
**void HoverAndClick(string)** | Hovers and clicks menu item | void

Available Assert methods in C# JDI Light:

|Method | Description | Return Type
--- | --- | ---
**Is** | Get select assert | MenuSelectAssert
**AssertThat** | Get select assert | MenuSelectAssert

[Java test examples](https://github.com/jdi-testing/jdi-light/blob/master/jdi-light-html-tests/src/test/java/io/github/epam/html/tests/complex/MenuTests.java)

[C# test examples](https://github.com/jdi-testing/jdi-light-csharp/blob/master/JDI.Light/JDI.Light.Tests/Tests/Composite/MenuTests.cs)

### NumberSelector
**NumberSelector** – a graphical control element, that allows the user to let the user enter a number.

NumberSelector are represented by the following class:
 
  - __Java__: _com.epam.jdi.light.ui.html.common.NumberSelector_
  - __C#__: _JDI.Light.Elements.Common.NumberSelector_
  
  
```java 
@UI("#height") 
// equal to @FindBy(css = "#height") 
public static NumberSelector height;

@Test
public void getNumberTest() {
        assertEquals(height.value(), number);
    }
```
```csharp 
[FindBy(Css = "#height")]
public INumberSelector numberSelector;

[Test]
public void GetNumberTest()
{
    Jdi.Assert.AreEquals(number, numberSelector.Value());
}
```


![NumberSelector](../images/html/numberSelector_html.png)

Here is the list of available methods in Java:

|Method | Description | Return Type
--- | --- | ---
**placeholder()** |Returns the placeholder text  | String
**min()** |Returns the min value   | String
**max()** |Returns the max value  | String
**value()** |Returns the value  | String
**step()** |Returns the step value | String
**setNumber(String)** |Sets the value | void
**is()** | Returns object for work with assertions | NumberAssert
**assertThat()** | Returns object for work with assertions | NumberAssert

Here is the list of available methods in C#:

|Method | Description | Return Type
--- | --- | ---
**Placeholder** |Returns the placeholder text  | String
**Min** |Returns the min value   | double
**Max** |Returns the max value  | double
**Value** |Returns the value  | double
**Step** |Returns the step value | double
**SetNumber(double)** |Sets the value | void
**Is()** | Returns object for work with assertions | NumberAssert
**AssertThat()** | Returns object for work with assertions | NumberAssert

[Java test examples](https://github.com/jdi-testing/jdi-light/blob/master/jdi-light-html-tests/src/test/java/io/github/epam/html/tests/elements/simple/NumberSelectorTests.java)

[Test examples in C#]
(https://github.com/jdi-testing/jdi-light-csharp/blob/master/JDI.Light/JDI.Light.Tests/Tests/Common/NumberSelectorTests.cs)

### ProgressBar
**Progress Bar** - Element for displaying an indicator showing the completion progress of a task

![ProgressBar](../images/progressbar.png)

ProgressBar is located in the following classes:
 
  - __Java__: _com.epam.jdi.light.ui.html.common.ProgressBar_
  - __C#__: _JDI.Light.Elements.Common.ProgressBar_

```java 
@UI("#progress") // @FindBy(id = "progress")
public static ProgressBar progress;

@Test
public void getValueTest() {
    assertEquals(progress.value(), "70");
}

@Test
public void maxTest() {
    assertEquals(progress.max(), "100");
}

@Test
public void assertValidationTest() {
    progress.assertThat().volume(greaterThan(0));
    progress.assertThat().volume(lessThan(200));
    progress.assertThat().volume(is(70));
}
```
```csharp

[FindBy(Css = "#progress")]
public ProgressBar Progress;

[Test]
public void GetValueTest() 
{
     Assert.AreEqual(Progress.Value(), "70");
}

[Test]
public void MaxTest() 
{
     Assert.AreEqual(Progress.Max(), "100");
}

```

Here is an example with provided HTML code:

![ProgressBar example](../images/html/progressbar_html.png)

Available method in Java JDI Light:

|Method | Description | Return Type
--- | --- | ---
**value()** |Get current progress value  | String
**max()** |Get progressbar maximum possible value  | String
**is()** |Various assert actions for Progress bar  | ProgressAssert
**assertThat()** |Various assert actions for Progress bar | ProgressAssert 


Available method in C# JDI Light:

|Method | Description | Return Type
--- | --- | ---
**Value()** |Get current progress value  | string
**Max()** |Get progressbar maximum possible value  | string
**Is()** |Various assert actions for Progress bar  | ProgressAssert
**AssertThat()** |Various assert actions for Progress bar | ProgressAssert 

[Java test examples](https://github.com/jdi-testing/jdi-light/blob/master/jdi-light-html-tests/src/test/java/io/github/epam/html/tests/elements/simple/ProgressTests.java)

[C# test examples](https://github.com/jdi-testing/jdi-light-csharp/blob/master/JDI.Light/JDI.Light.Tests/Tests/Common/ProgressTests.cs)

### Range

```java 
  @UI("#volume")  //@FindBy(id = "volume") 
  public static Range volume;
  @Test
  public void getLabelTextTest() {
      assertEquals(volume.labelText(), "Volume");
  }
  @Test
  public void getValueTest() {
      assertEquals(disabledRange.volume(), 50);
  }
  @Test
  public void minTest() {
      assertEquals(volume.min(), "10");
  }
  @Test
  public void maxTest() {
      assertEquals(volume.max(), "100");
  }
  @Test
  public void stepTest() {
      assertEquals(volume.step(), "5");
  }
  @Test
  public void setVolumeTest() {
      volume.setVolume(10);
      assertEquals(volume.volume(), 10);
  }
  @Test
  public void isValidationTest() {
      volume.is().enabled();
      volume.assertThat().minVolume(is(10));
      volume.assertThat().maxVolume(is(100));
      volume.assertThat().step(is(5));
      volume.is().volume(greaterThanOrEqualTo(10));
      volume.is().volume(lessThanOrEqualTo(100));
      volume.is().volume(is(90));
  }
  @Test
  public void labelTest() {
      assertEquals(volume.label().getText(), "Volume");
      volume.label().is().text(containsString("lume"));
      volume.label().assertThat().text(equalToIgnoringCase("volume"));
  }
  @Test
  public void assertValidationTest() {
      volume.assertThat().volume(greaterThan(0));
      volume.assertThat().volume(lessThan(200));
      disabledRange.assertThat().volume(is(50));
  }
  @Test
  public void baseValidationTest() {
      baseValidation(volume);
  }
```

```csharp
  [FindBy(Css = "#volume")]
  public IRange Volume { get; set; } 
  [Test]
  public void GetValueTest()
  {
      Assert.AreEqual(TestSite.Html5Page.DisabledRange.Value(), 50);
  }
  [Test]
  public void MinTest()
  {
      Assert.AreEqual(TestSite.Html5Page.Volume.Min(), 10);
  }
  [Test]
  public void MaxTest()
  {
      Assert.AreEqual(TestSite.Html5Page.Volume.Max(), 100);
  }
  [Test]
  public void StepTest()
  {
      Assert.AreEqual(TestSite.Html5Page.Volume.Step(), 5);
  }
  [Test]
  public void SetRangeTest()
  {
      TestSite.Html5Page.Volume.SetValue(10);
      Assert.AreEqual(TestSite.Html5Page.Volume.Value(), 10);
  }
  [Test]
  public void RangeTest()
  {
      TestSite.Html5Page.Volume.SetValue("30");
      Assert.AreEqual(TestSite.Html5Page.Volume.GetValue(), "30");
  }
```

**Range** - a graphical control element that allows the user to set the value from the range.</br>

![Range](../images/html/range_html.png)</br>

Range is represented by the following class:</br>

  - __Java__: _com.epam.jdi.light.ui.html.common.Range_
  - __C#__: _JDI.Light.Elements.Common.Range_
  
Here is a list of available methods in C#:

|Method | Description | Return Type
--- | --- | ---
**SetValue(string value)** | Sets the value | void
**SetValue(double value)** | Sets the value | void
**GetValue()** | Returns the value | String
**Value()** | Returns the value | Double
**Min()** | Returns the min value | Double
**Max()** | Returns the max value| Double
**Step()** | Returns the step value | Double
**Is()** | Returns object for work with assertions | RangeAssert
**AssertThat()** | Returns object for work with assertions | RangeAssert

[Test examples in C#](https://github.com/jdi-testing/jdi-light-csharp/blob/master/JDI.Light/JDI.Light.Tests/Tests/Simple/RangeTests.cs)</br></br>

And here are methods available in Java:

|Method | Description | Return Type
--- | --- | ---
**setVolume(int volume)** | Sets the value | void
**volume()** | Returns the value | int
**max()** | Returns the max value | String
**min()** | Returns the min value | String
**step()** | Returns the step value | String
**is()** | Returns object for work with assertions | RangeAssert
**assertThat()** | Returns object for work with assertions | RangeAssert

[Java test examples](https://github.com/jdi-testing/jdi-light/blob/master/jdi-light-html-tests/src/test/java/io/github/epam/html/tests/elements/simple/RangeTests.java)</br>

### Text
**Text** is a combination of letters and textual symbols. When performing testing, the text is used in most operations: when typing text into the login field, when finding a button with some certain text in it, or when checking if actual text matches expected one.

```java 
  @UI("[ui=jdi-text]") //@FindBy(css = "[ui=jdi-text]") 
  public static Text jdiText;

  @Test
  public void getTextTest() {
      assertEquals(jdiText.getText(), text);
  }

  @Test
  public void getValueTest() {
      assertEquals(jdiText.getValue(), text);
  }

  @Test
  public void isValidationTest() {
      jdiText.is().enabled();
      jdiText.is().text(is(text));
      jdiText.is().text(containsString("Powerful Framework for UI"));
  }

  @Test
  public void assertValidationTest() {
      jdiText.assertThat().text(is(text));
  }

  @Test
  public void baseValidationTest() {
      baseValidation(jdiText);
  }
  
```

```csharp
  [FindBy(Css = ".main-txt")]
  public TextElement Text;
        
  [Test]
  public void GetTextTest()
  {
      Jdi.Assert.AreEquals(TestSite.HomePage.Text.Value, _expectedText);
  }

  [Test]
  public void GetValueTest()
  {
      Jdi.Assert.AreEquals(TestSite.HomePage.Text.Value, _expectedText);
  }

  [Test]
  public void SetAttributeTest()
  {
      var attributeName = "testAttr";
      var value = "testValue";
      TestSite.HomePage.Text.SetAttribute(attributeName, value);
      Jdi.Assert.AreEquals(TestSite.HomePage.Text.GetAttribute(attributeName), value);
  }

  [Test]
  public void WaitSuspendButtonTextTest()
  {
       TestSite.Html5Page.Open();
       TestSite.Html5Page.GhostButton.Is.Displayed();
       TestSite.Html5Page.GhostButton.Is.Text(EqualTo("GHOST BUTTON"));
       Thread.Sleep(3000);
  	   TestSite.Html5Page.SuspendButton.Is.Displayed();
       TestSite.Html5Page.SuspendButton.Is.Text(EqualTo("SUSPEND BUTTON"));
  }
  
   [Test]
   public void IsValidationTest()
   {
        TestSite.HomePage.Text.Is.Enabled();
        TestSite.HomePage.Text.Is.Text(EqualTo(_expectedText));
        TestSite.HomePage.Text.Is.Text(ContainsString(_contains));
   }

   [Test]
   public void AssertValidationTest()
   {
        TestSite.HomePage.Text.AssertThat.Text(EqualTo(_expectedText));
   }

   [Test]
   public void BaseValidationTest()
   {
       TestSite.Html5Page.Open();
       BaseElementValidation(TestSite.Html5Page.JdiText);
   }
  
```

![Text](../images/html/text_html.png)

Text is represented by the following class:

Java: com.epam.jdi.light.ui.html.common.Text  
C#: JDI.Light.Elements.Common.TextElement

Here is a list of available methods in C#:

|Method | Description | Return Type
--- | --- | ---
**GetText()** | returns text| String
**GetValue()** | returns text| String
**Is** | Gets text assert | TextAssert
**AssertThat** | Gets text assert | TextAssert
**WaitFor** | Gets text assert | TextAssert

[Test examples in C#](https://github.com/jdi-testing/jdi-light-csharp/blob/master/JDI.Light/JDI.Light.Tests/Tests/Simple/TextTests.cs)

And here are methods available in Java:
    
|Method | Description | Return Type
--- | --- | ---
**getText()** |Get current value  | String
**is()** |Various assert actions for Text| TextAssert
**assertThat()** |Various assert actions for Text| TextAssert 

[Java test examples](https://github.com/jdi-testing/jdi-light/blob/master/jdi-light-html-tests/src/test/java/io/github/epam/html/tests/elements/simple/TextTests.java)  

### TextField
```java 
@UI("#name") 
// same as @FindBy(css = "#name")
public static TextField name;

    @Test
    public void sendKeysTest() {
        name.sendKeys("Test");
        assertEquals(name.getValue(), text+"Test");
    }

    @Test
    public void inputTest() {
        name.input("New text");
        assertEquals(name.getText(), "New text");
    }

    @Test
    public void clearTest() {
        name.clear();
        assertEquals(name.getText(), "");
    }

    @Test
    public void placeholderTest() {
        assertEquals(name.placeholder(), "Input name");
    }
```
```csharp 
[FindBy(Id = "name")]
public ITextField NameField;
        
        [Test]
        public void InputTest()
        {
            TestSite.ContactFormPage.NameField.Input(ToAddText);
            Jdi.Assert.AreEquals(TestSite.ContactFormPage.NameField.Value, ToAddText);
        }
        
        [Test]
        public void SendKeyTest()
        {
            TestSite.ContactFormPage.NameField.SendKeys(ToAddText);
            Jdi.Assert.AreEquals(TestSite.ContactFormPage.NameField.Value, _defaultText + ToAddText);
        }

        [Test]
        public void ClearTest()
        {
            TestSite.ContactFormPage.NameField.Clear();
            Jdi.Assert.AreEquals(TestSite.ContactFormPage.NameField.Value, "");
        }
```
**TextField** – is a simple element type that allows users to fill in text fields.

![InputTypeTextField](../images/html/textField_html.png)

Text fields are represented by the following classes in Java and C#:
 
  - __C#__: _JDI.Light.Elements.Common.TextField_
  - __Java__: _com.epam.jdi.light.ui.html.common.TextField_
  
Here is a list of available methods and properties in C#:

|Method / Property | Description | Return Type
--- | --- | ---
**SendKeys(string value)** | adds text to the field | void
**SetText(String value)** | sets new text | void
**Clear()** | clears the text field | void
**Input(string text)** | sets new text  | void
**Focus()** | places cursor within the text field | void
**Placeholder** | returns value of the placeholder attribute | String
**GetText()** | returns text from the text field  | String
**GetValue()** | returns text from the text field| String
**Is** | property that returns object for work with assertions| TextAssert
**AssertThat** | property that returns object for work with assertions| TextAssert


[Test examples in C#](https://github.com/jdi-testing/jdi-light-csharp/blob/master/JDI.Light/JDI.Light.Tests/Tests/Common/TextFieldsTests.cs)

And here are methods available in Java:

|Method | Description | Return Type
--- | --- | ---
**sendKeys(CharSequence... value)** | adds text to the field | void
**setText(String value)** | sets new text | void
**clear()** | clears the text field | void
**input(String value)** | sets new text | void
**focus()** | places cursor within the text field | void
**placeholder()** | returns value of the placeholder attribute | String
**getText()** | returns text from the text field  | String
**getValue()** | returns text from the text field| String

[Test examples in Java](https://github.com/jdi-testing/jdi-light/blob/master/jdi-light-html-tests/src/test/java/io/github/epam/html/tests/elements/simple/TextFieldTests.java)

### TextArea
```java 
@UI("#text-area") 
// same as FindBy(css = "#text-area")
public static TextArea textArea;

    @Test
    public void getLinesTest() {
        textArea.setLines("test 1", "test 2", "test 3");
        assertEquals(textArea.getLines(), asList("test 1", "test 2", "test 3"));
    }
    
    @Test
    public void focusTest() {
        textArea.focus();
    }
    
    @Test
    public void rowsTest() {
        assertEquals(textArea.rows(), 3);
        assertEquals(textArea.cols(), 33);
        assertEquals(textArea.minlength(), 10);
        assertEquals(textArea.maxlength(), 200);
    }
     
    @Test
    // this test demonstrates usage of methods inherited from TextField interface:
    public void clearTest() {
             textArea.setText(text);
             textArea.clear();
             assertEquals(textArea.getText(), "");
    }
```
```csharp 
[FindBy(Css = "#text-area")]
public ITextArea TextArea;

    [Test]
    public void GetTextTest()
    {
        TextArea.SetText(Text);
        Assert.AreEqual(TextArea.GetText(), "Text");
    }
    
   [Test]
   public void AddNewLineTest()
   {
      TextArea.SetText("line1", "line2");
      TextArea.AddNewLine("line3");
      Assert.CollectionEquals(TextArea.GetLines(), new[] { "line1", "line2", "line3" });
   }
```

**TextArea** – is a simple element type that allows users to fill in text areas (that may contain a few lines). 

![InputTypeTextArea](../images/html/textArea_html.png)

Text areas are represented by the following classes in Java and C#:
 
  - __C#__: _JDI.Light.Elements.Common.TextArea_
  - __Java__: _com.epam.jdi.light.ui.html.common.TextArea_
  
In both Java and C# TextArea is a descendant of TextField and inherits its methods. But TextArea also has methods of its own.
 
Here is a list of available methods in C#:
  
|Method | Description | Return Type
--- | --- | ---
**SetLines(string[] lines)** | sets lines (text)  | void
**GetLines()** | returns lines (text) from the text area | string[]
**Rows()** | returns value of rows attribute | int
**Cols()** | returns value of cols attribute | int
**Minlength()** | returns value of minlength attribute | int
**Maxlength()** | returns value of maxlength attribute | int
**AddNewLine(string line)** | add line to the already existing  | void
**Is()** | returns object for work with assertions  | TextAreaAssert
**AssertThat()** | returns object for work with assertions  | TextAreaAssert
 
  [Test examples in C#](https://github.com/jdi-testing/jdi-light-csharp/blob/master/JDI.Light/JDI.Light.Tests/Tests/Simple/TextAreaTests.cs)
  
  And here are methods available in Java:
  
|Method | Description | Return Type
--- | --- | ---
**setLines(String... lines)** | sets lines (text)  | void
**getLines()** | returns lines (text) from the text area | List<String>
**rows()** | returns value of rows attribute | int
**cols()** | returns value of cols attribute | int
**minlength()** | returns value of minlength attribute | int
**maxlength()** | returns value of maxlength attribute | int
**placeholder()** | returns value of placeholder attribute | String
**addNewLine(String line)** | add line to the already existing  | void
**is()** | returns object for work with assertions  | TextAreaAssert
**assertThat()** | returns object for work with assertions  | TextAreaAssert

  [Test examples in Java](https://github.com/jdi-testing/jdi-light/blob/master/jdi-light-html-tests/src/test/java/io/github/epam/html/tests/elements/simple/TextAreaTests.java)

### Title
**Title** – a graphical control element, that is the title of the document, which is displayed in the title bar of the browser or tab page.

Title is represented by the following class:
 
  - __Java__: _com.epam.jdi.light.ui.html.common.Title_
  - __C#__: _JDI.Light.Elements.Common.Title_
  
  
```java 
@UI("[ui=jdi-title]") 
// equal to @FindBy(css = "[ui=jdi-title]") 
public static Title jdiTitle;

@Test
public void getTextTest() {
        assertEquals(jdiTitle.getText(), "Title text");
}

@Test
public void clickTest() {
        jdiTitle.click();
}    
    
```
```csharp 
[FindBy(Css = "[ui=jdi-title]")]
public Title JdiTitle;

[Test]
public void GetTextTest() 
{
        Assert.AreEqual(JdiTitle.GetText(), "Title text");
}

[Test]
public void ClickTest() 
{
        JdiTitle.ClickTitle();
}

[Test]
public void IsValidationTest()
{
       TestSite.Html5Page.JdiTitle.Is.Enabled();
       TestSite.Html5Page.JdiTitle.Is.Text(EqualTo(_text));
       TestSite.Html5Page.JdiTitle.Is.Text(Is(_text));
       TestSite.Html5Page.JdiTitle.Is.Text(EqualToIgnoringCaseMatcher.EqualTo("jdi TESTING platform"));
}

[Test]
public void AssertValidationTest()
{
       TestSite.Html5Page.JdiTitle.AssertThat.Text(EqualTo(_text));
}

[Test]
public void BaseValidationTest()
{
       BaseElementValidation(TestSite.Html5Page.JdiTitle);
}   
    
```


![Title](../images/title.png)

Here is the list of available methods in C# JDI Light:

|Method | Description | Return Type
--- | --- | ---
**Is** |Gets Title's assert | TitleAssert
**AssertThat** |Gets Title's assert | TitleAssert

Here is the list of available methods in Java JDI Light:

|Method | Description | Return Type
--- | --- | ---
**click()** |Click the title | void
**getText()** |Returns the title text  | String

[Java test examples](https://github.com/jdi-testing/jdi-light/blob/master/jdi-light-html-tests/src/test/java/io/github/epam/html/tests/elements/simple/TitleTests.java)

[C# test examples](https://github.com/jdi-testing/jdi-light-csharp/blob/master/JDI.Light/JDI.Light.Tests/Tests/Common/TitleTests.cs)


## Complex elements
### RadioButtons

**RadioButtons** – interface element that allows user to select one option from a predefined group.

Radio buttons are represented by the following class:
 
  - __Java__: _com.epam.jdi.light.ui.html.complex.RadioButtons_
  - __C#__: _JDI.Light.Elements.Complex.RadioButtons_

```java 
@UI("[name=colors]") //@FindBy(name = "colors")
public static RadioButtons colors;

@Test
public void selectTest() {
    colors.select(Blue);
    assertEquals(colors.getValue(), "Blue");
}
```
```csharp 
[FindBy(Css = "#colors")] 
public IRadioButtons MyRadioButtons;

[Test]
public void SelectRadioButton() 
{
    MyRadioButtons.Select("some value");
}
[Test]
public void SelectRadioButtonByIndex() 
{
    MyRadioButtons.Select(1);
}
[Test]
public void GetSelected() 
{
    var selected = MyRadioButtons.GetSelected();
    Assert.AreEqual(selected, "some value");
	MyRadioButtons.Is().Selected(Is.EqualTo("some value")); 
	MyRadioButtons.AssertThat().Selected(Is.EqualTo("some value"));
}
```

Consider an example where each radio button is a particular color, described with given HTML code:

![RadioButton](../images/html/radio_html.png)

Here is the list of some available methods:

|Method | Description | Return Type
--- | --- | ---
**select(String/int/Enum)/Select(string/int)** |Select radiobutton by value/index  | void
**selected()/Selected()** |Get selected radiobutton value  | string
**is()** | returns object for work with assertions  | RadioButtonAssert
**assertThat()** | returns object for work with assertions  | RadioButtonAssert

[Java test examples](https://github.com/jdi-testing/jdi-light/blob/master/jdi-light-html-tests/src/test/java/io/github/epam/html/tests/elements/complex/RadioTests.java)

[C# test examples](https://github.com/jdi-testing/jdi-light-csharp/blob/master/JDI.Light/JDI.Light.Tests/Tests/Complex/RadioButtonsTests.cs)

### Table

**Table** – a complex element that consists of header, body (at least one row and one column) and footer. You are able to perform a list of readonly interactions with this element.

Tables are represented by the following classes in Java and C#:

```java 
         @UI("#users-table") //@FindBy(id = "users-table")
         public static Table users;
         	@JTable(
         		root = "#users-table",
         		row = "//tr[%s]/td",
         		column = "//tr/td[%s]",
         		cell = "//tr[{1}]/td[{0}]",
         		allCells = "td",
         		headers = "th",
         		header = {"Name", "Phone", "Email", "City"},
         	 	rowHeader = "Name",
         		size = 4
         	) public static Table usersSetup;
         
         
         @Test
            public void tablePerformanceTest() {
                tablePerformance(users);
            }
         @Test
            public void jTablePerformanceTest() {
                tablePerformance(usersSetup);
            }
            
            private void tablePerformance(Table table) {
                assertEquals(table.size(), 4);
                assertEquals(table.count(), 400);
                assertEquals(table.header(), asList("Name", "Phone", "Email", "City"));
                start();
                assertEquals(table.row(1).getValue(),
                        "Burke Tucker;076 1971 1687;et.euismod.et@ut.edu;GozŽe");
                logTime("Get 1 row");
        
                assertEquals(table.row("Burke Tucker").getValue(),
                        "Burke Tucker;076 1971 1687;et.euismod.et@ut.edu;GozŽe");
                logTime("Get 'Burke Tucker' row");
        
                String zacharyEmail = "ipsum.non.arcu@auctorullamcorper.ca";
                assertEquals(table.cell(3,4), zacharyEmail);
                logTime("Get cell(3,4)");
                assertEquals(table.cell("Email",4), zacharyEmail);
                logTime("Get cell(Email,4)");
                assertEquals(table.cell(3,"Zachary Hendrix"), zacharyEmail);
                logTime("Get cell(3,Zachary Hendrix)");
                assertEquals(table.cell("Email","Zachary Hendrix"), zacharyEmail);
                logTime("Get cell(Email,Zachary Hendrix)");
        
                assertEquals(table.column(2).getValue().substring(0, 30),
                        "076 1971 1687;(011307) 16843;0");
                logTime("Get column(2)");
        
                assertEquals(table.column("Phone").getValue().substring(0, 30),
                        "076 1971 1687;(011307) 16843;0");
                logTime("Get column(Phone)");
        
                String value = table.preview();
                assertEquals(value.substring(0,194),
                "Name Phone Email City" +
                    "Burke Tucker 076 1971 1687 et.euismod.et@ut.edu GozŽe" +
                    "Grady Brock (011307) 16843 cursus.et@commodo.org Alcobendas" +
                    "Harding Lloyd 0800 1111 neque.In.ornare@mauris.co.uk Beauvais");
                logTime("Preview");
                /*value = table.getValue();
                assertEquals(value.substring(0,228),
                    "||X||Name|Phone|Email|City||\r\n" +
                    "||1||Burke Tucker|076 1971 1687|et.euismod.et@ut.edu|GozŽe||\r\n" +
                    "||2||Grady Brock|(011307) 16843|cursus.et@commodo.org|Alcobendas||\r\n" +
                    "||3||Harding Lloyd|0800 1111|neque.In.ornare@mauris.co.uk|Beauvais||");
                logTime("Get value");*/
            }
         @Test
            public void tableDataTest() {
                assertEquals(users.row(2).asData(UserInfo.class),
                        GRADY_BROCK);
            }
         @Test
            public void tableEntityTest() {
                UserRow user = users.row(2).asLine(UserRow.class);
                user.name.click();
                validateAlert(containsString("Brock"));
                user.city.click();
                validateAlert(is("Alcobendas"));
            }
        
            private static long timeStart;
            public static void start() {
                timeStart = currentTimeMillis();
            }
            public static void logTime(String description) {
                out.println(description + ": " + (currentTimeMillis() - timeStart) + "ms");
                timeStart = currentTimeMillis();
            }	
         @Test
             public void hugeTableSearchTest() {
                 StopWatch timer = StopWatch.createStarted();
                 Line row = usersTable.row(
                     containsValue("Meyer", inColumn("Name")),
                     containsValue("co.uk", inColumn("Email")));
                 System.out.println("Huge table search test Time: " + timer.getTime());
                 Assert.assertEquals(row.getValue(),
                 "Brian Meyer;(016977) 0358;mollis.nec@seddictumeleifend.co.uk;Houston");
             }
         @Test
             public void hugeTableValidateTest() {
                 StopWatch timer = StopWatch.createStarted();
                 String actualTable = usersTable.preview();
                 System.out.println("Huge table validate test Time: " + timer.getTime());
                 Assert.assertEquals(actualTable, TABLE_SNAPSHOOT);
             }
         @Test
             public void bigDropdownTest() {
                 String name = "Charles Byers";
                 StopWatch timer = StopWatch.createStarted();
                 userNames.select(name);
                 System.out.println("Big dropdown test Time: " + timer.getTime());
                 Assert.assertEquals(userNames.selected(), name);
             }
         @Test
             public void longTextTest() {
                 String text = "Lorem ipsum dolor sit amet, eos numquam rationibus ad. Ius cu accumsan salutatus, ne pro purto ridens vulputate. Cu eum doctus tritani, munere sanctus complectitur vis id. Paulo vulputate te eos, suas tollit laudem nam id. His esse rebum reprimique ut, te solum atqui homero vim.\\n\\n" +
                         "Labitur salutatus eos an. Vim ut dicam fuisset. Ex sed animal accommodare, utinam graeci iisque vim id, ea fugit scripta deleniti nec. Eos cu nisl veri meis. Affert audiam copiosae mel ne, fabulas menandri temporibus has et. Sed latine graecis ei, eu fugit soluta intellegam vis, nibh graeci meliore ad duo.\\n\\n" +
                         "Et quis meis delenit mea, ius ea sumo laboramus vituperatoribus. Te simul luptatum tractatos nam, eam in causae constituam, quod stet ancillae nam ei. Ne his dico veniam legere, id has vidisse euismod sanctus. Vis putant volumus tincidunt et.\\n\\n" +
                         "Has eirmod consequat ad. Sea illud clita ut, has quando accusata cotidieque an, volutpat iudicabit definitionem ut sea. Pri at atqui molestiae, nibh ullum consulatu vix at. Nec id nisl nonumes epicurei, et vitae possit probatus ius. Fierent delicata argumentum ut quo. Tation tincidunt sed eu, sit in nostrud democritum.\\n\\n" +
                         "Usu esse utroque sapientem ad. Eam ut consul soleat sapientem, cu dolor consequuntur vis. Erat temporibus mea id, has ex dicam tritani. Pertinacia expetendis consectetuer eos ei, vidit malis periculis est ea, ne nam movet fuisset. Pro id habemus definitiones, in ferri solum reprehendunt mei. Vel eligendi honestatis liberavisse id.";
                 StopWatch timer = StopWatch.createStarted();
                 textareaPerformance.setText(text + "\\n"+ text);
                 System.out.println("Long text test Time: " + timer.getTime());
             }	
  ```

```csharp
       
        [Test]
        public void HugeTableSearchByColumnNamesContainValuesTest()
        {
            PerformancePage.UsersTable.AssertThat().HasRowWithValues(
                ContainsValue("Meyer", InColumn("Name")),
                ContainsValue("co.uk", InColumn("Email")));
            var row = PerformancePage.UsersTable.Row(
                ContainsValue("Meyer", InColumn("Name")),
                ContainsValue("co.uk", InColumn("Email")));
                Assert.AreEqual("Brian Meyer;(016977) 0358;mollis.nec@seddictumeleifend.co.uk;Houston",
                    row.GetValue());
        }

        [Test]
        public void HugeTableSearchByColumnNumbersContainValuesTest()
        {
            PerformancePage.UsersTable.AssertThat().HasRowWithValues(
                ContainsValue("Burke", InColumn(1)),
                ContainsValue("ut.edu", InColumn(3)));
            var row = PerformancePage.UsersTable.Row(1);
            PerformancePage.UsersTable.Is().HasRowWithValues( 
				HasValue("Brian Meyer", InColumn("Name")), 
				HasValue("(016977) 0358", InColumn("Phone")),
                HasValue("mollis.nec@seddictumeleifend.co.uk", InColumn("Email")), 
				HasValue("Houston", InColumn("City")));
        }

        [Test]
        public void HugeTableSearchByColumnNamesHasValuesTest()
        {
            PerformancePage.UsersTable.AssertThat().HasRowWithValues(
                HasValue("Brian Meyer", InColumn("Name")),
                HasValue("mollis.nec@seddictumeleifend.co.uk", InColumn("Email")));
            var row = PerformancePage.UsersTable.Row(
                HasValue("Brian Meyer", InColumn("Name")),
                HasValue("mollis.nec@seddictumeleifend.co.uk", InColumn("Email")));
            Assert.AreEqual("Brian Meyer;(016977) 0358;mollis.nec@seddictumeleifend.co.uk;Houston",
                row.GetValue());
        }

        [Test]
        public void HugeTableSearchByColumnNumbersHasValuesTest()
        {
            PerformancePage.UsersTable.AssertThat().HasRowWithValues(
                HasValue("Brian Meyer", InColumn(1)),
                HasValue("mollis.nec@seddictumeleifend.co.uk", InColumn(3)));
            var row = PerformancePage.UsersTable.Row(
                ContainsValue("Meyer", InColumn("Name")),
                ContainsValue("co.uk", InColumn("Email")));
            Assert.AreEqual("Brian Meyer;(016977) 0358;mollis.nec@seddictumeleifend.co.uk;Houston",
                row.GetValue());
        } 

		[Test]
        public void TableChainTest()
        {            
            PerformancePage.UsersTable.AssertThat()
                .Size(400)
                .Size(Is.GreaterThan(399))                
                .HasRowWithValues(
                    HasValue("Brian Meyer", InColumn("Name")),
                    HasValue("mollis.nec@seddictumeleifend.co.uk", InColumn("Email")))
                .NotEmpty()
                .RowsWithValues(3, ContainsValue("Baker", InColumn(1)))
                .HasColumn("Email")
                .HasColumns(new[] {"Name", "City"})
                .Columns(Is.SubsequenceOf(new[] {"Name", "City", "Phone", "Email", "Address"}));
        }
		
		[Test]
        public void TableRowPerformanceTest()
        {
            PerformancePage.Open();
            PerformancePage.CheckOpened();
            AreEqual("Burke Tucker;076 1971 1687;et.euismod.et@ut.edu;GozŽe", PerformancePage.UsersTable.Row(1).GetValue());
            AreEqual("Burke Tucker;076 1971 1687;et.euismod.et@ut.edu;GozŽe", PerformancePage.UsersTable.Row("Burke Tucker").GetValue());
            AreEqual("Burke Tucker;076 1971 1687;et.euismod.et@ut.edu;GozŽe", PerformancePage.UsersTable.Row(Users.Name).GetValue());
            var value = PerformancePage.UsersTable.Preview();
            AreEqual("Name Phone Email City" +
                "Burke Tucker 076 1971 1687 et.euismod.et@ut.edu GozŽe" +
                "Grady Brock (011307) 16843 cursus.et@commodo.org Alcobendas" +
                "Harding Lloyd 0800 1111 neque.In.ornare@mauris.co.uk Beauvais", value.Substring(0, 194));
        }

        [Test]
        public void TableCellPerformanceTest()
        {
            PerformancePage.Open();
            PerformancePage.CheckOpened();
            AreEqual("ipsum.non.arcu@auctorullamcorper.ca", PerformancePage.UsersTable.Cell(3, 4));
            AreEqual("ipsum.non.arcu@auctorullamcorper.ca", PerformancePage.UsersTable.Cell("Email", 4));
            AreEqual("ipsum.non.arcu@auctorullamcorper.ca", PerformancePage.UsersTable.Cell(3, "Zachary Hendrix"));
            AreEqual("ipsum.non.arcu@auctorullamcorper.ca", PerformancePage.UsersTable.Cell("Email", "Zachary Hendrix"));
        }

        [Test]
        public void TableColumnPerformanceTest()
        {
            PerformancePage.Open();
            PerformancePage.CheckOpened();
            AreEqual("076 1971 1687;(011307) 16843;0", PerformancePage.UsersTable.Column(2).GetValue().Substring(0, 30));
            AreEqual("076 1971 1687;(011307) 16843;0", PerformancePage.UsersTable.Column("Phone").GetValue().Substring(0, 30));
            AreEqual("076 1971 1687;(011307) 16843;0", PerformancePage.UsersTable.Column(Users.Phone).GetValue().Substring(0, 30));
        }		
```

  - __Java__: _com.epam.jdi.light.elements.complex.table.Table.java_
  - __C#__: _JDI.Light.Elements.Complex.Table.cs_
    
  ![Table](../images/html/tableHtml.png)

Here is a list of available methods in Java:

| Method | Description | Return Type|
--- | --- | ---
**cell(int colNum, int rowNum)** | Returns a cell object of a table according to the cell's index | String
**cell(int colNum, String rowName)** | Returns a cell object of a table according to the cell's index | String
**cell(String colName, int rowNum)** | Returns a cell object of a table according to the cell's index | String
**cell(String colName, String rowNum)** | Returns a cell object of a table according to the cell's index | String
**column(Enum colName)** | Returns a column object of a table according to column name | Line
**column(int colNum)** | Returns a column object of a table according to column number | Line
**column(String colName)** | Returns a column object of a table according to column name | Line
**columns()** | Returns a list of column objects of a table | List\<Line>
**filterRows(Matcher<String> matcher, Column column)** | Sets and returns a list of filtered rows of a table according to matching column | List\<Line>
**filterRows(Pair<Matcher<String>,Column>... matchers)** | Sets and returns a list of filtered rows of a table according to matching column | List\<Line>
**getValue()** | Returns a string content of values for particular row, where values are separated by ";" | String
**isEmpty()** | Asserts whether table is empty | boolean
**isNotEmpty()** | Asserts whether table is not empty | boolean
**preview()** | Returns table preview | String
**row(Enum rowName)** | Returns a row object of a table according to row name | Line
**row(int rowNum)** | Returns a row object of a table according to row number | Line
**row(Matcher<String> matcher, Column column)** | Returns a row object of a table according to matching column | Line
**row(Pair<Matcher<String>,Column>... matchers)** | Returns a row object of a table according to matching column | Line
**row(String rowName)** | Returns a row object of a table according to row name | Line
**row(TableMatcher... matchers)** | Returns a row object of a table according to matcher | Line
**rows()** | Returns a list of rows of a table | List\<Line>
**rows(TableMatcher... matchers)** | Returns a a list of rows of a table according to matchers | List\<Line>
**size()** | Return amount of columns | int
**count()** | Return return amount of rows | int
**header()** | Return a list of table's headers | List<String>
**webRow(int rowNum)** | Return all UIElements in the row according to row number | List<UIElement>
**webRow(String rowName)** | Return all UIElements in the row according to row name | List<UIElement>
**webRow(Enum rowName)** | Return all UIElements in the row according to row name | List<UIElement>
**webColumn(int colNum)** | Return all UIElements in the column according to column number | List<UIElement>
**webColumn(String colName)** | Return all UIElements in the column according to column name | List<UIElement>
**webColumn(Enum colName) Return** | All UIElements in the column according to column name | List<UIElement>
**webCell(int colNum, int rowNum)** | Return all UIElements in the column according to cell position | List<UIElement>
  
AssertTable methods in Java:
| Method | Description | Return Type|
--- | --- | ---
**assertThat()** | Applicable for performing assert actions for tables | TableAssert
**has()** | Applicable for performing assert actions for tables | TableAssert
**is()** | Applicable for performing assert actions for tables | TableAssert
**shouldBe()** | Applicable for performing assert actions for tables | TableAssert
**waitFor()** | Applicable for performing assert actions for tables | TableAssert

And here are methods available in C#:

| Method | Description | Return Type|
--- | --- | ---
**AssertThat()** | Applicable for performing assert actions for tables | TableAssert
**Is()** | Applicable for performing assert actions for tables | TableAssert
**ContainsValue(string value, Column column)** | Sets an object finding by some value occurance in particular column | TableMatcher 
**HasValue(string value, Column column)** | Sets an object finding by some full value in particular column | TableMatcher
**InColumn(string value)** | Sets an object of some column by particular value | Column
**InColumn(int num)** | Sets an object of some column by particular column's number | Column
**Row(params TableMatcher[] matchers)** | Sets and returns a row object of a table according to some matchers' params (returns 'null' if there is no such row) | Line
**Row(int rowNum)** | Sets and returns a row object of a table according to the row's index | Line
**Row(string rowName)** | Sets and returns a row object of a table according to the row's name | Line
**Row(Enum rowName)** | Sets and returns a row object of a table according to row's name | Line
**Row(Matcher<String> matcher, Column column)** | Sets and returns a row object of a table according to matching column | Line
**Row(params KeyValuePair<Matcher<string>, Column>[] matchers)** | Sets and returns a row object of a table according to matching column | Line
**RowsAsLines(params TableMatcher[] matchers)** | Sets and returns a a list of rows of a table according to matchers | List<Line>
**RowsAsLines()** | Sets and returns a list of rows of a table | List<Line>
**FilterRows(Matcher<String> matcher, Column column)** | Sets and returns a list of filtered rows of a table according to matching column | List<Line>
**FilterRows(params KeyValuePair<Matcher<string>, Column>[] matchers)** | Sets and returns a list of filtered rows of a table according to matching column | List<Line>
**Cell(int colNum, int rowNum)** | Sets and returns a cell object of a table according to the cell's indexes | string
**Cell(string colName, int rowNum)** | Sets and returns a cell object of a table according to the cell's column name and row index | string
**Cell(int colNum, string rowName)** | Sets and returns a cell object of a table according to the cell's column index and row name | string
**Cell(string colName, string rowName)** | Sets and returns a cell object of a table according to the cell's column name and row name | string
**Column(int colNum)** | Sets and returns a column object of a table according to the column's index | Line
**Column(string colName)** | Sets and returns a column object of a table according to the column's name | Line
**Column(Enum colName)** | Sets and returns a column object of a table according to column name | Line
**Columns()** | Sets and returns a list of column objects of a table | List<Line>
**GetValue()** | Returns a string content of values for particular row, where values are separated by ";" | string
**string Preview()** | Returns a string content of the whole table | string

AssertTable methods in C#:

| Method | Description | Return Type|
--- | --- | ---
**Empty()** | Asserts whether table is empty | TableAssert
**NotEmpty()** | Asserts whether table is not empty | TableAssert
**Size(Matcher<int> condition)** | Asserts whether table size satisfy some matcher | TableAssert
**Size(int expectedSize)** | Asserts whether table has particular size | TableAssert
**HasColumn(string column)** | Asserts whether table has particular header | TableAssert
**HasColumns(IEnumerable<string> columns)** | Asserts whether table has particular headers | TableAssert
**Columns(Matcher<IEnumerable<string>> condition)** | Asserts whether headers satisfy some matcher | TableAssert
**RowsWithValues(int count, params TableMatcher[] matchers)** | Asserts whether rows with particular matchers exist in a table multiple times | TableAssert
**HasRowWithValues(params TableMatcher[] matchers)** | Asserts whether a row with particular matchers exists in a table | TableAssert

[Java test examples](https://github.com/jdi-testing/jdi-light/blob/master/jdi-light-examples/src/test/java/io/github/epam/tests/recommended/TableTests.java)

[C# test examples](https://github.com/jdi-testing/jdi-light-csharp/blob/master/JDI.Light/JDI.Light.Tests/Tests/Composite/TableTests.cs)

### DataTable

**DataTable** – a complex element that consists of header, body (at least one row and one column) and footer. You are 
able to perform a list of readonly interactions with this element in order to get all data for the specified criteria.

DataTables are represented by the following classes in Java and C#:

```java 
         
         @UI("#users-table") //@FindBy(id = "users-table")
         public static DataTable<UserRow, UserInfo> usersData;
         	@JTable( root = "#users-table",
         		row = "//tr[%s]/td", column = "//tr/td[%s]",
         		cell = "//tr[{1}]/td[{0}]", allCells = "td",
         		headers = "th", header = {"Name", "Phone", "Email", "City"},
         		rowHeader = "Name", size = 4
         	)
         	public static DataTable<UserRow, UserInfo> usersDataSetup;
         
         @Test
             public void dataTableTest() {
                 dataTableValidation(usersData);
             }
         @Test
             public void jDataTableTest() {
                 dataTableValidation(usersDataSetup);
             }
             private void dataTableValidation(DataTable<UserRow, UserInfo> table) {
                 assertEquals(table.size(), 4);
                 assertEquals(table.count(), 400);
                 assertEquals(table.header(), asList("Name", "Phone", "Email", "City"));
                 String value = table.preview();
                 assertEquals(value.substring(0,194),
                 "Name Phone Email City" +
                     "Burke Tucker 076 1971 1687 et.euismod.et@ut.edu GozŽe" +
                     "Grady Brock (011307) 16843 cursus.et@commodo.org Alcobendas" +
                     "Harding Lloyd 0800 1111 neque.In.ornare@mauris.co.uk Beauvais");
             }
         @Test
             public void filterDataTest() {
                 assertEquals(usersData.data(2), GRADY_BROCK);
                 assertEquals(usersData.data("Grady Brock"), GRADY_BROCK);
                 assertEquals(usersData.data(d -> d.name.contains("Brock")), GRADY_BROCK);
                 usersData.assertThat().row(d -> d.equals(GRADY_BROCK));
                 /*
                 List<UserInfo> filteredData = usersData.datas(d -> d.name.contains("Brock"));
                 assertEquals(filteredData.size(), 1);
                 assertEquals(filteredData.get(0), GRADY_BROCK);
                 */
             }
         @Test
             public void filterLinesTest() {
                 UserRow line =  usersData.line(2);
                 validateUserRow(line);
                 line =  usersData.line("Grady Brock");
                 validateUserRow(line);
                 line =  usersData.line(d -> d.name.contains("Brock"));
                 validateUserRow(line);
                 /*
                 List<UserRow> filteredData = usersData.lines(d -> d.name.contains("Brock"));
                 assertEquals(filteredData.size(), 1);
                 validateUserRow(filteredData.get(0));
                 */
             }
         
             private void validateUserRow(UserRow line) {
                 line.city.click();
                 validateAlert(is(GRADY_BROCK.city));
                 assertEquals(line.email.getText(), GRADY_BROCK.email);
             }	    
         @Test
             public void tableParamsTest() {
                     assertEquals(users.size(), 4);
                     assertEquals(users.count(), 6);
                     assertEquals(users.header(), asList("Number", "Type", "User", "Description"));
             }    
         @Test
             public void previewTest() {
                     if (isFireFox()) return;
                     String value = users.preview();
                     assertEquals(value,
                             "Number Type User Desciption1  Admin User Manager RomanWolverineVip2  Admin User Manager Sergey IvanSpider ManVip3  Admin User Manager VladzimirPunisherVip4  Admin User Manager Helen BennettCaptain Americasome descriptionVip5  Admin User Manager Yoshi TannamuriCyclopesome descriptionVip6  Admin User Manager Giovanni RovelliHulksome descriptionVip");
             }   
         @Test
             public void valueTest() {
                     String value = users.getValue();
                     assertEquals(value,
                     "||X||Number|Type|User|Description||\r\n" +
                         "||1||1|Admin|Roman|Wolverine:VIP||\r\n" +
                         "||2||2|User|Sergey Ivan|Spider Man:Dude||\r\n" +
                         "||3||3|Manager|Vladzimir|Punisher:VIP||\r\n" +
                         "||4||4|User|Helen Bennett|Captain America\\nsome description:Dude||\r\n" +
                         "||5||5|User|Yoshi Tannamuri|Cyclope\\nsome description:Dude||\r\n" +
                         "||6||6|User|Giovanni Rovelli|Hulk\\nsome description:Dude||\r\n");
             }
         @Test
             public void dataColumnTestIndex() {
                     assertEquals(users.data(2), SPIDER_MAN);
             }
         @Test
             public void dataColumnNameTest() {
                     assertEquals(usersSetup.data("Sergey Ivan"), SPIDER_MAN);
             }
         @Test
             public void dataFilterTest() {
                     assertEquals(users.data(d -> d.user.contains("Ivan")), SPIDER_MAN);
             }
         @Test
             public void allDataFilterTest() {
                     List<MarvelUserInfo> filteredData = users.datas(d -> d.user.contains("Ivan"));
                     assertEquals(filteredData.size(), 1);
                     assertEquals(filteredData.get(0), SPIDER_MAN);
             }
         @Test
             public void commonMatchersTest() {
                     users.is().displayed();
                     users.has().size(6);
                     users.assertThat().size(greaterThan(3));
                     users.is().notEmpty().size(lessThanOrEqualTo(6));
             }
         @Test
             public void rowMatcherTest() {
                     users.has().row(d -> d.user.contains("Ivan"));
             }
         @Test
             public void rowsMatcherTest() {
                     users.assertThat().allRows(d -> d.user.length() > 4);
             }
         @Test
             public void atLeastMatcherTest() {
                     users.assertThat().atLeast(3).rows(d -> d.type.contains("User"));
             }
         @Test
             public void exactMatcherTest() {
                     users.assertThat().exact(2).rows(d -> d.description.contains(":VIP"));
             }
         @Test
             public void rowDataMatcherTest() {
                     users.has().row(SPIDER_MAN);
             }
         @Test
             public void rowDataExactMatcherTest() {
                     users.assertThat().exact(1).rows(SPIDER_MAN);
             }
         @Test
             public void tableChainTest() {
                     users.assertThat()
                         .displayed()
                         .size(6)
                         .size(greaterThan(3))
                         .notEmpty()
                         .row(d -> d.user.contains("Ivan"))
                         .allRows(d -> d.user.length() > 4)
                         .atLeast(3).rows(d -> d.type.contains("User"))
                         .row(SPIDER_MAN)
                         .exact(2).rows(d -> d.description.contains(":VIP"))
                         .exact(1).rows(SPIDER_MAN);
             }	
         @Test
             public void lineByIndexTest() {
                 MarvelUser line = users.line(2);
                 validateUserRow(line);
             }
         @Test
             public void lineByNameTest() {
                 MarvelUser line = usersSetup.line("Sergey Ivan");
                 validateUserRow(line);
             }
         @Test
             public void lineFilterTest() {
                 MarvelUser line = users.line(d -> d.user.contains("Ivan"));
                 validateUserRow(line);
             }
         @Test
             public void linesFilterTest() {
                 List<MarvelUser> filteredData = users.lines(d -> d.user.contains("Ivan"));
                 assertEquals(filteredData.size(), 1);
                 validateUserRow(filteredData.get(0));
             }
         
             public static void validateUserRow(MarvelUser line) {
                 line.type.select("Admin");
                 assertEquals(line.type.getValue(), "Admin");
                 line.type.select("User");
                 line.number.assertThat().text(is("2"));
             } 
         @Test
             public void baseValidationTest() {
                 baseValidation(users);
             }
  ```
 
  - __Java__: _com.epam.jdi.light.elements.complex.table.DataTable.java_
  - __C#__:
    
  ![DataTable](../images/html/tableHtml.png)

Here is a list of available methods in Java (_btw DataTable expand Table class - methods from previous table are available too_):

In return types column "D" refers to user data object and "L" refers to table line object.

| Method | Description | Return Type|
--- | --- | ---
**allData()** | Gets all section rows from the specified table | List\<D>
**allLines()** | Gets all object rows from the specified table | List\<L>
**data(Enum rowName)** | Returns a section of a table according to row name | D
**data(int rowNum)** | Returns a section of a table according to row number | D
**data(JFunc1<D, Boolean> matcher)** | Returns a section of a table according to matching row | D
**data(Matcher<String> matcher, Column column)** | Returns a section of a table according to matching row and column | D
**data(Pair<Matcher<String>,Column>...matchers)** | Returns a section of a table according to matching column | D
**data(String rowName)** | Returns a section of a table according to row name | D
**data(TableMatcher...matchers)** | Returns a section of a table according to matchers | D
**datas(JFunc1<D, Boolean> matcher)** | Returns a list of sections of a table according to matchers | List\<D>
**datas(JFunc1<D, Boolean> matcher, int amount)** | Returns a list of sections of a table according to matchers | List\<D>
**datas(TableMatcher...matchers)** | Returns a list of sections of a table according to matchers | List\<D>
**filterData(Matcher<String> matcher, Column column)** | Returns a list of sections of a table according to matching row and column | List\<D>
**filterDatas(Pair<Matcher<String>,Column>...matchers)** | Returns a list of sections of a table according to matching column | List\<D>
**filterLines(Matcher<String> matcher, Column column)** | Returns a list of objects of a table according to matching row and column | List\<L>
**filterLines(Pair<Matcher<String>,Column>...matchers)** | Returns a list of objects of a table according to matching column | List\<L>
**getValue()** | Returns a string content of values for particular row, where values are separated by "&#124;" | String
**line(Enum rowName)** | Returns an object of a table according to row name | L
**line(int rowNum)** | Returns an object of a table according to row number | L
**line(JFunc1<D, Boolean> matcher)** | Returns an object of a table according to matching row | L
**line(Matcher<String> matcher, Column column)** | Returns an object of a table according to matching row and column | L
**line(Pair<Matcher<String>,Column>...matchers)** | Returns an object of a table according to matching column | L
**line(String rowName)** | Returns an object of a table according to row name | L
**line(TableMatcher...matchers)** | Returns an object of a table according to matchers | L
**lines(JFunc1<D, Boolean> matcher)** | Returns a list of objects of a table according to matchers | List\<L>
**lines(TableMatcher...matchers)** | Returns a list of objects of a table according to matchers | List\<L>
**offCache()** | Turns off cache usage | void
**refresh()** | Clears all data and lines | void
**setup(Field field)** | Sets up the table using specified fields | void
**getValue()** | Return a table content separated by "\|" | String

DataTableAssert methods in Java:

| Method | Description | Return Type|
--- | --- | ---
**assertThat()** | Applicable for performing assert actions for tables | DataTableAssert
**has()** | Applicable for performing assert actions for tables | DataTableAssert
**is()** | Applicable for performing assert actions for tables | DataTableAssert
**shouldBe()** | Applicable for performing assert actions for tables | DataTableAssert
**waitFor()** | Applicable for performing assert actions for tables | DataTableAssert

[Java test examples](https://github.com/jdi-testing/jdi-light/blob/master/jdi-light-examples/src/test/java/io/github/epam/tests/recommended/DataTableTests.java)

### DropDown

**DropDown** – a graphical control element, that allows the user to choose one value from a list.

![DropDown](../images/dropdown.png)

JDI Light has support for dropdown elements with its own type. There are several ways of dropdown usage in JDI Light, serving different needs.

__JDI Dropdown annotation__

For better use JDI Light provides a __*@JDropdown*__ annotation to locate dropdown elements. This annotation consists of the following elements:

 - __*root()*__ - value of this element points to the root locator of dropdown element
 - __*value()*__ - locator of selected by default option in dropdown list
 - __*list()*__ - locator representing list options
 - __*expand()*__ - locator for expanding the dropdown list
 - __*how()*__ - type of locators with which elements will be identified. By default this is css
 
```java 
@JDropdown(root = "div[ui=dropdown]",
           value = ".filter-option",
           list = "li",
           expand = ".caret")
public Droplist colors;

@Test
public void complexTest() {
    metalAndColorsPage.shouldBeOpened();
    metalAndColorsPage.colors.select(Green);
}
```

```csharp 
[JDropDown(root: "#colors", 
           value: ".filter-option", 
           list:"li", 
           expand:".caret")]
public Droplist Colors;

[Test]
public void ComplexTest() 
{
    MetalAndColorsPage.ShouldBeOpened();
    MetalAndColorsPage.Colors.Select(Green);
}
```

Suppose we have 'Colors' dropdown, which looks like this in HTML code:

![Dropdown HTML](../images/html/dropdown_html.png) 

__Dropdown representation__

```java 
public Droplist colors;
@CSS("#colors") public Droplist colors;
public Droplist colors = dropdown("#colors");
public Droplist colors = $d("#colors");

@Test
public void colorsTest() {
    colors.select(Green);
    assertEquals(colors.selected(), Green);
}
```

```csharp 
public DropDown Colors;
[FindBy(Css = "#colors")] 
public DropDown Colors;

[Test]
public void ColorsTest() 
{
    Colors.Select(Green);
    Assert.AreEquals(Colors.Selected(), Green);
}
```

JDI Light provides a __Droplist__ class which can be used for dropdown representation as a type of web element.

Locator simple annotations from *com.epam.jdi.light.elements.pageobjects.annotations.simple* can be used together with dropdown elements.

[Java test examples](https://github.com/jdi-testing/jdi-light/blob/master/jdi-light-examples/src/test/java/io/github/epam/tests/epam/ComplexElementsTests.java)

For HTML5 elements Dropdown lists are also supported in JDI light. There is a __Dropdown__ class which is more like a special case of Droplist.
This type can be used in cases when dropdown is represented with HTML _\<select>_ tag.

Consider an example of HTML5 dropdown with a given HTML code:

```java 
@UI("#dress-code") //@FindBy(id = "dress-code")
public Dropdown dressCode;

@Test
public void selectEnumTest() {
    dressCode.select(Fancy);
    assertEquals(dressCode.getValue(), "Fancy");
}
```

```csharp 
[FindBy(Css = "#dress-code")] 
public Dropdown DressCode;

[Test]
public void SelectEnumTest() 
{
    DressCode.Select(Fancy);
    Assert.AreEquals(DressCode.GetSelected(), "Fancy");
}

[Test]
public void LabelTest()
{
    AreEqual(TestSite.Html5Page.DressCode.Label().GetText(), "Dress code:");
    TestSite.Html5Page.DressCode.Label().Is.Text(ContainsString("Dress"));
}

[Test]
public void IsValidationTest()
{
    TestSite.Html5Page.DressCode.Is.Selected("Casual");
    TestSite.Html5Page.DressCode.Is.Selected(DressCode.Casual);
    TestSite.Html5Page.DressCode.Is.Values(HasItems(new[] { "Pirate" }));
    TestSite.Html5Page.DressCode.Is.Disabled(HasItems(new[] { "Disabled" }));
    TestSite.Html5Page.DressCode.Is.Enabled(HasItems(new[] { "Pirate", "Fancy" }));
}

[Test]
public void AssertValidationTest()
{
    TestSite.Html5Page.DressCode.AssertThat.Values(
    ContainsInAnyOrder(new[] {"Fancy", "Casual", "Disabled", "Pirate"}));
}

[Test]
public void BaseValidationTest()
{
    BaseElementValidation(TestSite.Html5Page.DressCode);
}

```

![Dropdown HTML5](../images/html/dropdown_html5.png)

Here is the list of some available methods:

|Method | Description | Return Type
--- | --- | ---
**getValue()/getText()/getSelected()** | Return selected dropdown value | String
**selected(String option)** | Check if option has been selected | boolean
**isExpanded()** | Show that dropdown element expanded | boolean
**isDisplayed()** | Show\wait that dropdown element displayed on the screen | boolean
**expand()** | Expand dropdown list | void
**close()** | Close expanded before dropdown list | void
**size()** | Return amount of elements in the list | int
**setup(Field field)** | Setup the dropdown using specified fields | void
**sendKeys(CharSequence... charSequence)** | Send specific keys | void

Available Assert methods in Java:

|Method | Description | Return Type
--- | --- | ---
**is()** | Applicable for performing assert actions for DropDown's | ListAssert<UIElement>
**assertThat()** | Applicable for performing assert actions for DropDown's | ListAssert<UIElement>
**has()** | Applicable for performing assert actions for DropDown's | ListAssert<UIElement>
**waitFor()** | Applicable for performing assert actions for DropDown's | ListAssert<UIElement>
**shouldBe()** | Applicable for performing assert actions for DropDown's | ListAssert<UIElement>

Available Assert methods in C#:

|Method | Description | Return Type
--- | --- | ---
**Selected(string option)** |Checks whether some option is selected  | DropDownAssert 
**Selected(Enum option)** |Checks whether some option is selected  | DropDownAssert
**Values(Matcher<IEnumerable<string>> condition)** |Checks that dropdown's values match some contidion | DropDownAssert
**Disabled(Matcher<IEnumerable<string>> condition)** |Checks that dropdown's values are disabled by some condition | DropDownAssert
**Enabled(Matcher<IEnumerable<string>> condition)** |Checks that dropdown's values are enabled by some condition | DropDownAssert
**Is** |Gets dropdown's assertion | DropDownAssert
**AssertThat** |Gets dropdown's assertion | DropDownAssert

[Java test examples](https://github.com/jdi-testing/jdi-light/blob/master/jdi-light-html-tests/src/test/java/io/github/epam/html/tests/elements/complex/DropdownTests.java)

[C# test examples](https://github.com/jdi-testing/jdi-light-csharp/blob/master/JDI.Light/JDI.Light.Tests/Tests/Common/DropDownTests.cs)

### MultiDropDown

```java 
@UI("#multi-dropdown") //@FindBy(id = "multi-dropdown")
public static MultiSelect multiDropdown;

@Test
public void selectTest() {
    multiDropdown.check(Wood, Steam);
    assertEquals(multiDropdown.checked(), asList("Steam", "Wood"));
}
```
```csharp 
[FindBy(Css = "#multi-dropdown")]
public MultiDropdown MultiDropdown { get; set; }

[Test]
public void SelectMultipleOptions()
{
    var optionsList = new List<string> { "Steam", "Electro" };
    TestSite.Html5Page.MultiDropdown.SelectOptions(optionsList);
    Jdi.Assert.IsTrue(TestSite.Html5Page.MultiDropdown.OptionsAreSelected(optionsList));
}

[Test]
public void CheckOptionExists()
{
    TestSite.Html5Page.MultiDropdown.Expand();
    Jdi.Assert.IsTrue(TestSite.Html5Page.MultiDropdown.OptionExists("Steam"));
    Jdi.Assert.IsFalse(TestSite.Html5Page.MultiDropdown.OptionExists("Steam2"));
}

[Test]
public void CheckOptionIsDisabled()
{
    TestSite.Html5Page.MultiDropdown.Expand();
    Jdi.Assert.IsFalse(TestSite.Html5Page.MultiDropdown.OptionIsEnabled("Disabled"));
	Jdi.Assert.IsTrue(TestSite.Html5Page.MultiDropdown.OptionIsEnabled("Wood"));
}

[Test]
public void LabelTest()
{
    Jdi.Assert.AreEquals(TestSite.Html5Page.MultiDropdown.Label().GetText(), "Multi dropdown:");
    TestSite.Html5Page.MultiDropdown.Label().Is.Text(ContainsString("Multi"));
}

[Test]
public void IsValidationTest()
{
    TestSite.Html5Page.MultiDropdown.SelectOptions(new List<string> { "Steam" });
    TestSite.Html5Page.MultiDropdown.Is.Selected("Steam");
    TestSite.Html5Page.MultiDropdown.Is.Selected(Ages.Steam);
    TestSite.Html5Page.MultiDropdown.Is.Values(HasItems( new []{ "Wood" }));
    TestSite.Html5Page.MultiDropdown.Is.Disabled(HasItems(new[] { "Disabled" }));
    TestSite.Html5Page.MultiDropdown.Is.Enabled(HasItems( new []{ "Electro", "Metalic" }));
}

[Test]
public void AssertValidationTest()
{
    TestSite.Html5Page.MultiDropdown.SelectOptions(new List<string> { "Steam" });
    TestSite.Html5Page.MultiDropdown.AssertThat.Values(ContainsInAnyOrder( new []{ "Disabled", "Electro", "Metalic", "Wood", "Steam" }));
}

[Test]
public void BaseValidationTest()
{
    BaseElementValidation(TestSite.Html5Page.MultiDropdown);
}
```

**MultiDropDown** – a graphical control element, that allows the user to choose several values from a list.

![DropDown](../images/multidropdown.png)

Multi dropdown elements can be described by the following class:

 - __Java__: _com.epam.jdi.light.ui.html.complex.MultiDropdown_
 - __C#__: _JDI.Light.Elements.Composite.MultiDropdown_

Here is the list of some available methods in C# JDI Light:

|Method | Description | Return Type
--- | --- | ---
**OptionIsEnabled(string)** |Check whether option is enabled  | bool
**SelectOption(string)** |Select specified option  | void
**GetSelectedOptions()** |Get selected options  | List
**SelectOptions(List)** |Select specified options  | void
**OptionExists(string)** |Check whether option exists in list  | bool
**Expand()** |Expand list  | void
**Close()** |Close expanded list  | void

Available assert methods in C# JDI Light:

|Method | Description | Return Type
--- | --- | ---
**Selected(string option)** |Check whether option is selected  | MultiDropdownAssert
**Selected(Enum option)** |Check whether option is selected  | MultiDropdownAssert
**Values(Matcher<IEnumerable<string>> condition)** |Check whether whether some values exist in MultiDropDown by some matcher  | MultiDropdownAssert
**Disabled(Matcher<IEnumerable<string>> condition)** |Check whether whether some values are disabled in MultiDropDown by some matcher  | MultiDropdownAssert
**Enabled(Matcher<IEnumerable<string>> condition)** |Check whether whether some values are enabled in MultiDropDown by some matcher  | MultiDropdownAssert
**Is** |Gets multiDropDown's assert  | MultiDropdownAssert
**AssertThat** |Gets multiDropDown's assert  | MultiDropdownAssert

The list of available methods for Java JDI Light:

|Method | Description | Return Type
--- | --- | ---
**check(String/String.../Enum.../int...)** |Select values in multi dropdown | void
**uncheck(String.../Enum.../int...)** | Unselect values in multi dropdown | void
**selected()** | Get selected value by default | String
**checked()** | Get selected values | List\<String>

[Java test examples](https://github.com/jdi-testing/jdi-light/blob/master/jdi-light-html-tests/src/test/java/io/github/epam/html/tests/elements/complex/MultiDropdownTests.java)

[C# test examples](https://github.com/jdi-testing/jdi-light-csharp/blob/master/JDI.Light/JDI.Light.Tests/Tests/Composite/MultiDropdownTests.cs)

### DataList

**DataList** – a graphical control element, that allows the user to choose one value from a list or enter it by himself.
Datalist element contains a set of options with values available for entering.

![DataList](../images/icecreamdatalist.png)

__JDI DataList annotation__

For better use JDI Light provides a __*@JDataList*__ annotation to locate datalist elements. This annotation consists of the following elements:

 - __*root*__ - value of this element points to the root locator of dropdown element
 - __*values*__ - options locator in dropdown list
 - __*how*__ - type of locators with which elements will be identified. By default this is css
 
```java 
TBD
```

```csharp 
[JDataList(root: "#ice-cream", 
           values: "#ice-cream-flavors > option"]
public IDataList IceCream;

[JDataList("#disabled-dropdown",
          "#disabled-dropdown > option")]
        public DataList DisabledDropdownAsDataList { get; set; }

[Test]
public void ComplexTest() 
{
    IceCream.Select("Coconut");
}

[Test]
public void LabelTest()
{
    AreEqual(TestSite.Html5Page.IceCream.Label().GetText(), "Choose your lovely icecream");
    TestSite.Html5Page.IceCream.Label().Is.Text(ContainsString("lovely icecream"));
}

[Test]
public void IsValidationTest()
{
     TestSite.Html5Page.IceCream.Is.Enabled();
     TestSite.Html5Page.IceCream.Is.Attr("value" ,EqualTo(_text));
     TestSite.Html5Page.IceCream.Select("Vanilla");
     TestSite.Html5Page.IceCream.Is.Attr("value", ContainsString("Van"));
}

[Test]
public void AssertValidationTest()
{
     TestSite.Html5Page.IceCream.AssertThat.Attr("value", ContainsString(_text));
}

[Test]
public void BaseValidationTest()
{
     BaseElementValidation(TestSite.Html5Page.IceCream);
}

[Test]
public void NegativeSelectTest()
{
     Throws<ElementNotSelectableException>(() => TestSite.Html5Page.DisabledDropdownAsDataList.Select("Fancy", false));
}

[Test]
public void NegativeSelectEnumTest()
{
      Throws<ElementNotSelectableException>(() => TestSite.Html5Page.DisabledDropdownAsDataList.Select(DressCode.Fancy, false));
}

[Test]
public void NegativeSelectNumTest()
{
      Throws<ElementNotFoundException>(() => TestSite.Html5Page.IceCream.Select(7, false));
}

[Test]
public void AssertOptionsValuesTest()
{
      IsTrue(TestSite.Html5Page.IceCream.Values().SequenceEqual(_options));
}

```

Datalist element type is provided by JDI Light in:

 - __Java__: _com.epam.jdi.light.ui.html.complex.DataList_
 - __C#__: _JDI.Light.Elements.Common.DataList_
 
Have a look at the following example with provided HTML code:

```java 
@UI("#ice-cream") //@FindBy(id = "ice-cream")
public static DataList iceCreamDataList;DropDown

@Test
public void selectEnumTest() {
    iceCreamDataList.select(Strawberry);
    assertEquals(iceCreamDataList.getValue(), "Strawberry");
}
```


![Datalist example](../images/html/datalist_html.png)

The list of available methods in Java JDI Light:

|Method | Description | Return Type
--- | --- | ---
**select(String/Enum/int)** |Select datalist option by value or index | void
**selected()** |Get selected option value | String
**values()** |Get all option values from datalist | List\<String>
**listEnabled()** |Return list of values of enabled options | List\<String>
**listDisabled()** |Return list of values of disabled options | List\<String>

Here is the list of some available methods in C# JDI Light:

|Method | Description | Return Type
--- | --- | ---
**Expand()** |Expands the list of possible values | void
**Select(string/int)** |Select datalist by value/index  | void
**Input(string value)** |Input user's value into datalist  | void
**GetSelected()** |Get selected datalist value  | string

Available list of assert methods:

|Method | Description | Return Type
--- | --- | ---
**Is** |Gets element's assert | DataListAssert
**AssertThat** |Gets element's assert | DataListAssert

[Java test examples](https://github.com/jdi-testing/jdi-light/blob/master/jdi-light-html-tests/src/test/java/io/github/epam/html/tests/elements/complex/DataListTests.java)

[C# test examples](https://github.com/jdi-testing/jdi-light-csharp/blob/master/JDI.Light/JDI.Light.Tests/Tests/Common/DataListTests.cs)

### CheckList
**CheckList** – a graphical control element representing a set of checkboxes, each of which allows the user to control a two-state parameter (enabled or disabled).

Checklist element type is available in the following packages:
 
 - __Java__: com.epam.jdi.light.ui.html.complex.Checklist
 - __C__#: JDI.Light.Elements.Complex.CheckList 

See an example with a given HTML code describing checklist element.

```java 
@UI("[name=checks-group]") public static Checklist weather;
public static Checklist weatherNoLocator;

@Test
public void selectTest() {
    weather.check(Cold, Rainy);
    assertEquals(weather.checked(), asList("Cold", "Rainy day"));
}

@Test
public void assertValidationTest() {
    weather.assertThat().values(containsInAnyOrder(
      "Hot option", "Cold", "Rainy day", "Sunny", "Disabled"));
    weatherNoLocator.assertThat().selected("Hot option");
}
```
```csharp 
[FindBy(Css = "div:nth-child(11) > div.html-left")]
public ICheckList weather;

[FindBy(Css = "div:nth-child(11) > div.html-left")]
public ICheckList<MyCheckBox> genericWeather;

[Test]
public void CheckCheckList()
{
    weather.Check("Cold", "Hot option");
    Jdi.Assert.CollectionEquals(new[] { "Cold", "Hot option" }, weather.Checked());
}

[Test]
public void UncheckTest()
{
    _weather.Check(false, "Rainy day", "Sunny");
    _weather.Uncheck(false, "Rainy day", "Sunny");
    _weather.Is.Selected(HasSize(2));
    _weather.Is.Selected(HasItems(new[] { "Hot option", "Cold" }));
}

[Test]
public void IsValidationTests()
{
    weather.AssertThat
                .Values(HasItems(new[] {"Cold", "Sunny"}))
                .Disabled(HasItems(new[] {"Disabled"}))                
                .Size(Is.LessThan(6))
                .AllDisplayed();
}

[Test]
public void UncheckAllTest()
{
    _weather.Uncheck(false, "Rainy day", "Sunny");
    _weather.UncheckAll();
    _weather.Is.Selected(HasSize(0));
}

[Test]
public void CheckAllTest()
{
    _weather.CheckAll();
    _weather.Is.Selected(HasSize(4));
    _weather.Is.Selected(HasItems(new[] { "Hot option", "Cold", "Rainy day", "Sunny" }));
}

[Test]
public void IsDisabledTest()
{
    _weather.Select(false, "Disabled");
    _weather.Is.Selected(HasItems(new [] { "Hot option" } ));
}
```

![Checklist Example](../images/html/checklist_html.png)

List of available methods in Java JDI Light:

|Method | Description | Return Type
--- | --- | ---
**check(String.../Enum/int...)** | Check checkboxes | void
**uncheck(String.../Enum/int...)** | Unselect checkboxes | void
**select(String.../Enum/int...)** | Select checkboxes | void
**uncheckAll()** | Uncheck all checkboxes from checklist | void
**checkAll()** | Check all checkboxes from checklist | void
**checked()** | Get selected checkbox values | List\<String>
**values()** | Get checklist values | List\<String>
**listEnabled()** | Get enabled checkboxes | List\<String>
**listDisabled()** | Get disabled checkboxes | List\<String>
**size()** | Get checklist size | int
**is()** | Get select assert | selectAssert
**assertThat()** | Get select assert | selectAssert
**has()** | Get select assert | selectAssert
**selected()** | Get selected checkbox values | String

Here is the list of some available methods in C# JDI Light:

|Method | Description | Return Type
--- | --- | ---
**Check(params string[]/params int[])** |Check checklist by values/indexes  | void
**Uncheck(params string[]/params int[])** |Unselect checklist by values/indexes  | void
**Select(params string[]/params int[])** |Select checklist by values/indexes  | void
**UncheckAll()** |Uncheck all checkboxes | void
**CheckAll()** |Check all checkboxes | void
**Checked()** |Get selected checkboxes from checklist value  | List\<String>
**Values()** | Get checklist values | List\<String>
**ListEnabled()** | Get enabled checkboxes | List\<String>
**ListDisabled()** | Get disabled checkboxes | List\<String>
**Size()** | Get checklist size | int
**Is** | Get select assert | SelectAssert
**AssertThat** | Get select assert | SelectAssert
**Has** | Get select assert | SelectAssert
**Selected(string option)** | Checks whether checkbox is selected | bool


[Java test examples](https://github.com/jdi-testing/jdi-light/blob/master/jdi-light-html-tests/src/test/java/io/github/epam/html/tests/elements/complex/ChecklistTests.java)

[C# test examples](https://github.com/jdi-testing/jdi-light-csharp/blob/master/JDI.Light/JDI.Light.Tests/Tests/Complex/CheckListTests.cs)

### MultiSelector
**MultiSelector** – a graphical control element, that allows the user to do multiple choice.
Multi Selector are represented by the following class:
 
  - __Java__: _com.epam.jdi.light.ui.html.complex.MultiSelector_
  - __C#__: _JDI.Light.Elements.Common.MultiSelector_
  
  
```java 
@UI("#ages") 
// equal to @FindBy(css = "#ages") 
public static MultiSelect ages;

@Test
public void checkTest() {
       ages.check("Electro", "Metalic");
       assertEquals(ages.checked(), asList("Electro", "Metalic"));
    }
@Test
public void disabledTest() {
        ages.select("Disabled");
        assertEquals(ages.getValue(), text);
    }
```
```csharp 
[Test]
public void MultiSelectByValues() 
{
    MyMultiSelector.Select(string[]);
}
[Test]
public void MultiSelectByIndexes() 
{
    MyMultiSelector.Select(int[]);
}
```


![MultiSelector](../images/html/multiSelectHtml.png)

Here is a list of available methods and properties in C#:

|Method / Property | Description | Return Type
--- | --- | ---
**Check(string/string[]/int/int[]/Enum[])** | Select multiselector by values | void
**Uncheck(string[]/Enum[]/int[])** | Select multiselector by values/indexes | void
**Selected()** | Get selected values | string
**Checked()** | Get selected values  | List\<string>
**Is** | Property that returns object for work with assertions | SelectAssert
**AssertThat** | Property that returns object for work with assertions | SelectAssert
**has()** | Returns object for work with assertions | SelectAssert
**waitFor()** | Returns object for work with assertions | SelectAssert
**shouldBe()** | Returns object for work with assertions | SelectAssert

Here is the list of available methods/asserts in Java:

|Method | Description | Return Type
--- | --- | ---
**check(String/Strings.../TEnum...)** |Select multiselector by values | void
**uncheck(Strings.../TEnum.../int)** |Select multiselector by values/indexes  | void
**selected()** |Get selected values  | String
**checked()** |Get selected values  | List\<String>
**is()** |  Returns object for work with assertions| SelectAssert
**assertThat()** | Returns object for work with assertions| SelectAssert

[Java test examples](https://github.com/jdi-testing/jdi-light/blob/master/jdi-light-html-tests/src/test/java/io/github/epam/html/tests/elements/complex/MultiSelectorTests.java)

[C# test examples](https://github.com/jdi-testing/jdi-light-csharp/blob/master/JDI.Light/JDI.Light.Tests/Tests/Common/MultiSelectorTests.cs)

### ComboBox

**ComboBox** – a graphical control element, that allows the user to choose one
 value from a list or enter it by himself (is inherited from the [Datalist](#datalist))

![ComboBox](../images/icecreamdatalist.png)

ComboBox is provided by JDI Light in:
 
  - __Java__: _com.epam.jdi.light.ui.html.complex.Combobox_
  - __C#__: _JDI.Light.Elements.Common.Combobox_

```java 
public static Combobox iceCream;

@UI("#ice-cream") // @FindBy(id = "ice-cream")
public static DataList iceCreamDataList;

  
@Test
public void selectTest() {
    iceCreamDataList.select("Chocolate");
    assertEquals(iceCreamDataList.getValue(), "Chocolate");
}
@Test
public void selectNumTest() {
    iceCreamDataList.select(5);
    assertEquals(iceCreamDataList.getValue(), "Vanilla");
}
@Test
public void selectedTest() {
    assertEquals(iceCreamDataList.selected(), "Coconut");
}
@Test
public void labelTest() {
    assertEquals(iceCreamDataList.label().getText(), "Choose your lovely icecream");
    iceCreamDataList.label().is().text(containsString("lovely icecream"));
}
@Test
public void isValidationTest() {
    iceCream.is().enabled();
    iceCream.is().text(is(text));
    iceCream.select(Vanilla);
    iceCream.is().text(containsString("Van"));
}
```
```csharp 
[Test]
public void ExpandComboBox() 
{
    MyComboBox.Expand();
}
[Test]
public void SelectComboBox() 
{
    MyComboBox.Select("some value");
	MyComboBox.Is().Selected(Is.EqualTo("some value"));
	TestSite.Html5Page.IceCreamComboBox.AssertThat().Selected(Is.EqualTo("Strawberry"));	
}
[Test]
public void SelectByIndex() 
{
    MyComboBox.Select(1);
}
[Test]
public void FillComboBox() 
{
    MyComboBox.Input("some value");
    SubmitButton.Click();
}
```

Have a look at the following example with provided HTML code:  

![Combobox example](../images/html/datalist_html.png)

The list of available methods in Java JDI Light:

|Method | Description | Return Type
--- | --- | ---
**select(String/Enum/int)** |Select datalist option by value or index | void
**selected()** |Get selected option value | String
**values()** |Get all option values from datalist | List\<String>
**listEnabled()** |Return list of values of enabled options | List\<String>
**listDisabled()** |Return list of values of disabled options | List\<String>

Here is the list of some available methods in C# JDI Light:

|Method | Description | Return Type
--- | --- | ---
**Expand()** |Expands the list of possible values | void
**Select(string/int)** |Select datalist by value/index  | void
**Input(string)** |Input user's value into datalist  | void
**GetSelected()** |Get selected datalist value  | string
**is()** |  Returns object for work with assertions| ComboBoxAssert
**assertThat()** | Returns object for work with assertions| ComboBoxAssert

[Java test examples](https://github.com/jdi-testing/jdi-light/blob/master/jdi-light-html-tests/src/test/java/io/github/epam/html/tests/elements/complex/ComboboxTests.java)

[C# test examples](https://github.com/jdi-testing/jdi-light-csharp/blob/master/JDI.Light/JDI.Light.Tests/Tests/Common/ComboBoxTests.cs)

## Composite elements
###Section

**Section** - logical part of Web Page that contains other UI Elements
  
Section is represented by the following class:   

Java: com.epam.jdi.light.elements.composite.Section  
public class Section extends JDIBase implements PageObject 

C#: JDI.Light.Elements.Composite.Section  
public class Section : UIElement
  
```java 
   @UI(".someSectionUI") // @FindBy(css = ".someSectionUI")
   public static SomeSection someSectionUI;
   //public class SomeSection extends Section

   @Test
   public void someSectionWebElementTest() {
      assertNotNull(someSection.webElementPublic);
      assertEquals(someSection.webElementPublic.locator.toString(), "id='webElementPublic'");
      assertEquals(someSection.webElementPublic.parent, someSection);
      assertEquals(someSection.webElementPublic.name, "Web Element Public");
   }
   
```

```csharp

  [FindBy(Id = "contact-form")]
  public Contact ContactSection;
  
  [FindBy(Css = ".footer-content")]
  public static Footer Footer;
  
  [FindBy(Css = ".uui-header")]
  public static Header Header;
  
  public JdiSearch Search;
  
  [FindBy(Id = "summary-block")]
  public Summary SummaryBlock;
        
  [Test]
  public void SectionTest()
  {
      var e = TestSite.HomePage.Get<Section>(By.CssSelector(".main-title"));
      Assert.AreEqual("EPAM FRAMEWORK WISHES…", e.Text);
      Assert.AreEqual("Section", e.Name);
      Assert.AreEqual(true, e.Displayed);
      Assert.AreEqual(true, e.Enabled);
      Assert.AreEqual(false, e.Hidden);
      Assert.AreEqual(By.CssSelector(".main-title"), e.Locator);
      Assert.AreEqual(false, e.Selected);
      Assert.AreEqual("h3", e.TagName);
  }
  
  [TestCaseSource(nameof(ContactSectionCases))]
  public void CustomContactSectionTest(string htmlElementToCheckName, string expectedLocator, string expectedName, string expectedSmartLocator)
  {
      ContactSection.CheckInitializedElement(ContactSection.GetType().GetField(htmlElementToCheckName).GetValue(ContactSection) as UIElement, expectedLocator, expectedName, expectedSmartLocator);
  }

  [Test]
  public void CustomFooterSectionTest()
  {
      FooterSection.CheckInitializedElement(FooterSection.AboutLink, "By.PartialLinkText: About", "AboutLink", null);            
  }

  [TestCaseSource(nameof(HeaderSectionCases))]
  public void CustomHeaderSectionTest(string htmlElementToCheckName, string expectedLocator, string expectedName, string expectedSmartLocator)
  {
      HeaderSection.CheckInitializedElement(HeaderSection.GetType().GetField(htmlElementToCheckName).GetValue(HeaderSection) as UIElement, expectedLocator, expectedName, expectedSmartLocator);
  }

  [TestCaseSource(nameof(JdiSearchSectionCases))]
  public void CustomJdiSearchSectionTest(string htmlElementToCheckName, string expectedLocator, string expectedName, string expectedSmartLocator)
  {
      JdiSearchSection.CheckInitializedElement(JdiSearchSection.GetType().GetField(htmlElementToCheckName).GetValue(JdiSearchSection) as UIElement, expectedLocator, expectedName, expectedSmartLocator);
  }

  [Test]
  public void CustomSummarySectionTest()
  {
      TestSite.MetalsColorsPage.Open();
      SummarySection.CheckInitializedElement(SummarySection.Calculate, "By.Id: calculate-button", "Calculate", null);
  }

  public static object[] ContactSectionCases =
  {
      new object[] { nameof(ContactSection.DescriptionField), "By.CssSelector: textarea#description", "Description", null },
      new object[] { nameof(ContactSection.FirstRoller), "By.XPath: .//a[@class='ui-slider-handle ui-state-default ui-corner-all' and position()=1]", "FirstRoller", null },
      new object[] { nameof(ContactSection.LastNameField), "By.CssSelector: input#last-name", "Last Name", null },
      new object[] { nameof(ContactSection.NameField), "By.CssSelector: input#name", "First Name", null },
      new object[] { nameof(ContactSection.SecondRoller), "By.XPath: .//a[@class='ui-slider-handle ui-state-default ui-corner-all' and position()=2]", "SecondRoller", null },
      new object[] { nameof(ContactSection.SubmitButton), "By.XPath: //button[@type='submit' and contains(., 'Submit')]", "SubmitButton", null },
  };

  public static object[] HeaderSectionCases =
  {
      new object[] { nameof(HeaderSection.Image), "By.XPath: //img[@src=\"label/Logo_Epam_Color.svg\"]", "Image", null },
      new object[] { nameof(HeaderSection.Menu), "By.CssSelector: ul.uui-navigation.nav", "Menu", null },
      new object[] { nameof(HeaderSection.UserIcon), "By.CssSelector: #user-icon", "UserIcon", null },
      new object[] { nameof(HeaderSection.Search), "By.CssSelector: input#last-name", "Search", "By.Id: search" }
  };

  public static object[] JdiSearchSectionCases =
  {
      new object[] { nameof(JdiSearchSection.SearchButton), "By.CssSelector: .search>.icon-search", "SearchButton", null },
      new object[] { nameof(JdiSearchSection.SearchButtonActive), "By.CssSelector: .icon-search.active", "SearchButtonActive", null },
      new object[] { nameof(JdiSearchSection.SearchInput), "By.CssSelector: .search-field input", "SearchInput", null },
  };
```

And here are methods available in Java:

|Method | Description | Return Type
--- | --- | ---
**shouldBe()** | Returns object for work with assertions | IsAssert
**waitFor()** | Returns object for work with assertions | IsAssert
**has()** | Returns object for work with assertions | IsAssert
**is()** | Returns object for work with assertions | IsAssert
**assertThat()** | Returns object for work with assertions | IsAssert

[Java test examples](https://github.com/jdi-testing/jdi-light/blob/master/jdi-light-html-tests/src/test/java/io/github/epam/html/tests/elements/composite/section)  
[Test examples in C#](https://github.com/jdi-testing/jdi-light-csharp/blob/master/JDI.Light/JDI.Light.Tests/Tests/Composite/SectionTests.cs)

### Form

```java 
public class LoginForm extends Form<User> {
    @UI("#name") TextField name;
    @UI("#password") TextField password;
    @UI("#login-button") Button loginButton;
}

public class User extends DataClass<User> {
    public String name, password;
}

on JDISite.java >> public static LoginForm loginForm;

In tests:

@Test
public void loginWithUserTest() {
    shouldBeLoggedOut();
    loginForm.shouldBeOpened();
    loginForm.login(DEFAULT_USER);
    homePage.checkOpened();
}
    
@Test
public void fillContactFormTest() {
    shouldContactPageBeOpenedAndRefreshed();
    main.contactForm.fill(DEFAULT_CONTACT);
    main.contactForm.check(DEFAULT_CONTACT);
}   
```

**Form** – logical part of a web page that represents HTML form. Form consists of elements based on SetValue interface and buttons with function “submit”.

Form provides functionality to fill, submit and verify/check the form.  

![Form](../images/html/form_html.png)

Form is located in the following classes:
 
  - __Java__: _com.epam.jdi.light.elements.composite.Form_
  - __C#__: _JDI.Light.Elements.Composite.Form_
  
Form is parameterized by an entity that corresponds to the form. For example, a login form can be parameterized by a user entity. Entity should extend DataClass class parameterized by the entity itself. The names of the entity fields should be exactly the same as the names of the form fields. All fields of the entity managed by form should be String.

JDI Light Java supports three types of forms:

**JDI Light Forms** - typical Forms in JDI with **typified elements**, **@UI** annotations, extending from Form and without **fill/check** methods.

```java 
public class LoginFormSmart extends Form<User> {
    TextField name, password;
    Button loginButton;
}

on JDISite.java >> public static LoginFormSmart loginFormSmart;
```

**Smart JDI Forms** - forms that exploit Smart locators functionality of JDI. In Smart Forms there is no need to explicitly define locators for form elements, if such locators can be obtained implicitly from the field names using Smart locators functionality.
[See more details and exampels for Smart locators in documentation](https://jdi-docs.github.io/jdi-light/?java#smart-locators)

```java
on JDISite.java >> public static Form<User> lightLoginForm;
```

**Light Forms** - if a Form consists of only TextFields and Buttons there is no need to define Form UI Object. Such form can be added directly to the related page or to the root Site class.

```java 
@Test
public void onlyMandatoryOptionTest() {
    shouldContactPageBeOpenedAndRefreshed();
    main.contactFormCustom.onlyMandatory().fill(DEFAULT_CONTACT);
    main.contactFormCustom.onlyMandatory().check(DEFAULT_CONTACT);
}
```

In Java, Form has a filter property that defines which form elements will be filled/submited or verified/checked. Filter can be set to either **ALL**, **MANDATORY** or **OPTIONAL**. Based on this property, fill/submit and verify/check functions are applied to either all form elements or only mandatory (only optional) form elements. Mandatory form fields should be marked with **@Mandatory** annotation. Optional form fields are the ones without **@Mandatory** annotation. **ALL** is default Form option. To set form filters as **MANDATORY** or **OPTIONAL**, **onlyMandatory()** and **onlyOptional()** methods should be used. They set the corresponding form filter option for a duration of a single action (all form action methods set the form filter option back to **ALL**).

```java 
@BeforeSuite(alwaysRun = true)
public static void setUp() {
    logger.setLogLevel(INFO);
    initElements(StaticSite.class);
    Form.FILL_ACTION = (field, element, parent, setValue) -> {
         if (isInterface(field, TextField.class))
           	((TextField)element).higlight();
         ((SetValue) element).setValue(setValue);
    };
    homePage.open();
    logger.toLog("Run Tests");
}
```

In Java, Form has a **FILL_ACTION** and **GET_ACTION** lambdas that define how the Form should be filled and verified. The default behavior defined in the Form class simply exploits **setValue(String value)** method of the SetValue interface and **getValue()** method of the HasValue interface. However these lambdas are redefined in HtmlSettings class in order to customise behavior for a "non-text" form elements such as Checkboxes (the behavior of the custom elements is defined by **@FillValue** and **@VerifyValue** annotations). **FILL_ACTION** and **GET_ACTION** lambdas can also be further modified in order to customise the Form behavior, but it is important to take into account that behavior, defined in the HtmlSettings might be lost. It is customary to reassign these lambdas before all the tests are run, for example in the TestNG's **@beforeSuite** method.

```java 
public class LoginForm extends Form<User> {
    TextField name, password;
    Button loginButton;

	@Override
	public void fillAction(Field field, Object element, Object parent, String setValue) {
		if (isInterface(field, TextField.class))
			((TextField)element).higlight();
		super.fillAction(field, element, parent, setValue);
	}
}
```

In Java, if fill/submit and verify/check methods need to be redefined for a specific form, it is possible to override **fillAction()** and **getAction()** for such form.

Available methods in Java JDI Light:

|Method | Description | Return Type
--- | --- | ---
**fillAction(Field field, Object element, Object parent, String setValue)** | Defines the specifics of how the form elements will be filled | void
**getAction(Field field, Object element, Object parent)** | Defines the specifics of how the form elements will be obtained for verification and checks | String
**onlyMandatory()** | Sets form filter option to **MANDATORY** meaning that only mandatory form elements are filled/submitted or verified/checked for a duration of a single form action | void
**onlyOptional()** | Sets form filter option to **OPTIONAL** meaning that only optional form elements are filled/submitted or verified/checked for a duration of a single form action | void
**fill(T entity)** | Fills all setable elements on the form that can be matched with fields in input entity | void
**submit()** | Sends the form by clicking on Button "submit" or "submitButton" | void
**submit(String text)** | Fills first setable form field with value and clicks on Button "submit" or "submitButton"  | void
**submit(T entity)** | Fills all setable elements and clicks on Button "submit" or "submitButton"  | void
**submit(String text, String buttonName)** | Fills first setable field with value and clicks on Button “buttonName” or "buttonNamebutton"| void
**submit(T entity, String buttonName)** | Fills all setable elements and clicks on Button “buttonName” or "buttonNamebutton" | void
**pressButton(String buttonName)** | Clicks on Button “buttonName” or "buttonNamebutton". Allows different buttons to send one form e.g. save/publish/cancel/search/update/... | void
**verify(T entity)** | Verifies that form was filled correctly. If not returns list of keys where verification fails | List<String>
**check(T entity)** | Verifies that form was filled correctly. If not throws exception | void
**login()** | Clicks on Button "login" or "loginButton"| void
**login(T entity)** | Fills all setable elements and clicks on Button “login” or ”loginButton” | void
**loginAs(T entity)** | Fills all setable elements and clicks on Button “login” or ”loginButton” | void
**send()** | Sends the form by clicking on Button “send” or "sendButton" | void
**send(T entity)** | Fills all setable elements and clicks on Button “send” or ”sendButton” | void
**add(T entity)** | Fills all setable elements and clicks on Button “add” or ”addButton” | void
**publish(T entity)** | Fills all setable elements and clicks on Button “publish” or ”publishButton” | void
**save(T entity)** | Fills all setable elements and clicks on Button “save” or ”saveButton” | void
**update(T entity)** | Fills all setable elements and clicks on Button “update” or ”updateButton” | void
**cancel(T entity)** | Fills all setable elements and clicks on Button “cancel” or ”cancelButton” | void
**close(T entity)** | Fills all setable elements and clicks on Button “close” or ”closeButton” | void
**back(T entity)** | Fills all setable elements and clicks on Button “back” or ”backButton” | void
**select(T entity)** | Fills all setable elements and clicks on Button “select” or ”selectButton” | void
**next(T entity)** | Fills all setable elements and clicks on Button “next” or ”nextButton” | void
**search(T entity)** | Fills all setable elements and clicks on Button “search” or ”searchButton” | void

[Java test examples](https://github.com/jdi-testing/jdi-light/blob/master/jdi-light-html-tests/src/test/java/io/github/epam/html/tests/elements/composite/FormTests.java)

[C# test examples](https://github.com/jdi-testing/jdi-light-csharp/blob/master/JDI.Light/JDI.Light.Tests/Tests/Composite/FormTests.cs)

### WebPage

**WebPage** is provided by JDI Light in:
 
  - __Java__: _com.epam.jdi.light.elements.composite_

**WebPage** - is a parent Java class for all JDI Page Object classes. WebPage class extending DriverBase class, implementing PageObject interface and containing a scope of common used methods:

|Method | Description | Return Type
--- | --- | ---
**asForm()**|Returning new Form parameterized with local Name|Form<T>
**getCurrentPage()**|Returning the name of current Page|String
**setCurrentPage(WebPage page)**|Instantiating the current Page with Name|void
**WebPage()**|Default constructor for WebPage class|WebPage
**WebPage(String url)**|Parameterizing with URL constructor for WebPage class|void
**openUrl(String url)**|Opening WebPage with URL|void
**getUrl()**|Returning URL of Page|String
**getTitle()**|Returning Title of Page|String
**updatePageData(Url urlAnnotation, Title titleAnnotation)**|Setting Page URL and Title|void
**url()**|Returning new StringCheckType object wit checked URL|StringCheckType
**title()**|Returning new StringCheckType object wit checked Title|StringCheckType
**open(String url)**|Opens url specified for page|void
**open(Object... params)**|Opens url specified for page with parameters|void
**checkOpened()**|Checking that page opened|void
**isOpened()**|Checking that page opened|boolean
**shouldBeOpened()**|Checking that page opened|void
**shouldBeOpened(Object... params)**|Check that page opened with parameters|void
**openedPage(String url)**|Check that page opened|void
**refresh()**|Reloading current page|void
**reload()**|same as **refresh()**|void
**back()**|Go back to previous page|void
**forward()**|Go forward to next page|void
**zoom(double factor)**|Zooming current page|void
**getHtml()**|Getting HTML of current page|String
**scroll(int x, int y)**|Scrolling to designated position|void
**scrollToTop()**|Scrolling to top|void
**scrollToBottom()**|Scrolling to bottom|void
**scrollDown(int value)**|Scrolling dowd to designated position|void
**scrollUp(int value)**|Scrolling up to designated position|void
**scrollRight(int value)**|Scrolling right to designated position|void
**scrollLeft(int value)**|Scrolling left to designated position|void
**addPage(WebPage page)**|Adding selected page to Map of pages|void
**getPage(String value)**|Getting page from Map by value|T_extends_WebPage
**toString()**|Overriding method of Object class|String
  

more than that, it has nested Class **StringCheckType** with such methods:

|Method | Description | Return Type
--- | --- | ---
**StringCheckType(Supplier<String> actual, String equals, String what)**|parametrized constructor|StringCheckType
**check()**|Check that current page url/title equals to expected url/title|boolean
**match()**|Check that current page url/title matches to expected url/title-matcher|boolean
**contains()**|Check that current page url/title contains expected url/title-matcher|boolean

```java 
public class MainPage extends WebPage{}
MainPage mainPage = new MainPage;
mainPage.setCurrentPage(WebPage page);
mainPage.getCurrentPage();
mainPage.getUrl()
mainPage.getTitle()
mainPage.checkOpened()
mainPage.toString()
mainPage.StringCheckType().check()

@Test
public void verifyURL() {
    mainPage.setCurrentPage(mainPage);
    assertEquals(mainPage.getUrl(), "www.mainpage.ru");
}
@Test
public void verifyTitle() {
    mainPage.setCurrentPage(mainPage);
    assertEquals(mainPage.getTitle(), "Main page");
}
```

## JDI Light BDD Steps

### Label 

```
When  Click on "JDI Title"
When  Double Click on "JDI Title"
When  Right Click on "JDI Title"
When  Higlight "JDI Title"
When  Show "JDI Title"
When  Set "JDI Title" attribute "status" with value "marked"
When  Make Screenshot for "JDI Title"
```
**When** Click on "\<ELEMENT NAME\>" <br>
**When** Double Click on "\<ELEMENT NAME\>" <br>
**When** Right Click on "\<ELEMENT NAME\>" <br>
**When** Higlight "\<ELEMENT NAME\>" <br>
**When** Show "\<ELEMENT NAME\>" <br>
**When** Set "\<ELEMENT NAME\>" attribute "\<ATTRIBUTE NAME\>" with value "\<ATTRIBUTE VALUE\>" <br>
**When** Make Screenshot for "\<ELEMENT NAME\>"<br>

```
Then  Assert that "JDI Title" text equal to "JDI TESTING PLATFORM"
Then  Assert that "JDI Title" text contains "JDI"
Then  Assert that "JDI Title" text match to regexp ".* TESTING .*"
Then  Assert that "JDI Title" is enabled
Then  Assert that "JDI Title" is disabled
Then  Assert that "JDI Title" is displayed
Then  Assert that "JDI Title" disappear
Then  Assert that "JDI Title" hidden
Then  Assert that "JDI Title" not appear
Then  Assert that "JDI Title" not appear during "5" seconds
```
**Then** Assert that "\<ELEMENT NAME\>" text equal to "\<TEXT\>" <br>
**Then** Assert that "\<ELEMENT NAME\>" text contains "\<TEXT PART\>" <br>
**Then** Assert that "\<ELEMENT NAME\>" text match to regexp "\<REGULAR EXPRESSION\>" <br>
**Then** Assert that "\<ELEMENT NAME\>" is enabled <br>
**Then** Assert that "\<ELEMENT NAME\>" is disabled <br>
**Then** Assert that "\<ELEMENT NAME\>" is displayed <br>
**Then** Assert that "\<ELEMENT NAME\>" disappear <br>
**Then** Assert that "\<ELEMENT NAME\>" hidden <br>
**Then** Assert that "\<ELEMENT NAME\>" not appear <br>
**Then** Assert that "\<ELEMENT NAME\>" not appear during "\<SECONDS\>" seconds <br>

### Image
Samples of steps: <br>
_**attributes checks:**_<br>
**Then** image _"\<IMAGE NAME\>"_ src equals to _"\<SOURCE VALUE\>"_<br>
**Then** image _"\<IMAGE NAME\>"_ scr contains _"\<SOURCE VALUE\>"_<br>
**Then** image _"\<IMAGE NAME\>"_ height is equal to _"\<HEIGHT VALUE\>_"<br>
**Then** image _"\<IMAGE NAME\>"_ width is equal to _"\<WIDTH VALUE\>"_<br>
**Then** image _"\<IMAGE NAME\>"_ attribute is equal to _"\<ALT VALUE\>_"<br>

````
Scenario: Check image source
  Given I should be login
  And I open "Html5 Page"
  Then image "Jdi Logo" src is equals to "https://jdi-testing.github.io/jdi-light/images/jdi-logo.jpg"
````

### Alerts
_steps:_<br>
**Then** alert text is equal to _"\<SOURCE VALUE\>"_<br>
**Then** accept Alert<br>

````
Scenario: Click at image and accept Alert
  Given I open "Html5 Page"
  When click at "Jdi Logo"
  Then check Alert text is "JDI Logo"
  And accept Alert
  ````

### File Input

```
Examples for actions:
When I upload file "/src/test/resources/general.xml" by "Avatar" file input element
When I try to upload file "/jdi-light-bdd-tests/src/test/resources/general.xml" by "Disabled File Input" file input element
```
Actions:<br>
**When** I upload file "\<PATH TO FILE\>" by "Avatar" file input element<br>
**When** I try to upload file "\<PATH TO FILE\>" by "Disabled File Input" file input element<br>

```
Examples for validations:
Then "Avatar" file input element label equals to "Profile picture:"
Then "Avatar" file input element label contains "picture"
Then "Avatar" file input element text equals to "C:\fakepath\general.xml"
Then "Avatar" file input element text contains "general.xml"
Then "Avatar" file input element value equals to "C:\fakepath\general.xml"
Then "Avatar" file input element value contains "general.xml"
```
Validations:<br>
**Then** "Avatar" file input element label equals to "\<TEXT\>"<br>
**Then** "Avatar" file input element label contains "\<TEXT PART\>"<br>
**Then** "Avatar" file input element text equals to "\<PATH TO FILE\>"<br>
**Then** "Avatar" file input element text contains "\<PART OF PATH TO FILE\>"<br>
**Then** "Avatar" file input element value equals to "\<PATH TO FILE\>"<br>
**Then** "Avatar" file input element value contains "\<PART OF PATH TO FILE\>"<br>

## UI Objects
TBD

## Smart Locators

```
<input type="text" id="name">
<input type="text" id="last-name">
<button id="submit-button">
```
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

If Smart locator rule is id:
    SmartSearchLocator = "#{0}";
    
and convertation rule is hyphen to csharp name:
    SmartSearchName(string name) => StringExtensions.SplitHyphen(name);
    
So you can write:

public class UserCard : Form<User>
{
    TextField Name; 
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

If Smart locator rule is id:
    WebSettings.SMART_SEARCH_LOCATORS = asList("#%s");
    
and convertation rule is hyphen to java name:
    WebSettings.SMART_SEARCH_NAME = StringUtils::splitHyphen;

So you can write:

public class UserCard extends Form<User> {
    TextField name;
    TextField lastName;
    Button submitButton; 
}

```


If you have your developers follow some standard way to mark ui elements or you have an agreement to add special attribute you can even avoid to write locators for elements and make your page objects much more compact.

You can manage how to create locator from field name using.

### Settings interface ISmartLocators contains:
  
- **SmartSearch** - method that invoked if you have element has no locator

- **SmartSearchLocator** - locator that can be used to try to find element

- **SmartSearchName** -  method how to create locator name from filed name (this value will be passed as parameter in SmartSearchLocator)

## JDI Locators

JDI provides various locators for detecting elements using css locators and xpath expressions. JDI Light supports Selenium's @FindBy(s) locators as well as providing custom locators such as Selenium-like **@FindBy(s)**, aliases **@Css**/**@XPath** and custom **@ByText** and **@WithText** locators. 

Furthermore JDI Light introduces **@UI** locator that provides additional features for css support.

Apart from locator annotations JDI Light provides support for smart locators. When using this feature there is no need to explicitly provide locators for elements at all. 

### Selenium-like annotations

|Annotation | Description | Example
--- | --- | ---
**@FindBy** | This JDI Light locator corresponds to Selenium @FindBy locator. It is used to locate element exploiting one of the predefined strategies. JDI Light supports most of the Selenium strategies: **id**, **name**, **className**, **css**, **tagName**, **linkText**, **partialLinkText**, **xpath**. Added strategy is **text**, which allows detecting element(s) with the given text inside its text nodes. The **group** annotation parameter allows to use different **@FindBy** locators for different test groups. | @FindBy(css = "#passport")
**@FindBys** | TBD. The JDI Light annotation should correspond exactly to Selenium @FindBys annotation | @FindBys({@FindBy(css = ".main-form"), @FindBy(css = "#accept-conditions")})
**@FindAll** | TBD. The JDI Light annotation should correspond exactly to Selenium @FindAll annotation | TBD

### JDI Light specific annotations

|Annotation | Description | Example
--- | --- | ---
**@Css("expr")** | This locator is an alias to @FindBy(css = "expr")| @Css(".fa-sign-out")
**@XPath("expr")** | This locator is an alias to @FindBy(xpath = "expr") | @XPath(".//button\[@type='submit'\]")
**@ByText("text")** | This locator allows detecting element(s) with the given text inside its text nodes. It is equivalent to xpath = ".//*/text()\[normalize-space(.) = 'text'\]/parent::\*" | @ByText("Calculate")
**@WithText("text")** | This locator allows detecting element with the given text inside its text nodes. It is equivalent to xpath = ".//*/text()\[contains(normalize-space(.), 'text')\]/parent::\*" | @WithText("Calculat")
**@UI("expr")** | This locator can take either css locator or xpath expression as an argument and locate element accordingly. This locator provides additional features as described below. Additionally, the **group** annotation parameter allows to use different **@UI** locators for different test groups. | @UI("#users-table")
**@UI("\['text'\]")** | Such notation allows to enrich css locators to detect element(s) with given text inside its text nodes. It is equivalent to xpath = ".//\*/text()\[normalize-space(.) = 'text'\]/parent::\*" | @UI(".user\['Roman'\]") or @UI("\['Accept'\] input") 
**@UI("\[\*'text'\]")** | Such notation allows to enrich css locators to detect element(s) which contain(s) given text inside its text nodes. It is equivalent to xpath = ".//\*/text()\[contains(normalize-space(.), 'text')\]/parent::\*" | @UI(".user\[\*'Roma'\]") or @UI("\[\*'Accept'\] input")
**@UI("'expr\[n\]")** | Such notation allows to enrich css locators to choose an element at a specific position. It is equivalent to xpath = ".//xpath-expr\[n\]" | @UI("\[type=checkbox\]\[1\]")
**@UI("expr<")** | Such notation allows to enrich css locators by allowing to move up in the DOM to the parent of the element. E.g. \[’text’\]**<**\[type=checkbox\] is the same as //\*\[text()=’text’\]/..//*\[@type=‘checkbox’\] | @UI("\[’Ice Cream’\]<\[type=checkbox\]")
**@JDropdown** | This locator help to locate dropdown elements and <a href='https://jdi-docs.github.io/jdi-light/?java#dropdown' target="_blank">provide additional features</a> | @JDropdown(root = "div\[ui=combobox\]", value = "input", list = "li", expand = ".caret")


provide additional features
### Smart locators

```
<input type="text" id="name">
<input type="text" id="last-name">
<input type="text" id="passport-code">
<input type="text" id="passport-number">
<button id="submit-button">
```
```java 
public class UserCard extends Form<User> {
    @Css("#name") TextField name;
    @Css("#last-name") TextField lastName;
    @Css("#passport-code") TextField passportCode;
    @Css("#passport-number") TextField passportNumber;   
    @Css("#submit-button") Button submitButton; 
}
//If Smart locator rule is id
WebSettings.SMART_SEARCH_LOCATORS = asList("#%s");
//and convertation rule is hyphen to java name
WebSettings.SMART_SEARCH_NAME = StringUtils::splitHyphen;
//So you can write
public class UserCard extends Form<User> {
    TextField name;
    TextField lastName;
    TextField passportCode
    TextField passportNumber;  
    Button submitButton; 
}
//or just write all TextFields in one line
public class UserCard extends Form<User> {
    TextField name, lastName, passportCode, passportNumber;  
    Button submitButton; 
}
```

If you have your developers follow some standard way to mark ui elements or you have an agreement to add special attribute you can even avoid to write locators for elements and make your page objects much more compact.

You can manage how to create locator from a field name using:

**WebSettings.SMART_SEARCH** - function that is invoked if you have element that has no locator or just setting a list of used locators using

**WebSettings.SMART_SEARCH_LOCATORS** - list of locators that can be used to try to find element

**WebSettings.SMART_SEARCH_NAME** - function how to create locator name from filed name (this value will be passed as %s parameter in SMART_SEARCH_LOCATORS)

## Windows/Tabs manager
```java 
//example 1
homePage.shouldBeOpened();
githubLink.click();
System.out.println("New window is opened: " + newWindowIsOpened());
System.out.println("Windows count: " + windowsCount());
originalWindow(); // open original (first) window
switchToWindow(2); // open second window
assertEquals(repoDescription.getText(), DESCRIPTION_TEXT);

//example 2
homePage.shouldBeOpened();
openNewTab();
switchToWindow(2);
contactFormPage.open();
```
JDI has good support for managing opened windows and tabs of the browser. It can help to create/switch/close windows/tabs in the browser. Let's look at available methods in Java:

|Method | Description | Return Type
--- | --- | ---
**getWindows()** | Return list of all windows/tabs | Set<String>
**newWindowIsOpened()** | Check the new window is opened | boolean
**setWindowName(String value)** | Set readable name for current opened windows | void
**windowsCount()** | Get count of windows | int
**switchToNewWindow()** | Switch to the new window | void
**openNewTab()** | Open a new tab | void
**originalWindow()** | Switch to original window | void
**switchToWindow(int number)** | Switch to windows with a number. _switchToWindow(2) means switch to the second window_ | void
**switchToWindow(String value)** | Switch to windows with a name. For setup name for the current window, we should use the **setWindowsName()** method | void
**closeWindow()** | Close current window | void
**closeWindow(String value)** | Close window with a specific name. | void

## Alerts
```java 
alertButton.click();
acceptAlert();
```
```csharp 
AlertButton.Click();
GetAlert().AcceptAlert();
```
```java 
alertButton.click();
dismissAlert();
```
```csharp 
AlertButton.Click();
GetAlert().DismissAlert();
```
**Alert** –  a window with a message that displays on the screen and pauses the execution of the script until the user performs an action

<aside class="notice">
Note that you can make static import in order to simplify code Alerts.acceptAlert() > acceptAlert()
</aside>

Handle Window alerts/confirm/prompt dialogs desribed on <a href='https://developer.mozilla.org/en-US/docs/Web/API/Window' target="_blank">MDN</a>

alert('Alert')

![Alert](../images/alert.png)

```java 
alertButton.click();
String text = getAlertText();
assertEquals(text, "Alert Button");
acceptAlert();
```
```csharp 
AlertButton.Click();
String text = GetAlert().GetAlertText()
GetAlert().AcceptAlert();
```
```java 
alertButton.click();
validateAlert(is("Red button"));
validateAlert(equalToIgnoringCase("red button"));
validateAlert(containsString("Red"));
```
```csharp 
TBD ValidateAlert
```

confirm()

![Confirmation dialog](../images/confirm.png)

```java 
alertButton.click();
inputAndAcceptAlert("Some Text");
```
```csharp 
AlertButton.Click();
GetAlert().InputAndAcceptAlert("Some text");
```

prompt('Alert', 'Default value')

![Prompt dialog](../images/prompt.png)

Availiable methods in Java

|Method | Description | Return Type
--- | --- | ---
**acceptAlert()** | Accept alert | void
**dismissAlert()** | Dismiss alert | void
**getAlertText()** | Get alert text | String
**validateAlert(Matcher<String> text)** | Validate alert by matching passed value with alert text | void
**inputAndAcceptAlert(String text)** | Input the specified text in the alert and accept it | void

## Logs
```java
//setup loglevel before running a test (for example in TestInit)
logger.setLogLevel(STEP);

@Test
public void loginTest() {
    homePage.open();
    userIcon.click();
    loginForm.loginAs(DEFAULT_USER);
    homePage.checkOpened();
}
//results in the log
[22:17.102  STEP] : Open 'Home Page'(url=>https://jdi-testing.github.io/jdi-light/index.html)
[22:23.617  STEP] : Click on 'User Icon'
[22:23.727  STEP] : Login as User(userName:epam; password:1234)
[22:24.516  STEP] : Check that 'Home Page' is opened (url CONTAINS '/index.html'; title EQUALS 'Home Page')

```
JDI uses log4j library, but provide more levels of logging. (require log4j.xml / log2j2.xml)
**logger.setLogLevel(STEP);**
Level _STEP_ can show business-related information in the console output and the same log will be in the file (target/.logs/<logName>.log)

|LogLevel | Description 
--- | --- 
**OFF(0)** | No logging
**FATAL(100)** | Unexpected errors
**ERROR(200)** | Critical errors
**WARNING(300)** | Errors due to wrong params
**STEP(350)** | Business related info (JDI related loglevel)
**INFO(400)** | Actions Info
**DEBUG(500)** | Debug info (do not use for production stage)
**TRACE(600)** | Trace info (do not use for production stage)
**ALL(MAX_VALUE)** | All log messages (do not use for production stage)


## Reports
### Allure
TBD

### Report Portal
TBD

## JDI Settings
- **driver** -  we can set up where we would like to run our tests. Some typical options: chrome, firefox, ie... or we can just place it with ${driver} and read the exact driver name from command line
- **drivers.version** - by default JDI Light will download the latest version of drive for us but if we need a specific version we can put it here (in this case the framework will find and download exactly this version)
- **timeout.wait.element** – timeout in seconds to wait for an element on the opened page. Default 10 seconds.
- **timeout.wait.page** - JDI Light automatically define that new page opened and in this case will use this timeout (usually it is more than for element). By default 30 seconds.
- **domain** – web application root URL (used if we work with one application in tests). Can be also read from the command line like ${domain}
- **page.load.strategy** - like in <a href="https://seleniumhq.github.io/selenium/docs/api/javascript/module/selenium-webdriver/lib/capabilities_exports_PageLoadStrategy.html" target="_blank">Selenium strategies</a> to load the page. Options: normal, eager, none
- **browser.size** - the size of the tested browser. By default, JDI Light will maximize browser, but we can set exact values.

## SoftAsserts

```java 
    @Test
    public void buttonSoftAssertTest() {
        assertSoft();
        try {
            redButton.assertThat().hidden().displayed()
                .disabled().enabled()
                .disappear().cssClass(is("uui-button red"))
                .text(is("Big Red *** Button-Input"))
                .text(containsString("Red Button"))
                .attr("type", is("button"))
                .tag(is("input"))

                .assertResults();
            Assert.fail("Test should throw asserts");
        } catch (Throwable tr) {
            assertThat(tr.getMessage(), is("[java.lang.AssertionError: \n" +
                "Expected: is \"hidden\"\n" +
                "     but: was \"displayed\", java.lang.AssertionError: \n" +
                "Expected: is \"disabled\"\n" +
                "     but: was \"enabled\", java.lang.AssertionError: \n" +
                "Expected: is \"disappear\"\n" +
                "     but: was \"displayed\", java.lang.AssertionError: \n" +
                "Expected: is \"Big Red *** Button-Input\"\n" +
                "     but: was \"Big Red Button-Input\"]"));
        }
    }
    @Test
    public void multipleValidationsTest() {
        assertSoft();
        try {
            redButton.is().hidden().displayed().disabled().enabled();
            jdiLogo.is().alt(is("Jdi Logo 777"))
                .src(containsString("jdi-logo.jpg777"))
                .height(is(100))
                .width(is(1000));

            SoftAssert.assertResults();
            Assert.fail("Test should throw asserts");
        } catch (Throwable tr) {
            assertThat(tr.getMessage(), is("[java.lang.AssertionError: \n" +
                "Expected: is \"hidden\"\n" +
                "     but: was \"displayed\", java.lang.AssertionError: \n" +
                "Expected: is \"disabled\"\n" +
                "     but: was \"enabled\", java.lang.AssertionError: \n" +
                "Expected: is \"Jdi Logo 777\"\n" +
                "     but: was \"Jdi Logo 2\", java.lang.AssertionError: \n" +
                "Expected: a string containing \"jdi-logo.jpg777\"\n" +
                "     but: was \"https://jdi-testing.github.io/jdi-light/images/jdi-logo.jpg\", java.lang.AssertionError: \n" +
                "Expected: is <1000>\n" +
                "     but: was <101>]"));
        }
    }
```

**Soft Assert** - assert that collects errors during test is running. They don't throw an exception when an assert fails but save them. 

Here is the list of available methods in SoftAssert class:

|Method | Description | Return Type
--- | --- | ---
**setAssertType(String type)** |Set the type of asserts | void
**assertSoft()** |Set the soft type of asserts | void
**assertStrict()** |Set the strict type of asserts | void
**assertResults()** |Output results of asserts | void
**clearResults()** |Reset results of asserts | void

**Settings:**

- **test.properties** file - to choose type of assertions, you need to update **assert.type** property - select soft or strict type (#assert.type=soft | strict)

- to enable or disable SoftAssert in code use **assertSoft()** or **assertStrict()** methods from SoftAssert class

 **Output results** 
 
there are two ways how to use **assertResults()** method:

- As a method in a chain after asserts (example buttonSoftAssertTest)

- As a separate method if you need to check several elements (example multipleValidationsTest)

## Driver Settings
We can change default settings placed in the test.properties file (src/test/resources)

|Property name | Description | Examples
--- | --- | ---
**driver** | Describe what kind of driver we want to use: chrome, firefox, ie… or we can just place it with ${driver} and read the exact driver name from command line or pom file | driver = ${driver}
**drivers.version** | By default, JDI Light will download the latest version of the driver for us, but if we need a specific version we can put it here (in this case the framework will find and download exactly this version) | drivers.version = LATEST<br>drivers.version = PRELATEST<br> driver.version = 2.23
**timeout.wait.element** | Wait for an element on the opened page, by default = 10 seconds | timeout.wait.element = 20
**timeout.wait.page** | JDI Light automatically defines that new page opened and in this case will use this timeout (usually it is more than for element). By default 30 seconds | timeout.wait.page = 40
**domain** | web application root URL (used if we work with one application in tests). Can be also read from the command line like ${domain} | domain = https://jdi-testing.github.io/jdi-light/
**drivers.folder** | Setup folder for drivers | drivers.folder = C:\\Selenium
**screens.folder** | Setup screenshot folder | screens.folder = C:\\Test-screenshot
**element.search.strategy** | Can find only one element on a page (single), many elements on a page (multiple). Also, we can define if we want to search only in visible element or not. Consist of 2 params: visibility (visible can use displayed or any),  and type of search. Options: soft (=any, multiple); strict(=visible, single); or combine from visible/displayed/any/all and single/multiple. _Note: visible=displayed, any=all | element.search.strategy = visible, multiple
**browser.size** | the size . Optionsof the tested browser. By default, JDI Light will maximize browser, but we can set exact values | browser.size = MAXIMIZE<br>browser.size = 1024x762
**page.load.strategy** | Selenium-like strategies to load the page. Options: normal, eager, none | page.load.strategy = normal
**page.check.after.open** | Check the page has been open. Availible option: NONE, NEW_PAGE, EVERY_PAGE | page.check.after.open = NONE
**assert.type** | <a href="https://jdi-docs.github.io/jdi-light/?java#softasserts">Assert type</a>: soft or strict | assert.type = soft
**driver.remote.url** | <a href="https://jdi-docs.github.io/jdi-light/?java#remote-test-runs">Tests can run on remote web servers<a> | driver.remote.url=http://localhost:4444/wd/hub

## Parallel tests run
TBD

## Remote test runs
TBD


