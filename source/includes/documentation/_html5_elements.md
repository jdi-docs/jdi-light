## HTML5 elements
### HTML5 Common elements

#### Label

```java 
   
  //In the next test Label is found from 'name' and 'disabledName' locators:
   
  // @FindBy(css = "#name")
  @UI("#name") 
  public static TextField name;
	
  // @FindBy(css = "#disabled-name")
  @UI("#disabled-name") 
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
 public void labelAssertThatTest() {
     jdiTitle.assertThat().text(is(text));
 }

 @Test
 public void labelClickTest() {
     jdiTitle.click();
     validateAlert(containsString("JDI Title"));
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
**Label** – Elements' caption for a big number of JDI common elements.

![Label](../images/colorpicker.png)

```html 
<label for="test">Description</label>
```

Label's implementation is located in the following classes:

- __Java__: _com.epam.jdi.light.elements.base.BaseUIElement_
- __C#__: _JDI.Light.Elements.Base.UIElement_



Available methods in C# JDI Light:

|Method | Description | Return Type
--- | --- | --- 
**assertThat()** | Assert action | TextAssert
**click()** | Click the button  | void
**getText()** | Get button text | String
**is()** | Assert action | TextAssert
**Label()** | Creates label for element using the element's Id | Label
**LabelText()** | Gets the text of a label | string
<a href="https://github.com/jdi-testing/jdi-light-csharp/blob/master/JDI.Light/JDI.Light.Tests/Tests/Simple/LabelsTests.cs" target="_blank">C# test examples</a>

<a href="https://github.com/jdi-testing/jdi-light/blob/master/jdi-light-html-tests/src/test/java/io/github/epam/html/tests/elements/common/LabelTests.java" target="_blank">Java test examples</a>

[BDD Steps examples](https://jdi-docs.github.io/jdi-light/?java#label-2)


#### Button

```java 
@UI("[value*='Red Button']") // @FindBy(css = "[value*='Red Button']")
public static Button redButton;

@Test
public void buttonTest() {
   redButton.is().text(text);
   redButton.assertThat().displayed()
         .and().text(is(text))
         .core()
         .css("font-size", is("14px"))
         .cssClass("uui-button red")
         .attr("type", "button")
         .tag(is("input"));
}

@Test
public void buttonAssertThatTest() {
   redButton.assertThat().text(is(text));
}

