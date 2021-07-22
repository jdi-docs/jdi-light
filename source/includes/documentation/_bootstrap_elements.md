## Bootstrap elements
### Bootstrap Common elements

#### Checkboxes and radios

##### <a href="https://getbootstrap.com/docs/4.3/components/buttons/" target="_blank">Checkbox default</a>

Checkbox is located in the following classes:

- __Java__: _com.epam.jdi.light.ui.bootstrap.elements.common.Checkbox_


<!-- ![Checkbox default example](../../images/bootstrap/checkbox-default.png) -->

Here is an example with provided Bootstrap v4.3 code:

```java 
// @FindBy(css = "body") public static CheckboxesDefault checkboxesDefault;
@UI("body") public static CheckboxesDefault checkboxesDefault;

public class CheckboxesDefault extends Section {
    // @FindBy(css = "#check1") public Checkbox checkboxOne;
    @UI("#check1") public Checkbox checkboxOne; 
    // @FindBy(css = "#check2") public Checkbox checkboxTwo;
    @UI("#check1") public Checkbox checkboxTwo; 
}

@Test
public void isValidationTests() {
    checkboxesDefault.checkboxOne
            .is()
            .displayed()
            .enabled()
            .core()
            .hasClass("form-check")
            .tag(is("div"));
    checkboxesDefault.checkboxOne.label()
            .is()
            .displayed()
            .enabled()
            .core()
            .hasClass("form-check-label")
            .text(is("Default checkbox"))
            .tag(is("label"));
}

@Test
public void clickableTests() {
    checkboxesDefault.checkboxOne.check();
    checkboxesDefault.checkboxOne.is().selected();
    checkboxesDefault.checkboxOne.uncheck();
    checkboxesDefault.checkboxOne.is().deselected();
}
```

```html
<div class="form-check" id="check1">
    <input class="form-check-input" type="checkbox" value="" id="defaultCheck1">
    <label class="form-check-label" for="defaultCheck1">
        Default checkbox
    </label>
</div>
<div class="form-check" id="check2">
    <input class="form-check-input" type="checkbox" value="" id="defaultCheck2" disabled>
    <label class="form-check-label" for="defaultCheck2">
        Disabled checkbox
    </label>
</div>
```



|Method | Description | Return Type
--- | --- | ---
**assertThat()** | Assert action checkbox | CheckboxAssert
**click()** | Click the checkbox | void
**check(String)** | Set to checked on "true" (case insensitive) or unchecked otherwise | void
**check()** | Set to checked | void
**is()** | Assert action checkbox | CheckboxAssert
**isSelected()** | Verify value | boolean
**isEnabled()** | Verify state | boolean
**uncheck()** | Set to unchecked | void

<br>

<a href="https://github.com/jdi-testing/jdi-light/blob/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/composite/section/form/CheckboxesDefaultTests.java" target="_blank">Test examples in Java</a><br>

Button group is represented by Section class in Java:

[Section](https://jdi-docs.github.io/jdi-light/#section)

<br>

##### <a href="https://getbootstrap.com/docs/4.3/components/forms/#inline" target="_blank">Checkbox default inline</a>

Checkbox is located in the following classes:

- __Java__: _com.epam.jdi.light.ui.bootstrap.elements.common.Checkbox_


![Checkbox default inline example](../../images/bootstrap/checkbox-default-inline.png)

Here is an example with provided Bootstrap v4.3 code:

```java 
// @FindBy(css = "body") public static CheckboxesDefaultInline checkboxesDefaultInline;
@UI("body") public static CheckboxesDefaultInline checkboxesDefaultInline;

public class CheckboxesDefaultInline {
    // @FindBy(xpath = "//input[@id='inlineCheckbox1']/..") public Checkbox checkboxOne;
    @UI("//input[@id='inlineCheckbox1']/..") public Checkbox checkboxOne; 
    // @FindBy(xpath = "//input[@id='inlineCheckbox2']/..") public Checkbox checkboxTwo;
    @UI("//input[@id='inlineCheckbox2']/..") public Checkbox checkboxTwo; 
    // @FindBy(xpath = "//input[@id='inlineCheckbox3']/..") public Checkbox checkboxThree;
    @UI("//input[@id='inlineCheckbox3']/..") public Checkbox checkboxThree; 
}

@Test
public void isValidationTests() {
    checkboxesDefaultInline.checkboxOne
            .is()
            .displayed()
            .enabled()
            .core()
            .hasClass("form-check form-check-inline");
    checkboxesDefaultInline.checkboxOne.label()
            .is()
            .displayed()
            .enabled()
            .core()
            .hasClass("form-check-label")
            .text(is("1"));
}
@Test
public void clickableTests() {
    checkboxesDefaultInline.checkboxOne.check();
    checkboxesDefaultInline.checkboxOne
            .is()
            .selected();
    checkboxesDefaultInline.checkboxOne.uncheck();
    checkboxesDefaultInline.checkboxOne
            .is()
            .deselected();
    checkboxesDefaultInline.checkboxOne.label().click();
    checkboxesDefaultInline.checkboxOne
            .is()
            .selected();
}
```

```html
<div class="form-check form-check-inline">
    <input class="form-check-input" type="checkbox" id="inlineCheckbox1" value="option1">
    <label class="form-check-label" for="inlineCheckbox1">1</label>
</div>
<div class="form-check form-check-inline">
    <input class="form-check-input" type="checkbox" id="inlineCheckbox2" value="option2">
    <label class="form-check-label" for="inlineCheckbox2">2</label>
</div>
<div class="form-check form-check-inline">
    <input class="form-check-input" type="checkbox" id="inlineCheckbox3" value="option3"
           disabled>
    <label class="form-check-label" for="inlineCheckbox3">3 (disabled)</label>
</div>
```



|Method | Description | Return Type
--- | --- | ---
**assertThat()** | Assert action checkbox | CheckboxAssert
**click()** | Click the checkbox | void
**check(String)** | Set to checked on "true" (case insensitive) or unchecked otherwise | void
**check()** | Set to checked | void
**is()** | Assert action checkbox | CheckboxAssert
**isEnabled()** | Verify state | boolean
**isSelected()** | Verify value | boolean
**uncheck()** | Set to unchecked | void

<br>

<a href="https://github.com/jdi-testing/jdi-light/blob/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/composite/section/form/CheckboxesDefaultInlineTests.java" target="_blank">Test examples in Java</a>
<br>

Button group is represented by Section class in Java:

[Section](https://jdi-docs.github.io/jdi-light/#section)

<br>

##### <a href="https://getbootstrap.com/docs/4.3/components/forms/#default-stacked" target="_blank">Radio button</a>
Element that can be represented with one or more clickable buttons aiming to choose only one button of the group.

Radio button is located in the following classes:

- __Java__: _com.epam.jdi.light.ui.bootstrap.elements.complex.RadioButtons_


![Radio button example](../../images/bootstrap/radio-button.png)

Here is an example with provided Bootstrap v4.3 code:

```java 
//@FindBy(css = "#radio-buttons") public static RadioButtonGroup radioButtonGroup;
@UI("#radio-buttons") public static RadioButtonGroup radioButtonGroup;

public class RadioButtonGroup extends Section {
//@FindBy(css = "input[type='radio']")
@UI("input[type='radio']")
public RadioButtons radioButtons;
}

@Test
public void radioButtonByIndexTests() {
    radioButtonGroup.radioButtons.list().get(2).click();
    radioButtonGroup.radioButtons.list().get(2).is().selected();
    radioButtonGroup.radioButtons.list().is().selected(2);
    radioButtonGroup.radioButtons.is().selected(2);
    radioButtonGroup.radioButtons.list().get(1).is().deselected();
    radioButtonGroup.radioButtons.list().get(1).select();
    radioButtonGroup.radioButtons.list().get(1).is().selected();
    radioButtonGroup.radioButtons.list().is().selected(1);
    radioButtonGroup.radioButtons.list().get(2).is().deselected();
    radioButtonGroup.radioButtons.list().select(2);
    radioButtonGroup.radioButtons.list().get(2).is().selected();
}

@Test
public void radioButtonByLabelTests() {
    radioButtonGroup.radioButtons.list().select(labelText1);;
    radioButtonGroup.radioButtons.list().is().selected(labelText1);
    radioButtonGroup.radioButtons.is().selected(labelText1);
    radioButtonGroup.radioButtons.list().get(1).is().text(is(value1));
    radioButtonGroup.radioButtons.list().get(2).is().deselected();
    radioButtonGroup.radioButtons.list().get(2).label().click();
    radioButtonGroup.radioButtons.is().selected(labelText2);
    radioButtonGroup.radioButtons.list().get(2).is().text(is(value2));
    radioButtonGroup.radioButtons.list().get(1).is().deselected();
    radioButtonGroup.radioButtons.select(labelText1);
    radioButtonGroup.radioButtons.is().selected(labelText1);
    radioButtonGroup.radioButtons.list().get(2).is().deselected();
}
```

```html
<div class="btn-group-vertical mb-3" id="radio-buttons" role="group">
     <div class="form-check">
          <input class="form-check-input" type="radio" name="exampleRadios" id="exampleRadios1" value="option1" checked="">
          <label class="form-check-label" for="exampleRadios1">Default radio</label>
     </div>
     <div class="form-check">
          <input class="form-check-input" type="radio" name="exampleRadios" id="exampleRadios2" value="option2">
          <label class="form-check-label" for="exampleRadios2">Second default radio</label>
     </div>
     <div class="form-check">
           <input class="form-check-input" type="radio" name="exampleRadios" id="exampleRadios3" value="option3" disabled="">
           <label class="form-check-label" for="exampleRadios3">Disabled radio</label>
     </div>
</div>
```




|Method | Description | Return Type
--- | --- | ---
**assertThat()** | Assert action | TextAssert
**click()** | Click the button | void
**get()** | Select button by index | action
**getText()** | Get button text | String
**is()** | Assert action | TextAssert
**select()** | Select button | void
**selected()** | Radio button is selected | TextAssert

<br>

<a href="https://github.com/jdi-testing/jdi-light/blob/master/jdi-light-html-tests/src/test/java/io/github/epam/html/tests/elements/complex/RadioTests.java" target="_blank">Test examples in Java</a>
<br>

Button group is represented by Section class in Java:

[Section](https://jdi-docs.github.io/jdi-light/#section)

<br>

##### <a href="https://getbootstrap.com/docs/4.3/components/forms/#inline" target="_blank">Radio button inline</a>

Radio button is located in the following classes:

- __Java__: _com.epam.jdi.light.ui.bootstrap.elements.complex.RadioButtons_


![Radio button inline example](../../images/bootstrap/radio-default-inline.png)

Here is an example with provided Bootstrap v4.3 code:

```java 
//@FindBy(css = "body") public static RadioButtonsDefaultInline radioButtonsDefaultInline;
@UI("body") public static RadioButtonsDefaultInline radioButtonsDefaultInline;

public class RadioButtonsDefaultInline extends Section {
    //@FindBy(css = "input[name='inlineRadioOptions']")
    @UI("input[name='inlineRadioOptions']")
    public RadioButtons radioButtons;
}

@Test
public void baseInitTest() {
     radioButtonsDefaultInline.radioButtons.is().size(3);
     radioButtonsDefaultInline.radioButtons.list().get(1).is().deselected();
     radioButtonsDefaultInline.radioButtons.list().get(2).is().deselected();
     radioButtonsDefaultInline.radioButtons.list().get(3).is().deselected();
     radioButtonsDefaultInline.radioButtons.list().get(3).is().disabled();

     radioButtonsDefaultInline.radioButtons.list().get(1).label()
                .is()
                .core()
                .hasClass("form-check-label")
                .text(is(label1));
     radioButtonsDefaultInline.radioButtons.list().get(2).label()
                .is()
                .core()
                .hasClass("form-check-label")
                .text(is(label2));
     radioButtonsDefaultInline.radioButtons.list().get(3).label()
                .is()
                .core()
                .hasClass("form-check-label")
                .text(is(label3));
}

@Test
public void radioButtonByIndexTests() {
    radioButtonsDefaultInline.radioButtons.select(2);
    radioButtonsDefaultInline.radioButtons.is().selected(2);
    radioButtonsDefaultInline.radioButtons.is().selected("2");
    radioButtonsDefaultInline.radioButtons.list().get(2).is().selected();
    radioButtonsDefaultInline.radioButtons.list().get(1).is().deselected();
    radioButtonsDefaultInline.radioButtons.select(1);
    radioButtonsDefaultInline.radioButtons.is().selected(1);
    radioButtonsDefaultInline.radioButtons.is().selected("1");
    radioButtonsDefaultInline.radioButtons.list().get(2).is().deselected();
    radioButtonsDefaultInline.radioButtons.list().select("2");
    radioButtonsDefaultInline.radioButtons.list().get(2).is().selected();
}
```

```html 
<div class="form-check form-check-inline">
     <input class="form-check-input" type="radio" name="inlineRadioOptions" id="inlineRadio1" value="option1">
     <label class="form-check-label" for="inlineRadio1">1</label>
</div>
<div class="form-check form-check-inline">
     <input class="form-check-input" type="radio" name="inlineRadioOptions" id="inlineRadio2" value="option2">
     <label class="form-check-label" for="inlineRadio2">2</label>
</div>
<div class="form-check form-check-inline">
     <input class="form-check-input" type="radio" name="inlineRadioOptions" id="inlineRadio3" value="option3" disabled="">
     <label class="form-check-label" for="inlineRadio3">3 (disabled)</label>
</div>
```

|Method | Description | Return Type
--- | --- | ---
**assertThat()** | Assert action | TextAssert
**click()** | Click the button | void
**get()** | Select button by index | action
**getText()** | Get button text | String
**is()** | Assert action | TextAssert
**select()** | Select button | void
**selected()** | Radio button is selected | TextAssert

<br>

<a href="https://github.com/jdi-testing/jdi-light/blob/master/jdi-light-html-tests/src/test/java/io/github/epam/html/tests/elements/complex/RadioTests.java" target="_blank">Test examples in Java</a>
<br>

Button group is represented by Section class in Java:

[Section](https://jdi-docs.github.io/jdi-light/#section)

<br>
<br>
<br>

##### <a href="https://getbootstrap.com/docs/4.3/components/forms/#without-labels" target="_blank">Radio button and checkbox without labels</a>

Checkbox and Radio button are located in the following classes:

- __Java__: _com.epam.jdi.light.ui.bootstrap.elements.complex.RadioButtons_
- __Java__: _com.epam.jdi.light.ui.bootstrap.elements.common.Checkbox_


![Radio button and checkbox without labels example](../../images/bootstrap/default-without-labels.png)

Here is an example with provided Bootstrap v4.3 code:

```java 
//@FindBy(css = "body")
@UI("body") 
public static CheckboxesAndRadiosWithoutLabels checkboxesAndRadiosWithoutLabels;

//@FindBy(xpath = "//input[@id='blankCheckbox']/..")
@UI("//input[@id='blankCheckbox']/..")
public Checkbox checkbox;
//@FindBy(css = "#blankRadio1")
@UI("#blankRadio1")
public RadioButtons radioButtons;
}

@Test
public void isValidationTests() {
    checkboxesAndRadiosWithoutLabels.checkbox
            .is()
            .displayed()
            .enabled()
            .core()
            .hasClass("form-check")
            .tag(is("div"));
    checkboxesAndRadiosWithoutLabels.radioButtons
            .is()
            .displayed()
            .enabled()
            .core()
            .value("option1")
            .attr("type", "radio")
            .attr("aria-label", "...");
}

@Test
public void checkboxClickableTests() {
    checkboxesAndRadiosWithoutLabels.checkbox.check();
    checkboxesAndRadiosWithoutLabels.checkbox
            .is()
            .selected();
    checkboxesAndRadiosWithoutLabels.checkbox.uncheck();
    checkboxesAndRadiosWithoutLabels.checkbox
            .is()
            .deselected();
}

@Test
public void radioButtonTests() {
    checkboxesAndRadiosWithoutLabels.radioButtons.select(1);
    checkboxesAndRadiosWithoutLabels.radioButtons.list()
             .is()
             .selected(1);
    checkboxesAndRadiosWithoutLabels.radioButtons
             .is()
             .selected(1);
}
```

```html
<div class="form-check">
     <input class="form-check-input position-static" type="checkbox" id="blankCheckbox" value="option1" aria-label="...">
</div>
<div class="form-check">
      <input class="form-check-input position-static" type="radio" name="blankRadio" id="blankRadio1" value="option1" aria-label="...">
</div>
``` 

|Method | Description | Return Type
--- | --- | ---
**assertThat()** | Assert action | TextAssert
**check()** | Click the element | void
**click()** | Click the element | void
**is()** | Assert action | TextAssert

<br>
<a href="https://github.com/jdi-testing/jdi-light/blob/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/composite/section/form/CheckboxesAndRadiosWithoutLabelsTests.java" target="_blank">Test examples in Java</a>
<br>

Button group is represented by Section class in Java:

[Section](https://jdi-docs.github.io/jdi-light/#section)

<br><br><br><br><br><br>
##### <a href="https://getbootstrap.com/docs/4.3/components/forms/#checkboxes" target="_blank">Checkbox custom</a>
Checkbox is located in the following classes:

- __Java__: _com.epam.jdi.light.ui.bootstrap.elements.common.Checkbox_


![Checkbox custom example](../../images/bootstrap/checkbox-custom.png)

Here is an example with provided Bootstrap v4.3 code:

```java 
// @FindBy(css = "body") public static CheckboxesCustom checkboxesCustom;
@UI("body") public static CheckboxesCustom checkboxesCustom;

public class CheckboxesCustom extends Section {
    // @FindBy(css = "#customCheck1-div") public Checkbox checkbox;
    @UI("#customCheck1-div") public Checkbox checkbox; 
}

@Test
public void isValidationTests() {
    checkboxesCustom.checkbox
            .is()
            .displayed()
            .enabled()
            .core()
            .hasClass("custom-control custom-checkbox")
            .tag(is("div"));
    checkboxesCustom.checkbox.label()
            .is()
            .displayed()
            .enabled()
            .core()
            .hasClass("custom-control-label")
            .text(is("Check this custom checkbox"))
            .tag(is("label"));
}

@Test
public void clickableTests() {
    checkboxesCustom.checkbox.check();
    checkboxesCustom.checkbox.is().selected();
    checkboxesCustom.checkbox.click();
    checkboxesCustom.checkbox.is().deselected();
}
```

```html
<div class="custom-control custom-checkbox" id="customCheck1-div">
    <input type="checkbox" class="custom-control-input" id="customCheck1">
    <label class="custom-control-label" for="customCheck1">Check this custom checkbox</label>
</div>
```


|Method | Description | Return Type
--- | --- | ---
**assertThat()** | Assert action checkbox | CheckboxAssert
**check(String)** | Set to checked on "true" (case insensitive) or unchecked otherwise | void
**check()** | Set to checked | void
**click()** | Click the checkbox | void
**is()** | Assert action checkbox | CheckboxAssert
**isSelected()** | Verify value | boolean
**isEnabled()** | Verify state | boolean
**uncheck()** | Set to unchecked | void

<br>
<a href="https://github.com/jdi-testing/jdi-light/blob/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/common/CustomCheckboxTests.java" target="_blank">Test examples in Java</a>
<br>

Button group is represented by Section class in Java:

[Section](https://jdi-docs.github.io/jdi-light/#section)

<br>

##### <a href="https://getbootstrap.com/docs/4.3/components/forms/#radios" target="_blank">Radio button custom</a>

Radio button is located in the following classes:

- __Java__: _com.epam.jdi.light.ui.bootstrap.elements.complex.RadioButtons_


![Radio button custom example](../../images/bootstrap/custom-radio.png)

Here is an example with provided Bootstrap v4.3 code:

```java 
public class RadioButtonsCustom extends Section {
    //@FindBy(css = "[name='customRadio']")
    @UI("[name='customRadio']")
    public RadioButtons radioButtons;
}

@Test
public void radioButtonByIndexTests() {
   radioButtonCustom.radioButtons.list().get(1).select();
   radioButtonCustom.radioButtons.list().get(1).core().waitFor().selected();
   radioButtonCustom.radioButtons.list().get(1).is().selected();
   radioButtonCustom.radioButtons.list().get(2).is().deselected();
   radioButtonCustom.radioButtons.list().get(2).select();
   radioButtonCustom.radioButtons.list().get(2).core().waitFor().selected();
   radioButtonCustom.radioButtons.list().get(2).is().selected();
   radioButtonCustom.radioButtons.list().select(label1);
   radioButtonCustom.radioButtons.list().is().selected(label1);
   radioButtonCustom.radioButtons.list().get(2).is().deselected();
   radioButtonCustom.radioButtons.list().get(1).click();
   radioButtonCustom.radioButtons.list().get(1).is().selected();
   radioButtonCustom.radioButtons.list().get(2).is().deselected();
}

@Test
public void radioButtonByIndexInSelectTests() {
   radioButtonCustom.radioButtons.select(1);
   radioButtonCustom.radioButtons.is().selected(label1);
   radioButtonCustom.radioButtons.select(2);
   radioButtonCustom.radioButtons.is().selected(label2);
   radioButtonCustom.radioButtons.select(label1);
   radioButtonCustom.radioButtons.is().selected(label1);
   radioButtonCustom.radioButtons.is().selected(1);
   radioButtonCustom.radioButtons.select(label2);
   radioButtonCustom.radioButtons.is().selected(2);
}
```

```html
<div class="html-left" id="custom-radio-con">
    <div class="custom-control custom-radio" id="customRadio1-div">
         <input type="radio" id="customRadio1" name="customRadio" class="custom-control-input">
         <label class="custom-control-label" for="customRadio1">Toggle this custom radio</label>
    </div>
    <div class="custom-control custom-radio" id="customRadio2-div">
        <input type="radio" id="customRadio2" name="customRadio" class="custom-control-input">
        <label class="custom-control-label" for="customRadio2">Or toggle this other custom radio</label>
    </div>
</div>
```

|Method | Description | Return Type
--- | --- | ---
**assertThat()** | Assert action | TextAssert
**click()** | Click the button | void
**get()** | Select button by index | action
**getText()** | Get button text | String
**is()** | Assert action | TextAssert
**select()** | Select button | void
**selected()** | Radio button is selected | TextAssert

<br>
<a href="https://github.com/jdi-testing/jdi-light/blob/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/composite/section/form/RadioButtonCustomTests.java" target="_blank">Test examples in Java</a>
<br>

Button group is represented by Section class in Java:

[Section](https://jdi-docs.github.io/jdi-light/#section)

<br>

##### <a href="https://getbootstrap.com/docs/4.3/components/forms/#inline-1" target="_blank">Radio button custom inline</a>

Radio button is located in the following classes:

- __Java__: _com.epam.jdi.light.ui.bootstrap.elements.complex.RadioButtons_


![Radio button custom inline example](../../images/bootstrap/custom-radio-inline.png)

Here is an example with provided Bootstrap v4.3 code:

```java 
// @FindBy(css = "body") public static RadioButtonsCustomInline radioButtonsCustomInline;
@UI("body") public static RadioButtonsCustomInline radioButtonsCustomInline;

public class RadioButtonsCustomInline extends Section {
    //@FindBy(css = ".custom-control-inline .custom-control-input")
    @UI(".custom-control-inline .custom-control-input")
    public RadioButtons radioButtons;
}

@Test
public void radioButtonByIndexTests() {
    radioButtonsCustomInline.radioButtons.select(1);
    radioButtonsCustomInline.radioButtons.is().selected(1);
    radioButtonsCustomInline.radioButtons.list().get(2).select();
    radioButtonsCustomInline.radioButtons.list().is().selected(2);
    radioButtonsCustomInline.radioButtons.list().get(2).is().selected();
    radioButtonsCustomInline.radioButtons.list().get(1).click();
    radioButtonsCustomInline.radioButtons.list().get(1).is().selected();
    radioButtonsCustomInline.radioButtons.list().get(2).is().deselected();
}

@Test
public void radioButtonByLabelTests() {
    radioButtonsCustomInline.radioButtons.list().get(1).label().click();
    radioButtonsCustomInline.radioButtons.is().selected(1);
    radioButtonsCustomInline.radioButtons.list().get(2).label().click();
    radioButtonsCustomInline.radioButtons.is().selected(2);
    radioButtonsCustomInline.radioButtons.list().get(1).label().click();
    radioButtonsCustomInline.radioButtons.is().selected(text1);
    radioButtonsCustomInline.radioButtons.list().is().selected(text1);
    radioButtonsCustomInline.radioButtons.select(text2);
    radioButtonsCustomInline.radioButtons.list().is().selected(text2);
    radioButtonsCustomInline.radioButtons.list().get(1).label().is().text(text1);
    radioButtonsCustomInline.radioButtons.list().get(2).label().is().text(text2);
}
```

```html 
<div class="custom-control custom-radio custom-control-inline" id="customRadioInline1-div">
     <input type="radio" id="customRadioInline1" name="customRadioInline1" class="custom-control-input">
     <label class="custom-control-label" for="customRadioInline1">Toggle this <br> custom
                                    radio</label>
</div>
<div class="custom-control custom-radio custom-control-inline" id="customRadioInline2-div">
      <input type="radio" id="customRadioInline2" name="customRadioInline1" class="custom-control-input">
      <label class="custom-control-label" for="customRadioInline2">Or toggle this <br> custom
                                    radio</label>
</div>
```

|Method | Description | Return Type
--- | --- | ---
**assertThat()** | Assert action | TextAssert
**click()** | Click the button | void
**get()** | Select button by index | action
**getText()** | Get button text | String
**is()** | Assert action | TextAssert
**select()** | Select button | void
**selected()** | Radio button is selected | TextAssert

<br>
<a href="https://github.com/jdi-testing/jdi-light/blob/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/composite/section/form/RadioButtonsCustomInlineTests.java" target="_blank">Test examples in Java</a>
<br>

Button group is represented by Section class in Java:

[Section](https://jdi-docs.github.io/jdi-light/#section)

<br>

##### <a href="https://getbootstrap.com/docs/4.3/components/forms/#inline-1" target="_blank">Custom disabled</a>

Checkbox and Radio button is located in the following classes:

__Java__:
- com.epam.jdi.light.ui.bootstrap.elements.complex.RadioButtons_
- com.epam.jdi.light.ui.bootstrap.elements.common.Checkbox_


![Custom disabled example](../../images/bootstrap/custom-disabled.png)

Here is an example with provided Bootstrap v4.3 code:

```java 
// @FindBy(css = "body") public static CheckboxAndRadioButtonCustomDisabled checkboxAndRadioButtonCustomDisabled;
@UI("body") public static CheckboxAndRadioButtonCustomDisabled checkboxAndRadioButtonCustomDisabled;

    public class CheckboxAndRadioButtonCustomDisabled extends Section {
        //FindBy(css = "#customCheckDisabled1-div")
        @UI("#customCheckDisabled1-div")
        public Checkbox checkbox;
        //FindBy(css = "#customRadioDisabled2")
        @UI("#customRadioDisabled2")
        public RadioButtons radioButtons;
    }

    @Test
    public void radioButtonIsValidationTests() {
        checkboxAndRadioButtonCustomDisabled.radioButtons.list().get(1).is()
            .hidden()
            .disabled()
            .core()
            .attr("type", "radio")
            .attr("name", "radioDisabled")
            .hasClass("custom-control-input")
            .tag(Matchers.is("input"));
    }

    @Test
    public void baseInitTest() {
        checkboxAndRadioButtonCustomDisabled.radioButtons.is().size(1);
        checkboxAndRadioButtonCustomDisabled.radioButtons.list().get(1)
                .is()
                .deselected();
        checkboxAndRadioButtonCustomDisabled.radioButtons.list().get(1).label()
                .is()
                .text(is(label1));
    }
```

```html
<div class="custom-control custom-checkbox" id="customCheckDisabled1-div">
    <input type="checkbox" class="custom-control-input" id="customCheckDisabled1" disabled="">
    <label class="custom-control-label" for="customCheckDisabled1">Check this custom checkbox</label>
</div>
<div class="custom-control custom-radio" id="customRadioDisabled2-div">
    <input type="radio" name="radioDisabled" id="customRadioDisabled2" class="custom-control-input" disabled="">
    <label class="custom-control-label" for="customRadioDisabled2">Toggle this custom radio</label>
</div>
```


|Method | Description | Return Type
--- | --- | ---
**assertThat()** | Assert action | TextAssert
**check()** | Click the element | void
**click()** | Click the element | void
**is()** | Assert action | TextAssert

<br>
<a href="https://github.com/jdi-testing/jdi-light/tree/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/composite/section/form/CheckboxAndRadioButtonCustomDisabledTests.java" target="_blank">Test examples in Java</a>
<br>

Button group is represented by Section class in Java:

[Section](https://jdi-docs.github.io/jdi-light/#section)

<br>

##### <a href="https://getbootstrap.com/docs/4.3/components/forms/#inline-1" target="_blank">Switches custom</a>

Checkbox is located in the following classes:

- __Java__: _com.epam.jdi.light.ui.bootstrap.elements.common.Checkbox_


![Switches custom example](../../images/bootstrap/switches.png)

Here is an example with provided Bootstrap v4.3 code:

```java 
// @FindBy(css = "body") public static Switches switches;
@UI("body") public static Switches switches; 

public class Switches extends Section {
    // @FindBy(css = "#customSwitch1-div") public Checkbox checkbox;
    @UI("#customSwitch1-div") public Checkbox checkbox; 
    // @FindBy(css = "#customSwitch2-div") public Checkbox checkboxDisabled;
    @UI("#customSwitch2-div") public Checkbox checkboxDisabled; 
}

@Test
public void isValidationTests() {
    switches.checkbox
            .is()
            .displayed()
            .enabled()
            .core()
            .hasClass("custom-control custom-switch")
            .tag(is("div"));
    switches.checkbox.label()
            .is()
            .displayed()
            .enabled()
            .core()
            .hasClass("custom-control-label")
            .text(is("Toggle this switch element"))
            .tag(is("label"));
}

@Test
public void clickableTests() {
    switches.checkbox.check();
    switches.checkbox.is().selected();
    switches.checkbox.check();
    switches.checkbox.is().deselected();
}
```

```html
<div class="custom-control custom-switch" id="customSwitch1-div">
    <input type="checkbox" class="custom-control-input" id="customSwitch1">
    <label class="custom-control-label" for="customSwitch1">Toggle this switch
        element</label>
</div>
<div class="custom-control custom-switch" id="customSwitch2-div">
    <input type="checkbox" class="custom-control-input" disabled id="customSwitch2">
    <label class="custom-control-label" for="customSwitch2">Disabled switch element</label>
</div>
```



|Method | Description | Return Type
--- | --- | ---
**assertThat()** | Assert action checkbox | CheckboxAssert
**check(String)** | Set to checked on "true" (case insensitive) or unchecked otherwise | void
**check()** | Set to checked | void
**click()** | Click the checkbox | void
**is()** | Assert action checkbox | CheckboxAssert
**isEnabled()** | Verify state | boolean
**isSelected()** | Verify value | boolean
**uncheck()** | Set to unchecked | void

<br>
<a href="https://github.com/jdi-testing/jdi-light/tree/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/composite/section/form/SwitchesTests.java" target="_blank">Test examples in Java</a>
<br>

Button group is represented by Section class in Java:

[Section](https://jdi-docs.github.io/jdi-light/#section)

<br>

#### Button group

<a href="https://getbootstrap.com/docs/4.3/components/button-group/" target="_blank">Button group</a> – Element that groups a series of buttons together on a single line with the button group, and super-power them with JavaScript.

Button group is located in the following packages:

- __Java__: _io.github.epam.bootstrap.tests.composite.section.buttonGroup_
- __C#__:

<br>

Button group is represented by Section class in Java:

[Section](https://jdi-docs.github.io/jdi-light/#section)

##### <a href="https://getbootstrap.com/docs/4.3/components/button-group/#basic-example" target="_blank">Button Group Basic</a>
Wrap a series of buttons with .btn in .btn-group.

![Button Group Basic Example HTML](../../images/bootstrap/bgroup-basic-example-screen.png)

Here is an example with provided Bootstrap v4.3 code:

```java 
// @FindBy(css = "#basic-example") public static ButtonGroupBasic buttonGroupBasic;
@UI("#basic-example") 
public static ButtonGroupBasic buttonGroupBasic;

public class ButtonGroupBasic extends Section {
    @UI("//button[text()='Left']") 
    public Button leftButton;
    
    @UI("//button[text()='Middle']") 
    public Button middleButton;
    
    @UI("//button[text()='Right']") 
    public Button rightButton;
}

@Test
public void leftButtonTests() {
    buttonGroupBasic.leftButton.is()
            .displayed()
            .enabled()
            .core()
            .hasClass("btn btn-secondary")
            .css("font-size", "16px");
    buttonGroupBasic.leftButton.click();
    validateAlert(is(leftButtonClickAlert));
}
```

<br>

<!-- ![Button Group Basic Example Example](../../images/bootstrap/bgroup-basic-example-html.png) -->
```html
<div id="btn-md-group" class="btn-group mb-3" role="group" aria-label="Default button group">
    <button type="button" class="btn btn-secondary" ondblclick="alert('Left Button Double Clicked!');"
            oncontextmenu="alert('Left Button Right Clicked!');">Left
    </button>
    <button type="button" class="btn btn-secondary" ondblclick="alert('Middle Button Double Clicked!');"
            oncontextmenu="alert('Middle Button Right Clicked!');">Middle
    </button>
    <button type="button" class="btn btn-secondary" ondblclick="alert('Right Button Double Clicked!');"
            oncontextmenu="alert('Right Button Right Clicked!');">Right
    </button>
</div>
```

<br>

Available methods in Java JDI Light:

|Method | Description | Return Type
--- | --- | ---
**assertThat()** | Assert action | TextAssert
**click()** | Click the button | void
**displayed()** | Check that element is displayed | TextAssert
**enabled()** | Check that element is enabled | TextAssert
**getText()** | Get button text | String
**is()** | Assert action | TextAssert

<br>

<a href="https://github.com/jdi-testing/jdi-light/blob/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/composite/section/buttonGroup/BasicTests.java" target="_blank">Button Group Basic Tests Example</a>


##### <a href="https://getbootstrap.com/docs/4.0/components/button-group/#button-toolbar" target="_blank">Button toolbar</a>
Combine sets of button groups into button toolbars for more complex components. Use utility classes as needed to space out groups, buttons, and more.

![Button toolbar](../../images/bootstrap/button_toolbar.png)

Here is an example with provided Bootstrap v4.3 code:

```java 
// @FindBy(css = ".btn-toolbar") public static ButtonToolbar buttonToolbar;
@UI(".btn-toolbar") 
public static ButtonToolbar buttonToolbar;

public class ButtonGroupToolbar extends Section {
    @UI("button") 
    public WebList buttonsInToolbar;
    
    @UI("input") 
    public TextField inputAreaInToolbar;

    @Test
    public void buttonsInButtonToolbarTest() {
        buttonToolbar.buttonsInToolbar.forEach(button -> {
            button.is().displayed();
            button.is().enabled();
            button.assertThat().css("background-color", backgroundColorBeforeHovering);
            button.core().hover();
            button.assertThat().css("background-color", backgroundColorAfterHovering);
            button.assertThat().css("border-color", borderColorBeforeClicking);
            button.click();
            validateAlert(containsString("button is clicked"));
            button.assertThat().css("border-color", borderColorAfterClicking);
        });
    }
}
```

<!-- ![Button toolbar example](../../images/bootstrap/button_toolbar-html.png) -->

```html

<div class="btn-toolbar" id="buttonToolbar1" role="toolbar" aria-label="Toolbar with button groups">
    <div class="btn-group mr-2" role="group" aria-label="First group">
        <button type="button" class="btn btn-secondary" onclick="alert('1st button is clicked');">1
        </button>
        <button type="button" class="btn btn-secondary" onclick="alert('2nd button is clicked');">2
        </button>
        <button type="button" class="btn btn-secondary" onclick="alert('3rd button is clicked');">3
        </button>
        <button type="button" class="btn btn-secondary" onclick="alert('4th button is clicked');">4
        </button>
    </div>
    <div class="btn-group mr-2" role="group" aria-label="Second group">
        <button type="button" class="btn btn-secondary" onclick="alert('5th button is clicked');">5
        </button>
        <button type="button" class="btn btn-secondary" onclick="alert('6th button is clicked');">6
        </button>
        <button type="button" class="btn btn-secondary" onclick="alert('7th button is clicked');">7
        </button>
    </div>
    <div class="btn-group" role="group" aria-label="Third group">
        <button type="button" class="btn btn-secondary" onclick="alert('8th button is clicked');">8
        </button>
    </div>
</div>

```


It is possible to mix input groups with button groups in your toolbars.

![Button toolbar_mixed](../../images/bootstrap/button_toolbar_mixed.png)

Here is an example with provided Bootstrap v4.3 code:

```java 
    @Test
    public void inputFieldInButtonToolbarTest() {
        buttonToolbar.inputAreaInToolbar.is().displayed();
        buttonToolbar.inputAreaInToolbar.is().enabled();
        buttonToolbar.inputAreaInToolbar.is().core().attr("placeholder", placeholderForInputField);
        buttonToolbar.inputAreaInToolbar.setValue(textForTestingInputField);
        assertEquals(buttonToolbar.inputAreaInToolbar.getValue(), textForTestingInputField);
    }
``` 

```html
<div class="btn-toolbar mb-3" id="buttonToolbar2" role="toolbar"
     aria-label="Toolbar with button groups">
    <div class="btn-group mr-2" role="group" aria-label="First group">
        <button type="button" class="btn btn-secondary"
                onclick="alert('1st button is clicked');">1
        </button>
    </div>
    <div class="input-group">
        <div class="input-group-prepend">
            <div class="input-group-text" id="btnGroupAddon">@</div>
        </div>
        <input type="text" class="form-control" placeholder="Input group example"
               aria-label="Input group example" aria-describedby="btnGroupAddon">
    </div>
</div>
```

Available methods in Java JDI Light:

|Method | Description | Return Type
--- | --- | ---
**assertThat()** | Assert action | TextAssert
**click()** | Click the button | void
**displayed()** | Check that element is displayed | TextAssert
**enabled()** | Check that element is enabled | TextAssert
**getText()** | Get button text | String
**is()** | Assert action | TextAssert

<br>

<a href="https://github.com/jdi-testing/jdi-light/blob/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/composite/section/buttonGroup/ToolbarTests.java" target="_blank">Bootstrap test examples</a>


##### <a href="https://getbootstrap.com/docs/4.0/components/button-group/#sizing" target="_blank">Button Group Sizing</a>

Instead of applying button sizing classes to every button in a group,
just add ``.btn-group-*`` to each ``.btn-group``, including each one when nesting multiple groups.

![Button Group Sizing Example](../../images/bootstrap/bgroup-sizing.png)

```java 
@UI("#btn-lg-group") // @FindBy(id = "btn-lg-group")
public static ButtonGroupSizing largeBtnGroup;

public class ButtonGroupSizing extends Section { 
    @UI("//button[contains(text(), 'Left')]")
    public Button leftBtn;
    
    @UI("//button[contains(text(), 'Middle')]")
    public Button midBtn;
    
    @UI("//button[contains(text(), 'Right')]")
    public Button rightBtn;
    
    String leftBtnText = "Left";
    
    @Test
    public void isValidationTest() {
        largeBtnGroup.highlight();
        largeBtnGroup.is().displayed();
        largeBtnGroup.is().enabled();
        largeBtnGroup.leftBtn.is().text(is(leftBtnText));
        largeBtnGroup.leftBtn.is().text(containsString("Le"));
        assertThat(largeBtnGroup.leftBtn.core().css("font-size"), is("20px"));
        largeBtnGroup.leftBtn.assertThat().displayed()
                .and().text(is(leftBtnText))
                .core()
                .css("font-size", is("20px"))
                .cssClass("btn btn-secondary")
                .attr("type", "button")
                .tag(is("button"));
    }
}
``` 

Here is an example with provided Bootstrap v4.3 code:

```html
<div id="btn-lg-group" class="btn-group btn-group-lg mb-3" role="group"
     aria-label="Large button group">
    <button type="button" class="btn btn-secondary"
            onclick="alert('Lg Left Button Clicked!');"
            ondblclick="alert('Lg Left Button Double Clicked!');"
            oncontextmenu="alert('Lg Left Button Right Clicked!');">Left
    </button>
    <button type="button" class="btn btn-secondary"
            onclick="alert('Lg Middle Button Clicked!');"
            ondblclick="alert('Lg Middle Button Double Clicked!');"
            oncontextmenu="alert('Lg Middle Button Right Clicked!');">Middle
    </button>
    <button type="button" class="btn btn-secondary"
            onclick="alert('Lg Right Button Clicked!');"
            ondblclick="alert('Lg Right Button Double Clicked!');"
            oncontextmenu="alert('Lg Right Button Right Clicked!');">Right
    </button>
</div>
```

Available methods in Java JDI Light:

|Method | Description | Return Type
--- | --- | ---
**assertThat()** | Assert action | TextAssert
**click()** | Click the button | void
**displayed()** | Check that element is displayed | TextAssert
**enabled()** | Check that element is enabled | TextAssert
**getText()** | Get button text | String
**is()** | Assert action | TextAssert

<br>

<a href="https://github.com/jdi-testing/jdi-light/blob/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/composite/section/buttonGroup/SizingTests.java" target="_blank">Bootstrap test examples</a>


##### <a href="https://getbootstrap.com/docs/4.3/components/button-group/#nesting" target="_blank">Button Group Nesting</a>
Place a ``.btn-group`` within another ``.btn-group`` when you want dropdown menus mixed with a series of buttons.

![Button Group Nesting Example](../../images/bootstrap/bgroup-nesting.png)

Here is an example with provided Bootstrap v4.3 code:

```java 
// @FindBy(css = "#button-group-nesting") public static ButtonGroupNesting buttonGroupNesting;
@UI("#button-group-nesting") 
public static ButtonGroupNesting buttonGroupNesting;

public class ButtonGroupNesting extends Section {
    @UI("button[onclick*='Button 1']") 
    public Button one;
    
    @UI("button[onclick*='Button 2']") 
    public Button two;
    
    @JDropdown(expand = ".btn-group",
            value = ".dropdown-menu",
            list = ".dropdown-item")
    public Dropdown dropdownMenu;
}

@Test
 public void buttonOneTests() {
     buttonGroupNesting.one.is()
             .displayed()
             .enabled()
             .core()
             .hasClass("btn btn-secondary")
             .css("font-size", "16px");
     buttonGroupNesting.one.click();
     validateAlert(is(buttonOneClickAlert));
}

@Test
public void dropdownMenuTests() {
    buttonGroupNesting.dropdownMenu.expand();
    buttonGroupNesting.dropdownMenu.is().expanded();
    buttonGroupNesting.dropdownMenu.is().size(2);
    buttonGroupNesting.dropdownMenu.list().get(0).is().text(dropdownMenuLinkOne);
    buttonGroupNesting.dropdownMenu.select(dropdownMenuLinkOne);
    newWindowTitleCheck(linkOnePageTitle);
}
```

<br>

```html
<div class="btn-group" id="button-group-nesting" role="group"
     aria-label="Button group with nested dropdown">
    <button type="button" class="btn btn-secondary" onclick="alert('Button 1 Clicked!');">
        1
    </button>
    <button type="button" class="btn btn-secondary" onclick="alert('Button 2 Clicked!');">
        2
    </button>

    <div class="btn-group" role="group">
        <button id="btnGroupDr1" type="button" class="btn btn-secondary dropdown-toggle"
                data-toggle="dropdown" aria-haspopup="true" aria-expanded="false">
            Dropdown
        </button>
        <div class="dropdown-menu" aria-labelledby="btnGroupDr1">
            <a class="dropdown-item" href="https://github.com/jdi-testing/jdi-light"
               target="_blank">JDI Github</a>
            <a class="dropdown-item"
               href="https://jdi-docs.github.io/jdi-light/#jdi-light-framework"
               target="_blank">JDI Docs</a>
        </div>
    </div>
</div>
```
<br>

|Method | Description | Return Type
--- | --- | ---
**assertThat()** | Assert action | TextAssert
**click()** | Click the button | void
**displayed()** | Check that element is displayed | TextAssert
**enabled()** | Check that element is enabled | TextAssert
**expand()** | Dropdown expand | void
**expanded()** | Check that dropdown is expanded | TextAssert
**getText()** | Get button text | String
**getValue()** | Get button value | String
**is()** | Assert action | TextAssert
**select(String option)** | Select option by text | void
**select(int option)** | Select option by index | void
<br>

Inner elements represented by the following classes:
<ul>
    <li> [Text](https://jdi-docs.github.io/jdi-light/#text) </li>
    <li> [Button](https://jdi-docs.github.io/jdi-light/#button)</li>
    <li> [Dropdown](https://jdi-docs.github.io/jdi-light/#dropdown-2)</li>
</ul>

<a href="https://github.com/jdi-testing/jdi-light/blob/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/composite/section/buttonGroup/NestingTests.java" target="_blank">Button Group Nesting Tests Example</a>

<br>


##### <a href="https://getbootstrap.com/docs/4.3/components/button-group/#vertical-variation" target="_blank">Button Group Vertical Variation</a>
Make a set of buttons appear vertically stacked rather than horizontally.

![Button Group Nesting Example](../../images/bootstrap/bgroup-vertical-variation.png)

Here is an example with provided Bootstrap v4.3 code:

```java 
// @FindBy(css = "#vertical-variation") public static  ButtonGroupVerticalVariation buttonGroupVerticalVariation;
@UI("#vertical-variation") 
public static  ButtonGroupVerticalVariation buttonGroupVerticalVariation;

public class ButtonGroupVerticalVariation extends Section {
    @UI("button[onclick*='Button One']") 
    public Button buttonOne;
    
    @UI("button[onclick*='Button Two']") 
    public Button buttonTwo;
    
    @JDropdown(expand = ".btn-group",
            value = ".dropdown-menu",
            list = ".dropdown-item")
    public Dropdown dropdownMenu;
}

@Test
public void buttonOneTests() {
    buttonGroupVerticalVariation.buttonOne.is()
            .displayed()
            .enabled()
            .core()
            .hasClass("btn btn-secondary")
            .css("font-size", "16px");
    buttonGroupVerticalVariation.buttonOne.click();
    validateAlert(is(buttonOneClickAlert));

@Test
public void dropdownMenuTests() {
    buttonGroupVerticalVariation.dropdownMenu.expand();
    buttonGroupVerticalVariation.dropdownMenu.is().expanded();
    buttonGroupVerticalVariation.dropdownMenu.is().size(2);
    buttonGroupVerticalVariation.dropdownMenu.list().get(1).is().text(dropdownMenuLinkTwo);
    buttonGroupVerticalVariation.dropdownMenu.select(dropdownMenuLinkTwo);
    newWindowTitleCheck(linkTwoPageTitle);
}
```

<br>

```html 
<div class="btn-group-vertical mb-3" id="vertical-variation" role="group"
     aria-label="Vertical button group">
    <button type="button" class="btn btn-secondary" onclick="alert('Button One Clicked!');">
        Button one
    </button>
    <button type="button" class="btn btn-secondary" onclick="alert('Button Two Clicked!');">
        Button two
    </button>
    <div class="btn-group" role="group">
        <button id="btnGroupVerticalDrop1" type="button"
                class="btn btn-secondary dropdown-toggle" data-toggle="dropdown"
                aria-haspopup="true" aria-expanded="false">
            Dropdown
        </button>
        <div class="dropdown-menu" aria-labelledby="btnGroupVerticalDrop1"
             x-placement="bottom-start"
             style="position: absolute; will-change: transform; top: 0px; left: 0px; transform: translate3d(0px, 38px, 0px);">
            <a class="dropdown-item" href="https://github.com/jdi-testing/jdi-light"
               target="_blank">JDI Light</a>
            <a class="dropdown-item"
               href="https://jdi-docs.github.io/jdi-light/#jdi-light-framework"
               target="_blank">JDI Docs</a>
        </div>
    </div>
</div>
```
<br>

|Method | Description | Return Type
--- | --- | ---
**assertThat()** | Assert action | TextAssert
**click()** | Click the button | void
**displayed()** | Check that element is displayed | TextAssert
**enabled()** | Check that element is enabled | TextAssert
**expand()** | Dropdown expand | void
**expanded()** | Check that dropdown is expanded | TextAssert
**getText()** | Get button text | String
**getValue()** | Get button value | String
**is()** | Assert action | TextAssert
**select(String option)** | Select option by text | void
**select(int option)** | Select option by index | void
<br>

Inner elements represented by the following classes:
<ul>
    <li> [Text](https://jdi-docs.github.io/jdi-light/#text) </li>
    <li> [Button](https://jdi-docs.github.io/jdi-light/#button)</li>
    <li> [Dropdown](https://jdi-docs.github.io/jdi-light/#dropdown-2)</li>
</ul>
<br>

<a href="https://github.com/jdi-testing/jdi-light/blob/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/composite/section/buttonGroup/VerticalVariationTests.java" target="_blank">Button Group Vertical Variation Tests Example</a>
<br><br>

#### Alert
Alert is located in the following class: <br>
- __Java__: _com.epam.jdi.light.ui.bootstrap.common.Alert_

**<a href="https://getbootstrap.com/docs/4.3/components/alerts/" target="_blank">Alert</a>** – Element that provides contextual feedback messages for typical user actions with the handful of available and flexible alert messages.

![Alert](../../images/bootstrap/alert-dismissible.png)

Here is an example with provided Bootstrap v4.3 code:

```java 
// @FindBy(css = "#simple-alert") public static Alert simpleAlert; 
@Css("#simple-alert") 
public static Alert simpleAlert;

// @FindBy(css = "#dismissible-alert") public static Alert dismissibleAlert;
@Css("#dismissible-alert") 
public static Alert dismissibleAlert;

@Test
public void simpleAlertExistingTest() {
    simpleAlert.is().displayed();
    simpleAlert.is().enabled();
    dismissibleAlert.is().displayed();
    dismissibleAlert.is().enabled();
}

@Test
public void simpleAlertLinkClickableTest() {
    simpleAlert.click();
    switchToNewWindow();
    assertEquals(getTitle(), pageTitle);
    closeWindow();
}

@Test
public void dismissibleAlertButtonIsValidationTest() {
    dismissibleAlert.dismissButton().is().displayed()
            .enabled()
            .core()
            .attr("type", "button")
            .attr("data-dismiss", "alert")
            .attr("aria-label", "Close")
            .tag(is("button"));
}

@Test (priority = 1)
public void dismissibleAlertButtonClickTest() {
    dismissibleAlert.dismissButton().click();
    dismissibleAlert.base().waitSec(1);
    dismissibleAlert.is().hidden();
}
```

<br>

```html
<div class="alert alert-success" id="simple-alert" role="alert">
    Alert with <a
        href="https://jdi-testing.github.io/jdi-light/index.html"
        class="alert-link" target="_blank">index page link</a>.
</div>
<div class="alert alert-warning alert-dismissible fade show" id="dismissible-alert"
     role="alert">
    <strong>Dismissible alert!</strong><br> Hide alert clicking on "x".
    <button type="button" class="close" id="dismissible-alert-close-button"
            data-dismiss="alert" aria-label="Close">
        <span aria-hidden="true">&times;</span>
    </button>
</div>
```

Available methods in Java JDI Light:

|Method | Description | Return Type
--- | --- | ---
**assertThat()** | Assert action | TextAssert
**click()** | Click to hide alert | Action
**displayed()** | Check that element is displayed | TextAssert
**hidden()** | Check that element is hidden | TextAssert
**is()** | Assert action | TextAssert

<br>

<a href="https://github.com/jdi-testing/jdi-light/blob/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/common/AlertTests.java" target="_blank">Alert test examples</a>


<br><br><br><br><br><br>
#### Badge

**1) <a style="font-weight:bold" href="https://getbootstrap.com/docs/4.3/components/badge/" target="_blank">Badge</a>** - Element that scale to match the size of the immediate parent element by using relative font sizing and em units.<br>

Here is an example badge with provided Bootstrap v4.3 code:

![Badge](../../images/bootstrap/badge_heading.png)

```java 
// @FindBy(css = "#badge-secondary")
@UI("#badge-secondary") public static Text badgeSecondary;
// @FindBy(css = "#btn-primary")
@UI("#btn-primary") public static ButtonWithBadge buttonWithBadge;

@Test
public void getTextTest() {
    assertEquals(badgeSecondary.getText(), badgeSecondaryText);
    assertEquals(badgeSecondary.getValue(), badgeSecondaryText);
}

@Test
public void simpleVisibilityTest() {
    assertTrue(badgeSecondary.isDisplayed());
}

@Test
public void checkBadgeInButton(){
    buttonWithBadge.badge.is().displayed();
    buttonWithBadge.badge.is().text(badgeInButtonText);
}
```

```html
<h1>Heading 
    <span class="badge badge-secondary" id="badge-secondary">Badge</span>
</h1>
``` 

An example nested badge in button with provided Bootstrap v4.3 code:

![Badge](../../images/bootstrap/badge_button.png)

```html 
<button type="button" class="btn btn-primary" id="btn-primary" onclick="alert('Button with badge');">
    Profile
    <span class="badge badge-light">9</span> 
    <span class="sr-only">unread messages</span>
</button>
```

In this case Badge is represented by the following class:

[Text](https://jdi-docs.github.io/jdi-light/#text)

Available methods in Java JDI Light:

|Method | Description | Return Type
--- | --- | ---
**assertThat()** | Assert action | TextAssert
**displayed()** | Check that element is displayed | TextAssert
**getText()** | Get button text | String
**is()** | Assert action | TextAssert
<br>
**2) <a style="font-weight:bold" href="https://getbootstrap.com/docs/4.3/components/badge/#links" target="_blank">Badge</a>** - .badge-* classes on an link element quickly provide actionable badges with hover and focus states.<br>

![Badge](../../images/bootstrap/badge_link.png)

Here is an example with provided Bootstrap v4.3 code:

```java 
// @FindBy(css = "#badge-success")
@UI("#badge-success") public static Link badgeSuccess;

@Test
public void getTextTest() {
    assertEquals(badgeSuccess.getText(), badgeSuccessText);
    assertEquals(badgeSuccess.getValue(), badgeSuccessText);
}

@Test
public void simpleVisibilityTest() {
    assertTrue(badgeSuccess.isDisplayed());
}
```

```html 
<a href="https://github.com/jdi-testing" style="font-size: 16px;"class="badge badge-success" id="badge-success" alt="Github JDI Link">Github JDI</a>
```

In this case Badge is represented by Text class in Java:

[Link](https://jdi-docs.github.io/jdi-light/#link)

Available methods in Java JDI Light:

|Method | Description | Return Type
--- | --- | ---
**alt()** |Returns the alternate text | String
**assertThat()** | Returns object for work with assertions | LinkAssert
**click()** |Follow the link | void
**getText()** |Returns the link text  | String
**is()** | Returns object for work with assertions | LinkAssert
**ref()** |Returns the reference  | String
**url()** |Returns the URL  | URL

<a href="https://github.com/jdi-testing/jdi-light/blob/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/common/BadgeTests.java" target="_blank">Bootstrap badge test examples</a><br>
<br><br>

#### Breadcrumb



<a href="https://getbootstrap.com/docs/4.3/components/breadcrumb/" target="_blank">Breadcrumb</a> is a control element  used for navigational on web pages

![Breadcrumb example](../../images/bootstrap/breadcrumb.png)

```java 

// @FindBy(css = "#breadcrumb")
@UI("#breadcrumb") public static Breadcrumb breadcrumb;

@Test
public void getTextTest() {
    breadcrumb.items.has().size(3);
    breadcrumb.items
              .assertThat()
              .values(TEXT, hasItems(ITEMS_VALUES));
}
    
@Test
public void getCurrectItemTest() {
    breadcrumb.items.last().has().value(BOOTSTRAP);
    breadcrumb.items.last().has().text(BOOTSTRAP);
}
```

Here is an example with provided Bootstrap v4.3 code:

```html
<nav aria-label="breadcrumb">
    <ol class="breadcrumb" id="breadcrumb">
        <li class="breadcrumb-item"><a
                href="https://jdi-testing.github.io/jdi-light/index.html" target="_blank">Home</a>
        </li>
        <li class="breadcrumb-item"><a
                href="https://jdi-testing.github.io/jdi-light/html5.html" target="_blank">HTML
            5</a></li>
        <li class="breadcrumb-item active" aria-current="page">Bootstrap</li>
    </ol>
</nav>
```

Breadcrumb is represented  by the following class: <br>
- [UIBaseElement](https://jdi-docs.github.io/jdi-light/#uibaseelement)

Inner elements are represented  by the following class: <br>
- [Weblist](https://jdi-docs.github.io/jdi-light/#weblist)

Available methods in Java JDI Light:

|Method/Property | Description | Return Type
--- | --- | ---
**assertThat()**	 |  Assert action	| UIAssert
**click()** | Click the item  | void
**first()**|Get first item |UIElement
**getText()** |Get item text  |  String
**getValue()** |Get item value  |  String
**get(String option)**|Get item by text|UIElement
**get(int index)**|Get item by index| UIElement
**is()**	 |  Assert action	| UIAssert
**last()**|Get last item |UIElement
**shouldBe()**	 |  Assert action	| UIAssert


<a href="https://github.com/jdi-testing/jdi-light/blob/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/common/BreadcrumbTests.java" target="_blank">Breadcrumb Tests Example</a>

<br><br>

#### Navbar

##### <a href="https://getbootstrap.com/docs/4.3/components/navbar/#supported-content" target="_blank">Supported content</a>
Navbars come with built-in support for a handful of sub-components.

Choose from the following as needed:

+ ``.navbar-brand`` for your company, product, or project name.
+ ``.navbar-nav`` for a full-height and lightweight navigation (including support for dropdowns).
+ ``.navbar-toggler`` for use with our collapse plugin and other navigation toggling behaviors.
+ ``.form-inline`` for any form controls and actions.
+ ``.navbar-text`` for adding vertically centered strings of text.
+ ``.collapse.navbar-collapse`` for grouping and hiding navbar contents by a parent breakpoint.

Here’s an example of all the sub-components included in a responsive light-themed navbar
that automatically collapses at the lg (large) breakpoint.
<br>

1. Navbar with content <br>
   ![Supported content](../../images/bootstrap/navbar-supported-content-normal.png)<br>
2. Collapsed navbar <br>
   ![Supported content](../../images/bootstrap/navbar-supported-content-collapsed.png)<br>
3. Expanded navbar <br>
   ![Supported content](../../images/bootstrap/navbar-supported-content-uncollapsed.png)

```java 
// @FindBy(id = "navbar-supported-content")
@UI("#navbar-supported-content")
public static NavbarSupportedContent navbarSupportedContent

// @FindBy(tagName = "button[data-toggle=collapse]")
@UI("button[data-toggle=collapse]")
public Button navExpand;

@JDropdown(root = ".navbar-nav",
        list = "a")
public Collapse nav;

private static final String bootstrapNavPageUrl = "https://getbootstrap.com/docs/4.3/components/navbar/#nav";
private static final String jdiPageUrl = "https://github.com/jdi-testing/jdi-light/";
private static final String jdiBootstrapPageUrl = "https://jdi-testing.github.io/jdi-light/bootstrap.html#";
private static final String activeLinkText = "Active link";
private static final String jdiLinkText = "JDI Light";
private static final String dropdownLinkText = "Dropdown";
private static final String dropdownAction = "Action";
private static final String dropdownAnotherAction = "Another action";
private static final String dropdownSmthElse = "Something else here";
private static final String disabledLinkText = "Disabled link";

@Test(dataProvider = "navbarLinkData")
public void navLinkContentsTest(String elementName,
                                String elementText,
                                String elementUrl) {
    navbarSupportedContent.nav.show();
    navbarSupportedContent.nav.list().get(elementName)
            .is()
            .text(elementText)
            .and()
            .attr("href", elementUrl);
}

@Test(dataProvider = "collapseLinkTextData")
public void collapseLinkTextTest(String linkText) {
    WindowsManager.resizeWindow(900, 600);

    navbarSupportedContent.navExpand.show();
    navbarSupportedContent.navExpand.click();

    navbarSupportedContent.nav.is().expanded();

    assertTrue(navbarSupportedContent.nav.list().values().contains(linkText));
}
```

```html
<nav id="navbar-nav-with-disabled" class="navbar navbar-expand-lg navbar-light bg-light">
    <a class="navbar-brand" href="https://getbootstrap.com/docs/4.3/components/navbar/#nav"
       target="_blank">Navbar</a>
    <button class="navbar-toggler" type="button" data-toggle="collapse"
            data-target="#navbarNavAltMarkup" aria-controls="navbarNavAltMarkup"
            aria-expanded="false" aria-label="Toggle navigation">
        <span class="navbar-toggler-icon"></span>
    </button>
    <div class="collapse navbar-collapse" id="navbarNavAltMarkup">
        <div class="navbar-nav">
            <a class="nav-item nav-link active"
               href="https://jdi-testing.github.io/jdi-light/index.html" target="_blank">Home
                <span class="sr-only">(current)</span></a>
            <a class="nav-item nav-link"
               href="https://jdi-testing.github.io/jdi-light/html5.html" target="_blank">HTML
                5</a>
            <a class="nav-item nav-link"
               href="https://jdi-testing.github.io/jdi-light/bootstrap.html" target="_blank">Bootstrap</a>
            <a class="nav-item nav-link disabled"
               href="https://jdi-testing.github.io/jdi-light/bootstrap.html" tabindex="-1"
               aria-disabled="true" target="_blank">Disabled</a>
        </div>
    </div>
</nav>
```

Navbar is represented by Section class in Java:

[Section](https://jdi-docs.github.io/jdi-light/#section)

Inner elements of jumbotron can be represented by the following classes:

- [TextField](https://jdi-docs.github.io/jdi-light/#textfield)

- [Button](https://jdi-docs.github.io/jdi-light/#button)

- [Link](https://jdi-docs.github.io/jdi-light/#link)

- [Collapse](https://jdi-docs.github.io/jdi-light/#collapse)

Available methods in Java JDI Light:

|Method | Description | Return Type
--- | --- | ---
**attr()** | Check whether an element has attribute of specified name and with given value  | IsAssert
**click()** | Click on element  | void
**displayed()** | Asserts element is displayed  | UIAssert
**expanded()** | Check whether a dropdown is expanded  | void
**getValue()** | Get value from input group  | String
**hasClass()** | Checks whether element has class  | boolean
**is()** | Asserts element  | UIAssert
**select()** | Select a dropdown element  | void
**setValue()** | Set a value for input group  | void
**text()** | Check whether a text matches a pattern  | IsAssert
**toggle()** | Toggle collapse  | void

<a href="https://github.com/jdi-testing/jdi-light/blob/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/composite/section/navbar/NavbarSupportedContentTests.java" target="_blank">Bootstrap Test Examples</a>
<br><br>

##### <a href="https://getbootstrap.com/docs/4.3/components/navbar/#brand" target="_blank">Brand</a>
The ``.navbar-brand`` can be applied to most elements, but an anchor works best as some elements might require utility classes or custom styles.
<br>

Navbar brand as a link <br>
![Brand](../../images/bootstrap/navbar-brand-link.png)<br>
Navbar brand as heading <br>
![Brand](../../images/bootstrap/navbar-brand-heading.png)<br>
<br>

Adding images to the ```.navbar-brand``` will likely always require custom styles or utilities to properly size. Here are some examples to demonstrate.<br>

![Brand](../../images/bootstrap/navbar-brand-image.png)<br>
![Brand](../../images/bootstrap/navbar-brand-image-and-link.png)<br>

```java 
       //FindBy(css = "#brand-heading")
        @UI("#brand-heading")
        public UIElement navbarBrandHeading; 
  
        //FindBy(css = "#brand-link")
        @UI("#brand-link")
        public UIElement navbarBrandLink;
    
        //FindBy(css = "#brand-as-image")
        @UI("#brand-as-image")
        public UIElement navbarBrandAsImage;
    
        //FindBy(css = "#brand-as-image-and-link")
        @UI("#brand-as-image-and-link")
        public UIElement navbarBrandAsImageAndLink;

        @Test (dataProvider = "navbarBrandsWithLink")
        public void  checkNavbarLink(UIElement brandAsLink) {
            brandAsLink.is().core().hasAttr("href");
            brandAsLink.highlight("blue");
            brandAsLink.unhighlight();
            int winNumber = WindowsManager.windowsCount();
            brandAsLink.click();           
            WindowsManager.switchToWindow(winNumber + 1);
            assertThat(getUrl(), is(navbarUrl));
            WindowsManager.closeWindow();
            WindowsManager.switchToWindow(winNumber);
         }
    
        @Test(dataProvider = "navbarBrands")
        public void checkNavbarText(UIElement uiBaseElement, String navbarText) {
             uiBaseElement.highlight();
             uiBaseElement.is().core().text(navbarText);
             uiBaseElement.unhighlight();
        }

        @Test(dataProvider = "navbarBrandsWithImage")
        public void checkNavbarImage(UIElement brandWithImage) {
            UIElement imgFromNavbar = brandWithImage.children().get(1);
            imgFromNavbar.highlight("blue");
            imgFromNavbar.is().core().tag("img").attr("src", containsString(imgPath));
            imgFromNavbar.unhighlight();
            int winNumber = WindowsManager.windowsCount();
            imgFromNavbar.click();          
            WindowsManager.switchToWindow(winNumber + 1);
            assertThat(getUrl(), is(navbarUrl));
            WindowsManager.closeWindow();
            WindowsManager.switchToWindow(winNumber);
    }
```

```html 

<div id="navbar-base-for-brand">
     <p>Navbar - Brand as link</p>
     <nav class="navbar navbar-light bg-light">
         <a class="navbar-brand" id="brand-link" href="https://getbootstrap.com/docs/4.3/components/navbar/#nav" target="_blank">Brand link</a>
     </nav>
     <br>
     <p>Navbar - Brand as heading</p>
     <nav class="navbar navbar-light bg-light">
         <span class="navbar-brand mb-0 h1" id="brand-heading">Brand heading</span>
     </nav>
     <br>
     <p>Navbar - Brand as image</p>
     <nav class="navbar navbar-light bg-light">
         <a class="navbar-brand" id="brand-as-image" href="https://getbootstrap.com/docs/4.3/components/navbar/#nav" target="_blank">
             <img src="images/wolverin.jpg" width="20" height="30" alt="">
         </a>
     </nav>
     <br>
     <p>Navbar - Brand as image and link</p>
     <nav class="navbar navbar-light bg-light mb-3">
         <a class="navbar-brand" id="brand-as-image-and-link" href="https://getbootstrap.com/docs/4.3/components/navbar/#nav" target="_blank">
             <img src="images/wolverin.jpg" width="20" height="30" class="d-inline-block align-top" alt="">Brand link</a>
     </nav>
</div>
``` 

Available methods in Java JDI Light:

|Method | Description | Return Type
--- | --- | ---
**assertThat()** | Assert action | UIAssert
**is()** | Assert action | UIAssert
**hasAttr()** | Assert action | UIAssert

<a href="https://github.com/jdi-testing/jdi-light/blob/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/composite/section/navbar/NavbarBrandTests.java" target="_blank">Bootstrap test examples</a>

<br><br><br><br><br><br><br><br>

##### [Nav](https://getbootstrap.com/docs/4.3/components/navbar/#nav)
Navbar navigation links build on our ``.nav`` options with their own modifier class and require the use of toggler classes for proper responsive styling.

```java 

public class NavbarNav extends Section {
    @UI("#navbar-nav-with-disabled") public NavbarSimpleLinks navLinks1;
    @UI("#navbar-nav-with-dropdown") public NavbarComplexLinks navbarComplexLinks;
}
public class NavbarSimpleLinks extends Section {
    @UI(".navbar-brand") public Link brand;
    @UI(".navbar-nav a") public ListGroup listPages;
}
public class NavbarComplexLinks extends Section {
    @UI(".navbar-brand")
    public Link brand;
    @UI("ul li")
    public ListGroup listPages;

    @JDropdown(root = ".dropdown",
            expand = "#navbarDropdownMenuLink",
            list = "a")
    public Dropdown dropdown;

    public void selectMenu(String item) {
        dropdown.list().select(item);
    }
}

@Test
public void isDisabledItemNavWithDisabled(){
   navbarNav.navLinks1.listPages.get(4)
            .is()
            .displayed();
   navbarNav.navLinks1.listPages.get(4)
            .is()
            .disabled();
}
   





@Test
public void clickNavbarNavWithDropdownLinksTest() {
        navbarNav.navbarComplexLinks.listPages.get(4)
                .is()
                .displayed();
        UIElement dropdown = navbarNav.navbarComplexLinks.listPages.get(4);
        dropdown.click();
        navbarNav.navbarComplexLinks.selectMenu(ITEM_BRAND);
        newWindowTitleCheck(NAVBAR_BOOTSTRAP);
        dropdown.click();
        navbarNav.navbarComplexLinks.selectMenu(ITEM_NAV);
        newWindowTitleCheck(NAVBAR_BOOTSTRAP);
        dropdown.click();
        navbarNav.navbarComplexLinks.selectMenu(ITEM_FORMS);
        newWindowTitleCheck(NAVBAR_BOOTSTRAP);
}



```

![Color Nav example](../../images/bootstrap/nav.png)

Here is an example with provided Bootstrap v4.3 code:

```html
<nav id="navbar-nav-with-disabled" class="navbar navbar-expand-lg navbar-light bg-light">
    <a class="navbar-brand" href="https://getbootstrap.com/docs/4.3/components/navbar/#nav"
       target="_blank">Navbar</a>
    <button class="navbar-toggler" type="button" data-toggle="collapse"
            data-target="#navbarNavAltMarkup" aria-controls="navbarNavAltMarkup"
            aria-expanded="false" aria-label="Toggle navigation">
        <span class="navbar-toggler-icon"></span>
    </button>
    <div class="collapse navbar-collapse" id="navbarNavAltMarkup">
        <div class="navbar-nav">
            <a class="nav-item nav-link active"
               href="https://jdi-testing.github.io/jdi-light/index.html" target="_blank">Home
                <span class="sr-only">(current)</span></a>
            <a class="nav-item nav-link"
               href="https://jdi-testing.github.io/jdi-light/html5.html" target="_blank">HTML
                5</a>
            <a class="nav-item nav-link"
               href="https://jdi-testing.github.io/jdi-light/bootstrap.html" target="_blank">Bootstrap</a>
            <a class="nav-item nav-link disabled"
               href="https://jdi-testing.github.io/jdi-light/bootstrap.html" tabindex="-1"
               aria-disabled="true" target="_blank">Disabled</a>
        </div>
    </div>
</nav>
```

With dropdown

![Color Nav example](../../images/bootstrap/nav-dropdown.png)

Here is an example with provided Bootstrap v4.3 code:

```html
<nav id="navbar-nav-with-dropdown" class="navbar navbar-expand-lg navbar-light bg-light">
    <a class="navbar-brand" href="https://getbootstrap.com/docs/4.3/components/navbar/#nav"
       target="_blank">Navbar</a>
    <button class="navbar-toggler" type="button" data-toggle="collapse"
            data-target="#navbarNavDropdown" aria-controls="navbarNavDropdown"
            aria-expanded="false" aria-label="Toggle navigation">
        <span class="navbar-toggler-icon"></span>
    </button>
    <div class="collapse navbar-collapse" id="navbarNavDropdown">
        <ul class="navbar-nav">
            <li class="nav-item active">
                <a class="nav-link" href="https://jdi-testing.github.io/jdi-light/index.html"
                   target="_blank">Home <span class="sr-only">(current)</span></a>
            </li>
            <li class="nav-item">
                <a class="nav-link" href="https://jdi-testing.github.io/jdi-light/html5.html"
                   target="_blank">HTML 5</a>
            </li>
            <li class="nav-item">
                <a class="nav-link"
                   href="https://jdi-testing.github.io/jdi-light/bootstrap.html"
                   target="_blank">Bootstrap</a>
            </li>
            <li class="nav-item dropdown">
                <a class="nav-link dropdown-toggle"
                   href="https://getbootstrap.com/docs/4.3/components/navbar/"
                   id="navbarDropdownMenuLink" role="button" data-toggle="dropdown"
                   aria-haspopup="true" aria-expanded="false" target="_blank">
                    Navbar
                </a>
                <div class="dropdown-menu" aria-labelledby="navbarDropdownMenuLink">
                    <a class="dropdown-item"
                       href="https://getbootstrap.com/docs/4.3/components/navbar/#brand"
                       target="_blank">Brand</a>
                    <a class="dropdown-item"
                       href="https://getbootstrap.com/docs/4.3/components/navbar/#nav"
                       target="_blank">Nav</a>
                    <a class="dropdown-item"
                       href="https://getbootstrap.com/docs/4.3/components/navbar/#forms"
                       target="_blank">Forms</a>
                </div>
            </li>
        </ul>
    </div>
</nav>
``` 

Nav is represented by Section class in Java:

[Section](https://jdi-docs.github.io/jdi-light/#section)

Inner elements of media object can be represented by the following classes:
<ul>
    <li> [Link](https://jdi-docs.github.io/jdi-light/#link)  </li>
    <li> [Collapse](https://jdi-docs.github.io/jdi-light/#collapse)  </li>
    <li> [DropDown](https://jdi-docs.github.io/jdi-light/#dropdown-2)  </li>
    <li> [See more elements](https://jdi-docs.github.io/jdi-light/#bootstrap-common-elements) </li>
</ul>

Available methods in Java JDI Light:

|Method | Description | Return Type
--- | --- | ---
**click()** | Click the item| void
**is()** | Assert action | TextAssert

<a style="font-weight: bold;" target="_blank" href="https://github.com/jdi-testing/jdi-light/blob/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/composite/section/navbar/NavbarNavsTests.java">Bootstrap test examples</a>

<br>

##### [Forms](https://getbootstrap.com/docs/4.3/components/navbar/#forms)

Place various form controls and components within a navbar with ``.form-inline``.

![Forms example](../../images/bootstrap/navbar-forms1.png)

```java 

//FindBy(id = "#navbar-form-2")
@UI("#navbar-form-2")
public static NavbarForm navbarFormWithText;
//FindBy(id = "#navbar-form-3")
@UI("#navbar-form-3")
public static NavbarWithInputGroupForm navbarFormWithInputGroup;

@Test
public void checkSetValueInputGroup() {
    navbarFormWithInputGroup.inputGroup.input.setValue(inputText);
    navbarFormWithInputGroup.inputGroup.input.assertThat().text(is(inputText));
}

@Test
public void checkFormElements() {
    UIElement input = navbarFormWithText.form.core().find((By.tagName("input")));
    UIElement button = navbarFormWithText.form.core().find((By.tagName("button")));
    input.shouldBe().enabled();
    button.shouldBe().enabled().text(is(buttonText));
    navbarFormWithText.form.click();
}

```

Here is an example with provided Bootstrap v4.3 code:

```html
<nav class="navbar navbar-light bg-light" id="navbar-form-1">
    <form class="form-inline">
        <input class="form-control mr-sm-2" type="search" placeholder="Search"
               aria-label="Search" style="width: 135px">
        <button class="btn btn-outline-success my-2 my-sm-0"
                type="submit"
                onclick="alert('Search Main Button Clicked!');">Search
        </button>
    </form>
</nav>
```

Immediate children elements in .navbar use flex layout and will default to justify-content: between.

![Forms example](../../images/bootstrap/navbar-forms2.png)

Here is an example with provided Bootstrap v4.3 code:

```html
<nav class="navbar navbar-light bg-light" id="navbar-form-2">
    <a class="navbar-brand">Navbar</a>
    <form class="form-inline">
        <input class="form-control mr-sm-2" type="search" placeholder="Search"
               aria-label="Search" style="width: 135px">
        <button class="btn btn-sm btn-outline-secondary my-2 my-sm-0"
                type="submit"
                onclick="alert('Search Smaller Button Clicked!');">Search
        </button>
    </form>
</nav>
```

Input groups work, too:

![Forms example](../../images/bootstrap/navbar-forms3.png)

Here is an example with provided Bootstrap v4.3 code:

```html
<nav class="navbar navbar-light bg-light" id="navbar-form-3">
    <form class="form-inline">
        <div class="input-group">
            <div class="input-group-prepend">
                <span class="input-group-text" id="basic-addon1">@</span>
            </div>
            <input type="text" class="form-control" placeholder="Username"
                   aria-label="Username" aria-describedby="basic-addon1">
        </div>
    </form>
</nav>
```

Media object is represented by Section class in Java:

[Section](https://jdi-docs.github.io/jdi-light/#section)

Inner elements of media object can be represented by the following classes:

+ [Form](https://jdi-docs.github.io/jdi-light/#form)
+ [TextField](https://jdi-docs.github.io/jdi-light/#textfield)
+ [Button](https://jdi-docs.github.io/jdi-light/#button)
+ [Link](https://jdi-docs.github.io/jdi-light/#link)
+ [See more elements](https://jdi-docs.github.io/jdi-light/#html5-common-elements)

<a style="font-weight: bold;" target="_blank" href="https://github.com/jdi-testing/jdi-light/blob/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/composite/section/navbar/NavbarFormsTests.java">Bootstrap test examples</a>
<br><br>

##### [Text](https://getbootstrap.com/docs/4.3/components/navbar/#text)
Navbars may contain bits of text with the help of ``.navbar-text``.
This class adjusts vertical alignment and horizontal spacing for strings of text.

<br>

![Text example](../../images/bootstrap/navbar-text1.png)

Here is an example with provided Bootstrap v4.3 code:

```java 
//@FindBy(xpath = "//h4[.='Navbar - Text']/../..") public static NavbarText navbarText;
@UI("//h4[.='Navbar - Text']/../..") public static NavbarText navbarText;

public class NavbarText extends Section {
    @UI("nav:nth-child(1)") public Text simpleText;
    @UI("nav.navbar.navbar-expand-lg.navbar-light.bg-light") public NavbarTextLinks complexNavbar;
}

@Test
public void verifySimpleNavbarTextTest() {
    navbarText.simpleText
        .is()
        .text(is(inlineElement));
}
```


```html
<nav class="navbar navbar-light bg-light">
   <span class="navbar-text">
	   Navbar text with an inline element
	</span>
</nav>
```

Mix and match with other components and utilities as needed.

![Text example](../../images/bootstrap/navbar-text2.png)

Here is an example with provided Bootstrap v4.3 code:

```java 
public class NavbarTextLinks extends Section {
    @UI(".navbar-brand") public Link brand;
    @UI("ul li") public ListGroup listPages;
    @UI(".navbar-text") public Text simpleText;
}

@Test
public void verifyComplexNavbarHomeTest() {
    navbarText.complexNavbar.listPages.get(1)
        .is()
        .text(is(linkName1));
    navbarText.complexNavbar.listPages.get(1).click();
    newWindowTitleCheck(page1);
    navbarText.complexNavbar.listPages.get(2)
        .is()
        .text(is(linkName2));
    navbarText.complexNavbar.listPages.get(2).click();
    newWindowTitleCheck(page2);
    navbarText.complexNavbar.listPages.get(3)
        .is()
        .text(is(linkName3));
    navbarText.complexNavbar.listPages.get(3).click();
    newWindowTitleCheck(page3);
}
```


```html
<nav class="navbar navbar-expand-lg navbar-light bg-light">
    <a class="navbar-brand" href="https://getbootstrap.com/docs/4.3/components/navbar/#nav"
       target="_blank">Navbar w/ text</a>
    <button class="navbar-toggler" type="button" data-toggle="collapse"
            data-target="#navbarText"
            aria-controls="navbarText" aria-expanded="false" aria-label="Toggle navigation">
        <span class="navbar-toggler-icon"></span>
    </button>
    <div class="collapse navbar-collapse" id="navbarText">
        <ul class="navbar-nav mr-auto">
            <li class="nav-item active">
                <a class="nav-link" href="https://jdi-testing.github.io/jdi-light/index.html"
                   target="_blank">Home <span class="sr-only">(current)</span></a>
            </li>
            <li class="nav-item">
                <a class="nav-link" href="https://jdi-testing.github.io/jdi-light/html5.html"
                   target="_blank">HTML 5</a>
            </li>
            <li class="nav-item">
                <a class="nav-link"
                   href="https://jdi-testing.github.io/jdi-light/bootstrap.html"
                   target="_blank">Bootstrap</a>
            </li>
        </ul>
        <span class="navbar-text">
		  Navbar text with an inline element
		</span>
    </div>
</nav>
```

Available methods in Java JDI Light:

|Method | Description | Return Type
--- | --- | ---
**assertThat()** | Assert action | TextAssert
**click()** | Click the button | void
**get()** | Select button by index | action
**getText()** | Get button text | String
**is()** | Assert action | TextAssert

<br><br>

[Navbar-text test example](https://github.com/jdi-testing/jdi-light/blob/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/composite/section/navbar/NavBarTextTests.java) <br>
<br>

Available methods and properties in C# JDI Light:

|Method/Property | Description | Return Type
--- | --- | ---
|  |
|  |
|  |
|  |
<br><br>

##### [Color schemes](https://getbootstrap.com/docs/4.3/components/navbar/#color-schemes)

Theming the navbar has never been easier thanks to the combination of theming classes and ``background-color`` utilities
Choose from ``.navbar-light`` for use with light background colors, or ``.navbar-dark`` for dark background colors. Then, customize with ``.bg-*`` utilities.

![Color schemes example](../../images/bootstrap/navbar-color-schemes.png)

Here is an example with provided Bootstrap v4.3 code:

```java 
public class NavbarColorScheme extends Navbar {

    //@FindBy(className = "navbar-brand")
    @UI(".navbar-brand")
    public Link navbarLink;

    //@FindBy(linkText = "Home\n(current)")
    @ByText("Home")
    public Link homeLink;

    //@FindBy(linkText = "Contact form")
    @ByText("Contact form")
    public Link contactFormLink;

    //@FindBy(linkText = "Metals & Colors")
    @ByText("Metals & Colors")
    public Link metalsAndColorsLink;

    //@FindBy(xpath = "//form/button")
    @UI("form button")
    public Button searchButton;
}

@Test(dataProvider = "navbarColorSchemesWithColors")
public void colorSchemeAccordanceTest(NavbarColorScheme navbarColorScheme, String bgColor, 
String navbarAndHomeColor, String contactAndMetalsColor, String searchColor) {
    navbarColorScheme.core().is()
            .css("background-color", bgColor);
    checkColorOfElement(navbarColorScheme.navbarLink, navbarAndHomeColor);
    checkColorOfElement(navbarColorScheme.homeLink, navbarAndHomeColor);
    checkColorOfElement(navbarColorScheme.contactFormLink, contactAndMetalsColor);
    checkColorOfElement(navbarColorScheme.metalsAndColorsLink, contactAndMetalsColor);
    checkColorOfElement(navbarColorScheme.searchButton, 
String.format("rgba%s, 1)", searchColor));
    navbarColorScheme.searchButton.core().is()
            .css("border-color", String.format("rgb%s)", searchColor));
}

private void checkColorOfElement(ICoreElement elem, String color) {
    elem.core().is()
            .css("color", color);
}
```

```html
<nav id="navbar-dark-colorscheme" class="navbar navbar-expand-lg navbar-dark bg-dark mb-1">
    <a class="navbar-brand"
       href="https://getbootstrap.com/docs/4.0/components/navbar/#color-schemes"
       target="_blank">Navbar</a>
    <button class="navbar-toggler collapsed" type="button" data-toggle="collapse"
            data-target="#navbarColor01" aria-controls="navbarColor01" aria-expanded="false"
            aria-label="Toggle navigation">
        <span class="navbar-toggler-icon"></span>
    </button>
    <div class="navbar-collapse collapse" id="navbarColor01" style="">
        <ul class="navbar-nav mr-auto">
            <li class="nav-item active">
                <a class="nav-link" href="https://jdi-testing.github.io/jdi-light/index.html"
                   target="_blank">Home <span class="sr-only">(current)</span></a>
            </li>
            <li class="nav-item">
                <a class="nav-link" href="https://jdi-testing.github.io/jdi-light/contacts.html"
                   target="_blank">Contact form</a>
            </li>
            <li class="nav-item">
                <a class="nav-link"
                   href="https://jdi-testing.github.io/jdi-light/metals-colors.html"
                   target="_blank">Metals & Colors</a>
            </li>
        </ul>
        <form class="form-inline">
            <input class="form-control mr-sm-2" type="search" placeholder="Search"
                   aria-label="Search">
            <button class="btn btn-outline-info my-2 my-sm-0" type="button"
                    onclick="alert('Search');">Search
            </button>
        </form>
    </div>
</nav>
```

Available methods in Java JDI Light:

|Method | Description | Return Type
--- | --- | ---
**assertThat()** | Assert action | TextAssert
**click()** | Click the button | void
**getText()** | Get button text | String
**is()** | Assert action | TextAssert

<a href="https://github.com/jdi-testing/jdi-light/blob/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/composite/section/navbar/NavbarColorSchemeTests.java">Bootstrap test examples</a>

<br><br>

##### [Containers](https://getbootstrap.com/docs/4.3/components/navbar/#containers)
Although it’s not required, you can wrap a navbar in a ``.container`` to center it on a page or add one within to only center the contents of a fixed or static top navbar.

```java 
public class NavbarContainer extends Section {
//@FindBy(id = "navbar-containers-centred")
    @UI("#navbar-containers-centred") public NavbarSimpleLinks navLinks1;
//@FindBy(id = "navbar-containers-expanded")
    @UI("#navbar-containers-expanded") public NavbarComplexLinks navbarComplexLinks;
}

@Test
  public void getNameNavbarContainerBrandTest() {
        navbarContainers.navLinks1.brand.is().text(textNavbarCentredContainer);
        navbarContainers.navbarComplexLinks.brand.is().text(textNavbarExpandedConteiner);
  }






@Test
public void clickNavbarCentredContainerLinksTest() {
     navbarContainers.navLinks1.brand.click();
     assertThat(WindowsManager.windowsCount(), is(2));
     WindowsManager.switchToWindow(2);
     assertThat(getUrl(), is(url));
     WindowsManager.closeWindow();
}







```

![Containers schemes example](../../images/bootstrap/navbar-containers.png)

Here is an example with provided Bootstrap v4.3 code:

```html
<div class="container" id="navbar-containers-centred">
    <nav class="navbar navbar-expand-lg navbar-light bg-light mb-1">
        <a class="navbar-brand"
           href="https://getbootstrap.com/docs/4.3/components/navbar/#containers"
           target="_blank">Navbar</a>
    </nav>
</div>
```

When the container is within your navbar, its horizontal padding is removed at breakpoints lower than your specified ``.navbar-expand{-sm|-md|-lg|-xl}`` class.
This ensures we’re not doubling up on padding unnecessarily on lower viewports when your navbar is collapsed.

```html
<nav class="navbar navbar-expand-lg navbar-light bg-light mb-3"
     id="navbar-containers-expanded">
    <div class="container">
        <a class="navbar-brand"
           href="https://getbootstrap.com/docs/4.3/components/navbar/#containers"
           target="_blank">Navbar</a>
    </div>
</nav>
```

Container is represented by Section class in Java:

[Section](https://jdi-docs.github.io/jdi-light/#section)

Inner elements of media object can be represented by the following classes:
<ul>
    <li> [Collapse](https://jdi-docs.github.io/jdi-light/#collapse)  </li>
    <li> [DropDown](https://jdi-docs.github.io/jdi-light/#dropdown-2)  </li>
    <li> [See more elements](https://jdi-docs.github.io/jdi-light/#bootstrap-common-elements) </li>
</ul>

[Bootstrap test examples](https://github.com/jdi-testing/jdi-light/blob/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/composite/section/NavbarContainersTest.java)

##### [Placement](https://getbootstrap.com/docs/4.3/components/navbar/#placement)
Use our position utilities to place navbars in non-static positions. Choose from fixed to the top, fixed to the bottom, or stickied to the top (scrolls with the page until it reaches the top, then stays there). Fixed navbars use position: fixed, meaning they’re pulled from the normal flow of the DOM and may require custom CSS (e.g., ``padding-top`` on the ``<body>``) to prevent overlap with other elements.

Also note that ``.sticky-top`` uses position: sticky, which isn’t fully supported in every browser.

![Containers schemes example](../../images/bootstrap/navbar-placement-sticky.png)

Here is an example with provided Bootstrap v4.3 code:

```java 
//@FindBy(id = "navbar-sticky-top")
@UI("#navbar-sticky-top")
public static NavbarPlacement navbarPlacementStickyTop;

@Test
public void navbarPositionTest() {
    navbarPlacementStickyTop.show();
    navbarPlacementStickyTop.core()
            .is()
            .css("position", "sticky")
            .css("top", "0px");
}




```

```html
<nav class="navbar navbar-expand-lg sticky-top navbar-light bg-light" id="navbar-sticky-top">
    <a class="navbar-brand" href="https://getbootstrap.com/docs/4.3/components/navbar/#placement">Sticky Top</a>
    <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarNav"
            aria-controls="navbarNav" aria-expanded="false" aria-label="Toggle navigation">
        <span class="navbar-toggler-icon"></span>
    </button>
    <div class="collapse navbar-collapse" id="navbarNav">
        <ul class="navbar-nav">
            <li class="nav-item active">
                <a class="nav-link" href="javascript: void();"> <span class="sr-only"></span>Home</a>
            </li>
            <li class="nav-item">
                <a class="nav-link" href="javascript: void();">Features</a>
            </li>
            <li class="nav-item">
                <a class="nav-link" href="javascript: void();">Pricing</a>
            </li>
            <li class="nav-item">
                <a class="nav-link disabled" href="javascript: void();" tabindex="-1" aria-disabled="true">Disabled</a>
            </li>
        </ul>
    </div>
</nav>
```

Available methods in Java JDI Light:

|Method | Description | Return Type
--- | --- | ---
**click()** | Click a link | void
**css()** | Match passed value with the element css | isAssert
**getRect()** | Get element rectangle | Rectangle
**is()** | Assertelement | isAssert
**jsExecute()** | Execute javascript | String
**text()** | Check whether a text matches a pattern | isAssert

<a href="https://github.com/jdi-testing/jdi-light/blob/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/composite/section/navbar/NavbarPlacementTests.java">Bootstrap test examples</a>

<br><br>

##### [Responsive behaviors](https://getbootstrap.com/docs/4.3/components/navbar/#responsive-behaviors)

Navbars can utilize ``.navbar-toggler``, ``.navbar-collapse``, and ``.navbar-expand{-sm|-md|-lg|-xl}`` classes to change when their content collapses behind a button.
In combination with other utilities, you can easily choose when to show or hide particular elements.

For navbars that never collapse, add the ``.navbar-expand`` class on the navbar.
For navbars that always collapse, don’t add any ``.navbar-expand`` class.

###### [Navbar Toggler](https://getbootstrap.com/docs/4.3/components/navbar/#toggler)

Navbar togglers are left-aligned by default, but should they follow a sibling element like a ``.navbar-brand``, they’ll automatically be aligned to the far right.
Reversing your markup will reverse the placement of the toggler.
Below are examples of different toggle styles.

**1. With no ``.navbar-brand`` shown in lowest breakpoint**

``FullScreen``
![No .navbar-brand full screen example](../../images/bootstrap/nobrand-lg.png)

``Collapsed``
![No .navbar-brand collapsed example](../../images/bootstrap/nobrand-collapsed.png)

``Expanded``
![No .navbar-brand expanded example](../../images/bootstrap/nobrand-expanded.png)

Here is an example with provided Bootstrap v4.3 code:

```html
<nav class="navbar navbar-expand-lg navbar-dark bg-primary mb-2">
    <button class="navbar-toggler collapsed" type="button" data-toggle="collapse"
            data-target="#navbarTogglerDemo01" aria-controls="navbarTogglerDemo01"
            aria-expanded="false" aria-label="Toggle navigation">
        <span class="navbar-toggler-icon"></span>
    </button>
    <div class="navbar-collapse collapse" id="navbarTogglerDemo01" style="">
        <a class="navbar-brand" href="javascript:void();">Hidden brand</a>
        <ul class="navbar-nav mr-auto mt-2 mt-lg-0">
            <li class="nav-item active">
                <a class="nav-link" href="https://github.com/jdi-testing/jdi-light"
                   target="_blank">JDI <span class="sr-only">(current)</span></a>
            </li>
            <li class="nav-item">
                <a class="nav-link" href="https://jdi-docs.github.io/jdi-light/#navbar"
                   target="_blank">JDI Docs</a>
            </li>
            <li class="nav-item">
                <a class="nav-link disabled" href="#" tabindex="-1"
                   aria-disabled="true">Disabled</a>
            </li>
        </ul>
        <form class="form-inline my-2 my-lg-0">
            <input class="form-control mr-sm-2" type="search" placeholder="Search"
                   aria-label="Search">
            <button class="btn btn-outline-light my-2 my-sm-0" type="submit"
                    onclick="alert('Search Button Clicked!');">Search
            </button>
        </form>
    </div>
</nav>
```

**2. With a brand name shown on the left and toggler on the right**

``FullScreen``
![Toggler Right FullScreen example](../../images/bootstrap/toggler-right-lg.png)

``Collapsed``
![Toggler Right Collapsed example](../../images/bootstrap/toggler-right-collapsed.png)

``Expanded``
![Toggler Right Expanded example](../../images/bootstrap/toggler-right-expanded.png)

Here is an example with provided Bootstrap v4.3 code:

```html
<nav class="navbar navbar-expand-lg navbar-dark bg-success mb-2">
    <a class="navbar-brand" href="javascript:void();">Navbar</a>
    <button class="navbar-toggler" type="button" data-toggle="collapse"
            data-target="#navbarTogglerDemo02" aria-controls="navbarTogglerDemo02"
            aria-expanded="false" aria-label="Toggle navigation">
        <span class="navbar-toggler-icon"></span>
    </button>

    <div class="collapse navbar-collapse" id="navbarTogglerDemo02">
        <ul class="navbar-nav mr-auto mt-2 mt-lg-0">
            <li class="nav-item active">
                <a class="nav-link" href="https://github.com/jdi-testing/jdi-light"
                   target="_blank">JDI <span class="sr-only">(current)</span></a>
            </li>
            <li class="nav-item">
                <a class="nav-link" href="https://jdi-docs.github.io/jdi-light/#navbar"
                   target="_blank">JDI Docs</a>
            </li>
            <li class="nav-item">
                <a class="nav-link disabled" href="#" tabindex="-1"
                   aria-disabled="true">Disabled</a>
            </li>
        </ul>
        <form class="form-inline my-2 my-lg-0">
            <input class="form-control mr-sm-2" type="search" placeholder="Search">
            <button class="btn btn-outline-light my-2 my-sm-0" type="submit"
                    onclick="alert('Search Button Clicked!');">Search
            </button>
        </form>
    </div>
</nav>
```

**3. With a toggler on the left and brand name on the right**

``FullScreen``
![Toggler Left FullScreen example](../../images/bootstrap/toggler-left-lg.png)

``Collapsed``
![Toggler Left Collapsed example](../../images/bootstrap/toggler-left-collapsed.png)

``Expanded``
![Toggler Left Expanded example](../../images/bootstrap/toggler-left-expanded.png)

Here is an example with provided Bootstrap v4.3 code:

```html
<nav class="navbar navbar-expand-lg navbar-dark mb-3 bg-dark">
    <button class="navbar-toggler collapsed" type="button" data-toggle="collapse"
            data-target="#navbarTogglerDemo03" aria-controls="navbarTogglerDemo03"
            aria-expanded="false" aria-label="Toggle navigation">
        <span class="navbar-toggler-icon"></span>
    </button>
    <a class="navbar-brand" href="javascript:void();">Navbar</a>

    <div class="navbar-collapse collapse" id="navbarTogglerDemo03" style="">
        <ul class="navbar-nav mr-auto mt-2 mt-lg-0">
            <li class="nav-item active">
                <a class="nav-link" href="https://github.com/jdi-testing/jdi-light"
                   target="_blank">JDI <span class="sr-only">(current)</span></a>
            </li>
            <li class="nav-item">
                <a class="nav-link" href="https://jdi-docs.github.io/jdi-light/#navbar"
                   target="_blank">JDI Docs</a>
            </li>
            <li class="nav-item">
                <a class="nav-link disabled" href="#" tabindex="-1"
                   aria-disabled="true">Disabled</a>
            </li>
        </ul>
        <form class="form-inline my-2 my-lg-0">
            <input class="form-control mr-sm-2" type="search" placeholder="Search"
                   aria-label="Search">
            <button class="btn btn-outline-light my-2 my-sm-0" type="submit"
                    onclick="alert('Search Button Clicked!');">Search
            </button>
        </form>
    </div>
</nav>
```

<br>

###### [External content](https://getbootstrap.com/docs/4.3/components/navbar/#external-content)
Plugin to trigger hidden content elsewhere on the page.

![External_content example](../../images/bootstrap/navbar-external.png)

Here is an example with provided Bootstrap v4.3 code:

```java 
@UI("#navbar-external-content") //FindBy(css = "#navbar-external-content")
public static NavbarExternalContent navbarExternalContent;

@Test
public void expandingTest() {
    navbarExternalContent.toggler.expander().is().core().attr(ariaExpanded, "false");
    navbarExternalContent.toggler.expand();
    navbarExternalContent.toggler.expander().is().core().attr(ariaExpanded, "true");
    navbarExternalContent.toggler.collapse();
    navbarExternalContent.toggler.expander().is().core().attr(ariaExpanded, "false");
}

@Test
public void getTextTest() {
    navbarExternalContent.toggler.expand();
    navbarExternalContent.toggler.value().children().get(1).is()
            .displayed()
            .text(text);
    navbarExternalContent.toggler.value().children().get(2).is()
            .displayed()
            .text(mutedText);
    navbarExternalContent.toggler.collapse();
}

```

```html
<div class="pos-f-t" id="navbar-external-content">
    <div class="collapse" id="navbarToggleExternalContent">
        <div class="bg-dark p-4">
            <h5 class="text-white h4">Collapsed content</h5>
            <span class="text-muted">Toggleable via the navbar brand.</span>
        </div>
    </div>
    <nav class="navbar navbar-dark bg-dark">
        <button class="navbar-toggler" type="button" data-toggle="collapse"
                data-target="#navbarToggleExternalContent"
                aria-controls="navbarToggleExternalContent" aria-expanded="false"
                aria-label="Toggle navigation">
            <span class="navbar-toggler-icon"></span>
        </button>
    </nav>
</div>
```

Navbar - External content is represented by Section class in Java:

[Section](https://jdi-docs.github.io/jdi-light/#section)

Inner elements of Navbar - External content can be represented by the following classes:

+ [Collapse](https://jdi-docs.github.io/jdi-light/#collapse)

+ [Text](https://jdi-docs.github.io/jdi-light/#text)

Available methods in Java JDI Light:

|Method/Property | Description | Return Type
--- | --- | ---
**assertThat()** | Assert action | TextAssert
**collapse()** | Collapses element  | void
**expand()** | Expands element  | void
**getText()** | Get current value | String
**is()** | Assert action | TextAssert

<a href="https://github.com/jdi-testing/jdi-light/blob/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/composite/section/navbar/ExternalContentTests.java" target=a_blank> Bootstrap test examples </a>
<br>


####Progress
Progress is located in the following class:

- __Java__: _com.epam.jdi.light.ui.bootstrap.elements.common.Progress_

<a style="font-weight: bold;" target="_blank" href="https://getbootstrap.com/docs/4.3/components/progress/">Progress</a> is custom progress bar featuring support for stacked bars, animated backgrounds, and text labels.

There is also a complex element <a style="font-weight: bold;" href="https://jdi-docs.github.io/jdi-light/?java#multiple-progress-bars">MultiplebarsProgress</a> which may consist of several progress bars.


![Progress example](../../images/bootstrap/progress.png)

Here is an example with provided Bootstrap v4.3 code:_

```java 
//FindBy(css = "#progress-bar-base-width-25 .progress-bar"
@UI("#progress-bar-base-width-25 .progress-bar")  
public static Progress progressBaseWidth25;

@Test(dataProvider = "progressWidth")
public void getWidthTest(Progress progress, String width) {
   progress.is().value(width);
}

@Test(dataProvider = "progressColor")
public void getColorTest(Progress progress, String color) {
   progress.is().color(color);
}
```

```html 
<div id="progress-base">
    <p>base</p>
    <div class="progress" id="progress-bar-base-width-0">
        <div class="progress-bar" role="progressbar" aria-valuenow="0" aria-valuemin="0" aria-valuemax="100"></div>
    </div>
    <div class="progress" id="progress-bar-base-width-25">
        <div class="progress-bar" role="progressbar" style="width: 25%" aria-valuenow="25" aria-valuemin="0" aria-valuemax="100"></div>
    </div>
    <div class="progress" id="progress-bar-base-width-50">
        <div class="progress-bar" role="progressbar" style="width: 50%" aria-valuenow="50" aria-valuemin="0" aria-valuemax="100"></div>
    </div>
    <div class="progress" id="progress-bar-base-width-75">
        <div class="progress-bar" role="progressbar" style="width: 75%" aria-valuenow="75" aria-valuemin="0" aria-valuemax="100"></div>
    </div>
    <div class="progress" id="progress-bar-base-width-100">
        <div class="progress-bar" role="progressbar" style="width: 100%" aria-valuenow="100" aria-valuemin="0" aria-valuemax="100"></div>
    </div>
</div>
```

Available methods in Java JDI Light:

|Method/Property | Description | Return Type
--- | --- | ---
**animated()** | Match passed value with the progress css _'animation-name'_ | ProgressAssert
**color()** | Match passed value with the progress css _'background-color'_ | ProgressAssert
**getValue()** | Get aria value of the bar | String
**getMaxValue()** | Get max value of the bar  | String
**getMinValue()** | Get min value of the bar  | String
**getColor()** | Get color of the bar  | String
**getStyle()** | Get style of the bar | String
**height()** | Match passed value with the progress height | ProgressAssert
**is()** | Various assert actions for Progress | ProgressAssert
**maxValue()** | Match passed value with the progress value _'aria-valuemax'_ | ProgressAssert
**minValue()** | Match passed value with the progress value _'aria-valuemin'_ | ProgressAssert
**value()** | Match passed value with the progress value _'aria-valuenow'_ | ProgressAssert

<a href="https://github.com/jdi-testing/jdi-light/blob/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/common/progress/ProgressBaseTests.java" target=a_blank> Bootstrap test examples </a>

<br><br><br><br><br>

#####Labels

Add <a style="font-weight: bold;" target="_blank" href="https://getbootstrap.com/docs/4.3/components/progress/#labels">labels</a> to your progress bars by placing text within the `.progress-bar`.

![Progress label example](../../images/bootstrap/progress-label.png)

Here is an example with provided Bootstrap v4.3 code:

```java 
//@FindBy(css = "#progress-with-labels")
@UI("#progress-with-labels") 
public static Progress progressWithLabels; 

@Test
public void getDefaultPercentTest() {
   assertThat(progressWithLabels.core().getText(), is(defaultPercent));
}
 
@Test
public void getPercentTest() {
   progressWithLabels.core().is().text(defaultPercent);
   minus.click();
   progressWithLabels.core().is().text("20%");
   for (int i = 0; i < 10; i++) {
       minus.click();
   }
   progressWithLabels.core().is().text(minPercent);
   plus.click();
   progressWithLabels.core().is().text("5%");
   for (int i = 0; i < 30; i++) {
       plus.click();
   }
   progressWithLabels.core().is().text(maxPercent);
}
```

```html 
<div class="progress">
    <div id="progress-with-labels" class="progress-bar" role="progressbar" style="width: 25%;" aria-valuenow="25" aria-valuemin="0" aria-valuemax="100">25%</div>
</div>
```

<a href="https://github.com/jdi-testing/jdi-light/tree/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/common/progress/ProgressWithLabelsTests.java" target=a_blank> Bootstrap test examples </a>

<br><br><br><br><br><br><br><br><br><br><br><br><br><br>

#####Height

We only set a <a style="font-weight: bold;" target="_blank" href="https://getbootstrap.com/docs/4.3/components/progress/#height">height</a>
value on the .progress, so if you change that value the inner .progress-bar will automatically resize accordingly.

![Progress height example](../../images/bootstrap/progress_height.PNG)

Here is an example with provided Bootstrap v4.3 code:

```java 
//@FindBy(css = "#progress-height .progress")
@UI("#progress-height .progress")
public static JList<ProgressSection> progressHeightSections;

@Test
public void heightOfSectionShouldBeValid() {
   for (ProgressSection section : progressHeightSections) {
       int actualHeight = section.core().getSize().getHeight();
       int expectedHeight = section.getProgressSectionHeightValueInPx();
       assertEquals(actualHeight, expectedHeight);
   }
}

@Test
public void heightOfBarShouldBeValid() {
   for (ProgressSection section : progressHeightSections) {
       int expectedBarHeight = section.getProgressSectionHeightValueInPx();
       section.progress.is().height(expectedBarHeight);
   }
}

```

```html 
<div id="progress-height">
    <p>various heights</p>
          <div class="progress" id="progress-height-20px" style="height: 20px;">
              <div class="progress-bar bg-success" role="progressbar" style="width: 25%" aria-valuenow="25" aria-valuemin="0" aria-valuemax="100"></div>
          </div>
          <div class="progress" id="progress-height-40px" style="height: 40px;">
              <div class="progress-bar bg-info" role="progressbar" style="width: 50%" aria-valuenow="50" aria-valuemin="0" aria-valuemax="100"></div>
          </div>
          <div class="progress" id="progress-height-60px" style="height: 60px;">
              <div class="progress-bar bg-warning" role="progressbar" style="width: 75%" aria-valuenow="75" aria-valuemin="0" aria-valuemax="100"></div>
          </div>
          <div class="progress" id="progress-height-80px" style="height: 80px;">
              <div class="progress-bar bg-danger" role="progressbar" style="width: 100%" aria-valuenow="100" aria-valuemin="0" aria-valuemax="100"></div>
          </div>
      </div>
```  

<a href="https://github.com/jdi-testing/jdi-light/tree/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/common/progress/ProgressHeightTests.java" target=a_blank> Bootstrap test examples </a>

<br><br><br><br><br>

#####Backgrounds

Use <a style="font-weight: bold;" target="_blank" href="https://getbootstrap.com/docs/4.3/components/progress/#backgrounds">background</a> utility classes to change the appearance of individual progress bars.

![Progress backgroundsexample](../../images/bootstrap/progress-backgrounds.png)

Here is an example with provided Bootstrap v4.3 code:

```java 
//@FindBy(css = "#progress-background-green")
@UI("#progress-backgrounds-green") public static Progress progressBackgroundGreen;
//@FindBy(css = "#progress-background-blue")
@UI("#progress-backgrounds-blue") public static Progress progressBackgroundBlue;
//@FindBy(css = "#progress-background-yellow")
@UI("#progress-backgrounds-yellow") public static Progress progressBackgroundYellow;
//@FindBy(css = "#progress-background-red")
@UI("#progress-backgrounds-red") public static Progress progressBackgroundRed;

@DataProvider(name = "progressBackgroundsWithAttributes")
public static Object[][] progressBackgroundsWithAttributes() {
   return new Object[][]{
           {progressBackgroundGreen, 25, "rgba(40, 167, 69, 1)"},
           {progressBackgroundBlue, 50, "rgba(23, 162, 184, 1)"},
           {progressBackgroundYellow, 75, "rgba(255, 193, 7, 1)"},
           {progressBackgroundRed, 100, "rgba(220, 53, 69, 1)"}
   };
}

@Test(dataProvider = "progressBackgroundsWithAttributes")
public void isValidationTest(ICoreElement progressBackground, int widthNumber, String color) {
   progressBackground.core().is()
           .tag(is("div"))
           .attr("role", "progressbar")
           .attr("style", String.format("width: %s%%;", widthNumber))
           .attr("aria-valuenow", widthNumber + "")
           .attr("aria-valuemin", "0")
           .attr("aria-valuemax", "100")
           .css("background-color", color);
}

```

```html 
<div class="progress">
    <div id="progress-backgrounds-green" class="progress-bar bg-success" role="progressbar" style="width: 25%" aria-valuenow="25" aria-valuemin="0" aria-valuemax="100"></div>
</div>
<div class="progress">
    <div id="progress-backgrounds-blue" class="progress-bar bg-info" role="progressbar" style="width: 50%" aria-valuenow="50" aria-valuemin="0" aria-valuemax="100"></div>
</div>
<div class="progress">
    <div id="progress-backgrounds-yellow" class="progress-bar bg-warning" role="progressbar" style="width: 75%" aria-valuenow="75" aria-valuemin="0" aria-valuemax="100"></div>
</div>
<div class="progress">
    <div id="progress-backgrounds-red" class="progress-bar bg-danger" role="progressbar" style="width: 100%" aria-valuenow="100" aria-valuemin="0" aria-valuemax="100"></div>
</div>
```

<a href="https://github.com/jdi-testing/jdi-light/blob/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/common/progress/ProgressBackgroundTests.java" target=a_blank> Bootstrap test examples </a>

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

#####Striped

Add <a style="font-weight: bold;" target="_blank" href="https://getbootstrap.com/docs/4.3/components/progress/#striped">.progress-bar-striped</a> to any `.progress-bar to apply` a stripe via CSS gradient over the progress bar’s background color.

![Progress striped example](../../images/bootstrap/progress-striped.png)

Here is an example with provided Bootstrap v4.3 code:

```java 
//@FindBy(css = "#striped-base .progress")    
@UI("#striped-base .progress") 
public static JList<ProgressSection> progressSections;
   
@Test(dataProvider = "progressData")
public void checkProgressData(String progressId, String value, String color,
                              String min, String max, String classStriped
    progressSections.stream().filter(progressSection ->
            progressSection.progress.attr("id").equals(progressId)).forEach(
            progressSection -> {
                progressSection.progress.is().core().hasClass(classStriped);
                progressSection.progress.is().value(value)
                        .color(color)
                        .minValue(min)
                        .maxValue(max);
            });
}

```

```html 
<div id="striped-base">
    <br>
    <p>striped</p>

    <div class="progress">
        <div class="progress-bar progress-bar-striped" id="striped_ordinary" role="progressbar" style="width: 10%" aria-valuenow="10" aria-valuemin="0" aria-valuemax="100"></div>
    </div>
    <div class="progress">
        <div class="progress-bar progress-bar-striped bg-success" id="striped_success" role="progressbar" style="width: 25%" aria-valuenow="25" aria-valuemin="0" aria-valuemax="100"></div>
    </div>
    <div class="progress">
        <div class="progress-bar progress-bar-striped bg-info" id="striped_info" role="progressbar" style="width: 50%" aria-valuenow="50" aria-valuemin="0" aria-valuemax="100"></div>
    </div>
    <div class="progress">
        <div class="progress-bar progress-bar-striped bg-warning" id="striped_warning" role="progressbar" style="width: 75%" aria-valuenow="75" aria-valuemin="0" aria-valuemax="100"></div>
    </div>
    <div class="progress">
        <div class="progress-bar progress-bar-striped bg-danger" id="striped_danger" role="progressbar" style="width: 100%" aria-valuenow="100" aria-valuemin="0" aria-valuemax="100"></div>
    </div>
</div>
```

<a href="https://github.com/jdi-testing/jdi-light/blob/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/common/progress/ProgressBarsListTests.java" target=a_blank> Bootstrap test examples </a>

<br><br><br><br><br><br>


#####Animated stripes

The striped gradient can also be <a style="font-weight: bold;" target="_blank" href="https://getbootstrap.com/docs/4.3/components/progress/#animated-stripes">animated</a>.
Add .progress-bar-animated to .progress-bar to animate the stripes right to left via CSS3 animations.

Here is an example with provided Bootstrap v4.3 code:

```java 
//FindBy(css = "#progress-animated")
@UI("#progress-animated") 
public static Progress progressAnimated;

@Test
public void isValidationTest() {
   progressAnimated.is()
           .animated("progress-bar-stripes")
           .color("rgba(0, 123, 255, 1)")
           .value("75");
}
```

```html 
<div class="progress">
    <div class="progress-bar progress-bar-striped progress-bar-animated" id="progress-animated" role="progressbar" aria-valuenow="75" aria-valuemin="0" aria-valuemax="100" style="width: 75%"></div>
</div>
```

<a href="https://github.com/jdi-testing/jdi-light/blob/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/common/progress/ProgressAnimatedStripesTests.java" target=a_blank> Bootstrap test examples </a>
<br><br><br><br><br><br><br><br>

####Spinners

Bootstrap “spinners” can be used to show the loading state in your projects.
They’re built only with HTML and CSS, meaning you don’t need any JavaScript to create them.
You will, however, need some custom JavaScript to toggle their visibility.
Their appearance, alignment, and sizing can be easily customized with Bootstrap utility classes.

For accessibility purposes, each loader in the examples below includes ``role="status"`` and a nested ``<span class="sr-only">Loading...</span>``.

Spinners are represented by the following class in JDI:

- __Java__: <a href="https://github.com/jdi-testing/jdi-light/blob/bootstrap/jdi-light-bootstrap/src/main/java/com/epam/jdi/light/ui/bootstrap/elements/common/Spinner.java">Spinner</a>
- __C#__: TBD


Available methods in Java JDI Light:

|Method/Property | Description | Return Type
--- | --- | ---
**color()**	 |  Assert action	| SpinnerAssert
**disappearAfter(int sec)**|Wait when spinner disappear | Spinner
**getColor()** |Get item color | String
**is()**	 |  Assert action	| SpinnerAssert


**Border Spinner**

```java 

// @FindBy(id = "button-show-spinner-border")
@UI("#button-show-spinner-border") 
public static Button buttonSpinnerBorder; 
// @FindBy(css = "#spinner-border")
@UI("#spinner-border") public static Spinner spinnerBorder; 

@Test()
public void checkSpinnerClass() {
  spinnerBorder.assertThat().core().hasClass("spinner-border");
}

@Test(priority = 1)
public void checkSpinnerAppearAndThenDisappear() {
  buttonSpinnerBorder.click();
  spinnerBorder.disappearAfter(4);
}

```

<a style="font-weight:bold" href="https://getbootstrap.com/docs/4.3/components/spinners/#border-spinner" target="_blank">Border Spinner</a> - use the border spinners for a lightweight loading indicator.

![Border Spinner Example](../../images/bootstrap/borderspinner.png)


Here is an example with provided Bootstrap v4.3 code:

```html
<div class="spinner-border" role="status">
    <span class="sr-only">Loading...</span>
</div>
```

[Bootstrap test examples](https://github.com/jdi-testing/jdi-light/tree/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/common/spinner/SpinnerBorderTests.java)


##### Colors
 ```java 
 // @FindBy(id = "spinner-text-primary")
 @UI("#spinner-text-primary") 
 public static Spinner spinnerWithTextPrimary; 
 // @FindBy(css = "#spinner-text-light")
 @UI("#spinner-text-light") 
 public static Spinner spinnerWithTextLight; 
 
 @Test(dataProvider = "Color Spinners")
 public void assertColorTests(Spinner colorSpinner, String color)
 {
     colorSpinner.is().color(color);
  }
 
 @Test(dataProvider = "Color Spinners")
 public void assertSpinnerColorTests(Spinner colorSpinner,
                                             String color){
     colorSpinner.is()
         .core()
         .cssClass(containsString(color));
  }
 
 @Test(dataProvider = "Color Spinners")
 public void assertColorByHasClassTests(Spinner colorSpinner,
                                                String color){
     colorSpinner.core().hasClass("spinner-border" + color);
  }
 
 @Test(dataProvider = "Color Spinners")
 public void isValidationTest(Spinner colorSpinner, String __){
     colorSpinner.is()
         .displayed()
         .core()
         .css("font-size", is("14px"))
         .cssClass(containsString("spinner-border"))
         .attr("role", "status");
  }
 ```

The border spinner uses <a style="font-weight:bold" href="https://getbootstrap.com/docs/4.3/components/spinners/#colors" target="_blank">currentColor</a>
for its border-color,
meaning you can customize the color with <a href="https://getbootstrap.com/docs/4.3/utilities/colors/" target="_blank">text color utilities</a>.
You can use any of our text color utilities on the standard spinner.


![Colored Spinners Example](../../images/bootstrap/coloredspinners.png)
Here is an example with provided Bootstrap v4.3 code:

```html
<div class="spinner-border text-primary" role="status" id="spinner-text-primary">
    <span class="sr-only">Loading...</span>
</div>
<div class="spinner-border text-secondary" role="status" id="spinner-text-secondary">
    <span class="sr-only">Loading...</span>
</div>
<div class="spinner-border text-success" role="status" id="spinner-text-success">
    <span class="sr-only">Loading...</span>
</div>
<div class="spinner-border text-danger" role="status" id="spinner-text-danger">
    <span class="sr-only">Loading...</span>
</div>
<div class="spinner-border text-warning" role="status" id="spinner-text-warning">
    <span class="sr-only">Loading...</span>
</div>
<div class="spinner-border text-info" role="status" id="spinner-text-info">
    <span class="sr-only">Loading...</span>
</div>
<div class="spinner-border text-light" role="status" id="spinner-text-light">
    <span class="sr-only">Loading...</span>
</div>
<div class="spinner-border text-dark" role="status" id="spinner-text-dark">
    <span class="sr-only">Loading...</span>
</div>
```

<a href="https://github.com/jdi-testing/jdi-light/blob/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/common/spinner/SpinnerColorTests.java" target="_blank">Bootstrap test example with colored spinners</a>

<br><br>

##### Growing Spinners

```java 

// @FindBy(id = "growing-spinners")
@UI("#growing-spinners")
public static GrowingSpinnersSection growingSpinners;

// @FindBy(css = ".text-primary")
@UI(".text-primary")
public Spinner primarySpinner;

// @FindBy(css = ".text-secondary")
@UI(".text-secondary")
public Spinner secondarySpinner;

// @FindBy(css = ".text-success")
@UI(".text-success")
public Spinner successSpinner;

// @FindBy(css = ".text-danger")
@UI(".text-danger")
public Spinner dangerSpinner;

private static final String spinnerGrowClass = "spinner-grow";

@DataProvider
public Object[][] spinnerData() {
    return new Object[][] {
            {growingSpinners.primarySpinner},
            {growingSpinners.secondarySpinner},
            {growingSpinners.successSpinner},
            {growingSpinners.dangerSpinner}
    };
}

@Test(dataProvider = "spinnerData")
public void spinnerHasGrowClassTest(Spinner spinner) {
    spinner.highlight();
    spinner.is().core().hasClass(spinnerGrowClass);
}

@Test(dataProvider = "spinnerData")
public void isValidationTest(Spinner spinner) {
    spinner.highlight();
    spinner
            .is()
            .displayed()
            .and()
            .enabled();
}
```

If you don’t fancy a border spinner, switch to the <a style="font-weight: bold;" href="https://getbootstrap.com/docs/4.3/components/spinners/#growing-spinner" target="_blank">grow spinner</a>.

Once again, this spinner is built with currentColor, so you can easily change its appearance with <a href="https://getbootstrap.com/docs/4.3/utilities/colors/" target="_blank">text color utilities</a>.
Below it is in blue, along with the supported variants.

![Growing Spinners Example](../../images/bootstrap/growingspinners.png)


Here is an example with provided Bootstrap v4.3 code:

```html
<div id="growing-spinners">
    <div class="spinner-grow text-primary" role="status">
        <span class="sr-only">Loading...</span>
    </div>
    <div class="spinner-grow text-secondary" role="status">
        <span class="sr-only">Loading...</span>
    </div>
    <div class="spinner-grow text-success" role="status">
        <span class="sr-only">Loading...</span>
    </div>
    <div class="spinner-grow text-danger" role="status">
        <span class="sr-only">Loading...</span>
    </div>
    <div class="spinner-grow text-warning" role="status">
        <span class="sr-only">Loading...</span>
    </div>
    <div class="spinner-grow text-info" role="status">
        <span class="sr-only">Loading...</span>
    </div>
    <div class="spinner-grow text-light" role="status">
        <span class="sr-only">Loading...</span>
    </div>
    <div class="spinner-grow text-dark" role="status">
        <span class="sr-only">Loading...</span>
    </div>
</div>
```

<a href="https://github.com/jdi-testing/jdi-light/blob/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/common/spinner/GrowingSpinnersTests.java" target="_blank">Bootstrap Test Examples</a>

<br><br><br><br><br><br>

##### Spinner Alignment

Spinners in Bootstrap are built with ``rem``s, ``currentColor``, and ``display: inline-flex``.
This means they can easily be resized, recolored, and <a style="font-weight: bold;" href="https://getbootstrap.com/docs/4.3/components/spinners/#alignment" target="_blank">quickly aligned</a>.


**Spinner Margin**

```java 

// @FindBy(id = "spinner-alignment")
@UI("#spinner-alignment") 
public static SpinnerAlignmentSection spinnerAlignment

@Test(dataProvider = "spinnerData")
public void isValidationTest(Spinner spinner) {
    spinner.children().get(0).highlight();
    spinner
            .is()
            .enabled()
            .and()
            .displayed();
}

@Test(dataProvider = "spinnerStyleData")
public void spinnerAlignmentStyleTest(Spinner spinner,
                                       String style) {
    spinner.is().core().hasClass(style);
}
```

Use margin utilities like ``.m-5`` for easy spacing.

![Spinner Margin Example](../../images/bootstrap/spinnermargin.png)


Here is an example with provided Bootstrap v4.3 code:

```html
<div class="border mb-3 p-3">
    <div class="spinner-border" role="status">
        <span class="sr-only">Loading...</span>
    </div>
</div>
```

**Spinner Placement**

Use <a href="https://getbootstrap.com/docs/4.3/utilities/flex/" target="_blank">flexbox utilities</a>,
<a href="https://getbootstrap.com/docs/4.3/utilities/float/" target="_blank">float utilities</a>, or <a href="https://getbootstrap.com/docs/4.3/content/typography/" target="_blank">text alignment</a> utilities
to place spinners exactly where you need them in any situation.


**Spinner Flex**

![Spinner Flex Center Example](../../images/bootstrap/spinner-flex-center.png)

![Spinner Flex Center HTML Example](../../images/bootstrap/spinner-flex-right.png)

Here are the examples with provided Bootstrap v4.3 code:

```html
<div class="d-flex justify-content-center border mb-3 p-3">
    <div class="spinner-border" role="status">
        <span class="sr-only">Loading...</span>
    </div>
</div>
```

```html
<div class="d-flex align-items-center border mb-3 p-3">
    <div class="spinner-border ml-auto" role="status" 
        aria-hidden="true"></div>
</div>
```


**Spinner Floats**

![Spinner Float Right Example](../../images/bootstrap/spinnerfloat.png)

Here is an example with provided Bootstrap v4.3 code:

```html
<div class="clearfix border mb-3 p-3">
    <div class="spinner-border float-right" role="status">
        <span class="sr-only">Loading...</span>
    </div>
</div>
```


**Spinner Text Align**

![Spinner Text Align Center Example](../../images/bootstrap/spinner-text-align.png)

Here is an example with provided Bootstrap v4.3 code:

```html
<div class="text-center mb-3 border p-3">
    <div class="spinner-border" role="status">
        <span class="sr-only">Loading...</span>
    </div>
</div>
```

<a href="https://github.com/jdi-testing/jdi-light/blob/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/common/spinner/SpinnerAlignmentTests.java" target="_blank">Bootstrap Test Examples</a>

##### Spinner Size

```java 

// @FindBy(id = "spinner-size")
@UI("#spinner-size") 
public static SpinnerSizeSection spinnerSize;

// @FindBy(css = ".spinner-border-sm")
@UI(".spinner-border-sm")
public Spinner smallSpinner;

// @FindBy(css = ".spinner-grow-sm")
@UI(".spinner-grow-sm")
public Spinner smallGrowingSpinner;

// @FindBy(id = "spinBorder")
@UI("#spinBorder")
public Spinner spinner;

// @FindBy(id = "spinGrow")
@UI("#spinGrow")
public Spinner growingSpinner;

private static final String smallSpinnerClass =
                                     "spinner-border-sm";
private static final String smallGrowingSpinnerClass =
                                     "spinner-grow-sm";
private static final String spinnerStyleValue = 
        "width: 3rem; height: 3rem; border: 3px dashed red";

@DataProvider
public Object[][] spinnerData() {
    return new Object[][] {
            {spinnerSize.smallSpinner},
            {spinnerSize.smallGrowingSpinner},
            {spinnerSize.spinner},
            {spinnerSize.growingSpinner}
    };
}

@Test(dataProvider = "spinnerData")
public void isValidationTest(Spinner spinner) {
    spinner.highlight();
    spinner.is().enabled().and().displayed();
}

@Test
public void spinnerClassTest() {
    spinnerSize.smallSpinner.is().core().
    hasClass(smallSpinnerClass);
    spinnerSize.smallGrowingSpinner.
    is().
    core().
    hasClass(smallGrowingSpinnerClass);
}

@Test
public void spinnerStylingTest() {
    spinnerSize.spinner.
    is().core().
    attr("style", spinnerStyleValue);
    spinnerSize.growingSpinner.is().core().
    attr("style", spinnerStyleValue);
}
```

Add ``.spinner-border-sm`` and ``.spinner-grow-sm``
to make a <a href="https://getbootstrap.com/docs/4.3/components/spinners/#size" target="_blank">smaller spinner</a>
that can quickly be used within other components.

![Spinner Size Native Example](../../images/bootstrap/spinner-size-native.png)


<br>
Here is an example with provided Bootstrap v4.3 code:

```html
<div class="border mb-3 p-3 text-center">
    <div class="spinner-border spinner-border-sm" role="status">
        <span class="sr-only">Loading...</span>
    </div>
    <div class="spinner-grow spinner-grow-sm" role="status">
        <span class="sr-only">Loading...</span>
    </div>
</div>
```
<br>
Or, use custom CSS or inline styles to change the dimensions as needed.

![Spinner Size CSS Example](../../images/bootstrap/spinner-size-css.png)

<br>
Here is an example with provided Bootstrap v4.3 code:

```html
<div id="spinner-size">
    <div class="border mb-3 p-3 text-center">
        <div class="spinner-border" id="spinBorder"
             style="width: 3rem; height: 3rem;"
             role="status">
            <span class="sr-only">Loading...</span>
        </div>
        <div class="spinner-grow" id="spinGrow"
             style="width: 3rem; height: 3rem;"
             role="status">
            <span class="sr-only">Loading...</span>
        </div>
    </div>
</div>
```
<br>
<a href="https://github.com/jdi-testing/jdi-light/blob/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/common/spinner/SpinnerSizeTests.java" target="_blank">Bootstrap Test Examples</a>

<br><br><br><br><br><br><br>

#### Spinner Buttons

Use <a href="https://getbootstrap.com/docs/4.3/components/spinners/#buttons" target="_blank">spinners within buttons</a> to indicate an action is currently processing or taking place.
You may also swap the text out of the spinner element and utilize button text as needed.

![Spinner Buttons Example](../../images/bootstrap/spinnerbuttons.png)

Buttons with spinner are represented by ButtonWithSpinner class in Java:

- __Java__: <a href="https://github.com/jdi-testing/jdi-light/blob/bootstrap/jdi-light-bootstrap/src/main/java/com/epam/jdi/light/ui/bootstrap/elements/complex/ButtonWithSpinner.java">ButtonWithSpinner</a>
- __C#__: TBD

Available methods in Java JDI Light for ButtonWithSpinner:

|Method | Description | Return Type
--- | --- | ---
**click()** | Click the button  | void
**getText()** | Get button text | String
**is()** | Assert action | TextAssert

The inner element is  [Spinner](https://jdi-docs.github.io/jdi-light/#spinners)

<br>

<a href="https://github.com/jdi-testing/jdi-light/blob/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/common/spinner/SpinnerButtonsTests.java" target="_blank">Bootstrap Test Examples</a>


```java 

public class ButtonWithSpinner extends Button{
    // @FindBy(css = "[class*='spinner']")
    public @UI("[class*='spinner']") Spinner spinner;
}

// @FindBy(id = "#button-with-spinner-and-text")
@UI("#button-with-spinner-and-text") 
public static ButtonWithSpinner buttonWithSpinnerAndText;

private final String spinnerClassName = "spinner-border";

@Test()
public void checkButtonText() {
    assertTrue(buttonWithSpinnerAndText.isDisplayed());
    buttonWithSpinnerAndText.assertThat().text(is(buttonText));
}

@Test()
public void checkSpinnerInButtonWithText() {
    buttonWithSpinnerAndText.spinner.is().core()
    .hasClass(spinnerClassName);
    buttonWithSpinnerAndText.spinner
        .is()
        .displayed()
        .and()
        .enabled();
}

```
<br>
Here is an example with provided Bootstrap v4.3 code:

```html
 <div class="border text-center p-3 mb-3">
     <button class="btn btn-primary" type="button" 
            disabled="" id="button-with-spinner">
         <span class="spinner-border spinner-border-sm"
               role="status"
               id=spinner-in-button" aria-hidden="true">
               
        </span>
         <span class="sr-only">Loading...</span>
     </button>
     <button class="btn btn-primary"
             type="button" disabled=""
             id="button-with-spinner-and-text">
         <span class="spinner-border spinner-border-sm"
               role="status"
               id=spinner-in-button-with-text"
               aria-hidden="true"></span>
         Loading...
     </button>
 </div>

 <div class="border text-center p-3 mb-3">
     <button class="btn btn-primary" 
            type="button" disabled=""
             id="button-with-growing-spinner">
         <span class="spinner-grow spinner-grow-sm"
                role="status"
               id=growing-spinner-in-button" 
               aria-hidden="true">             
        </span>
         <span class="sr-only">Loading...</span>
     </button>
     <button class="btn btn-primary" 
             type="button" disabled=""
             id="button-with-growing-spinner-and-text">
         <span class="spinner-grow spinner-grow-sm"
               role="status"
               id=growing-spinner-in-button-with-text"
                aria-hidden="true"></span>
         Loading...
     </button>
 </div>
```


#### Tooltip
<a style="font-weight:bold" href="https://getbootstrap.com/docs/4.3/components/tooltips/" target="_blank">Tooltip</a> is a hint that used in conjuction with a pointer.

![Tooltip top](../../images/bootstrap/tooltip_top.png)

![Tooltip bottom](../../images/bootstrap/tooltip_bottom.png)

![Tooltip left](../../images/bootstrap/tooltip_left.png)

![Tooltip right](../../images/bootstrap/tooltip_right.png)

![Tooltip with title](../../images/bootstrap/tooltip_with_html.png)

![Tooltip disabled](../../images/bootstrap/tooltip_disabled.png)

```java 

@UI("#tooltipOnTop") public static Tooltip tooltipOnTopButton; //@FindBy(css = "#tooltipOnTop")
@UI("#tooltipOnLeft") public static Tooltip tooltipOnLeftButton; //@FindBy(css = "#tooltipOnLeft")

@Test(dataProvider = "Tooltips")
public void getTooltipTextTests(Tooltip tooltip, String tooltipText) {
    assertEquals(tooltip.getTooltipText(), tooltipText);
}

@Test(dataProvider = "TooltipsPlacements")
public void tooltipPlacementTests(Tooltip tooltip, String placement) {
    assertEquals(tooltip.getTooltipPlacement(), placement);
}

@Test(dataProvider = "Tooltips")
public void tooltipIsVisibleByHoverTests(Tooltip tooltip, String __)
    tooltip.core().hover();
    tooltip.assertThat().isVisible();
}

@Test(dataProvider = "Tooltips")
public void tooltipIsInvisibleTests(Tooltip tooltip, String __) {
    tooltip.is().hidden();
}

@Test
public void tooltipWithHtmlTest() {
    assertTrue(tooltipWithHTML.isTooltipWithHTML());
}
```

Here is an example with provided Bootstrap v4.3 code:

```html
<button type="button" class="btn btn-info btn-block" id="tooltipOnTop" data-toggle="tooltip"
        data-placement="top" title="Tooltip on top">Tooltip on top
</button>
<hr>
<button type="button" class="btn btn-info btn-block" id="tooltipOnRight" data-toggle="tooltip"
        data-placement="right" title="Tooltip on right">Tooltip on right
</button>
<hr>
<button type="button" class="btn btn-info btn-block" id="tooltipOnBottom" data-toggle="tooltip"
        data-placement="bottom" title="Tooltip on bottom">Tooltip on bottom
</button>
<hr>
<button type="button" class="btn btn-info btn-block" id="tooltipOnLeft" data-toggle="tooltip"
        data-placement="left" title="Tooltip on left">Tooltip on left
</button>
<hr>
<button type="button" class="btn btn-info btn-block" id="tooltipWithHTML" data-toggle="tooltip"
        data-html="true" title="<em>Tooltip</em> <u>with</u> <b>HTML</b>">Tooltip with HTML
</button>
<hr>
<span class="d-inline-block" id="wrapperForDisabledButton" tabindex="0" data-toggle="tooltip"
      title="Disabled tooltip">
		<button class="btn btn-info btn-block" id="tooltipOnDisabledButton"
                style="pointer-events: none;" type="button" disabled>Disabled button</button>
</span>
```

Available methods in Java JDI Light:

|Method/Property | Description | Return Type
--- | --- | ---
assertThat()	 |  Assert action	| TooltipAssert
click() | Click the item  | void
getText() |Get item text  |  String
getValue() |Get item value  |  String
getTooltipText() |Get tooltip text |String
getTooltipPlacement() |Get tooltip placement| String
isTooltipWithHTML() |Check that tooltip contains html text |boolean
is()	 |  Assert action	| UIAssert

<a href="https://github.com/jdi-testing/jdi-light/blob/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/common/TooltipTests.java" target="_blank">Bootstrap test example with tooltips</a>

<br>

####Image

<a style="font-weight:bold" href="https://getbootstrap.com/docs/4.3/content/images/" target="_blank">Images</a> is a hint that used in conjuction with a pointer.

```java 
    //@FindBy(css = "#card-image")
    @UI("#card-image")
    public static CardImage cardImage;

    public class CardImage extends Card {
        @UI(".card-text") public Text text;
        @UI("#bs-card-image") public Image image;
    }

    @Test
    public void availabilityTest() {
        cardImage.image.is()
                .displayed()
                .enabled();
    }

    @Test
    public void getAltTest() {
        assertEquals(cardImage.image.alt(), ALT_ATTR_EXPECTED);
    }

    @Test
    public void isValidationTest() {
        cardImage.image.is().src(is(SRC_ATTR_EXPECTED));
        cardImage.image.is().alt(is(ALT_ATTR_EXPECTED));
        cardImage.image.unhighlight();
        cardImage.image.assertThat().width(is(WIDTH));
        cardImage.image.assertThat().height(is(HEIGHT));
    }

    @Test
    public void imageClassTest() {
        cardImage.image.is().core().hasClass(IMAGE_TOP_CLASS);
        cardImage.image.assertThat().core().hasClass(IMAGE_TOP_CLASS);
    }
```

Here is an example with provided Bootstrap v4.3 code:

```html
<div class="card mb-3" id="card-image-caps-1" style="width: 18rem;">
  <img style="width: 30%; margin: 0 auto;" src="images/captain-america.jpg" class="card-img-top"
    alt="Captain America image">
</div>
```

Available methods in Java JDI Light:

|Method/Property | Description | Return Type
--- | --- | ---
alt() | Assert alt image attribute  | ImageAssert
assertThat()	 |  Assert action	| ImageAssert
getText() | Get item text | String
getValue() |Get item value  |  String
height() | Assert image height | ImageAssert
is()	 |  Assert action	| UIAssert
width() | Assert image width | ImageAssert

<a href="https://github.com/jdi-testing/jdi-light/blob/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/common/ImageTests.java" target="_blank">Bootstrap test example with tooltips</a>

<br>


### Bootstrap Complex elements

####Collapse

The <a style="font-weight: bold;" href="https://getbootstrap.com/docs/4.3/components/collapse/" target="_blank">collapse</a> is used to show and hide content.
Buttons or anchors are used as triggers that are mapped to specific elements you toggle.

``Collapse`` extends JDI Light's ``DropdownExpand``, thus inheriting its methods.<br>
You can use a ``@JDropdown`` annotation to declare a Collapse within your Page Object.

![Collapse example](../../images/bootstrap/collapse.png)

Here is an example with provided Bootstrap v4.3 code:

```java 
@JDropdown(expand = "#bs-group-toggle-one",
            value = "#bs-group-one",
            list = "#bs-group-one-body")
public static Collapse collapseGroupOne;

String groupOneText = "You probably haven't heard of them accusamus labore sustainable VHS.";

@Test
public void collapseGroupOneTest() {
    collapseGroupOne.highlight();
    collapseGroupOne.expand();

    collapseGroupOne.is().expanded();
    collapseGroupOne.value().is().text(groupOneText);

    collapseGroupOne.collapse();
    collapseGroupOne.is().collapsed();
}

@Test
public void collapseGroupOneListTest() {
    collapseGroupOne.highlight();
    collapseGroupOne.expand();

    collapseGroupOne.is().expanded();
    collapseGroupOne.list().is().size(1);
    collapseGroupOne.list().get(1).is().text(groupOneText);

    collapseGroupOne.collapse();
    collapseGroupOne.is().collapsed();
}
```

```html
<div class="accordion mb-3" id="accordionExample">
    <div class="card">
        <div class="card-header" id="headingOne">
            <h2 class="mb-0">
                <button id="bs-group-toggle-one" class="btn btn-link" type="button"
                        data-toggle="collapse" data-target="#bs-group-one"
                        aria-expanded="true" aria-controls="collapseOne">
                    Collapsible Group Item #1
                </button>
            </h2>
        </div>

        <div class="collapse"
             aria-labelledby="headingOne" data-parent="#accordionExample" id="bs-group-one">
            <div class="card-body" id="bs-group-one-body">You probably haven't heard of
                them accusamus labore sustainable VHS.
            </div>
        </div>
    </div>
</div>
```

Available methods in Java JDI Light:

|Method | Description | Return Type
--- | --- | ---
**assertThat()** | Assert action | UISelectAssert
**collapse()** | Collapses element  | void
**expand()** | Expands element  | void
**is()** | Various assert actions | UISelectAssert
**list()** | Returns collapse ``list()`` property | WebList
**value()** | Returns collapse ``value()`` property | UIElement

[Bootstrap test examples](https://github.com/jdi-testing/jdi-light/tree/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/complex/CollapseTests.java)

####Carousel
<a style="font-weight:bold" href="https://getbootstrap.com/docs/4.3/components/carousel/" target="_blank">Carousel</a> - a slideshow component for cycling through elements—images or slides of text—like a carousel.<br>

**Slides only**<br>
Here’s a carousel with slides only. Note the presence of the .d-block and .w-100 on carousel images to prevent browser default image alignment.

![Carousel slides only example](../../images/bootstrap/carousel-slides-only.png)

Here is an example with provided Bootstrap v4.3 code:

```java 

@UI("#carousel-example-slides-only")
public static Carousel carouselWithSlidesOnly;

@Test
public void getSlidesTextTest() {
    carouselWithSlidesOnly.is().text(firstSlideText);
    carouselWithSlidesOnly.is().text(secondSlideText);
}

``` 

```html 
<div id="carousel-example-slides-only" class="carousel slide mb-2" data-ride="carousel">
    <div class="carousel-inner">
        <div class="carousel-item active">
            <svg class="bd-placeholder-img bd-placeholder-img-lg d-block w-100" width="800"
                 height="400" xmlns="http://www.w3.org/2000/svg"
                 preserveAspectRatio="xMidYMid slice" focusable="false" role="img"
                 aria-label="Placeholder: First slide"><title>Placeholder</title>
                <rect width="100%" height="100%" fill="#777"></rect>
                <text x="34%" y="27%" fill="#555" dy=".3em" style="font-size:25px;">First
                    slide
                </text>
            </svg>
        </div>
        <div class="carousel-item">
            <svg class="bd-placeholder-img bd-placeholder-img-lg d-block w-100" width="800"
                 height="400" xmlns="http://www.w3.org/2000/svg"
                 preserveAspectRatio="xMidYMid slice" focusable="false" role="img"
                 aria-label="Placeholder: First slide"><title>Placeholder</title>
                <rect width="100%" height="100%" fill="#33AAFF"></rect>
                <text x="27%" y="27%" fill="#555" dy=".3em" style="font-size:25px;">Second
                    slide
                </text>
            </svg>
        </div>
        <div class="carousel-item">
            <svg class="bd-placeholder-img bd-placeholder-img-lg d-block w-100" width="800"
                 height="400" xmlns="http://www.w3.org/2000/svg"
                 preserveAspectRatio="xMidYMid slice" focusable="false" role="img"
                 aria-label="Placeholder: First slide"><title>Placeholder</title>
                <rect width="100%" height="100%" fill="#20AD1E"></rect>
                <text x="31%" y="27%" fill="#555" dy=".3em" style="font-size:25px;">Third
                    slide
                </text>
            </svg>
        </div>
    </div>
</div>
```

**With controls**<br>
Adding in the previous and next controls:

![Carousel with controls example](../../images/bootstrap/carousel-with-controls.png)

Here is an example with provided Bootstrap v4.3 code:

```java 
@UI("#carousel-example-controls") // @FindBy(css = "#carousel-example-controls")
public static Carousel carouselWithControls;

@Test
public void prevTest() {
	carouselWithControls.prev();	
	carouselWithControls.is().text(firstSlideText);
	carouselWithControls.prevControl().is().text(prevText);
	
	carouselWithControls.next();	
	carouselWithControls.is().text(secondSlideText);
	carouselWithControls.nextControl().is().text(prevText);
}

@Test
public void getTextTest() {
    assertEquals(carouselWithControls.getText(), thirdSlideText);
}

```

```html 
<div id="carousel-example-controls" class="carousel slide mb-2" data-ride="carousel">
    <div class="carousel-inner">
        <div class="carousel-item">
            <svg class="bd-placeholder-img bd-placeholder-img-lg d-block w-100" width="800"
                 height="400" xmlns="http://www.w3.org/2000/svg"
                 preserveAspectRatio="xMidYMid slice" focusable="false" role="img"
                 aria-label="Placeholder: First slide"><title>Placeholder</title>
                <rect width="100%" height="100%" fill="#777"></rect>
                <text x="34%" y="27%" fill="#555" dy=".3em" style="font-size:25px;">First
                    slide
                </text>
            </svg>
        </div>
        <div class="carousel-item">
            <svg class="bd-placeholder-img bd-placeholder-img-lg d-block w-100" width="800"
                 height="400" xmlns="http://www.w3.org/2000/svg"
                 preserveAspectRatio="xMidYMid slice" focusable="false" role="img"
                 aria-label="Placeholder: First slide"><title>Placeholder</title>
                <rect width="100%" height="100%" fill="#33AAFF"></rect>
                <text x="27%" y="27%" fill="#555" dy=".3em" style="font-size:25px;">Second
                    slide
                </text>
            </svg>
        </div>
        <div class="carousel-item active">
            <svg class="bd-placeholder-img bd-placeholder-img-lg d-block w-100" width="800"
                 height="400" xmlns="http://www.w3.org/2000/svg"
                 preserveAspectRatio="xMidYMid slice" focusable="false" role="img"
                 aria-label="Placeholder: First slide"><title>Placeholder</title>
                <rect width="100%" height="100%" fill="#20AD1E"></rect>
                <text x="31%" y="27%" fill="#555" dy=".3em" style="font-size:25px;">Third
                    slide
                </text>
            </svg>
        </div>
    </div>
    <a class="carousel-control-prev" href="#carousel-example-controls" role="button"
       data-slide="prev">
        <span class="carousel-control-prev-icon" aria-hidden="true"></span>
        <span class="sr-only">Previous</span>
    </a>
    <a class="carousel-control-next" href="#carousel-example-controls" role="button"
       data-slide="next">
        <span class="carousel-control-next-icon" aria-hidden="true"></span>
        <span class="sr-only">Next</span>
    </a>
</div>
```

**With indicators**<br>
You can also add the indicators to the carousel, alongside the controls, too.

![Carousel with indicators example](../../images/bootstrap/carousel-with-indicators.png)

Here is an example with provided Bootstrap v4.3 code:

```java 
@UI("#carousel-example-indicators")
public static Carousel carouselWithIndicators;

@Test
public void selectTest() {
	carouselWithIndicators.select(1);
	carouselWithIndicators.is().text(firstSlideFullText);
	carouselWithIndicators.get(1).is().selected();
	carouselWithIndicators.get(2).is().deselected();
}

```

```html 
<div id="carousel-example-indicators" class="carousel slide mb-2" data-ride="carousel">
    <ol class="carousel-indicators">
        <li data-target="#carousel-example-indicators" data-slide-to="0"
            class="active"></li>
        <li data-target="#carousel-example-indicators" data-slide-to="1" class=""></li>
        <li data-target="#carousel-example-indicators" data-slide-to="2" class=""></li>
    </ol>
    <div class="carousel-inner">
        <div class="carousel-item active">
            <svg class="bd-placeholder-img bd-placeholder-img-lg d-block w-100" width="800"
                 height="400" xmlns="http://www.w3.org/2000/svg"
                 preserveAspectRatio="xMidYMid slice" focusable="false" role="img"
                 aria-label="Placeholder: First slide"><title>Placeholder</title>
                <rect width="100%" height="100%" fill="#777"></rect>
                <text x="34%" y="27%" fill="#555" dy=".3em" style="font-size:25px;">First
                    slide
                </text>
            </svg>
        </div>
        <div class="carousel-item">
            <svg class="bd-placeholder-img bd-placeholder-img-lg d-block w-100" width="800"
                 height="400" xmlns="http://www.w3.org/2000/svg"
                 preserveAspectRatio="xMidYMid slice" focusable="false" role="img"
                 aria-label="Placeholder: First slide"><title>Placeholder</title>
                <rect width="100%" height="100%" fill="#33AAFF"></rect>
                <text x="27%" y="27%" fill="#555" dy=".3em" style="font-size:25px;">Second
                    slide
                </text>
            </svg>
        </div>
        <div class="carousel-item">
            <svg class="bd-placeholder-img bd-placeholder-img-lg d-block w-100" width="800"
                 height="400" xmlns="http://www.w3.org/2000/svg"
                 preserveAspectRatio="xMidYMid slice" focusable="false" role="img"
                 aria-label="Placeholder: First slide"><title>Placeholder</title>
                <rect width="100%" height="100%" fill="#20AD1E"></rect>
                <text x="31%" y="27%" fill="#555" dy=".3em" style="font-size:25px;">Third
                    slide
                </text>
            </svg>
        </div>
    </div>
    <a class="carousel-control-prev" href="#carousel-example-indicators" role="button"
       data-slide="prev">
        <span class="carousel-control-prev-icon" aria-hidden="true"></span>
        <span class="sr-only">Previous</span>
    </a>
    <a class="carousel-control-next" href="#carousel-example-indicators" role="button"
       data-slide="next">
        <span class="carousel-control-next-icon" aria-hidden="true"></span>
        <span class="sr-only">Next</span>
    </a>
</div>
```

**With captions**<br>
Add captions to your slides easily with the .carousel-caption element within any .carousel-item.
They can be easily hidden on smaller viewports, as shown below, with optional display utilities.
We hide them initially with .d-none and bring them back on medium-sized devices with .d-md-block.

![Carousel with captions example](../../images/bootstrap/carousel-with-captions.png)

Here is an example with provided Bootstrap v4.3 code:

```java 

@UI("#carousel-example-captions")
public static Carousel carouselWithCaptions;

@Test
public void captionTest() {
	carouselWithCaptions.select(1);
	carouselWithCaptions.is().text(firstSlideWithLabelText);

	carouselWithCaptions.select(2);
	carouselWithCaptions.is().text(secondSlideWithLabelText);

	carouselWithCaptions.select(3);
	carouselWithCaptions.is().text(thirdSlideWithLabelText);
}

```

```html 
<div id="carousel-example-captions" class="carousel slide mb-2" data-ride="carousel">
    <ol class="carousel-indicators">
        <li data-target="#carousel-example-captions" data-slide-to="0" class=""></li>
        <li data-target="#carousel-example-captions" data-slide-to="1" class="active"></li>
        <li data-target="#carousel-example-captions" data-slide-to="2" class=""></li>
    </ol>
    <div class="carousel-inner">
        <div class="carousel-item">
            <svg class="bd-placeholder-img bd-placeholder-img-lg d-block w-100" width="800"
                 height="400" xmlns="http://www.w3.org/2000/svg"
                 preserveAspectRatio="xMidYMid slice" focusable="false" role="img"
                 aria-label="Placeholder: First slide"><title>Placeholder</title>
                <rect width="100%" height="100%" fill="#777"></rect>
                <text x="34%" y="12%" fill="#555" dy=".3em" style="font-size:25px;">First
                    slide
                </text>
            </svg>
            <div class="carousel-caption d-none d-md-block">
                <h5>First slide label</h5>
                <p>Nulla vitae elit libero, a pharetra augue mollis interdum.</p>
            </div>
        </div>
        <div class="carousel-item active">
            <svg class="bd-placeholder-img bd-placeholder-img-lg d-block w-100" width="800"
                 height="400" xmlns="http://www.w3.org/2000/svg"
                 preserveAspectRatio="xMidYMid slice" focusable="false" role="img"
                 aria-label="Placeholder: First slide"><title>Placeholder</title>
                <rect width="100%" height="100%" fill="#33AAFF"></rect>
                <text x="27%" y="12%" fill="#555" dy=".3em" style="font-size:25px;">Second
                    slide
                </text>
            </svg>
            <div class="carousel-caption d-none d-md-block">
                <h5>Second slide label</h5>
                <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit.</p>
            </div>
        </div>
        <div class="carousel-item">
            <svg class="bd-placeholder-img bd-placeholder-img-lg d-block w-100" width="800"
                 height="400" xmlns="http://www.w3.org/2000/svg"
                 preserveAspectRatio="xMidYMid slice" focusable="false" role="img"
                 aria-label="Placeholder: First slide"><title>Placeholder</title>
                <rect width="100%" height="100%" fill="#20AD1E"></rect>
                <text x="31%" y="12%" fill="#555" dy=".3em" style="font-size:25px;">Third
                    slide
                </text>
            </svg>
            <div class="carousel-caption d-none d-md-block">
                <h5>Third slide label</h5>
                <p>Praesent commodo cursus magna, vel scelerisque nisl consectetur.</p>
            </div>
        </div>
    </div>
    <a class="carousel-control-prev" href="#carousel-example-captions" role="button"
       data-slide="prev">
        <span class="carousel-control-prev-icon" aria-hidden="true"></span>
        <span class="sr-only">Previous</span>
    </a>
    <a class="carousel-control-next" href="#carousel-example-captions" role="button"
       data-slide="next">
        <span class="carousel-control-next-icon" aria-hidden="true"></span>
        <span class="sr-only">Next</span>
    </a>
</div>
```

**Crossfade**<br>
Add .carousel-fade to your carousel to animate slides with a fade transition instead of a slide.

Here is an example with provided Bootstrap v4.3 code:

```java 

@UI("#carousel-example-fade")
public static Carousel carouselWithFadeTransition;

@Test
public void fadePrevTest() {
	carouselWithFadeTransition.prev();
	carouselWithFadeTransition.is().text(thirdSlideFullText);

	carouselWithFadeTransition.prev();
	carouselWithFadeTransition.is().text(secondSlideFullText);

	carouselWithFadeTransition.prevControl().is().text(prevText);
}

```

```html 
<div id="carousel-example-fade" class="carousel slide mb-2 carousel-fade"
     data-ride="carousel">
    <div class="carousel-inner">
        <div class="carousel-item active">
            <svg class="bd-placeholder-img bd-placeholder-img-lg d-block w-100" width="800"
                 height="400" xmlns="http://www.w3.org/2000/svg"
                 preserveAspectRatio="xMidYMid slice" focusable="false" role="img"
                 aria-label="Placeholder: First slide"><title>Placeholder</title>
                <rect width="100%" height="100%" fill="#777"></rect>
                <text x="34%" y="27%" fill="#555" dy=".3em" style="font-size:25px;">First
                    slide
                </text>
            </svg>
        </div>
        <div class="carousel-item">
            <svg class="bd-placeholder-img bd-placeholder-img-lg d-block w-100" width="800"
                 height="400" xmlns="http://www.w3.org/2000/svg"
                 preserveAspectRatio="xMidYMid slice" focusable="false" role="img"
                 aria-label="Placeholder: First slide"><title>Placeholder</title>
                <rect width="100%" height="100%" fill="#33AAFF"></rect>
                <text x="27%" y="27%" fill="#555" dy=".3em" style="font-size:25px;">Second
                    slide
                </text>
            </svg>
        </div>
        <div class="carousel-item">
            <svg class="bd-placeholder-img bd-placeholder-img-lg d-block w-100" width="800"
                 height="400" xmlns="http://www.w3.org/2000/svg"
                 preserveAspectRatio="xMidYMid slice" focusable="false" role="img"
                 aria-label="Placeholder: First slide"><title>Placeholder</title>
                <rect width="100%" height="100%" fill="#20AD1E"></rect>
                <text x="31%" y="27%" fill="#555" dy=".3em" style="font-size:25px;">Third
                    slide
                </text>
            </svg>
        </div>
    </div>
    <a class="carousel-control-prev" href="#carousel-example-fade" role="button"
       data-slide="prev">
        <span class="carousel-control-prev-icon" aria-hidden="true"></span>
        <span class="sr-only">Previous</span>
    </a>
    <a class="carousel-control-next" href="#carousel-example-fade" role="button"
       data-slide="next">
        <span class="carousel-control-next-icon" aria-hidden="true"></span>
        <span class="sr-only">Next</span>
    </a>
</div>
```

**Individual .carousel-item interval**<br>
Add data-interval="" to a .carousel-item to change the amount of time to delay between automatically cycling to the next item.

Here is an example with provided Bootstrap v4.3 code:

```java 

@Test
public void intervalTest() {
	int customInterval = 1;
	WebPage.reload();
	durationMoreThan(interval, () -> carouselWithCustomInterval.is().text(secondSlideFullText));
	customInterval = carouselWithCustomInterval.interval() / 1000;
	durationMoreThan(customInterval, () -> carouselWithCustomInterval.is().text(thirdSlideFullText));
}

```

```html 
<div id="carousel-example-interval" class="carousel slide mb-3" data-ride="carousel">
    <div class="carousel-inner">
        <div class="carousel-item active" data-interval="3000">
            <svg class="bd-placeholder-img bd-placeholder-img-lg d-block w-100" width="800"
                 height="400" xmlns="http://www.w3.org/2000/svg"
                 preserveAspectRatio="xMidYMid slice" focusable="false" role="img"
                 aria-label="Placeholder: First slide"><title>Placeholder</title>
                <rect width="100%" height="100%" fill="#777"></rect>
                <text x="34%" y="27%" fill="#555" dy=".3em" style="font-size:25px;">First
                    slide
                </text>
            </svg>
        </div>
        <div class="carousel-item" data-interval="3000">
            <svg class="bd-placeholder-img bd-placeholder-img-lg d-block w-100" width="800"
                 height="400" xmlns="http://www.w3.org/2000/svg"
                 preserveAspectRatio="xMidYMid slice" focusable="false" role="img"
                 aria-label="Placeholder: First slide"><title>Placeholder</title>
                <rect width="100%" height="100%" fill="#33AAFF"></rect>
                <text x="27%" y="27%" fill="#555" dy=".3em" style="font-size:25px;">Second
                    slide
                </text>
            </svg>
        </div>
        <div class="carousel-item" data-interval="3000">
            <svg class="bd-placeholder-img bd-placeholder-img-lg d-block w-100" width="800"
                 height="400" xmlns="http://www.w3.org/2000/svg"
                 preserveAspectRatio="xMidYMid slice" focusable="false" role="img"
                 aria-label="Placeholder: First slide"><title>Placeholder</title>
                <rect width="100%" height="100%" fill="#20AD1E"></rect>
                <text x="31%" y="27%" fill="#555" dy=".3em" style="font-size:25px;">Third
                    slide
                </text>
            </svg>
        </div>
    </div>
    <a class="carousel-control-prev" href="#carousel-example-interval" role="button"
       data-slide="prev">
        <span class="carousel-control-prev-icon" aria-hidden="true"></span>
        <span class="sr-only">Previous</span>
    </a>
    <a class="carousel-control-next" href="#carousel-example-interval" role="button"
       data-slide="next">
        <span class="carousel-control-next-icon" aria-hidden="true"></span>
        <span class="sr-only">Next</span>
    </a>
</div>
```

Carousel is located in the following classes:

- __Java__: _com.epam.jdi.light.ui.bootstrap.elements.complex.Carousel_

Available methods in Java JDI Light:

|Method/Property | Description | Return Type
--- | --- | ---
assertThat() | Assert action | TextAssert
currentSlide() | Return current slide | UIElement
get(int i) | Return slide by index  | UIElement
getText() | Get carousel text  | String
indicators() | Return list of carousel indicators | WebList
interval() | Return current slide interval | int
isDisplayed() | Check that carousel is displayed | boolean
is() | Assert action | TextAssert
next() | Move to the next slide | void
nextControl() | Return 'next' control | UIElement
prev() | Move to the previous slide | void
prevControl() | Return 'previous' control | UIElement
select(int i) | Select slide by index  | void

<a href="https://github.com/jdi-testing/jdi-light/tree/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/complex/CarouselTests.java" target="_blank">Bootstrap test examples</a>

<br>
<br>
<br>

####Multiple progress bars

Include <a style="font-weight: bold;" target="_blank" href="https://getbootstrap.com/docs/4.3/components/progress/#multiple-bars">multiple progress bars</a>  in a progress component if you need.

There is a common element <a style="font-weight: bold;" target="_blank" href="https://jdi-docs.github.io/jdi-light/#progress">Progress</a> which includes only one progress bar.

![Progress multiple example](../../images/bootstrap/progress-multiple.png)

Here is an example with provided Bootstrap v4.3 code:

```java 
@UI("#progress-multiple-bars")  //FindBy(css = "#progress-multiple-bars")
public static MultipleProgressBars multipleProgressBars;

@Test(dataProvider = "multipleProgressBarsData")
public void separateBarTest(Progress progress, String color, String value, String minValue, String maxValue) {
    progress.is()
            .displayed()
            .enabled()
            .color(color)
            .value(value)
            .minValue(minValue)
            .maxValue(maxValue);
}

@Test
public void entireMultipleProgressBarsTest() {
    multipleProgressBars.getProgresses().is().size(3);
    multipleProgressBars.is()
            .displayed()
            .enabled();
    assertThat(multipleProgressBars.core().css("background-color"), is("rgba(233, 236, 239, 1)"));
    baseValidation(multipleProgressBars);
}

@Test
public void getValuesTest() {
    assertThat(multipleProgressBars.getValues(), is(multipleprogressValues));
    assertThat(multipleProgressBars.getValues().get(1), is("30"));
}
```

```html 
<div id="progress-multiple-bars" class="progress">
    <div id="progress-multiple-ordinary" class="progress-bar" role="progressbar" style="width: 15%" aria-valuenow="15" aria-valuemin="0" aria-valuemax="100"></div>
    <div id="progress-multiple-success" class="progress-bar bg-success" role="progressbar" style="width: 30%" aria-valuenow="30" aria-valuemin="0" aria-valuemax="100"></div>
    <div id="progress-multiple-info" class="progress-bar bg-info" role="progressbar" style="width: 20%" aria-valuenow="20" aria-valuemin="0" aria-valuemax="100"></div>
</div>
```

Available methods in Java JDI Light:

|Method | Description | Return Type
--- | --- | ---
**assertThat()** | Assert action | UIAssert
**getProgress(int Index)** |	Returns progressbar by index |	Progress
**getProgresses()** | Returns list of progressbars |	JList`<Progress>`
**getValues()** |	Returns list of values of each progressbar |	List`<String>`
**is()** | Various assert actions | UIAssert

[Bootstrap test examples](https://github.com/jdi-testing/jdi-light/tree/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/complex/MultipleProgressBarsTests.java)
<br><br><br>

#### Navs

***[Navs](https://getbootstrap.com/docs/4.3/components/navs/)*** - Different types of combination of navigation components.

##### Base
**[Base nav](https://getbootstrap.com/docs/4.3/components/navs/#base-nav)**

![Nav base example](../../images/bootstrap/nav-base.png)

Here is an example with provided Bootstrap v4.3 code:

```java 
// @FindBy(css = "#nav-base-li") public static NavsBaseLi navsBaseLi;
@UI("#nav-base-li") public static NavsBaseLi navsBaseLi;

public class NavsBaseLi extends Section {
    // @FindBy(css = "li") public ListGroup navItem;
    @UI("li") public ListGroup navItem;
    // @FindBy(css = "li a")  public ListGroup navItemLink;
    @UI("li a") public ListGroup navItemLink;
}

@Test(dataProvider = "clickValidate")
public void linkClickableLiTests(int index, String pageTitle) {
    navsBaseLi.navItem.get(index).highlight();
    navsBaseLi.navItem.get(index).click();
    newWindowTitleCheck(pageTitle);
    navsBaseLi.navItem.get(index).unhighlight();
}

@Test(dataProvider = "listData")
public void itemsIsValidationTests(int index, String linkText) {
    navsBaseLi.navItemLink.get(index).is()
            .core()
            .hasClass("nav-link")
            .text(is(linkText));
}

@Test
public void isValidationTests() {
    navsBaseLi.navItem.is()
            .size(4);
    navsBaseLi.navItemLink.get(1)
            .is()
            .core()
            .hasClass("active");
    navsBaseLi.navItemLink.get(4)
            .is()
            .core()
            .hasClass("disabled");
}
```

```html
<ul class="nav" id="nav-base-li">
    <li class="nav-item">
        <a class="nav-link active" href="https://jdi-testing.github.io/jdi-light/index.html"
           target="_blank">Active</a>
    </li>
    <li class="nav-item">
        <a class="nav-link" href="https://github.com/jdi-docs" target="_blank">JDI Docs</a>
    </li>
    <li class="nav-item">
        <a class="nav-link" href="https://github.com/jdi-testing" target="_blank">JDI -
            testing tool</a>
    </li>
    <li class="nav-item">
        <a class="nav-link disabled" href="https://getbootstrap.com" tabindex="-1"
           aria-disabled="true" target="_blank">Disabled</a>
    </li>
</ul>
```

```html
<nav class="nav" id="nav-base-a">
    <a class="nav-link active" href="https://jdi-testing.github.io/jdi-light/index.html"
       target="_blank">Active</a>
    <a class="nav-link" href="https://github.com/jdi-docs" target="_blank">JDI Docs</a>
    <a class="nav-link" href="https://github.com/jdi-testing" target="_blank">JDI - testing
        tool</a>
    <a class="nav-link disabled" href="https://getbootstrap.com" tabindex="-1"
       aria-disabled="true" target="_blank">Disabled</a>
</nav>
```

Available methods in Java JDI Light:

All methods are inherited from base element -  [UIElement](https://jdi-docs.github.io/jdi-light/#uielement)

Most applicable methods:

|Method | Description | Return Type
--- | --- | ---
**assertThat()** | Assert action | TextAssert
**click()** | Get button text | void
**get()** | Select button by index | UIElement
**getText()** | Get button text | String
**highlight()** | Get button text | void
**is()** | Assert action | TextAssert
**unhighlight()** | Get button text | void

<br>

[Java test examples](https://github.com/jdi-testing/jdi-light/blob/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/composite/section/navs/BaseTests.java)<br>

Nav group is represented by Section class in Java:

[Section](https://jdi-docs.github.io/jdi-light/#section)

<br>

##### Horizontal alignment
**[Nav horizontal alignmen](https://getbootstrap.com/docs/4.3/components/navs/#horizontal-alignment)**

![Nav horizontal alignmen example](../../images/bootstrap/nav-align-center.png)

![Nav horizontal alignmen example](../../images/bootstrap/nav-align-right.png)

Here is an example with provided Bootstrap v4.3 code:

```java 
// @FindBy(css = "#nav-center") public static NavsAlignmentCenter navsAlignmentCenter;
@UI("#nav-center") public static NavsAlignmentCenter navsAlignmentCenter;

public class NavsAlignmentCenter extends Section {
    // @FindBy(css = "li") public ListGroup navItem;
    @UI("li") public ListGroup navItem;
    // @FindBy(css = "li a")  public ListGroup navItemLink;
    @UI("li a") public ListGroup navItemLink;
}

@Test
public void isValidationTests() {
    navsAlignmentCenter.navItem.is()
            .size(4);
    navsAlignmentCenter.is()
            .displayed()
            .enabled()
            .core()
            .hasClass("nav justify-content-center");
    navsAlignmentCenter.navItemLink.get(1)
            .is()
            .core()
            .hasClass("active");
}

@Test(dataProvider = "listData")
public void itemsIsValidationTests(int index, String linkText) {
    navsAlignmentCenter.navItem.get(index)
            .is()
            .core()
            .hasClass("nav-item")
            .text(is(linkText));
}

@Test(dataProvider = "clickValidate")
public void linkClickableLiTests(int index, String pageTitle) {
    navsAlignmentCenter.navItem.get(index).highlight();
    navsAlignmentCenter.navItem.get(index).click();
    newWindowTitleCheck(pageTitle);
    navsAlignmentCenter.navItem.get(index).unhighlight();
}
```

```html
<ul class="nav justify-content-center" id="nav-center">
    <li class="nav-item">
        <a class="nav-link active" href="https://jdi-testing.github.io/jdi-light/index.html"
           target="_blank">Active</a>
    </li>
    <li class="nav-item">
        <a class="nav-link" href="https://github.com/jdi-docs" target="_blank">JDI Docs</a>
    </li>
    <li class="nav-item">
        <a class="nav-link" href="https://github.com/jdi-testing" target="_blank">JDI -
            testing tool</a>
    </li>
    <li class="nav-item">
        <a class="nav-link disabled" href="https://getbootstrap.com" tabindex="-1"
           aria-disabled="true" target="_blank">Disabled</a>
    </li>
</ul>
```

```html
<ul class="nav justify-content-end" id="nav-end">
    <li class="nav-item">
        <a class="nav-link active" href="https://jdi-testing.github.io/jdi-light/index.html"
           target="_blank">Active</a>
    </li>
    <li class="nav-item">
        <a class="nav-link" href="https://github.com/jdi-docs" target="_blank">JDI Docs</a>
    </li>
    <li class="nav-item">
        <a class="nav-link" href="https://github.com/jdi-testing" target="_blank">JDI -
            testing tool</a>
    </li>
    <li class="nav-item">
        <a class="nav-link disabled" href="https://getbootstrap.com" tabindex="-1"
           aria-disabled="true" target="_blank">Disabled</a>
    </li>
</ul>
```

Available methods in Java JDI Light:

All methods are inherited from base element -  [UIElement](https://jdi-docs.github.io/jdi-light/#uielement)

Most applicable methods:

|Method | Description | Return Type
--- | --- | ---
**assertThat()** | Assert action | TextAssert
**click()** | Get button text | void
**get()** | Select button by index | UIElement
**getText()** | Get button text | String
**highlight()** | Get button text | void
**is()** | Assert action | TextAssert
**unhighlight()** | Get button text | void

<br>

[Java test examples](https://github.com/jdi-testing/jdi-light/blob/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/composite/section/navs/AlignmentTests.java)<br>

Nav group is represented by Section class in Java:

[Section](https://jdi-docs.github.io/jdi-light/#section)

<br>

##### Vertical alignment
**[Nav vertical alignmen](https://getbootstrap.com/docs/4.3/components/navs/#vertical)**

![Nav vertical alignmen example](../../images/bootstrap/nav-vertical.png)

Here is an example with provided Bootstrap v4.3 code:

```java 
// @FindBy(css = "#nav-vert-li") public static NavsVerticalLi navsVerticalLi;
@UI("#nav-vert-li") public static NavsVerticalLi navsVerticalLi;

public class NavsVerticalLi extends Section {
    // @FindBy(css = "li") public ListGroup navItem;
    @UI("li") public ListGroup navItem;
    // @FindBy(css = "li a")  public ListGroup navItemLink;
    @UI("li a") public ListGroup navItemLink;
}

@Test
public void isValidationTests() {
    navsVerticalLi.navItem.is()
            .size(4);
    navsVerticalLi.is()
            .displayed()
            .enabled()
            .core()
            .hasClass("nav flex-column");
    navsVerticalLi.navItemLink.get(1)
            .is()
            .core()
            .hasClass("active");
    navsVerticalLi.navItemLink.get(4)
            .is()
            .core()
            .hasClass("disabled");
}

@Test(dataProvider = "clickValidate")
public void linkClickableLiTests(int index, String pageTitle) {
    navsVerticalLi.navItem.get(index).highlight();
    navsVerticalLi.navItem.get(index).click();
    newWindowTitleCheck(pageTitle);
    navsVerticalLi.navItem.get(index).unhighlight();
}
```

```html
<ul class="nav flex-column" id="nav-vert-li">
    <li class="nav-item">
        <a class="nav-link active" href="https://jdi-testing.github.io/jdi-light/index.html"
           target="_blank">Active</a>
    </li>
    <li class="nav-item">
        <a class="nav-link" href="https://github.com/jdi-docs" target="_blank">JDI Docs</a>
    </li>
    <li class="nav-item">
        <a class="nav-link" href="https://github.com/jdi-testing" target="_blank">JDI -
            testing tool</a>
    </li>
    <li class="nav-item">
        <a class="nav-link disabled" href="https://getbootstrap.com" tabindex="-1"
           aria-disabled="true" target="_blank">Disabled</a>
    </li>
</ul>
```

```html
<nav class="nav flex-column" id="nav-vert-a">
    <a class="nav-link active" href="https://jdi-testing.github.io/jdi-light/index.html"
       target="_blank">Active</a>
    <a class="nav-link" href="https://github.com/jdi-docs" target="_blank">JDI Docs</a>
    <a class="nav-link" href="https://github.com/jdi-testing" target="_blank">JDI - testing
        tool</a>
    <a class="nav-link disabled" href="https://getbootstrap.com" tabindex="-1"
       aria-disabled="true" target="_blank">Disabled</a>
</nav>
```


Available methods in Java JDI Light:

All methods are inherited from base element -  [UIElement](https://jdi-docs.github.io/jdi-light/#uielement)

Most applicable methods:

|Method | Description | Return Type
--- | --- | ---
**assertThat()** | Assert action | TextAssert
**click()** | Get button text | void
**get()** | Select button by index | UIElement
**getText()** | Get button text | String
**highlight()** | Get button text | void
**is()** | Assert action | TextAssert
**unhighlight()** | Get button text | void

<br>

[Java test examples](https://github.com/jdi-testing/jdi-light/blob/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/composite/section/navs/VerticalTests.java)<br>

Nav group is represented by Section class in Java:

[Section](https://jdi-docs.github.io/jdi-light/#section)

<br>

##### Tabs
**[Nav tabs](https://getbootstrap.com/docs/4.3/components/navs/#tabs)**

![Nav tabs example](../../images/bootstrap/nav-tabs.png)

Here is an example with provided Bootstrap v4.3 code:

```java 
// @FindBy(css = "#nav-tabs") public static NavsTabs navsTabs;
@UI("#nav-tabs") public static NavsTabs navsTabs;

public class NavsTabs extends Section {
    // @FindBy(css = "li") public ListGroup navItem;
    @UI("li") public ListGroup navItem;
    // @FindBy(css = "li a")  public ListGroup navItemLink;
    @UI("li a") public ListGroup navItemLink;
}

@Test
public void isValidationTests() {
    navsTabs.navItem.is()
            .size(4);
    navsTabs.is()
            .displayed()
            .enabled()
            .core()
            .hasClass("nav nav-tabs");
    navsTabs.navItemLink.get(1)
            .is()
            .core()
            .hasClass("active");
    navsTabs.navItemLink.get(4)
            .is()
            .core()
            .hasClass("disabled");
}

@Test(dataProvider = "clickValidate")
public void linkClickableLiTests(int index, String pageTitle) {
    navsTabs.navItem.get(index).highlight();
    navsTabs.navItem.get(index).click();
    newWindowTitleCheck(pageTitle);
    navsTabs.navItem.get(index).unhighlight();
}
```

```html
<ul class="nav nav-tabs" id="nav-tabs">
    <li class="nav-item">
        <a class="nav-link active" href="https://jdi-testing.github.io/jdi-light/index.html"
           target="_blank">Active</a>
    </li>
    <li class="nav-item">
        <a class="nav-link" href="https://github.com/jdi-docs" target="_blank">JDI Docs</a>
    </li>
    <li class="nav-item">
        <a class="nav-link" href="https://github.com/jdi-testing" target="_blank">JDI -
            testing tool</a>
    </li>
    <li class="nav-item">
        <a class="nav-link disabled" href="https://getbootstrap.com" tabindex="-1"
           aria-disabled="true" target="_blank">Disabled</a>
    </li>
</ul>
```


Available methods in Java JDI Light:

All methods are inherited from base element -  [UIElement](https://jdi-docs.github.io/jdi-light/#uielement)

Most applicable methods:

|Method | Description | Return Type
--- | --- | ---
**assertThat()** | Assert action | TextAssert
**click()** | Get button text | void
**get()** | Select button by index | UIElement
**getText()** | Get button text | String
**highlight()** | Get button text | void
**is()** | Assert action | TextAssert
**unhighlight()** | Get button text | void

<br>

[Java test examples](https://github.com/jdi-testing/jdi-light/blob/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/composite/section/navs/TabsTests.java)<br>

Nav group is represented by Section class in Java:

[Section](https://jdi-docs.github.io/jdi-light/#section)

<br>

##### Pills
**[Nav pills](https://getbootstrap.com/docs/4.3/components/navs/#pills)**

![Nav pills example](../../images/bootstrap/nav-pills.png)

Here is an example with provided Bootstrap v4.3 code:

```java 
// @FindBy(css = "#nav-pills") public static NavsPills navsPills;
@UI("#nav-pills") public static NavsPills navsPills;

public class NavsPills extends Section {
    // @FindBy(css = "li") public ListGroup navItem;
    @UI("li") public ListGroup navItem;
    // @FindBy(css = "li a")  public ListGroup navItemLink;
    @UI("li a") public ListGroup navItemLink;
}

@Test(dataProvider = "listData")
public void itemsIsValidationTests(int index, String linkText) {
    navsPills.navItem.get(index)
            .is()
            .core()
            .hasClass("nav-item")
            .text(is(linkText));
    navsPills.navItemLink.get(index)
            .is()
            .core()
            .hasClass("nav-link")
            .text(is(linkText));
}

@Test(dataProvider = "clickValidate")
public void linkClickableLiTests(int index, String pageTitle) {
    navsPills.navItem.get(index).highlight();
    navsPills.navItem.get(index).click();
    newWindowTitleCheck(pageTitle);
    navsPills.navItem.get(index).unhighlight();
}
```

```html
<ul class="nav nav-pills" id="nav-pills">
    <li class="nav-item">
        <a class="nav-link active" href="https://jdi-testing.github.io/jdi-light/index.html"
           target="_blank">Active</a>
    </li>
    <li class="nav-item">
        <a class="nav-link" href="https://github.com/jdi-docs" target="_blank">JDI Docs</a>
    </li>
    <li class="nav-item">
        <a class="nav-link" href="https://github.com/jdi-testing" target="_blank">JDI -
            testing tool</a>
    </li>
    <li class="nav-item">
        <a class="nav-link disabled" href="https://getbootstrap.com" tabindex="-1"
           aria-disabled="true" target="_blank">Disabled</a>
    </li>
</ul>
```


Available methods in Java JDI Light:

All methods are inherited from base element -  [UIElement](https://jdi-docs.github.io/jdi-light/#uielement)

Most applicable methods:

|Method | Description | Return Type
--- | --- | ---
**assertThat()** | Assert action | TextAssert
**click()** | Get button text | void
**get()** | Select button by index | UIElement
**getText()** | Get button text | String
**highlight()** | Get button text | void
**is()** | Assert action | TextAssert
**unhighlight()** | Get button text | void

<br>

[Java test examples](https://github.com/jdi-testing/jdi-light/blob/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/composite/section/navs/PillsTests.java)<br>

Nav group is represented by Section class in Java:

[Section](https://jdi-docs.github.io/jdi-light/#section)

<br>

##### Fill and justify
**[Nav fill and justify](https://getbootstrap.com/docs/4.3/components/navs/#fill-and-justify)**

![Nav fill and justify example](../../images/bootstrap/nav-fill-and-justify.png)

Here is an example with provided Bootstrap v4.3 code:

```java 
// @FindBy(css = "#nav-justify") public static NavsJustify navsJustify;
@UI("#nav-justify") public static NavsJustify navsJustify;

public class NavsJustify extends Section {
    // @FindBy(css = "li") public ListGroup navItem;
    @UI("li") public ListGroup navItem;
    // @FindBy(css = "li a")  public ListGroup navItemLink;
    @UI("li a") public ListGroup navItemLink;
}

@Test(dataProvider = "listData")
public void itemsIsValidationTests(int index, String linkText) {
    navsJustify.navItem.get(index)
            .is()
            .core()
            .hasClass("nav-item")
            .text(is(linkText));
    navsJustify.navItemLink.get(index)
            .is()
            .core()
            .hasClass("nav-link")
            .text(is(linkText));
}

@Test(dataProvider = "clickValidate")
public void linkClickableLiTests(int index, String pageTitle) {
    navsJustify.navItem.get(index).highlight();
    navsJustify.navItem.get(index).click();
    newWindowTitleCheck(pageTitle);
    navsJustify.navItem.get(index).unhighlight();
}
```

```html
<ul class="nav nav-pills nav-fill" id="nav-justify">
    <li class="nav-item">
        <a class="nav-link active" href="https://jdi-testing.github.io/jdi-light/index.html"
           target="_blank">Active</a>
    </li>
    <li class="nav-item">
        <a class="nav-link" href="https://github.com/jdi-docs" target="_blank">JDI Docs</a>
    </li>
    <li class="nav-item">
        <a class="nav-link" href="https://github.com/jdi-testing" target="_blank">JDI - testing
            tool</a>
    </li>
    <li class="nav-item">
        <a class="nav-link disabled" href="https://getbootstrap.com" tabindex="-1"
           aria-disabled="true" target="_blank">Disabled</a>
    </li>
</ul>
```


Available methods in Java JDI Light:

All methods are inherited from base element -  [UIElement](https://jdi-docs.github.io/jdi-light/#uielement)

Most applicable methods:

|Method | Description | Return Type
--- | --- | ---
**assertThat()** | Assert action | TextAssert
**click()** | Get button text | void
**get()** | Select button by index | UIElement
**getText()** | Get button text | String
**highlight()** | Get button text | void
**is()** | Assert action | TextAssert
**unhighlight()** | Get button text | void

<br>

[Java test examples](https://github.com/jdi-testing/jdi-light/blob/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/composite/section/navs/FillAndJustifyTests.java)<br>

Nav group is represented by Section class in Java:

[Section](https://jdi-docs.github.io/jdi-light/#section)

<br>

##### Tabs with dropdowns
**[Nav tabs with dropdowns](https://getbootstrap.com/docs/4.3/components/navs/#tabs-with-dropdowns)**

![Nav tabs with dropdowns example](../../images/bootstrap/nav-tabs-with-dropdowns.png)

Here is an example with provided Bootstrap v4.3 code:

```java 
// @FindBy(css = "#nav-with-dropdown") public static NavsTabsWithDropdown navsTabsWithDropdown;
@UI("#nav-with-dropdown") public static NavsTabsWithDropdown navsTabsWithDropdown;

public class NavsTabsWithDropdown extends Section {
    // @FindBy(css = "li") public ListGroup navItem;
    @UI("li") public ListGroup navItem;
    // @FindBy(css = "a.nav-link") public ListGroup navItemLink;
    @UI("a.nav-link") public ListGroup navItemLink;
    @JDropdown(expand = ".dropdown-toggle",
            value = ".dropdown-toggle",
            list = ".dropdown-item")
    public Dropdown dropdownMenu;
}

@Test
public void isValidationTests() {
    navsTabsWithDropdown.navItem.is()
            .size(4);
    navsTabsWithDropdown.is()
            .displayed()
            .enabled()
            .core()
            .hasClass("nav nav-tabs");
    navsTabsWithDropdown.navItemLink.get(1)
            .is()
            .core()
            .hasClass("active");
    navsTabsWithDropdown.navItemLink.get(4)
            .is()
            .core()
            .hasClass("disabled");
}

@Test
public void dropdownIsValidationTests() {
    navsTabsWithDropdown.dropdownMenu.expand();
    navsTabsWithDropdown.dropdownMenu
            .is()
            .displayed()
            .expanded()
            .enabled()
            .size(4);
    navsTabsWithDropdown.dropdownMenu
            .is()
            .core()
            .attr("data-toggle", "dropdown")
            .attr("aria-haspopup", "true")
            .attr("aria-expanded", "true")
            .attr("role", "button")
            .tag("a");
}
```

```html
<ul class="nav nav-tabs" id="nav-with-dropdown">
    <li class="nav-item">
        <a class="nav-link active" href="https://jdi-testing.github.io/jdi-light/index.html"
           target="_blank">Active</a>
    </li>
    <li class="nav-item dropdown">
        <a class="nav-link dropdown-toggle" data-toggle="dropdown" href="#" role="button"
           aria-haspopup="true" aria-expanded="false">Dropdown</a>
        <div class="dropdown-menu">
            <a class="dropdown-item"
               href="https://jdi-testing.github.io/jdi-light/index.html" target="_blank">JDI
                home</a>
            <a class="dropdown-item" href="https://github.com/jdi-docs" target="_blank">JDI
                Docs</a>
            <a class="dropdown-item" href="https://github.com/jdi-testing" target="_blank">JDI
                - testing tool</a>
            <div class="dropdown-divider"></div>
            <a class="dropdown-item" href="https://getbootstrap.com" target="_blank">Bootstrap</a>
        </div>
    </li>
    <li class="nav-item">
        <a class="nav-link" href="https://github.com/jdi-testing" target="_blank">JDI -
            testing tool</a>
    </li>
    <li class="nav-item">
        <a class="nav-link disabled" href="https://getbootstrap.com" tabindex="-1"
           aria-disabled="true" target="_blank">Disabled</a>
    </li>
</ul>
```


Available methods in Java JDI Light:

All methods are inherited from base element -  [UIElement](https://jdi-docs.github.io/jdi-light/#uielement)

Most applicable methods:

|Method | Description | Return Type
--- | --- | ---
**assertThat()** | Assert action | TextAssert
**click()** | Get button text | void
**expand()** | Get button text | void
**expanded()** | Get button text | TextAssert
**get()** | Select button by index | UIElement
**getText()** | Get button text | String
**highlight()** | Get button text | void
**is()** | Assert action | TextAssert
**unhighlight()** | Get button text | void

<br>

[Java test examples](https://github.com/jdi-testing/jdi-light/blob/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/composite/section/navs/TabsWithDropdownTests.java)<br>

Nav group is represented by Section class in Java:

[Section](https://jdi-docs.github.io/jdi-light/#section)

##### Pills with dropdowns
**[Nav pills with dropdowns](https://getbootstrap.com/docs/4.3/components/navs/#pills-with-dropdowns)**

![Nav pills with dropdowns example](../../images/bootstrap/nav-pills-with-dropdowns.png)

Here is an example with provided Bootstrap v4.3 code:

```java 
// @FindBy(css = "#nav-pills-drop") public static NavsPillsWithDropdown navsPillsWithDropdown;
@UI("#nav-pills-drop") public static NavsPillsWithDropdown navsPillsWithDropdown;

public class NavsPillsWithDropdown extends Section {
    // @FindBy(css = "li") public ListGroup navItem;
    @UI("li") public ListGroup navItem;
    // @FindBy(css = "a.nav-link") public ListGroup navItemLink;
    @UI("a.nav-link") public ListGroup navItemLink;
    @JDropdown(expand = ".dropdown-toggle",
            value = ".dropdown-toggle",
            list = ".dropdown-item")
    public Dropdown dropdownMenu;
}

@Test
public void dropdownIsValidationTests() {
    navsPillsWithDropdown.dropdownMenu.expand();
    navsPillsWithDropdown.dropdownMenu
            .is()
            .expanded()
            .size(4)
            .core()
            .attr("data-toggle", "dropdown")
            .attr("aria-haspopup", "true")
            .attr("aria-expanded", "true")
            .attr("role", "button")
            .tag("a");
    navsPillsWithDropdown.dropdownMenu.expand();
}

@Test
public void dropdownClickableTests() {
    navsPillsWithDropdown.dropdownMenu.select(linkDrop1);
    newWindowTitleCheck(pageTitle1);
    navsPillsWithDropdown.dropdownMenu.select(linkDrop2);
    newWindowTitleCheck(pageTitle2);
    navsPillsWithDropdown.dropdownMenu.select(linkDrop3);
    newWindowTitleCheck(pageTitle3);
    navsPillsWithDropdown.dropdownMenu.select(linkDrop4);
    newWindowTitleCheck(pageTitle4);
}
```

```html
<ul class="nav nav-pills" id="nav-pills-drop">
    <li class="nav-item">
        <a class="nav-link active" href="https://jdi-testing.github.io/jdi-light/index.html"
           target="_blank">Active</a>
    </li>
    <li class="nav-item dropdown">
        <a class="nav-link dropdown-toggle" data-toggle="dropdown" href="#" role="button"
           aria-haspopup="true" aria-expanded="false">Dropdown</a>
        <div class="dropdown-menu">
            <a class="dropdown-item"
               href="https://jdi-testing.github.io/jdi-light/index.html" target="_blank">JDI
                home</a>
            <a class="dropdown-item" href="https://github.com/jdi-docs" target="_blank">JDI
                Docs</a>
            <a class="dropdown-item" href="https://github.com/jdi-testing" target="_blank">JDI
                - testing tool</a>
            <div class="dropdown-divider"></div>
            <a class="dropdown-item" href="https://getbootstrap.com" target="_blank">Bootstrap</a>
        </div>
    </li>
    <li class="nav-item">
        <a class="nav-link" href="https://github.com/jdi-testing" target="_blank">JDI -
            testing tool</a>
    </li>
    <li class="nav-item">
        <a class="nav-link disabled" href="https://getbootstrap.com" tabindex="-1"
           aria-disabled="true" target="_blank">Disabled</a>
    </li>
</ul>
```

Available methods in Java JDI Light:

All methods are inherited from base element -  [UIElement](https://jdi-docs.github.io/jdi-light/#uielement)

Most applicable methods:

|Method | Description | Return Type
--- | --- | ---
**assertThat()** | Assert action | TextAssert
**click()** | Get button text | void
**expand()** | Get button text | void
**expanded()** | Get button text | TextAssert
**get()** | Select button by index | UIElement
**getText()** | Get button text | String
**highlight()** | Get button text | void
**is()** | Assert action | TextAssert
**unhighlight()** | Get button text | void

<br>

[Java test examples](https://github.com/jdi-testing/jdi-light/blob/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/composite/section/navs/PillsWithDropdownTests.java)<br>

Nav group is represented by Section class in Java:

[Section](https://jdi-docs.github.io/jdi-light/#section)

<br>


#### RadioButtons

**RadioButtons** – extends from <a href="https://jdi-docs.github.io/jdi-light/#radiobuttons">HTML 5 RadioButtons</a> class.

Bootstrap RadioButtons class is represented by the following class:

    - __Java__: _com.epam.jdi.light.ui.bootstrap.elements.complex.RadioButtons_

Is similar to the parent class but overrides its list() method and adds list(JFunc1<WebElement, Boolean> searchRule, ElementArea elementArea) method.

  <br>


### Bootstrap Composite elements
#### Forms
<a style="font-weight:bold" href="https://getbootstrap.com/docs/4.3/components/forms/" target="_blank">Forms</a> – logical part of a web page that represents an HTML form.
Form can consists of:
<ul>
<li>Textual form controls(inputs, selects, and textareas)</li>
<li>File inputs</li>
<li>Range inputs</li>
<li>Checkboxes and Radiobuttons</li>
<li>Help text</li>
<li>Fieldsets(which can disable all the controls within)</li>
</ul>

Available methods in Java JDI Light:

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
**is()** | Asserts element  | UIAssert
**login()** | Clicks "login" Button or "loginButton"| void
**login(T entity)** | Fills all settable elements and clicks “login” Button or ”loginButton” | void
**loginAs(T entity)** | Fills all settable elements and clicks “login” Button or ”loginButton” | void
**next(T entity)** | Fills all settable elements and clicks “next” Button or ”nextButton” | void
**onlyMandatory()** | Sets form filter option to **MANDATORY**, meaning that only mandatory form elements are filled/submitted or verified/checked for the duration of a single form action | void
**onlyOptional()** | Sets form filter option to **OPTIONAL**, meaning that only optional form elements are filled/submitted or verified/checked for the duration of a single form action | void
**pressButton(String buttonName)** | Clicks “buttonName” Button or "buttonNamebutton". Allows different buttons to send one form, e.g. save/publish/cancel/search/update/... | void
**publish(T entity)** | Fills all settable elements and clicks “publish” Button or ”publishButton” | void
**save(T entity)** | Fills all settable elements and clicks “save” Button or ”saveButton” | void
**search(T entity)** | Fills all settable elements and clicks “search” Button or ”searchButton” | void
**select(T entity)** | Fills all settable elements and clicks “select” Button or ”selectButton” | void
**send()** | Sends the form by clicking “send” Button or "sendButton" | void
**send(T entity)** | Fills all settable elements and clicks “send” Button or ”sendButton” | void
**submit()** | Sends the form by clicking "submit" Button or "submitButton" | void
**submit(String text)** | Fills first settable form field with value and clicks "submit" Button or "submitButton"  | void
**submit(T entity)** | Fills all settable elements and clicks "submit" Button or "submitButton"  | void
**submit(String text, String buttonName)** | Fills first settable field with value and clicks “buttonName” Button or "buttonNamebutton"| void
**submit(T entity, String buttonName)** | Fills all settable elements and clicks “buttonName” Button or "buttonNamebutton" | void
**update(T entity)** | Fills all settable elements and clicks “update” Button or ”updateButton” | void
**verify(T entity)** | Verifies that form has been filled correctly. If not, returns a list of keys where verification has failed | List<String>

##### Simple form
This is an example of simple form consisting of some basic elements.
![Simple form](../../images/bootstrap/form-simple.png)

Here is an example with provided Bootstrap v4.3 code:

```java 
     public class BootstrapFormsPage extends WebPage {
         // FindBy(css = "#support-form")
         @UI("#support-form")      
         public static SupportMessageForm supportMessageForm;
     }
    
    @Test
    public void submitButtonTest() {
        supportMessageForm.supportButtonSubmit.click();
        lastLogEntry.has().text(containsString(logLineSubmit));
    }

    @Test
    public void clearButtonTest() {
        supportMessageForm.supportButtonClear.click();
        lastLogEntry.has().text(containsString(logLineClear));
    }

    @Test
    public void submitFormTest() {
        setDefaultValues();
        supportMessageForm.submit(EXAMPLE_MESSAGE);
        lastLogEntry.has().text(containsString(logLineSubmit));
        supportMessageForm.check(EXAMPLE_MESSAGE);
    }

    @Test
    public void fillFormTest() {
        setDefaultValues();
        supportMessageForm.fill(EXAMPLE_MESSAGE);
        supportMessageForm.supportEmail.has().text(EXAMPLE_MESSAGE.supportEmail);
        supportMessageForm.supportMessage.has().text(EXAMPLE_MESSAGE.supportMessage);
        supportMessageForm.check(EXAMPLE_MESSAGE);
    }

    @Test
    public void clearFormTest() {
        setDefaultValues();
        supportMessageForm.clear(EXAMPLE_MESSAGE);
        lastLogEntry.has().text(containsString(logLineClear));
        supportMessageForm.check(TEMPLATE_MESSAGE);
    }
```

```html 
<form id="support-form">
    <div class="form-group">
        <label for="support-email">Please enter your email address at which
            our manager can contact you</label>
        <input type="email" class="form-control" id="support-email" aria-describedby="emailHelp" placeholder="Enter email">
        <small id="emailHelp" class="form-text text-muted">We'll never share your email with anyone
            else.</small>
    </div>
    <div class="form-group">
        <label for="support-message">Your message</label>
        <textarea class="form-control" id="support-message" rows="3"></textarea>
    </div>
    <button type="submit" class="btn btn-primary" id="support-button-submit">Submit</button>
    <button type="reset" class="btn btn-danger" id="support-button-clear">Clear</button>
</form>
```

[Bootstrap test examples](https://github.com/jdi-testing/jdi-light/tree/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/composite/section/form/SimpleFormTests.java)
<br><br><br><br><br><br><br><br><br><br><br>

##### Complicated form
This is an example of complicated form consisting of various specific elements.
![Complicated form](../../images/bootstrap/form-complicated.png)

Here is an example with provided Bootstrap v4.3 code:

```java 
    public class BootstrapFormsPage extends WebPage {
        // @FindBy(css = "#superhero-creation-form")
        @UI("#superhero-creation-form") 
        public static SuperheroForm superheroForm;
        // @FindBy(css = ".logs  li:first-child")        
        @UI(".logs  li:first-child") 
        public static Text lastLogEntry;
    }
    
    @Test
    public void submitButtonTest() {
        superheroForm.superheroButtonSubmit.click();
        lastLogEntry.has().text(containsString(logLineSubmit));
    }
    
    @Test
    public void clearButtonTest() {
        superheroForm.superheroButtonClear.click();
        lastLogEntry.has().text(containsString(logLineClear));
    }
    
    @Test
    public void submitFormTest() {
        superheroForm.submit(EXAMPLE_HERO);
        lastLogEntry.has().text(containsString(logLineSubmit));
        superheroForm.check(EXAMPLE_HERO);
    }
    
    @Test
    public void clearFormTest() {
        superheroForm.clear(EXAMPLE_HERO);
        lastLogEntry.has().text(containsString(logLineClear));
        superheroForm.check(TEMPLATE_HERO);
    }
``` 

```html 
<form id="superhero-creation-form">
    <div class="form-group">
        <label for="current-alias">Enter your alias</label>
        <input type="text" class="form-control" id="current-alias" aria-describedby="emailHelp" placeholder="Enter alias">
    </div>
    <div class="form-group">
        <label for="alter-ego">Enter your alter ego</label>
        <input type="text" class="form-control" id="alter-ego" aria-describedby="emailHelp" placeholder="Enter alter ego">
    </div>
    <!-- Radios start -->
    <fieldset class="form-group">
        <div class="row">
            <legend class="col-form-label col-sm-2 pt-0">Species</legend>
            <div class="col-sm-10">
                <div class="form-check">
                    <input class="form-check-input" type="radio" name="superheroSpecies" id="human" value="option1" checked="">
                    <label class="form-check-label" for="human">
                        Human
                    </label>
                </div>
                <div class="form-check">
                    <input class="form-check-input" type="radio" name="superheroSpecies" id="symbiote" value="option2">
                    <label class="form-check-label" for="symbiote">
                        Symbiote
                    </label>
                </div>
                <div class="form-check">
                    <input class="form-check-input" type="radio" name="superheroSpecies" id="skrulls" value="option3">
                    <label class="form-check-label" for="skrulls">
                        Skrulls
                    </label>
                </div>
                <div class="form-check">
                    <input class="form-check-input" type="radio" name="superheroSpecies" id="kryptonian" value="option4">
                    <label class="form-check-label" for="kryptonian">
                        Kryptonian
                    </label>
                </div>
            </div>
        </div>
    </fieldset>
    <!-- Radios end -->
    <div>
        <label for="superhero-range">Power scale:</label>
        <input type="range" class="custom-range mb-3" min="0" max="100" id="superhero-range">
    </div>
    <label for="select-universe">Universe:</label>
    <select class="custom-select mb-3" id="select-universe">
        <option selected="">Select character's universe</option>
        <option value="1">DC</option>
        <option value="2">Marvel Earth-616</option>
        <option value="3">Marvel Cinematic Universe</option>
    </select>
    <div class="custom-control custom-switch mb-3" id="superhero-switch-div">
        <input type="checkbox" class="custom-control-input" id="superhero-switch">
        <label class="custom-control-label" for="superhero-switch">I'm not going to destroy all living beings</label>
    </div>
    <button type="submit" class="btn btn-primary" id="superhero-button-submit">Submit</button>
    <button type="reset" class="btn btn-danger" id="superhero-button-clear">Clear</button>
</form>
```

[Bootstrap test examples](https://github.com/jdi-testing/jdi-light/tree/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/composite/section/form/ComplicatedFormTests.java)

#####Sizing
<a style="font-weight:bold" href="https://getbootstrap.com/docs/4.0/components/forms/#sizing" target="_blank">Set</a> heights using classes like .form-control-lg and .form-control-sm.

![Forms_sizing](../../images/bootstrap/forms-sizing.png)

Here is an example with provided Bootstrap v4.3 code:

```java 
@UI("#forms-sizing")  //@FindBy(css = "#forms-sizing")
public static FormsSizing formsSizing;

@UI("#form-sizing-lg")  //@FindBy(css = "#form-sizing-lg")
public TextField largeTextField;

@UI("#form-sizing-select-lg")  //@FindBy(css = "#form-sizing-select-lg")
public DropdownSelect largeSelect;

private String text = "TextField";
private String placeholderLarge = ".form-control-lg";
private String placeholderDefault = "Default input";
private String placeholderSmall = ".form-control-sm";

@Test
public void sendKeysTest() {
    formsSizing.largeTextField.sendKeys("Test");
    assertEquals(formsSizing.largeTextField.getText(), text+"Test");
}

@Test
public void selectOptionTest() {
    formsSizing.largeSelect.select("Large select");
    assertEquals(formsSizing.largeSelect.getValue(), "Large select");
}

@Test
public void isValidationTest() {
    formsSizing.largeTextField.is()
                    .enabled()
                    .text(is(text));
    formsSizing.largeSelect.is()
                    .displayed()
                    .selected("Large option");
    formsSizing.largeTextField.is()
                    .enabled()
                    .placeholder(placeholderLarge);
}

```

````html
<div class="html-left" id="forms-sizing">
    <div class="mb-3">
        <input class="form-control form-control-lg mb-3" id="form-sizing-lg" type="text"
               placeholder=".form-control-lg">
        <input class="form-control mb-3" id="form-sizing-default" type="text"
               placeholder="Default input">
        <input class="form-control form-control-sm mb-3" id="form-sizing-sm" type="text"
               placeholder=".form-control-sm">
    </div>

    <div class="mb-3">
        <select class="form-control form-control-lg mb-3" id="form-sizing-select-lg">
            <option>Large select</option>
            <option>Large option</option>
        </select>
        <select class="form-control mb-3" id="form-sizing-select-default">
            <option>Default select</option>
            <option>Default option</option>
        </select>
        <select class="form-control form-control-sm mb-3" id="form-sizing-select-sm">
            <option>Small select</option>
            <option>Small option</option>
        </select>
    </div>
</div>
````

Form group is represented by Section class in Java:

[Section](https://jdi-docs.github.io/jdi-light/#section)

Inner elements of Forms - Sizing are represented by the following classes:

+ [TextField](https://jdi-docs.github.io/jdi-light/#textfield)

+ DropdownSelect    TBD

|Method / Property | Description | Return Type
--- | --- | ---
**AssertThat** | Assert action | TextAssert
**GetText()** | returns text from the text field  | String
**GetValue()** | returns text from the text field| String
**Is** | Assert action | TextAssert
**select(string/int)** | Select data by value/index| void
**SendKeys(string value)** | adds text to the field | void
**SetText(String value)** | sets new text | void

[Bootstrap test examples](https://github.com/jdi-testing/jdi-light/blob/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/composite/section/form/FormReadOnlyTests.java)

<br><br>
**Readonly**

Add the <a style="font-weight: bold;" target="_blank" href="https://getbootstrap.com/docs/4.3/components/forms/#readonly">readonly</a> boolean attribute on an input to prevent modification of the input’s value. Read-only inputs appear lighter (just like disabled inputs), but retain the standard cursor.

![Forms_readonly_example](../../images/bootstrap/form-readonly.png)

Here is an example with provided Bootstrap v4.3 code:

```java 
//@FindBy(css = "#forms-readonly-input")
@UI("#forms-readonly-input")
public static TextField readonlyInput;


@Test
public void checkReadonlyAttribute() {
    assertTrue(readonlyInput.attrs().has("readonly"));
    readonlyInput.highlight();
    readonlyInput.is()
            .displayed()
            .enabled();
}

@Test(expectedExceptions = {InvalidElementStateException.class})
public void check() {
    readonlyInput.setValue(text);
    readonlyInput.sendKeys(text);
}


```

```html
<input class="form-control mb-3" id="forms-readonly-input" type="text"
                                   placeholder="Readonly input here..." readonly>
```

Available methods in Java JDI Light:

|Method / Property | Description | Return Type
--- | --- | ---
**AssertThat()** | property that returns object for work with assertions| TextAssert
**Focus()** | places cursor within the text field | void
**GetText()** | returns text from the text field  | String
**GetValue()** | returns text from the text field| String
**Is()** | property that returns object for work with assertions| TextAssert
**Input(string text)** | sets new text  | void
**Placeholder** | returns value of the placeholder attribute | String
**SendKeys(string value)** | adds text to the field | void
**SetText(String value)** | sets new text | void


<a href="https://github.com/jdi-testing/jdi-light/tree/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/composite.section.form.FormReadOnlyTests.java" target=a_blank> Bootstrap test examples </a>


<br><br>
#####Readonly plain text

If you want to have input readonly elements in your form styled as
<a style="font-weight: bold;" target="_blank" href="https://getbootstrap.com/docs/4.3/components/forms/#readonly-plain-text">plain text</a>,
use the <b>.form-control-plaintext</b> class to remove the default form field styling and preserve the correct margin and padding.
Compare items with plaintext mark (upper) and without it (lower):

![Forms_readonly_plain_text_example](../../images/bootstrap/readonly_plain_text.png)

Here is an example with provided Bootstrap v4.3 code:

```java 
//@FindBy(css = "#readonlyPlainText1")
@UI("#readonlyPlainText1")
public static ReadonlyPlainText readonlyPlainText1;

@Test
public void isValidationTest() {
    readonlyPlainText1.is().core().hasClass("form-control-plaintext");
    assertTrue(readonlyPlainText1.hasAttribute("readonly"));
    readonlyPlainText1.is().core().attr("type", "text");

@Test
public void textValidationTest() {
    readonlyPlainText1.is().text("email@example.com");
}

@Test
public void labelTest() {
    readonlyPlainText1.label().is().text("Email");
}
```

```html
<div class="form-group row">
    <label for="readonlyPlainText1" class="col-sm-2 col-form-label">Email</label>
    <div class="col-sm-10">
        <input type="text" readonly class="form-control-plaintext" id="readonlyPlainText1"
               value="email@example.com">
    </div>
</div>
```


Available methods in Java JDI Light:

|Method/Property | Description | Return Type
--- | --- | ---
**assertThat()** | Assert action | TextAssert
**attr()** | Match passed value with element attribute | ICoreElement
**getValue()** | Get item value | String
**hasClass()** | Match passed value with element class | ICoreElement
**is()** | Various assert actions for Progress | ProgressAssert
**label()** | Get label associated with an item | Label
**labelText()** | Get text of a label associated with an item | String

<a href="https://github.com/jdi-testing/jdi-light/tree/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/mposite.section.form.ReadonlyPlainTextTests.java" target=a_blank> Bootstrap test examples </a>

<br><br>

#####Range input

Set horizontally scrollable <a style="font-weight: bold;" target="_blank" href="https://getbootstrap.com/docs/4.3/components/forms/#range-inputs">range inputs</a>
using .form-control-range.

![Forms_range_input_example](../../images/bootstrap/range_input.png)

Here is an example with provided Bootstrap v4.3 code:

```java 
//@FindBy(css = "#formControlRange")
@UI("#formControlRange")
public static RangeInput rangeInput;

 @Test
 public void itemHasProperClass() {
    rangeInput.is().core().hasClass("form-control-range");
 }

 @Test
 public void itemHasProperType() {
    rangeInput.is().core().attr("type", "range");
 }

 @Test
 public void labelValidationTest() {
    rangeInput.label().is().text("Example Range input");
 }
```

```html
<form class="mb-3">
    <div class="form-group">
        <label for="formControlRange">Example Range input</label>
        <input type="range" class="form-control-range" id="formControlRange">
    </div>
</form>
```

Available methods in Java JDI Light:

|Method/Property | Description | Return Type
--- | --- | ---
**assertThat()** | Assert action | UIAssert
**attr()** | Match passed value with element attribute | String
**hasClass()** | Match passed value with element class | boolean
**is()** | Various assert actions for Progress | UIAssert
**label()** | Get label associated with an item | Label
**labelText()** | Get text of a label associated with an item | String

<a href="https://github.com/jdi-testing/jdi-light/tree/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/composite/section/form/RangeInputTests.java" target=a_blank> Bootstrap test examples </a>

#####Select menu

```java 
public class SelectMenu extends Form implements ISelector {
    //FindBy(css = "option")
    @UI("option") public WebList optionsSelectMenu;
    //FindBy(css = "option[selected]")
    @UI("option[selected]") public UIElement selectedOptionsSelectMenu;
    @Override
    public WebList list() { return optionsSelectMenu; }
}

//FindBy(id = "forms-select-menu")
@UI("#forms-select-menu")
public static SelectMenu formsSelectMenu;

@Test
public void getSelectedOptionFormsSelectMenuTest() {
  formsSelectMenu.selectedOptionsSelectMenu.is().text("Open this select menu");
}

//FindBy(id = "forms-select-menu-large")
@UI("#forms-select-menu-large")
public static SelectMenu formsSelectMenuLarge;
 
@Test(dataProvider = "optionFormSelectMenuTest")
public void getTextFormsSelectMenuTest(int i, String optionText, String value) {
  formsSelectMenuLarge.optionsSelectMenu.get(i).is().text(optionText);
  formsSelectMenuLarge.optionsSelectMenu.get(i).assertThat().attr("value", value);
}




//FindBy(id = "forms-select-menu-small")
@UI("#forms-select-menu-small")
public static SelectMenu formsSelectMenuSmall;








//FindBy(id = "forms-select-menu-multiple")
@UI("#forms-select-menu-multiple")
public static SelectMenu formsSelectMenuMultiple;
















//FindBy(id = "forms-select-menu-size")
@UI("#forms-select-menu-size")
public static SelectMenu formsSelectMenuSize;






@Test
public void selectOptionFormsSelectMenuTest() {
  formsSelectMenuSize.optionsSelectMenu.get(4).click();
  assertEquals(formsSelectMenuSize.getValue(), "Three");
}
















```

You can use custom <a href = "https://getbootstrap.com/docs/4.3/components/forms/#select-menu" target = "a_blank">select menus</a>.

Select menu is located in the following classes:

- __Java__: _com.epam.jdi.light.ui.bootstrap.elements.common.SelectMenu*_


![Select menu](../../images/bootstrap/form-select-menu.png) <br>
Here is an example with provided Bootstrap v4.3 code:

```html
<select class="custom-select mb-3" id="forms-select-menu">
    <option selected>Open this select menu</option>
    <option value="1">One</option>
    <option value="2">Two</option>
    <option value="3">Three</option>
</select>
``` 
<br>

**Large select menu**
![Select menu](../../images/bootstrap/form-select-menu-large.png) <br>
Here is an example with provided Bootstrap v4.3 code:

```html
<select class="custom-select custom-select-lg mb-3" id="forms-select-menu-large">
    <option selected>Open this select menu</option>
    <option value="1">One</option>
    <option value="2">Two</option>
    <option value="3">Three</option>
</select>
```
 <br>

**Small select menu**
![Select menu](../../images/bootstrap/form-select-menu-small.png) <br>
Here is an example with provided Bootstrap v4.3 code:

```html
<select class="custom-select custom-select-sm mb-3" id="forms-select-menu-small">
    <option selected>Open this select menu</option>
    <option value="1">One</option>
    <option value="2">Two</option>
    <option value="3">Three</option>
</select>
```
<br>

**Select menu multiple**
![Select menu](../../images/bootstrap/form-select-menu-multiple.png) <br>
Here is an example with provided Bootstrap v4.3 code:

```html
<select class="custom-select mb-3" multiple id="forms-select-menu-multiple">
    <option selected>Open this select menu</option>
    <option value="1">One</option>
    <option value="2">Two</option>
    <option value="3">Three</option>
</select>
```
<br>

**Select menu size**
![Select menu](../../images/bootstrap/form-select-menu-size.png) <br>
Here is an example with provided Bootstrap v4.3 code:

```html
<select class="custom-select mb-3" size="3" id="forms-select-menu-size">
    <option selected>Open this select menu</option>
    <option value="1">One</option>
    <option value="2">Two</option>
    <option value="3">Three</option>
</select>
```
<br>

Available methods in Java JDI Light:
<br>

|Method | Description | Return Type
--- | --- | ---
**assertThat()** | Assert action | TextAssert
**click()** | Click the button | void
**is()** | Assert action | TextAssert
<br>

<a href="https://github.com/jdi-testing/jdi-light/blob/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/composite/section/form/FormsSelectMenuTests.java" target=a_blank> Bootstrap test examples </a>

#####Range

Create custom <a style="font-weight: bold;" target="_blank" href="https://getbootstrap.com/docs/4.3/components/forms/#range">range</a>
controls (`<input type="range">`) with .custom-range. The track (the background) and thumb (the value) are both styled to appear the same across browsers.
Range inputs have implicit values for min and max: 0 and 100, respectively. You may specify new values for those using the min and max attributes.

![Range_example](../../images/bootstrap/range.png)

Here is an example with provided Bootstrap v4.3 code:

```java 
//@FindBy(css = "#customRange3")
@UI("#customRange3")
public static Range range;

@Test
public void labelTest() {\
    range.label().is().text(labelText);
 }

@Test
public void validateThumbMinMaxAndStepValuesTest() {
    range.is().thumbValue(2.5);
    range.is().minValue(0);
    range.is().maxValue(5);
    range.is().step(0.5);
}
 
@Test
public void setThumbValueTest() {
    range3.setThumbValue(5);
    range3.is().thumbValue(5);
}
```

```html
<div class="html-left">
    <label for="customRange1">Example range</label>
    <input type="range" class="custom-range" id="customRange1">

    <label for="customRange2">Example range</label>
    <input type="range" class="custom-range" min="0" max="5" id="customRange2">

    <label for="customRange3">Example range</label>
    <input type="range" class="custom-range" min="0" max="5" step="0.5" id="customRange3">
</div>
```

Available methods in Java JDI Light:

|Method/Property | Description | Return Type
--- | --- | ---
**assertThat()** | Assert action | UIAssert
**getValue()** | Get thumb value as String | String
**is()** | Various assert actions for Progress | RangeAssert
**label()** | Get label associated with an item | Label
**labelText()** | Get text of a label associated with an item | String
**max()** | Get maximal limit of range | double
**min()** | Get minimal limit of range | double
**step()** | Get incremental step of range | double
**setThumbValue()** | Set thumb value with a "double" parameter | void
**setValue()** | Set thumb value with a String parameter | void
**thumbValue()** | Get thumb value | double


<a href="https://github.com/jdi-testing/jdi-light/tree/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/common/RangeTests.java" target=a_blank> Bootstrap test examples </a>

<br><br>

##### Form Validation

###### Custom style
You can use custom <a href = "https://getbootstrap.com/docs/4.3/components/forms/#custom-styles" target = "a_blank">Bootstrap form validation</a> messages.

![Custom style validation](../../images/bootstrap/form-bootstrap-validation.png)

Here is an example with provided Bootstrap v4.3 code:

```java 
@UI("#validated-form")
public FormValidationForm form;

@Test
public void bootstrapValidationTest() {
    String name = "ValidName";
    String email = "InvalidEmail";
    String phone = "InvalidPhone";

    SimpleContact entity = new SimpleContact(name, email, phone);

    form.fill(entity);
    form.submit();

    Map<String, String> validFeedback = form.getValidFeedback();
    MatcherAssert.assertThat("Number of valid feedbacks not equals 1", validFeedback.size() == 1);
    MatcherAssert.assertThat(validFeedback.keySet(), Matchers.hasItems("Name"));
    MatcherAssert.assertThat(validFeedback.values(), Matchers.hasItem("Hi, " + name + "!"));

    Map<String, String> invalidFeedback = form.getInvalidFeedback();
    MatcherAssert.assertThat("Number of invalid feedbacks not equals 2", invalidFeedback.size() == 2);
    MatcherAssert.assertThat(invalidFeedback.keySet(), 
        Matchers.hasItems("Email", "Phone"));
    MatcherAssert.assertThat(invalidFeedback.values(), 
        Matchers.hasItems("Enter valid email!", "It doesn't look like a valid phone number"));
}
```

 ```html 
<form id="validated-form" class="" novalidate="">
    <div class="row">
        <div class="col">
            <div class="form-group">
                <input id="validated-form-name-field" type="text" class="form-control" placeholder="Enter name" required="">
                <div id="name-valid-feedback" class="valid-feedback">Hi, Valid Name!</div>
                <div class="invalid-feedback">Enter your name!</div>
            </div>
        </div>
        <div class="col">
            <div class="form-group">
                <input type="email" class="form-control" id="validated-form-email" placeholder="Enter email" required="">
                <div class="valid-feedback">Looks good!</div>
                <div class="invalid-feedback">Enter valid email!</div>
            </div>
        </div>
        <div class="col">
            <div class="form-group">
                <input type="text" class="form-control" id="validated-form-phone" placeholder="Enter phone" pattern="^[-+0-9()\s]+$">
                <div class="valid-feedback">Looks good!</div>
                <div class="invalid-feedback">It doesn't look like a valid phone number</div>
            </div>
        </div>
    </div>
    <div class="row">
        <div class="col">
        <button type="submit" class="btn btn-primary" id="validated-form-submit">Send</button>
        <button type="reset" class="btn btn-danger" id="validated-form-reset">Clear</button>
        </div>
    </div>
</form>
```

Additional JavaScript code to use Bootstrap validation:

![Browser default validation](../../images/bootstrap/form-bootstrap-validation-js.png)

###### Browser default

Also you can use <a href = "https://getbootstrap.com/docs/4.3/components/forms/#browser-defaults" target = "a_blank">browser default validation</a>.

![Browser default validation](../../images/bootstrap/form-browser-defaults.png)

Here is an example with provided Bootstrap v4.3 code:

```java 
@UI("#validated-form")
public FormValidationForm form;

@Test
public void browserValidationTest() {
    String name = "ValidName";
    String email = "InvalidEmail";
    String phone = "InvalidPhone";

    SimpleContact entity = new SimpleContact(name, email, phone);

    form.fill(entity);
    form.submit();

    Map<String, String> validFeedback = form.getValidationMessages();

    MatcherAssert.assertThat("", validFeedback.get("Email"),
        Matchers.is("Please include an '@' in the email address. 'InvalidEmail' is missing an '@'.")); //Browser dependent message
    MatcherAssert.assertThat("", validFeedback.get("Phone"),
        Matchers.is("Please match the requested format.")); //Browser dependent message
    MatcherAssert.assertThat("", validFeedback.get("Name"), Matchers.is(""));
}
```

 ```html 
<form id="validated-form"">
    <div class="row">
        <div class="col">
            <div class="form-group">
                <input id="validated-form-name-field" type="text" class="form-control" placeholder="Enter name" required="">
            </div>
        </div>
        <div class="col">
            <div class="form-group">
                <input type="email" class="form-control" id="validated-form-email" placeholder="Enter email" required="">
            </div>
        </div>
        <div class="col">
            <div class="form-group">
                <input type="text" class="form-control" id="validated-form-phone" placeholder="Enter phone" pattern="^[-+0-9()\s]+$">
            </div>
        </div>
    </div>
    <div class="row">
        <div class="col">
        <button type="submit" class="btn btn-primary" id="validated-form-submit">Send</button>
        <button type="reset" class="btn btn-danger" id="validated-form-reset">Clear</button>
        </div>
    </div>
</form>
```

Available methods for form validation in Java JDI Light:

|Method/Property | Description | Return Type
--- | --- | ---
**isValid()** | Return if form valid | boolean
**getValidationMessages()** | Return map field names to browser validation messages | Map<String, String>
**getValidFeedback()** |  Return map field names to visible valid bootstrap feedback text | Map<String, String>
**getInvalidFeedback()** |  Return map field names to visible invalid bootstrap feedback text | Map<String, String>
**getFeedbackElements()** |  Return map field names to visible bootstrap feedback elements | Map<String, UIElement>

<a href="https://github.com/jdi-testing/jdi-light/tree/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/composite/section/form/BootstrapValidationTest.java" target="_blank">Bootstrap Test Examples</a>



#### Scrollspy
**[Scrollspy](https://getbootstrap.com/docs/4.3/components/scrollspy/#example-in-navbar)** – automatically update Bootstrap navigation or list group components based on scroll position to indicate which link is currently active in the viewport.
<br><br>
- [Scrollspy in navbar] (https://getbootstrap.com/docs/4.3/components/scrollspy/#example-in-navbar)
  <br>



![Scrollspy](../../images/bootstrap/scroll_spy1.png)<br>

```java 
    // @FindBy(css = "#navbar-example2")
    @UI("#navbar-example2") public static NavbarWithDropdown navbarWithDropdown;
    // @FindBy(css = "#navbar-example2~div")
    @UI("#navbar-example2~div") public static ScrollSpyNav scrollSpyInNavbar;
    
    public class NavbarWithDropdown extends Section {
        // @FindBy(css = "ul>li")
        @UI("ul>li") 
        public ListGroup navGroup;
        // @FindBy(css ="ul>li>a")
        @UI("ul>li>a") 
        public ListGroup navItemLink;
        @JDropdown(expand = ".dropdown-toggle",
                value = ".dropdown-toggle",
                list = ".dropdown-item")
        public Dropdown dropdownMenu;
        // @FindBy(css = ".navbar-brand")
        @UI(".navbar-brand") 
        public Link navbarLink;
    }
  
    public class ScrollSpyNav extends Section {
        // @FindBy(xpath = ".//h4 | .//h5")
        @UI(".//h4 | .//h5") public ListGroup header;
        // @FindBy(css = "p")
        @UI("p") public ListGroup mainText;          
    
        public void scrollParagraph(ListGroup listGroup, int index, String className){
            mainText.get(index).show();
    
            if (!listGroup.get(index).core().hasClass(className) &&
                    index < header.size()) {
                header.get(index + 1).show();
            }
        }
    }

    private String itemLink = "https://jdi-testing.github.io/jdi-light/bootstrap.html#";
    
    @DataProvider
    public Object[][] dropdownCheck() {
        return new Object[][]{
                {3, itemLink + "one", "one"},
                {4, itemLink + "two", "two"},
                {5, itemLink + "three", "three"}
        };
    }

    @Test(dataProvider = "dropdownCheck", priority = 1)
    public void dropdownCheckTests(int _index, String link, String header) {
        navbarWithDropdown.dropdownMenu.expand();
        navbarWithDropdown.dropdownMenu.list().get(header).is()
                .core()
                .displayed()
                .enabled()
                .text(is(header))
                .value(is(header))
                .attr(ATTR_NAME_HREF, is(link));
    }

    @Test
    public void navbarLinkClickableTests() {
        navbarWithDropdown.navbarLink.click();
        newWindowTitleCheck(pageTitle);
    }

    @Test
    public void isValidationTests() {
        navbarWithDropdown.navItemLink.get(3).is().text(dropdown);
        navbarWithDropdown.navItemLink.get(3).is().value(dropdown);
        navbarWithDropdown.navItemLink.is().size(3);
        navbarWithDropdown.navGroup.is().size(3);

        navbarWithDropdown.dropdownMenu.expand();
        navbarWithDropdown.dropdownMenu.is().size(3);

        navbarWithDropdown.find(By.className("dropdown-divider")).is()
                .core()
                .displayed()
                .enabled()
                .attr("role", "separator");
    }
      
```

```html
<nav id="navbar-example2" class="navbar navbar-light bg-light">
    <a class="navbar-brand"
       href="https://getbootstrap.com/docs/4.3/components/scrollspy/#example-in-navbar"
       target="_blank">Navbar</a>
    <ul class="nav nav-pills">
        <li class="nav-item"><a class="nav-link" href="#fat">@fat</a>
        </li>
        <li class="nav-item"><a class="nav-link" href="#mdo">@mdo</a>
        </li>
        <li class="nav-item dropdown"><a
                class="nav-link dropdown-toggle" data-toggle="dropdown"
                href="#" role="button" aria-haspopup="true"
                aria-expanded="false">Dropdown</a>
            <div class="dropdown-menu">
                <a class="dropdown-item" href="#one">one</a> <a
                    class="dropdown-item" href="#two">two</a>
                <div role="separator" class="dropdown-divider"></div>
                <a class="dropdown-item" href="#three">three</a>
            </div>
        </li>
    </ul>
</nav>
<div data-spy="scroll" data-target="#navbar-example2"
     data-offset="0" class="scrollspy-example">
    <h4 id="fat">@fat</h4>
    <p>...</p>
    <h4 id="mdo">@mdo</h4>
    <p>...</p>
    <h4 id="one">one</h4>
    <p>...</p>
    <h4 id="two">two</h4>
    <p>...</p>
    <h4 id="three">three</h4>
    <p>...</p>
</div>
```
<br>
<br>






- [Scrollspy with nested nav] (https://getbootstrap.com/docs/4.3/components/scrollspy/#example-with-nested-nav)
  <br>

![Scrollspy](../../images/bootstrap/scroll_spy2.png)<br>

```java 
// @FindBy(css = "#navbar-example3")
@UI("#navbar-example3") public static NestedNav nestedNav;
// @FindBy(css = "#navbar-example3~div")
@UI("#navbar-example3~div") public static ScrollSpyNav scrollSpyWithNestedNav;
  
public class NestedNav extends Section {
    // @FindBy(css = "nav")
    @UI("nav") public ListGroup navGroup;          
    // @FindBy(css = "nav nav a")
    @UI("nav nav a") public ListGroup navItemLink; 
    // @FindBy(css = ".navbar-brand")
    @UI(".navbar-brand") public Link navbarLink;   
}

public class ScrollSpyNav extends Section {
    // @FindBy(xpath = ".//h4 | .//h5")
    @UI(".//h4 | .//h5") public ListGroup header;
    // @FindBy(css = "p")
    @UI("p") public ListGroup mainText;          

    public void scrollParagraph(ListGroup listGroup, int index, String className){
        mainText.get(index).show();

        if (!listGroup.get(index).core().hasClass(className) &&
                index < header.size()) {
            header.get(index + 1).show();
        }
    }
}

@DataProvider
public Object[][] itemsCheck() {
    return new Object[][]{
            {1}, {2}, {3}, {4}, {5}, {6}, {7}
    };
}

@Test(dataProvider = "itemsCheck")
public void paragraphClickableTests(int index) {
    scrollSpyWithNestedNav.mainText.get(index).highlight();

    scrollSpyWithNestedNav.scrollParagraph(nestedNav.navItemLink, index, CLASS_NAME_ACTIVE);

    assertTrue(nestedNav.navItemLink.get(index).hasClass(CLASS_NAME_ACTIVE));
    nestedNav.navItemLink.get(index).unhighlight();
}


@Test
public void isValidationTests() {
    nestedNav.navItemLink.is().size(7);
    nestedNav.navGroup.is().size(3);
    scrollSpyWithNestedNav.mainText.is().size(7);
    scrollSpyWithNestedNav.header.is().size(7);
}
```

```html
<nav id="navbar-example3" class="navbar navbar-light bg-light">
    <a class="navbar-brand"
       href="https://getbootstrap.com/docs/4.3/components/scrollspy/#example-with-nested-nav"
       target="_blank">Navbar</a>
    <nav class="nav nav-pills flex-column">
        <a class="nav-link" href="#item-1">Item 1</a>
        <nav class="nav nav-pills flex-column">
            <a class="nav-link ml-3 my-1" href="#item-1-1">Item 1-1</a> <a
                class="nav-link ml-3 my-1" href="#item-1-2">Item 1-2</a>
        </nav>
        <a class="nav-link" href="#item-2">Item 2</a> <a
            class="nav-link" href="#item-3">Item 3</a>
        <nav class="nav nav-pills flex-column">
            <a class="nav-link ml-3 my-1" href="#item-3-1">Item 3-1</a> <a
                class="nav-link ml-3 my-1" href="#item-3-2">Item 3-2</a>
        </nav>
    </nav>
</nav>

<div data-spy="scroll" data-target="#navbar-example3"
     data-offset="0" class="scrollspy-example-2">
    <h4 id="item-1">Item 1</h4>
    <p>...</p>
    <h5 id="item-1-1">Item 1-1</h5>
    <p>...</p>
    <h5 id="item-1-2">Item 1-2</h5>
    <p>...</p>
    <h4 id="item-2">Item 2</h4>
    <p>...</p>
    <h4 id="item-3">Item 3</h4>
    <p>...</p>
    <h5 id="item-3-1">Item 3-1</h5>
    <p>...</p>
    <h5 id="item-3-2">Item 3-2</h5>
    <p>...</p>
</div>
```
<br>
<br>

- [Scrollspy with list-group] (https://getbootstrap.com/docs/4.3/components/scrollspy/#example-with-list-group)
  <br>

![Scrollspy](../../images/bootstrap/scroll_spy3.png)<br>

```java 
// @FindBy(css = "#list-example>a")
@UI("#list-example>a") public static ListGroup listGroupForScrollSpy;
// @FindBy(css = "#list-example~div")
@UI("#list-example~div") public static ScrollSpyNav scrollSpyWithListGroup;

public class ScrollSpyNav extends Section {
    // @FindBy(xpath = ".//h4 | .//h5")
    @UI(".//h4 | .//h5") public ListGroup header;
    // @FindBy(css = "p")
    @UI("p") public ListGroup mainText;          

    public void scrollParagraph(ListGroup listGroup, int index, String className){
        mainText.get(index).show();

        if (!listGroup.get(index).core().hasClass(className) &&
                index < header.size()) {
            header.get(index + 1).show();
        }
    }
}

@DataProvider
public Object[][] itemsCheck() {
    return new Object[][]{
            {1}, {2}, {3}, {4}
    };
}   

@Test(dataProvider = "itemsCheck")
public void paragraphClickableTests(int index) {
    scrollSpyWithListGroup.mainText.get(index).highlight();

    scrollSpyWithListGroup.scrollParagraph(listGroupForScrollSpy, index, CLASS_NAME_ACTIVE);

    listGroupForScrollSpy.get(index)
            .is()
            .core()
            .displayed()
            .enabled()
            .cssClass(CLASS_NAME_LIST_GROUP_ITEM_LIST_GROUP_ITEM_ACTION_ACTIVE)
            .css(CSS_NAME_BACKGROUND_COLOR, "rgba(0, 123, 255, 1)")//#007bff Color Hex
            .css(CSS_NAME_BORDER_COLOR, "rgb(0, 123, 255)");//#007bff Color Hex

    listGroupForScrollSpy.get(index).unhighlight();
}

@Test
public void isValidationTests() {
    scrollSpyWithListGroup.header.is().size(4);
    scrollSpyWithListGroup.mainText.is().size(4);
    listGroupForScrollSpy.is().size(4);
}
```

```html
<div id="list-example" class="list-group">
    <a class="list-group-item list-group-item-action"
       href="#list-item-1">Item 1</a> <a
        class="list-group-item list-group-item-action"
        href="#list-item-2">Item 2</a> <a
        class="list-group-item list-group-item-action"
        href="#list-item-3">Item 3</a> <a
        class="list-group-item list-group-item-action"
        href="#list-item-4">Item 4</a>
</div>
<div data-spy="scroll" data-target="#list-example"
     data-offset="0" class="scrollspy-example">
    <h4 id="list-item-1">Item 1</h4>
    <p>...</p>
    <h4 id="list-item-2">Item 2</h4>
    <p>...</p>
    <h4 id="list-item-3">Item 3</h4>
    <p>...</p>
    <h4 id="list-item-4">Item 4</h4>
    <p>...</p>
</div>
```

Available methods in Java JDI Light:

|Method | Description | Return Type
--- | --- | ---
**assertThat()**	|  Assert action	| TextAssert
**click()**	| Click element | void
**expand()**| Expand dropdown|void
**get(int)**	| Select element by index	 | UIElement
**get(String)**	| Select element by text	 | UIElement
**getText()**|Get text	  | String
**getValue()**| Get value | String
**is()**		|  Assert action	| TextAssert
**list()**| Get list of dropdown | WebList
**show ()**| Scroll to element| void
**size()**| Get WebList size| int

In these java test cases examples next classes have been used:

- Java: com.epam.jdi.light.elements.composite.Section

- Java: com.epam.jdi.light.elements.complex.ListGroup

- Java: com.epam.jdi.light.ui.bootstrap.elements.common.Link

- Java: com.epam.jdi.light.elements.complex.dropdown.Dropdown

[Scrollspy in navbar Tests Example](https://github.com/jdi-testing/jdi-light/blob/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/composite/section/scrollspy/ScrollspyInNavbarTests.java)

[Scrollspy with nested nav Tests Example](https://github.com/jdi-testing/jdi-light/blob/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/composite/section/scrollspy/ScrollspyWithNestedNavTests.java)

[Scrollspy with list-group Tests Example](https://github.com/jdi-testing/jdi-light/blob/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/composite/section/scrollspy/ScrollspyWithListGroupTests.java)

<br><br>

#### Media object

```java 
public class MediaObject extends Section {
}
```

<a href="https://getbootstrap.com/docs/4.3/components/media-object" target=a_blank> Media object</a> helps build complex and repetitive components where some media is positioned alongside content that doesn’t wrap around said media.

**Media object sample**

![Media object sample](../../images/bootstrap/media-object-sample.png)

Here is an example with provided Bootstrap v4.3 code:

  ```java 
  // @FindBy(css = "#media-object-sample")
  @UI("#media-object-sample") public static MediaObjectSample mediaObjectSample; 
  
  public class MediaObjectSample extends MediaObject {
  @UI("img") public Image imageOfMediaObject;
  
  @Title
  @UI("h5") public Text headingOfMediaObject;
  
  @UI(".media-body") public Text bodyOfMediaObject;
  }
  
  @Test
  public void isValidationTestSample() {
      mediaObjectSample.is().displayed();
      mediaObjectSample.is().enabled();
      mediaObjectSample.bodyOfMediaObject.is().text(is(bodyTextOfMediaObjectSample));
      mediaObjectSample.bodyOfMediaObject.is().text(containsString("American comic books"));
      assertThat(mediaObjectSample.headingOfMediaObject.core().css("font-size"), is("20px"));
      assertThat(mediaObjectSample.bodyOfMediaObject.core().css("font-size"), is("14px"));
      mediaObjectSample.bodyOfMediaObject.assertThat().displayed()
              .and().text(is(bodyTextOfMediaObjectSample))
              .core()
              .css("font-size", is("14px"))
              .cssClass("media-body")
      ;
  }
  ```

```html
<div class="media" id="media-object-sample">
    <img src="images/wolverin.jpg" class="mr-3" alt="...">
    <div class="media-body">
        <h5 class="mt-0">WOLVERINE</h5>
        Wolverine is a fictional character appearing in American comic books published by Marvel
        Comics, mostly in association with the X-Men. He is a mutant who possesses animal-keen
        senses, enhanced physical capabilities, powerful regenerative ability known as a healing
        factor, and three retractable claws in each hand.
    </div>
</div>
```


**Media object nesting**

![Media object nesting](../../images/bootstrap/media-object-nesting.png)

Here is an example with provided Bootstrap v4.3 code:

  ```java 
  // @FindBy(css = "#media-object-nesting")
  @UI("#media-object-nesting") public static MediaObjectNesting mediaObjectNesting; 
  
  public class MediaObjectNesting extends MediaObject {
  @UI("img") public Image imageOfMediaObject;
  
  @Title
  @UI("h5") public Text headingOfMediaObject;
  
  @UI(".media-body") public Text bodyOfMediaObject;
  
  @UI("div.media div.media") public MediaObjectSample  nestingMediaObject;
  }
  
  @Test
  public void isValidationTestNesting() {
      mediaObjectNesting.is().displayed();
      mediaObjectNesting.is().enabled();
      mediaObjectNesting.nestingMediaObject.bodyOfMediaObject.is().text(is(bodyTextOfMediaObjectNesting));
      mediaObjectNesting.nestingMediaObject.bodyOfMediaObject.is().text(containsString("vel eu leo"));
      assertThat(mediaObjectNesting.nestingMediaObject.headingOfMediaObject.core().css("font-size"), is("20px"));
      assertThat(mediaObjectNesting.nestingMediaObject.bodyOfMediaObject.core().css("font-size"), is("14px"));
      mediaObjectNesting.nestingMediaObject.bodyOfMediaObject.assertThat().displayed()
              .and().text(is(bodyTextOfMediaObjectNesting))
              .core()
              .css("font-size", is("14px"))
              .cssClass("media-body")
      ;
  
  }
  
  ```

```html
<div class="media" id="media-object-nesting">
    <img src="images/wolverin.jpg" class="mr-3" alt="...">
    <div class="media-body">
        <h5 class="mt-0">Media heading</h5>
        Cras sit amet nibh libero, in gravida nulla. Nulla vel metus scelerisque ante
        sollicitudin.
        <div class="media mt-3">
            <a class="mr-3" href="https://jdi-testing.github.io/jdi-light/index.html"
               target="_blank">
                <img src="images/punisher.jpg" class="mr-3" alt="...">
            </a>
            <div class="media-body">
                <h5 class="mt-0">IRON MAN</h5>
                Donec sed odio dui. Nullam quis risus eget urna mollis ornare vel eu leo.
            </div>
        </div>
    </div>
</div>
```


**Media object list**


![Media object list](../../images/bootstrap/media-object-list.png)

Here is an example with provided Bootstrap v4.3 code:

```java 
    // @FindBy(css = "#media-object-list")
    @UI("#media-object-list") public static JList<MediaObjectSample> mediaObjectList; 
    
    @Test
    public void isValidationTestListMediaObject() {
        mediaObjectList.is().displayed();
        mediaObjectList.is().enabled();
        mediaObjectList.get(1).headingOfMediaObject.is().text(is(listOfHeading.get(0)));
        mediaObjectList.get(2).bodyOfMediaObject.is().text(containsString("Stark requires"));
        assertThat(mediaObjectList.get(2).headingOfMediaObject.core().css("font-size"), is("20px"));
        assertThat(mediaObjectList.get(1).bodyOfMediaObject.core().css("font-size"), is("14px"));
        mediaObjectList.assertThat().displayed()
                .core()
                .css("font-size", is("14px"));
    }

```

```html
<ul class="list-unstyled" id="media-object-list">
    <li class="media">
        <img src="images/wolverin.jpg" class="mr-3" alt="...">
        <div class="media-body">
            <h5 class="mt-0 mb-1">WOLVERINE first</h5>
            Wolverine is a fictional character appearing in American comic books published by
            Marvel Comics
        </div>
    </li>
    <li class="media my-4">
        <img src="images/punisher.jpg" class="mr-3" alt="...">
        <div class="media-body">
            <h5 class="mt-0 mb-1">IRON MAN second</h5>
            I do anything and everything that Mr. Stark requires — including occasionally taking
            out the trash
        </div>
    </li>
    <li class="media">
        <img src="images/spider-man.jpg" class="mr-3" alt="...">
        <div class="media-body">
            <h5 class="mt-0 mb-1">SPIDER MAN third</h5>
            Spider-Man is a fictional superhero created by writer-editor Stan Lee and
            writer-artist Steve Ditko.
        </div>
    </li>
</ul>
```

Media object is represented by MediaObject class:

<a href="https://github.com/jdi-testing/jdi-light/tree/bootstrap/jdi-light-bootstrap/src/main/java/com/epam/jdi/light/ui/bootstrap/elements/composite/MediaObject.java">MediaObject</a>

MediaObject class is inherited from Section class:

[Section](https://jdi-docs.github.io/jdi-light/#section)

Inner elements of media object can be represented by the following classes:
<ul>
    <li> [Text](https://jdi-docs.github.io/jdi-light/#text) </li>
    <li> [Label](https://jdi-docs.github.io/jdi-light/#label) </li>
    <li> [Link](https://jdi-docs.github.io/jdi-light/#link)  </li>
    <li> [Image](https://jdi-docs.github.io/jdi-light/#image)  </li>
    <li> [See more elements](https://jdi-docs.github.io/jdi-light/#html5-common-elements) </li>
</ul>

   <a href="https://github.com/jdi-testing/jdi-light/tree/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/composite/section/mediaObject/MediaObjectTests.java" target=a_blank> Bootstrap test examples </a>


#### Modal
[Modal](https://getbootstrap.com/docs/4.3/components/modal/) is a dialog box/popup window that is displayed on page.

##### [Modal Live demo](https://getbootstrap.com/docs/4.3/components/modal/#live-demo)
Toggle a working modal demo by clicking the button below. It will slide down and fade in from the top of the page.

![Modal_Live_demo](../../images/bootstrap/modal-live-demo.png)

Here is an example with provided Bootstrap v4.3 code:

```java 
//FindBy(css = "#modal-live-demo .bd-example .btn")
@UI("#modal-live-demo .bd-example .btn") 
public static Button modalLiveDemoLaunchButton;

//FindBy(css = "#exampleModalLive")
@UI("#exampleModalLive") 
public static ModalLiveDemo modalLiveDemo;

public class ModalLiveDemo extends Modal {
    @UI(".modal-body") public Text body;
    @UI("//div[@class='modal-footer']//button[1]") public Button closeButton;
    @UI("//div[@class='modal-footer']//button[2]") public Button saveButton;
    @UI(".modal-header .close") public Button closeX;
}

@Test
public void modalContentTextTest() {
    modalLiveDemoLaunchButton.is().text(is(launchButtonText));
    modalLiveDemoLaunchButton.click();
    modalLiveDemo.title.is().text(is(titleText));
    modalLiveDemo.body.is().text(is(bodyText));
    modalLiveDemo.saveButton.is().text(is(saveButtonText));
    modalLiveDemo.closeButton.is().text(is(closeButtonText));
    modalLiveDemo.close();
}

@Test
public void saveAndCloseButtonsTest() {
    modalLiveDemoLaunchButton.click();
    modalLiveDemo.is().displayed();
    modalLiveDemo.saveButton.click();
    modalLiveDemo.is().displayed();
    modalLiveDemo.closeButton.click();
    modalLiveDemo.is().hidden();
}
```

```html
<div id="exampleModalLive" class="modal fade" tabindex="-1" role="dialog"
     aria-labelledby="exampleModalLiveLabel" aria-hidden="true">
    <div class="modal-dialog" role="document">
        <div class="modal-content">
            <div class="modal-header">
                <h5 class="modal-title" id="exampleModalLiveLabel">Modal title</h5>
                <button type="button" class="close" data-dismiss="modal" aria-label="Close">
                    <span aria-hidden="true">&times;</span>
                </button>
            </div>
            <div class="modal-body">
                <p>Woohoo, you're reading this text in a modal!</p>
            </div>
            <div class="modal-footer">
                <button type="button" class="btn btn-secondary" data-dismiss="modal">Close
                </button>
                <button type="button" class="btn btn-primary">Save changes</button>
            </div>
        </div>
    </div>
</div>
```

Modal is represented by Section class in Java:

+ Section #BS

Inner elements of Modal - Live demo are represented by the following classes:

+ [Text](https://jdi-docs.github.io/jdi-light/#text)
+ [Button](https://jdi-docs.github.io/jdi-light/#button)

Available methods in Java JDI Light:

|Method | Description | Return Type
--- | --- | ---
**close()** | Close modal | void
**click()** | Click the button | void
**getText()** | Returns text | String
**is()** | Asserts element  | UIAssert

[Bootstrap test examples](https://github.com/jdi-testing/jdi-light/tree/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/composite/section/modal/ModalLiveDemoTests.java)

##### [Scrolling Long Content Modal](https://getbootstrap.com/docs/4.3/components/modal/#scrolling-long-content)

When modals become too long for the user’s viewport or device, they scroll independent of the page itself.

![Modal long scrollable](../../images/bootstrap/modal_scrollable1.png)

Here is an example with provided Bootstrap v4.3 code:

```java 
// @FindBy(id = "modal-scroll-long")
@UI("#modal-scroll-long")
public static SectionModalLongScrolling sectionModalLongScrolling;

// @FindBy(id = "exampleModalLong")
@UI("#exampleModalLong")
public ModalWithButtons modalLong;

// @FindBy(id = "exampleModalScrollable")
@UI("#exampleModalScrollable")
public ModalWithButtons modalScrollable;

// @FindBy(css = "#modal-scroll-long div:nth-child(2) button")
@UI("div:nth-child(2) button")
public Button buttonLongScroll;

// @FindBy(css = "#modal-scroll-long div:nth-child(4) button")
@UI("div:nth-child(4) button")
public Button buttonLongScrollable;

@DataProvider
public Object[][] listData() {
    return new Object[][]{
            {sectionModalLongScrolling.buttonLongScroll, sectionModalLongScrolling.modalLong},
            {sectionModalLongScrolling.buttonLongScrollable, sectionModalLongScrolling.modalScrollable}
    };
}

@Test(dataProvider = "listData")
public void bottomButtonsTest(Button showModal, ModalWithButtons modal) {
    showModal.click();
    modal.is().displayed();
    modal.bottomSave();
    modal.bottomClose();
    modal.is().disappear();
}
```

```html 
<!-- Button trigger modal -->
<button type="button" class="btn btn-primary" data-toggle="modal" data-target="#exampleModalLong">
  Launch demo modal
</button>

<!-- Modal -->
<div class="modal fade" id="exampleModalLong" tabindex="-1" role="dialog" aria-labelledby="exampleModalLongTitle" aria-hidden="true">
  <div class="modal-dialog" role="document">
    <div class="modal-content">
      <div class="modal-header">
        <h5 class="modal-title" id="exampleModalLongTitle">Modal title</h5>
        <button type="button" class="close" data-dismiss="modal" aria-label="Close">
          <span aria-hidden="true">&times;</span>
        </button>
      </div>
      <div class="modal-body">
        ...
      </div>
      <div class="modal-footer">
        <button type="button" class="btn btn-secondary" data-dismiss="modal">Close</button>
        <button type="button" class="btn btn-primary">Save changes</button>
      </div>
    </div>
  </div>
</div>
```

![Modal scrollable](../../images/bootstrap/modal_scrollable2.png)

Here is an example with provided Bootstrap v4.3 code:

```html 
<!-- Button trigger modal -->
<button type="button" class="btn btn-primary" data-toggle="modal" data-target="#exampleModalScrollable">
  Launch demo modal
</button>

<!-- Modal -->
<div class="modal fade" id="exampleModalScrollable" tabindex="-1" role="dialog" aria-labelledby="exampleModalScrollableTitle" aria-hidden="true">
  <div class="modal-dialog modal-dialog-scrollable" role="document">
    <div class="modal-content">
      <div class="modal-header">
        <h5 class="modal-title" id="exampleModalScrollableTitle">Modal title</h5>
        <button type="button" class="close" data-dismiss="modal" aria-label="Close">
          <span aria-hidden="true">&times;</span>
        </button>
      </div>
      <div class="modal-body">
        ...
      </div>
      <div class="modal-footer">
        <button type="button" class="btn btn-secondary" data-dismiss="modal">Close</button>
        <button type="button" class="btn btn-primary">Save changes</button>
      </div>
    </div>
  </div>
</div>
```

Modal is represented by Section class in Java:

+ Section #BS

Available methods in Java JDI Light:

|Method | Description | Return Type
--- | --- | ---
**close()** | Close modal | void
**displayed()** | Asserts element is displayed  | UIAssert
**is()** | Asserts element  | UIAssert
**hidden()** | Asserts element is hidden | UIAssert

[Bootstrap test examples](https://github.com/jdi-testing/jdi-light/tree/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/composite/section/modal/ModalScrollingLongContentTests.java)

##### [Vertically Centered Modal](https://getbootstrap.com/docs/4.3/components/modal/#vertically-centered)

Add ``.modal-dialog-centered`` to ``.modal-dialog`` to vertically center the modal.

![Modal Vertically Centered](../../images/bootstrap/modal-vertically-centered.png)

```java 

// @FindBy(id = "modal-vertically-centered")
@UI("#modal-vertically-centered")
public static ModalVerticallyCentered modalVerticallyCentered;

@Test(dataProvider = "modalBasicData")
public void modalBasicFunctionalityTest(Button showButton,
                                        Button dismissButton,
                                        Modal modal,
                                        String modalId) {
    WebDriverWait wait = new WebDriverWait(WebDriverFactory.getDriver(), 5);

    showButton.show();
    showButton.click();

    wait.until(ExpectedConditions.visibilityOfElementLocated(By.id(modalId)));

    modal.is().displayed();

    dismissButton.show();
    dismissButton.click();

    modal.is().hidden();
}
```

Here is an example with provided Bootstrap v4.3 code:

```html
<div id="exModalCenter" class="modal fade" tabindex="-1" role="dialog"
     aria-labelledby="exampleModalCenterTitle" aria-hidden="true">
    <div class="modal-dialog modal-dialog-centered" role="document">
        <div id="modal-vertical-content-1" class="modal-content">
            <div class="modal-header">
                <h5 class="modal-title" id="exModalCenterTitle">Modal title</h5>
                <button type="button" class="close" data-dismiss="modal" aria-label="Close">
                    <span aria-hidden="true">&times;</span>
                </button>
            </div>
            <div class="modal-body">
                <p>Cras mattis consectetur purus sit amet fermentum. Cras justo odio, dapibus ac
                    facilisis in, egestas eget quam. Morbi leo risus, porta ac consectetur ac,
                    vestibulum at eros.</p>
            </div>
            <div class="modal-footer">
                <button type="button" class="btn btn-secondary" data-dismiss="modal">Close
                </button>
                <button type="button" class="btn btn-primary">Save changes</button>
            </div>
        </div>
    </div>
</div>
```

Modal is represented by Section class in Java:

+ Section #BS

Available methods in Java JDI Light:

|Method | Description | Return Type
--- | --- | ---
**close()** | Close modal | void
**displayed()** | Asserts element is displayed  | UIAssert
**hidden()** | Asserts element is hidden | UIAssert
**is()** | Asserts element  | UIAssert

<a href="https://github.com/jdi-testing/jdi-light/blob/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/composite/section/modal/ModalVerticallyCenteredTests.java" target="_blank">Bootstrap Test Examples</a>

##### Modal - Tooltips and popovers

**Modal - Tooltips and popovers**

Tooltips and popovers can be placed within modals as needed. When modals are closed, any tooltips and popovers within are also automatically dismissed.


![Modal - Tooltips and popovers](../../images/bootstrap/modal-tooltips-and-popovers.png)

Here is an example with provided Bootstrap v4.3 code:

```java 
//@Findby(xpath="//h4[.='Modal - Tooltips and popovers']/../..")
@UI("//h4[.='Modal - Tooltips and popovers']/../..")
public static ModalTooltipsAndPopovers modalTooltipsAndPopovers;

public class ModalTooltipsAndPopovers extends Section {
//@Findby(xpath="//button")
    @UI("//button") public Button demoModalButton;
    public ModalTooltipsAndPopoversDialog modalDlg;
}

public class ModalTooltipsAndPopoversDialog extends Modal {
//@Findby(css=".modal-body")
    @UI(".modal-body")
    public ModalTooltipsAndPopoversBody body;
    @UI("//div[@class='modal-footer']//button[1]")
    public Button closeButton;
    @UI("//div[@class='modal-footer']//button[2]")
    public Button saveButton;
}

public class ModalTooltipsAndPopoversBody extends Section {
//@Findby(css="h5:nth-child(1)")
    @UI("h5:nth-child(1)") public Text title1;
    public Popover popover;
    @UI("h5:nth-child(4)") public Text title2;
    @UI("p:nth-child(5) > a:nth-child(1)") public Link thisLink;
    public Tooltip tooltipOnLink;
    @UI("p:nth-child(5) > a:nth-child(2)") public Link thatLink;
}

@Test
public void verifyOpenModalDialogTooltips() {
    modalTooltipsAndPopovers.demoModalButton.click();
    modalTooltipsAndPopovers.modalDlg.title.is().text(is(TITLE));
    modalTooltipsAndPopovers.modalDlg.body.title1.is().text(is(BODY_TITLE1));
    modalTooltipsAndPopovers.modalDlg.body.title2.is().text(is(BODY_TITLE2));
    modalTooltipsAndPopovers.modalDlg.body.thisLink.is().text(is(THIS_LINK));
    modalTooltipsAndPopovers.modalDlg.body.thatLink.is().text(is(THAT_LINK));
    modalTooltipsAndPopovers.modalDlg.saveButton.is().text(is(SAVE_BUTTON));
    modalTooltipsAndPopovers.modalDlg.closeButton.is().text(is(CLOSE_BUTTON));
    modalTooltipsAndPopovers.modalDlg.closeButton.click();
}

```

```html
<div id="exampleModalPopovers" class="modal fade" tabindex="-1" role="dialog"
     aria-labelledby="exampleModalPopoversLabel" aria-hidden="true">
    <div class="modal-dialog" role="document">
        <div class="modal-content">
            <div class="modal-header">
                <h5 class="modal-title" id="exampleModalPopoversLabel">Modal title</h5>
                <button type="button" class="close" data-dismiss="modal" aria-label="Close">
                    <span aria-hidden="true">&times;</span>
                </button>
            </div>
            <div class="modal-body">
                <h5>Popover in a modal</h5>
                <p>This <a href="#exampleModalPopovers" role="button" class="btn btn-secondary popover-test"
                           title="Popover title" data-toggle="popover"
                           data-content="Popover body content is set in this attribute."
                           data-container="#exampleModalPopovers">button</a> triggers a popover on click.
                </p>
                <hr/>
                <h5>Tooltips in a modal</h5>
                <p><a href="#exampleModalPopovers" class="tooltip-test" title="Tooltip" data-toggle="tooltip"
                      data-container="#exampleModalPopovers">This link</a> and
                    <a href="#exampleModalPopovers" class="tooltip-test" title="Tooltip" data-toggle="tooltip"
                       data-container="#exampleModalPopovers">that link</a> have tooltips on hover.
                </p>
            </div>
            <div class="modal-footer">
                <button type="button" class="btn btn-secondary" data-dismiss="modal">Close
                </button>
                <button type="button" class="btn btn-primary">Save changes</button>
            </div>
        </div>
    </div>
</div>
```

Modal is represented by Section class in Java:

+ Section #BS

Available methods in Java JDI Light:

|Method | Description | Return Type
--- | --- | ---
**close()** | Close modal | void
**displayed()** | Asserts element is displayed  | UIAssert
**hidden()** | Asserts element is hidden | UIAssert
**is()** | Asserts element  | UIAssert


<a href="https://github.com/jdi-testing/jdi-light/blob/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/composite/section/modal/ModalTooltipsAndPopoversTests.java" target="_blank">Bootstrap Test Examples</a>

<br><br>

**Modal using grid**

<a style="font-weight: bold;" target="_blank" href="https://getbootstrap.com/docs/4.3/components/modal/#using-the-grid">Modal using grid</a>

![Modal using grid example](../../images/bootstrap/modal-grid.png)

Here is an example with provided Bootstrap v4.3 code:

```java 
public class GridModalBody extends Section {
//FindBy(css = ".row")
@UI(".row")
private JList<GridRow> allGridRows;

//FindBy(css = '[class*='col']')
@UI("[class*='col']")
private JList<GridCell> allGridCells;

public JList<GridCell> getAllCells() {
   return allGridCells;
}

public JList<GridRow> getAllRows() {
   return allGridRows;
}

public GridRow getGridRow(int rowN) {
   return allGridRows.get(rowN);
}

public GridCell getCellInRow(int rowN, int cellN) {
    return getGridRow(rowN).getCell(cellN);
}

public String getTextFromCellInRow(int rowN, int cellN) {
        return getCellInRow(rowN, cellN).getText();
    }
}

@Test(dataProvider = "gridData")
public void checkTextInCell(int rowN, int cellN, String textExpected, String max_width) {
GridCell cell = gridModalSection.getGridModalWindow().getBody()
    .getCellInRow(rowN, cellN);
    cell.highlight("blue");
    cell.is().core()
             .text(textExpected)
             .and()
             .css("max-width", startsWith(max_width));
    cell.unhighlight();
    }

@Test
public void checkCloseXModalButton() {
     gridModalSection.getGridModalWindow().getBtnCloseX().highlight("red");
     gridModalSection.getGridModalWindow().close();
     gridModalSection.getGridModalWindow().is().disappear();
    }

@Test
public void checkCloseByEscapeButton() {
     gridModalSection.getGridModalWindow().core().sendKeys(Keys.ESCAPE);
     gridModalSection.getGridModalWindow().is().disappear();
    }
```

```html
<div id="grid-modal-base" class="html-left mb-3">
    <div id="gridSystemModal" class="modal fade" tabindex="-1" role="dialog"
         aria-labelledby="gridModalLabel" aria-hidden="true">
        <div class="modal-dialog" role="document">
            <div class="modal-content">
                <div class="modal-header">
                    <h5 class="modal-title" id="gridModalLabel">Grids in modals</h5>
                    <button id="close-modal-cross" type="button" class="close" data-dismiss="modal"
                            aria-label="Close"><span aria-hidden="true">&times;</span></button>
                </div>
                <div class="modal-body">
                    <div class="container-fluid bd-example-row">
                        <div class="row">
                            <div class="col-md-4">.col-md-4</div>
                            <div class="col-md-4 ml-auto">.col-md-4 .ml-auto</div>
                        </div>
                        <div class="row">
                            <div class="col-md-3 ml-auto">.col-md-3 .ml-auto</div>
                            <div class="col-md-2 ml-auto">.col-md-2 .ml-auto</div>
                        </div>
                        <div class="row">
                            <div class="col-md-6 ml-auto">.col-md-6 .ml-auto</div>
                        </div>
                        <div class="row">
                            <div class="col-sm-9">
                                Level 1: .col-sm-9
                                <div class="row">
                                    <div class="col-8 col-sm-6">
                                        Level 2: .col-8 .col-sm-6
                                    </div>
                                    <div class="col-4 col-sm-6">
                                        Level 2: .col-4 .col-sm-6
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
                <div class="modal-footer">
                    <button id="close-modal" type="button" class="btn btn-secondary"
                            data-dismiss="modal">Close
                    </button>
                    <button id="save-modal" type="button" class="btn btn-primary">Save changes
                    </button>
                </div>
            </div>
        </div>
    </div>

    <div class="bd-example">
        <button id="btn-modal-using-grid" type="button" class="btn btn-primary" data-toggle="modal"
                data-target="#gridSystemModal">Launch demo modal
        </button>
    </div>
</div>
```

Available methods in Java JDI Light:

|Method/Property | Description | Return Type
--- | --- | ---
**close()** | Close Modal Window using X control | void
**clickBtnClose()** | Close Modal Window  | void
**displayed()** | Asserts element is displayed  | UIAssert
**disappear()** | Asserts element is not displayed | UIAssert
**getCellInRow(int rowN, int cellN)** | Get cellN from rowN | GridCell
**getGridRow(int rowN)** | Get rowN  | GridRow
**getTitle()** | Get Modal Window Title | Text

[Bootstrap test examples](https://github.com/jdi-testing/jdi-light/tree/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/composite/section/modal/GridModalTests.java)

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

**Varying modal content**

Have a bunch of buttons that all trigger the same modal with slightly different contents? Use event.relatedTarget and HTML data-* attributes (possibly via jQuery) to <a href="https://getbootstrap.com/docs/4.3/components/modal/#varying-modal-content">vary the contents</a> of the modal depending on which button was clicked.

![Varying modal content example](../../images/bootstrap/modal-varying-content.PNG)

Here is an example with provided Bootstrap v4.3 code:

```java 
    public class Modal extends Section {
        //@FindBy(xpath = "div/h5[@class='modal-title']")
        @UI(".modal-header .modal-title")
        public Text title;
    }

    public class ModalVaryingContent extends Modal {
        //@FindBy(xpath = "div/button[@class='close']")
        @UI(".modal-header .close")
        public Button closeX;
    }

    @Test(dataProvider = "modalVaryingContentButtonsWithRecipients")
    public void modalButtonsTest(Button modalButton, String recipient) {
        checkButton(modalButton, String.format("Open modal for @%s", recipient), 
        whiteColor, blueColorBackground, blueColorBorder);
    }

    @Test(dataProvider = "modalVaryingContentButtonsWithRecipients")
    public void headerValidationTest(Button modalButton, String recipient) {
        modalButton.click();
        modalVaryingContentWindow.is().displayed();
        modalVaryingContentWindow.title.core().is()
                .text(String.format("NEW MESSAGE TO @%s", recipient.toUpperCase()));
        modalVaryingContentWindow.closeX.click();
        modalVaryingContentWindow.is().hidden();
    }

    private void checkButton(Button button, String text, String color, 
    String backgroundColor, String borderColor) {
        button.is().core()
                .text(text)
                .tag("button")
                .css("color", color)
                .css("background-color", backgroundColor)
                .css("border-color", borderColor);
    }
```

```html
<div class="modal fade" id="exampleModal" tabindex="-1" role="dialog"
     aria-labelledby="exampleModalLabel" aria-hidden="true">
    <div class="modal-dialog" role="document">
        <div id="modalVaryingContentWindow" class="modal-content">
            <div class="modal-header">
                <h5 class="modal-title" id="exampleModalLabel">New message</h5>
                <button type="button" class="close" data-dismiss="modal" aria-label="Close">
                    <span aria-hidden="true">&times;</span>
                </button>
            </div>
            <div class="modal-body">
                <form>
                    <div class="form-group">
                        <label for="recipient-name"
                               class="col-form-label">Recipient:</label>
                        <input type="text" class="form-control" id="recipient-name"/>
                    </div>
                    <div class="form-group">
                        <label for="message-text" class="col-form-label">Message:</label>
                        <textarea class="form-control" id="message-text"></textarea>
                    </div>
                </form>
            </div>
            <div class="modal-footer">
                <button type="button" class="btn btn-secondary" data-dismiss="modal">Close
                </button>
                <button type="button" class="btn btn-primary">Send message</button>
            </div>
        </div>
    </div>
</div>
```

Available methods in Java JDI Light:

|Method/Property | Description | Return Type
--- | --- | ---
**assertThat()** | Assert action  | TextAssert
**click()** | Click button  | void
**displayed()** | Assert is displayed  | void
**getTitle()** | Get Modal Window Title | Text
**getText()** | Get text value of the element | String


[Bootstrap test examples](https://github.com/jdi-testing/jdi-light/blob/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/composite/section/modal/ModalVaryingContentTests.java)

<br><br>

**Embedding YouTube videos**

Embedding YouTube videos in modals requires additional JavaScript not in Bootstrap to automatically stop playback and more. See <a href="https://stackoverflow.com/questions/18622508/bootstrap-3-and-youtube-in-modal">this helpful Stack Overflow post</a> for more information.

![Embedding YouTube video example](../../images/bootstrap/modal-youtube.png)

Here is an example with provided Bootstrap v4.3 code:

```java  
@UI("#modal-youtube button.btn-primary")
public static Button modalEmbeddedVideoButton;
@UI("#youTubeModalLabel")
public static EmbeddedVideoModal embeddedVideoModal;

private final static String VIDEO_TITLE = "Forget about Selenium. May the JDI Light force be with you";
private final static String VIDEO_URL = "https://www.youtube.com/watch?v=lw4g9ItC7Sc";

@Test
public void videoTitleTest() {
    modalEmbeddedVideoButton.click();
    embeddedVideoModal.getVideoModalFrame().getVideoTitle().is()
        .displayed()
        .enabled()
        .ref(VIDEO_URL)
        .text(VIDEO_TITLE);
    embeddedVideoModal.close();
}

@Test
public void playVideoTest() {
    modalEmbeddedVideoButton.click();
    embeddedVideoModal.getVideoModalFrame().getPlayButton().click();
    embeddedVideoModal.getVideoModalFrame().getProgressBar().assertThat()
        .displayed()
        .attr("aria-valuenow", Matchers.matchesPattern("[1-9]{1}[0-9]*"));
    embeddedVideoModal.close();
}
```

```html
<div id="modal-youtube" class="html-left mb-3">
    <div class="bd-example">
        <button type="button" class="btn btn-primary mb-3" data-toggle="modal"
                data-target="#youTubeModalLabel">Embedding YouTube video
        </button>
    </div>
    <div class="modal fade" tabindex="-1" role="dialog" aria-labelledby="youTubeModalLabel"
         id="youTubeModalLabel" aria-hidden="true">
        <div class="modal-dialog modal-xl">
            <div class="modal-content">

                <div class="modal-header">
                    <h5 class="modal-title h4">Embedding YouTube video</h5>
                    <button type="button" class="close" data-dismiss="modal" aria-label="Close">
                        <span aria-hidden="true">×</span>
                    </button>
                </div>
                <div class="modal-body">
                    <iframe allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture"
                            allowfullscreen="" src="https://www.youtube.com/embed/lw4g9ItC7Sc"
                            width="1120" height="630" frameborder="0"></iframe>
                </div>
            </div>
        </div>
    </div>
</div>
```

Available methods in Java JDI Light:

|Method/Property | Description | Return Type
--- | --- | ---
**close()** | Close Modal Window using X control | void
**displayed()** | Asserts element is displayed  | UIAssert
**disappear()** | Asserts element is not displayed | UIAssert
**waitFor()** | Assert action | UIAssert

[Bootstrap test examples](https://github.com/jdi-testing/jdi-light/blob/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/composite/section/modal/ModalEmbeddingVideoTests.java)

<br><br>

**Optional Sizes**

Modals have three <a style="font-weight: bold;" href="https://getbootstrap.com/docs/4.3/components/modal/#optional-sizes" target="_blank">optional sizes</a>, available via modifier classes to be placed on a ``.modal-dialog``.
These sizes kick in at certain breakpoints to avoid horizontal scrollbars on narrower viewports.

![Modal Optional Sizes Example](../../images/bootstrap/modal-optional-sizes.jpg)

```java  
// @FindBy(id = "modal-optional-sizes")
@UI("#modal-optional-sizes")
public static ModalOptionalSizes modalOptionalSizes;

// @FindBy(css = "button:nth-of-type(1)")
@UI("button:nth-of-type(1)")
public Button xlButton;

// @FindBy(css = "button:nth-of-type(2)")
@UI("button:nth-of-type(2)")
public Button lgButton;

// @FindBy(css = "button:nth-of-type(3)")
@UI("button:nth-of-type(3)")
public Button smButton;

@Test(dataProvider = "modalCssData")
public void modalCssTest(Button button, Modal modal, String modalCss) {
    button.show();
    button.click();

    modal.is().displayed();

    modal.children().get(1).core().is().hasClass(modalCss);

    modal.close();
}

@Test(dataProvider = "modalSizeData")
public void modalSizeTest(Button button,
                          Modal modal,
                          int modalWidth) {
    button.show();
    button.click();

    modal.is().displayed();

    assertThat(modal.children().get(2).core().getRect().width, equalTo(modalWidth));

    modal.close();
}
```

Here is an example with provided Bootstrap v4.3 code:

```html
<div class="modal fade bd-example-modal-xl" tabindex="-1" role="dialog"
     aria-labelledby="myExtraLargeModalLabel" aria-hidden="true">
    <div class="modal-dialog modal-xl">
        <div class="modal-content">

            <div class="modal-header">
                <h5 class="modal-title h4" id="myExtraLargeModalLabel">Extra large modal</h5>
                <button type="button" class="close" data-dismiss="modal" aria-label="Close">
                    <span aria-hidden="true">&times;</span>
                </button>
            </div>
            <div class="modal-body">
                ...
            </div>
        </div>
    </div>
</div>
```

Modal is represented by Section class in Java:

+ Section #BS

Available methods in Java JDI Light:

|Method | Description | Return Type
--- | --- | ---
**close()** | Close modal | void
**displayed()** | Asserts element is displayed  | UIAssert
**hidden()** | Asserts element is hidden | UIAssert
**hasClass()** | Matches passed value with the element class | IsAssert
**is()** | Asserts element  | UIAssert

<a href="https://github.com/jdi-testing/jdi-light/blob/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/composite/section/modal/ModalOptionalSizesTests.java" target="_blank">Bootstrap Test Examples</a>

#### Popovers

***[Popovers](https://getbootstrap.com/docs/4.3/components/popovers/)***

##### Example
**[Popover example](https://getbootstrap.com/docs/4.3/components/popovers/#example)**

![Popover example](../../images/bootstrap/popover-title.png)

Here is an example with provided Bootstrap v4.3 code:

```java 
// @FindBy(css = "body") public static Popover popover;
@UI("body") public static Popover popover;

@Test
public void isValidationTests() {
    popover.getPopover(locator);
    popover.popoverButton.is()
            .displayed()
            .enabled()
            .core()
            .attr("data-toggle", "popover")
            .attr("data-content", popoverBody)
            .attr("data-original-title", popoverHeader)
            .text(is(buttonText));
    popover.container
            .is()
            .enabled()
            .core()
            .hasClass("popover fade bs-popover-right show")
            .attr("role", "tooltip")
            .attr("x-placement", "right");
    popover.body
            .is()
            .enabled()
            .core()
            .hasClass("popover-body")
            .text(is(popoverBody));
    popover.header
            .is()
            .core()
            .hasClass("popover-header")
            .text(is(popoverHeader.toUpperCase()));
    popover.popoverButton.click();
}

@Test()
public void clickableTests() {
    popover.getPopover(locator);
    popover.popoverButton.click();
    popover.popoverButton
            .is()
            .core()
            .attr("aria-describedby", containsString("popover"));
    popover.container
            .is()
            .enabled();
    popover.container.click();
    popover.popoverButton
            .is()
            .core()
            .attr("aria-describedby", "");
    assertFalse(popover.container.isDisplayed());
}
```

```html
<button type="button" class="btn btn-lg btn-danger btn-block mb-3" id="popover-title"
        data-toggle="popover" title="Popover title"
        data-content="And here's some amazing content. It's very engaging. Right?">Click to
    toggle popover
</button>
```

```html 
<div class="popover fade bs-popover-right show" role="tooltip" id="popover757247" style="will-change: 
    transform; position: absolute; transform: translate3d(542px, 39291px, 0px); top: 0px; left: 0px;" x-placement=
    "right">
    <div class="arrow" style="top: 35px;"></div>
    <h3 class="popover-header">Popover title</h3><div class="popover-body">And here's some amazing content. It's very engaging. Right?</div>
</div>
```



|Method | Description | Return Type
--- | --- | ---
**assertThat()** | Assert action | TextAssert
**click()** | Get button text | void
**disabled()** | assert is disabled | TextAssert
**displayed()** | assert is displayed | TextAssert
**get()** | Select button by index | UIElement
**getText()** | Get button text | String
**getPopover(String locator)** | Get the popover click  | void
**getBody()** | Get body of popover  |  String
**getContainer()** | Get container of popover  |  String
**getHeader()** | Get header of popover  |  String
**enabled()** | assert is enabled | TextAssert
**highlight()** | Get button text | void
**is()** | Assert action | TextAssert
**unhighlight()** | Get button text | void

<br>

[Java test examples](https://github.com/jdi-testing/jdi-light/blob/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/composite/section/popover/PopoverTests.java)<br>

Popover group is represented by Section class in Java:

[Section](https://jdi-docs.github.io/jdi-light/#section)

<br>

Inner elements of input group can be represented by following classes:
 <ul>
  <li> [Text](https://jdi-docs.github.io/jdi-light/#text) </li>

  <li> [Button](https://jdi-docs.github.io/jdi-light/#button-2) </li> 

  <li> [MediaObject](https://jdi-docs.github.io/jdi-light/#media-object) </li>
 </ul>


##### Four directions popovers
**[Four directions popovers](https://getbootstrap.com/docs/4.3/components/popovers/#four-directions)**

Popover top

![Four directions popover top example](../../images/bootstrap/popover-top.png)

Here is an example with provided Bootstrap v4.3 code:

```java 
// @FindBy(css = "body") public static Popover popover;
@UI("body") public static Popover popover;

@Test
public void isValidationTests() {
    popover.getPopover(locator);
    popover.popoverButton.is()
            .displayed()
            .enabled()
            .core()
            .attr("data-toggle", "popover")
            .attr("data-content", popoverBody)
            .attr("data-original-title", popoverHeader)
            .text(is(buttonText));
    popover.container
            .is()
            .enabled()
            .core()
            .hasClass("popover fade bs-popover-right show")
            .attr("role", "tooltip")
            .attr("x-placement", "right");
    popover.body
            .is()
            .enabled()
            .core()
            .hasClass("popover-body")
            .text(is(popoverBody));
    popover.header
            .is()
            .core()
            .hasClass("popover-header")
            .text(is(popoverHeader.toUpperCase()));
    popover.popoverButton.click();
}

@Test()
public void clickableTests() {
    popover.getPopover(locator);
    popover.popoverButton.click();
    popover.popoverButton
            .is()
            .core()
            .attr("aria-describedby", containsString("popover"));
    popover.container
            .is()
            .enabled();
    popover.container.click();
    popover.popoverButton
            .is()
            .core()
            .attr("aria-describedby", "");
    assertFalse(popover.container.isDisplayed());
}
```

```html
<button type="button" class="btn btn-secondary btn-block mb-3" id="popover-top"
        data-container="body" data-toggle="popover" data-placement="top"
        data-content="Top popover is visible.">
    Popover on top
</button>
```

```html 
<div class="popover fade show bs-popover-top" role="tooltip" id="popover561586" x-placement="top" 
    style="position: absolute; transform: translate3d(320px, 39051px, 0px); top: 0px; left: 0px; will-change: 
    transform;">
    <div class="arrow" style="left: 68px;"></div>
    <h3 class="popover-header"></h3><div class="popover-body">Top popover is visible.</div>
</div>
```

<br><br>

Popover right

![Four directions popover right example](../../images/bootstrap/popover-right.png)

Here is an example with provided Bootstrap v4.3 code:

```html
<button type="button" class="btn btn-secondary btn-block mb-3" id="popover-right"
        data-container="body" data-toggle="popover" data-placement="right"
        data-content="Right popover is visible.">
    Popover on right
</button>
```

```html 
<div class="popover fade bs-popover-right show" role="tooltip" id="popover525348" x-placement="right" 
    style="position: absolute; transform: translate3d(542px, 39152px, 0px); top: 0px; left: 0px; will-change: 
    transform;">
    <div class="arrow" style="top: 7px;"></div>
    <h3 class="popover-header"></h3>
    <div class="popover-body">Right popover is visible.</div>
</div>
```

<br><br>

Popover bottom

![Four directions popover bottom example](../../images/bootstrap/popover-bottom.png)

Here is an example with provided Bootstrap v4.3 code:

```html
<button type="button" class="btn btn-secondary btn-block mb-3" id="popover-bottom"
        data-container="body" data-toggle="popover" data-placement="bottom"
        data-content="Bottom popover is visible.">
    Popover on bottom
</button>
```

```html 
<div class="popover fade show bs-popover-bottom" role="tooltip" id="popover24015" x-placement="bottom" 
    style="position: absolute; transform: translate3d(308px, 39244px, 0px); top: 0px; left: 0px; will-change: 
    transform;">
    <div class="arrow" style="left: 80px;"></div>
    <h3 class="popover-header"></h3>
    <div class="popover-body">Bottom popover is visible.</div>
</div>
```
<br><br>

Popover left

![Four directions popover left example](../../images/bootstrap/popover-left.png)

Here is an example with provided Bootstrap v4.3 code:

```html
<button type="button" class="btn btn-secondary btn-block mb-3" id="popover-left"
        data-container="body" data-toggle="popover" data-placement="left"
        data-content="Left popover is visible.">
    Popover on left
</button>
```

```html 
<div class="popover fade bs-popover-left show" role="tooltip" id="popover587895" x-placement="left" 
    style="position: absolute; transform: translate3d(88px, 39260px, 0px); top: 0px; left: 0px; will-change: 
    transform;">
    <div class="arrow" style="top: 7px;"></div>
    <h3 class="popover-header"></h3>
    <div class="popover-body">Left popover is visible.</div>
</div>
```
<br><br>



|Method | Description | Return Type
--- | --- | ---
**assertThat()** | Assert action | TextAssert
**click()** | Get button text | void
**enabled()** | assert is enabled | TextAssert
**disabled()** | assert is disabled | TextAssert
**displayed()** | assert is displayed | TextAssert
**get()** | Select button by index | UIElement
**getText()** | Get button text | String
**highlight()** | Get button text | void
**is()** | Assert action | TextAssert
**unhighlight()** | Get button text | void

<br>

[Java test examples](https://github.com/jdi-testing/jdi-light/blob/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/composite/section/popover/PopoverTests.java)<br>

Popover group is represented by Section class in Java:

[Section](https://jdi-docs.github.io/jdi-light/#section)

<br>

Inner elements of input group can be represented by following classes:
 <ul>
  <li> [Text](https://jdi-docs.github.io/jdi-light/#text) </li>

  <li> [Button](https://jdi-docs.github.io/jdi-light/#button-2) </li> 

  <li> [MediaObject](https://jdi-docs.github.io/jdi-light/#media-object) </li>
 </ul>


##### Dismissible
**[Dismissible popover](https://getbootstrap.com/docs/4.3/components/popovers/#dismiss-on-next-click)**

![Dismissible popover example](../../images/bootstrap/popover-dismissible.png)

Here is an example with provided Bootstrap v4.3 code:

```java 
// @FindBy(css = "body") public static Popover popover;
@UI("body") public static Popover popover;

@Test
public void isValidationTests() {
    popover.getPopover(locator);
    popover.popoverButton.is()
            .displayed()
            .enabled()
            .core()
            .attr("data-toggle", "popover")
            .attr("data-content", popoverBody)
            .attr("data-original-title", popoverHeader)
            .text(is(buttonText));
    popover.container
            .is()
            .enabled()
            .core()
            .hasClass("popover fade bs-popover-right show")
            .attr("role", "tooltip")
            .attr("x-placement", "right");
    popover.body
            .is()
            .enabled()
            .core()
            .hasClass("popover-body")
            .text(is(popoverBody));
    popover.header
            .is()
            .core()
            .hasClass("popover-header")
            .text(is(popoverHeader.toUpperCase()));
    popover.popoverButton.click();
}

@Test()
public void clickableTests() {
    popover.getPopover(locator);
    popover.popoverButton.click();
    popover.popoverButton
            .is()
            .core()
            .attr("aria-describedby", containsString("popover"));
    popover.container
            .is()
            .enabled();
    popover.container.click();
    popover.popoverButton
            .is()
            .core()
            .attr("aria-describedby", "");
    assertFalse(popover.container.isDisplayed());
}
```

```html
<a tabindex="0" class="btn btn-lg btn-danger btn-block mb-3" role="button"
   id="popover-dismissible" data-toggle="popover" data-trigger="focus"
   title="Dismissible popover"
   data-content="And here's some amazing content. It's very engaging. Right?">Dismissible
    popover</a>
```

```html 
<div class="popover fade bs-popover-right" role="tooltip" id="popover278744" 
    style="will-change: transform; position: absolute; transform: translate3d(542px, 39355px, 0px); top: 0px; left: 0px;" 
    x-placement="right">
    <div class="arrow" style="top: 35px;"></div>
    <h3 class="popover-header">Dismissible popover</h3>
    <div class="popover-body">And here's some amazing content. It's very engaging. Right?</div>
</div>
```

|Method | Description | Return Type
--- | --- | ---
**assertThat()** | Assert action | TextAssert
**click()** | Get button text | void
**disabled()** | assert is disabled | TextAssert
**displayed()** | assert is displayed | TextAssert
**enabled()** | assert is enabled | TextAssert
**get()** | Select button by index | UIElement
**getText()** | Get button text | String
**highlight()** | Get button text | void
**is()** | Assert action | TextAssert
**unhighlight()** | Get button text | void

<br>

[Java test examples](https://github.com/jdi-testing/jdi-light/blob/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/composite/section/popover/PopoverTests.java)<br>

Popover group is represented by Section class in Java:

[Section](https://jdi-docs.github.io/jdi-light/#section)

<br>

Inner elements of input group can be represented by following classes:
 <ul>
  <li> [Text](https://jdi-docs.github.io/jdi-light/#text) </li>

  <li> [Button](https://jdi-docs.github.io/jdi-light/#button-2) </li> 

  <li> [MediaObject](https://jdi-docs.github.io/jdi-light/#media-object) </li>
 </ul>



##### Disabled elements popover

**[Disabled elements popover](https://getbootstrap.com/docs/4.3/components/popovers/#disabled-elements)**

![Disabled elements popover example](../../images/bootstrap/popover-disabled.png)

Here is an example with provided Bootstrap v4.3 code:

 ```java 
 // @FindBy(css = "body") public static Popover popover;
 @UI("body") public static Popover popover;
 
 @Test
 public void isValidationTests() {
     popover.getPopover(locator);
     popover.popoverButton.is()
             .displayed()
             .enabled()
             .core()
             .attr("data-toggle", "popover")
             .attr("data-content", popoverBody)
             .attr("data-original-title", popoverHeader)
             .text(is(buttonText));
     popover.container
             .is()
             .enabled()
             .core()
             .hasClass("popover fade bs-popover-right show")
             .attr("role", "tooltip")
             .attr("x-placement", "right");
     popover.body
             .is()
             .enabled()
             .core()
             .hasClass("popover-body")
             .text(is(popoverBody));
     popover.header
             .is()
             .core()
             .hasClass("popover-header")
             .text(is(popoverHeader.toUpperCase()));
     popover.popoverButton.click();
 }
 
 @Test()
 public void clickableTests() {
     popover.getPopover(locator);
     popover.popoverButton.click();
     popover.popoverButton
             .is()
             .core()
             .attr("aria-describedby", containsString("popover"));
     popover.container
             .is()
             .enabled();
     popover.container.click();
     popover.popoverButton
             .is()
             .core()
             .attr("aria-describedby", "");
     assertFalse(popover.container.isDisplayed());
 }
 ```

```html
<span class="d-inline-block mb-3" style="width:100%;" data-toggle="popover"
      id="popover-disabled" data-content="Disabled popover">
        <button class="btn btn-primary btn-block" style="pointer-events: none;" type="button"
                disabled>Disabled button</button>
</span>
```

```html 
<div class="popover fade show bs-popover-right" role="tooltip" id="popover180279" x-placement="right" 
    style="will-change: transform; position: absolute; transform: translate3d(542px, 39442px, 0px); top: 0px; left: 0px;">
    <div class="arrow" style="top: 7px;"></div>
    <h3 class="popover-header"></h3>
    <div class="popover-body">Disabled popover</div>
</div>
```



|Method | Description | Return Type
--- | --- | ---
**assertThat()** | Assert action | TextAssert
**click()** | Get button text | void
**disabled()** | assert is disabled | TextAssert
**displayed()** | assert is displayed | TextAssert
**enabled()** | assert is enabled | TextAssert
**get()** | Select button by index | UIElement
**getText()** | Get button text | String
**highlight()** | Get button text | void
**is()** | Assert action | TextAssert
**unhighlight()** | Get button text | void

<br>

[Java test examples](https://github.com/jdi-testing/jdi-light/blob/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/composite/section/popover/PopoverTests.java)<br>

Popover group is represented by Section class in Java:

[Section](https://jdi-docs.github.io/jdi-light/#section)

<br>

Inner elements of input group can be represented by following classes:
<ul>
    <li> [Text](https://jdi-docs.github.io/jdi-light/#text) </li>
    <li> [Button](https://jdi-docs.github.io/jdi-light/#button-2) </li> 
    <li> [MediaObject](https://jdi-docs.github.io/jdi-light/#media-object) </li>
</ul>

#### List group

***[List groups](https://getbootstrap.com/docs/4.3/components/list-group/)*** are a flexible and powerful component for displaying a series of content. Modify and extend them to support just about any content within.


##### Basic Example

***[List group basic example](https://getbootstrap.com/docs/4.3/components/list-group/#basic-example)*** - an unordered list with list items and the proper classes.

List Group is located in the following classes:

- __Java__: _com.epam.jdi.light.ui.bootstrap.elements.complex.ListGroup_


![List group basic example](../../images/bootstrap/list-group-basic.png)

Here is an example with provided Bootstrap v4.3 code:

```java 
@UI("#list-group-basic-example") public static ListGroupBasicExample listGroupBasicExample;
// @FindBy(css = "#list-group-basic-example") public static ListGroupBasicExample listGroupBasicExample;

public class ListGroupBasicExample extends Section {
    @UI("li") public ListGroup listGroup;
}

public void listGroupIsValidationTest() {
    listGroupBasicExample.listGroup.is()
            .size(5);
}

@Test(dataProvider = "listData")
public void listGroupTests(int num, String text) {
    listGroupBasicExample.listGroup.get(num).is()
            .text(is(text))
            .css("font-size", is("14px"));
}
```

```html
<ul class="list-group mb-3" id="list-group-basic-example">
    <li class="list-group-item">Cras justo odio</li>
    <li class="list-group-item">Dapibus ac facilisis in</li>
    <li class="list-group-item">Morbi leo risus</li>
    <li class="list-group-item">Porta ac consectetur ac</li>
    <li class="list-group-item">Vestibulum at eros</li>
</ul>
```



|Method | Description | Return Type
--- | --- | ---
**assertThat()** | Assert action | TextAssert
**get()** | Select button by index | action
**getText()** | Get button text | String
**is()** | Assert action | TextAssert

<br>

[Java test examples](https://github.com/jdi-testing/jdi-light/blob/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/composite/section/listGroup/BasicExampleTests.java)
<br>

Button group is represented by Section class in Java:

[Section](https://jdi-docs.github.io/jdi-light/#section)

<br>

##### Active Items

***[List group active Items](https://getbootstrap.com/docs/4.3/components/list-group/#active-items)***

List Group is located in the following classes:

- __Java__: _com.epam.jdi.light.ui.bootstrap.elements.complex.ListGroup_


![List group active items example](../../images/bootstrap/list-group-active.png)

Here is an example with provided Bootstrap v4.3 code:

```java 
@UI("#list-group-active-items") public static ListGroupActiveItems listGroupActiveItems;
// @FindBy(css = "#list-group-active-items") public static ListGroupActiveItems listGroupActiveItems;)

public class ListGroupActiveItems extends Section {
    @UI("li") public ListGroup listGroup;
}

@Test(dataProvider = "listData")
public void listGroupTextTests(int num, String text) {
    listGroupActiveItems.listGroup.get(num).is()
            .text(text)
            .css("font-size", is("14px"));
}

@Test
public void isValidationTests() {
    listGroupActiveItems.listGroup.is()
            .size(5);
    listGroupActiveItems.is()
            .displayed()
            .enabled()
            .core()
            .hasClass("list-group");
    listGroupActiveItems.listGroup.get(1).is()
            .hasClass(listClass + " active");
}
```

```html
<ul class="list-group mb-3" id="list-group-active-items">
    <li class="list-group-item active">Cras justo odio</li>
    <li class="list-group-item">Dapibus ac facilisis in</li>
    <li class="list-group-item">Morbi leo risus</li>
    <li class="list-group-item">Porta ac consectetur ac</li>
    <li class="list-group-item">Vestibulum at eros</li>
</ul>
```



|Method | Description | Return Type
--- | --- | ---
**assertThat()** | Assert action | TextAssert
**get()** | Select button by index | action
**getText()** | Get button text | String
**is()** | Assert action | TextAssert

<br>

[Java test examples](https://github.com/jdi-testing/jdi-light/blob/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/composite/section/listGroup/ActiveItemsTests.java)
<br>

Button group is represented by Section class in Java:

[Section](https://jdi-docs.github.io/jdi-light/#section)

<br>

##### Disabled Items

***[List group disabled Items](https://getbootstrap.com/docs/4.3/components/list-group/#disabled-items)***

List Group is located in the following classes:

- __Java__: _com.epam.jdi.light.ui.bootstrap.elements.complex.ListGroup_


![List group disabled items example](../../images/bootstrap/list-group-disabled.png)

Here is an example with provided Bootstrap v4.3 code:

```java 
@UI("#disabled-items") public static ListGroupDisabledItems listGroupDisabledItems;
// @FindBy(css = "#disabled-items") public static ListGroupDisabledItems listGroupDisabledItems;

public class ListGroupDisabledItems extends Section {
    @UI("li") public ListGroup listGroup;
}

@Test
public void isValidationTests() {
    listGroupDisabledItems.listGroup.is()
            .size(5);
    listGroupDisabledItems.is()
            .displayed()
            .enabled()
            .core()
            .hasClass("list-group");
    listGroupDisabledItems.listGroup.get(1).is()
            .hasClass(listClass + " disabled")
            .attr("aria-disabled", "true");
}

@Test(dataProvider = "listData")
public void listGroupTextTests(int num, String text) {
    listGroupDisabledItems.listGroup.get(num).is()
            .text(text)
            .css("font-size", is("14px"));
}
```

```html
<ul class="list-group mb-3" id="disabled-items">
    <li class="list-group-item disabled" aria-disabled="true">Cras justo odio</li>
    <li class="list-group-item">Dapibus ac facilisis in</li>
    <li class="list-group-item">Morbi leo risus</li>
    <li class="list-group-item">Porta ac consectetur ac</li>
    <li class="list-group-item">Vestibulum at eros</li>
</ul>
```



|Method | Description | Return Type
--- | --- | ---
**assertThat()** | Assert action | TextAssert
**get()** | Select button by index | action
**getText()** | Get button text | String
**is()** | Assert action | TextAssert

<br>

[Java test examples](https://github.com/jdi-testing/jdi-light/blob/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/composite/section/listGroup/DisabledItemsTests.java)
<br>

Button group is represented by Section class in Java:

[Section](https://jdi-docs.github.io/jdi-light/#section)

<br>

##### Links

***[List group links and buttons](https://getbootstrap.com/docs/4.3/components/list-group/#links-and-buttons)***

List Group is located in the following classes:

- __Java__: _com.epam.jdi.light.ui.bootstrap.elements.complex.ListGroup_


![List group links example](../../images/bootstrap/list-group-links.png)

Here is an example with provided Bootstrap v4.3 code:

```java 
@UI("#list-group-links") public static ListGroupLinks listGroupLinks;
// @FindBy(css = "#list-group-links") public static ListGroupLinks listGroupLinks;

public class ListGroupLinks extends Section {
    @UI("a") public ListGroup listGroup;
}

@Test(dataProvider = "clickValidate")
public void linkClickableTests(int index, String pageTitle) {
    listGroupLinks.listGroup.get(index).highlight();
    listGroupLinks.listGroup.get(index).click();
    newWindowTitleCheck(pageTitle);
    listGroupLinks.listGroup.get(index).unhighlight();
}

@Test
public void isValidationTests() {
    listGroupLinks.listGroup.is()
            .size(5);
    listGroupLinks.is()
            .displayed()
            .enabled()
            .core()
            .hasClass("list-group");
    listGroupLinks.listGroup.get(1).is()
            .hasClass(listClass + " active");
    listGroupLinks.listGroup.get(5).is()
            .hasClass(listClass + " disabled");
    assertFalse(listGroupLinks.listGroup.get(5).isClickable());
}
```

```html
<div class="list-group mb-3" id="list-group-links">
    <a href="https://github.com/jdi-docs"
       class="list-group-item list-group-item-action active" target="_blank">
        JDI Docs
    </a>
    <a href="https://github.com/jdi-testing" class="list-group-item list-group-item-action"
       target="_blank">JDI - testing tool</a>
    <a href="https://jdi-testing.github.io/jdi-light/index.html"
       class="list-group-item list-group-item-action" target="_blank">JDI website</a>
    <a href="https://getbootstrap.com/docs/4.3/components/list-group/#links-and-buttons"
       class="list-group-item list-group-item-action" target="_blank">Bootstrap</a>
    <a href="https://github.com/jdi-docs"
       class="list-group-item list-group-item-action disabled" tabindex="-1"
       aria-disabled="true" target="_blank">JDI Docs</a>
</div>
```



|Method | Description | Return Type
--- | --- | ---
**assertThat()** | Assert action | TextAssert
**click()** | Click the button | void
**get()** | Select button by index | action
**getText()** | Get button text | String
**is()** | Assert action | TextAssert

<br>

[Java test examples](https://github.com/jdi-testing/jdi-light/blob/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/composite/section/listGroup/LinksTests.java)
<br>

Button group is represented by Section class in Java:

[Section](https://jdi-docs.github.io/jdi-light/#section)

<br>

##### Buttons

***[List group links and buttons](https://getbootstrap.com/docs/4.3/components/list-group/#links-and-buttons)***

List Group is located in the following classes:

- __Java__: _com.epam.jdi.light.ui.bootstrap.elements.complex.ListGroup_


![List group buttons example](../../images/bootstrap/list-group-buttons.png)

Here is an example with provided Bootstrap v4.3 code:

```java 
@UI("#list-group-buttons") public static ListGroupButtons listGroupButtons;
// @FindBy(css = "#list-group-buttons") public static ListGroupButtons listGroupButtons;

public class ListGroupButtons extends Section {
    @UI("button") public ListGroup listGroup;
}

@Test
public void isValidationTests() {
    listGroupButtons.listGroup.is()
            .size(5);
    listGroupButtons.is()
            .displayed()
            .enabled()
            .core()
            .hasClass("list-group");
    listGroupButtons.listGroup.get(1).is()
            .hasClass(listClass + " active");
    listGroupButtons.listGroup.get(5).is()
            .disabled();
}

@Test(dataProvider = "clickValidate")
public void buttonClickableTests(int index, String text) {
    listGroupButtons.listGroup.get(index).highlight();
    listGroupButtons.listGroup.get(index).click();
    validateAlert(is(text));
    listGroupButtons.listGroup.get(index).unhighlight();
}
```

```html
<div class="list-group mb-3" id="list-group-buttons">
    <button type="button" class="list-group-item list-group-item-action active"
            onclick="alert('Cras justo odio');">Cras justo odio
    </button>
    <button type="button" class="list-group-item list-group-item-action"
            onclick="alert('Dapibus ac facilisis in');">Dapibus ac facilisis in
    </button>
    <button type="button" class="list-group-item list-group-item-action"
            onclick="alert('Morbi leo risus');">Morbi leo risus
    </button>
    <button type="button" class="list-group-item list-group-item-action"
            onclick="alert('Porta ac consectetur ac');">Porta ac consectetur ac
    </button>
    <button type="button" class="list-group-item list-group-item-action"
            onclick="alert('Vestibulum at eros');" disabled>Vestibulum at eros
    </button>
</div>
```



|Method | Description | Return Type
--- | --- | ---
**assertThat()** | Assert action | TextAssert
**click()** | Click the button | void
**get()** | Select button by index | action
**getText()** | Get button text | String
**is()** | Assert action | TextAssert

<br>

[Java test examples](https://github.com/jdi-testing/jdi-light/blob/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/composite/section/listGroup/Buttons.java)
<br>

Button group is represented by Section class in Java:

[Section](https://jdi-docs.github.io/jdi-light/#section)

<br>

##### Flush

***[List group flush](https://getbootstrap.com/docs/4.3/components/list-group/#flush)***

List Group is located in the following classes:

- __Java__: _com.epam.jdi.light.ui.bootstrap.elements.complex.ListGroup_


![List group flush example](../../images/bootstrap/list-group-flush.png)

Here is an example with provided Bootstrap v4.3 code:

```java 
@UI("#list-group-flush") public static ListGroupFlush listGroupFlush;
// @FindBy(css = "#list-group-flush") public static ListGroupFlush listGroupFlush;

public class ListGroupFlush extends Section {
    @UI("li") public ListGroup listGroup;
}

@Test(dataProvider = "listData")
public void listGroupTests(int num, String text) {
    listGroupFlush.listGroup.get(num).is()
            .text(text)
            .css("font-size", is("14px"));
}

@Test
public void initTests() {
    listGroupFlush.listGroup.is().size(5);
    listGroupFlush.is()
            .displayed()
            .enabled()
            .core()
            .hasClass("list-group list-group-flush");
}
```

```html  
<div class="html-left">
    <ul class="list-group list-group-flush mb-3" id="list-group-flush">
        <li class="list-group-item">Cras justo odio</li>
        <li class="list-group-item">Dapibus ac facilisis in</li>
        <li class="list-group-item">Morbi leo risus</li>
        <li class="list-group-item">Porta ac consectetur ac</li>
        <li class="list-group-item">Vestibulum at eros</li>
    </ul>
</div>
```



|Method | Description | Return Type
--- | --- | ---
**assertThat()** | Assert action | TextAssert
**get()** | Select button by index | action
**getText()** | Get button text | String
**is()** | Assert action | TextAssert

<br>

[Java test examples](https://github.com/jdi-testing/jdi-light/blob/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/composite/section/listGroup/FlushTests.java)
<br>

Button group is represented by Section class in Java:

[Section](https://jdi-docs.github.io/jdi-light/#section)

<br>

##### Horizontal

***[List group horizontal](https://getbootstrap.com/docs/4.3/components/list-group/#horizontal)***

List Group is located in the following classes:

- __Java__: _com.epam.jdi.light.ui.bootstrap.elements.complex.ListGroup_


![List group horizontal example](../../images/bootstrap/list-group-horizontal.png)

Here is an example with provided Bootstrap v4.3 code:

```java 
@UI("#list-group-horizontal") public static ListGroupHorizontal listGroupHorizontal;
// @FindBy(css = "#list-group-horizontal") public static ListGroupHorizontal listGroupHorizontal;

public class ListGroupHorizontal extends Section {
    @UI("li") public ListGroup listGroup;
}

@Test
public void initTests() {
    listGroupHorizontal.listGroup.is()
            .size(3);
}

@Test(dataProvider = "listData")
public void listGroupTests(int num, String text) {
    listGroupHorizontal.listGroup.get(num).is()
            .text(text)
            .css("font-size", is("14px"));
}
```

```html
<ul class="list-group list-group-horizontal mb-3" id="list-group-horizontal">
    <li class="list-group-item">Cras justo odio</li>
    <li class="list-group-item">Dapibus ac facilisis in</li>
    <li class="list-group-item">Morbi leo risus</li>
</ul>
```



|Method | Description | Return Type
--- | --- | ---
**assertThat()** | Assert action | TextAssert
**get()** | Select button by index | action
**getText()** | Get button text | String
**is()** | Assert action | TextAssert

<br>

[Java test examples](https://github.com/jdi-testing/jdi-light/blob/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/composite/section/listGroup/Horizontal.java)
<br>

Button group is represented by Section class in Java:

[Section](https://jdi-docs.github.io/jdi-light/#section)

<br>

##### With Badges

***[List group with badges](https://getbootstrap.com/docs/4.3/components/list-group/#with-badges)***

List Group is located in the following classes:

- __Java__: _com.epam.jdi.light.ui.bootstrap.elements.complex.ListGroup_


![List group with badges example](../../images/bootstrap/list-group-badges.png)

Here is an example with provided Bootstrap v4.3 code:

```java 
@UI("#list-group-with-badges") public static ListGroupWithBadges listGroupWithBadges;
// @FindBy(css = "#list-group-with-badges") public static ListGroupWithBadges listGroupWithBadges;

public class ListGroupWithBadges extends Section {
    @UI("li") public ListGroup listGroup;
    @UI("li span") public ListGroup badge;
}

@Test
public void initTests() {
    listGroupWithBadges.listGroup.is()
            .size(3);
    listGroupWithBadges.badge.is()
            .size(3);
}

@Test(dataProvider = "listData")
public void listGroupTests(int num, String text) {
    listGroupWithBadges.listGroup.get(num).is()
            .text(containsString(text))
            .css("font-size", is("14px"))
            .hasClass("list-group-item d-flex justify-content-between align-items-center");
}
```

```html
<ul class="list-group mb-3" id="list-group-with-badges">
    <li class="list-group-item d-flex justify-content-between align-items-center">
        Cras justo odio
        <span class="badge badge-primary badge-pill">14</span>
    </li>
    <li class="list-group-item d-flex justify-content-between align-items-center">
        Dapibus ac facilisis in
        <span class="badge badge-primary badge-pill">2</span>
    </li>
    <li class="list-group-item d-flex justify-content-between align-items-center">
        Morbi leo risus
        <span class="badge badge-primary badge-pill">1</span>
    </li>
</ul>
```



|Method | Description | Return Type
--- | --- | ---
**assertThat()** | Assert action | TextAssert
**get()** | Select button by index | action
**getText()** | Get button text | String
**is()** | Assert action | TextAssert

<br>

[Java test examples](https://github.com/jdi-testing/jdi-light/blob/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/composite/section/listGroup/WithBadgesTests.java)
<br>

Button group is represented by Section class in Java:

[Section](https://jdi-docs.github.io/jdi-light/#section)

<br>

##### Custom Content

***[List group custom content](https://getbootstrap.com/docs/4.3/components/list-group/#custom-content)***

List Group is located in the following classes:

- __Java__: _com.epam.jdi.light.ui.bootstrap.elements.complex.ListGroup_


![List group custom content example](../../images/bootstrap/list-group-custom.png)

Here is an example with provided Bootstrap v4.3 code:

```java 
@UI("#list-group-custom-content") public static ListGroupCustomContent listGroupCustomContent;
// @FindBy(css = "#list-group-custom-content") public static ListGroupCustomContent listGroupCustomContent;

public class ListGroupCustomContent extends Section {
    @UI("a") public ListGroup listGroup;
    @UI("a div h5") public ListGroup header;
    @UI("a div small") public ListGroup dateText;
    @UI("a p") public ListGroup mainText;
    @UI("small.footer") public ListGroup footer;
    @UI("a div") public ListGroup container;
}

@Test
 public void isValidationTests() {
     listGroupCustomContent.listGroup.is()
             .size(3);
     listGroupCustomContent.container.is()
             .size(3);
}

@Test(dataProvider = "clickValidate")
public void linkClickableTests(int index, String pageTitle) {
    listGroupCustomContent.listGroup.get(index).highlight();
    listGroupCustomContent.listGroup.get(index).click();
    newWindowTitleCheck(pageTitle);
    listGroupCustomContent.listGroup.get(index).unhighlight();
}
```

```html
<div class="list-group mb-3" id="list-group-custom-content">
    <a href="https://jdi-testing.github.io/jdi-light/index.html"
       class="list-group-item list-group-item-action active" target="_blank">
        <div class="d-flex w-100 justify-content-between">
            <h5 class="mb-1">List group item heading one</h5>
            <small>3 days ago</small>
        </div>
        <p class="mb-1">Some simple text for first section of custom list group.</p>
        <small class="footer">JDI website</small>
    </a>
    <a href="https://github.com/jdi-testing" class="list-group-item list-group-item-action"
       target="_blank">
        <div class="d-flex w-100 justify-content-between">
            <h5 class="mb-1">List group item heading two</h5>
            <small class="text-muted">3 days ago</small>
        </div>
        <p class="mb-1">Some simple text for second section of custom list group.</p>
        <small class="text-muted footer">JDI - testing tool</small>
    </a>
    <a href="https://github.com/jdi-docs" class="list-group-item list-group-item-action"
       target="_blank">
        <div class="d-flex w-100 justify-content-between">
            <h5 class="mb-1">List group item heading three</h5>
            <small class="text-muted">3 days ago</small>
        </div>
        <p class="mb-1">Some simple text for third section of custom list group.</p>
        <small class="text-muted footer">JDI Docs</small>
    </a>
</div>
```



|Method | Description | Return Type
--- | --- | ---
**assertThat()** | Assert action | TextAssert
**click()** | Click the button | void
**get()** | Select button by index | action
**getText()** | Get button text | String
**is()** | Assert action | TextAssert
**select()** | Select button | void
**selected()** | Radio button is selected | TextAssert

<br>

[Java test examples](https://github.com/jdi-testing/jdi-light/blob/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/composite/section/listGroup/CustomContentTests.java)
<br>

Button group is represented by Section class in Java:

[Section](https://jdi-docs.github.io/jdi-light/#section)

<br>

#### Toast
<a style="font-weight:bold" href="https://getbootstrap.com/docs/4.3/components/toasts/" target="_blank">Toast</a> - Toasts are lightweight notifications designed to mimic the push notifications.
<br />
__Options for toasts:__
<br />
- _Animation<br/>_
- _Autohide <br/>_
- _Delay <br/>_
  <br/>
  __Events for toasts:__
  <br>
- _show.bs.toast_ - this event fires immediately when the show instance method is called.<br/>
- _shown.bs.toast_ - this event is fired when the toast has been made visible to the user<br/>
- _hide.bs.toast_ - this event is fired immediately when the hide instance method has been called.<br/>
- _hidden.bs.toast_ - this event is fired when the toast has finished being hidden from the user<br/>
  <br />

<a style="font-weight:bold" href="https://getbootstrap.com/docs/4.3/components/toasts/#basic" target="_blank">**Simple Toast**</a>
<br />

![Simple toast example](../../images/bootstrap/toast.png)

Here is an example with provided Bootstrap v4.3 code:

```java 
//@FindBy(id="simpleToast")
@UI("#simpleToast") public static Toast simpleToast; 

@Test
public void simpleToastValidationTest() {
    simpleToastButton.click();
    simpleToast.is().displayed();
    simpleToast.headerText.is().text(toastHeaderText);
    simpleToast.body.is().text(toastBodyText);
}

```

```html
<div class="toast" role="alert" data-animation="false" aria-live="assertive"
     aria-atomic="true" id="simpleToast">
    <div class="toast-header">
        <img src="images/range-circle.png" class="rounded mr-2" alt="...">
        <strong class="mr-auto">Bootstrap</strong>
        <small class="text-muted">11 mins ago</small>
        <button type="button" class="ml-2 mb-1 close" data-dismiss="toast"
                aria-label="Close">
            <span aria-hidden="true">&times;</span>
        </button>
    </div>
    <div class="toast-body">
        Hello, world! This is a toast message.
    </div>
</div>
```

<br>

<a style="font-weight:bold" href="https://getbootstrap.com/docs/4.3/components/toasts/#translucent" target="_blank">**Translucent Toast**</a>


![Translucent toast example](../../images/bootstrap/toast_center.png)

Here is an example with provided Bootstrap v4.3 code:

```java 
//@FindBy(id="translucentToast")
@UI("#translucentToast") public static Toast translucentToast; 

@Test
public void translucentToastValidationTest() {
    translucentToastButton.click();
    translucentToast.is().displayed();
    translucentToast.headerText.is().text(toastHeaderText);
    translucentToast.body.is().text(toastBodyText);
}

```

```html
<div aria-live="polite" aria-atomic="true"
     style="min-height: 200px;background-color: grey;">
    <div class="toast" role="alert" data-animation="false" aria-live="assertive"
         aria-atomic="true" id="translucentToast">
        <div class="toast-header">
            <img src="images/range-circle.png" class="rounded mr-2" alt="...">
            <strong class="mr-auto">Bootstrap</strong>
            <small class="text-muted">11 mins ago</small>
            <button type="button" class="ml-2 mb-1 close" data-dismiss="toast"
                    aria-label="Close">
                <span aria-hidden="true">&times;</span>
            </button>
        </div>
        <div class="toast-body">
            Hello, world! This is a toast message.
        </div>
    </div>
</div>
```

<a style="font-weight:bold" href="https://getbootstrap.com/docs/4.3/components/toasts/#stacking" target="_blank">**Stacking**</a>

When you have multiple toasts, we default to vertically stacking them in a readable manner

![Toast stack example](../../images/bootstrap/stack_of_toast.png)

Here is an example with provided Bootstrap v4.3 code:

```java 
//@FindBy(id="firstMultipleToast")
@UI("#firstMultipleToast") public static Toast firstStackToast; 
//@FindBy(id="secondMultipleToast")
@UI("#secondMultipleToast") public static Toast secondStackToast; 

@Test
public void stackOfToastsValidationTest() {
    stackOfToastsButton.click();
    firstStackToast.is().displayed();
    secondStackToast.is().displayed();
    firstStackToast.headerText.is().text(toastHeaderText);
    firstStackToast.body.is().text(stackToastBodyText);
    secondStackToast.headerText.is().text(toastHeaderText);
    secondStackToast.body.is().text(secondStackToastBodyText);
}

```

```html
<div aria-live="polite" aria-atomic="true"
     style="min-height: 200px;background-color: grey;">
    <div class="toast several" role="alert" aria-live="assertive" id="firstMultipleToast"
         aria-atomic="true">
        <div class="toast-header">
            <img src="images/range-circle.png" class="rounded mr-2" alt="...">
            <strong class="mr-auto">Bootstrap</strong>
            <small class="text-muted">just now</small>
            <button type="button" class="ml-2 mb-1 close" data-dismiss="toast"
                    aria-label="Close">
                <span aria-hidden="true">&times;</span>
            </button>
        </div>
        <div class="toast-body">
            See? Just like this.
        </div>
    </div>
    <div class="toast several" role="alert" aria-live="assertive" id="secondMultipleToast"
         aria-atomic="true">
        <div class="toast-header">
            <img src="images/range-circle.png" class="rounded mr-2" alt="...">
            <strong class="mr-auto">Bootstrap</strong>
            <small class="text-muted">2 seconds ago</small>
            <button type="button" class="ml-2 mb-1 close" data-dismiss="toast"
                    aria-label="Close">
                <span aria-hidden="true">&times;</span>
            </button>
        </div>
        <div class="toast-body">
            Heads up, toasts will stack automatically
        </div>
    </div>
</div>
```


<a style="font-weight:bold" href="https://getbootstrap.com/docs/4.3/components/toasts/#stacking" target="_blank">**Placement**</a>

Place toasts with custom CSS as you need them. The top right is often used for notifications, as is the top middle.
<br /><br />
Example with top right align:

![Toast top right example](../../images/bootstrap/toast_align.png)

Here is an example with provided Bootstrap v4.3 code:

```java 
//@FindBy(id="toastRightTop")
@UI("#toastRightTop") public static Toast toastWithTopAlign; 

@Test
public void toastWithTopAlignValidationTest() {
    toastWithTopAlignButton.click();
    toastWithTopAlign.is().displayed();
    toastWithTopAlign.headerText.is().text(toastHeaderText);
    toastWithTopAlign.body.is().text(toastBodyText);
    toastWithTopAlign.closeButton.click();
    toastWithTopAlign.base().waitSec(1);
    toastWithTopAlign.is().hidden();
}

```

```html
<div aria-live="polite" aria-atomic="true"
     style="position: relative; min-height: 200px;background-color: grey;">
    <div class="toast" id="toastRightTop" style="position: absolute; top: 0; right: 0;"
         data-autohide="false">
        <div class="toast-header">
            <img src="images/range-circle.png" class="rounded mr-2" alt="...">
            <strong class="mr-auto">Bootstrap</strong>
            <small>11 mins ago</small>
            <button type="button" class="ml-2 mb-1 close" data-dismiss="toast"
                    aria-label="Close">
                <span aria-hidden="true">&times;</span>
            </button>
        </div>
        <div class="toast-body">
            Hello, world! This is a toast message.
        </div>
    </div>
</div>
```

Example with top right align stack of toasts:

![Toast top right stack example](../../images/bootstrap/stack_top_html.png)

Here is an example with provided Bootstrap v4.3 code:

```java  
//@FindBy(id="firstStackToast")
@UI("#firstStackToast") public static Toast firstTopAlignStackToast; 
//@FindBy(id="secondStackToast")
@UI("#secondStackToast") public static Toast secondTopAlignStackToast; 

@Test
 public void stackOfTopAlignToastsValidationTest() {
    stackOfToastsWithTopAlignButton.click();
    firstTopAlignStackToast.headerText.is().text(toastHeaderText);
    firstTopAlignStackToast.body.is().text(stackToastBodyText);
    secondTopAlignStackToast.headerText.is().text(toastHeaderText);
    secondTopAlignStackToast.body.is().text(secondStackToastBodyText);
    firstTopAlignStackToast.is().displayed();
    secondTopAlignStackToast.is().displayed();
}

``` 

```html
<div aria-live="polite" aria-atomic="true"
     style="position: relative; min-height: 200px; background-color: grey;">
    <!-- Position it -->
    <div style="position: absolute; top: 0; right: 0;">

        <!-- Then put toasts within -->
        <div class="toast severalWithPosition" role="alert" aria-live="assertive"
             id="firstStackToast" aria-atomic="true">
            <div class="toast-header">
                <img src="images/range-circle.png" class="rounded mr-2" alt="...">
                <strong class="mr-auto">Bootstrap</strong>
                <small class="text-muted">just now</small>
                <button type="button" class="ml-2 mb-1 close" data-dismiss="toast"
                        aria-label="Close">
                    <span aria-hidden="true">&times;</span>
                </button>
            </div>
            <div class="toast-body">
                See? Just like this.
            </div>
        </div>

        <div class="toast severalWithPosition" role="alert" aria-live="assertive"
             id="secondStackToast" aria-atomic="true">
            <div class="toast-header">
                <img src="images/range-circle.png" class="rounded mr-2" alt="...">
                <strong class="mr-auto">Bootstrap</strong>
                <small class="text-muted">2 seconds ago</small>
                <button type="button" class="ml-2 mb-1 close" data-dismiss="toast"
                        aria-label="Close">
                    <span aria-hidden="true">&times;</span>
                </button>
            </div>
            <div class="toast-body">
                Heads up, toasts will stack automatically
            </div>
        </div>
    </div>
</div>
```

Example with center align toast:

![Toast top right stack example](../../images/bootstrap/toast_center.png)

Here is an example with provided Bootstrap v4.3 code:

```java 
//@FindBy(id="toastCenterTop")
@UI("#toastCenterTop") public static Toast toastWithCenterAlign; 
//@FindBy(id="toastRightTop")
@UI("#toastRightTop") public static Toast toastWithTopAlign; 

@Test
public void toastWithCenterAlignValidationTest() {
    toastWithCenterAlignButton.click();
    toastWithCenterAlign.is().displayed();
    toastWithCenterAlign.headerText.is().text(toastHeaderText);
    toastWithCenterAlign.body.is().text(toastBodyText);
    toastWithCenterAlign.closeButton.click();
    toastWithCenterAlign.base().waitSec(1);
    toastWithCenterAlign.is().hidden();
}

```

```html
<div aria-live="polite" aria-atomic="true"
     class="d-flex justify-content-center align-items-center"
     style="min-height: 200px;background-color: grey;">

    <!-- Then put toasts within -->
    <div class="toast" role="alert" id="toastCenterTop" aria-live="assertive"
         aria-atomic="true" data-delay="3000">
        <div class="toast-header">
            <img src="images/range-circle.png" class="rounded mr-2" alt="...">
            <strong class="mr-auto">Bootstrap</strong>
            <small>11 mins ago</small>
            <button type="button" class="ml-2 mb-1 close" data-dismiss="toast"
                    aria-label="Close">
                <span aria-hidden="true">&times;</span>
            </button>
        </div>
        <div class="toast-body">
            Hello, world! This is a toast message.
        </div>
    </div>
</div>
```

Available methods in Java JDI Light:

|Method | Description | Return Type
--- | --- | ---
**assertThat()** |	Assert action |	TextAssert
**close()** |	Close toast |	void
**getText()** |	Get toast text |	String
**getTitle()** |	Get toast title |	String
**is()** |	Assert action |	TextAssert
**isDisplayed()** | Show\wait that toast element displayed on the screen | Boolean

[Toast test examples](https://github.com/jdi-testing/jdi-light/tree/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/common/)

<br>

#### Pagination

##### Overview

***[Pagination overview](https://getbootstrap.com/docs/4.3/components/pagination/#overview)***

Pagination is located in the following classes:

- __Java__: _com.epam.jdi.light.ui.bootstrap.elements.complex.Pagination_


![Pagination overview example](../../images/bootstrap/pagination-overview-example.png)

Here is an example with provided Bootstrap v4.3 code:

```java 
// @FindBy(css = "#pagination-overview") public static PaginationOverview paginationOverview;
@UI("#pagination-overview") public static PaginationOverview paginationOverview;

public class PaginationOverview extends Section {
    @UI("li") public Pagination paginationItems; // @FindBy(css = "li") public Pagination paginationItems;
}

@Test
 public void isValidationTests() {
     paginationOverview.paginationItems.is()
             .size(5);
     paginationOverview.is()
             .core()
             .hasClass("pagination");
 }

 @Test(dataProvider = "listData")
 public void linkTextTests(int index, String linkText) {
     paginationOverview.paginationItems.get(index).is()
             .displayed()
             .enabled()
             .css("font-size", is("14px"))
             .hasClass("page-item")
             .text(is(linkText));
 }

 @Test(dataProvider = "listPageTitles")
 public void linkClickableTests(int index, String pageTitle) {
     paginationOverview.paginationItems.get(index).hover();
     paginationOverview.paginationItems.get(index).highlight();
     paginationOverview.paginationItems.get(index).click();
     newWindowTitleCheck(pageTitle);
     paginationOverview.paginationItems.get(index).unhighlight();
 }
```

```html
<nav aria-label="Page navigation example">
    <ul class="pagination" id="pagination-overview">
        <li class="page-item"><a class="page-link" href="https://github.com/jdi-docs"
                                 target="_blank">Previous</a></li>
        <li class="page-item"><a class="page-link" href="https://github.com/jdi-testing"
                                 target="_blank">1</a></li>
        <li class="page-item"><a class="page-link"
                                 href="https://jdi-testing.github.io/jdi-light/index.html"
                                 target="_blank">2</a></li>
        <li class="page-item"><a class="page-link" href="https://getbootstrap.com"
                                 target="_blank">3</a></li>
        <li class="page-item"><a class="page-link"
                                 href="https://jdi-docs.github.io/jdi-light/"
                                 target="_blank">Next</a></li>
    </ul>
</nav>
```



|Method | Description | Return Type
--- | --- | ---
**assertThat()** | Assert action | TextAssert
**click()** | Click the element | void
**get()** | Select button by index | UIElement
**getText()** | Get button text | String
**highlight()** | Highlight element | void
**hover()** | Hover on the element | void
**is()** | Assert action | TextAssert
**unhighlight()** | Unhighlight element | void

<br>

[Java test examples](https://github.com/jdi-testing/jdi-light/blob/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/composite/section/pagination/OverviewTests.java)
<br>

Button group is represented by Section class in Java:

[Section](https://jdi-docs.github.io/jdi-light/#section)

<br>

##### Working with icons

***[Pagination working with icons](https://getbootstrap.com/docs/4.3/components/pagination/#working-with-icons)***

Pagination is located in the following classes:

- __Java__: _com.epam.jdi.light.ui.bootstrap.elements.complex.Pagination_


![Pagination working with icons example](../../images/bootstrap/pagination-icons-example.png)

Here is an example with provided Bootstrap v4.3 code:

```java 
// @FindBy(css = "#pagination-icons") public static PaginationIcons paginationIcons;
@UI("#pagination-icons") public static PaginationIcons paginationIcons;

public class PaginationIcons extends Section {
    @UI("li") public Pagination paginationItems; // @FindBy(css = "li") public Pagination paginationItems;
}

@Test
public void isValidationTests() {
    paginationIcons.paginationItems.is()
            .size(5);
    paginationIcons.is()
            .core()
            .hasClass("pagination");
}

@Test(dataProvider = "listPageTitles")
public void linkClickableTests(int index, String pageTitle) {
    paginationIcons.paginationItems.get(index).hover();
    paginationIcons.paginationItems.get(index).highlight();
    paginationIcons.paginationItems.get(index).click();
    newWindowTitleCheck(pageTitle);
    paginationIcons.paginationItems.get(index).unhighlight();
}
```

```html
<nav aria-label="Page navigation example">
    <ul class="pagination" id="pagination-icons">
        <li class="page-item">
            <a class="page-link" href="https://github.com/jdi-docs" target="_blank"
               aria-label="Previous">
                <span aria-hidden="true">&laquo;</span>
            </a>
        </li>
        <li class="page-item"><a class="page-link" href="https://github.com/jdi-testing"
                                 target="_blank">1</a></li>
        <li class="page-item"><a class="page-link"
                                 href="https://jdi-testing.github.io/jdi-light/index.html"
                                 target="_blank">2</a></li>
        <li class="page-item"><a class="page-link" href="https://getbootstrap.com"
                                 target="_blank">3</a></li>
        <li class="page-item">
            <a class="page-link" href="https://jdi-docs.github.io/jdi-light/"
               target="_blank" aria-label="Next">
                <span aria-hidden="true">&raquo;</span>
            </a>
        </li>
    </ul>
</nav>
```



|Method | Description | Return Type
--- | --- | ---
**assertThat()** | Assert action | TextAssert
**click()** | Click the element | void
**get()** | Select button by index | UIElement
**getText()** | Get button text | String
**highlight()** | Highlight element | void
**hover()** | Hover on the element | void
**is()** | Assert action | TextAssert
**unhighlight()** | Unhighlight element | void

<br>

[Java test examples](https://github.com/jdi-testing/jdi-light/blob/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/composite/section/pagination/IconsTests.java)
<br>

Button group is represented by Section class in Java:

[Section](https://jdi-docs.github.io/jdi-light/#section)

<br>

##### Disabled and active states

***[Pagination disabled and active states](https://getbootstrap.com/docs/4.3/components/pagination/#disabled-and-active-states)***

Pagination is located in the following classes:

- __Java__: _com.epam.jdi.light.ui.bootstrap.elements.complex.Pagination_


![Pagination disabled and active states example](../../images/bootstrap/pagination-dis-and-active-example.png)

Here is an example with provided Bootstrap v4.3 code:

```java 
// @FindBy(css = "#pagination-states") public static PaginationStates paginationStates;
@UI("#pagination-states") public static PaginationStates paginationStates;

public class PaginationStates extends Section {
    @UI("li") public Pagination paginationItems; // @FindBy(css = "li") public Pagination paginationItems;
}

@Test
public void isValidationTests() {
    paginationStates.paginationItems.is()
            .size(5);
    paginationStates.is()
            .core()
            .hasClass("pagination");
    paginationStates.paginationItems.get(1).is()
            .core()
            .hasClass("disabled");
    paginationStates.paginationItems.get(3).is()
            .core()
            .hasClass("active");
}

@Test(dataProvider = "listPageTitles")
public void linkClickableTests(int index, String pageTitle) {
    paginationStates.paginationItems.get(index).hover();
    paginationStates.paginationItems.get(index).highlight();
    paginationStates.paginationItems.get(index).click();
    newWindowTitleCheck(pageTitle);
    paginationStates.paginationItems.get(index).unhighlight();
}
```

```html
<nav aria-label="disabled-and-active-states">
    <ul class="pagination" id="pagination-states">
        <li class="page-item disabled">
            <a class="page-link" href="https://github.com/jdi-docs" target="_blank"
               tabindex="-1" aria-disabled="true">Previous</a>
        </li>
        <li class="page-item"><a class="page-link" href="https://github.com/jdi-testing"
                                 target="_blank">1</a></li>
        <li class="page-item active" aria-current="page">
            <a class="page-link" href="https://jdi-testing.github.io/jdi-light/index.html"
               target="_blank">2 <span class="sr-only">(current)</span></a>
        </li>
        <li class="page-item"><a class="page-link" href="https://getbootstrap.com"
                                 target="_blank">3</a></li>
        <li class="page-item">
            <a class="page-link" href="https://jdi-docs.github.io/jdi-light/"
               target="_blank">Next</a>
        </li>
    </ul>
</nav>
```



|Method | Description | Return Type
--- | --- | ---
**assertThat()** | Assert action | TextAssert
**click()** | Click the element | void
**get()** | Select button by index | UIElement
**getText()** | Get button text | String
**highlight()** | Highlight element | void
**hover()** | Hover on the element | void
**is()** | Assert action | TextAssert
**unhighlight()** | Unhighlight element | void

<br>

[Java test examples](https://github.com/jdi-testing/jdi-light/blob/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/composite/section/pagination/StatesTests.java)
<br>

Button group is represented by Section class in Java:

[Section](https://jdi-docs.github.io/jdi-light/#section)

<br>

##### Sizing

***[Pagination sizing](https://getbootstrap.com/docs/4.3/components/pagination/#sizing)***

Pagination is located in the following classes:

- __Java__: _com.epam.jdi.light.ui.bootstrap.elements.complex.Pagination_


![Pagination sizing example](../../images/bootstrap/pagination-sizing-example.png)

Here is an example with provided Bootstrap v4.3 code:

```java 
// @FindBy(css = "#pagination-big") public static PaginationSizeBig paginationSizeBig;
// @FindBy(css = "#pagination-small") public static PaginationSizeSmall paginationSizeSmall;
@UI("#pagination-big") public static PaginationSizeBig paginationSizeBig;
@UI("#pagination-small") public static PaginationSizeSmall paginationSizeSmall;

public class PaginationSizeBig extends Section {
    @UI("li") public Pagination paginationItems; // @FindBy(css = "li") public Pagination paginationItems;
    @UI(".page-link") public Pagination paginationItemsText; // @FindBy(css = ".page-link") public Pagination paginationItemsText;
}

public class PaginationSizeSmall extends Section {
    @UI("li") public Pagination paginationItems; // @FindBy(css = "li") public Pagination paginationItems;
    @UI(".page-link") public Pagination paginationItemsText; // @FindBy(css = ".page-link") public Pagination paginationItemsText;
}

@Test
public void isValidationTests() {
    paginationSizeBig.paginationItems.is()
            .size(3);
    paginationSizeBig.is()
            .core()
            .hasClass("pagination pagination-lg");
    paginationSizeSmall.paginationItems.is()
            .size(3);
    paginationSizeSmall.is()
            .core()
            .hasClass("pagination pagination-sm");
}

@Test(dataProvider = "listData")
public void linkTextTests(int index, String linkText) {
    paginationSizeBig.paginationItemsText.get(index).is()
            .core()
            .css("font-size", is("20px"));
    paginationSizeSmall.paginationItemsText.get(index).is()
            .core()
            .css("font-size", is("14px"));
}
```

```html
<nav aria-label="sizing-big">
    <ul class="pagination pagination-lg" id="pagination-big">
        <li class="page-item active" aria-current="page">
            <span class="page-link">1<span class="sr-only">(current)</span></span>
        </li>
        <li class="page-item"><a class="page-link"
                                 href="https://jdi-testing.github.io/jdi-light/index.html"
                                 target="_blank">2</a></li>
        <li class="page-item"><a class="page-link" href="https://getbootstrap.com"
                                 target="_blank">3</a></li>
    </ul>
</nav>

<nav aria-label="sizing-small">
    <ul class="pagination pagination-sm" id="pagination-small">
        <li class="page-item active" aria-current="page">
            <span class="page-link">1<span class="sr-only">(current)</span></span>
        </li>
        <li class="page-item"><a class="page-link"
                                 href="https://jdi-testing.github.io/jdi-light/index.html"
                                 target="_blank">2</a></li>
        <li class="page-item"><a class="page-link" href="https://getbootstrap.com"
                                 target="_blank">3</a></li>
    </ul>
</nav>
```



|Method | Description | Return Type
--- | --- | ---
**assertThat()** | Assert action | TextAssert
**click()** | Click the element | void
**get()** | Select button by index | UIElement
**getText()** | Get button text | String
**highlight()** | Highlight element | void
**hover()** | Hover on the element | void
**is()** | Assert action | TextAssert
**unhighlight()** | Unhighlight element | void

<br>

[Java test examples](https://github.com/jdi-testing/jdi-light/blob/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/composite/section/pagination/SizingTests.java)
<br>

Button group is represented by Section class in Java:

[Section](https://jdi-docs.github.io/jdi-light/#section)

<br>

##### Alignment

***[Pagination alignment](https://getbootstrap.com/docs/4.3/components/pagination/#alignment)***

Pagination is located in the following classes:

- __Java__: _com.epam.jdi.light.ui.bootstrap.elements.complex.Pagination_


![Pagination alignment example](../../images/bootstrap/pagination-alignment-example.png)

Here is an example with provided Bootstrap v4.3 code:

```java 
// @FindBy(css = "#pagination-center") public static PaginationAlignCenter paginationAlignCenter;
// @FindBy(css = "#pagination-end") public static PaginationAlignEnd paginationAlignEnd; 
@UI("#pagination-center") public static PaginationAlignCenter paginationAlignCenter;
@UI("#pagination-end") public static PaginationAlignEnd paginationAlignEnd;

public class PaginationAlignCenter extends Section {
    @UI("li") public Pagination paginationItems; // @FindBy(css = "li") public Pagination paginationItems;
}

public class PaginationAlignEnd extends Section {
    @UI("li") public Pagination paginationItems; // @FindBy(css = "li") public Pagination paginationItems;
}

@Test
public void isValidationTests() {
    paginationAlignCenter.paginationItems.is()
            .size(5);
    paginationAlignCenter.is()
            .core()
            .hasClass("pagination justify-content-center");
    paginationAlignCenter.paginationItems.get(1).is()
            .core()
            .hasClass("disabled");
    paginationAlignEnd.paginationItems.is()
            .size(5);
    paginationAlignEnd.is()
            .core()
            .hasClass("pagination justify-content-end");
    paginationAlignEnd.paginationItems.get(1).is()
            .core()
            .hasClass("disabled");
}

@Test(dataProvider = "listPageTitles")
public void linkClickableCenterTests(int index, String pageTitle) {
    paginationAlignCenter.paginationItems.get(index).hover();
    paginationAlignCenter.paginationItems.get(index).highlight();
    paginationAlignCenter.paginationItems.get(index).click();
    newWindowTitleCheck(pageTitle);
    paginationAlignCenter.paginationItems.get(index).unhighlight();
}
```

```html
<nav aria-label="Page navigation example">
    <ul class="pagination justify-content-center" id="pagination-center">
        <li class="page-item disabled">
            <a class="page-link" href="https://github.com/jdi-docs" target="_blank"
               tabindex="-1" aria-disabled="true">Previous</a>
        </li>
        <li class="page-item"><a class="page-link" href="https://github.com/jdi-testing"
                                 target="_blank">1</a></li>
        <li class="page-item"><a class="page-link"
                                 href="https://jdi-testing.github.io/jdi-light/index.html"
                                 target="_blank">2</a></li>
        <li class="page-item"><a class="page-link" href="https://getbootstrap.com"
                                 target="_blank">3</a></li>
        <li class="page-item">
            <a class="page-link" href="https://jdi-docs.github.io/jdi-light/"
               target="_blank">Next</a>
        </li>
    </ul>
</nav>
<nav aria-label="Page navigation example">
    <ul class="pagination justify-content-end" id="pagination-end">
        <li class="page-item disabled">
            <a class="page-link" href="https://github.com/jdi-docs" target="_blank"
               tabindex="-1" aria-disabled="true">Previous</a>
        </li>
        <li class="page-item"><a class="page-link" href="https://github.com/jdi-testing"
                                 target="_blank">1</a></li>
        <li class="page-item"><a class="page-link"
                                 href="https://jdi-testing.github.io/jdi-light/index.html"
                                 target="_blank">2</a></li>
        <li class="page-item"><a class="page-link" href="https://getbootstrap.com"
                                 target="_blank">3</a></li>
        <li class="page-item">
            <a class="page-link" href="https://jdi-docs.github.io/jdi-light/"
               target="_blank">Next</a>
        </li>
    </ul>
</nav>
```



|Method | Description | Return Type
--- | --- | ---
**assertThat()** | Assert action | TextAssert
**click()** | Click the element | void
**get()** | Select button by index | UIElement
**getText()** | Get button text | String
**highlight()** | Highlight element | void
**hover()** | Hover on the element | void
**is()** | Assert action | TextAssert
**unhighlight()** | Unhighlight element | void

<br>

[Java test examples](https://github.com/jdi-testing/jdi-light/blob/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/composite/section/pagination/AlignTests.java)
<br>

Button group is represented by Section class in Java:

[Section](https://jdi-docs.github.io/jdi-light/#section)

<br>


#### Input group
##### Basic Example
**<a style="font-weight:bold" href="https://getbootstrap.com/docs/4.3/components/input-group/#basic-example" target="_blank">Input group</a>** – Place one add-on or button on either side of an input. You may also place one on both sides of an input.
<br />

```java 

    //@FindBy(css = "#input-group-basic-example1")
   @UI("#input-group-basic-example1") public static InputGroupInputWithText inputGroupBasicExample1;

   public class InputGroupInputWithText extends Section{
       @UI(".input-group-text") public Text text;
       @UI(".form-control") public TextField input;
   }

   @Test(priority = 1)
   public void setTextTestExample1() {
        inputGroupBasicExample1.input.setText(textExample1);
        inputGroupBasicExample1.input.is().text(is(textExample1));
   }

```
**1.Input group example - Input + left span**

<img src="images/bootstrap/input-group-base-example1.png" alt="Input group example1" height="50%" width="50%">

Here is an example with provided Bootstrap v4.3 code:


```html
<div class="input-group mb-3" id="input-group-basic-example1">
    <div class="input-group-prepend">
        <span class="input-group-text" id="basic-addon">@</span>
    </div>
    <input type="text" class="form-control" placeholder="Username" aria-label="Username"
           aria-describedby="basic-addon1">
</div>
```

```java 

    //@FindBy(css = "#input-group-basic-example2")
   @UI("#input-group-basic-example2") public static InputGroupInputWithText inputGroupBasicExample2;

   public class InputGroupInputWithText extends Section{
       @UI(".input-group-text") public Text text;
       @UI(".form-control") public TextField input;
   }

    @Test(priority = 4)
    public void checkAddonConsistTextTestExample2() {
       inputGroupBasicExample2.text.is().text(containsString(partOfAddonExample2));
    }

```
<br /><br /><br /><br /><br /><br />
**2.Input group example - Input + right span**

<img src="images/bootstrap/input-group-base-example2.png" alt="Input group example1" height="50%" width="50%">

Here is an example with provided Bootstrap v4.3 code:


```html
<div class="input-group mb-3" id="input-group-basic-example2">
    <input type="text" class="form-control" placeholder="Recipient's username"
           aria-label="Recipient's username" aria-describedby="basic-addon2">
    <div class="input-group-append">
        <span class="input-group-text" id="basic-addon2">@example.com</span>
    </div>
</div>
``` 

```java 

    //@FindBy(css = "#input-group-basic-example3")
   @UI("#input-group-basic-example3") public static InputGroupInputWithLabelAndText inputGroupBasicExample3;

   public class InputGroupInputWithLabelAndText extends Section{
       @UI(".input-group-text") public Text text;
       @UI("#basic-url") public TextField input;
   }

   @Test(priority = 6)
   public void checkLabelExample3() {
       assertEquals(inputGroupBasicExample3.input.core().label().getText(), labelExample3);
   }

```
<br /><br /><br /><br />
**3.Input group example - Input + label + left span**

<img src="images/bootstrap/input-group-base-example3.png" alt="Input group example1" height="50%" width="50%">


Here is an example with provided Bootstrap v4.3 code:

```html
<div class="input-group mb-3" id="input-group-basic-example3">
    <div class="input-group-prepend">
        <span class="input-group-text" id="basic-addon3">https://example.com/users/</span>
    </div>
    <input type="text" class="form-control" id="basic-url" aria-describedby="basic-addon3">
</div>
```


```java 

   //@FindBy(css = "#input-group-basic-example4")
  @UI("#input-group-basic-example4") public static InputGroupInputWithTwoText inputGroupBasicExample4;

  public class InputGroupInputWithTwoText extends Section{
      @UI(".input-group-prepend .input-group-text") public Text text_pretend;
      @UI(".input-group-append .input-group-text") public Text text_append;
      @UI(".form-control") public TextField input;
  }

  @Test(priority = 7)
  public void checkAddonsExample4() {
      inputGroupBasicExample4.text_append.is().enabled();
      inputGroupBasicExample4.text_append.is().text(is(addonAppendExample4));
      inputGroupBasicExample4.text_pretend.is().enabled();
      inputGroupBasicExample4.text_pretend.is().text(is(addonPretendExample4));
  }

``` 
<br /><br />
**4.Input group example - Input + left and right span**

<img src="images/bootstrap/input-group-base-example4.png" alt="Input group example4" height="50%" width="50%">

Here is an example with provided Bootstrap v4.3 code:

```html
<div class="input-group mb-3" id="input-group-basic-example4">
    <div class="input-group-prepend">
        <span class="input-group-text">$</span>
    </div>
    <input type="text" class="form-control" aria-label="Amount (to the nearest dollar)">
    <div class="input-group-append">
        <span class="input-group-text">.00</span>
    </div>
</div>
```

```java 

   //@FindBy(css = "#input-group-basic-example5")
  @UI("#input-group-basic-example5") public static InputGroupTextareaWithText inputGroupBasicExample5;

  public class InputGroupTextareaWithText extends Section{
      @UI(".input-group-text") public Text text;
      @UI(".form-control") public TextArea area;
  }

  @Test(priority = 9)
  public void getLinesTestExample5() {
      inputGroupBasicExample5.area.setLines(linesTextArea);
      assertEquals(inputGroupBasicExample5.area.getLines(), asList(linesTextArea));
  }

```

<br /><br /><br /><br/><br />
**5.Input group example - Input + textarea**

<img src="images/bootstrap/input-group-base-example5.png" alt="Input group example5" height="50%" width="50%">

Here is an example with provided Bootstrap v4.3 code:

```html
<div class="input-group" id="input-group-basic-example5">
    <div class="input-group-prepend">
        <span class="input-group-text">With textarea</span>
    </div>
    <textarea class="form-control" aria-label="With textarea"></textarea>
</div>
```

Input group are represented by Section class in Java:

[Section](https://jdi-docs.github.io/jdi-light/#section)

Inner elements of input group can be represented by following classes:
 <ul>
  <li> [Text](https://jdi-docs.github.io/jdi-light/#text) </li>

  <li> [TextField](https://jdi-docs.github.io/jdi-light/#textfield) </li> 

  <li> [TextArea](https://jdi-docs.github.io/jdi-light/#textarea) </li>


 <li>  [See more elements](https://jdi-docs.github.io/jdi-light/#html5-common-elements) </li> 
 </ul>

[Bootstrap test example ](https://github.com/jdi-testing/jdi-light/tree/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/composite/section/inputGroup)

##### Sizing
<a style="font-weight:bold" href="https://getbootstrap.com/docs/4.3/components/input-group/#sizing" target="_blank">Sizing</a> – Add the relative form sizing classes to the .input-group itself and contents within will automatically resize—no need for repeating the form control size classes on each element.
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>

```java 
    @UI("#input-group-default") public static InputGroupSizing inputGroupDefaultSizing;
    @UI("#input-group-small") public static InputGroupSizing inputGroupSmallSizing;
    @UI("#input-group-large") public static InputGroupSizing inputGroupLargeSizing;
    //@FindBy(css = "#input-group-default")
    //@FindBy(css = "#input-group-small")
    //@FindBy(css = "#input-group-large")

    @Test
    public void getTextFromSizingTest() {
        assertEquals(inputGroupDefaultSizing.input.getText(), text);
        assertEquals(inputGroupSmallSizing.input.getText(), text);
        assertEquals(inputGroupLargeSizing.input.getText(), text);
    }

    @Test
    public void clearSizingTest() {
        inputGroupDefaultSizing.input.clear();
        assertEquals(inputGroupDefaultSizing.input.getText(), "");
        inputGroupSmallSizing.input.clear();
        assertEquals(inputGroupDefaultSizing.input.getText(), "");
        inputGroupLargeSizing.input.clear();
        assertEquals(inputGroupDefaultSizing.input.getText(), "");
    }
```


**Sizing on the individual input group elements isn’t supported.**
![Sizing](../../images/bootstrap/sizing.png)

Here is an example with provided Bootstrap v4.3 code:

```html
<div class="input-group input-group-sm mb-3" id="input-group-small">
    <div class="input-group-prepend">
        <span class="input-group-text" id="inputGroup-sizing-sm">Small</span>
    </div>
    <input type="text" class="form-control" aria-label="Sizing example input"
           aria-describedby="inputGroup-sizing-sm">
</div>

<div class="input-group mb-3" id="input-group-default">
    <div class="input-group-prepend">
        <span class="input-group-text" id="inputGroup-sizing-default">Default</span>
    </div>
    <input type="text" class="form-control" aria-label="Sizing example input"
           aria-describedby="inputGroup-sizing-default">
</div>

<div class="input-group input-group-lg" id="input-group-large">
    <div class="input-group-prepend">
        <span class="input-group-text" id="inputGroup-sizing-lg">Large</span>
    </div>
    <input type="text" class="form-control" aria-label="Sizing example input"
           aria-describedby="inputGroup-sizing-lg">
</div>
```

And here are methods available in Java:

|Method / Property | Description | Return Type
--- | --- | ---
**assertThat()** | property that returns object for work with assertions| TextAssert
**clear()** | clears the text field | void
**focus()** | places cursor within the text field | void
**getText()** | returns text from the text field  | String
**getValue()** | returns text from the text field| String
**is()** | property that returns object for work with assertions| TextAssert
**setText(String value)** | adds text to the field | void


##### Wrapping
```java 
   public static UIElement inputGroupWrap,inputGroupNowrap;//@FindBy(css = "#input-group-wrap")

   @Test
   public void checkWrapping() {
       assertFalse(inputGroupWrap.hasClass("flex-nowrap"));
       inputGroupWrap.assertThat().core().css("flex-wrap", "wrap");
   }
 
   @Test
   public void checkNoWrapping() {
       assertTrue(inputGroupNowrap.hasClass("flex-nowrap"));
       inputGroupNowrap.assertThat().core().css("flex-wrap", "nowrap");
   } 
```


**<a style="font-weight:bold" href="https://getbootstrap.com/docs/4.3/components/input-group/#wrapping" target="_blank">Wrapping</a>** – Input groups wrap by default via flex-wrap: wrap in order to accommodate custom form field validation within an input group. You may disable this with .flex-nowrap.

![Wrapping](../../images/bootstrap/wrapping.png)

Here is an example with provided Bootstrap v4.3 code:

```html
<div class="input-group flex-nowrap" id="input-group-nowrap">
    <div class="input-group-prepend">
        <span class="input-group-text" id="addon-wrapping1">@</span>
    </div>
    <input type="text" class="form-control" placeholder="Input group with nowrap"
           aria-label="Username" aria-describedby="addon-wrapping">
</div>
```

Wrapping property can be checked by using following class:

- _com.epam.jdi.light.elements.common.UIElement_

<a  href="https://github.com/jdi-testing/jdi-light/blob/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/composite/section/inputGroup/InputGroupWrapping.java" target="_blank">Bootstrap test example wrapping</a>


##### Checkboxes and radios

<a style="font-weight:bold" href="https://getbootstrap.com/docs/4.3/components/input-group/#checkboxes-and-radios" target="_blank">Checkboxes and radios</a> – Place any checkbox or radio option within an input group’s addon instead of text.

__Example with radio__

```java 
  @UI("#input-group-radio") public static InputGroupInputWithRadio inputGroupRadio;// @FindBy(css = "#input-group-radio")

  public class InputGroupInputWithRadio extends Section{
      @Css("[type=\"radio\"]") public RadioButtons radio;
      @Css(".form-control") public TextField input;
  }
  
  @Test
  public void getSizeRadioButtons() {
      inputGroupRadio.radio.is().size(1);
  }

   @Test
   public void inputTest() {
       inputGroupRadio.input.input(new_text);
       inputGroupRadio.input.assertThat().text(is(new_text));
   }

 
```

![radio](../../images/bootstrap/input-group-radio.png)

Here is an example with provided Bootstrap v4.3 code:

```html
<div class="input-group" id="input-group-radio">
    <div class="input-group-prepend">
        <div class="input-group-text">
            <input type="radio" name="radio-button" id="radio-button"
                   aria-label="Radio button for following text input">
        </div>
    </div>
    <input type="text" class="form-control" aria-label="Text input with radio button">
</div>
```

This input group example is represented by the following classes in Java:

+ [Section](https://jdi-docs.github.io/jdi-light/#section)
+ [RadioButtons](https://jdi-docs.github.io/jdi-light/#radiobuttons)

  <a  href="https://github.com/jdi-testing/jdi-light/blob/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/composite/section/inputGroup/InputGroupRadioTests.java" target="_blank">Bootstrap test example with radio</a>

<br />

```java 
 @UI("#input-group-checkbox") public static InputGroupInputWithCheckBox inputGroupCheckBox;// @FindBy(css = "#input-group-checkbox")

 public class InputGroupInputWithCheckBox extends Section{
     @Css("[type=\"checkbox\"]") public Checkbox checkbox;
     @Css(".form-control") public TextField input;
 }
  
 @Test
 public void checkCheckboxTest() {
     inputGroupCheckBox.checkbox.check();
     inputGroupCheckBox.checkbox.isSelected();
 }

   @Test
   public void inputTest() {
       inputGroupRadio.input.input(new_text);
       inputGroupRadio.input.assertThat().text(is(new_text));
   }

 
```
__Example with checkbox__

![Checkbox](../../images/bootstrap/input-group-checkbox.png)

Here is an example with provided Bootstrap v4.3 code:

```html
<div class="input-group mb-3" id="input-group-checkbox">
    <div class="input-group-prepend">
        <div class="input-group-text">
            <input type="checkbox" aria-label="Checkbox for following text input">
        </div>
    </div>
    <input type="text" class="form-control" aria-label="Text input with checkbox">
</div>
```

This input group example is represented by the following classes in Java:

+ [Section](https://jdi-docs.github.io/jdi-light/#section)
+ [CheckBox](https://jdi-docs.github.io/jdi-light/#checkbox)

  <a href="https://github.com/jdi-testing/jdi-light/blob/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/composite/section/inputGroup/InputGroupCheckboxesTests.java" target="_blank">Bootstrap test example with checkbox</a>

<br /><br /><br /><br /><br />

##### Multiple inputs
<a style="font-weight:bold" href="https://getbootstrap.com/docs/4.3/components/input-group/" target="_blank">Multiple inputs</a> – While multiple inputs are supported visually, validation styles are only available for input groups with a single input.

![Multiple inputs](../../images/bootstrap/multiple_inputs.png)

```java 
//FindBy(css = "#multiple-inputs"")
@UI("#multiple-inputs") public static MultipleInputs multipleInputs;

@Test
public void getTextTest() {
     int index = 1;

     String name = multipleInputs.getText(index);
     assertEquals(name, inputData.get(index));

     String surname = multipleInputs.getText("#mi-i-2");
     assertEquals(surname, inputData.get(2));

     String text = multipleInputs.getText();
     assertEquals(text, inputData.get(1));
}

@Test
public void getTextAllTest() {
    assertEquals(multipleInputs.getAllTexts(), inputDataList);
}

@Test
public void setValueTest() {
    multipleInputs.clearAll();

    String value = inputData.get(1);
    multipleInputs.setValue(value);
    multipleInputs.is().text(value, 1);

    int index = 2;
    String name = inputData.get(index);
    multipleInputs.setValue(name, index);
    multipleInputs.is().text(name, index);

    String locator = "#mi-i-2";
    String surname = inputData.get(2);
    multipleInputs.clear(locator);
    multipleInputs.setValue(surname, locator);
    multipleInputs.is().text(surname, locator);
}

@Test
public void setAllValuesTest() {
    multipleInputs.clearAll();
    multipleInputs.setAllValues(inputDataList);
    multipleInputs.is().texts(inputDataList);
}
```

Here is an example with provided Bootstrap v4.3 code:

```html
<div class="input-group" id="multiple-inputs">
    <div class="input-group-prepend">
        <span class="input-group-text">First and last name</span>
    </div>
    <input type="text" aria-label="First name" class="form-control" id="mi-i-1">
    <input type="text" aria-label="Last name" class="form-control" id="mi-i-2">
</div>
```

And here are methods available in Java:

|Method | Description | Return Type
--- | --- | ---
**assertThat()**| Property that returns object for work with assertions | MultipleInputsAssert
**clear()**| Clear first input within element | void
**clear(String locator)**| Clear input within element with *locator* | void
**clear(int index)**| Clear input within element with *index* | void
**clearAll()**| Clear all inputs within element | void
**focus()**| Focus on first input within element | void
**focus(String locator)**| Focus on input within element with *locator* | void
**focus(int index)**| Focus on input within element with *index* | void
**getAllText()**| Return texts for all inputs within element | List\<String>
**getAllValue()**| Return values for all inputs within element | List\<String>
**getText()**| Return text for first input within element | String
**getText(String locator)**| Return text for input within element with *locator* | String
**getText(int index)**| Return text for input within element with *index* | String
**getValue()**| Return value for first input within element | String
**getValue(String locator)**| Return value for input within element with *locator* | String
**getValue(int index)**| Return value for input within element with *index* | String
**input(String value)**| Set text for first input within element | void
**input(String value, String locator)**| Set text for input within element with *locator* | void
**input(String value, int index)**| Set text for input within element with *index* | void
**inputAll()**| Set texts for all inputs within element | void
**is()**| Property that returns object for work with assertions | MultipleInputsAssert
**placeholder()**| Return placeholder from first input within element | String
**placeholder(String locator)**| Return placeholder from input within element with *locator* | String
**placeholder(int index)**| Return placeholder from input within element with *index* | String
**placeholderAll()**| Return placeholders for all inputs within element | List\<String>
**sendKeys(String value)**| Send text to first input within element | void
**sendKeys(String value, String locator)**| Send text to input within element with *locator* | void
**sendKeys(String value, int index)**| Send text to input within element with *index* | void
**sendKeysAll(List\<String> values)**| Send texts to all inputs within element | void
**setAllValue(List\<String> values)**| Set values for all inputs within element | void
**setValue(String value)**| Set value for first input within element | void
**setValue(String value, String locator)**| Set value for input within element with *locator* | void
**setValue(String value, int index)**| Set value for input within element with *index* | void

<a href="https://github.com/jdi-testing/jdi-light/blob/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/complex/MultipleInputsTests.java" target="_blank">Bootstrap test example with multiple inputs</a>


##### Multiple addons
<a style="font-weight:bold" href="https://getbootstrap.com/docs/4.3/components/input-group/#multiple-addons" target="_blank">Multiple addons</a> are supported and can be mixed with checkbox and radio input versions.

![Multiple addons](../../images/bootstrap/multiple_addons.png)

```java 
 @UI("#multiple-addons-1")  public static InputGroupMultipleAddonsUpper multipleAddonUpper; //@FindBy(css = "#multiple-addons-1")
 @UI("#multiple-addons-2")  public static InputGroupMultipleAddonsLower multipleAddonLower; //@FindBy(css = "#multiple-addons-2")
 
 public class InputGroupMultipleAddonsUpper extends Section {
     @UI("#left-sign") public Label firstLabel; //@FindBy(css = "#left-sign")
     @UI("#left-nil") public Label secondLabel; //@FindBy(css = "#left-nil")
     @UI(".form-control") public TextField textField; //@FindBy(css = ".form-control")
 }

 @Test(dataProvider = "InputGroupMultipleAddonsLabels")
 public void assertTextFromValueTest(Label multipleAddonsLabel, String labelValue) {
    multipleAddonsLabel.is().text(labelValue);
 }
 
 @Test(dataProvider = "InputGroupMultipleAddonsLabels")
 public void isValidationTest(Label multipleAddonsLabel, String labelValue) {
     multipleAddonsLabel.is()
        .displayed()
        .core()
        .hasClass("input-group-text")
        .text(labelValue);
 }
 
 @Test(dataProvider = "InputGroupMultipleAddonsTextFields")
 public void inputTest(TextField textField) {
     textField.input(text);
     textField.assertThat().text(is(text));
 }
 
 @Test(dataProvider = "InputGroupMultipleAddonsTextFields")
 public void textFieldTests(TextField textField) {
     textField.setText(text);
     textField.is().text(text);
     textField.is().text(containsString(partOfText));
     textField.clear();
     textField.is().text(emptyText);
 }
```
Here is an example with provided Bootstrap v4.3 code:

```html
<div class="input-group mb-3" id="multiple-addons-1">
    <div class="input-group-prepend">
        <span class="input-group-text" id="left-sign">$</span>
        <span class="input-group-text" id="left-nil">0.00</span>
    </div>
    <input type="text" class="form-control"
           aria-label="Dollar amount (with dot and two decimal places)">
</div>

<div class="input-group mb-3" id="multiple-addons-2">
    <input type="text" class="form-control"
           aria-label="Dollar amount (with dot and two decimal places)">
    <div class="input-group-append">
        <span class="input-group-text" id="right-sign">$</span>
        <span class="input-group-text" id="right-nil">0.00</span>
    </div>
</div>
```


Multiple input is represented by Section class in Java:

[Section](https://jdi-docs.github.io/jdi-light/#section)

Inner elements of multiple input can be represented by the following classes:

+ [TextField](https://jdi-docs.github.io/jdi-light/#textfield)
+ [Label](https://jdi-docs.github.io/jdi-light/#label)

<a href="https://github.com/jdi-testing/jdi-light/blob/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/composite/section/inputGroup/InputGroupMultipleAddonsTests.java" target="_blank">Bootstrap test example with multiple addons</a>












<br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /> <br />
##### Button addons

**[Button addons](https://getbootstrap.com/docs/4.3/components/input-group/#button-addons)** – Multiple buttons have no detailed information on Bootstrap website


![Button addons](../../images/bootstrap/button_addons.png)

Here is an example with provided Bootstrap v4.3 code:


```java 
//@FindBy(css = "#input-group-button-addon4") public static ButtonAddons inputGroupButtonAddons4;
@UI("#input-group-button-addon1") public static ButtonAddons inputGroupButtonAddons1;
@UI("#input-group-button-addon2") public static ButtonAddons inputGroupButtonAddons2;
@UI("#input-group-button-addon3") public static ButtonAddons inputGroupButtonAddons3;
@UI("#input-group-button-addon4") public static ButtonAddons inputGroupButtonAddons4;

public class ButtonAddons extends Section {
    @UI("button") public Button button;
    @UI("input") public TextField input;
    @UI("button") public ListGroup listButtons;
    @UI("input") public TextField inputField;
}

@Test
public void checkButtonAddon2Test() {
    inputGroupButtonAddons2.input.input(text);
    inputGroupButtonAddons2.button.click();
    inputGroupButtonAddons2.input.input(placeholder_text);
    inputGroupButtonAddons2.input.assertThat().text(placeholder_text);
}

@Test
public void checkButtonAddon4Test() {
    inputGroupButtonAddons4.inputField.input(text);
    inputGroupButtonAddons4.listButtons.get(1).click();
    inputGroupButtonAddons4.inputField.input(placeholder_text);
    inputGroupButtonAddons4.listButtons.get(2).click();
    inputGroupButtonAddons4.inputField.assertThat().text(placeholder_text);
}
```


```html
<div class="input-group mb-3" id="input-group-button-addon1">
    <div class="input-group-prepend">
        <button class="btn btn-outline-secondary" type="button" id="button-addon1">Button
        </button>
    </div>
    <input type="text" class="form-control" placeholder=""
           aria-label="Example text with button addon" aria-describedby="button-addon1">
</div>

<div class="input-group mb-3" id="input-group-button-addon2">
    <input type="text" class="form-control" placeholder="Recipient's username"
           aria-label="Recipient's username" aria-describedby="button-addon2">
    <div class="input-group-append">
        <button class="btn btn-outline-secondary" type="button" id="button-addon2">Button
        </button>
    </div>
</div>

<div class="input-group mb-3" id="input-group-button-addon3">
    <div class="input-group-prepend" id="button-addon3">
        <button class="btn btn-outline-secondary" type="button">Button</button>
        <button class="btn btn-outline-secondary" type="button">Button</button>
    </div>
    <input type="text" class="form-control" placeholder=""
           aria-label="Example text with two button addons"
           aria-describedby="button-addon3">
</div>

<div class="input-group" id="input-group-button-addon4">
    <input type="text" class="form-control" placeholder="Recipient's username"
           aria-label="Recipient's username with two button addons"
           aria-describedby="button-addon4">
    <div class="input-group-append" id="button-addon4">
        <button class="btn btn-outline-secondary" type="button">Button</button>
        <button class="btn btn-outline-secondary" type="button">Button</button>
    </div>
</div>
```

And here are methods available in Java:

|Method | Description | Return Type
--- | --- | ---
**assertThat()** | property that returns object for work with assertions| TextAssert
**clear()** | clears the text field | void
**click()** | click on button | void
**displayed()** | check item is displayed | TextAssert
**enabled()** | check item is enabled | TextAssert
**expand()** | expand dropdown menu | void
**expanded()** | check that dropdown is expanded | TextAssert
**focus()** | places cursor within the text field | void
**getText()** | returns text from the text field  | String
**getValue()** | returns text from the text field| String
**input(String value)** | adds text to the field | void
**is()** | property that returns object for work with assertions| TextAssert
**sendKeys(String value)** | adds text to the field | void
**setText(String value)** | adds text to the field | void

 <br>
Input group are represented by Section class in Java:

[Section](https://jdi-docs.github.io/jdi-light/#section)

Inner elements of input group can be represented by following classes:
 <ul>
  <li> [Text](https://jdi-docs.github.io/jdi-light/#text) </li>

  <li> [TextField](https://jdi-docs.github.io/jdi-light/#textfield) </li> 

  <li> [TextArea](https://jdi-docs.github.io/jdi-light/#textarea) </li>

  <li> [Button](https://jdi-docs.github.io/jdi-light/#button-2) </li>

 <li>  [See more elements](https://jdi-docs.github.io/jdi-light/#html5-common-elements) </li> 
 </ul>
 <br>

<a  href="https://github.com/jdi-testing/jdi-light/blob/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/composite/section/inputGroup/InputGroupButtonAddonsTests.java" target="_blank">Button Addons test example</a>


##### Buttons with dropdowns

**[Buttons with dropdowns](https://getbootstrap.com/docs/4.3/components/input-group/#buttons-with-dropdowns)** – Buttons with dropdowns have no detailed information on Bootstrap website

![Buttons with dropdowns](../../images/bootstrap/buttons_with_dropdowns.png)

Here is an example with provided Bootstrap v4.3 code:

```java 
@UI("#button-with-dropdown") public static ButtonWithDropdown buttonWithDropdown;
// @FindBy(css = "#button-with-dropdown") public static ButtonWithDropdown buttonWithDropdown;

public class ButtonWithDropdown extends Section {
@UI("input") public TextField textInputArea;
@UI("button") public Button dropdownButton;
@JDropdown(expand = ".input-group-prepend",
        value = ".dropdown-toggle",
        list = ".dropdown-item")
public Dropdown dropdownMenu;
}

@Test
public void dropdownMenuTests() {
    buttonWithDropdown.dropdownMenu.expand();
    buttonWithDropdown.dropdownMenu.is().expanded();
    buttonWithDropdown.dropdownMenu.is().size(4);
    buttonWithDropdown.dropdownMenu.list().get(0).is().text(action);
}

@Test
public void textInputAreaTests() {
    buttonWithDropdown.textInputArea.sendKeys(testText);
    buttonWithDropdown.textInputArea.is().text(testText);
    buttonWithDropdown.textInputArea.clear();
    buttonWithDropdown.textInputArea.is().text("");
}

@Test
public void dropdownButtonTests() {
    buttonWithDropdown.dropdownButton.is().displayed();
    buttonWithDropdown.dropdownButton.is().enabled();
    buttonWithDropdown.dropdownButton.is().text(dropdownButton);
}
```

```html
<div class="input-group mb-3" id="button-with-dropdown">
    <div class="input-group-prepend">
        <button class="btn btn-outline-secondary dropdown-toggle" type="button"
                data-toggle="dropdown" aria-haspopup="true" aria-expanded="false">Dropdown
        </button>
        <div class="dropdown-menu">
            <a class="dropdown-item" href="#">Action</a>
            <a class="dropdown-item" href="#">Another action</a>
            <a class="dropdown-item" href="#">Something else here</a>
            <div role="separator" class="dropdown-divider"></div>
            <a class="dropdown-item" href="#">Separated link</a>
        </div>
    </div>
    <input type="text" class="form-control" aria-label="Text input with dropdown button">
</div>
```

And here are methods available in Java:

|Method | Description | Return Type
--- | --- | ---
**assertThat()** | property that returns object for work with assertions| TextAssert
**clear()** | clears the text field | void
**click()** | click on button | void
**displayed()** | check item is displayed | TextAssert
**enabled()** | check item is enabled | TextAssert
**expand()** | expand dropdown menu | void
**expanded()** | check that dropdown is expanded | TextAssert
**focus()** | places cursor within the text field | void
**getText()** | returns text from the text field  | String
**getValue()** | returns text from the text field| String
**is()** | property that returns object for work with assertions| TextAssert
**sendKeys(String value)** | adds text to the field | void
**setText(String value)** | adds text to the field | void

 <br>
Input group are represented by Section class in Java:

[Section](https://jdi-docs.github.io/jdi-light/#section)

Inner elements of input group can be represented by following classes:
 <ul>
  <li> [Text](https://jdi-docs.github.io/jdi-light/#text) </li>

  <li> [TextField](https://jdi-docs.github.io/jdi-light/#textfield) </li> 

  <li> [TextArea](https://jdi-docs.github.io/jdi-light/#textarea) </li>

  <li> [Dropdown](https://jdi-docs.github.io/jdi-light/#dropdown-2) </li>

 <li>  [See more elements](https://jdi-docs.github.io/jdi-light/#html5-common-elements) </li> 
 </ul>
 <br>


[Buttons with dropdowns test examples](https://github.com/jdi-testing/jdi-light/blob/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/composite/section/inputGroup/InputGroupButtonWithDropdownTests.java) <br>
<br>

##### Segmented buttons
**[Segmented buttons](https://getbootstrap.com/docs/4.3/components/input-group/#segmented-buttons)** – Segmented buttons have no detailed information on Bootstrap website

![Segmented buttons](../../images/bootstrap/segmented_buttons.png)

Here is an example with provided Bootstrap v4.3 code:

```java 
@UI("#segmented-button") public static SegmentedButton segmentedButton;
// @FindBy(css = "#segmented-button") public static SegmentedButton segmentedButton;

public class SegmentedButton extends Section {
    @UI("#Segmented-action-button") public Button actionButton;
    @UI("input") public TextField textInputArea;
    @JDropdown(expand = ".dropdown-toggle",
            value = ".sr-only",
            list = ".dropdown-item")
    public Dropdown dropdownMenu;
}

@Test
public void textInputAreaTests() {
    segmentedButton.textInputArea.is()
            .displayed()
            .enabled();
    segmentedButton.textInputArea.sendKeys(testText);
    segmentedButton.textInputArea.is().text(testText);
    segmentedButton.textInputArea.clear();
    segmentedButton.textInputArea.is().text("");
}

@Test
public void dropdownMenuTests() {
    segmentedButton.dropdownMenu.expand();
    segmentedButton.dropdownMenu.is().expanded();
    segmentedButton.dropdownMenu.is().size(4);
    segmentedButton.dropdownMenu.list().get(0).is().text(action);
    segmentedButton.dropdownMenu.select(action);
    newWindowTitleCheck();
}

@Test
public void actionButtonTests() {
    segmentedButton.actionButton.is().displayed();
    segmentedButton.actionButton.is().enabled();
    segmentedButton.actionButton.is().text(action);
    segmentedButton.actionButton.click();
    validateAlert(is(actionButtonClickAlert));
}
```

```html
<div class="input-group mb-3" id="segmented-button">
    <div class="input-group-prepend">
        <button type="button" class="btn btn-outline-secondary" id="Segmented-action-button"
                onclick="alert('Action Button Alert');">Action
        </button>
        <button type="button"
                class="btn btn-outline-secondary dropdown-toggle dropdown-toggle-split"
                data-toggle="dropdown" aria-haspopup="true" aria-expanded="false">
            <span class="sr-only">Toggle Dropdown</span>
        </button>
        <div class="dropdown-menu">
            <a class="dropdown-item"
               href="https://jdi-testing.github.io/jdi-light/index.html"
               target="_blank">Action</a>
            <a class="dropdown-item"
               href="https://jdi-testing.github.io/jdi-light/index.html" target="_blank">Another
                action</a>
            <a class="dropdown-item"
               href="https://jdi-testing.github.io/jdi-light/index.html" target="_blank">Something
                else here</a>
            <div role="separator" class="dropdown-divider"></div>
            <a class="dropdown-item"
               href="https://jdi-testing.github.io/jdi-light/index.html" target="_blank">Separated
                link</a>
        </div>
    </div>
    <input type="text" class="form-control"
           aria-label="Text input with segmented dropdown button">
</div>
```

And here are methods available in Java:

|Method | Description | Return Type
--- | --- | ---
**assertThat()** | property that returns object for work with assertions| TextAssert
**clear()** | clears the text field | void
**click()** | click on button | void
**displayed()** | check item is displayed | TextAssert
**enabled()** | check item is enabled | TextAssert
**expand()** | expand dropdown menu | void
**expanded()** | check that dropdown is expanded | TextAssert
**focus()** | places cursor within the text field | void
**getText()** | returns text from the text field  | String
**getValue()** | returns text from the text field| String
**is()** | property that returns object for work with assertions| TextAssert
**sendKeys(String value)** | adds text to the field | void
**setText(String value)** | adds text to the field | void

 <br>
Input group are represented by Section class in Java:

[Section](https://jdi-docs.github.io/jdi-light/#section)

Inner elements of input group can be represented by following classes:
 <ul>
  <li> [Text](https://jdi-docs.github.io/jdi-light/#text) </li>

  <li> [TextField](https://jdi-docs.github.io/jdi-light/#textfield) </li> 

  <li> [TextArea](https://jdi-docs.github.io/jdi-light/#textarea) </li>

  <li> [Dropdown](https://jdi-docs.github.io/jdi-light/#dropdown-2) </li>

 <li>  [See more elements](https://jdi-docs.github.io/jdi-light/#html5-common-elements) </li> 
 </ul>
 <br>


[Segmented buttons test examples](https://github.com/jdi-testing/jdi-light/blob/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/composite/section/inputGroup/InputGroupSegmentedButtonTests.java) <br>


##### Custom select
**[Custom select](https://getbootstrap.com/docs/4.3/components/input-group/#custom-select)** – Input groups include support for custom selects and text field. Browser default versions of these are not supported.

![Custom select](../../images/bootstrap/custom_select.png)

Here is an example with provided Bootstrap v4.3 code:

```java 
@UI("#custom-select-01") public static CustomSelect customSelect;
// @FindBy(css = "#custom-select-01") public static CustomSelect customSelect;

public class CustomSelect extends Section {
    @UI(".input-group-prepend") public Text optionText;
    @UI("#inputGroupSelect01") public Selector selector;
}

@Test
   public void isValidationOptionsSectionTests() {
       customSelect.optionText.is().text(optionText);
}

@Test
public void selectorByIndexTests() {
    customSelect.selector.is().selected(selectChoose);
    customSelect.selector.select(2);
    customSelect.selector.is().selected(selectOne);
    customSelect.selector.select(1);
    customSelect.selector.is().selected(selectChoose);
}

@Test(priority = 1)
public void selectorByValueTests() {
    customSelect.selector.select(selectOne);
    customSelect.selector.is().selected(selectOne);
    customSelect.selector.select(selectTwo);
    customSelect.selector.is().selected(selectTwo);
}

@Test
public void selectorIsValidationTests() {
    customSelect.selector.is().displayed()
            .enabled();
    customSelect.selector.is().size(4);
}
```

```html
<div class="input-group mb-3" id="custom-select-01">
    <div class="input-group-prepend">
        <label class="input-group-text" for="inputGroupSelect01">Options</label>
    </div>
    <select class="custom-select" id="inputGroupSelect01">
        <option selected>Choose...</option>
        <option value="1">One</option>
        <option value="2">Two</option>
        <option value="3">Three</option>
    </select>
</div>

<div class="input-group mb-3" id="custom-select-02">
    <select class="custom-select" id="inputGroupSelect02">
        <option selected>Choose...</option>
        <option value="1">One</option>
        <option value="2">Two</option>
        <option value="3">Three</option>
    </select>
    <div class="input-group-append">
        <label class="input-group-text" for="inputGroupSelect02">Options</label>
    </div>
</div>
```

<br><br><br><br><br><br><br><br><br><br>
**[Custom select with button](https://getbootstrap.com/docs/4.3/components/input-group/#custom-select)** – Input groups include support for custom selects and button. Browser default versions of these are not supported.

![Custom select with button](../../images/bootstrap/custom-select-with-button.png)

Here is an example with provided Bootstrap v4.3 code:

```java 
@UI("#custom-select-button-01") public static CustomSelectWithButton customSelectWithButton;
// @FindBy(css = "#custom-select-button-01") public static CustomSelect customSelect;

public class CustomSelectWithButton extends Section {
    @UI("#inputGroupSelect03") public Selector selector;
    @UI("button") public Button button;
}

@Test
public void buttonTests() {
    customSelectWithButton.button.is().displayed();
    customSelectWithButton.button.is().enabled();
    customSelectWithButton.button.is().text(buttonText);
    customSelectWithButton.button.hover();
    customSelectWithButton.button.click();
    validateAlert(is(buttonClickAlert));
}

@Test
public void selectorByIndexTests() {
    customSelectWithButton.selector.is().selected(selectChoose);
    customSelectWithButton.selector.select(2);
    customSelectWithButton.selector.is().selected(selectOne);
    customSelectWithButton.selector.select(3);
    customSelectWithButton.selector.is().selected(selectTwo);
}

@Test(priority = 1)
public void selectorByValueTests() {
    customSelectWithButton.selector.select(selectTwo);
    customSelectWithButton.selector.is().selected(selectTwo);
    customSelectWithButton.selector.select(selectThree);
    customSelectWithButton.selector.is().selected(selectThree);
}

@Test
public void selectorIsValidationTests() {
    customSelectWithButton.selector.is().displayed()
            .enabled();
    customSelectWithButton.selector.is().size(4);
}
```

```html
<div class="input-group mb-3" id="custom-select-button-01">
    <div class="input-group-prepend">
        <button class="btn btn-outline-secondary" type="button"
                onclick="alert('Button clicked, thank you!');">Button
        </button>
    </div>
    <select class="custom-select" id="inputGroupSelect03"
            aria-label="Example select with button addon">
        <option selected>Choose...</option>
        <option value="1">One</option>
        <option value="2">Two</option>
        <option value="3">Three</option>
    </select>
</div>

<div class="input-group mb-3" id="custom-select-button-02">
    <select class="custom-select" id="inputGroupSelect04"
            aria-label="Example select with button addon">
        <option selected>Choose...</option>
        <option value="1">One</option>
        <option value="2">Two</option>
        <option value="3">Three</option>
    </select>
    <div class="input-group-append">
        <button class="btn btn-outline-secondary" type="button"
                onclick="alert('Button clicked, thank you!');">Button
        </button>
    </div>
</div>
```



And here are methods available in Java:

|Method | Description | Return Type
--- | --- | ---
**assertThat()** | property that returns object for work with assertions| TextAssert
**clear()** | clears the text field | void
**click()** | click on button | void
**displayed()** | check item is displayed | TextAssert
**enabled()** | check item is enabled | TextAssert
**focus()** | places cursor within the text field | void
**getText()** | returns text from the text field  | String
**getValue()** | returns text from the text field| String
**is()** | property that returns object for work with assertions| TextAssert
**select(int value)** | choose item by index | void
**selected** | returns text from the selected item | TextAssert
**sendKeys(String value)** | adds text to the field | void
**setText(String value)** | adds text to the field | void


  <br>
 Input group are represented by Section class in Java:

[Section](https://jdi-docs.github.io/jdi-light/#section)

Inner elements of input group can be represented by following classes:
  <ul>
   <li> [Text](https://jdi-docs.github.io/jdi-light/#text) </li>

  <li>  [See more elements](https://jdi-docs.github.io/jdi-light/#html5-common-elements) </li> 
  </ul>
  <br>

[Custom select test examples](https://github.com/jdi-testing/jdi-light/blob/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/composite/section/inputGroup/InputGroupCustomSelect.java) <br>
[Custom select with button test examples](https://github.com/jdi-testing/jdi-light/blob/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/composite/section/inputGroup/InputGroupCustomSelectWithButton.java)

##### Custom file input

[Custom file input](https://getbootstrap.com/docs/4.3/components/input-group/#custom-file-input) – Input groups include support for custom selects and custom file inputs. Browser default versions of these are not supported.

![Custom file input](../../images/bootstrap/custom_file_input.png)

```java 
public class InputGroupCustomUploadFile extends Section {
    
@UI("label[for='upload-file-c']") //@FindBy(css ="label[for='upload-file-c']")
public Label labelInputFile;
@UI("input#upload-file-c") //@FindBy(css ="input#upload-file-c")
public FileInput fileInput; 
@UI("button") //@FindBy(css = "button") 
public Button btnSubmit;

public void clickSubmitButton() {
        btnSubmit.click();
    }
}

public class InputGroupCustomFileInput extends Section {
@UI("label[for='file-input-c']") //@FindBy(css ="label[for='file-input-c']") 
public Label labelInputFile;
@UI("input#file-input-c")   //@FindBy(css ="input#file-input-c")
public FileInput fileInput;
}
 
@BeforeMethod
public void before() {
States.shouldBeLoggedIn();
bsPage.shouldBeOpened();
inputGroupCustomFileInput.fileInput.core().
                        setup(jdiB -> jdiB.setSearchRule(ANY_ELEMENT));
inputGroupCustomFileInput.fileInput.core().setClickArea(ACTION_CLICK);
inputGroupCustomUploadFile.fileInput.core().
                        setup(jdiB -> jdiB.setSearchRule(ANY_ELEMENT));
inputGroupCustomUploadFile.fileInput.core().setClickArea(ACTION_CLICK);
}

@Test
public void uploadTest() {
clearInput();
inputGroupCustomFileInput.fileInput.uploadFile(mergePath(PROJECT_PATH,
                "/src/test/resources/general.xml"));
inputGroupCustomFileInput.fileInput.is().text(containsString("general.xml"));
inputGroupCustomFileInput.fileInput.is().value(containsString("general.xml"));
}

@Test
public void buttonUploadFileTest() {
inputGroupCustomUploadFile.btnSubmit.is().text("Submit");
inputGroupCustomUploadFile.clickSubmitButton();
validateAlert(is(alertMessage));
}
```

```html
<div class="input-group mb-3" id="file-input">
    <div class="custom-file">
        <input type="file" class="custom-file-input" id="file-input-c">
        <label class="custom-file-label" for="file-input-c">Choose file</label>
    </div>
</div>
<div class="input-group" id="upload-file">
    <div class="custom-file">
        <input type="file" class="custom-file-input" id="upload-file-c">
        <label class="custom-file-label" for="upload-file-c">Choose file</label>
    </div>
    <div class="input-group-append">
         <button class="btn btn-outline-secondary" type="button" 
                    onclick="alert('Button clicked, thank you!');">Submit</button>
    </div>
</div> 
```

And here are methods available in Java:

|Method | Description | Return Type
--- | --- | ---
**assertThat()** | property that returns object for work with assertions | UIAssert
**click()** | click on element | void
**getValue()** | Get file name | String
**hover()** | hover on element | void
**is()** | property that returns object for work with assertions | UIAssert
**label()**| Get label | Label
**setValue(String value)** | set file path to input | void
**text()** | returns text of input field | String
**uploadFile(String path)** | set file path to input | void
**uploadFileRobot(String path, long mSecDelay)** | set file path to input | void
<br>

The Custom file input is defined as a section and uses additional web elements: Button, FileInput and Label.

They are located in the following Java classes:

- com.epam.jdi.light.ui.html.common.Button

- com.epam.jdi.light.elements.common;

- com.epam.jdi.light.ui.bootstrap.elements.common;


[Bootstrap test examples](https://github.com/jdi-testing/jdi-light/blob/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/composite/section/inputgroup/InputGroupCustomFileInputTests.java)


#### Card

[Cards](https://getbootstrap.com/docs/4.3/components/card/) in Bootstrap provide a flexible and extensible
content container with multiple variants and options.

##### Card Example

[Card Example](https://getbootstrap.com/docs/4.3/components/card/#example) - basic card with mixed content and a
fixed width. Cards have no fixed width to start, so they’ll naturally fill the full width of its parent element.
This is easily customized with our various sizing options.

![Card Example](../../images/bootstrap/simplecard.png)

Here is an example with provided Bootstrap v4.3 code:

```java 
// @FindBy(css = "#card-example") 
@UI("#card-example")
public static CardExample cardExample;

public class CardExample extends Card {
    @UI(".card-title")
    public Text title;
    @UI(".card-text")
    public Text text;
    @UI(".btn")
    public Button button;
    @UI("#bs-card-example-image")
    public Image image;
}   

@Test
public void isValidationTest() {
    cardExample.image.is().src(is(imageSrc));
    cardExample.image.is().alt(is(imageAlt));
    cardExample.image.unhighlight();
    cardExample.image.assertThat().width(is(86));
    cardExample.image.assertThat().height(is(137));
    cardExample.title.is().text(is(titleText));
    cardExample.text.is().text(is(mainText));
    cardExample.button.is().displayed()
            .and().text(is(buttonText))
            .core()
            .attr("type", "submit")
            .tag(is("button"));
    cardExample.button.is().enabled();
}

@Test
public void clickTest() {
    cardExample.button.click();
    Alerts.validateAlert(is(alertText));
}
```

```html 
<div class="card mb-3" id="card-example" style="width: 18rem;">
  <img style="width: 30%; margin: 0 auto;" id="bs-card-example-image"
    src="https://jdi-testing.github.io/jdi-light/images/wolverin.jpg" class="card-img-top" alt="image">
  <div class="card-body">
    <h5 class="card-title">Card title</h5>
    <p class="card-text">Some quick example text to build on the card title and make up
      the bulk of the card's content.</p>
    <button href="#" class="btn btn-primary" onclick="alert('Card Button Clicked!')">
      Click Me!
    </button>
  </div>
</div>
```

Card is represented by Section class in Java:

[Section](https://jdi-docs.github.io/jdi-light/#section)

Inner elements of Card Example represented by the following classes:

- [Text](https://jdi-docs.github.io/jdi-light/#text)
- [Button](https://jdi-docs.github.io/jdi-light/#button)
- [Image](https://jdi-docs.github.io/jdi-light/#image)

Available methods in Java JDI Light:

|Method | Description | Return Type
--- | --- | ---
**alt()** | Assert alt image attribute | ImageAssert
**assertThat()** | Assert action | UIAssert
**getText()**| Returns text | String
**height()** | Assert image height | ImageAssert
**is()** | Assert action | UIAssert
**src()** | Assert image src | ImageAssert
**width()** | Assert image width | ImageAssert

[Bootstrap test examples](https://github.com/jdi-testing/jdi-light/blob/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/composite/section/card/CardExampleTests.java)

##### Card Body

[Card Body](https://getbootstrap.com/docs/4.3/components/card/#body) - the building block of a card is the `.card-body`.
Use it whenever you need a padded section within a card.

![Card Body Example](../../images/bootstrap/cardbody.png)

Here is an example with provided Bootstrap v4.3 code:

```java 
//@FindBy(css = ".card-body")
@UI(".card-body")
public static CardBody cardBody;

public class CardBody extends Card {
    @UI(".card-body")
    public Text text;
}

@Test
public void getBodyTextTest() {
    assertEquals(cardBody.text.getText(), text);
}
```

```html 
<div class="card" id="card-body">
  <div class="card-body">
    This is some text within a card body.
  </div>
</div>
```

Card is represented by Section class in Java:

[Section](https://jdi-docs.github.io/jdi-light/#section)

Inner elements of Card Body represented by the following classes:

[Text](https://jdi-docs.github.io/jdi-light/#text)

Available methods in Java JDI Light:

|Method | Description | Return Type
--- | --- | ---
**assertThat()** | Assert action | UIAssert
**getText()**| Returns text | String
**is()** | Assert action | UIAssert

[Bootstrap test examples](https://github.com/jdi-testing/jdi-light/tree/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/composite/section/card/CardBodyTests.java)

##### Card Titles, Text and Links

[Card Titles, Text and Links](https://getbootstrap.com/docs/4.3/components/card/#titles-text-and-links) - card titles
are used by adding `.card-title` to a `<h*>` tag. In the same way, links are added and placed next to each other
by adding `.card-link` to an `<a>` tag.

Subtitles are used by adding a `.card-subtitle` to a `<h*>` tag. If the `.card-title` and the `.card-subtitle` items
are placed in a `.card-body` item, the card title and subtitle are aligned nicely.

![Card Titles, Text and Links Example](../../images/bootstrap/cardsubslinks.png)

Here is an example with provided Bootstrap v4.3 code:

```java 
// @FindBy(css = "#card-subtitle-link") 
@UI("#card-subtitle-link") 
public static CardWithSubtitlesAndLinks cardWithSubtitlesAndLinks;

public class CardWithSubtitlesAndLinks extends Card {
    @UI(".card-title") public Text title;
    @UI(".card-subtitle") public Text subtitle;
    @UI(".card-text") public Text mainText;
    @UI("#bs-card-2-link1") public Link link1;
    @UI("#bs-card-2-link2") public Link link2;
}

@Test
public void getLink1TextTest() {
    assertEquals(cardWithSubtitlesAndLinks.link1.getText(), link1Text);
}

@Test
public void clickLink1Test() {
    cardWithSubtitlesAndLinks.link1.click();
    ArrayList<String> tabs = new ArrayList<>(WebDriverFactory.getDriver().getWindowHandles());
    WebDriver driver = WebDriverFactory.getDriver();
    driver.switchTo().window(tabs.get(1));
    assertEquals(getUrl(), link1Ref);
    driver.close();
    driver.switchTo().window(tabs.get(0));
}
```

```html 
<div class="card" id="card-subtitle-link" style="width: 18rem;">
  <div class="card-body">
    <h5 class="card-title">Card title</h5>
    <h6 class="card-subtitle mb-2 text-muted">Card subtitle</h6>
    <p class="card-text">Some quick example text to build on the card title and
      make up the bulk of the card's content.</p>
    <a href="https://github.com/jdi-testing/jdi-light" target="_blank" class="card-link" id="bs-card-2-link1">
      JDI Light Github</a>
    <a href="https://jdi-testing.github.io/jdi-light/index.html" target="_blank" class="card-link"
      id="bs-card-2-link2">JDI Website</a>
  </div>
</div>
```

Card is represented by Section class in Java:

[Section](https://jdi-docs.github.io/jdi-light/#section)

Inner elements of Card with Titles and Links represented by the following classes:

- [Text](https://jdi-docs.github.io/jdi-light/#text)
- [Link](https://jdi-docs.github.io/jdi-light/#link)

Available methods in Java JDI Light:

|Method | Description | Return Type
--- | --- | ---
**assertThat()** | Assert action | UIAssert
**getText()**| Returns text | String
**is()** | Assert action | UIAssert
**ref()** | Returns the reference | String
**url()** | Returns the URL | URL

[Bootstrap test examples](https://github.com/jdi-testing/jdi-light/blob/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/composite/section/card/CardWithSubtitlesAndLinksTests.java)

##### Card Images

[Card Images](https://getbootstrap.com/docs/4.3/components/card/#images) are used with `.card-img-top` to place an image
to the top of the card. With `.card-text`, text can be added to the card. Text within `.card-text` can also be styled
with the standard HTML tags.

![Card Images Example](../../images/bootstrap/card-image.png)

Here is an example with provided Bootstrap v4.3 code:

```java 
//@FindBy(css = "#card-image")
@UI("#card-image") 
public static CardImage cardImage;

public class CardImage extends Card {
    @UI(".card-text") public Text text;
    @UI("#bs-card-image") public Image image;
}

@Test
public void getSrcTest() {
    assertEquals(cardImage.image.src(), SRC_ATTR_EXPECTED);
}

@Test
public void getAltTest() {
    assertEquals(cardImage.image.alt(), ALT_ATTR_EXPECTED);
}

@Test
public void imageClassTest() {
     cardImage.image.is().core().hasClass(IMAGE_TOP_CLASS);
     cardImage.image.assertThat().core().hasClass(IMAGE_TOP_CLASS);
}
```

```html 
<div class="card mb-3" id="card-image-caps-1" style="width: 18rem;">
  <img style="width: 30%; margin: 0 auto;" src="images/captain-america.jpg" class="card-img-top"
    alt="Captain America image">
  <div class="card-body">
    <h5 class="card-title">Card title</h5>
    <p class="card-text">This is a wider card with supporting text below as a natural
      lead-in to additional content. This content is a little bit longer.</p>
    <p class="card-text"><small class="text-muted">Last updated 3 mins ago</small></p>
  </div>
</div>
```

Card is represented by Section class in Java:

[Section](https://jdi-docs.github.io/jdi-light/#section)

Inner elements of Card Image represented by the following classes:

- [Text](https://jdi-docs.github.io/jdi-light/#text)
- [Image](https://jdi-docs.github.io/jdi-light/#image)

And here are methods available in Java:

|Method | Description | Return Type
--- | --- | ---
**alt()** | get attribute alt | String
**assertThat()** | property that returns object for work with assertions| TextAssert
**displayed()** | check item is displayed | TextAssert
**enabled()** | check item is enabled | TextAssert
**hasClass(String className)** | check that expected className is presented | IsAssert
**is()** | property that returns object for work with assertions| TextAssert
**src()** | get attribute src | String

[Bootstrap test examples](https://github.com/jdi-testing/jdi-light/blob/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/composite/section/card/CardImageTests.java)

##### Card List Groups

[Card List Groups Example](https://getbootstrap.com/docs/4.3/components/card/#list-groups) – create lists of content in a card
with a flush list group.

![Card list groups](../../images/bootstrap/card_list_groups.png)

Here is an example with provided Bootstrap v4.3 code:

```java 
//@FindBy(css = "#card-list-groups")
@UI("#card-list-groups")
public static CardListGroups cardListGroups;

public class CardListGroups extends Card {
    @UI(".card-header") public Label cardHeader;
    @UI(".list-group-item") public WebList listGroups;
}

@Test
public void checkCardListHeaderTest() {
    cardListGroups.cardHeader.assertThat().text(cardHeaderText);
}

@Test
public void checkCardListCellsQuantity() {
    assertEquals(cardListGroups.listGroups.size(), cardListGroupsSize);
}

@Test
public void checkCardListGroupsValues() {
    int checkedValues = 0;
    for (WebElement s : cardListGroups.listGroups) {
        if (cardListGroupsValues.contains(s.getText())) {
            checkedValues++;
        }
    }
    assertEquals(cardListGroupsValues.size(), checkedValues);
}
```

```html 
<div class="card mb-3" id="card-list-groups" style="width: 18rem;">
  <div class="card-header">
    Featured
  </div>
  <ul class="list-group list-group-flush">
    <li class="list-group-item">Cras justo odio</li>
    <li class="list-group-item">Dapibus ac facilisis in</li>
    <li class="list-group-item">Vestibulum at eros</li>
  </ul>
</div>
```

Card is represented by Section class in Java:

[Section](https://jdi-docs.github.io/jdi-light/#section)

Inner elements of Card List Groups represented by the following classes:

- [Text](https://jdi-docs.github.io/jdi-light/#text)

|Method | Description | Return Type
--- | --- | ---
**assertThat()** | Assert action | TextAssert
**getText()** | Returns text of list cell | String
**is()** | Assert action | TextAssert
**size()** | Returns cells quantity of list groups | int

[Bootstrap test examples](https://github.com/jdi-testing/jdi-light/tree/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/composite/section/card/CardListGroupsTests.java)

##### Card Kitchen Sink

[Card Kitchen Sink](https://getbootstrap.com/docs/4.3/components/card/#kitchen-sink) – Mix and match multiple content
types to create the card you need, or throw everything in there. Shown below are image styles, blocks, text styles, and
a list group—all wrapped in a fixed-width card.

![Card Kitchen Sink Example](../../images/bootstrap/card-kitchen-sink.png)

Here is an example with provided Bootstrap v4.3 code:

```java 
//@FindBy(css = "#card-kitchen-sink")
@UI("#card-kitchen-sink")
public static CardKitchenSink cardKitchenSink; 

public class CardKitchenSink extends Card {
    @UI(".card-img-top") public Image image;
    @UI(".card-title") public Text title;
    @UI(".card-text") public Text text;
    @UI(".card-body") public WebList body;
    @UI(".list-group") public WebList list;
}

@Test
public void itemsTest() {
    assertEquals(cardKitchenSink.list.size(), 3);
    cardKitchenSink.list.get(1).is().text(is(item1Text));
    cardKitchenSink.list.get(2).is().text(is(item2Text));
    cardKitchenSink.list.get(3).is().text(is(item3Text));
    cardKitchenSink.list.get(1).is().text(containsString(item1Text));
    cardKitchenSink.list.get(2).is().text(containsString(item2Text));
    cardKitchenSink.list.get(3).is().text(containsString(item3Text));
}

@Test
public void isValidationTest() {
    cardKitchenSink.image.is().src(is(imgSrc));
    cardKitchenSink.image.is().alt(is(imgAlt));
    cardKitchenSink.image.unhighlight();
    cardKitchenSink.image.assertThat().width(is(86));
    cardKitchenSink.image.assertThat().height(is(137));
    cardKitchenSink.title.is().text(is(titleText));
    cardKitchenSink.title.is().text(containsString(titleText));
    cardKitchenSink.text.is().text(is(cardText));
    cardKitchenSink.text.is().text(containsString(cardText));
}
```

```html 
<div class="card mb-3" id="card-kitchen-sink" style="width: 18rem;">
  <img src="images/spider-man.jpg" class="card-img-top" alt="Spider Man" style="width: 30%; margin: 0 auto;">
  <div class="card-body">
    <h5 class="card-title">Card title</h5>
    <p class="card-text">Some quick example text to build on the card title and make up
      the bulk of the card's content.</p>
  </div>
  <ul class="list-group list-group-flush">
    <li class="list-group-item">Cras justo odio</li>
    <li class="list-group-item">Dapibus ac facilisis in</li>
    <li class="list-group-item">Vestibulum at eros</li>
  </ul>
  <div class="card-body">
    <a href="https://github.com/jdi-testing/jdi-light" target="_blank" class="card-link">JDI Light Github</a>
    <a href="https://jdi-testing.github.io/jdi-light/index.html" target="_blank" class="card-link">JDI Website</a>
  </div>
</div>
```

Card is represented by Section class in Java:

[Section](https://jdi-docs.github.io/jdi-light/#section)

Inner elements of Card Kitchen Sink represented by the following classes:

- [Text](https://jdi-docs.github.io/jdi-light/#text)
- [Button](https://jdi-docs.github.io/jdi-light/#button)
- [Link](https://jdi-docs.github.io/jdi-light/#link)

Available methods in Java JDI Light:

|Method | Description | Return Type
--- | --- | ---
**alt()** | Assert alt image attribute | ImageAssert
**assertThat()** | Assert action | UIAssert
**getName()**| Returns name of kitchen sink | String
**getText()**| Returns text of kitchen sink | String
**height()** | Assert image height | ImageAssert
**is()** | Assert action | UIAssert
**isDisplayed()** | Returns true if kitchen sink is displayed, false if not | boolean
**src()** | Assert image src | ImageAssert
**width()** | Assert image width | ImageAssert

[Bootstrap test examples](https://github.com/jdi-testing/jdi-light/tree/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/composite/section/card/CardKitchenSinkTests.java)

##### Card with Header and Footer

[Card with Header and Footer](https://getbootstrap.com/docs/4.3/components/card/#header-and-footer) - add an optional
header and/or footer within a card.

![Card with Header and Footer Example](../../images/bootstrap/cardheaderfooter.png)

Here is an example with provided Bootstrap v4.3 code:

```java 
//@FindBy(css = "#card-with-header-and-footer") 
@UI("#card-with-header-and-footer")
public static CardWithHeaderAndFooter cardWithHeaderAndFooter;

public class CardWithHeaderAndFooter extends Card {
    @UI(".card-title") public Text title;
    @UI(".card-body p") public Text paragraph;
    @UI("button") public Button button;
    @UI(".card-header") public Text header;
    @UI("//*[contains(@class, 'footer')]") public Text footer;
}

@Test
public void getFooterTextCardWithHeaderAndFooterTest() {
    cardWithHeaderAndFooter.footer.is().text(textFooterCardWithHeaderAndFooter);
}

@Test
public void getHeaderTextCardWithHeaderAndFooterTest() {
    cardWithHeaderAndFooter.header.is().text(textHeaderCardWithHeaderAndFooter);
}
```

```html 
<div class="card mb-3 text-center" id="card-with-header-and-footer">
  <div class="card-header">
    Featured
  </div>
  <div class="card-body">
    <h5 class="card-title">Special title treatment</h5>
    <p class="card-text">With supporting text below as a natural lead-in to additional
      content.</p>
    <button href="#" class="btn btn-primary" onclick="alert('Button Clicked!');">Click
      Me!
    </button>
  </div>
  <div class="card-footer text-muted">
    2 days ago
  </div>
</div>
```

Card is represented by Section class in Java:

[Section](https://jdi-docs.github.io/jdi-light/#section)

Inner elements of Card with Header and Footer represented by the following classes:

- [Text](https://jdi-docs.github.io/jdi-light/#text)
- [Button](https://jdi-docs.github.io/jdi-light/#button)

Available methods in Java JDI Light:

|Method | Description | Return Type
--- | --- | ---
**assertThat()** | Assert action | UIAssert
**click()** | Click the button | void
**is()** | Assert action | UIAssert
**text()** | Assert text | TextAssert

[Bootstrap test examples](https://github.com/jdi-testing/jdi-light/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/composite/section/card/CardWithHeaderAndFooterTests.java)

##### Card with Grid Markup

[Card with Grid Markup](https://getbootstrap.com/docs/4.3/components/card/#using-grid-markup) - using the grid,
wrap cards in columns and rows as needed.

![Card with Grid Markup Example](../../images/bootstrap/card_grid.png)

Here is an example with provided Bootstrap v4.3 code:

```java 
//@FindBy(css = "#card-with-grid-markup")
@UI("#card-with-grid-markup")
public static CardWithGridMarkup cardWithGridMarkup;

public class CardWithGridMarkup extends Card {
    @UI(".card-title") public Text title;
    @UI(".card-body p") public Text paragraph;
    @UI("button") public Button button;
    @UI(".row .col-sm-6") public JList<CardWithHeaderAndFooter> listCard; 
}

@Test
public void getTitleTextCardWithGridMarkup11Test() {
    cardWithGridMarkup.listCard.get(0).title.is().text(textTitleCardWithGridMarkup11);
}

@Test
public void getButtonTextCardWithGridMarkup22Test() {
    cardWithGridMarkup.listCard.get(3).button.is().text(textButtonCardWithGridMarkup22);
    cardWithGridMarkup.listCard.get(3).button.click();
    validateAlert(is(textAlert));
    cardWithGridMarkup.listCard.get(3).button.is()
            .enabled()
            .displayed();
}
```

```html 
<div id="card-with-grid-markup">
  <div class="row mb-3">
    <div class="col-sm-6">
      <div class="card">
        <div class="card-body">
          <h5 class="card-title">Title</h5>
          <p class="card-text">1st row 1st cell</p>
          <button href="#" class="btn btn-primary" onclick="alert('Button Clicked!');">Click me
          </button>
        </div>
      </div>
    </div>
    <div class="col-sm-6">
      <div class="card">
        <div class="card-body">
          <h5 class="card-title">Title</h5>
          <p class="card-text">1st row 2nd cell</p>
          <button href="#" class="btn btn-primary" onclick="alert('Button Clicked!');">Click me
          </button>
        </div>
      </div>
    </div>
  </div>
  <div class="row mb-3">
    <div class="col-sm-6">
      <div class="card">
        <div class="card-body">
          <h5 class="card-title">Title</h5>
          <p class="card-text">2nd row 1st cell</p>
          <button href="#" class="btn btn-primary" onclick="alert('Button Clicked!');">Click me
          </button>
        </div>
      </div>
    </div>
    <div class="col-sm-6">
      <div class="card">
        <div class="card-body">
          <h5 class="card-title">Title</h5>
          <p class="card-text">2nd row 2nd cell</p>
          <button href="#" class="btn btn-primary" onclick="alert('Button Clicked!');">Click me
          </button>
        </div>
      </div>
    </div>
  </div>
</div>
```

Card is represented by Section class in Java:

[Section](https://jdi-docs.github.io/jdi-light/#section)

Inner elements of Card with Grid Markup represented by the following classes:

- [Text](https://jdi-docs.github.io/jdi-light/#text)
- [Button](https://jdi-docs.github.io/jdi-light/#button)

Available methods in Java JDI Light:

|Method | Description | Return Type
--- | --- | ---
**assertThat()** | Assert action | UIAssert
**click()** | Click the button | void
**is()** | Assert action | UIAssert
**text()** | Assert text | TextAssert

[Bootstrap test examples](https://github.com/jdi-testing/jdi-light/tree/bootstrap/jdi-light/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/composite/section/card/CardWithGridMarkupTests.java)

##### Card Utilities

[Card Utilities](https://getbootstrap.com/docs/4.3/components/card/#using-utilities) - use handful of available
sizing utilities to quickly set a card’s width.

![Card Utilities Example](../../images/bootstrap/card_utilities.png)

Here is an example with provided Bootstrap v4.3 code:

```java 
//@FindBy(className = ".w-75") 
@UI(".w-75")
public static CardUtilities cardWidth75;

public class CardUtilities extends Card {
    @UI(".card-title") public Text cardTitle;
    @UI(".card-text") public Text cardText;
    @UI(".btn") public Button cardButton;
}

@Test(dataProvider = "cardUtilitiesElementsWithWidth")
public void cardValidationTest(CardUtilities cardUtilitiesElem, 
int widthInPercent, String widthInPixels) {
    cardUtilitiesElem.core().is()
            .hasClass(String.format("card w-%d", widthInPercent))
            .css("width", widthInPixels)
            .css("background-color", whiteColor);
}
```

```html 
<div class="card w-75" style="margin-bottom: 10px;">
  <div class="card-body">
    <h5 class="card-title">Spider man (w-75)</h5>
    <p class="card-text">Spider-Man is a fictional superhero created by writer-editor
      Stan Lee and writer-artist Steve Ditko.</p>
    <a href="https://en.wikipedia.org/wiki/Spider-Man" class="btn btn-primary" target="_blank">Read more</a>
  </div>
</div>
```

Available methods in Java JDI Light:

|Method | Description | Return Type
--- | --- | ---
**assertThat()** | Assert action | TextAssert
**css()** | Get element's css value | int
**hasClass()** | Assert class | String
**is()** | Assert action | TextAssert

[Bootstrap test examples](https://github.com/jdi-testing/jdi-light/blob/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/composite/section/card/CardUtilitiesTests.java)

##### Card Using Custom CSS

[Card Using Custom CSS](https://getbootstrap.com/docs/4.3/components/card/#using-custom-css) - use custom CSS in your
stylesheets or as inline styles to set a width.

![Card Using Custom CSS Example](../../images/bootstrap/card_custom_CSS.png)

Here is an example with provided Bootstrap v4.3 code:

```java 
//@FindBy(css = "#card-custom-css-1")
@UI("#card-custom-css-1")
public static CardWithCustomCss cardWithCustomCss13Rem;

public class CardWithCustomCss extends Card {
    @UI(".card-title") public Text title;
    @UI(".card-text") public Text text;
    @UI(".btn") public Button button;
}

@Test
public void getTextTest() {
    assertEquals(cardWithCustomCss13Rem.text.getText(), text);
}

@Test
public void isValidationTest() {
    cardWithCustomCss13Rem.title.is().text(is(title));
    cardWithCustomCss13Rem.text.is().text(is(text));
    cardWithCustomCss13Rem.button.is().displayed()
            .and().text(is(buttonText))
            .core()
            .css("font-size", is("16px"))
            .cssClass("btn btn-primary")
            .tag(is("a"))
            .attr("href", link);
    cardWithCustomCss13Rem.button.is().enabled();
    cardWithCustomCss13Rem.is().displayed()
            .core()
            .css("width", is("208px"))
            .css("margin-bottom", is("10px"));
}
```

```html 
<div class="card" id="card-custom-css-1" style="width: 13rem; margin-bottom: 10px;">
  <div class="card-body">
    <h5 class="card-title">Spider man (13rem)</h5>
    <p class="card-text">Spider-Man is a fictional superhero created by writer-editor
      Stan Lee and writer-artist Steve Ditko.</p>
    <a href="https://en.wikipedia.org/wiki/Spider-Man" class="btn btn-primary" target="_blank">Read more</a>
  </div>
</div>
```

Card is represented by Section class in Java:

[Section](https://jdi-docs.github.io/jdi-light/#section)

Inner elements of Card with custom CSS represented by the following classes:

- [Text](https://jdi-docs.github.io/jdi-light/#text)
- [Button](https://jdi-docs.github.io/jdi-light/#button)

Available methods in Java JDI Light:

|Method | Description | Return Type
--- | --- | ---
**assertThat()** | Assert action | UIAssert
**click()** | Click the button | void
**is()** | Assert action | UIAssert
**text()** | Assert text | TextAssert

[Bootstrap test examples](https://github.com/jdi-testing/jdi-light/blob/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/composite/section/card/CardWithCustomCss13RemTests.java)

##### Card Text Alignment

[Card Text Alignment](https://getbootstrap.com/docs/4.3/utilities/text/#text-alignment) - You can quickly change
the text alignment of any card — in it's entirety or specific parts — with Bootstrap's text align classes.

![Card Text Alignment Example](../../images/bootstrap/cardtextalignment.png)

Here is an example with provided Bootstrap v4.3 code:

```java 
//@FindBy(css = "#card-text-left")
@UI("#card-text-left")
public static CardTextAlignment cardLeftTextAlignment;
//@FindBy(css = "#card-text-center")
@UI("#card-text-center")
public static CardTextAlignment cardCenterTextAlignment;
//@FindBy(css = "#card-text-right")
@UI("#card-text-right")
public static CardTextAlignment cardRightTextAlignment;

public class CardTextAlignment extends Card {
    @UI(".card-title") public Text cardTitle;
    @UI(".card-text") public Text cardDescription;
    @UI("button") public Button cardButton;
}

String alertText = "Button Clicked!";

@Test
public void clickTest() {
    cardLeftTextAlignment.highlight();
    cardLeftTextAlignment.cardButton.click();
    validateAlert(is(alertText));

    cardCenterTextAlignment.highlight();
    cardCenterTextAlignment.cardButton.click();
    validateAlert(is(alertText));

    cardRightTextAlignment.highlight();
    cardRightTextAlignment.cardButton.click();
    validateAlert(is(alertText));
}
```

```html 
<div id="card-text-center" class="card mb-2 text-center" style="width: 18rem;">
  <div class="card-body">
    <h5 class="card-title">Special title treatment</h5>
    <p class="card-text">With supporting text below as a natural lead-in to additional
      content.</p>
    <button href="#" class="btn btn-success" onclick="alert('Button Clicked!');">Click
      Me!
    </button>
  </div>
</div>
```

Card is represented by Section class in Java:

[Section](https://jdi-docs.github.io/jdi-light/#section)

Inner elements of Card Text Alignment represented by the following classes:

- [Text](https://jdi-docs.github.io/jdi-light/#text)
- [Button](https://jdi-docs.github.io/jdi-light/#button)

Available methods in Java JDI Light:

|Method | Description | Return Type
--- | --- | ---
**assertThat()** | Assert action | TextAssert
**attr()** | Assert button attribute | IsAssert
**click()** | Click button | void
**css()** | Get button css value | String
**cssClass()** | Assert button css class | IsAssert
**displayed()** | Check that element is displayed | TextAssert
**getText()** | Get button text | String
**getValue()** | Get button value | String
**is()** | Assert action | TextAssert
**tag()** | Assert button tag | IsAssert

[Bootstrap test examples](https://github.com/jdi-testing/jdi-light/blob/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/composite/section/card/CardTextAlignmentTests.java)

##### Card Navigation

[Card Navigation](https://getbootstrap.com/docs/4.3/components/card/#navigation) adds some navigation to a card’s header
(or block) with Bootstrap’s nav components.

![Card Navigation Example](../../images/bootstrap/cardnav.png)

Here is an example with provided Bootstrap v4.3 code:

```java 
@UI("#card-navigation") // @FindBy(id = "card-navigation")
public static CardNavigation cardNavigation;

public class CardNavigation extends Card {
    @UI(".nav") public Menu nav;
    @UI("#activeLink") public Link activeLink;
    @UI("#jdiLink") public Link jdiLink;
    @UI("#disabledLink") public Link disabledLink;
    @UI("h5") public Text title;
    @UI(".card-text") public Text subtitle;
    @UI("button") public Button button;
}

@Test
public void getLinkTextTest() {
    cardNavigation.nav.highlight();
    assertEquals(cardNavigation.activeLink.getText(), activeLinkText);
    assertEquals(cardNavigation.jdiLink.getText(), jdiLinkText);
    assertEquals(cardNavigation.disabledLink.getText(), disabledLinkText);
}

@Test
public void isValidationTest() {
    cardNavigation.highlight();

    cardNavigation.title.is().text(titleText);
    cardNavigation.title.is().displayed();

    cardNavigation.subtitle.is().text(subtitleText);
    cardNavigation.subtitle.is().displayed();

    cardNavigation.activeLink.is().displayed();
    cardNavigation.activeLink.is().enabled();

    cardNavigation.jdiLink.is().displayed();
    cardNavigation.jdiLink.is().enabled();

    cardNavigation.disabledLink.is().displayed();
    cardNavigation.disabledLink.is().disabled();

    cardNavigation.activeLink.assertThat().text(is(activeLinkText));
    cardNavigation.jdiLink.assertThat().text(is(jdiLinkText));
    cardNavigation.disabledLink.assertThat().text(is(disabledLinkText));

    cardNavigation.activeLink.is().ref(activeLinkRef);
    cardNavigation.jdiLink.is().ref(jdiLinkRef);
    cardNavigation.disabledLink.is().ref(disabledLinkRef);

    cardNavigation.button.is().text(is(buttonText));
    cardNavigation.button.is().text(containsString("Click"));
    assertThat(cardNavigation.button.core().css("font-size"), is("16px"));
    cardNavigation.button.assertThat().displayed()
            .and()
            .core()
            .cssClass("btn btn-primary")
            .attr("onclick", "alert('Button Clicked!');")
            .tag(is("button"));
}
```

```html 
<div id="card-navigation" class="card text-center mb-3">
  <div class="card-header">
    <ul class="nav nav-tabs card-header-tabs">
      <li class="nav-item">
        <a id="activeLink" class="nav-link active" href="javascript: void()"
          onclick="alert('Active Tab Clicked!');">Active</a>
      </li>
      <li class="nav-item">
        <a id="jdiLink" class="nav-link" href="https://github.com/jdi-testing/jdi-light" target="_blank">JDI</a>
      </li>
      <li class="nav-item">
        <a id="disabledLink" class="nav-link disabled" href="javascript: void()" tabindex="-1"
          aria-disabled="true">Disabled</a>
      </li>
    </ul>
  </div>
  <div class="card-body">
    <h5 class="card-title">Special title treatment</h5>
    <p class="card-text">With supporting text below as a natural lead-in to additional
      content.</p>
    <button href="#" class="btn btn-primary" onclick="alert('Button Clicked!');">Click
      Me!
    </button>
  </div>
</div>
```

Card is represented by Section class in Java:

[Section](https://jdi-docs.github.io/jdi-light/#section)

Inner elements of Card Navigation represented by the following classes:

- [Menu](https://jdi-docs.github.io/jdi-light/#menu)
- [Text](https://jdi-docs.github.io/jdi-light/#text)
- [Button](https://jdi-docs.github.io/jdi-light/#button)
- [Link](https://jdi-docs.github.io/jdi-light/#link)

Available methods in Java JDI Light:

|Method | Description | Return Type
--- | --- | ---
**attr()** | Assert element attribute | IsAssert
**click()** | Click element | void
**css()** | Get button css value | String
**cssClass()** | Assert element css class | IsAssert
**disabled()** | Check that element is disabled | UIAssert
**displayed()** | Check that element is displayed | TextAssert
**enabled()** | Check that element is enabled | UIAssert
**getText()** | Get element text | String
**getValue()** | Get element value | String
**is()** | Assert action | TextAssert
**ref()** | Get link ref attribute value | String
**tag()** | Assert element tag | IsAssert

[Bootstrap test examples](https://github.com/jdi-testing/jdi-light/blob/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/composite/section/card/CardNavigationTests.java)

##### Card Image Caps

[Card Image Caps](https://getbootstrap.com/docs/4.3/components/card/#image-caps) - similar to headers and footers, cards
can include top and bottom “image caps” — images at the top or bottom of a card.

![Card Image Caps Example](../../images/bootstrap/cardimagecaps.png)

Here is an example with provided Bootstrap v4.3 code:

```java 
//@FindBy(id = "card-image-caps-1")
@UI("#card-image-caps-1")
public static CardImageCaps cardImageOnTop;

public class CardImageCaps extends Card {
    @UI(".card-img-top") public Image image;
    @UI(".card-body") public Text text;
}

@Test
public void getSrcTest() {
    assertEquals(cardImageOnTop.image.src(), topCardData.getSrcAttr());
    assertEquals(cardImageOnBottom.image.src(), bottomCardData.getSrcAttr());
}

@Test
public void getAltTest() {
    assertEquals(cardImageOnTop.image.alt(), topCardData.getAltAttr());
    assertEquals(cardImageOnBottom.image.alt(), bottomCardData.getAltAttr());
}
```

```html 
<div class="card mb-3" id="card-image-caps-1" style="width: 18rem;">
  <img style="width: 30%; margin: 0 auto;" src="images/captain-america.jpg" class="card-img-top"
    alt="Captain America image">
  <div class="card-body">
    <h5 class="card-title">Card title</h5>
    <p class="card-text">This is a wider card with supporting text below as a natural
      lead-in to additional content. This content is a little bit longer.</p>
    <p class="card-text"><small class="text-muted">Last updated 3 mins ago</small></p>
  </div>
</div>
```

Card is represented by Section class in Java:

[Section](https://jdi-docs.github.io/jdi-light/#section)

Inner elements of Card Image Caps represented by the following classes:

- [Text](https://jdi-docs.github.io/jdi-light/#text)
- [Image](https://jdi-docs.github.io/jdi-light/#image)

Available methods in Java JDI Light:

|Method | Description | Return Type
--- | --- | ---
**assertThat()** | Assert action | UIAssert
**getName()**| Returns name of card | String
**getText()**| Returns text of card | String
**is()** | Assert action | UIAssert
**isDisplayed()** | Returns true if card is displayed, false if not | boolean

[Bootstrap test examples](https://github.com/jdi-testing/jdi-light/blob/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/composite/section/card/CardImageCapsTests.java)

##### Card Image Overlays

[Card Image Overlays](https://getbootstrap.com/docs/4.3/components/card/#image-overlays) turn an image into a card
background and overlay your card’s text. Depending on the image, you may or may not need additional styles or utilities.

![Card Image Overlays Example](../../images/bootstrap/card-image-overlays.png)

Here is an example with provided Bootstrap v4.3 code:

```java 
//@FindBy(css = "#card-image-overlay") 
@UI("#card-image-overlay")
public static CardImageOverlays cardImageOverlays;

public class CardImageOverlays extends Card {
    @UI("#card-svg") public VectorImage vectorImage;
    @UI("#card-overlay-section") public OverlaySection overlaySection;
}

@Test
public void availabilityTest() {
    cardImageOverlays.overlaySection.title.is()
            .displayed()
            .enabled();
    cardImageOverlays.overlaySection.title.is()
            .displayed()
            .enabled();
}

@Test
public void isValidationTest() {
    cardImageOverlays.overlaySection.title.is().text(is(TITLE));
    cardImageOverlays.vectorImage.assertThat().height(is(HEIGHT));
    cardImageOverlays.vectorImage.assertThat().width(is(WIDTH));
}

@Test
public void classTest() {
    cardImageOverlays.overlaySection.is().core().hasClass(OVERLAY_CLASS);
    cardImageOverlays.overlaySection.assertThat().core().hasClass(OVERLAY_CLASS);
    cardImageOverlays.vectorImage.is().core().hasClass(IMAGE_TOP_CLASS);
    cardImageOverlays.vectorImage.assertThat().core().hasClass(IMAGE_TOP_CLASS);
}

@Test
public void vectorInternalElementsTest() {
     assertEquals(cardImageOverlays.vectorImage.getText(VECTOR_TEXT_TAG), VECTOR_TEXT);
     assertEquals(cardImageOverlays.vectorImage.getAttribute(VECTOR_TEXT_TAG, VECTOR_TEXT_ATTR), VECTOR_TEXT_VALUE);
}
```

```html 
<div class="card bg-dark text-dark mb-3">
  <img src="images/captain-america.jpg" class="card-img" alt="Captain America image">
  <div class="card-img-overlay">
    <h5 class="card-title">Card title</h5>
    <p class="card-text">This is a wider card with supporting text below as a natural
      lead-in to additional content. This content is a little bit longer.</p>
    <p class="card-text">Last updated 3 mins ago</p>
  </div>
</div>
```

Card is represented by Section class in Java:

[Section](https://jdi-docs.github.io/jdi-light/#section)

Inner elements of Card Image Overlays represented by the following classes:

- [Text](https://jdi-docs.github.io/jdi-light/#text)
- [VectorImage](https://jdi-docs.github.io/jdi-light/#vector-image) <---No such element--->

And here are methods available in Java:

|Method | Description | Return Type
--- | --- | ---
**assertThat()** | property that returns object for work with assertions| TextAssert
**displayed()** | check item is displayed | TextAssert
**enabled()** | check item is enabled | TextAssert
**getAttribute(String tagName, String attr)** | get attribute of an element inside vector image by tag | String
**getText(String tagName)** | get text of an element inside vector image by tag | String
**hasClass(String className)** | check that expected className is presented | IsAssert
**is()** | property that returns object for work with assertions| TextAssert

[Bootstrap test examples](https://github.com/jdi-testing/jdi-light/blob/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/composite/section/card/CardImageOverlaysTests.java)

##### Card Horizontal

[Card Horizontal](https://getbootstrap.com/docs/4.3/components/card/#horizontal) - using a combination of grid and
utility classes, cards can be made horizontal in a mobile-friendly and responsive way.

![Card Horizontal Example](../../images/bootstrap/card_horizontal.png)

Here is an example with provided Bootstrap v4.3 code:

```java 
//FindBy(css = "#card-horizontal")
@UI("#card-horizontal")
public static CardHorizontal cardHorizontal;

public class CardHorizontal extends Card {
    @UI(".card-title") public Text title;
    @UI("//p[contains(text(), 'fictional character')]") public Text mainText;
    @UI(".text-muted") public Text smallText;
    @UI(".card-img") public Image image;
}

@Test
public void getSrcTest() {
    assertEquals(cardHorizontal.image.src(), imageSrc);
}

@Test
public void isValidationTest() {
    cardHorizontal.title.is().text(is(titleText));
    cardHorizontal.mainText.is().text(is(mainText));
    cardHorizontal.smallText.is().displayed()
            .and().text(is(smallText))
            .core()
            .css("font-size", is("11.2px"))
            .tag(is("small"));
    cardHorizontal.image.is().displayed()
            .and().src(is(imageSrc))
            .core()
            .attr("title", imageTitle);
    cardHorizontal.image.unhighlight();
    cardHorizontal.image.assertThat().width(anyOf(is(91), is(94)));
    cardHorizontal.image.assertThat().height(anyOf(is(146), is(150)));
}
```

```html 
<div class="card mb-3" id="card-horizontal" style="max-width: 540px;">
  <div class="row no-gutters">
    <div class="col-md-4">
      <img src="images/wolverin.jpg" class="card-img" id="card-horizontal-img" title="Wolverine icon">
    </div>
    <div class="col-md-8">
      <div class="card-body">
        <h5 class="card-title" id="card-horizontal-title">Wolverine</h5>
        <p class="card-text">Wolverine is a fictional character appearing in
          American comic books published by Marvel Comics, mostly in association
          with the X-Men. He is a mutant who possesses animal-keen senses,
          enhanced physical capabilities, powerful regenerative ability known as a
          healing factor, and three retractable claws in each hand. Wolverine has
          been depicted variously as a member of the X-Men, Alpha Flight, and the
          Avengers.</p>
        <p class="card-text"><small class="text-muted">The character appeared in
            #180 (1974)</small></p>
      </div>
    </div>
  </div>
</div>
```

Card is represented by Section class in Java:

[Section](https://jdi-docs.github.io/jdi-light/#section)

Inner elements of Card Horizontal represented by the following classes:<br>

- [Text](https://jdi-docs.github.io/jdi-light/#text)
- [Image](https://jdi-docs.github.io/jdi-light/#image)

Available methods in Java JDI Light:

|Method | Description | Return Type
--- | --- | ---
**alt()** | Assert alt image attribute | ImageAssert
**assertThat()** | Assert action | UIAssert
**getText()**| Returns text | String
**height()** | Assert image height | ImageAssert
**is()** |	Assert action | UIAssert
**src()** | Assert image src | ImageAssert
**width()** | Assert image width | ImageAssert

[Bootstrap test examples](https://github.com/jdi-testing/jdi-light/blob/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/composite/section/card/CardHorizontalTests.java)

##### Card Background And Color

[Card Background And Color](https://getbootstrap.com/docs/4.3/components/card/#background-and-color) - use text and
background utilities to change the appearance of a card.

![Card Background And Color Example](../../images/bootstrap/cardbackgroundandcolor.png)

Here is an example with provided Bootstrap v4.3 code:

```java 
//@FindBy(css = "#card-bright-blue")
@UI("#card-bright-blue")
public static CardStyled cardBrightBlue;

public class CardStyled extends Card {
    @UI(".card-header") public Text header;
    @UI(".card-title") public Text title;
    @UI(".card-text") public Text body;
}

@Test(dataProvider = "cardColors")
public void checkColorCardsTest(CardWithHeaderAndFooter card, String cssClass, String color) {
    card.is()
            .core()
            .hasClass(cssClass)
            .css("background-color", is(color));

    card.header.is()
            .displayed().and()
            .core().css("background-color", is("rgba(0, 0, 0, 0.03)"));

    card.paragraph.is()
            .displayed().and()
            .core().css("background-color", is("rgba(0, 0, 0, 0)"));

}
```

```html 
<div class="card text-white bg-primary mb-3" style="max-width: 18rem;" id="card-bright-blue">
  <div class="card-header">Header</div>
  <div class="card-body">
    <h5 class="card-title">Primary card title</h5>
    <p class="card-text">Some quick example text to build on the card title and make up
      the bulk of the card's content.</p>
  </div>
</div>
```

Card is represented by Section class in Java:

[Section](https://jdi-docs.github.io/jdi-light/#section)

Inner elements of Card Background Color can be represented by the following classes:

- [Text](https://jdi-docs.github.io/jdi-light/#text)
- [Button](https://jdi-docs.github.io/jdi-light/#button)

Available methods in Java JDI Light:

|Method | Description | Return Type
--- | --- | ---
**assertThat()** | Assert action | UIAssert
**css()** | Get element css value | String
**displayed()** | Check that element is displayed | TextAssert
**is()** | Assert action | UIAssert

[Bootstrap test examples](https://github.com/jdi-testing/jdi-light/blob/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/composite/section/card/CardBackgroundAndColorTests.java)

##### Card Border

[Card Border](https://getbootstrap.com/docs/4.3/components/card/#border) - use border utilities to change just the
border-color of a card. Note that you can put `.text-{color}` classes on the parent `.card` or a subset of the card’s
contents as shown below.

![Card Border Example](../../images/bootstrap/cardborders.png)

Here is an example with provided Bootstrap v4.3 code:

```java 
//@FindBy(css = "#card-border-primatry")
@UI("#card-border-primary")//@FindBy(css = "#card-border-primatry")
public static CardStyled cardBorderPrimary;

public class CardStyled extends Card {
    @UI(".card-header") public Text header;
    @UI(".card-title") public Text title;
    @UI(".card-text") public Text body;
}

@Test(dataProvider = "cardBorderColor")
public void getBorderColorTest(CardBorder cardBorder, String color) {
    cardBorder.is().core().css("border-bottom-color", is(color));
    cardBorder.is().core().css("border-left-color", is(color));
    cardBorder.is().core().css("border-right-color", is(color));
    cardBorder.is().core().css("border-top-color", is(color));
}

@Test(dataProvider = "cardBorderHeaderText")
public void getHeaderTextTest(CardBorder cardBorder, String headerText) {
    assertEquals(cardBorder.border.getText(), headerText);
}
```

```html 
<div class="card border-primary mb-3" id="card-border-primary" style="max-width: 18rem;">
  <div class="card-header">Card with primary border</div>
  <div class="card-body text-primary">
    <h5 class="card-title">Primary card title</h5>
    <p class="card-text">Some quick example text to build on the card title and make up
      the bulk of the card's content.</p>
  </div>
</div>
```

Card is represented by Section class in Java:

[Section](https://jdi-docs.github.io/jdi-light/#section)

Inner elements of Card Border represented by the following classes:

[Text](https://jdi-docs.github.io/jdi-light/#text)

Available methods in Java JDI Light:

|Method | Description | Return Type
--- | --- | ---
**assertThat()** | Assert action | UIAssert
**css()** | Get element css value | String
**is()** | Assert action | UIAssert
**text()** | Assert text | TextAssert

[Bootstrap test examples](https://github.com/jdi-testing/jdi-light/blob/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/composite/section/card/CardBorderTests.java)

##### Card Mixins Utilities

[Card Mixins Utilities](https://getbootstrap.com/docs/4.3/components/card/#mixins-utilities) - you can also change
the borders on the card header and footer as needed, and even remove their background-color with `.bg-transparent`.

![Card Mixins Utilities Example](../../images/bootstrap/card-mixins-utilities.png)

Here is an example with provided Bootstrap v4.3 code:

```java 
//@FindBy(css = "#card-mixins-utilities")
@UI("#card-mixins-utilities")         
public static CardMixinsUtilities cardMixinsUtilities;

public class CardMixinsUtilities extends Card {
    @UI(".card-header") public Text header;
    @UI(".card-footer") public Text footer;
    @UI(".card-title") public Text title;
    @UI(".card-text") public Text text;
}

@Test
public void getHeaderTextTest() {
    assertEquals(cardMixinsUtilities.header.getText(), header);
}

@Test
public void isValidationTest() {
    cardMixinsUtilities.is().displayed()
            .and().core().css("border-color", "rgb(40, 167, 69)");
}
```

```html 
<div class="card border-success mb-3" id="card-mixins-utilities" style="max-width: 18rem;">
  <div class="card-header bg-transparent border-success">According To Samuel L. Jackson
  </div>
  <div class="card-body text-success">
    <h5 class="card-title">The Secret To Marvel Studios’ Success</h5>
    <p class="card-text">Because while the Marvel Cinematic Universe always includes
      plenty of spectacle and pulse pounding action, each blockbuster tells a very
      human story. The heroes of the world are flawed and funny, allowing audiences to
      connect with characters who are super powered and dealing with situations we
      truly can't comprehend.</p>
  </div>
  <div class="card-footer bg-transparent border-success">For Cinema Blend</div>
</div>
```

Card is represented by Section class in Java:

[Section](https://jdi-docs.github.io/jdi-light/#section)

Inner elements of Card Mixing Utilities represented by the following classes:

[Text](https://jdi-docs.github.io/jdi-light/#text)

Available methods in Java JDI Light:

|Method | Description | Return Type
--- | --- | ---
**assertThat()** | Assert action | UIAssert
**css()** | Get element css value | String
**is()** | Assert action | UIAssert
**text()** | Assert text | TextAssert

[Bootstrap test examples](https://github.com/jdi-testing/jdi-light/blob/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/composite/section/card/CardMixinsUtilitiesTests.java)

##### Card Groups

[Card Groups](https://getbootstrap.com/docs/4.3/components/card/#card-groups) - use card groups to render cards as
a single, attached element with equal width and height columns.

![Card_Groups Example](../../images/bootstrap/card-groups.png)

Here is an example with provided Bootstrap v4.3 code:

```java 
//@FindBy(css = ".card-group:nth-of-type(1)") 
@UI(".card-group:nth-of-type(1)")
public static CardGroupedSection cardGroupSectionWithoutFooter;

public class CardGroupSection extends Section {
    @UI(".card:nth-of-type(1)") public CardGrouped card1;
    @UI(".card:nth-of-type(2)") public CardGrouped card2;
}

public class CardGrouped extends Card {
    @UI(".card-title") public Text title;
    @UI(".card-text:nth-of-type(1)") public Text mainText;
    @UI(".card-text .text-muted") public Text mutedText;
    @UI(".card-img-top") public Image image;
    @UI(".card-footer small") public Text footerText;
}

private String card1ImageSrc = "https://jdi-testing.github.io/jdi-light/images/spider-man.jpg";
private String card2ImageSrc = "https://jdi-testing.github.io/jdi-light/images/hulk.jpg";
private String card1ImageAlt = "spider-man";
private String card2ImageAlt = "hulk";

@Test
public void getSrcTest() {
    assertEquals(cardGroupSectionWithoutFooter.card1.image.src(), card1ImageSrc);
    assertEquals(cardGroupSectionWithoutFooter.card2.image.src(), card2ImageSrc);
}

@Test
public void getAltTest() {
    assertEquals(cardGroupSectionWithoutFooter.card1.image.alt(), card1ImageAlt);
    assertEquals(cardGroupSectionWithoutFooter.card2.image.alt(), card2ImageAlt);
}
```

```html 
<div class="card-group" style="margin-bottom: 10px;">
  <div class="card">
    <p style="text-align: center;"><img src="images/spider-man.jpg" class="card-img-top" alt="spider-man"
        style="width: 75px; height: 120px;"></p>
    <div class="card-body">
      <h5 class="card-title">Spider man</h5>
      <p class="card-text">Spider-Man is a fictional superhero created by
        writer-editor Stan Lee and writer-artist Steve Ditko.</p>
      <p class="card-text"><small class="text-muted">Peter Parker</small></p>
    </div>
  </div>
  <div class="card">
    <p style="text-align: center;"><img src="images/hulk.jpg" class="card-img-top" alt="hulk"
        style="width: 98px; height: 120px;">
    </p>
    <div class="card-body">
      <h5 class="card-title">Hulk</h5>
      <p class="card-text">The Hulk is a fictional superhero appearing in publications
        by the American publisher Marvel Comics.</p>
      <p class="card-text"><small class="text-muted">Bruce Banner</small></p>
    </div>
  </div>
</div>
```

###### Card Groups with Footer

![Card Groups with Footer Example](../../images/bootstrap/card-groups-with-footer.png)

Here is an example with provided Bootstrap v4.3 code:

```java 
//@FindBy(css = ".card-group:nth-of-type(2)")
@UI(".card-group:nth-of-type(2)")
public static CardGroupedSection cardGroupWithFooter;

public class CardGroupSection extends Section {
    @UI(".card:nth-of-type(1)") public CardGrouped card1;
    @UI(".card:nth-of-type(2)") public CardGrouped card2;
}

public class CardGrouped extends Card {
    @UI(".card-title") public Text title;
    @UI(".card-text:nth-of-type(1)") public Text mainText;
    @UI(".card-text .text-muted") public Text mutedText;
    @UI(".card-img-top") public Image image;
    @UI(".card-footer small") public Text footerText;
}

private String card1ImageSrc = "https://jdi-testing.github.io/jdi-light/images/spider-man.jpg";
private String card2ImageSrc = "https://jdi-testing.github.io/jdi-light/images/hulk.jpg";
private String card1ImageAlt = "spider-man";
private String card2ImageAlt = "hulk";

@Test
public void getSrcTest() {
    assertEquals(cardGroupWithFooter.card1.image.src(), card1ImageSrc);
    assertEquals(cardGroupWithFooter.card2.image.src(), card2ImageSrc);
}

@Test
public void getAltTest() {
    assertEquals(cardGroupWithFooter.card1.image.alt(), card1ImageAlt);
    assertEquals(cardGroupWithFooter.card2.image.alt(), card2ImageAlt);
}
```

```html 
<div class="card-group" style="margin-bottom: 10px;">
  <div class="card">
    <p style="text-align: center;"><img src="images/spider-man.jpg" class="card-img-top" alt="spider-man"
        style="width: 75px; height: 120px;"></p>
    <div class="card-body">
      <h5 class="card-title">Spider man</h5>
      <p class="card-text">Spider-Man is a fictional superhero created by
        writer-editor Stan Lee and writer-artist Steve Ditko.</p>
    </div>
    <div class="card-footer">
      <small class="text-muted">Peter Parker</small>
    </div>
  </div>
  <div class="card">
    <p style="text-align: center;"><img src="images/hulk.jpg" class="card-img-top" alt="hulk"
        style="width: 98px; height: 120px;">
    </p>
    <div class="card-body">
      <h5 class="card-title">Hulk</h5>
      <p class="card-text">The Hulk is a fictional superhero appearing in publications
        by the American publisher Marvel Comics.</p>
    </div>
    <div class="card-footer">
      <small class="text-muted">Bruce Banner</small>
    </div>
  </div>
</div>
```

Card is represented by Section class in Java:

[Section](https://jdi-docs.github.io/jdi-light/#section)

Inner elements of Card Grouped represented by the following classes:

- [Text](https://jdi-docs.github.io/jdi-light/#text)
- [Image](https://jdi-docs.github.io/jdi-light/#image)

[Bootstrap test examples](https://github.com/jdi-testing/jdi-light/tree/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/composite/section/card/CardGroupsTests.java)

##### Card Decks

[Card Decks](https://getbootstrap.com/docs/4.3/components/card/#card-decks) - use card decks for a set of equal width
and height cards that aren't attached to one another.

![Card_Decks Example](../../images/bootstrap/card-decks.png)

Here is an example with provided Bootstrap v4.3 code:

```java 
//@FindBy(css = ".card-deck:nth-of-type(1)")
@UI(".card-deck:nth-of-type(1)")
public static CardDeckSection cardDeckSectionWithoutFooter;

public class CardDeckSection extends Section {
    @UI(".card:nth-of-type(1)") public CardGrouped card1;
    @UI(".card:nth-of-type(2)") public CardGrouped card2;
}

public class CardGrouped extends Card {
    @UI(".card-title") public Text title;
    @UI(".card-text:nth-of-type(1)") public Text mainText;
    @UI(".card-text .text-muted") public Text mutedText;
    @UI(".card-img-top") public Image image;
    @UI(".card-footer small") public Text footerText;
}

private static final String card1Title = "SPIDER MAN";
private static final String card2Title = "HULK";
private static final String card1MainText = "Spider-Man is a fictional superhero created by writer-editor Stan Lee and writer-artist Steve Ditko.";
private static final String card2MainText = "The Hulk is a fictional superhero appearing in publications by the American publisher Marvel Comics.";

@Test
public void getTitleTextTest() {
    cardDeckSectionWithoutFooter.highlight();
    assertEquals(cardDeckSectionWithoutFooter.card1.title.getText(), card1Title);
    assertEquals(cardDeckSectionWithoutFooter.card2.title.getText(), card2Title);
}

@Test
public void getMainTextTest() {
    cardDeckSectionWithoutFooter.highlight();
    assertEquals(cardDeckSectionWithoutFooter.card1.mainText.getText(), card1MainText);
    assertEquals(cardDeckSectionWithoutFooter.card2.mainText.getText(), card2MainText);
}
```

```html 
<div class="card-deck" style="margin-bottom: 10px;">
  <div class="card">
    <p style="text-align: center;"><img src="images/spider-man.jpg" class="card-img-top" alt="spider-man"
        style="width: 75px; height: 120px;"></p>
    <div class="card-body">
      <h5 class="card-title">Spider man</h5>
      <p class="card-text">Spider-Man is a fictional superhero created by
        writer-editor Stan Lee and writer-artist Steve Ditko.</p>
      <p class="card-text"><small class="text-muted">Peter Parker</small></p>
    </div>
  </div>
  <div class="card">
    <p style="text-align: center;"><img src="images/hulk.jpg" class="card-img-top" alt="hulk"
        style="width: 98px; height: 120px;">
    </p>
    <div class="card-body">
      <h5 class="card-title">Hulk</h5>
      <p class="card-text">The Hulk is a fictional superhero appearing in publications
        by the American publisher Marvel Comics.</p>
      <p class="card-text"><small class="text-muted">Bruce Banner</small></p>
    </div>
  </div>
</div>
```

###### Card Decks with Footer

![Card Decks with Footer Example](../../images/bootstrap/card-decks-with-footer.png)

Here is an example with provided Bootstrap v4.3 code:

```java 
//@FindBy(css = ".card-deck:nth-of-type(2)")
@UI(".card-deck:nth-of-type(2)")
public static CardDeckSection cardDeckSectionWithFooter;

public class CardGroupSection extends Section {
    @UI(".card:nth-of-type(1)") public CardGrouped card1;
    @UI(".card:nth-of-type(2)") public CardGrouped card2;
}

public class CardGrouped extends Card {
    @UI(".card-title") public Text title;
    @UI(".card-text:nth-of-type(1)") public Text mainText;
    @UI(".card-text .text-muted") public Text mutedText;
    @UI(".card-img-top") public Image image;
    @UI(".card-footer small") public Text footerText;
}

private static final String card1Title = "SPIDER MAN";
private static final String card2Title = "HULK";
private static final String card1MainText = "Spider-Man is a fictional superhero created by writer-editor Stan Lee and writer-artist Steve Ditko.";
private static final String card2MainText = "The Hulk is a fictional superhero appearing in publications by the American publisher Marvel Comics.";

@Test
public void getTitleTextTest() {
    cardDeckSectionWithFooter.highlight();
    assertEquals(cardDeckSectionWithFooter.card1.title.getText(), card1Title);
    assertEquals(cardDeckSectionWithFooter.card2.title.getText(), card2Title);
}

@Test
public void getMainTextTest() {
    cardDeckSectionWithFooter.highlight();
    assertEquals(cardDeckSectionWithFooter.card1.mainText.getText(), card1MainText);
    assertEquals(cardDeckSectionWithFooter.card2.mainText.getText(), card2MainText);
}    
```

```html 
<div class="card-deck" style="margin-bottom: 10px;">
  <div class="card">
    <p style="text-align: center;"><img src="images/spider-man.jpg" class="card-img-top" alt="spider-man"
        style="width: 75px; height: 120px;"></p>
    <div class="card-body">
      <h5 class="card-title">Spider man</h5>
      <p class="card-text">Spider-Man is a fictional superhero created by
        writer-editor Stan Lee and writer-artist Steve Ditko.</p>
    </div>
    <div class="card-footer">
      <small class="text-muted">Peter Parker</small>
    </div>
  </div>
  <div class="card">
    <p style="text-align: center;"><img src="images/hulk.jpg" class="card-img-top" alt="hulk"
        style="width: 98px; height: 120px;">
    </p>
    <div class="card-body">
      <h5 class="card-title">Hulk</h5>
      <p class="card-text">The Hulk is a fictional superhero appearing in publications
        by the American publisher Marvel Comics.</p>
    </div>
    <div class="card-footer">
      <small class="text-muted">Bruce Banner</small>
    </div>
  </div>
</div>
```

Card are represented by Section class in Java:

[Section](https://jdi-docs.github.io/jdi-light/#section)

Inner elements of Card Grouped can be represented by the following classes:

- [Text](https://jdi-docs.github.io/jdi-light/#text)
- [Image](https://jdi-docs.github.io/jdi-light/#image)

Available methods in Java JDI Light:

|Method | Description | Return Type
--- | --- | ---
**alt()** | Get image alt() value | String
**assertThat()** | Assert action | TextAssert
**attr()** | Assert element attribute | IsAssert
**css()** | Get element css value | String
**displayed()** | Check that element is displayed | TextAssert
**getText()** | Get element text | String
**is()** | Assert action | TextAssert
**src()** | Get image source path | String

[Bootstrap test examples](https://github.com/jdi-testing/jdi-light/blob/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/composite/section/card/CardDeckTests.java)

##### Card Columns

[Card Columns](https://getbootstrap.com/docs/4.3/components/card/#card-columns) can also be extended and customized
with some additional code. For example `.card-columns` class to generate a set of responsive tiers for changing
the number of columns.

![Card Columns Example](../../images/bootstrap/card-columns.png)

Here is an example with provided Bootstrap v4.3 code:

```java 
//@FindBy(css = ".card-columns") 
@UI(".card-columns")
public static CardColumns cardColumns; 

public class CardColumnsSection extends Section {
    @UI(".card:nth-of-type(1)") public CardWithinCardColumns topLeftCard;
    @UI(".card:nth-of-type(2)") public CardWithinCardColumns bottomLeftCard;
    @UI(".card:nth-of-type(3)") public CardWithinCardColumns topRightCard;
    @UI(".card:nth-of-type(4)") public CardWithinCardColumns middleRightCard;
    @UI(".card:nth-of-type(5)") public CardWithinCardColumns bottomRightCard;
}

public class CardWithinCardColumns extends Card {
    @UI(".card-title") public Text title;
    @UI("p:nth-of-type(1)") public Text mainText;
    @UI(".card-text small") public Text mutedText;
    @UI("footer small") public Text footerText;
    @UI(".card-img-top") public Image image;
}

@Test
public void checkElementsPositionTest() {
    assertTrue(cardColumnsSection.topLeftCard.core().getLocation().x <
            cardColumnsSection.topRightCard.core().getLocation().x);
    assertTrue(cardColumnsSection.topLeftCard.core().getLocation().y <
            cardColumnsSection.bottomLeftCard.core().getLocation().y);
    assertTrue(cardColumnsSection.topRightCard.core().getLocation().y <
            cardColumnsSection.middleRightCard.core().getLocation().y);
    assertTrue(cardColumnsSection.middleRightCard.core().getLocation().y <
            cardColumnsSection.bottomRightCard.core().getLocation().y);
    assertTrue(cardColumnsSection.bottomLeftCard.core().getLocation().x <
            cardColumnsSection.bottomRightCard.core().getLocation().x);
    assertTrue(cardColumnsSection.bottomLeftCard.core().getLocation().x <
            cardColumnsSection.middleRightCard.core().getLocation().x);
}
```

```html 
<div class="card-columns" style="column-count: 2">
  <div class="card p-3">
    <blockquote class="blockquote mb-0 card-body">
      <p>I don’t want to go.</p>
      <footer class="blockquote-footer">
        <small class="text-muted">
          Peter Parker in <cite title="Source Title">Avengers</cite>
        </small>
      </footer>
    </blockquote>
  </div>
  <div class="card">
    <img src="images/hulk.jpg" class="card-img-top" alt="hulk">
    <div class="card-body">
      <h5 class="card-title">Who is Hulk?</h5>
      <p class="card-text">..A monster man who took "Go Green" too seriously.</p>
      <p class="card-text"><small class="text-muted">Last updated 3 mins ago</small>
      </p>
    </div>
  </div>
  <div class="card bg-primary text-white text-center p-3">
    <blockquote class="blockquote mb-0">
      <p>If toast is cut diagonally, I can’t eat it.</p>
      <footer class="blockquote-footer text-white">
        <small>
          Nick Fury in <cite title="Source Title">Captain Marvel</cite>
        </small>
      </footer>
    </blockquote>
  </div>
  <div class="card text-center">
    <div class="card-body">
      <h5 class="card-title">Iron Man</h5>
      <p class="card-text">I do anything and everything that Mr. Stark requires —
        including occasionally taking out the trash.</p>
      <p class="card-text"><small class="text-muted">Last updated 3 mins ago</small>
      </p>
    </div>
  </div>
  <div class="card">
    <img src="images/punisher.jpg" class="card-img-top" alt="punisher">
  </div>
</div>
```

Card are represented by Section class in Java:

[Section](https://jdi-docs.github.io/jdi-light/#section)

Inner elements of Card Columns can be represented by the following classes:

- [Text](https://jdi-docs.github.io/jdi-light/#text)
- [Image](https://jdi-docs.github.io/jdi-light/#image)

Available methods in Java JDI Light:

|Method | Description | Return Type
--- | --- | ---
**alt()** | Assert alt image attribute | ImageAssert
**assertThat()** |	Assert action | UIAssert
**getText()**| Returns text | String
**height()** | Assert image height | ImageAssert
**is()** | Assert action | UIAssert
**src()** | Assert image src | ImageAssert
**width()** | Assert image width | ImageAssert

[Bootstrap test examples](https://github.com/jdi-testing/jdi-light/tree/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/composite/section/card/CardColumnsTests.java)

#### Jumbotron

[Jumbotron](https://getbootstrap.com/docs/4.3/components/jumbotron) – Lightweight, flexible component for showcasing hero

![Jumbotron](../../images/bootstrap/jumbotron.png)

Here is an example with provided Bootstrap v4.3 code:

```java 
// @FindBy(css = "#jumbotron")
@Css("#jumbotron")
public static Jumbotron jumbotron;

public class Jumbotron extends Section implements IsJumbotron {
    @Css(".display-4") public Text title;
    @Css(".lead") public Text description;
    @Css(".btn") public Button learnMoreBtn;
}

@Test
public void getTextTest() {
    assertEquals(jumbotron.getText(), mJumbotronWithButton);
}

@Test
public void clickTest() {
    jumbotron.learnMoreBtn.click();
    ArrayList<String> tabs = new ArrayList<>(WebDriverFactory.getDriver().getWindowHandles());
    WebDriver driver = WebDriverFactory.getDriver();
    driver.switchTo().window(tabs.get(1));
    assertEquals(getUrl(), mJumbotronUrl);
    driver.close();
    driver.switchTo().window(tabs.get(0));
} 
```

```html
<div class="jumbotron" id="jumbotron">
    <h1 class="display-4">Hello, world!</h1>
    <p class="lead">This is a simple hero unit, a simple
        jumbotron-style component for calling extra attention to
        featured content or information.</p>
    <hr class="my-4">
    <p>It uses utility classes for typography and spacing to
        space content out within the larger container.</p>
    <a class="btn btn-primary btn-lg"
       href="https://getbootstrap.com/docs/4.3/components/jumbotron/"
       target="_blank" role="button">Learn more</a>
</div>
```

Jumbotron is represented by Section class in Java:

[Section](https://jdi-docs.github.io/jdi-light/#section)

Inner elements of jumbotron can be represented by the following classes:

- [Text](https://jdi-docs.github.io/jdi-light/#text)
- [Button](https://jdi-docs.github.io/jdi-light/#button)
- [Label](https://jdi-docs.github.io/jdi-light/#label)
- [Link](https://jdi-docs.github.io/jdi-light/#link)

[See more elements](https://jdi-docs.github.io/jdi-light/#html5-common-elements)

[Bootstrap test examples](https://github.com/jdi-testing/jdi-light/tree/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/composite/section/jumbotron)

#### Dropdown
<a style="font-weight:bold" href="https://getbootstrap.com/docs/4.3/components/dropdowns/" target="_blank">Dropdowns</a> are toggleable, contextual overlays for displaying lists of links and more.

For working with Dropdown there are two classes available in JDI:

- __Java__: <a href="https://github.com/jdi-testing/jdi-light/blob/bootstrap/jdi-light-bootstrap/src/main/java/com/epam/jdi/light/ui/bootstrap/elements/composite/BootstrapDropdown.java">BootstrapDropdown</a>,
  <a href="https://github.com/jdi-testing/jdi-light/blob/bootstrap/jdi-light-bootstrap/src/main/java/com/epam/jdi/light/ui/bootstrap/elements/composite/DropdownMenu.java">DropdownMenu</a>
- __C#__: TBD

<a href="https://github.com/jdi-testing/jdi-light/blob/bootstrap/jdi-light-bootstrap/src/main/java/com/epam/jdi/light/ui/bootstrap/elements/composite/BootstrapDropdown.java">BootstrapDropdown</a> class is designed to work with Dropdown element.
<a href="https://github.com/jdi-testing/jdi-light/blob/bootstrap/jdi-light-bootstrap/src/main/java/com/epam/jdi/light/ui/bootstrap/elements/composite/DropdownMenu.java">DropdownMenu</a> class
extends <a href="https://github.com/jdi-testing/jdi-light/blob/bootstrap/jdi-light-bootstrap/src/main/java/com/epam/jdi/light/ui/bootstrap/elements/composite/BootstrapDropdown.java">BootstrapDropdown</a> class providing additional methods for working with the Dropdown menu items elements


Methods available for BootstrapDropdown class in Java JDI Light:

|Method/Property | Description | Return Type
--- | --- | ---
**assertThat()** | Assert action | BootstrapDropdownAssert
**collapse()** | Collapse dropdown | void
**collapsed()** | Assert that dropdown is collapsed | BootstrapDropdownAssert
**expand()** | Expand dropdown | void
**expanded()** | Assert that dropdown is expanded | BootstrapDropdownAssert
**expander()** | Get dropdown expander | Button
**has()** | Assert action | BootstrapDropdownAssert
**is()** | Assert action | BootstrapDropdownAssert
**isCollapsed()** | Return if dropdown expanded | boolean
**isExpanded()** | Return if dropdown expanded | boolean
**menu()** | Get dropdown menu | UIElement
**shouldBe()** | Assert action | BootstrapDropdownAssert
**verify()** | Soft assert action | BootstrapDropdownAssert
**waitFor()** | Assert action | BootstrapDropdownAssert

<br>
Additional methods available for DropdownMenu class in Java JDI Light:

|Method | Description | Return Type
--- | --- | ---
**active(int itemIndex)** | Check if item in dropdown menu is active | DropdownMenuAssert
**assertThat()** | Assert action | DropdownMenuAssert
**has()** | Assert action | DropdownMenuAssert
**hasItems(String... item)** | Return if dropdown contains all items | boolean
**hasItems(String... values)** | Asserts whether dropdown has all items from arguments | DropdownMenuAssert
**is()** | Assert action | DropdownMenuAssert
**itemValues()** | Get items text values | List<String>
**itemValues(String... values)** | Asserts whether dropdown are exactly match arguments  | DropdownMenuAssert
**list()** | Get dropdown items | WebList
**select(String item)** | Click at dropdown item | void
**select(int index)** | Click at dropdown item | void
**shouldBe()** | Assert action | DropdownMenuAssert
**verify()** | Soft assert action | DropdownMenuAssert
**waitFor()** | Assert action | DropdownMenuAssert

##### [Single button](https://getbootstrap.com/docs/4.3/components/dropdowns/#single-button)
Any single `.btn` can be turned into a dropdown toggle with some markup changes. Here’s how you can put them to work with either `<button>` elements:

![Dropdown example](../../images/bootstrap/dropdown.png)

Here is an example with provided Bootstrap v4.3 code for `<button>` elements:

```java 
//@FindBy(id = "simpleDropdown")
@UI("#simpleDropdown")
public static DropdownMenu simpleDropdown;

@Test
public void textTest() {
	simpleDropdown.assertThat()
		.core()
		.text(DROPDOWN);
	assertThat(simpleDropdown.core().getText(), is(DROPDOWN));
}

@Test
public void itemsTest() {
	simpleDropdown.expand();
	simpleDropdown.assertThat()
		.itemValues(is(Arrays.asList(ITEMS_ARR)))
		.hasItems(FIRSTITEM)
		.hasItems(SECONDITEM)
		.hasItems(LASTITEM)
		.hasItems(FIRSTITEM, LASTITEM);
	assertThat(simpleDropdown.itemValues(), is(Arrays.asList(ITEMS_ARR)));
}

@Test
public void clickTest() {
	simpleDropdown.expand();
	simpleDropdown.is()
		.expanded();
	simpleDropdown.collapse();
	simpleDropdown.is()
		.collapsed();
}
```

```html 
<div id="simpleDropdown" class="dropdown">
    <button class="btn btn-primary dropdown-toggle" type="button" 
    id="dropdownMenuButton" data-toggle="dropdown" aria-haspopup="true"
     aria-expanded="false" style="margin-bottom: 5px;">
        Dropdown
    </button>
    <div class="dropdown-menu" aria-labelledby="dropdownMenuButton" x-placement=
    "bottom-start" style="position: absolute; transform: translate3d(0px, 38px, 0px);
     top: 0px; left: 0px; will-change: transform;">
        <a class="dropdown-item" href="https://getbootstrap.com/" target="_blank">Action</a>
        <a class="dropdown-item" href="https://getbootstrap.com/docs/4.0/components/dropdowns/" target="_blank">Another
            action</a>
        <a class="dropdown-item" href="https://getbootstrap.com/docs/4.3/getting
        -started/introduction/" target="_blank">Separated link</a>
    </div>
</div>
```

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

And with `<a>` elements:

```java 
//@FindBy(id = "linkDropdown")
@UI("#linkDropdown")
public static DropdownMenu linkDropdown;

@Test
public void linkDropdownIsValidationTest() {
    linkDropdown.expander().is()
        .core()
        .tag(is("a"));
}
```

```html 
<div id="linkDropdown" class="dropdown show">
    <a class="btn btn-primary dropdown-toggle" href="https://
      getbootstrap.com/" role="button" id="dropdownMenuLink" data-toggle=
      "dropdown" aria-haspopup="true" aria-expanded="false" style="margin-bottom: 5px;">
        Dropdown link
    </a>
    <div class="dropdown-menu" aria-labelledby="dropdownMenuLink">
        <a class="dropdown-item" href="https://getbootstrap.com/docs/4.0/
        components/dropdowns/" target="_blank">Action</a>
        <a class="dropdown-item" href="https://getbootstrap.com/docs/4.0/
        components/dropdowns/" target="_blank">Another
        action</a>
        <a class="dropdown-item" href="https://getbootstrap.com/docs/4.3/
        getting-started/introduction/" target="_blank">Something else here</a>
    </div>
</div>
```

<a href="https://github.com/jdi-testing/jdi-light/blob/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/composite/dropdown/DropdownTests.java">Bootstrap test examples</a>


##### <a href="https://getbootstrap.com/docs/4.3/components/dropdowns/#split-button">Split button</a>
Similarly, create split button dropdowns with virtually the same markup as single button dropdowns, but with the addition of ``.dropdown-toggle-split`` for proper spacing around the dropdown caret.

![Split button example](../../images/bootstrap/dropdown-split.png)

Here is an example with provided Bootstrap v4.3 code:

```java 
//@FindBy(id = "splitDropdown")
@UI("#splitDropdown")
public static DropdownMenu splitDropdown;

@Test
public void splitDropdownIsValidationTest() {
    splitDropdown.expander().is()
    .core()
    .hasClass("dropdown-toggle-split");
}
```

```html
<div id="splitDropdown" class="btn-group">
    <button type="button" class="btn btn-primary" style="margin-bottom: 5px;">Action
    </button>
    <button type="button" class="btn btn-primary dropdown-toggle dropdown-toggle-split"
            data-toggle="dropdown" aria-haspopup="true" aria-expanded="false"
            style="margin-bottom: 5px;">
        <span class="sr-only">Toggle Dropdown</span>
    </button>
    <div class="dropdown-menu">
        <a class="dropdown-item"
           href="https://getbootstrap.com/docs/4.0/components/dropdowns/"
           target="_blank">Action</a>
        <a class="dropdown-item"
           href="https://getbootstrap.com/docs/4.0/components/dropdowns/" target="_blank">Another
            action</a>
        <a class="dropdown-item"
           href="https://getbootstrap.com/docs/4.3/getting-started/introduction/"
           target="_blank">Something else here</a>
    </div>
</div>
```


<a href="https://github.com/jdi-testing/jdi-light/blob/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/composite/dropdown/DropdownTests.java">Bootstrap test examples</a>

<br>

##### <a href="https://getbootstrap.com/docs/4.3/components/dropdowns/#sizing">Sizing</a>
Button dropdowns work with buttons of all sizes, including default and split dropdown buttons.

![Sizing example](../../images/bootstrap/dropdown-sizing.png)

Here is an example of Large button code:

```java 
//@FindBy(id = "largeDropdown")
public static DropdownMenu largeDropdown;
@UI("#largeSplitDropdown")

@Test
public void largeDropdownIsValidationTest() {
    largeDropdown.expander().is()
        .core()
        .hasClass("btn-lg")
        .css(PADDING, is("8px 16px"))
        .css(FONTSIZE, is("20px"))
        .css(LINEHEIGHT, is("30px"))
        .css(BORDERRADIUS, is("4.8px"));
}
```

```html 
<div id="largeDropdown" class="btn-group show">
    <button class="btn btn-primary btn-lg dropdown-toggle" type="button" data-
    toggle="dropdown" aria-haspopup="true" aria-expanded="true" style="margin-
    bottom: 5px;">
        Large button
    </button>
    <div class="dropdown-menu show" x-placement="bottom-start" style="position:
    absolute; transform: translate3d(0px, 48px, 0px); top: 0px; left: 0px; will-
    change: transform;">
        <a class="dropdown-item" href="https://getbootstrap.com/
        docs/4.0/components/dropdowns/" target="_blank">Action</a>
        <a class="dropdown-item" href="https://getbootstrap.com/
        docs/4.0/components/dropdowns/" target="_blank">Another
            action</a>
        <a class="dropdown-item" href="https://getbootstrap.com/
        docs/4.3/getting-started/introduction/"
         target="_blank">Something else here</a>
    </div>
</div>
```


Here is an example of Large split button code:

```java 
//@FindBy(id = "largeSplitDropdown")
@UI("#largeSplitDropdown")
public static DropdownMenu largeSplitDropdown;

@Test
public void largeSplitDropdownIsValidationTest() {
    largeSplitDropdown.expander().is()
        .core()
        .hasClass("btn-lg")
        .hasClass("dropdown-toggle-split")
        .css(PADDING, is("8px 12px"))
        .css(FONTSIZE, is("20px"))
        .css(LINEHEIGHT, is("30px"))
        .css(BORDERRADIUS, is("0px 4.8px 4.8px 0px"));
}
```

```html 
<div id="largeSplitDropdown" class="btn-group">
    <button class="btn btn-primary btn-lg" type="button" style="margin-bottom: 5px;">
        Large split button
    </button>
    <button type="button" class="btn btn-lg btn-primary dropdown-toggle dropdown-toggle-split" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false" style="margin-bottom: 5px;">
        <span class="sr-only">Toggle Dropdown</span>
    </button>
    <div class="dropdown-menu" x-placement="bottom-start" 
     style="position: absolute; transform: translate3d(180px, 48px, 0px);
     top: 0px; left: 0px; will-change: transform;">
        <a class="dropdown-item" href="https://getbootstrap.com/
         docs/4.0/components/dropdowns/" target="_blank">Action</a>
        <a class="dropdown-item" href="https://getbootstrap.com/
          docs/4.0/components/dropdowns/"
          target="_blank">Another action</a>
        <a class="dropdown-item" href="https://getbootstrap.com/
        docs/4.3/getting-started
        /introduction/" target="_blank">Something else here</a>
    </div>
</div>
```

<a href="https://github.com/jdi-testing/jdi-light/blob/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/composite/dropdown/DropdownTests.java">Bootstrap test examples</a>


##### <a href="https://getbootstrap.com/docs/4.3/components/dropdowns/#directions">Directions</a>
Trigger dropdown menus <a href="https://getbootstrap.com/docs/4.3/components/dropdowns/#dropup">above</a> elements by adding ``.dropup`` to the parent element.<br>
Trigger dropdown menus <a href="https://getbootstrap.com/docs/4.3/components/dropdowns/#dropright">at the right</a> of the elements by adding ``.dropright`` to the parent element.<br>
Trigger dropdown menus <a href="https://getbootstrap.com/docs/4.3/components/dropdowns/#dropleft">at the left</a> of the elements by adding ``.dropleft`` to the parent element.

![Directions example](../../images/bootstrap/dropdown-directions-example.png)

Here is an example of Dropup code:

```java 
//@FindBy(id = "dropUpDropdown")
@UI("#dropUpDropdown")
public static DropdownMenu dropUpDropdown;

@Test
public void dropUpDropdownIsValidationTest() {
    dropUpDropdown.is()
        .core()
        .hasClass("dropup");
    dropUpDropdown.menu().is()
        .core()
        .css(TOP, is("auto"))
        .css(BOTTOM, is("100%"));
}
```

```html
<div id="dropUpDropdown" class="btn-group dropup">
    <button type="button" class="btn btn-primary dropdown-toggle" data-toggle="dropdown"
            aria-haspopup="true" aria-expanded="false" style="margin-bottom: 5px;">
        Dropup
    </button>
    <div class="dropdown-menu">
        <a class="dropdown-item"
           href="https://getbootstrap.com/docs/4.0/components/dropdowns/"
           target="_blank">Action</a>
        <a class="dropdown-item"
           href="https://getbootstrap.com/docs/4.0/components/dropdowns/" target="_blank">Another
            action</a>
        <a class="dropdown-item"
           href="https://getbootstrap.com/docs/4.3/getting-started/introduction/"
           target="_blank">Something else here</a>
    </div>
</div>
```

<br>

Here is an example of Dropup split code:

```java 
//@FindBy(id = "dropUpSplitDropdown")
@UI("#dropUpSplitDropdown")
public static DropdownMenu dropUpSplitDropdown;

@Test
public void dropUpSplitDropdownIsValidationTest() {
    dropUpSplitDropdown.is()
        .core()
        .hasClass("dropup");
    dropUpSplitDropdown.menu().is()
        .core()
        .css(TOP, is("auto"))
        .css(BOTTOM, is("100%"));
    }
```

```html
<div id="dropUpSplitDropdown" class="btn-group dropup">
    <button type="button" class="btn btn-primary" style="margin-bottom: 5px;">
        Split dropup
    </button>
    <button type="button" class="btn btn-primary dropdown-toggle dropdown-toggle-split"
            data-toggle="dropdown" aria-haspopup="true" aria-expanded="false"
            style="margin-bottom: 5px;">
        <span class="sr-only">Toggle Dropdown</span>
    </button>
    <div class="dropdown-menu">
        <a class="dropdown-item"
           href="https://getbootstrap.com/docs/4.0/components/dropdowns/"
           target="_blank">Action</a>
        <a class="dropdown-item"
           href="https://getbootstrap.com/docs/4.0/components/dropdowns/" target="_blank">Another
            action</a>
        <a class="dropdown-item"
           href="https://getbootstrap.com/docs/4.3/getting-started/introduction/"
           target="_blank">Something else here</a>
    </div>
</div>
```

<br>

Here is an example of Dropright code:

```java 
//@FindBy(id = "dropRightDropdown")
@UI("#dropRightDropdown")
public static DropdownMenu dropRightDropdown;

@Test
public void dropRightDropdownIsValidationTest() {
    dropRightDropdown.is()
        .core()
        .hasClass("dropright");
    dropRightDropdown.menu().is()
        .core()
        .css(RIGHT, is("auto"))
        .css(LEFT, is("100%"));
}
```

```html
<div id="dropRightDropdown" class="btn-group dropright">
    <button type="button" class="btn btn-primary dropdown-toggle" data-toggle="dropdown"
            aria-haspopup="true" aria-expanded="false" style="margin-bottom: 5px;">
        Dropright
    </button>
    <div class="dropdown-menu">
        <a class="dropdown-item"
           href="https://getbootstrap.com/docs/4.0/components/dropdowns/"
           target="_blank">Action</a>
        <a class="dropdown-item"
           href="https://getbootstrap.com/docs/4.0/components/dropdowns/" target="_blank">Another
            action</a>
        <a class="dropdown-item"
           href="https://getbootstrap.com/docs/4.3/getting-started/introduction/"
           target="_blank">Something else here</a>
    </div>
</div>
```

<br><br>

Here is an example of Dropright split code:

```java 
//@FindBy(id = "dropRightSplitDropdown")
@UI("#dropRightSplitDropdown")
public static DropdownMenu dropRightSplitDropdown;

@Test
public void dropRightSplitDropdownIsValidationTest() {
    dropRightSplitDropdown.is()
        .core()
        .hasClass("dropright");
    dropRightSplitDropdown.menu().is()
        .core()
        .css(RIGHT, is("auto"))
        .css(LEFT, is("100%"));
    }
```

```html
<div id="dropRightSplitDropdown" class="btn-group dropright">
    <button type="button" class="btn btn-primary" style="margin-bottom: 5px;">
        Split dropright
    </button>
    <button type="button" class="btn btn-primary dropdown-toggle dropdown-toggle-split"
            data-toggle="dropdown" aria-haspopup="true" aria-expanded="false"
            style="margin-bottom: 5px;">
        <span class="sr-only">Toggle Dropright</span>
    </button>
    <div class="dropdown-menu">
        <a class="dropdown-item"
           href="https://getbootstrap.com/docs/4.0/components/dropdowns/"
           target="_blank">Action</a>
        <a class="dropdown-item"
           href="https://getbootstrap.com/docs/4.0/components/dropdowns/" target="_blank">Another
            action</a>
        <a class="dropdown-item"
           href="https://getbootstrap.com/docs/4.3/getting-started/introduction/"
           target="_blank">Something else here</a>
    </div>
</div>
```

<br>

Here is an example of Dropleft code:

```java 
//@FindBy(id = "dropLeftDropdown")
@UI("#dropLeftDropdown")
public static DropdownMenu dropLeftDropdown;

@Test
public void dropLeftDropdownIsValidationTest() {
    dropLeftDropdown.is()
        .core()
        .hasClass("dropleft");
    dropLeftDropdown.menu().is()
        .core()
        .css(LEFT, is("auto"))
        .css(RIGHT, is("100%"));
    }
```

```html
<div id="dropLeftDropdown" class="btn-group dropleft">
    <button type="button" class="btn btn-primary dropdown-toggle" data-toggle="dropdown"
            aria-haspopup="true" aria-expanded="false" style="margin-bottom: 5px;">
        Dropleft
    </button>
    <div class="dropdown-menu">
        <a class="dropdown-item"
           href="https://getbootstrap.com/docs/4.0/components/dropdowns/"
           target="_blank">Action</a>
        <a class="dropdown-item"
           href="https://getbootstrap.com/docs/4.0/components/dropdowns/" target="_blank">Another
            action</a>
        <a class="dropdown-item"
           href="https://getbootstrap.com/docs/4.3/getting-started/introduction/"
           target="_blank">Something else here</a>
    </div>
</div>
```

<br>

Here is an example of Dropleft split code:

```java 
//@FindBy(id = "dropLeftSplitDropdown")
@UI("#dropLeftSplitDropdown")
public static DropdownMenu dropLeftSplitDropdown;

@Test
public void dropLeftSplitDropdownIsValidationTest() {
    dropLeftSplitDropdown.menu().is()
        .core()
        .css(LEFT, is("auto"))
        .css(RIGHT, is("100%"));
}
```

```html 
<div id="dropLeftSplitDropdown" class="btn-group">
    <div class="btn-group dropleft" role="group">
        <button type="button" class="btn btn-primary dropdown-toggle dropdown-toggle-split" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false" style="margin-bottom: 5px;">
            <span class="sr-only">Toggle Dropleft</span>
        </button>
        <div class="dropdown-menu" x-placement="left-start" style="position: absolute; transform: translate3d(-2px, 0px, 0px); top: 0px; left: 0px; will-change: transform;">
            <a class="dropdown-item" href="https://getbootstrap.com/docs/4.0/components/dropdowns/" target="_blank">Action</a>
            <a class="dropdown-item" href="https://getbootstrap.com/docs/4.0/components/dropdowns/" target="_blank">Another action</a>
            <a class="dropdown-item" href="https://getbootstrap.com/docs/4.3/getting-started/introduction/" target="_blank">Something else here</a>
        </div>
    </div>
    <button type="button" class="btn btn-primary" style="margin-bottom: 5px;">
        Split dropleft
    </button>
</div>
```
<a href="https://github.com/jdi-testing/jdi-light/blob/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/composite/dropdown/DropdownTests.java">Bootstrap test examples</a>

<br>

##### <a href="https://getbootstrap.com/docs/4.3/components/dropdowns/#menu-items">Menu items</a>
Historically dropdown menu contents had to be links, but that’s no longer the case with v4.
Now you can optionally use ``<button>`` elements in your dropdowns instead of just ``<a>``s.


![Menu items example](../../images/bootstrap/dropdown-menu-items.png)

Here is an example of Menu items code:

```java 
//@FindBy(css = "#dropdown-menu-items")
@UI("#dropdown-menu-items")
public static DropdownMenu dropdownMenuItems;

@DataProvider(name = "actionsDataProvider")
public Object[][] actionsDataProvider() {
    return new Object[][]{
        {"Action", "Action"},
        {"Another action", "Another action"},
        {"Something else here", "One more action"}
    };
}

@Test(dataProvider = "actionsDataProvider")
public void menuItemsActionsTest(String itemText, String alertText) {
    dropdownMenuItems.expand();
    dropdownMenuItems.select(itemText);
    Alerts.validateAlert(Matchers.is(alertText));
    dropdownMenuItems.collapse();
}
```

```html 
<div class="dropdown" id="dropdown-menu-items">
    <button class="btn btn-primary dropdown-toggle" type="button" id="dropdownMenu2" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false" style="margin-bottom: 5px;">
        Menu items
    </button>
    <div class="dropdown-menu" aria-labelledby="dropdownMenu2">
        <button class="dropdown-item" type="button" onclick="alert('Action');">
            Action
        </button>
        <button class="dropdown-item" type="button" onclick="alert('Another action');">
            Another action
        </button>
        <button class="dropdown-item" type="button" onclick="alert('One more action');">
            Something else here
        </button>
    </div>
</div>
```
<br><br><br><br><br><br>
You can also create non-interactive dropdown items with ``.dropdown-item-text``. Feel free to style further with custom CSS or text utilities.

![Non-interactive items example](../../images/bootstrap/dropdown-non-interactive-items.png)

Here is an example of non-interactive dropdown items code:

```java 
//@FindBy(css = "dropdown-menu-text-item")
@UI("#dropdown-menu-text-item")
public static DropdownMenu dropdownMenuTextItem;

@Test(expectedExceptions = RuntimeException.class,
        expectedExceptionsMessageRegExp = ".*Expected: an array containing \"href\".*")
public void textItemTest() {
    dropdownMenuTextItem.expand();
    UIElement textItem = dropdownMenuTextItem.list().get("Dropdown item text");
    textItem.waitFor().enabled();
    textItem.assertThat()
        .tag("span");

    textItem.waitSec(1);
    textItem.assertThat()
        .hasAttr("href");
}
```

```html 
<div class="dropdown" id="dropdown-menu-text-item">
    <button class="btn btn-primary dropdown-toggle" type="button" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false" style="margin-bottom: 5px;">
        Menu items with non-interactive
    </button>
    <div class="dropdown-menu" x-placement="bottom-start"
     style="position: absolute; transform: translate3d(0px, 37px, 0px);
     top: 0px; left: 0px; will-change: transform;">
        <span class="dropdown-item-text">Dropdown item text</span>
        <a class="dropdown-item" href="https://getbootstrap.com/
            docs/4.3/components/dropdowns/" target="_blank">Action</a>
        <a class="dropdown-item" href="https://getbootstrap.com/
            docs/4.3/getting-started/introduction/"
             target="_blank">Another action</a>
    </div>
</div>
```

<a href="https://github.com/jdi-testing/jdi-light/blob/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/composite/dropdown/DropdownMenuItemsTest.java">Bootstrap test examples</a>

<br><br>
<a href="https://getbootstrap.com/docs/4.3/components/dropdowns/#active">**Active**</a><br>

Add ``.active`` to items in the dropdown to style them as active.

![Active example](../../images/bootstrap/dropdown-menu-items-active.png)

Here is a code example of items in the dropdown which are styled as active:

```java 
//@FindBy(css = "#dropdown-menu-items-active")
@UI("#dropdown-menu-items-active")
public static DropdownMenu dropdownMenuItemsActive;

@Test(dataProvider = "dropdownMenu")
public void dropdownMenuTest(String itemText, String itemHref) {
    dropdownMenuItemsActive.expand();
    int currWindowNum = WindowsManager.windowsCount();
    dropdownMenuItemsActive.select(itemText);
    WindowsManager.switchToWindow(currWindowNum + 1);
    String Url = WebPage.getUrl();
    assertEquals(Url, itemHref);
    WindowsManager.closeWindow();
    WindowsManager.switchToWindow(currWindowNum);
    dropdownMenuItemsActive.collapse();
}

@Test
public void isActiveTest() {
    dropdownMenuItemsActive.expand();
    dropdownMenuItemsActive.is().active(2);
    dropdownMenuItemsActive.collapse();
}
```

```html 
<div class="dropdown" id="dropdown-menu-items-active">
    <button class="btn btn-primary dropdown-toggle" type="button" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false" style="margin-bottom: 5px;">
        Menu items with active
    </button>
    <div class="dropdown-menu">
        <a class="dropdown-item" href="https://getbootstrap.com/
        docs/4.3/components/dropdowns/#active" 
        target="_blank">Action</a>
        <a class="dropdown-item active" 
        href="https://getbootstrap.com/docs/4.3/components/dropdowns/"
         target="_blank">Another action</a>
        <a class="dropdown-item" href="https://getbootstrap.com/
        docs/4.3/getting-started/introduction/"
         target="_blank">Something else here</a>
    </div>
</div>
```
<a href="https://github.com/jdi-testing/jdi-light/blob/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/composite/dropdown/DropdownActiveTests.java">Bootstrap test examples</a>
<br><br><br><br><br><br><br><br>
<a href="https://getbootstrap.com/docs/4.3/components/dropdowns/#disabled">**Disabled**</a><br>

Add ``.disabled`` to items in the dropdown to style them as disabled.

![Disabled example](../../images/bootstrap/dropdown-menu-items-disabled.png)

Here is a code example of items in the dropdown which are styled as disabled:

```java 
//@FindBy(css = "#dropdown-menu-disabled-item")
@UI("#dropdown-menu-disabled-item")
public static DropdownMenu dropdownMenuDisabledItem;

private final String DISABLED_ITEM_TEXT = "Disabled link";
private final String DISABLED_ITEM_HREF = "https://getbootstrap.com/docs/4.3/components/dropdowns/";

@Test
public void itemTest() {
    dropdownMenuDisabledItem.expand();
    dropdownMenuDisabledItem.list()
        .get(DISABLED_ITEM_TEXT)
        .assertThat()
        .tag("a")
        .attr("href", DISABLED_ITEM_HREF)
        .disabled();
    dropdownMenuDisabledItem.collapse();
}
```

```html 
<div class="dropdown" id="dropdown-menu-disabled-item">
    <button class="btn btn-primary dropdown-toggle" type="button" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false" style="margin-bottom: 5px;">
        Menu items with disabled
    </button>
    <div class="dropdown-menu">
        <a class="dropdown-item" href="https://getbootstrap.com/
           docs/4.3/components/dropdowns/" 
           target="_blank">Regular link</a>
        <a class="dropdown-item disabled"
             href="https://getbootstrap.com/docs/4.3/components/
            dropdowns/" target="_blank">Disabled link</a>
        <a class="dropdown-item" href="https://getbootstrap.com/
            docs/4.3/getting-started/introduction/"
             target="_blank">Another link</a>
    </div>
</div>
```

<a href="https://github.com/jdi-testing/jdi-light/blob/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/composite/dropdown/DisabledMenuItemTest.java">Bootstrap test examples</a>

<br>

##### <a href="https://getbootstrap.com/docs/4.3/components/dropdowns/#menu-alignment">Menu alignment</a>
By default, a dropdown menu is automatically positioned 100% from the top and along the left side of its parent. Add ``.dropdown-menu-right`` to a ``.dropdown-menu`` to right align the dropdown menu.

Here is an example of right-aligned menu:

![Right-aligned-example](../../images/bootstrap/dropdown-alignment-right.png)

Here is an example of right-aligned menu code:

```java 
//@FindBy(id = "rightAllignedDropdown")
@UI("#rightAllignedDropdown")
public static DropdownMenu rightAllignedDropdown;

@Test
public void rightAllignedDropdownIsValidationTest() {
    rightAllignedDropdown.menu().is()
        .core()
        .hasClass("dropdown-menu-right");
}
```

```html
<div id="rightAllignedDropdown" class="btn-group">
    <button type="button" class="btn btn-primary dropdown-toggle" data-toggle="dropdown"
            aria-haspopup="true" aria-expanded="false" style="margin-bottom: 5px;">
        Right-aligned menu example
    </button>
    <div class="dropdown-menu dropdown-menu-right">
        <button class="dropdown-item" type="button" onclick="alert('Action');">Action
        </button>
        <button class="dropdown-item" type="button" onclick="alert('Another action');">
            Another action
        </button>
        <button class="dropdown-item" type="button" onclick="alert('One more action');">
            Something else here
        </button>
    </div>
</div>
```

<a href="https://getbootstrap.com/docs/4.3/components/dropdowns/#responsive-alignment">**Responsive alignment**</a><br>

If you want to use responsive alignment, disable dynamic positioning by adding the<br> ``data-display="static"`` attribute and use the responsive variation classes.

To align **right** the dropdown menu with the given breakpoint or larger, add<br> ``.dropdown-menu{-sm|-md|-lg|-xl}-right``.

Here is an example of left-aligned but right aligned when large screen:

![Right-aligned-when-large-screen-example](../../images/bootstrap/dropdown-alignment-large-right.png)

Here is an example of left-aligned but right aligned when large screen code:

```html 
<div class="btn-group">
    <button type="button" class="btn btn-primary dropdown-toggle" 
    data-toggle="dropdown" data-display="static" aria-haspopup="true" aria-expanded="false" style="margin-bottom: 5px;">
        Right aligned when large screen
    </button>
    <div class="dropdown-menu dropdown-menu-lg-right">
        <button class="dropdown-item" type="button" onclick="alert('Action');">Action
        </button>
        <button class="dropdown-item" type="button" onclick="alert('Another action');">
            Another action
        </button>
        <button class="dropdown-item" type="button" onclick="alert('One more action');">
            Something else here
        </button>
    </div>
</div>
```

To align **left** the dropdown menu with the given breakpoint or larger, add<br> ``.dropdown-menu-right`` and ``.dropdown-menu{-sm|-md|-lg|-xl}-left``.

Here is an example of right-aligned but left aligned when large screen code:

```java 
//@FindBy(id = "leftAllignedDropdown")
@UI("#leftAllignedDropdown")
public static DropdownMenu leftAllignedDropdown;

@Test
public void leftAllignedDropdownIsValidationTest() {
    leftAllignedDropdown.menu().is()
        .core()
        .hasClass("dropdown-menu-lg-left")
        .css(RIGHT, is("auto"))
        .css(LEFT, is("0px"));
}
```

```html 
<div id="leftAllignedDropdown" class="btn-group">
    <button type="button" class="btn btn-primary dropdown-toggle" data-toggle="dropdown" data-display="static" aria-haspopup="true" aria-expanded="false" style="margin-bottom: 5px;">
        Left aligned when large screen
    </button>
    <div class="dropdown-menu dropdown-menu-right dropdown-menu-lg-left">
        <button class="dropdown-item" type="button" onclick="alert('Action');">Action
        </button>
        <button class="dropdown-item" type="button" onclick="alert('Another action');">
            Another action
        </button>
        <button class="dropdown-item" type="button" onclick="alert('One more action');">
            Something else here
        </button>
    </div>
</div>
```
<a href="https://github.com/jdi-testing/jdi-light/blob/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/composite/dropdown/DropdownTests.java">Bootstrap test examples</a>

<br>

##### <a href="https://getbootstrap.com/docs/4.3/components/dropdowns/#menu-content">Menu content</a>
<a href="https://getbootstrap.com/docs/4.3/components/dropdowns/#headers">**Headers**</a><br>

Add a header to label sections of actions in any dropdown menu.

![Headers example](../../images/bootstrap/dropdown-menu-content-headers.png)

Here is an example headers code in the menu items:

```java 
//@FindBy(id = "dropdown-content-header")
@UI("#dropdown-content-header")
public static DropdownMenuContent dropdownMenuContentHeader;

@Test
public void checkHeaderTest() {
    dropdownMenuContentHeader.show();
    dropdownMenuContentHeader.is().displayed();
    dropdownMenuContentHeader.expand();
    dropdownMenuContentHeader.menu().children().is().size(2);
    dropdownMenuContentHeader.header.is().core()
            .displayed()
            .tag("h6")
            .hasClass("dropdown-header")
            .text("DROPDOWN HEADER");
}
```

```html
<div class="dropdown-menu" id="dropdown-content-header">
    <h6 class="dropdown-header">Dropdown header</h6>
    <a class="dropdown-item" href="https://getbootstrap.com/"
     target="_blank">Action</a>
    <a class="dropdown-item" href="https://getbootstrap.com/docs/
     4.0/components/dropdowns/"
       target="_blank">Another action</a>
</div>
```

<a href="https://github.com/jdi-testing/jdi-light/blob/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/composite/dropdown/DropdownMenuContentTests.java">Bootstrap test examples</a>

<br><br><br><br><br><br>

<a href="https://getbootstrap.com/docs/4.3/components/dropdowns/#dividers">**Dividers**</a><br>

Separate groups of related menu items with a divider.

![Dividers example](../../images/bootstrap/dropdown-menu-content-dividers.png)

Here is an example dividers code in the menu items:

```java 
//@FindBy(id = "dropdown-content-divider")
@UI("#dropdown-content-divider")
public static DropdownMenuContent dropdownMenuContentDivider;

@Test
public void checkDividerTest() {
    dropdownMenuContentDivider.show();
    dropdownMenuContentDivider.is().displayed();
    dropdownMenuContentDivider.expand();
    dropdownMenuContentDivider.menu().children().is().size(4);
    dropdownMenuContentDivider.divider.is().core()
            .displayed()
            .tag("div")
            .hasClass("dropdown-divider");
}
```

```html
<div class="dropdown-menu" id="dropdown-content-divider">
    <a class="dropdown-item" href="https://getbootstrap.com/"
     target="_blank">Action</a>
    <a class="dropdown-item" href="https://getbootstrap.com/docs
    /4.0/components/dropdowns/"
       target="_blank">Another action</a>
    <div class="dropdown-divider"></div>
    <a class="dropdown-item"
       href="https://getbootstrap.com/docs/4.3/getting-started/
        introduction/"
       target="_blank">Separated link</a>
</div>
```
<a href="https://github.com/jdi-testing/jdi-light/blob/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/composite/dropdown/DropdownMenuContentTests.java">Bootstrap test examples</a>
<br><br><br><br>
<a href="https://getbootstrap.com/docs/4.3/components/dropdowns/#text">**Text**</a><br>

Place any freeform text within a dropdown menu with text and use <a href="https://getbootstrap.com/docs/4.3/utilities/spacing/">spacing utilities</a>. Note that you’ll likely need additional sizing styles to constrain the menu width.

![Text example](../../images/bootstrap/dropdown-menu-content-text.png)

Here is an example text code in the menu items:

```java 
//@FindBy(id = "dropdown-content-text")
@UI("#dropdown-content-text")
public static DropdownMenuContent dropdownMenuContentText;

@Test
public void checkTextTest() {
    dropdownMenuContentText.show();
    dropdownMenuContentText.is().displayed();
    dropdownMenuContentText.expand();
    dropdownMenuContentText.menu().children().is().size(2);
    dropdownMenuContentText.text.is()
           .values(TextTypes.TEXT, hasItems("Some example text that's free-flowing within the dropdown menu."));
    dropdownMenuContentText.text.is()
           .values(TextTypes.TEXT, hasItems("And this is more example text."));
}
```

```html
<div class="dropdown-menu p-4 text-muted" style="max-width: 200px;" id="dropdown-content-text">
    <p>
        Some example text that's free-flowing within the dropdown menu.
    </p>
    <p class="mb-0">
        And this is more example text.
    </p>
</div>
```
<br><br><br><br><br><br><br>
<a href="https://getbootstrap.com/docs/4.3/components/dropdowns/#forms">**Forms**</a><br>

Put a form within a dropdown menu, or make it into a dropdown menu, and use <a href="https://getbootstrap.com/docs/4.3/utilities/spacing/">margin or padding utilities</a> to give it the negative space you require.

![Form example](../../images/bootstrap/dropdown-menu-content-form.png)

Here is an example form code in the menu items:

```java 
public class DropdownForm extends DropdownMenu {
    @UI("//form") public FormDropdownLogin form;
}

@Test
public void fillTest() {
    dropdownForm.expand();

    dropdownForm.form.fill(USER);
    dropdownForm.form.check(USER);

    dropdownForm.collapse();
}

@Test
public void checkboxTests() {
    dropdownForm.expand();

    dropdownForm.form.remember.check();
    dropdownForm.form.remember.is().selected();
    dropdownForm.form.remember.uncheck();
    dropdownForm.form.remember.is().deselected();

    dropdownForm.collapse();
}

@Test
public void testButton(){
    dropdownForm.expand();

    dropdownForm.form.submit();
    validateAlert(is("Sign in"));

    dropdownForm.collapse();
}
```
```html
<div class="dropdown-menu">
    <form class="px-4 py-3">
        <div class="form-group">
            <label for="exampleDropdownFormEmail1">Email address</label>
            <input type="email" class="form-control" id="exampleDropdownFormEmail1"
                   placeholder="email@example.com">
        </div>
        <div class="form-group">
            <label for="exampleDropdownFormPassword1">Password</label>
            <input type="password" class="form-control" id="exampleDropdownFormPassword1"
                   placeholder="Password">
        </div>
        <div class="form-group">
            <div class="form-check">
                <input type="checkbox" class="form-check-input" id="dropdownCheck">
                <label class="form-check-label" for="dropdownCheck">
                    Remember me
                </label>
            </div>
        </div>
        <button type="button" class="btn btn-primary" onclick="alert('Sign in');">Sign in
        </button>
    </form>
    <div class="dropdown-divider"></div>
    <a class="dropdown-item" href="https://jdi-testing.github.io/jdi-light/index.html"
       target="_blank">New around here? Sign up</a>
    <a class="dropdown-item" href="https://jdi-testing.github.io/jdi-light/index.html"
       target="_blank">Forgot password?</a>
</div>
```


<a href="https://github.com/jdi-testing/jdi-light/blob/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/composite/dropdown/DropdownFormTest.java" target="_blank">Bootstrap Test Examples</a>

<br><br><br><br><br><br>

<a target="_blank" href="https://getbootstrap.com/docs/4.3/components/dropdowns/#dropdown-options">**Dropdown Options**</a><br>

Use ``data-offset`` or ``data-reference`` to change the location of the dropdown.

![Dropdown Options Example](../../images/bootstrap/dropdown-options.png)

```java 
//@FindBy(id = "offsetDropdown")
@UI("#offsetDropdown")
public static DropdownMenu offsetDropdown;

//@FindBy(id = "referenceDropdown")
@UI("#referenceDropdown")
public static DropdownMenu referenceDropdown;

@Test(dataProvider = "dropdownData")
public void expandCollapseTest(BootstrapDropdown dropdown) {
    dropdown.expand();
    dropdown.is().expanded();
    dropdown.collapse();
    dropdown.is().collapsed();
}

@Test
public void optionsCssTest() {
    offsetDropdown.expand();
    assertThat(offsetDropdown.core().children().get(1).getAttribute(DATA_OFFSET), is(DATA_OFFSET_VALUE));
    offsetDropdown.collapse();

    referenceDropdown.expand();
    assertThat(referenceDropdown.core().children().get(2).getAttribute(DATA_REFERENCE), is(DATA_REFERENCE_VALUE));
    referenceDropdown.collapse();
}
```

Here is an example with Bootstrap v4.3 code:

```html
<div id="referenceDropdown" class="btn-group">
    <button type="button" class="btn btn-secondary">Reference</button>
    <button type="button" class="btn btn-secondary dropdown-toggle dropdown-toggle-split" id="dropdownMenuReference" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false" data-reference="parent">
        <span class="sr-only">Toggle Dropdown</span>
    </button>
    <div class="dropdown-menu" aria-labelledby="dropdownMenuReference">
        <a class="dropdown-item" href="javascript: void();" onclick="alert('Action clicked!');">Action</a>
        <a class="dropdown-item" href="javascript: void();" onclick="alert('Another action clicked!');">Another action</a>
        <a class="dropdown-item" href="javascript: void();" onclick="alert('Something else here clicked!');">Something else here</a>
        <div class="dropdown-divider"></div>
        <a class="dropdown-item" href="javascript: void();" onclick="alert('Separated link clicked!');">Separated link</a>
    </div>
</div>
```

<a href="https://github.com/jdi-testing/jdi-light/blob/bootstrap/jdi-light-bootstrap-tests/src/test/java/io/github/epam/bootstrap/tests/composite/dropdown/DropdownOptionsTests.java" target="_blank">Bootstrap Test Examples</a>