@Test
public void buttonClickTest() {
   redButton.click();
   validateAlert(containsString("Red button"));
   dblClickButton.doubleClick();
   validateAlert(containsString("Double Click"));
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
**Button** – Element that represents a clickable button.

![Button](../images/button.png)

```html 
<button type="button" id="red-button" class="btn btn-danger" onclick="alert('Red button');" 
ondblclick="alert('Double Click');" oncontextmenu="alert('Right Click');">Red button</button>
```

```h
<button type="button" id="red-button" class="btn btn-danger" onclick="alert('Red button');" 
ondblclick="alert('Double Click');" oncontextmenu="alert('Right Click');">Red button</button>


Button is located in the following classes:
 
  - __Java__: _com.epam.jdi.light.ui.html.common.Button_
  - __C#__: _JDI.Light.Elements.Common.Button_


Here is an example with provided HTML code:

<!-- ![Button example](../images/html/button_html.png) -->

```html
<input type="button" value="Big Red Button-Input" 
class="uui-button red" onclick="alert('Red button');">
```

Available methods in Java JDI Light:

|Method | Description | Return Type
--- | --- | ---
**assertThat()** | Assert action | TextAssert
**click()** | Click the button  | void
**getText()** | Get button text | String
**is()** | Assert action | TextAssert

<a href="https://github.com/jdi-testing/jdi-light/blob/master/jdi-light-html-tests/src/test/java/io/github/epam/html/tests/elements/common/ButtonTests.java" target="_blank">Java test examples</a>
<br>
[BDD Steps example](https://jdi-docs.github.io/jdi-light/?java#button-3)

Available methods and properties in C# JDI Light:

|Method/Property | Description | Return Type
--- | --- | ---
**AssertThat** | Assert action | TextAssert
**Click()** | Click the button  | void
**GetText()** | Get button text | string
**Is** | Assert action | TextAssert

<a href="https://github.com/jdi-testing/jdi-light-csharp/blob/master/JDI.Light/JDI.Light.Tests/Tests/Simple/ButtonTests.cs" target="_blank">C# test examples</a>
<br>
[BDD Steps example](https://jdi-docs.github.io/jdi-light/?java#button-3)

#### Checkbox

**Checkbox** – Element allows you to select single value for submission.

![Checkbox](../images/checkbox.png)

Checkbox is located in the following classes:

- __Java__: _com.epam.jdi.light.ui.html.common.Checkbox*_
- __C#__: _JDI.Light.Elements.Common.CheckBox*_


Here is an example with provided HTML code:

<!-- ![Checkbox example](../images/html/checkbox_html.png) -->

```java 
//@FindBy(id = "accept-conditions") 
@UI("#accept-conditions")
public static Checkbox acceptConditions;

@Test
public void checkTest() {
    acceptConditions.check();
    acceptConditions.is().selected();
}

@Test
public void uncheckTest() {
    acceptConditions.uncheck();
    acceptConditions.is().deselected();
}

@Test
public void getLabelTextTest() {
    acceptConditions.label().is().text(labelText);
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

```html
<input type="checkbox" id="accept-conditions" checked="">
<label for="accept-conditions">Accept terms and conditions</label>
```

Available methods in Java JDI Light:

|Methods | Description | Return Type
--- | --- | ---
**assertThat()** | Assert action checkbox | CheckboxAssert
**check(String)**| Set to checked on "true" (case insensitive) or unchecked otherwise | void
**check()**| Set to checked | void
**click()** | Click the checkbox  | void
**is()** | Assert action checkbox | CheckboxAssert
**isSelected()** | Verify value | boolean
**uncheck()**| Set to unchecked | void

Available methods in C# JDI Light:

|Method | Description | Return Type
--- | --- | ---
**AssertThat** | Gets assert for checkbox | CheckBoxAssert
**Check(bool checkEnabled = true)** | Checks a checkbox | void
**Deselected()** | Checks whether a checkbox is deselected | CheckBoxAssert
**Displayed()** | Checks whether a checkbox is displayed | CheckBoxAssert
**Enabled()** | Checks whether a checkbox is enabled | CheckBoxAssert
**Is** | Gets assert for checkbox | CheckBoxAssert
**IsChecked** | Determines whether a checkbox is checked | bool
**Selected()** | Checks whether a checkbox is selected | CheckBoxAssert
**Uncheck(bool checkEnabled = true)** | Unhecks a checkbox | void

<a href="https://github.com/jdi-testing/jdi-light/blob/master/jdi-light-html-tests/src/test/java/io/github/epam/html/tests/elements/common/CheckboxTests.java" target="_blank">Java test examples</a>

<a href="https://github.com/jdi-testing/jdi-light-csharp/blob/master/JDI.Light/JDI.Light.Tests/Tests/Simple/CheckBoxTests.cs" target="_blank">C# test examples</a>

[BDD Steps example](https://jdi-docs.github.io/jdi-light/?java#checkbox-2)

#### ColorPicker

```java 
@UI("#color-picker") // @FindBy(id = "color-picker")
public static ColorPicker colorPicker;

@Test
public void checkColorTest() {
    colorPicker.assertThat().color(COLOR);
    disabledPicker.is().color(DISABLED_COLOR);
}

@Test
public void setColorTest() {
    colorPicker.setColor(SETTING_COLOR);
    colorPicker.is().color(SETTING_COLOR);
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
**ColorPicker** – Elements of this type provide a user interface element that lets a user specify a color, either by using a visual color picker interface or by entering the color into a text field in "#rrggbb" hexadecimal format. Only simple colors (with no alpha channel) are allowed. The values are compatible with CSS.

![ColorPicker](../images/colorpicker.png)

Colorpicker is located in the following classes:

- __Java__: _com.epam.jdi.light.ui.html.common.ColorPicker_


Here is an example with provided HTML code:

<!-- ![ColorPicker](../images/html/colorpicker_html.png) -->

```html
<input type="color" value="#3fd7a6" id="color-picker">
<label for="color-picker">Select a color</label>
```

Here is the list of some available methods in Java:

|Methods | Description | Return Type
--- | --- | ---
**assertThat()** | Assert acton color | ColorAssert
**color()** | Returns color code in  hexadecimal format ("#rrggbb") | String
**is()** | Assert acton color | ColorAssert
**setColor(String)** | Set color from string hex representation ("#rrggbb") | void

<a href="https://github.com/jdi-testing/jdi-light/blob/master/jdi-light-html-tests/src/test/java/io/github/epam/html/tests/elements/common/ColorPickerTests.java" target="_blank">Java test examples</a>
<br>
[BDD Steps example](https://jdi-docs.github.io/jdi-light/?java#colorpicker-2)<br>

Here is the list of some available methods in C#:

|Methods | Description | Return Type
--- | --- | ---
**AssertThat()** | Assert acton color | ColorAssert
**Color()** | Returns color code in  hexadecimal format ("#rrggbb") | string
**Is()** | Assert acton color | ColorAssert
**SetColor(String)** | Set color from string hex representation ("#rrggbb") | void

<a href="https://github.com/jdi-testing/jdi-light-csharp/blob/master/JDI.Light/JDI.Light.Tests/Tests/Simple/ColorPickerTests.cs" target="_blank">Test examples in C#</a>
<br>
[BDD Steps example](https://jdi-docs.github.io/jdi-light/?java#colorpicker-2)<br>

#### DateTimeSelector

**DateTimeSelector** - Is used for Input Type Date and its derivatives and allows users to set the value of date and/or time.

The list of supported elements:

- Input Type Date
- Input Type Week
- Input Type Month
- Input Type Time
- Input Type DateTime-Local

There following classes represent this type of element:

- __C#__: _JDI.Light.Elements.Common.DateTimeSelector_
- __Java__: _com.epam.jdi.light.ui.html.common.DateTimeSelector_

Here is the list of some methods available in C#:

|Method | Description | Return Type
--- | --- | ---
**AssertThat()** | Asserts action of DateTimeSelector | DateTimeSelectorAssert
**GetDateTime()** | Returns the set date or time | DateTime
**Is()** | Asserts action of DateTimeSelector | DateTimeSelectorAssert
**Max()** | Gets attribute with name max | string
**Min()** | Gets attribute with name min | string
**SetDateTime(string/DateTime value)** | Sets a date or time | void
**Value()** | Returns value attribute | string

And here are some of the methods available in Java:

|Method | Description | Return Type
--- | --- | ---
**assertThat()** | Assertion | DateTimeAssert
**is()** | Assertion | DateTimeAssert
**max()** | Gets attribute with name max | String
**min()** | Gets attribute with name min | String
**setDateTime(string value)** | Sets a date or time | void
**value()** | Returns the set date or time | String

[BDD Steps example](https://jdi-docs.github.io/jdi-light/#datetimeselector-2)

__In the following sections there are examples of different implementations of such fields.__

__Input Type Date__

```java 
//@FindBy(css = "#birth-date")
@UI("#birth-date")  
public static DateTimeSelector birthDate;

//@FindBy(id = "party-time")
@UI("#party-time") 
public static DateTimeSelector partyTime;

//@FindBy(css = "#booking-time")
@UI("#booking-date")  
public static DateTimeSelector bookingTime;

@Test
public void setDateTimeTest() {
    partyTime.setDateTime("2017-05-10T00:00");
    partyTime.show();
    partyTime.is().text("2017-05-10T00:00");
    bookingTime.setDateTime("05:00");
    bookingTime.show();
    bookingTime.is().text("05:00");
}

@Test
public void getDateTest() {
    birthDate.is().text("1985-06-18");
}

@Test
public void minMaxTest() {
    assertEquals(partyTime.min(), "2018-05-07T00:00");
    assertEquals(partyTime.max(), "2018-06-14T00:00");
}

@Test
public void labelTest() {
    birthDate.label().assertThat().text(is("Birth date"));
    birthDate.label().is().text(equalToIgnoringCase("birth date"));
    birthDate.assertThat().date(containsString("1985"));
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
**Input Type Date** – A graphical control element that allows user to set value for date.

![InputTypeDate](../images/html/inputTypeDate_html2.png)

```html
<label for="birth-date">Birth date</label>
<input type="date" id="birth-date" value="1985-06-18" min="1970-01-01" max="2030-12-31">
```

<a href="https://github.com/jdi-testing/jdi-light-csharp/blob/master/JDI.Light/JDI.Light.Tests/Tests/Simple/DateTimeTests.cs" target="_blank">Test examples in C#</a>

<a href="https://github.com/jdi-testing/jdi-light/blob/master/jdi-light-html-tests/src/test/java/io/github/epam/html/tests/elements/common/DateTests.java" target="_blank">Test examples in Java</a>

__Input Type Week__

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
**Input Type Week** – A graphical control element that allows user to set values for week and year.

![InputTypeWeek](../images/html/inputTypeWeek_html2.png)

```html
<label for="autumn-week">Autumn</label>
<input type="week" id="autumn-week" value="2018-W40"
 min="2018-W35" max="2018-W48" required="">
```


<a href="https://github.com/jdi-testing/jdi-light-csharp/blob/master/JDI.Light/JDI.Light.Tests/Tests/Simple/DateTimeTests.cs" target="_blank">Test examples in C#</a>

<a href="https://github.com/jdi-testing/jdi-light/blob/master/jdi-light-html-tests/src/test/java/io/github/epam/html/tests/elements/common/WeekTests.java" target="_blank">Test examples in Java</a>


__Input Type Month__

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
**Input Type Month** – a graphical control element that allows user to set values for month and year.

![InputTypeMonth](../images/html/inputTypeMonth_html2.png)

```html
<label for="month-date">Month of Holidays</label>
<input type="month" id="month-date" min="2015-03"
 max="2020-12" value="2018-05">
```

<a href="https://github.com/jdi-testing/jdi-light-csharp/blob/master/JDI.Light/JDI.Light.Tests/Tests/Simple/DateTimeTests.cs" target="_blank">Test examples in C#</a>

<a href="https://github.com/jdi-testing/jdi-light/blob/master/jdi-light-html-tests/src/test/java/io/github/epam/html/tests/elements/common/MonthTests.java" target="_blank">Test examples in Java</a>

__Input Type Time__

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
**Input Type Time** – A graphical control element that allows user to set time.

![InputTypeTime](../images/html/inputTypeTime_html2.png)

```html
<label for="booking-time">Booking Time:</label>
<input type="time" id="booking-time" value="11:00" min="9:00" max="18:00">
```

<a href="https://github.com/jdi-testing/jdi-light-csharp/blob/master/JDI.Light/JDI.Light.Tests/Tests/Simple/DateTimeTests.cs" target="_blank">Test examples in C#</a>

<a href="https://github.com/jdi-testing/jdi-light/blob/master/jdi-light-html-tests/src/test/java/io/github/epam/html/tests/elements/common/TimeTests.java" target="_blank">Test examples in Java</a>

__Input Type DateTime-Local__

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
**Input Type DateTime-Local** – A graphical control element that allows user to set time and date.

![InputTypeDateTime](../images/html/inputDateTimeLocal_html2.png)

```html
<label for="party-time">Date/time:</label>
<input type="datetime-local" id="party-time" value="2018-06-12T19:30" min="2018-05-07T00:00" max="2018-06-14T00:00">
```

<a href="https://github.com/jdi-testing/jdi-light/blob/master/jdi-light-html-tests/src/test/java/io/github/epam/html/tests/elements/common/DateTimeTests.java" target="_blank">Test examples in Java</a>

<a href="https://github.com/jdi-testing/jdi-light-csharp/blob/master/JDI.Light/JDI.Light.Tests/Tests/Simple/DateTimeTests.cs" target="_blank">Test examples in C#</a>


#### FileInput

**FileInput** - A graphical control element that allows user to upload documents to web site.

![FileInput](../images/fileInputAndDownload.png)

FileInput element is located in JDI Light in:

- __Java__: _com.epam.jdi.light.ui.html.common.FileInput_
- __C#__: _JDI.Light.Elements.Composite.FileInput_


Here is an example with HTML code provided:

<!-- ![FileInput example](../images/html/fileinput_html.png) -->

```java 
//@FindBy(id = "avatar")
@UI("#avatar") 
public static FileInput avatar; 

//@FindBy(xpath = "//a[@download]")
@UI("[download]") 
public static Link downloadJdiLogo;

@Test
public void uploadTest() {
    avatar.uploadFile(mergePath(PROJECT_PATH, "/src/test/resources/general.xml"));
    avatar.is().text(containsString("general.xml"));
}

@Test
public void labelTest() {
    avatar.label().is().text(containsString("picture:"));
}

@Test
public void downloadTest() {
    FileAssert.cleanupDownloads();
    FileAssert.downloadJdiLogo.click();
    FileAssert.assertThatFile("jdi-logo.jpg")
            .isDownloaded()
            .hasSize(is(32225L));
    FileAssert.assertThatFile("jdi-logo.jpg").hasSize(greaterThan(100L));
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

```html
<label for="avatar">Profile picture:</label>
<input type="file" id="avatar" accept="image/png, image/jpeg">
<input type="file" accept="image/png, image/jpeg" disabled="">
<a href="/jdi-light/images/jdi-logo.jpg" download="">Download JDI Logo</a>
```

Available method in Java JDI Light:

|Method | Description | Return Type
--- | --- | ---
**assertThat()** | property that returns object for work with assertions | TextAssert
**click()** | click on element | void
**getValue()** | Get file name | String
**is()** | property that returns object for work with assertions | TextAssert
**hover()** | hover on element | void
**label()**| Get label | Label
**setValue(String value)** | set file path to input | void
**text()** | returns text of input field | String
**uploadFile(String path)** | set file path to input | void
**uploadFileRobot(String path, long mSecDelay)** | set file path to input | void

Available method in C# JDI Light:

|Method | Description | Return Type
--- | --- | ---
**CleanupDownloads()** | Cleans the directory | void
**HasSize(Matcher<long> size)** | Checks that a file has a particular size according to the matcher | FileAssert
**IsDownloaded()** |Checks whether a file is downloaded  | FileAssert
**SelectFile(string filepath)** |Select file to upload  | void
**Text(Matcher<string> value)** | Checks whether an occurrence of a text is contained within a text file | FileAssert

<a href="https://github.com/jdi-testing/jdi-light/blob/master/jdi-light-html-tests/src/test/java/io/github/epam/example/common/FileInputExampleTests.java">Test examples in Java</a>

<a href="https://github.com/jdi-testing/jdi-light-csharp/blob/master/JDI.Light/JDI.Light.Tests/Tests/Simple/FileInputTests.cs">Test examples in C#</a>

[BDD Steps example](https://jdi-docs.github.io/jdi-light/?java#fileinput-2)

#### Icon

**Icon** – Is a simple element type that represents icons and graphic images.

![Icon](../images/html/image_html2.png)

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
public IIcon Logo
;

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

```html
<label for="jdi-logo">JDI Logo:</label>
<img src="/jdi-light/images/jdi-logo.jpg" id="jdi-logo" alt="Jdi Logo 2"
     width="101" height="100" onclick="alert('JDI Logo');">
```

<a href="https://github.com/jdi-testing/jdi-light/blob/master/jdi-light-html-tests/src/test/java/io/github/epam/html/tests/elements/common/ImageTests.java" target="_blank">Test examples in Java</a>
<br>

<br><br><br><br><br><br><br><br><br>

Icon is represented by Image class:

[Image](https://jdi-docs.github.io/jdi-light/#image)


Icon in JDI is a descendant of Image. It inherits all Image's methods and serves as its wrapper. Here are Java methods for Icon, inherited from Image interface:

|Method | Description | Return Type
--- | --- | ---
**alt()** |get value of alt attribute | String
**assertThat()** |method for building assertions  | ImageAssert
**click()** | click on the image| void
**height()** |get value of height attribute| String
**is()** | method for building assertions | ImageAssert
**src()** | get value of src attribute | String
**width()** | get value of width attribute| String

Here is a list of available methods in C#:

|Method | Description | Return Type
--- | --- | ---
**Alt** |get value of alt attribute | string
**AssertThat()** |method for building assertions  | ImageAssert
**Click()** | click on the image| void
**Height** |get value of height attribute| string
**Is()** | method for building assertions | ImageAssert
**Src** | get value of src attribute | string
**Width** | get value of width attribute| string

<a href="https://github.com/jdi-testing/jdi-light/blob/master/jdi-light-html-tests/src/test/java/io/github/epam/html/tests/elements/common/ImageTests.java" target="_blank">Test examples in Java</a><br>

<a href="https://github.com/jdi-testing/jdi-light-csharp/blob/master/JDI.Light/JDI.Light.Tests/Tests/Simple/ImagesTests.cs" target="_blank">Test examples in C#</a><br>

[BDD Steps example](https://jdi-docs.github.io/jdi-light/?java#icon-2)

#### Image

**Image** – Is a simple element type that represents graphic images.

![Image](../images/html/image_html2.png)

```java 
@UI("#jdi-logo") 
// same as FindBy(css = "#jdi-logo")
public static Image jdiLogo;

@Test
public void isValidationTest() {
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
```html
<label for="jdi-logo">JDI Logo:</label>
<img src="/jdi-light/images/jdi-logo.jpg" id="jdi-logo" alt="Jdi Logo 2" 
     width="101" height="100" onclick="alert('JDI Logo');">
```

<br><br><br><br><br><br><br><br><br>

Images are represented by the following classes in Java and C#:

- __Java__: _com.epam.jdi.light.ui.html.common.Image_
- __C#__: _JDI.Light.Elements.Common.Image_

Here is a list of available methods in Java:

|Method | Description | Return Type
--- | --- | ---
**alt()** |get value of alt attribute | String
**assertThat()** |method for building assertions  | ImageAssert
**click()** | click on the image| void
**height()** |get value of height attribute| String
**is()** | method for building assertions | ImageAssert
**src()** | get value of src attribute | String
**width()** | get value of width attribute| String

<a href="https://github.com/jdi-testing/jdi-light/blob/master/jdi-light-html-tests/src/test/java/io/github/epam/html/tests/elements/common/ImageTests.java" target="_blank">Test examples in Java</a>

Here is a list of available methods in C#:

|Method | Description | Return Type
--- | --- | ---
**Alt** |get value of alt attribute | string
**AssertThat()** |method for building assertions  | ImageAssert
**Click()** | click on the image| void
**Height** |get value of height attribute| string
**Is()** | method for building assertions | ImageAssert
**Src** | get value of src attribute | string
**Width** | get value of width attribute| string

<a href="https://github.com/jdi-testing/jdi-light-csharp/blob/master/JDI.Light/JDI.Light.Tests/Tests/Simple/ImagesTests.cs" target="_blank">Test examples in C#</a>

#### Link

```java 
//@FindBy(css = "[ui=github-link]") 
@UI("[ui=github-link]") 
public static Link githubLink;

@Test
public void linkTextTest() {
    githubLink.is().text(EXPECTED_TEXT);
    githubLink.is().text(equalTo(EXPECTED_TEXT));
    githubLink.is().text(containsString(PART_OF_EXPECTED_TEXT));
}

@Test
public void linkRefTest() {
    githubLink.is().ref(EXPECTED_URL);
    githubLink.is().ref(equalTo(EXPECTED_URL));
    githubLink.is().ref(containsString(PART_OF_EXPECTED_URL));
    githubLink.is().ref(matchesPattern(EXPECTED_URL_REGEX));
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

**Link** – A graphical control element that allows user to link from one page to other web pages, files, locations within the same page, email addresses, or any other URL.

Link are represented by the following class:

- __Java__: _com.epam.jdi.light.ui.html.common.Link_
- __C#__: _JDI.Light.Elements.Common.Link_


![Link](../images/html/link_html2.png)

```html 
<a ui="github-link" href="https://github.com/jdi-testing" alt="Github JDI Link">Github JDI</a>
```

Here is the list of available methods in Java:

|Method | Description | Return Type
--- | --- | ---
**alt()** |Returns the alternate text | String
**assertThat()** | Returns object for work with assertions | LinkAssert
**click()** |Follow the link | void
**getText()** |Returns the link text  | String
**is()** | Returns object for work with assertions | LinkAssert
**ref()** |Returns the reference  | String
**url()** |Returns the URL  | URL

<a href="https://github.com/jdi-testing/jdi-light/tree/1509---jdi-light-test-examples/jdi-light-html-tests/src/test/java/io/github/epam/example/common/LinkExampleTests.java" target="_blank">Test examples in Java</a><br>
[BDD Steps example](https://jdi-docs.github.io/jdi-light/#link-2)

Here is the list of available methods in C#:

|Method | Description | Return Type
--- | --- | ---
**Alt()** |Returns the alternate text | string
**AssertThat()** | Returns object for work with assertions | LinkAssert
**Click()** |Follow the link | void
**GetText()** |Returns the link text  | string
**Is()** | Returns object for work with assertions | LinkAssert
**Ref()** |Returns the reference  | string
**Url()** |Returns the URL  | string

<a href="https://github.com/jdi-testing/jdi-light-csharp/blob/master/JDI.Light/JDI.Light.Tests/Tests/Simple/LinkTests.cs" target="_blank">Test examples in C#</a>
<br>
[BDD Steps example](https://jdi-docs.github.io/jdi-light/#link-2)

#### Menu

**Menu** - A list of links, which leads to different pages or sections of website.

Menu element is located in JDI Light in:

- __Java__: _com.epam.jdi.light.ui.html. element
  .Menu_
- __C#__: _JDI.Light.Elements.Composite.Menu_

![Menu example](../images/html/menu2.png)

Here is an example with provided HTML code:

<!-- ![Menu example](../images/html/menu.png) -->

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

```html 
<ul class="sidebar-menu">
    <li ui="label" index="1">
        <a href="index.html"> <span>Home</span>  </a>
    </li>           
    <li ui="label" index="2">
        <a href="contacts.html"> <span>Contact form</span> </a> 
     </li>            
    <li class="menu-title" index="3">                
        <a ui="label"> 
            <span>Service</span>
            <div class="fa fa-caret-down arrow"></div>                
        </a>                
        <ul class="sub hide-menu">                    
            <li ui="label" index="1">
                <a href="support.html">
                    <p><span>Support</span></p>
                </a>
            </li>                    
            <li ui="label" index="2"><a href="dates.html"><span>Dates</span></a>
            </li>                    
            <li ui="label" index="3"><a href="complex-table.html"> <span>Complex Table </span></a>
            </li>                    
            <li ui="label" index="4"><a href="simple-table.html"> <span>Simple Table</span></a>
            </li>                    
            <li ui="label" index="5"><a href="search.html"> <span>Search</span> </a>
            </li>                    
            <li ui="label" index="6"><a href="user-table.html"> <span>User Table</span></a>
            </li>                    
            <li ui="label" index="7"><a href="table-pages.html"> <span>Table with pages</span></a>
            </li>                    
            <li ui="label" index="8"><a href="different-elements.html"> <span>Different elements</span> </a>
            </li>                    
            <li ui="label" index="9"><a href="performance.html"><span>Performance</span></a>
            </li>                
        </ul>            
    </li>            
    <li ui="label" index="4"><a href="metals-colors.html">  <span>Metals &amp; Colors</span></a>       
    </li>            
    <li class="menu-title active" index="5">
        <a ui="label">
          <span>Elements packs</span>
          <div class="fa fa-caret-down arrow"></div>                
        </a>                
        <ul class="sub">                    
            <li ui="label" index="1" class="active"><a href="html5.html"><span>HTML 5</span></a></li>                    
            <li ui="label" index="2"><a href="bootstrap.html"><span>Bootstrap</span>  </a></li>					          
            <li ui="label" index="3"><a href="bootstrap_form.html">	<span>Bootstrap form</span></a></li>					          
            <li ui="label" index="4"><a href="react-ant.html"> <span>React Ant</span></a></li>               
         </ul>            
    </li>        
</ul>
```


Available method in Java JDI Light:

|Method | Description | Return Type
--- | --- | ---
**String selected()** | Returns selected menu item | String
**List<String> values()** | Returns selected menu item and subitems | List<String>
**void hoverAndClick(String...)** | Hovers and clicks menu item and subitems | void
**void hoverAndClick(String)** | Hovers and clicks menu item | void
**void select(int...)** | Select menu element by index | void
**void select(int)** | Select menu element and subelements by index | void
**void select(String...)** | Select menu element and subelement | void
**void select(String)** | Select menu element | void
**void select(TEnum...)** | Select menu element and subelement | void
**void select(TEnum)** | Select menu element | void

Available method in C# JDI Light:

|Method | Description | Return Type
--- | --- | ---
**AssertThat** | Get select assert | MenuSelectAssert
**Is** | Get select assert | MenuSelectAssert
**List<string> Values()** | Gets values of all options | List<string>
**string Selected()** | Returns selected menu item | string
**void HoverAndClick(string[])** | Hovers and clicks menu item and subitems | void
**void HoverAndClick(string)** | Hovers and clicks menu item | void
**void Select(string[])** | Select menu element and subelements by string values | void
**void Select(string)** | Select menu element | void
**void Select(int[])** | Select menu element and subelements by index | void
**void Select(int)** | Select menu element and subelements by index | void
**void Select(Enum[])** | Select menu element and subelements by getting values of enum | void
**void Select(Enum)** | Select menu element | void

<a href="https://github.com/jdi-testing/jdi-light/blob/master/jdi-light-html-tests/src/test/java/io/github/epam/html/tests/elements/complex/MenuTests.java" target="_blank">Test examples in Java</a>

<a href="https://github.com/jdi-testing/jdi-light-csharp/blob/master/JDI.Light/JDI.Light.Tests/Tests/Composite/MenuTests.cs" target="_blank">Test examples in C#</a>

[BDD Steps example](https://jdi-docs.github.io/jdi-light/#menu-2)

#### NumberSelector

**NumberSelector** – A graphical control element, that allows the user to let the user enter a number.

NumberSelector are represented by the following class:

- __Java__: _com.epam.jdi.light.ui.html.common.NumberSelector_
- __C#__: _JDI.Light.Elements.Common.NumberSelector_


```java 
    @UI("#height") 
    // equal to @FindBy(css = "#height") 
    public static NumberSelector height;

    @Test
    public void minMaxTest() {
        height.assertThat().min(is(0.3));
        height.assertThat().max(is(2.5));
    }

    @Test
    public void stepTest() {
        height.assertThat().step(is(0.2));
    }

    @Test
    public void placeholderTest() {
        height.is().placeholder("20 cm increments. Range [0.3,2.5]");
    }

    @Test
    public void setNumberTest() {
        height.setNumber("1.4");
        height.is().number(greaterThanOrEqualTo(0.3));
        height.is().number(lessThanOrEqualTo(2.5));
        height.assertThat().number(is(1.4));
    }

    @Test
    public void labelTest() {
        height.label().is().text("Height (metres):");
        height.label().is().text(containsString("Height"));
        height.label().is().text(equalToIgnoringCase("height (metres):"));
    }

    @Test
    public void assertValidationTest() {
        height.assertThat().number(greaterThan(0.0));
        height.assertThat().number(lessThan(3.0));
        height.assertThat().number(is(2.1));
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


![NumberSelector](../images/html/numberSelector_html2.png)

```html
<label for="height">Height (metres):</label>
<input type="number" id="height" min="0.3" max="2.5" step="0.2"
 placeholder="20 cm increments. Range [0.3,2.5]">
```

Here is the list of available methods in Java:

|Method | Description | Return Type
--- | --- | ---
**assertThat()** | Returns object for work with assertions | NumberAssert
**is()** | Returns object for work with assertions | NumberAssert
**max()** |Returns the max value  | String
**min()** |Returns the min value   | String
**value()** |Returns the value  | String
**placeholder()** |Returns the placeholder text  | String
**setNumber(String)** |Sets the value | void
**step()** |Returns the step value | String

Here is the list of available methods in C#:

|Method | Description | Return Type
--- | --- | ---
**AssertThat()** | Returns object for work with assertions | NumberAssert
**Is()** | Returns object for work with assertions | NumberAssert
**Max** |Returns the max value  | double
**Min** |Returns the min value   | double
**Placeholder** |Returns the placeholder text  | String
**SetNumber(double)** |Sets the value | void
**Step** |Returns the step value | double
**Value** |Returns the value  | double

<a href="https://github.com/jdi-testing/jdi-light/blob/master/jdi-light-html-tests/src/test/java/io/github/epam/html/tests/elements/common/NumberSelectorTests.java" target="_blank">Test examples in Java</a>

<a href="https://github.com/jdi-testing/jdi-light-csharp/blob/master/JDI.Light/JDI.Light.Tests/Tests/Common/NumberSelectorTests.cs" target="_blank">Test examples in C#</a>

[BDD Steps example](https://jdi-docs.github.io/jdi-light/?java#numberselector-2)<br>

#### ProgressBar

**Progress Bar** - Element for displaying an indicator showing the completion progress of a task.

![ProgressBar](../images/progressbar.png)

ProgressBar is located in the following classes:

- __Java__: _com.epam.jdi.light.ui.html.common.ProgressBar_
- __C#__: _JDI.Light.Elements.Common.ProgressBar_

```java 
@UI("#progress") // @FindBy(id = "progress")
public static ProgressBar progress;

@Test
public void valueTest() {
    progress.is().volume(70);
    progress.is().volume(greaterThanOrEqualTo(10));
    progress.is().volume(lessThanOrEqualTo(100));
}

@Test
public void maxTest() {
    progress.is().maxVolume(100);
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

<!-- ![ProgressBar example](../images/html/progressbar_html.png) -->

```html
<label for="progress">File progress</label>
<progress id="progress" max="100" value="70"></progress>
```

Available method in Java JDI Light:

|Method | Description | Return Type
--- | --- | ---
**assertThat()** |Various assert actions for Progress bar | ProgressAssert
**is()** |Various assert actions for Progress bar  | ProgressAssert
**max()** |Get progressbar maximum possible value  | String
**value()** |Get current progress value  | String

<a href="https://github.com/jdi-testing/jdi-light/blob/master/jdi-light-html-tests/src/test/java/io/github/epam/html/tests/elements/common/ProgressTests.java" target="_blank">Test examples in Java</a><br>
[BDD Steps example](https://jdi-docs.github.io/jdi-light/?java#progress-bar) <br>


Available method in C# JDI Light:

|Method | Description | Return Type
--- | --- | ---
**AssertThat()** |Various assert actions for Progress bar | ProgressAssert
**Is()** |Various assert actions for Progress bar  | ProgressAssert
**Max()** |Get progressbar maximum possible value  | string
**Value()** |Get current progress value  | string

<a href="https://github.com/jdi-testing/jdi-light-csharp/blob/master/JDI.Light/JDI.Light.Tests/Tests/Simple/ProgressTests.cs" target="_blank">Test examples in C#</a><br>
[BDD Steps example](https://github.com/jdi-testing/jdi-light/blob/master/jdi-light-bdd-tests/src/test/resources/features/ProgressBar.feature)<br>

#### Range

```java 
@UI("#volume")  //@FindBy(id = "volume") 
public static Range volume;

@Test
public void setVolumeTest() {
    volume.setVolume(10);
    volume.assertThat().volume(10);
}

@Test
public void checkStepTest() {
    volume.assertThat().step(5);
    volume.assertThat().step(is(5));
}

@Test
public void checkMaxTest() {
    volume.assertThat().maxVolume(100);
    volume.assertThat().maxVolume(is(100));
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

**Range** - A graphical control element that allows the user to set the value from the range.</br>

![Range](../images/html/range_html2.png)</br>

```html
<label for="volume">Volume</label>
<input type="text" disabled="" id="volume-value"> <br>
    <span>10</span>
    <input type="range" id="volume" min="10" max="100" value="90" step="5"
           class="range" list="volume-list"
           oninput="showVal(this.value)" onchange="showVal(this.value)">
    <span>100</span>
    
    <datalist id="volume-list">
        <option value="0">
        </option>
        <option value="20">
        </option>
        <option value="40">
        </option>
        <option value="60">
        </option>
        <option value="80">
        </option>
        <option value="100">
        </option>
    </datalist> <br> <br>

<input type="range" disabled="">
```

Range is represented by the following class:</br>

- __Java__: _com.epam.jdi.light.ui.html.common.Range_
- __C#__: _JDI.Light.Elements.Common.Range_

Here is a list of available methods in C#:

|Method | Description | Return Type
--- | --- | ---
**AssertThat()** | Returns object for work with assertions | RangeAssert
**GetValue()** | Returns the value | String
**Is()** | Returns object for work with assertions | RangeAssert
**Max()** | Returns the max value| Double
**Min()** | Returns the min value | Double
**SetValue(string value)** | Sets the value | void
**SetValue(double value)** | Sets the value | void
**Step()** | Returns the step value | Double
**Value()** | Returns the value | Double

<a href="https://github.com/jdi-testing/jdi-light-csharp/blob/master/JDI.Light/JDI.Light.Tests/Tests/Simple/RangeTests.cs" target="_blank">Test examples in C#</a></br>
[BDD Steps example](https://jdi-docs.github.io/jdi-light/?java#range-2) <br>

And here are methods available in Java:

|Method | Description | Return Type
--- | --- | ---
**assertThat()** | Returns object for work with assertions | RangeAssert
**getValue()** | Gets the value | String
**is()** | Returns object for work with assertions | RangeAssert
**max()** | Returns the max value | double
**min()** | Returns the min value | double
**setValue(double volume)** | Sets the value | void
**setValue(String volume)** | Sets the value | void
**step()** | Returns the step value | double
**value()** | Returns the value | double

<a href="https://github.com/jdi-testing/jdi-light/blob/master/jdi-light-html-tests/src/test/java/io/github/epam/html/tests/elements/common/RangeTests.java" target="_blank">Test examples in Java</a></br>
[BDD Steps example](https://jdi-docs.github.io/jdi-light/?java#range-2) <br>

#### Text
**Text** - Is a combination of letters and textual symbols. When performing testing, the text is used in most operations: when typing text into the login field, when finding a button with some certain text in it, or when checking if actual text matches expected one.

```java 
@UI("[ui=jdi-text]") //@FindBy(css = "[ui=jdi-text]") 
public static Text jdiText;

@Test
public void textPositiveTest() {
    jdiText.is().text(equalTo(TEXT));
    jdiText.is().text(TEXT);
}

@Test
public void textContainsTest() {        
    jdiText.is().text(containsString(PART_OF_TEXT));
}

@Test
public void textDoesNotContainWordTest() {
    jdiText.is().text(not(NOT_EXPECTED_TEXT));
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

![Text](../images/html/text_html2.png)

```html 
<p ui="jdi-text">Powerful Framework for UI Tests Automation. Suitable for any UI project: 
Web(Html5, Angular, React...), Mobile(Android IOs), Desktop(Win app) etc.</p>
```

Text is represented by the following class:

- __C#__: JDI.Light.Elements.Common.TextElement
- __Java__: com.epam.jdi.light.ui.html.common.Text

Here is a list of available methods in C#:

|Method | Description | Return Type
--- | --- | ---
**AssertThat** | Gets text assert | TextAssert
**Is** | Gets text assert | TextAssert
**GetText()** | returns text| String
**GetValue()** | returns text| String
**WaitFor** | Gets text assert | TextAssert

<a href="https://github.com/jdi-testing/jdi-light-csharp/blob/master/JDI.Light/JDI.Light.Tests/Tests/Simple/TextTests.cs" target="_blank">Test examples in C#</a>

And here are methods available in Java:

|Method | Description | Return Type
--- | --- | ---
**assertThat()** |Various assert actions for Text| TextAssert
**getText()** |Get current value | String
**is()** |Various assert actions for Text| TextAssert

<a href="https://github.com/jdi-testing/jdi-light/tree/1509---jdi-light-test-examples/jdi-light-html-tests/src/test/java/io/github/epam/example/common/TextExampleTests.java" target="_blank">Test examples in Java</a>

[BDD Steps example](https://jdi-docs.github.io/jdi-light/?java#text-2)

#### TextField
```java 
@UI("#name") //@FindBy(css = "#name")
public static TextField name;

@Test
public void setTextTest() {
    name.setText(text);
    name.is().text(text);
    name.is().text(is(text));
    name.is().text(containsString("Field"));
}

@Test
public void sendKeysTest() {
    name.setText(text);
    name.sendKeys("Test");
    name.is().text(text + "Test");
}

@Test
public void clearTest() {
    name.clear();
    name.is().text("");
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
**TextField** – Is a simple element type that allows users to fill in text fields.

![InputTypeTextField](../images/html/textField_html2.png)

```html
<label for="name">Your name:</label>
<input type="text" id="name" placeholder="Input name">
<label for="disabled-name">Surname:</label>
<input type="text" id="disabled-name" placeholder="Iovlev" disabled="">
```

Text fields are represented by the following classes in Java and C#:

- __C#__: _JDI.Light.Elements.Common.TextField_
- __Java__: _com.epam.jdi.light.ui.html.common.TextField_

Here is a list of available methods and properties in C#:

|Method / Property | Description | Return Type
--- | --- | ---
**AssertThat** | property that returns object for work with assertions| TextAssert
**Clear()** | clears the text field | void
**Focus()** | places cursor within the text field | void
**GetText()** | returns text from the text field  | String
**GetValue()** | returns text from the text field| String
**Input(string text)** | sets new text  | void
**Is** | property that returns object for work with assertions| TextAssert
**Placeholder** | returns value of the placeholder attribute | String
**SendKeys(string value)** | adds text to the field | void
**SetText(String value)** | sets new text | void

<a href="https://github.com/jdi-testing/jdi-light-csharp/blob/master/JDI.Light/JDI.Light.Tests/Tests/Common/TextFieldsTests.cs" target="_blank">Test examples in C#</a><br>
[BDD Steps example](https://jdi-docs.github.io/jdi-light/?java#textfield-2)<br>

And here are methods available in Java:

|Method | Description | Return Type
--- | --- | ---
**clear()** | clears the text field | void
**focus()** | places cursor within the text field | void
**getText()** | returns text from the text field  | String
**getValue()** | returns text from the text field| String
**input(String value)** | sets new text | void
**placeholder()** | returns value of the placeholder attribute | String
**sendKeys(CharSequence... value)** | adds text to the field | void
**setText(String value)** | sets new text | void

<a href="https://github.com/jdi-testing/jdi-light/blob/master/jdi-light-html-tests/src/test/java/io/github/epam/html/tests/elements/common/TextFieldTests.java" target="_blank">Test examples in Java</a><br>
[BDD Steps example](https://jdi-docs.github.io/jdi-light/?java#textfield-2)<br>

#### TextArea

**TextArea** – Is a simple element type that allows users to fill in text areas (they may contain a few lines).

![InputTypeTextArea](../images/html/textArea_html2.png)


```java 
@UI("#text-area") 
// same as FindBy(css = "#text-area")
public static TextArea textArea;

String text = "TextArea";

@Test
public void addNewLineTest(){
    textArea.setLines("line1", "line2");
    textArea.addNewLine("line3");
    textArea.assertThat().text(is("line1\nline2\nline3"));
    textArea.clear();
    textArea.assertThat().text(is(""));
}

@Test
public void isValidationTest() {
    textArea.is().enabled();
    textArea.setText(text);
    textArea.is().text(containsString("Area"));
    disabledTextArea.is().disabled();
}

@Test
public void rowsTest() {
    textArea.is().rowsCount(is(3));
    textArea.is().colsCount(is(33));
    textArea.is().minlength(is(10));
    textArea.is().maxlength(is(200));
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
```html
<label for="text-area">Text example:</label>
<textarea id="text-area" rows="3" cols="33" maxlength="200" minlength="10"
          required="" wrap="hard" placeholder="Input huge text">Textarea with sizing
          and wrap attribute (try values of hard, soft, and off to see how it affects wrapping).
          The maximum number of characters is constrained to 200 by the maxlength attribute.
</textarea> <br>
<textarea disabled="" placeholder="Disabled area"></textarea>
```

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

Text areas are represented by the following classes:

- __Java__: <a href='https://github.com/jdi-testing/jdi-light/blob/bootstrap/jdi-light-html/src/main/java/com/epam/jdi/light/ui/html/elements/common/TextArea.java'>TextArea</a>
- __C#__: _JDI.Light.Elements.Common.TextArea_

In JAVA TextArea is a descendant of UIBaseElement with HasLabel, SetValue, HasPlaceholder, IsInput interfaces parameterized with TextAreaAssert and inherits its methods. But TextArea also has methods of its own.

In C# TextArea is a descendant of TextField and inherits its methods. But TextArea also has methods of its own.

Here is a list of available methods in Java:

|Method | Description | Return Type
--- | --- | ---
**addNewLine(String line)** | add line to the already existing  | void
**cols()** | returns value of cols attribute | int
**getLines()** | returns lines (text) from the text area | List<String>
**getValue()**    | calls getText() method                 | String
**getText()**     | returns value of attribute "value"     | String
**is()**          | returns object for work with assertions | TextAreaAssert
**labelText()** | returns value of TextArea label | String
**maxlength()** | returns value of maxlength attribute | int
**minlength()** | returns value of minlength attribute | int
**placeholder()** | returns value of placeholder in TextArea | String
**rows()** | returns value of rows attribute | int
**setLines(String... lines)** | sets lines (text)  | void
**setValue()**    | setting value                          | void


<a href="https://github.com/jdi-testing/jdi-light/blob/master/jdi-light-html-tests/src/test/java/io/github/epam/html/tests/elements/common/TextAreaTests.java" target="_blank">Test examples in Java</a><br>

Here is a list of available methods in C#:

|Method | Description | Return Type
--- | --- | ---
**AddNewLine(string line)** | add line to the already existing ones | void
**AssertThat()** | returns object for work with assertions  | TextAreaAssert
**Cols()** | returns value of cols attribute | int
**GetLines()** | returns lines (text) from the text area | string[]
**Is()** | returns object for work with assertions  | TextAreaAssert
**Maxlength()** | returns value of maxlength attribute | int
**Minlength()** | returns value of minlength attribute | int
**Rows()** | returns value of rows attribute | int
**SetLines(string[] lines)** | sets lines (text)  | void

<a href="https://github.com/jdi-testing/jdi-light-csharp/blob/master/JDI.Light/JDI.Light.Tests/Tests/Simple/TextAreaTests.cs" target="_blank">Test examples in C#</a><br>

#### Title
**Title** – A graphical control element representing document title, which is displayed in the title bar of the browser or tab page.

Title is represented by the following class:

- __Java__: _com.epam.jdi.light.ui.html.common.Title_
- __C#__: _JDI.Light.Elements.Common.Title

![Title](../images/html/title2.png)

```java 
@UI("[ui=jdi-title]") //@FindBy(css = "[ui=jdi-title]") 
public static Title jdiTitle;

@Test
public void textTest() {
    jdiTitle.is().text(titleText);
}

@Test
public void clickTest() {
    jdiTitle.click();
    assertEquals(getAlertText(), "JDI Title");
    acceptAlert();
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

```html 
<h1 ui="jdi-title" onclick="alert('JDI Title');">JDI Testing platform</h1>
```

Here is the list of methods available in C# JDI Light:

|Method | Description | Return Type
--- | --- | ---
**AssertThat** |Gets Title's assert | TitleAssert
**Is** |Gets Title's assert | TitleAssert

Here is the list of available methods in Java JDI Light:

|Method | Description | Return Type
--- | --- | ---
**AssertThat()** |Gets Title's assert | TitleAssert
**click()** |Click title | void
**getText()** |Returns title text  | String
**Is()** |Gets Title's assert | TitleAssert

<a href="https://github.com/jdi-testing/jdi-light/blob/master/jdi-light-html-tests/src/test/java/io/github/epam/html/tests/elements/common/LabelTests.java" target="_blank">Test examples in Java</a>

<a href="https://github.com/jdi-testing/jdi-light-csharp/blob/master/JDI.Light/JDI.Light.Tests/Tests/Simple/TitleTests.cs" target="_blank">Test examples in C#</a>


### HTML5 Complex elements
#### RadioButtons

**RadioButtons** – Interface element that allows user to select a single option from a predefined group.

Radio buttons are represented by the following class:

- __Java__: _com.epam.jdi.light.ui.html.complex.elements.RadioButtons_
- __C#__: _JDI.Light.Elements.Complex.RadioButtons_

Consider an example where each radio button is a particular color, described with given HTML code:

![RadioButton](../images/html/radio_html2.png)

```java 
    //@FindBy(name = "colors")
    @UI("[name=colors]") 
    public static RadioButtons colors;

    @Test
    public void selectTest() {
        colors.select("Green");
        colors.is().selected(Green);
        colors.is().text("Green");
        colorsNoLocator.select("Blue");
        colorsNoLocator.is().selected("Blue");
        colors.is().value("Blue");
    }

    @Test
    public void valuesTest() {
        colors.is().values(hasItems("Red", "Green", "Blue", "Yellow"));
    }

    @Test
    public void isValidationTest() {
        colors.is().values(hasItem("Yellow"));
        colors.is().disabled(hasItem("Yellow"));
        colors.is().enabled(not(hasItem("Yellow")));
        colors.is().enabled(hasItems("Green", "Blue"));
    }

    @Test
    public void assertValidationTest() {
        colors.assertThat().values(contains("Red", "Green", "Blue", "Yellow"));
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

```html
<input type="radio" id="red" name="colors">
<label for="red">Red</label> <br>

<input type="radio" id="green" name="colors" checked="">
<label for="green">Green</label> <br>

<input type="radio" id="blue" name="colors">
<label for="blue">Blue</label> <br>

<input type="radio" id="yellow" name="colors" disabled="">
<label for="yellow">Yellow</label>
```

Here is the list of some available methods in Java:

|Method | Description | Return Type
--- | --- | ---
**assertThat()** | Returns object for work with assertions | RadioButtonAssert
**is()** | Returns object for work with assertions | RadioButtonAssert
**select(String/int/Enum)** | Select radiobutton by value/index  | void
**selected()** | Get selected radiobutton value | string
**values()** | Returns list of values | List<string>

Here is the list of some available methods in C#:

|Method | Description | Return Type
--- | --- | ---
**AssertThat()** | Returns object for work with assertions | RadioButtonAssert
**Is()** | Returns object for work with assertions | RadioButtonAssert
**Select(string/int)** | Select radiobutton by value/index  | void
**Selected()** | Get selected radiobutton value | string
**Values()** | Returns list of values | List<string>


<a href="https://github.com/jdi-testing/jdi-light/blob/master/jdi-light-html-tests/src/test/java/io/github/epam/html/tests/elements/complex/RadioTests.java" target="_blank">Test examples in Java</a>

<a href="https://github.com/jdi-testing/jdi-light-csharp/blob/master/JDI.Light/JDI.Light.Tests/Tests/Complex/RadioButtonsTests.cs" target="_blank">Test examples in C#</a>

[BDD Steps example](https://jdi-docs.github.io/jdi-light/#radiobuttons-2) <br>

#### Table

**Table** – A complex element that consists of a header, a body (at least one row and one column) and a footer. You are able to perform a list of readonly interactions with this element.

Tables are represented by the following classes in Java and C#:

- __Java__: <a href="https://github.com/jdi-testing/jdi-light/blob/master/jdi-light/src/main/java/com/epam/jdi/light/elements/complex/table/Table.java">Table.java</a>
- __C#__: <a href="https://github.com/jdi-testing/jdi-light-csharp/blob/master/JDI.Light/JDI.Light/Elements/Complex/Table/Table.cs">Table.cs</a>

![Table](../images/html/tableHtml2.png)

```html 
<table class="uui-table stripe tbl-without-header table-td-click"
                ui="table" id="users-table">
    <tbody>
        <tr>
            <th>Name</th>
            <th>Phone</th>
            <th>Email</th>
            <th>City</th>
        </tr>
        <tr>
            <td>Burke Tucker</td>
            <td>076 1971 1687</td>
            <td>et.euismod.et@ut.edu</td>
            <td>GozŽe</td>
        </tr>
        <tr>
            <td>Grady Brock</td>
            <td>(011307) 16843</td>
            <td>cursus.et@commodo.org</td>
            <td>Alcobendas</td>
        </tr>
        <tr>
            <td>Harding Lloyd</td>
            <td>0800 1111</td>
            <td>neque.In.ornare@mauris.co.uk</td>
            <td>Beauvais</td>
        </tr>
    </tbody>
</table>
```


```java 
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
public void tableReceivingDataTest() {
    assertThat(usersSetup.column("City").getValue().substring(0,26), is("GozŽe;Alcobendas;Beauvais;"));
    assertThat(usersSetup.preview().substring(0,35), is("Name Phone Email CityBurke Tucker 0"));
    assertThat(usersSetup.cell(1,4), is("Zachary Hendrix"));
}

@Test
public void rowMatcherTest() {
    usersSetup.has().rowThat(containsValue("Colby Young", inColumn("Name")));
    usersSetup.assertThat().all().rows(containsValue("0", inColumn("Phone")));
    usersSetup.assertThat().no().rows(containsValue("Australopithecus", inColumn("Name")));
    usersSetup.assertThat().atLeast(2).rows(containsValue("Sean", inColumn("Name")));
    usersSetup.assertThat().exact(15).rows(containsValue("0800 1111", inColumn("Phone")));
}

@Test
public void tableParamTest() {
    usersSetup.is().size(4);
    usersSetup.is().count(400);
    usersSetup.is().columns(asList("Name", "Phone", "Email", "City"));
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
        Assert.AreEqual(
     "Brian Meyer;(016977) 0358;
        mollis.nec@seddictumeleifend.co.uk;Houston",
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
       HasValue("mollis.nec@seddictumeleifend.co.uk", 
            InColumn("Email")), 
       HasValue("Houston", InColumn("City")));
}

[Test]
public void HugeTableSearchByColumnNamesHasValuesTest()
{
    PerformancePage.UsersTable.AssertThat().HasRowWithValues(
        HasValue("Brian Meyer", InColumn("Name")),
        HasValue("mollis.nec@seddictumeleifend.co.uk",
        InColumn("Email")));
    var row = PerformancePage.UsersTable.Row(
        HasValue("Brian Meyer", InColumn("Name")),
        HasValue("mollis.nec@seddictumeleifend.co.uk",
         InColumn("Email")));
    Assert.AreEqual("Brian Meyer;(016977)
             0358;mollis.nec@seddictumeleifend.co.uk;Houston",
             row.GetValue());
}

[Test]
public void HugeTableSearchByColumnNumbersHasValuesTest()
{
    PerformancePage.UsersTable.AssertThat().HasRowWithValues(
        HasValue("Brian Meyer", InColumn(1)),
        HasValue("mollis.nec@seddictumeleifend.co.uk",
         InColumn(3)));
    var row = PerformancePage.UsersTable.Row(
        ContainsValue("Meyer", InColumn("Name")),
        ContainsValue("co.uk", InColumn("Email")));
    Assert.AreEqual("Brian Meyer;
        (016977) 0358;mollis.nec@seddictumeleifend.co.uk;Houston",
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
            HasValue("mollis.nec@seddictumeleifend.co.uk", 
           InColumn("Email")))
        .NotEmpty()
        .RowsWithValues(3, ContainsValue("Baker", InColumn(1)))
        .HasColumn("Email")
        .HasColumns(new[] {"Name", "City"})
        .Columns(Is.SubsequenceOf(new[] {"Name", "City", "Phone",
         "Email", "Address"}));
}

[Test]
public void TableRowPerformanceTest()
{
    PerformancePage.Open();
    PerformancePage.CheckOpened();
    AreEqual("Burke Tucker;076 1971 1687;et.euismod.et@ut.edu;GozŽe",
       PerformancePage.UsersTable.Row(1).GetValue());
    AreEqual("Burke Tucker;076 1971 1687;et.euismod.et@ut.edu;GozŽe",
      PerformancePage.UsersTable.Row("Burke Tucker").GetValue());
    AreEqual("Burke Tucker;076 1971 1687;et.euismod.et@ut.edu;GozŽe", 
      PerformancePage.UsersTable.Row(Users.Name).GetValue());
    var value = PerformancePage.UsersTable.Preview();
    AreEqual("Name Phone Email City" +
      "Burke Tucker 076 1971 1687 et.euismod.et@ut.edu GozŽe"+
      "Grady Brock (011307) 16843 cursus.et@commodo.org Alcobendas"+
      "Harding Lloyd 0800 1111 neque.In.ornare@mauris.co.uk Beauvais",
                         value.Substring(0, 194));
}

[Test]
public void TableCellPerformanceTest()
{
    PerformancePage.Open();
    PerformancePage.CheckOpened();
    AreEqual("ipsum.non.arcu@auctorullamcorper.ca",
       PerformancePage.UsersTable.Cell(3, 4));
    AreEqual("ipsum.non.arcu@auctorullamcorper.ca",
       PerformancePage.UsersTable.Cell("Email", 4));
    AreEqual("ipsum.non.arcu@auctorullamcorper.ca",
       PerformancePage.UsersTable.Cell(3, "Zachary Hendrix"));
    AreEqual("ipsum.non.arcu@auctorullamcorper.ca",
       PerformancePage.UsersTable.Cell("Email", "Zachary Hendrix"));
}

[Test]
public void TableColumnPerformanceTest()
{
    PerformancePage.Open();
    PerformancePage.CheckOpened();
    AreEqual("076 1971 1687;(011307) 16843;0",
       PerformancePage.UsersTable.Column(2).
         GetValue().Substring(0, 30));
    AreEqual("076 1971 1687;(011307) 16843;0",
    PerformancePage.UsersTable.Column("Phone").
        GetValue().Substring(0, 30));
    AreEqual("076 1971 1687;(011307) 16843;0",
    PerformancePage.UsersTable.Column(Users.Phone).
        GetValue().Substring(0, 30));
}		
```

__JDI JTable annotation__

Along with providing a Table type element JDI Light also provides a __*@JDropdown*__ annotation for
a better element locating. In addition to what Table type does __*@JDropdown*__  also allows
some kind of customization in the way the element is being located on the page.


This annotation has the following fields that can be used for locating a table element:

- __*String root()*__ - value of this field points to the root locator of table element
- __*String[] header()*__ - list of the columns names
- __*String headers()*__ - locator of a table header
- __*String row()*__ - locator representing a single row of a table
- __*String column()*__ - locator representing a column of a table
- __*String cell()*__ - locator representing a table cell
- __*String allCells()*__ - locator representing all table cells
- __*String rowHeader()*__ - the value of a table header corresponding to a particular raw
- __*int size()*__ - amount of columns
- __*int count()*__ - amount of rows
- __*int firstColumnIndex()*__ - index of the first column
- __*int[] columnsMapping()*__ - a collection containing indexes of the columns
  that are going to be used for processing, e.g. if one decides to work with not all columns but only with particular ones
  or if a column contains e.g. an icon or a checkbox and should not be processed then its index shouldn't be listed in columnsMapping field


Here is a list of available methods in Java:

| Method | Description | Return Type|
--- | --- | ---
**cell(int colNum, int rowNum)** | Returns a cell object of a table according to the cell index | String
**cell(int colNum, String rowName)** | Returns a cell object of a table according to the cell index | String
**cell(String colName, int rowNum)** | Returns a cell object of a table according to the cell index | String
**cell(String colName, String rowNum)** | Returns a cell object of a table according to the cell index | String
**column(Enum colName)** | Returns a column object of a table according to column name | Line
**column(int colNum)** | Returns a column object of a table according to column number | Line
**column(String colName)** | Returns a column object of a table according to column name | Line
**column(String column)** | Asserts whether table Check that the table has the specified column | BaseTableAssert
**columns()** | Returns a list of column objects of a table | List\<Line>
**columns(List<String> columns)** | Asserts whether table Check that the table has the specified columns | BaseTableAssert
**columns(Matcher<Collection<? extends String>>)** | Match passed value with table columns | BaseTableAssert
**count()** | Returns amount of rows | int
**empty()** | Asserts whether table is empty | BaseTableAssert
**filterRows(Matcher<String> matcher, Column column)** | Sets and returns a list of filtered rows of a table according to matching column | List\<Line>
**filterRows(Pair<Matcher<String>,Column>... matchers)** | Sets and returns a list of filtered rows of a table according to matching column | List\<Line>
**getValue()** | Returns a string content of values for a particular row, where values are separated by ";" | String
**header()** | Returns a list of table's headers | List<String>
**isEmpty()** | Asserts whether a table is empty | boolean
**isNotEmpty()** | Asserts whether a table is not empty | boolean
**notEmpty()** | Asserts whether table is not empty | BaseTableAssert
**preview()** | Returns table preview | String
**row(Matcher<String> matcher, Column column)** |Check that the table has rows that meet expected condition| BaseTableAssert
**rows(TableMatcher... matchers)** |Makes sure that the table has at least a certain number of the specified line| BaseTableAssert
**row(Enum rowName)** | Returns a row object of a table according to row name | Line
**row(int rowNum)** | Returns a row object of a table according to row number | Line
**row(Matcher<String> matcher, Column column)** | Returns a row object of a table according to matching column | Line
**row(Pair<Matcher<String>,Column>... matchers)** | Returns a row object of a table according to matching column | Line
**row(String rowName)** | Returns a row object of a table according to row name | Line
**row(TableMatcher... matchers)** | Returns a row object of a table according to matcher | Line
**rowThat(TableMatcher... matchers)** |Check that the table has at list one specified row | BaseTableAssert
**rowThat(Single matcher, Column column)** | Check that the table has at list one specified row | BaseTableAssert
**rows()** | Returns a list of rows of a table | List\<Line>
**rows(TableMatcher... matchers)** | Returns a list of rows of a table according to matchers | List\<Line>
**size()** | Returns amount of columns | int
**webRow(int rowNum)** | Returns all UIElements in the row according to row number | List<UIElement>
**webRow(String rowName)** | Returns all UIElements in the row according to row name | List<UIElement>
**webRow(Enum rowName)** | Returns all UIElements in the row according to row name | List<UIElement>
**webColumn(int colNum)** | Returns all UIElements in the column according to column number | List<UIElement>
**webColumn(String colName)** | Returns all UIElements in the column according to column name | List<UIElement>
**webColumn(Enum colName)** | Returns all UIElements in the column according to column name | List<UIElement>
**webCell(int colNum, int rowNum)** | Returns all UIElements in the column according to cell position | List<UIElement>
**size(Matcher<Integer> condition)** | Asserts whether table size satisfies some matcher condition | BaseTableAssert
**size(int size)** | Asserts whether table has a particular size | BaseTableAssert

And here are methods available in C#:

| Method | Description | Return Type|
--- | --- | ---
**AssertThat()** | Applicable for performing assert actions for tables | TableAssert
**Cell(int colNum, int rowNum)** | Sets and returns a cell object of a table according to the cell's indices | string
**Cell(string colName, int rowNum)** | Sets and returns a cell object of a table according to the cell's column name and row index | string
**Cell(int colNum, string rowName)** | Sets and returns a cell object of a table according to the cell's column index and row name | string
**Cell(string colName, string rowName)** | Sets and returns a cell object of a table according to the cell's column name and row name | string
**Column(int colNum)** | Sets and returns a column object of a table according to the column's index | Line
**Column(string colName)** | Sets and returns a column object of a table according to the column's name | Line
**Column(Enum colName)** | Sets and returns a column object of a table according to column name | Line
**Columns()** | Sets and returns a list of column objects of a table | List<Line>
**Columns(Matcher<IEnumerable<string>> condition)** | Asserts whether headers satisfy some matcher condition | TableAssert
**ContainsValue(string value, Column column)** | Looks for an object by some value occurrence in a particular column | TableMatcher
**Empty()** | Asserts whether table is empty | TableAssert
**FilterRows(Matcher<String> matcher, Column column)** | Sets and returns a list of filtered rows of a table according to matching column | List<Line>
**FilterRows(params KeyValuePair<Matcher<string>, Column>[] matchers)** | Sets and returns a list of filtered rows of a table according to matching column | List<Line>
**GetValue()** | Returns a string content of values for a particular row, where values are separated by ";" | string
**HasColumn(string column)** | Asserts whether table has a particular header | TableAssert
**HasColumns(IEnumerable<string> columns)** | Asserts whether table has particular headers | TableAssert
**HasRowWithValues(params TableMatcher[] matchers)** | Asserts whether a row with particular matchers exists in a table | TableAssert
**HasValue(string value, Column column)** | Looks for an object (exact match) in a particular column | TableMatcher
**Is()** | Applicable for performing assert actions for tables | TableAssert
**InColumn(string value)** | Sets an object of some column to a particular value | Column
**InColumn(int num)** | Sets an object of some column to a particular column number | Column
**NotEmpty()** | Asserts whether table is not empty | TableAssert
**Row(params TableMatcher[] matchers)** | Sets and returns a row object from a table according to some matcher params (returns 'null' if there is no such row) | Line
**Row(int rowNum)** | Sets and returns a row object of a table according to the row index | Line
**Row(string rowName)** | Sets and returns a row object of a table according to the row name | Line
**Row(Enum rowName)** | Sets and returns a row object of a table according to row name | Line
**Row(Matcher<String> matcher, Column column)** | Sets and returns a row object of a table according to matching column | Line
**Row(params KeyValuePair<Matcher<string>, Column>[] matchers)** | Sets and returns a row object of a table according to matching column | Line
**RowsAsLines(params TableMatcher[] matchers)** | Sets and returns a list of rows of a table according to matchers | List<Line>
**RowsAsLines()** | Sets and returns a list of rows of a table | List<Line>
**RowsWithValues(int count, params TableMatcher[] matchers)** | Asserts whether rows with particular matchers exist in a table multiple times | TableAssert
**string Preview()** | Returns a string content of the whole table | string
**Size(Matcher<int> condition)** | Asserts whether table size satisfies some matcher condition | TableAssert
**Size(int expectedSize)** | Asserts whether table has a particular size | TableAssert

<a href="https://github.com/jdi-testing/jdi-light/blob/master/jdi-light-examples/src/test/java/io/github/epam/tests/recommended/TableTests.java" target="_blank">Test examples in Java</a>

<a href="https://github.com/jdi-testing/jdi-light-csharp/blob/master/JDI.Light/JDI.Light.Tests/Tests/Composite/TableTests.cs" target="_blank">Test examples in C#</a>

[BDD Steps example](https://jdi-docs.github.io/jdi-light/?java#table-2)<br>

#### DataTable

**DataTable** – A complex element that consists of header, a body (at least one row and one column) and a footer. You are
able to perform a list of readonly interactions with this element in order to get all data based on specified criteria.

DataTables are represented by the following classes in Java:

```java 
@UI("#users-table") //@FindBy(id = "users-table")
public static DataTable<PerformanceUserRow, PerformanceUserInfo> usersData;
@JTable( root = "#users-table",
        row = "//tr[%s]/td", column = "//tr/td[%s]",
        cell = "//tr[{1}]/td[{0}]", allCells = "td",
        headers = "th", header = {"Name", "Phone", "Email", "City"},
        rowHeader = "Name", size = 4
)
public static DataTable<PerformanceUserRow, PerformanceUserInfo> usersDataSetup;

@Test
public void filterDataTest() {
    assertEquals(usersDataSetup.dataRow("Grady Brock"), GRADY_BROCK);
    assertEquals(usersDataSetup.dataRow(2), GRADY_BROCK);
    usersDataSetup.assertThat().row(d -> d.name.contains("Brock"));
    usersDataSetup.has().row(GRADY_BROCK);
    usersDataSetup.assertThat().row(d -> d.equals(GRADY_BROCK));
}

@Test
public void filterLinesTest() {
    PerformanceUserRow line =  usersData.line(2);
    validateUserRow(line);
    line =  usersData.line("Grady Brock");
    validateUserRow(line);
    line =  usersData.line(d -> d.name.contains("Brock"));
    validateUserRow(line);
}

private void validateUserRow(PerformanceUserRow line) {
    line.city.click();
    validateAlert(is(GRADY_BROCK.city));
    assertEquals(line.email.getText(), GRADY_BROCK.email);
}

@Test
public void rowMatcherChainTest() {
    usersDataSetup.assertThat()
            .all().rows(d -> d.name.length() > 4)
            .no().rows(d -> isBlank(d.phone))
            .atLeast(2).rows(d -> d.name.contains("Sean"))
            .exact(15).rows(d -> d.phone.contains("0800 1111"))
            .exact(1).row(GRADY_BROCK);
}
  ```

- __Java__: _com.epam.jdi.light.elements.complex.table.DataTable.java_

![DataTable](../images/html/tableHtml2.png)

```html 
<table class="uui-table stripe tbl-without-header table-td-click"
     ui="table" id="users-table">
    <tbody>
        <tr>
            <th>Name</th>
            <th>Phone</th>
            <th>Email</th>
            <th>City</th>
        </tr>
        <tr>
            <td>Burke Tucker</td>
            <td>076 1971 1687</td>
            <td>et.euismod.et@ut.edu</td>
            <td>GozŽe</td>
        </tr>
        <tr>
            <td>Grady Brock</td>
            <td>(011307) 16843</td>
            <td>cursus.et@commodo.org</td>
            <td>Alcobendas</td>
        </tr>
        <tr>
            <td>Harding Lloyd</td>
            <td>0800 1111</td>
            <td>neque.In.ornare@mauris.co.uk</td>
            <td>Beauvais</td>
        </tr>
    </tbody>
</table>
```

Here is a list of available methods in Java (DataTable expand [Table](#table) class - methods from previous table are available too_):

In return types column _"D"_ refers to the user data object and _"L"_ refers to the table line object.

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
**getValue()** | Returns string content of values for particular row, where values are separated by "&#124;" | String
**getValue()** | Returns table content separated by "&#124;" | String
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

DataTableAssert methods in Java:

| Method | Description | Return Type|
--- | --- | ---
**assertThat()** | Applicable for performing assert actions for tables | DataTableAssert
**has()** | Applicable for performing assert actions for tables | DataTableAssert
**is()** | Applicable for performing assert actions for tables | DataTableAssert
**shouldBe()** | Applicable for performing assert actions for tables | DataTableAssert
**waitFor()** | Applicable for performing assert actions for tables | DataTableAssert

<a href="https://github.com/jdi-testing/jdi-light/blob/master/jdi-light-html-tests/src/test/java/io/github/epam/html/tests/elements/common/RangeTests.java" target="_blank">Test examples in Java</a><br>

[BDD Steps example](https://jdi-docs.github.io/jdi-light/?java#datatable-2)
<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

#### Dropdown

**Dropdown** – A graphical control element that allows user to choose a single value from a list.

![DropDown](../images/dropdown.png)

JDI Light has support for dropdown elements with their own type. There are several ways of dropdown usage in JDI Light, each serving different needs.

__Dropdown representation__

JDI Light provides a __Dropdown__ class which is using for dropdown representation as a type of web element.

Also this class can be used when working with HTML5 elements in cases when dropdown is represented with HTML _\<select>_ tag.

Consider an example of HTML5 dropdown with the given HTML code:

![Dropdown HTML5](../images/html/dropdown_html52.png)

```java 
@JDropdown(root = "div[ui=dropdown]",
    value = ".filter-option",
    list = "li",
    expand = ".caret")
public static Dropdown colors2; //@FindBy(css = "div[ui=dropdown]")
	
@Test
public void selectStringTest() {
    colors2.select("Red");
    colors2.is().selected("Red");
}

@Test
public void selectEnumTest() {
    colors2.select(Green);
    colors2.is().selected(Green);
}

@Test
public void selectIndexTest() {
    colors2.select(4);
    colors2.is().selected(Blue);
}

@Test
public void checkValuesTest() {
    colors2.assertThat().size(5);
    colors2.assertThat().values(is(dropdownValues));
    colors2.is().values(hasItem("Yellow"));
    colors2.is().values(not(hasItem("Missing color")));
    colors2.is().enabled("Colors", "Red", "Green", "Blue", "Yellow");
    colors2.is().values(INNER, hasItem("Yellow"));
    colors2.assertThat().values(INNER, is(dropdownValues));
    colors2.is().values(INNER, not(hasItem("Missing color")));
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

```html
<select id="dress-code">
    <option value="fancy">Fancy</option>
    <option value="casual" selected="">Casual</option>
    <option value="disabled" disabled="">Disabled</option>
    <option value="pirate">Pirate</option>
</select>
```


__JDI Dropdown annotation__

For better use, JDI Light provides a __*@JDropdown*__ annotation to locate dropdown elements. This annotation can be used in cases when working with a
complex element that may consist of more a complicated html structure. JDropdown annotation allows customise navigation of the web element inner structure by using
annotation default methods.

<!-- ![Dropdown HTML](../images/html/dropdown_html.png) -->


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

```html 
<div class="form-group colors" ui="dropdown" id="colors">
    <select class="selectpicker uui-form-element" style="display: none;">
        <option>Colors</option>
        <option>Red</option>
        <option>Green</option>
        <option>Blue</option>
        <option>Yellow</option>
    </select>
    <div class="btn-group bootstrap-select uui-form-element"><button type="button"
            class="btn dropdown-toggle selectpicker btn-default" data-toggle="dropdown" title="Colors"><span
                class="filter-option pull-left" value="">Colors</span>&nbsp;<span class="caret"></span></button>
        <div class="dropdown-menu open" style="max-height: 933px; overflow: hidden; min-height: 90px;">
            <ul class="dropdown-menu inner selectpicker" role="menu"
                style="max-height: 921px; overflow-y: auto; min-height: 78px;">
                <li rel="0" class="selected"><a tabindex="0" class="" style=""><span class="text">Colors</span>
                    <i class="glyphicon glyphicon-ok icon-ok check-mark"></i></a></li>
                <li rel="1"><a tabindex="0" class="" style=""><span class="text">Red</span>
                    <i class="glyphicon glyphicon-ok icon-ok check-mark"></i></a></li>
                <li rel="2"><a tabindex="0" class="" style=""><span class="text">Green</span>
                    <i class="glyphicon glyphicon-ok icon-ok check-mark"></i></a></li>
                <li rel="3"><a tabindex="0" class="" style=""><span class="text">Blue</span>
                    <i class="glyphicon glyphicon-ok icon-ok check-mark"></i></a></li>
                <li rel="4"><a tabindex="0" class="" style=""><span class="text">Yellow</span>
                    <i class="glyphicon glyphicon-ok icon-ok check-mark"></i></a></li>
            </ul>
        </div>
    </div>
</div>
```

JDropdown annotation consists of the following elements using which element inner structure can be customised:

- __*root()*__ - value of this element points to the root locator of dropdown element
- __*value()*__ - locator of option selected by default in dropdown list
- __*list()*__ - locator representing list options
- __*expand()*__ - locator for expanding the dropdown list
- __*how()*__ - type of locators with which elements will be identified. By default it is css

Here is a list of some available methods:

|Method | Description | Return Type
--- | --- | ---
**assertThat()** | Applicable for performing assert actions for DropDown | ListAssert<UIElement>
**close()** | Close expanded before dropdown list | void
**expand()** | Expand dropdown list | void
**getValue()/getText()/getSelected()** | Return selected dropdown value | String
**has()** | Applicable for performing assert actions for DropDown | ListAssert<UIElement>
**is()** | Applicable for performing assert actions for DropDown | ListAssert<UIElement>
**isExpanded()** | Show that dropdown element expanded | boolean
**isDisplayed()** | Show\wait that dropdown element displayed on the screen | boolean
**selected(String option)** | Check if option has been selected | boolean
**setup(Field field)** | Setup the dropdown using specified fields | void
**shouldBe()** | Applicable for performing assert actions for DropDown | ListAssert<UIElement>
**size()** | Return amount of elements in the list | int
**waitFor()** | Applicable for performing assert actions for DropDown | ListAssert<UIElement>

Available Assert methods in C#:

|Method | Description | Return Type
--- | --- | ---
**AssertThat** |Gets dropdown assertion | DropDownAssert
**Disabled(Matcher<IEnumerable<string>> condition)** |Checks that dropdown values are disabled by some condition | DropDownAssert
**Enabled(Matcher<IEnumerable<string>> condition)** |Checks that dropdown values are enabled by some condition | DropDownAssert
**Is** |Gets dropdown assertion | DropDownAssert
**Selected(string option)** |Checks whether some option is selected  | DropDownAssert
**Selected(Enum option)** |Checks whether some option is selected  | DropDownAssert
**Values(Matcher<IEnumerable<string>> condition)** |Checks that dropdown values match some condition | DropDownAssert

<a href="https://github.com/jdi-testing/jdi-light/tree/master/jdi-light-html-tests/src/test/java/io/github/epam/html/tests/elements/complex/dropdown" target="_blank">Test examples in Java</a>

<a href="https://github.com/jdi-testing/jdi-light-csharp/blob/master/JDI.Light/JDI.Light.Tests/Tests/Common/DropDownTests.cs" target="_blank">Test examples in C#</a>

[BDD test examples](https://jdi-docs.github.io/jdi-light/?java#dropdown-3)
<br><br><br>

#### MultiDropdown

**MultiDropdown** – A graphical control element that allows user to choose several values from a list.

![DropDown](../images/multidropdown.png)

JDI Light provides a MultiSelector class which is using for MultiDropdown representation as a type of web element.

```java 
    //@FindBy(id = "multi-dropdown")
    @UI("#multi-dropdown") 
    public static MultiSelector multiDropdown;

    @Test
    public void selectTest() {
        multiDropdown.check("Electro", "Metalic");
        multiDropdown.checked().equals(asList("Electro", "Metalic"));
        multiDropdown.is().selected("Electro");
        multiDropdown.uncheck("Metalic");
        multiDropdown.checked().equals(asList("Electro"));
    }

    @Test
    public void disabledTest() {
        multiDropdown.check("Steam");
        multiDropdown.select("Disabled");
        multiDropdown.is().selected("Steam");
    }

    @Test
    public void labelTest() {
        multiDropdown.label().is().text("Multi dropdown:");
        multiDropdown.label().is().text(containsString("Multi"));
    }

    @Test
    public void isValidationTest() {
        multiDropdown.is().selected("Steam");
        multiDropdown.is().selected(Steam);
        multiDropdown.assertThat().values(hasItem("Steam"));
        multiDropdown.shouldBe().value("Steam");
        multiDropdown.assertThat().disabled(hasItem("Disabled"))
                .enabled(not(hasItem("Disabled")))
                .enabled(hasItems("Electro", "Metalic"));
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

```html
<span class="multiselect-native-select">
    <select id="multi-dropdown" multiple="multiple">
         <option value="electro">Electro</option>
         <option value="steam" selected="">Steam</option>
         <option value="metalic">Metalic</option>
         <option value="dis" disabled="">Disabled</option>
         <option value="wood">Wood</option>
    </select>
    <div class="btn-group">
        <button type="button" class="multiselect dropdown-toggle btn btn-default"
                data-toggle="dropdown" title="Steam">
            <span class="multiselect-selected-text">Steam</span>
            <b class="caret"></b>
        </button>
        <ul class="multiselect-container dropdown-menu">
            <li><a tabindex="0"><label class="checkbox" title="Electro"><input
                    type="checkbox" value="electro"> Electro</label></a></li>
            <li class="active"><a tabindex="0"><label class="checkbox" title="Steam">
                <input type="checkbox" value="steam"> Steam</label></a></li>
            <li><a tabindex="0"><label class="checkbox" title="Metalic">
                <input type="checkbox" value="metalic"> Metalic</label></a></li>
            <li class="disabled"><a tabindex="-1"><label class="checkbox" title="Disabled">
                <input type="checkbox" value="dis" disabled=""> Disabled</label></a></li>
            <li><a tabindex="0"><label class="checkbox" title="Wood">
                <input type="checkbox" value="wood"> Wood</label></a></li>
        </ul>
    </div>
</span>
```

MultiDropdown are represented by the following classes:

- __Java__: _com.epam.jdi.light.ui.html.complex.MultiSelector_
- __C#__: _JDI.Light.Elements.Composite.MultiDropdown_

The list of methods available for Java in JDI Light:

|Method | Description | Return Type
--- | --- | ---
**assertThat()** | Applicable for performing assert actions for MultiDropdown | DataTableAssert
**check(String/String.../Enum.../int...)** |Select values in multi dropdown | void
**checked()** | Get selected values | List\<String>
**has()** | Applicable for performing assert actions for MultiDropdown | DataTableAssert
**is()** | Applicable for performing assert actions for MultiDropdown | DataTableAssert
**selected()** | Get selected value by default | String
**shouldBe()** | Applicable for performing assert actions for MultiDropdown | DataTableAssert
**uncheck(String.../Enum.../int...)** | Deselect values in multi dropdown | void
**waitFor()** | Applicable for performing assert actions for MultiDropdown | DataTableAssert

Here is the list of some methods available for C# in JDI Light:

|Method | Description | Return Type
--- | --- | ---
**AssertThat** |Gets multiDropDown assert  | MultiDropdownAssert
**Close()** |Close expanded list  | void
**Disabled(Matcher<IEnumerable<string>> condition)** |Check whether some values are disabled in MultiDropDown by some matcher  | MultiDropdownAssert
**Enabled(Matcher<IEnumerable<string>> condition)** |Check whether some values are enabled in MultiDropDown by some matcher  | MultiDropdownAssert
**Expand()** |Expand list  | void
**GetSelectedOptions()** |Get selected options  | List
**Is** |Gets multiDropDown assert  | MultiDropdownAssert
**OptionIsEnabled(string)** |Check whether option is enabled  | bool
**OptionExists(string)** |Check whether option exists in list  | bool
**SelectOption(string)** |Select specified option  | void
**SelectOptions(List)** |Select specified options  | void
**Selected(string option)** |Check whether option is selected  | MultiDropdownAssert
**Selected(Enum option)** |Check whether option is selected  | MultiDropdownAssert
**Values(Matcher<IEnumerable<string>> condition)** |Check whether some values exist in MultiDropDown by some matcher  | MultiDropdownAssert

<a href="https://github.com/jdi-testing/jdi-light/blob/master/jdi-light-html-tests/src/test/java/io/github/epam/html/tests/elements/complex/MultiDropdownTests.java" target="_blank">Test examples in Java</a>

<a href="https://github.com/jdi-testing/jdi-light-csharp/blob/master/JDI.Light/JDI.Light.Tests/Tests/Composite/MultiDropdownTests.cs" target="_blank">Test examples in C#</a><br>

[BDD Steps example](https://jdi-docs.github.io/jdi-light/?java#multidropdown-2)<br>
#### DataList

**DataList** – A graphical control element that allows user to choose one value from a list or enter it by himself.
DataList element contains a set of options with values available as inputs.

![DataList](../images/icecreamdatalist.png)

__C# JDI DataList annotation__

For better use in C# JDI Light provides a __*[JDataList]*__ annotation to locate DataList elements. This annotation consists of the following elements:

- __*root*__ - value of this element points to the root locator of the dropdown element
- __*values*__ - options locator in dropdown list
- __*how*__ - type of locators with which elements will be identified. By default it is set as css

```csharp 
[JDataList("#ice-cream", "#ice-cream-flavors > option")]
    public DataList IceCream { get; set; }

[JDataList("#disabled-dropdown",
          "#disabled-dropdown > option")]
    public DataList DisabledDropdownAsDataList { get; set; }

[Test]
public void GetValueTest()
{
    AreEqual(TestSite.Html5Page.IceCream.Selected(), "Coconut");
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

DataList element type is provided by JDI Light in:

- __Java__: _com.epam.jdi.light.ui.html.complex.DataListOptions_
- __C#__: _JDI.Light.Elements.Common.DataList_

Have a look at the following example with HTML code provided:

```java 
@UI("#ice-cream") //@FindBy(id = "ice-cream")
public static DataListOptions iceCreamDataList;

@Test
public void selectTest() {
    iceCream.select("Chocolate");
    iceCream.is().selected("Chocolate");
}

@Test
public void selectNumTest() {
    iceCream.select(5);
    iceCream.is().selected("Vanilla");
}
```


<!-- ![Datalist example](../images/html/datalist_html.png) -->

```html
<label for="ice-cream">Choose your lovely icecream</label>
<input list="ice-cream-flavors" id="ice-cream" placeholder="Ice cream">

<datalist id="ice-cream-flavors">
    <option value="Chocolate"></option>
    <option value="Coconut"></option>
    <option value="Mint"></option>
    <option value="Strawberry"></option>
    <option value="Vanilla"></option>
</datalist>
```

The list of methods available for Java in JDI Light:

|Method | Description | Return Type
--- | --- | ---
**assertThat** |Gets element's assert | DataListAssert
**input(string value)** |Input user's value into DataList  | void
**is** |Gets element's assert | DataListAssert
**listEnabled()** |Return a list of values of enabled options | List\<String>
**listDisabled()** |Return a list of values of disabled options | List\<String>
**select(String/Enum/int)** |Select datalist option by value or index | void
**selected()** |Get selected option value | String
**values()** |Get all option values from DataList | List\<String>

The list of some methods available for C# in JDI Light:

|Method | Description | Return Type
--- | --- | ---
**AssertThat** |Gets element's assert | DataListAssert
**Expand()** |Expands the list of possible values | void
**GetSelected()** |Get selected DataList value  | string
**Input(string value)** |Input user's value into DataList  | void
**Is** |Gets element's assert | DataListAssert
**Select(string/int)** |Select datalist by value/index  | void

<a href="https://github.com/jdi-testing/jdi-light/blob/master/jdi-light-html-tests/src/test/java/io/github/epam/html/tests/elements/complex/combobox/DataListTests.java" target="_blank">Test examples in Java</a>

<a href="https://github.com/jdi-testing/jdi-light-csharp/blob/master/JDI.Light/JDI.Light.Tests/Tests/Common/DataListTests.cs" target="_blank">Test examples in C#</a>

[BDD Steps example](https://jdi-docs.github.io/jdi-light/?java#datalist-2)

#### CheckList
**CheckList** – A graphical control element representing a set of checkboxes, each of which allows user to control a two-state parameter (enabled or disabled).

Checklist element type is available in the following packages:

- __Java__: com.epam.jdi.light.ui.html.complex.Checklist
- __C__#: JDI.Light.Elements.Complex.CheckList

See an example with HTML code describing checklist element.

![Checklist Example](../images/html/checklist_html2.png)

```java 
//@FindBy(name = "checks-group")
@UI("[name=checks-group]") public static Checklist weather;
public static Checklist weatherNoLocator;

@Test
public void checkTest() {
    weather.check("Rainy day", "Sunny");
    weather.is().checked(hasSize(2));
    weather.is().checked(hasItems("Rainy day", "Sunny"));
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

```html
<input type="checkbox" id="hot" name="checks-group" checked="">
<label for="hot">Hot option</label> <br>

<input type="checkbox" id="cold" name="checks-group">
<label for="cold">Cold</label> <br>

<input type="checkbox" id="rainy" name="checks-group">
<label for="rainy">Rainy day</label> <br>

<input type="checkbox" id="sunny-day" name="checks-group">
<label for="sunny-day">Sunny</label> <br>

<input type="checkbox" id="disabled-ch" name="checks-group" disabled="">
<label for="disabled-ch">Disabled</label>
```

List of available methods in Java JDI Light:

|Method | Description | Return Type
--- | --- | ---
**assertThat()** | Get select assert | selectAssert
**check(String.../Enum/int...)** | Check specified checkboxes and uncheck others | void
**checkAll()** | Check all checkboxes in checklist | void
**checked()** | Get selected checkbox values | List\<String>
**has()** | Get select assert | selectAssert
**is()** | Get select assert | selectAssert
**listEnabled()** | Get enabled checkboxes | List\<String>
**listDisabled()** | Get disabled checkboxes | List\<String>
**selected()** | Get selected checkbox values | String
**select(String.../Enum/int...)** | Select checkboxes | void
**size()** | Get checklist size | int
**uncheck(String.../Enum/int...)** | Uncheck specified checkboxes and check others  | void
**uncheckAll()** | Uncheck all checkboxes in checklist | void
**values()** | Get checklist values | List\<String>

Here is the list of some methods available for C# in JDI Light:

|Method | Description | Return Type
--- | --- | ---
**AssertThat** | Get select assert | SelectAssert
**Check(params string[]/params int[])** |Check checklist by values/indexes  | void
**CheckAll()** |Check all checkboxes | void
**Checked()** |Get selected checkboxes from checklist value  | List\<String>
**Has** | Get select assert | SelectAssert
**Is** | Get select assert | SelectAssert
**ListEnabled()** | Get enabled checkboxes | List\<String>
**ListDisabled()** | Get disabled checkboxes | List\<String>
**Select(params string[]/params int[])** |Select checklist by values/indexes  | void
**Selected(string option)** | Checks whether a checkbox is selected | bool
**Size()** | Get checklist size | int
**Uncheck(params string[]/params int[])** |Unselect checklist by values/indexes  | void
**UncheckAll()** |Uncheck all checkboxes | void
**Values()** | Get checklist values | List\<String>

<a href="https://github.com/jdi-testing/jdi-light/blob/master/jdi-light-html-tests/src/test/java/io/github/epam/html/tests/elements/complex/ChecklistTests.java" target="_blank">Test examples in Java</a>

<a href="https://github.com/jdi-testing/jdi-light-csharp/blob/master/JDI.Light/JDI.Light.Tests/Tests/Complex/CheckListTests.cs" target="_blank">Test examples in C#</a>

[BDD Steps example](https://jdi-docs.github.io/jdi-light/?java#checklist-2)

#### MultiSelector
**MultiSelector** – A graphical control element that allows user to make a multiple choice.
MultiSelector is represented by the following class:

- __Java__: _com.epam.jdi.light.ui.html.complex.MultiSelector_
- __C#__: _JDI.Light.Elements.Common.MultiSelector_

![MultiSelector](../images/html/multiSelectHtml2.png)

```java 
@UI("#ages") // @FindBy(css = "#ages")  
public static MultiSelector ages;

@Test
public void selectTest() {
    ages.check("Electro", "Metalic");
    assertEquals(ages.checked(), asList("Electro", "Metalic"));
}

@Test
public void selectEnumTest() {
    ages.check(Wood, Steam);
    assertEquals(ages.checked(), asList("Steam", "Wood"));
}

@Test
public void selectNumTest() {
    ages.check(1, 5);
    assertEquals(ages.checked(), asList("Electro", "Wood"));
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

```html
<select id="ages" multiple="" size="4">
    <option value="electro">Electro</option>
    <option value="steam" selected="">Steam</option>
    <option value="metalic">Metalic</option>
    <option value="dis" disabled="">Disabled</option>
    <option value="wood">Wood</option>
</select>
```

Here is a list of available methods and properties in C#:

|Method / Property | Description | Return Type
--- | --- | ---
**AssertThat** | Property that returns object for work with assertions | SelectAssert
**Check(string/string[]/int/int[]/Enum[])** | Select multiselector by values | void
**Checked()** | Get selected values  | List\<string>
**has()** | Returns object for work with assertions | SelectAssert
**Is** | Property that returns object for work with assertions | SelectAssert
**Selected()** | Get selected values | string
**shouldBe()** | Returns object for work with assertions | SelectAssert
**Uncheck(string[]/Enum[]/int[])** | Select multiselector by values/indexes | void
**waitFor()** | Returns object for work with assertions | SelectAssert

Here is the list of available methods/asserts in Java:

|Method | Description | Return Type
--- | --- | ---
**assertThat()** | Returns object for work with assertions| SelectAssert
**check(String/Strings.../TEnum...)** |Select multiselector by values | void
**checked()** |Get selected values  | List\<String>
**is()** |  Returns object for work with assertions| SelectAssert
**selected()** |Get selected values  | String
**uncheck(Strings.../TEnum.../int)** |Select multiselector by values/indices  | void

<a href="https://github.com/jdi-testing/jdi-light/blob/master/jdi-light-html-tests/src/test/java/io/github/epam/html/tests/elements/complex/MultiSelectorTests.java" target="_blank">Test examples in Java</a>

<a href="https://github.com/jdi-testing/jdi-light-csharp/blob/master/JDI.Light/JDI.Light.Tests/Tests/Common/MultiSelectorTests.cs" target="_blank">Test examples in C#</a>

[BDD Steps example](https://jdi-docs.github.io/jdi-light/?java#multidropdown-2)<br>

#### ComboBox

**ComboBox** – A graphical control element that allows user to choose a single
value from a list or enter it by himself (is inherited from the [Datalist](#datalist))

![ComboBox](../images/icecreamdatalist.png)

ComboBox is provided by JDI Light in:

- __Java__: _com.epam.jdi.light.ui.html.complex.Combobox_
- __C#__: _JDI.Light.Elements.Common.Combobox_

```java 
    public static Combobox iceCream;

    // @FindBy(id = "ice-cream")
    @UI("#ice-cream") 
    public static DataList iceCreamDataList;

    @Test
    public void inputTest() {
        iceCreamIs.input("New text");
        iceCreamIs.is().text("New text");
        iceCreamIs.clear();
        iceCreamIs.is().text("");
    }

    @Test
    public void placeholderTest() {
        iceCreamIs.placeholder().equals("Ice cream");
    }

    @Test
    public void selectTest() {
        iceCreamIs.select("Chocolate");
        iceCreamIs.select(Strawberry);
        iceCreamIs.select(5);
    }

    @Test
    public void labelTest() {
        iceCreamIs.label().is().text("Choose your lovely icecream");
        iceCreamIs.label().is().text(containsString("lovely icecream"));
    }

    @Test
    public void isValidationTest() {
        iceCreamIs.listEnabled();
        iceCreamIs.assertThat().equals(asList("Chocolate", "Strawberry"));
        iceCreamIs.is().enabled();
        iceCreamIs.is().selected("Coconut");
        iceCreamIs.is().selected(is("Coconut"));
        iceCreamIs.select(Vanilla);
        iceCreamIs.is().text(containsString("Van"));
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

Have a look at the following example with HTML code provided:

<!-- ![Combobox example](../images/html/datalist_html.png) -->

```html
<input list="ice-cream-flavors" id="ice-cream" placeholder="Ice cream">

<datalist id="ice-cream-flavors">
    <option value="Chocolate"></option>
    <option value="Coconut"></option>
    <option value="Mint"></option>
    <option value="Strawberry"></option>
    <option value="Vanilla"></option>
</datalist>
```

The list of methods available for Java in JDI Light:

|Method | Description | Return Type
--- | --- | ---
**listEnabled()** |Return list of values of enabled options | List\<String>
**listDisabled()** |Return list of values of disabled options | List\<String>
**select(String/Enum/int)** |Select combobox option by value or index | void
**selected()** |Get selected option value | String
**values()** |Get all option values from combobox | List\<String>

Here is the list of some methods available for C# in JDI Light:

|Method | Description | Return Type
--- | --- | ---
**assertThat()** | Returns object for work with assertions| ComboBoxAssert
**Expand()** |Expands the list of possible values | void
**GetSelected()** |Get selected combobox value  | string
**Input(string)** |Input user's value into combobox  | void
**is()** |  Returns object for work with assertions| ComboBoxAssert
**Select(string/int)** |Select combobox by value/index  | void

<a href="https://github.com/jdi-testing/jdi-light/blob/master/jdi-light-html-tests/src/test/java/io/github/epam/html/tests/elements/complex/combobox/IsComboboxTests.java" target="_blank">Test examples in Java</a>

<a href="https://github.com/jdi-testing/jdi-light/blob/master/jdi-light-html-tests/src/test/java/io/github/epam/html/tests/elements/complex/ComboboxTests.java" target="_blank">Test examples in C#</a>

[BDD Steps example](https://jdi-docs.github.io/jdi-light/?java#combobox-2)

### HTML5 Composite elements
####Section

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

**Section** - Logical part of Web Page that contains other UI Elements

Section is located in the following classes:

- __Java__: _com.epam.jdi.light.elements.composite.Section_
- __C#__: _JDI.Light.Elements.Composite.Section_


```java 
   @UI(".someSectionUI") // @FindBy(css = ".someSectionUI")
   public static SomeSection someSectionUI;

   @Test
   public void someSectionWebElementTest() {
      assertNotNull(someSection.webElementPublic);
      assertEquals(someSection.webElementPublic.locator.toString(), "id='webElementPublic'");
      assertEquals(someSection.webElementPublic.parent, someSection);
      assertEquals(someSection.webElementPublic.name, "Web Element Public");
   }
   
```



And here are methods available in Java:

|Method | Description | Return Type
--- | --- | ---
**assertThat()** | Returns object for work with assertions | IsAssert
**has()** | Returns object for work with assertions | IsAssert
**is()** | Returns object for work with assertions | IsAssert
**shouldBe()** | Returns object for work with assertions | IsAssert
**waitFor()** | Returns object for work with assertions | IsAssert

<a href="https://github.com/jdi-testing/jdi-light/blob/master/jdi-light-html-tests/src/test/java/io/github/epam/html/tests/elements/composite/section" target="_blank">Test examples in Java</a>

<a href="https://github.com/jdi-testing/jdi-light-csharp/blob/master/JDI.Light/JDI.Light.Tests/Tests/Composite/SectionTests.cs" target="_blank">Test examples in C#</a>


#### Form



**Form** – Logical part of a web page that represents an HTML form.
Form consists of elements based on _SetValue_ interface and buttons with **submit** function.

Form provides the _fill, submit and verify/check_ functionality.

![Form](../images/html/contact_form_example.png)

```html
<form class="form" id="contact-form">
    <div class="row overflow">
        <div class="col-sm-4">
            <div class="form-group form-group10">
                <label for="name">Name</label>
                <input id="name" type="text" class="uui-form-element">
            </div>
        </div>
        <div class="col-sm-4">
            <div class="form-group form-group10">
                <label for="last-name">Last Name</label>
                <input id="last-name" type="text" class="uui-form-element">
            </div>
        </div>
        <div class="col-sm-4">
            <div class="form-group form-group10">
                <label for="position">Position</label>
                <input id="position" type="text" class="uui-form-element">
            </div>
        </div>
        <div class="col-sm-3">
            <div class="form-group form-group10 lower">
                <label for="passport">Passport</label>
                <input id="passport" type="checkbox" name="passport" class="uui-form-element">
            </div>
        </div>
        <div class="col-sm-4">
            <div class="form-group form-group10">
                <label for="passport-number">Number</label>
                <input id="passport-number" type="text" class="uui-form-element">
            </div>
        </div>
        <div class="col-sm-5">
            <div class="form-group form-group10">
                <label for="passport-seria">Seria</label>
                <input id="passport-seria" type="text" class="uui-form-element">
            </div>
        </div>
        </div>
    <div class="row">
        <div class="col-sm-4">
            <label for="gender">Gender</label>
            <select class="uui-form-element" ui="dropdown" id="gender">
                <option>Male</option>
                <option checked="">Female</option>
            </select>
        </div>
        <div class="col-sm-4">
            <label for="religion">Religion</label>
            <div class="form-group form-group10">
                <input list="religion-options" id="religion" placeholder="Religion" class="uui-form-element">
                <datalist id="religion-options">
                    <option>Christian</option>
                    <option>Muslims</option>
                    <option>Induism</option>
                    <option>Other</option>
                </datalist>
            </div>
        </div>
        <div class="col-sm-4">	
            <label for="weather">Weather</label>
            <div class="form-group salad" ui="droplist" id="weather">
                <div class="dropdown salad">
                    <button type="button" class="btn btn-default dropdown-toggle" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false"><span class="caret"></span></button>
                    <ul class="dropdown-menu" style="display: none;">
                        <li>
                            <a href="#" class="checkbox">
                                <input type="checkbox" id="g5" class="uui-form-element blue">
                                <label for="g5">Sun</label>
                            </a>
                        </li>
                        <li>
                            <a href="#" class="checkbox">
                                <input type="checkbox" id="g6" class="uui-form-element blue">
                                <label for="g6">Rain</label>
                            </a>
                        </li>
                        <li>
                            <a href="#" class="checkbox">
                                <input type="checkbox" id="g7" class="uui-form-element blue">
                                <label for="g7">Weather</label>
                            </a>
                        </li>
                        <li>
                            <a href="#" class="checkbox">
                                <input type="checkbox" id="g8" class="uui-form-element blue">
                                <label for="g8">Snow</label>
                            </a>
                        </li>
                    </ul>
                </div>
            </div>
        </div>
    </div>
    <div class="row overflow">
        <div class="col-sm-12">
            <div class="form-group">
                <label for="description">Description</label>
                <textarea class="uui-form-element" rows="4" cols="10" id="description"></textarea>
            </div>
            <div> 
                <input id="accept-conditions" type="checkbox" name="accept-conditions">
                <label for="accept-conditions">Accept conditions</label>
            </div>
        </div>
        <div class="col-sm-12 text-right">
            <button class="uui-button dark-blue" type="submit">Submit</button>
        </div>
    </div>
 </form>
```

Form is located in the following classes:

- __Java__: <a href="https://github.com/jdi-testing/jdi-light/tree/master/jdi-light/src/main/java/com/epam/jdi/light/elements/composite/Form.java">Form.java</a>
- __C#__:   <a href="https://github.com/jdi-testing/jdi-light-csharp/blob/master/JDI.Light/JDI.Light/Elements/Composite/Form.cs">Form.cs</a>

 ```java    
public class ContactFormCustom extends Form<Contacts> {
    @Mandatory TextField name;
    TextField lastName, position, passportNumber, passportSeria;

    Dropdown gender;
    IsCombobox religion;

    Checkbox passport, acceptConditions;
    TextArea description;

    @UI("['Submit']") public Button submit;
}

@Test
public void submitEntityToContactFormCustomTest() {
    main.contactFormCustom.submit(DEFAULT_CONTACT);
    main.contactFormCustom.check(DEFAULT_CONTACT);
    checkContactFormCustomSubmitted();
}

@Test
public void plainSubmitTest() {
    main.contactFormCustom.fill(DEFAULT_CONTACT);
    main.contactFormCustom.submit();
    main.contactFormCustom.check(DEFAULT_CONTACT);
    checkContactFormCustomSubmitted();
}

@Test
public void onlyMandatoryOptionTest() {
    main.contactFormCustom.onlyMandatory().fill(DEFAULT_CONTACT);
    main.contactFormCustom.onlyMandatory().check(DEFAULT_CONTACT);
    main.contactFormCustom.check(ONLY_NAME_FILLED_DEFAULT_CONTACT);
}

@Test
public void onlyOptionalOptionTest() {
    main.contactForm.onlyOptional().fill(DEFAULT_CONTACT);
    main.contactFormCustom.onlyOptional().check(ALL_EXCEPT_NAME_FILLED_DEFAULT_CONTACT);
}
 ```

Form is parameterized by an entity that corresponds to the form. For example, a login form can be parameterized by a user entity. The entity should extend DataClass class (parameterized by the entity itself).
The names of the entity fields should be exactly the same as the names of the form fields. All fields of the entity managed by the form should be Strings.

<br>
JDI Light allows you to define a form in three ways:
<br>

**By creating a normal JDI Light Form** - a typical Form in JDI with typified elements, @UI annotations, extending from Form.

<br>
**By using smart locators for a JDI Light Form** - Such Form utilizes the
 _Smart locator_ functionality of JDI. In this case there is no need to explicitly define
  locators for the form elements as such locators can be obtained implicitly from field names
   using Smart locator functionality.
[See more details and examples for Smart locators in documentation](https://jdi-docs.github.io/jdi-light/?java#smart-locators)

<br>

**If a Form consists of only TextFields and Buttons**, there is no need to define a Form UI Object.
Such form can be added directly to the related page or to the root Site class.
In this case the form field  will be taken from the entity that the form is being parameterized by.

<br>

**Form Filters**

In Java, Form has a **filter** property that defines which form elements will be filled/submited
or verified/checked. Filter can be set to either *ALL*, *MANDATORY* or *OPTIONAL*.

Based on this property, fill/submit and verify/check functions are applied to either all
form elements or only mandatory (only optional) form elements.

 <br>
 Mandatory form fields should be marked with *@Mandatory* annotation. Optional form fields are the ones without
  *@Mandatory* annotation. *ALL* is the default Form option.

  <br> 
 To set form filters 
  as *MANDATORY* or *OPTIONAL*, *onlyMandatory()* and *onlyOptional()* methods 
  should be used. They set the corresponding form filter option for a duration of a single
   action (all form action methods set the form filter option back to *ALL*).

<br>

**Form Actions**

In Java, Form also has a **FILL_ACTION** and **GET_ACTION** lambdas.
This defines how the Form should be filled and verified. The default behavior defined in the
Form class simply utilizes *setValue(String value)* method of the SetValue interface and
*getValue()* method of the HasValue interface.

However, these lambdas can be redefined in the _HtmlSettings_ class in order to customise the behavior
for "non-text" form elements such as Checkboxes (the behavior of custom elements is defined
by *@FillValue* and *@VerifyValue* annotations).

*FILL_ACTION* and *GET_ACTION* lambdas can also be further modified in order to customize
Form behavior, but it is important to take into account that behavior defined in the
HtmlSettings might be lost.

It is customary to reassign these lambdas before all the tests are run, for example in TestNG's *@BeforeSuite* method.

<br>
In Java, if fill/submit and verify/check methods need to be redefined for a specific form, it is possible to override **fillAction()** and **getAction()** for such form.

<br>
Methods available for Java in JDI Light:

|Method | Description | Return Type
--- | --- | ---
**add(T entity)** | Fills all settable elements and clicks “add” Button or ”addButton” | void
**back(T entity)** | Fills all settable elements and clicks “back” Button or ”backButton” | void
**cancel(T entity)** | Fills all settable elements and clicks “cancel” Button or ”cancelButton” | void
**check(T entity)** | Verifies that form has been filled correctly. If not, throws an exception | void
**close(T entity)** | Fills all settable elements and clicks “close” Button or ”closeButton” | void
**fill(T entity)** | Fills all settable elements of the form that can be matched with fields of the input entity | void
**fillAction(Field field, Object element, Object parent, String setValue)** | Defines the specifics of how form elements will be filled | void
**getAction(Field field, Object element, Object parent)** | Defines the specifics of how form elements will be obtained for verification and checks | String
**isDisplayed()** | Check that form is displayed | boolean
**isValid()** | Return that form is valid | boolean
**login()** | Clicks "login" Button or "loginButton"| void
**login(T entity)** | Fills all settable elements and clicks “login” Button or ”loginButton” | void
**loginAs(T entity)** | Fills all settable elements and clicks “login” Button or ”loginButton” | void
**next(T entity)** | Fills all settable elements and clicks “next” Button or ”nextButton” | void
**onlyMandatory()** | Sets form filter option to **MANDATORY**, meaning that only mandatory form elements are filled/submitted or verified/checked for the duration of a single form action | void
**onlyOptional()** | Sets form filter option to **OPTIONAL**, meaning that only optional form elements are filled/submitted or verified/checked for the duration of a single form action | void
**pressButton(String buttonName)** | Clicks “buttonName” Button or "buttonNamebutton". Allows different buttons to send one form, e.g. save/publish/cancel/search/update/... | void
**publish(T entity)** | Fills all settable elements and clicks “publish” Button or ”publishButton” | void
**save(T entity)** | Fills all settable elements and clicks “save” Button or ”saveButton” | void
**select(T entity)** | Fills all settable elements and clicks “select” Button or ”selectButton” | void
**search(T entity)** | Fills all settable elements and clicks “search” Button or ”searchButton” | void
**send()** | Sends the form by clicking “send” Button or "sendButton" | void
**send(T entity)** | Fills all settable elements and clicks “send” Button or ”sendButton” | void
**submit()** | Sends the form by clicking "submit" Button or "submitButton" | void
**submit(String text)** | Fills first settable form field with value and clicks "submit" Button or "submitButton"  | void
**submit(T entity)** | Fills all settable elements and clicks "submit" Button or "submitButton"  | void
**submit(String text, String buttonName)** | Fills first settable field with value and clicks “buttonName” Button or "buttonNamebutton"| void
**submit(T entity, String buttonName)** | Fills all settable elements and clicks “buttonName” Button or "buttonNamebutton" | void
**verify(T entity)** | Verifies that form has been filled correctly. If not, returns a list of keys where verification has failed | List<String>
**update(T entity)** | Fills all settable elements and clicks “update” Button or ”updateButton” | void

<a href="https://github.com/jdi-testing/jdi-light/blob/master/jdi-light-html-tests/src/test/java/io/github/epam/html/tests/elements/composite/FormTests.java" target="_blank">Test examples in Java</a>

<a href="https://github.com/jdi-testing/jdi-light-csharp/blob/master/JDI.Light/JDI.Light.Tests/Tests/Composite/FormTests.cs" target="_blank">Test examples in C#</a>

[BDD Steps example](https://jdi-docs.github.io/jdi-light/?java#form-2)

#### WebPage

**WebPage** - A parent Java class for all JDI Page Object classes. WebPage class extends _DriverBase_ class, implements PageObject interface and contains a number of commonly used methods:

**WebPage** is provided by JDI Light in:

- __Java__: _com.epam.jdi.light.elements.composite_

![WebPage](../images/html/webpage.png)

Methods available for Java in JDI Light:

```java 
public class ActionsWebPageTests extends TestsInit {

    @BeforeMethod
    public void before() {
        shouldBeLoggedIn();
        contactFormPage.shouldBeOpened();
        leftMenu.select("Contact form");
    }

    @Test
    public void getUrlTest() {
        Assert.assertEquals(WebPage.getUrl(), "https://jdi-testing.github.io/jdi-light/contacts.html");
    }

    @Test
    public void checkUrlPageTest() {
        contactFormPage.url().check();
    }

    @Test
    public void getTitleTest() {
        Assert.assertEquals(WebPage.getTitle(), "Contact Form");
    }

    @Test
    public void checkTitlePageTest() {
       contactFormPage.title().check();
    }

    @Test
    public void checkOpenedTest() {
        contactFormPage.checkOpened();
    }

    @Test
    public void isOpenedTest() {
        Assert.assertTrue(contactFormPage.isOpened());
    }

    @Test
    public void scrollToBottomTest() {
        WebPage.scrollToBottom();
    }

    @Test
    public void toStringTest() {
        Assert.assertEquals(contactFormPage.toString(), "StaticSite.contactFormPage (url=https://jdi-testing.github.io/jdi-light/contacts.html; title=Contact Form)");
    }
}
```

|Method | Description | Return Type
--- | --- | ---
**asForm()**|Returns new Form parameterized with local Name|Form<T>
**back()**|Go back to previous page|void
**checkOpened()**|Checks that page has opened|void
**forward()**|Go forward to next page|void
**getCurrentPage()**|Returns the name of current Page|String
**getHtml()**|Gets HTML of current page|String
**getTitle()**|Returns Page Title|String
**getUrl()**|Returns URL of Page|String
**isOpened()**|Checks that page has opened|boolean
**open(String url)**|Opens url specified for page|void
**open(Object... params)**|Opens url specified for page with parameters|void
**openedPage(String url)**|Checks that page has opened|void
**openSite()**|Opens a Site|void
**openSite(Class<?> site)**|Parameterized Site opening|void
**openUrl(String url)**|Opening WebPage with URL|void
**refresh()**|Reloads current page|void
**reload()**|Same as **refresh()**|void
**scroll(int x, int y)**|Scrolls to designated position|void
**scrollToTop()**|Scrolls to top|void
**scrollToBottom()**|Scrolls to bottom|void
**scrollDown(int value)**|Scrolls down to designated position|void
**scrollUp(int value)**|Scrolls up to designated position|void
**scrollRight(int value)**|Scrolls right to designated position|void
**scrollLeft(int value)**|Scrolls left to designated position|void
**setCurrentPage(WebPage page)**|Instantiates the current Page with Name|void
**setUrl(String uri)**|Setting Up URL of Page|void
**setUrl(String uri, String template, CheckTypes validate)**|Parameterized setting Up URL of Page|void
**shouldBeOpened()**|Checks that page has opened|void
**shouldBeOpened(Object... params)**|Checks that page has opened with parameters|void
**title()**|Returns new StringCheckType object with checked Title|StringCheckType
**toString()**|Overrides the Object class toString() method|String
**updatePageData(Url urlAnnotation, Title titleAnnotation)**|Setting Page URL and     |void
**url()**|Returns new StringCheckType object with checked URL|StringCheckType
**visualWindowCheck()**|empty|void
**WebPage()**|Default constructor for WebPage class|WebPage
**WebPage(String url)**|Parameterized URL constructor for WebPage class|WebPage
**WebPage(String url, String title)**|Parameterized with URL and Title constructor|WebPage
**windowScreenshot()**|Getting window screenshot|String
**xOffset()**|Getting window x offset|long
**yOffset()**|Getting window y offset|long
**zoom(double factor)**|Zooms current page|void
**zoomLevel()**|Getting zoom level|double

More than that, it has a nested **StringCheckType** class with the following methods:

|Method | Description | Return Type
--- | --- | ---
**check()**|Checks that current page url/title equals to expected url/title|boolean
**contains()**|Checks that current page url/title contains expected url/title-matcher|boolean
**match()**|Checks that current page url/title matches to expected url/title-matcher|boolean
**StringCheckType(Supplier<String> actual, String equals, String what)**|A parameterized constructor|StringCheckType

<a href="https://github.com/jdi-testing/jdi-light/blob/master/jdi-light-html-tests/src/test/java/io/github/epam/html/tests/elements/composite/webpage/ActionsWebPageTests.java" target="_blank">Test examples in Java</a>

[BDD Steps example](https://jdi-docs.github.io/jdi-light/?java#webpage-2)
