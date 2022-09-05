## 4. Material UI elements

### 4.1 Checkbox

```java
    // @FindBy(xpath = "//h2[text()='Basic checkboxes']/following-sibling::div/span[contains(@class,'MuiCheckbox-root')]")
    @UI("//h2[text()='Basic checkboxes']/following-sibling::div/span[contains(@class,'MuiCheckbox-root')]")
    public static List<Checkbox> basicCheckboxes;

    @Test
    public void basicCheckboxTests() {
        basicCheckboxes.forEach(this::basicCheckboxTestLogic);
    }
    
    private void basicCheckboxTestLogic(Checkbox checkbox) {
        if (checkbox.isDisabled()) {
            checkbox.is().disabled();
            if (checkbox.isChecked()) {
                checkbox.is().checked();
            } else {
                checkbox.is().unchecked();
            }
        } else {
            checkbox.is().enabled();
            if (checkbox.isUnchecked()) {
                checkbox.is().unchecked();
                checkbox.check();
                checkbox.is().checked();
            } else {
                checkbox.is().checked();
                checkbox.uncheck();
                checkbox.is().unchecked();
            }
        }
        if (checkbox.isIndeterminate()) {
            checkbox.is().indeterminate();
        }
        checkbox.has().css("color", "rgba(0, 0, 0, 0)");
    }    
```

##### <a href="https://v4.mui.com/components/checkboxes/" target="_blank"> Checkbox overview </a>

Checkbox is located in the following class:

- __Java__: _com.epam.jdi.light.material.elements.inputs.Checkbox_

__Checkbox__ - element that allows the user to select one or more items from a set. It can be used to turn an option on or off.

![Checkbox](../../images/material-ui/Checkbox.png)

Here is an example with provided Material-UI v4.12.3 code:

```html
<span class="MuiButtonBase-root MuiIconButton-root jss165 MuiCheckbox-root MuiCheckbox-colorSecondary jss166 Mui-checked MuiIconButton-colorSecondary" aria-disabled="false">
   <span class="MuiIconButton-label">
      <input class="jss168" type="checkbox" data-indeterminate="false" aria-label="primary checkbox" value="" checked="">
      <svg class="MuiSvgIcon-root" focusable="false" viewBox="0 0 24 24" aria-hidden="true">
         <path d="M19 3H5c-1.11 0-2 .9-2 2v14c0 1.1.89 2 2 2h14c1.11 0 2-.9 2-2V5c0-1.1-.89-2-2-2zm-9 14l-5-5 1.41-1.41L10 14.17l7.59-7.59L19 8l-9 9z"></path>
      </svg>
   </span>
   <span class="MuiTouchRipple-root"></span>
</span>
```
Available methods in Java JDI Light:

| Field / Method | Description | Return Type
--- | --- | ---
**icon** | Returns checkbox icon | Icon
**is()** | Returns object for work with assertions | CheckboxAssert
**isChecked()** | Checks whether checkbox is checked | boolean
**isUnchecked()** | Checks whether checkbox is unchecked | boolean
**isEnabled()** | Checks whether checkbox is enabled | boolean
**check()** | Checks checkbox | void
**uncheck()** | Unchecks checkbox | void
**label()** | Returns checkboxes label | Label
**isIndeterminate()** | Checks whether checkbox is indeterminate | boolean
**labelPosition()** | Returns checkbox label's position (top, bottom start, end) | Position

##### <a href="https://github.com/jdi-testing/jdi-light/blob/master_material_ui/jdi-light-material-ui-tests/src/test/java/io/github/epam/material/tests/inputs/CheckboxTests.java" target="_blank">Here you can find Checkbox tests</a>

<br></br>

### 4.2 Chips

```java
    // @FindBy(xpath = "//h2[text()='Chip array']/following-sibling::div//div[contains(@class, 'MuiChip-root')]")
    @UI("//h2[text()='Chip array']/following-sibling::div//div[contains(@class, 'MuiChip-root')]")
    public static List<Chip> arrayChips;
    
    @Test(dataProvider = "arrayChipsTestsDataProvider", 
            dataProviderClass = ChipDataProvider.class)
    public void arrayChipsTests(int index, String text) {
        arrayChipsTestLogic(arrayChips.get(index), text);
    }
    
    public void arrayChipsTestLogic(Chip chip, String text) {
        String clickInfoText = String.format(basicClickText + " %s", text).trim();
        chip.is().displayed();
        chip.label().has().text(text);
        chip.is().enabled();
        chip.is().clickable();
        chip.click();
        lastClickArrayInfo.has().text(clickInfoText);
        if (chip.icon().isDisplayed()) {
            chip.icon().is().displayed();
            chip.icon().click();
            lastClickArrayInfo.has().text(basicClickText);
        }
        if (chip.isDeletable()) {
            chip.is().deletable();
        }
    }
```

##### <a href="https://v4.mui.com/components/chips/" target="_blank"> Chips overview </a>

Chip is located in the following class:

- __Java__: _com.epam.jdi.light.material.elements.displaydata.Chip_

__Chips__ - compact elements that represent an input, attribute, or action. Chips allow users to enter information, make selections, filter content, or trigger actions.

![Chip](../../images/material-ui/Chip.png)

Here is an example with provided Material-UI v4.12.3 code:

```html
<h2>Chip array</h2>
<div>
  <ul class="MuiPaper-root jss13 MuiPaper-elevation1 MuiPaper-rounded">
    <li>
      <div class="MuiButtonBase-root MuiChip-root jss14 MuiChip-clickable MuiChip-deletable" tabindex="0" role="button">
        <span class="MuiChip-label">Angular</span>
        <svg class="MuiSvgIcon-root MuiChip-deleteIcon" focusable="false" viewBox="0 0 24 24" aria-hidden="true">
          <path d="M12 2C6.47 2 2 6.47 2 12s4.47 10 10 10 10-4.47 10-10S17.53 2 12 2zm5 13.59L15.59 17 12 13.41 8.41 17 7 15.59 10.59 12 7 8.41 8.41 7 12 10.59 15.59 7 17 8.41 13.41 12 17 15.59z"></path>
        </svg>
        <span class="MuiTouchRipple-root"></span>
      </div>
    </li>
    <li>
      <div class="MuiButtonBase-root MuiChip-root jss14 MuiChip-clickable MuiChip-deletable" tabindex="0" role="button">
        <span class="MuiChip-label">jQuery</span>
        <svg class="MuiSvgIcon-root MuiChip-deleteIcon" focusable="false" viewBox="0 0 24 24" aria-hidden="true">
          <path d="M12 2C6.47 2 2 6.47 2 12s4.47 10 10 10 10-4.47 10-10S17.53 2 12 2zm5 13.59L15.59 17 12 13.41 8.41 17 7 15.59 10.59 12 7 8.41 8.41 7 12 10.59 15.59 7 17 8.41 13.41 12 17 15.59z"></path>
        </svg>
        <span class="MuiTouchRipple-root"></span>
      </div>
    </li>
    <li>
      <div class="MuiButtonBase-root MuiChip-root jss14 MuiChip-clickable MuiChip-deletable" tabindex="0" role="button">
        <span class="MuiChip-label">Polymer</span>
        <svg class="MuiSvgIcon-root MuiChip-deleteIcon" focusable="false" viewBox="0 0 24 24" aria-hidden="true">
          <path d="M12 2C6.47 2 2 6.47 2 12s4.47 10 10 10 10-4.47 10-10S17.53 2 12 2zm5 13.59L15.59 17 12 13.41 8.41 17 7 15.59 10.59 12 7 8.41 8.41 7 12 10.59 15.59 7 17 8.41 13.41 12 17 15.59z"></path>
        </svg>
        <span class="MuiTouchRipple-root"></span>
      </div>
    </li>
    <li>
      <div class="MuiButtonBase-root MuiChip-root jss14 MuiChip-clickable" tabindex="0" role="button">
        <svg class="MuiSvgIcon-root MuiChip-icon" focusable="false" viewBox="0 0 24 24" aria-hidden="true">
          <path d="M11.99 2C6.47 2 2 6.48 2 12s4.47 10 9.99 10C17.52 22 22 17.52 22 12S17.52 2 11.99 2zM12 20c-4.42 0-8-3.58-8-8s3.58-8 8-8 8 3.58 8 8-3.58 8-8 8zm3.5-9c.83 0 1.5-.67 1.5-1.5S16.33 8 15.5 8 14 8.67 14 9.5s.67 1.5 1.5 1.5zm-7 0c.83 0 1.5-.67 1.5-1.5S9.33 8 8.5 8 7 8.67 7 9.5 7.67 11 8.5 11zm3.5 6.5c2.33 0 4.31-1.46 5.11-3.5H6.89c.8 2.04 2.78 3.5 5.11 3.5z"></path>
        </svg>
        <span class="MuiChip-label">React</span><span class="MuiTouchRipple-root"></span>
      </div>
    </li>
    <li>
      <div class="MuiButtonBase-root MuiChip-root jss14 MuiChip-clickable MuiChip-deletable" tabindex="0" role="button">
        <span class="MuiChip-label">Vue.js</span>
        <svg class="MuiSvgIcon-root MuiChip-deleteIcon" focusable="false" viewBox="0 0 24 24" aria-hidden="true">
          <path d="M12 2C6.47 2 2 6.47 2 12s4.47 10 10 10 10-4.47 10-10S17.53 2 12 2zm5 13.59L15.59 17 12 13.41 8.41 17 7 15.59 10.59 12 7 8.41 8.41 7 12 10.59 15.59 7 17 8.41 13.41 12 17 15.59z"></path>
        </svg>
        <span class="MuiTouchRipple-root"></span>
      </div>
    </li>
  </ul>
  <p id="lastChipArrayClickInfo">You clicked on: jQuery</p>
</div>
```

Available methods in Java JDI Light:

| Field / Method  | Description | Return Type
--- | --- | ---
**deleteIcon** | Returns chip's delete icon | Icon
**avatar** | Returns chip's avatar | Avatar
**icon** | Returns chip's icon | Icon
**is()** | Returns object for work with assertions | ChipAssert
**label()** | Returns chip's label | Label
**isClickable()** | Checks whether chip is clickable | boolean
**isDeletable()** | Checks whether chip is deletable | boolean
**isLink()** | Checks whether chip is link | boolean
**href()** | Returns chip's href attribute | String
**delete()** | Deletes chip | void

##### <a href="https://github.com/jdi-testing/jdi-light/blob/master_material_ui/jdi-light-material-ui-tests/src/test/java/io/github/epam/material/tests/displaydata/ChipTests.java" target="_blank">Here you can find Chips tests</a>

<br></br>

### 4.3 Tooltip

```java
    // @FindBy(xpath = "//h2[text()='Simple tooltips']/following-sibling::div[1]/button")
    @UI("//h2[text()='Simple tooltips']/following-sibling::div[1]/button")
    public static List<TooltipButton> simpleTooltipsButton;

    @Test(dataProvider = "simpleTooltipsTestData")
    public void simpleTooltipsTest(int number, String text) {
        checkTooltip(simpleTooltipsButton.get(number), text);
    }

    private static void checkTooltip(TooltipButton tooltipButton, String expectedText) {
        tooltipButton.hover();
        tooltipButton.tooltip().is().visible();
        tooltipButton.tooltip().has().text(containsString(expectedText));
    }
  
    @DataProvider
    public Object[][] simpleTooltipsTestData() {
        return new Object[][]{
                {1, "Delete"}, {2, "Add"}, {3, "Add"}
        };
    }
    
    public interface HasTooltip extends ICoreElement {
        default Tooltip tooltip() {
            return new Tooltip();
        }
    }
```

##### <a href="https://v4.mui.com/components/tooltips/" target="_blank"> Tooltip overview </a>

Tooltip is located in the following class:

- __Java__: _com.epam.jdi.light.material.elements.displaydata.Tooltip_

__Tooltips__ - elements that display informative text when users hover over, focus on, or tap an element.

![Tooltip](../../images/material-ui/Tooltip.png)

Here is an example with provided Material-UI v4.12.3 code:

```html
<button class="MuiButtonBase-root MuiFab-root jss183 MuiFab-primary" tabindex="0" type="button" aria-label="add" title="Add">
   <span class="MuiFab-label">
      <svg class="MuiSvgIcon-root" focusable="false" viewBox="0 0 24 24" aria-hidden="true">
         <path d="M19 13h-6v6h-2v-6H5v-2h6V5h2v6h6v2z"></path>
      </svg>
   </span>
  <span class="MuiTouchRipple-root"></span>
</button>
```

Available methods in Java JDI Light:

|Method | Description | Return Type
--- | --- | ---
**is()** | Returns object for work with assertions | TooltipAssert
**isVisible()** | Checks whether element is displayed | boolean
**isInteractive()** | Checks whether element is interactive | boolean
**getValue()** | Gets tooltip text | String

##### <a href="https://github.com/jdi-testing/jdi-light/blob/master_material_ui/jdi-light-material-ui-tests/src/test/java/io/github/epam/material/tests/displaydata/TooltipTests.java" target="_blank">Here you can find Tooltip tests</a>

<br></br>

### 4.4 Container

```java
    // @FindBy(css = ".MuiContainer-root.MuiContainer-maxWidthSm")
    @UI(".MuiContainer-root.MuiContainer-maxWidthSm")
    public static Container container;

    @Test
    public void fluidContainerTest() {
        container.has().maxWidth("600px");
        container.is().fluid();
        container.is().displayed();
        container.is().enabled();
    }
```

##### <a href="https://v4.mui.com/components/container/" target="_blank"> Container overview </a>

Container is located in the following class:

- __Java__: _com.epam.jdi.light.material.elements.layout.Container_

__Container__ - the most basic layout element. It centers your content horizontally.

![Container](../../images/material-ui/Container.png)

Here is an example with provided Material-UI v4.12.3 code:

```html
<div class="MuiContainer-root MuiContainer-maxWidthSm">
  <div class="MuiTypography-root MuiTypography-body1" style="background-color: rgb(207, 232, 252); height: 20vh;">
    Example text
  </div>
</div>
```

Available methods in Java JDI Light:

|Method | Description | Return Type
--- | --- | ---
**is()** | Returns object for work with assertions | ContainerAssert
**isFixed()** | Check whether container is fixed | boolean
**isFluid()** | Check whether container is fluid | boolean
**maxWidth()** | Returns max width of container | int


##### <a href="https://github.com/jdi-testing/jdi-light/blob/master_material_ui/jdi-light-material-ui-tests/src/test/java/io/github/epam/material/tests/layout/ContainerTests.java" target="_blank"> Here you can find Container tests </a>

<br></br>

### 4.5 Avatar

```java
    // @FindBy(className = "MuiAvatar-root")
    @UI(".MuiAvatar-root")
    public static List<Avatar> avatarsWithPhoto;

    @Test
    public void avatarsWithPhotoTests() {
        for(Avatar avatar : avatarsWithPhoto) {
            avatar.is().displayed();
            avatar.image().is().displayed();
        }
    }
```

##### <a href="https://v4.mui.com/components/avatars/" target="_blank"> Avatars overview </a>

Avatar is located in the following class:

- __Java__: _com.epam.jdi.light.material.elements.displaydata.Avatar_

__Avatars__ - graphical representations of users.

![Avatar](../../images/material-ui/Avatar.png)

Here is an example with provided Material-UI v4.12.3 code:

```html
<span class="MuiBadge-root">
   <div class="MuiAvatar-root MuiAvatar-circular">
     <img alt="Remy Sharp" src="https://v4.mui.com/static/images/avatar/1.jpg" class="MuiAvatar-img"></div>
   <span class="MuiBadge-badge jss347 MuiBadge-anchorOriginBottomRightCircular MuiBadge-dot"></span>
</span>
```

Available methods in Java JDI Light:

|Method | Description | Return Type
--- | --- | ---
**is()** | Returns object for work with assertions | AvatarAssert
**icon()** | Returns avatar's icon | Icon
**variant()** | Returns avatar's variant type | VariantType

##### <a href="https://github.com/jdi-testing/jdi-light/blob/master_material_ui/jdi-light-material-ui-tests/src/test/java/io/github/epam/material/tests/displaydata/AvatarTests.java" target="_blank">Here you can find Avatar tests</a>

<br></br>

### 4.6 Divider

```java
    // @FindBy(css = "hr.MuiDivider-root")
    @UI("hr.MuiDivider-root")
    public static Divider insetDivider;

    @Test
    public void insetDividerTest() {
        insetDivider.is().inset();
    }
```

##### <a href="https://v4.mui.com/components/dividers/" target="_blank"> Divider overview </a>

Divider is located in the following class:

- __Java__: _com.epam.jdi.light.material.elements.displaydata.Divider_

__Divider__ - a thin line that groups content in lists and layouts.

![InsetDivider](../../images/material-ui/InsetDivider.png)

Here is an example with provided Material-UI v4.12.3 code:

```html
<ul class="MuiList-root jss46 MuiList-padding">
  <li class="MuiListItem-root MuiListItem-gutters">...</li>
  <li class="MuiDivider-root MuiDivider-inset" role="separator"></li>
  <li class="MuiListItem-root MuiListItem-gutters">...</li>
  <li class="MuiDivider-root MuiDivider-inset" role="separator"></li>
  <li class="MuiListItem-root MuiListItem-gutters">...</li>
</ul>
```

Available methods in Java JDI Light:

|Method | Description | Return Type
--- | --- | ---
**is()** | Returns object for work with assertions | DividerAssert
**isInset()** | Assert inset divider | boolean
**isVertical()** | Assert vertical divider| boolean

##### <a href="https://github.com/jdi-testing/jdi-light/blob/master_material_ui/jdi-light-material-ui-tests/src/test/java/io/github/epam/material/tests/displaydata/InsetDividerTests.java" target="_blank">Here you can find Inset Divider tests</a>
##### <a href="https://github.com/jdi-testing/jdi-light/blob/master_material_ui/jdi-light-material-ui-tests/src/test/java/io/github/epam/material/tests/displaydata/VerticalDividerTests.java" target="_blank">Here you can find Vertical Divider tests</a>

<br></br>

### 4.7 Card

```java
    // @FindBy(id = "simpleCard")
    @UI("#simpleCard")
    public static SimpleCard simpleCard;

    @Test
    public void simpleCardTest() {
        simpleCard.is().displayed();
        simpleCard.has().title(Matchers.equalTo("be•nev•o•lent"));
        simpleCard.primaryText().has().text(containsString("a benevolent smile"));
        simpleCard.learnMoreButton().click();
    }
```

##### <a href="https://v4.mui.com/components/cards/" target="_blank"> Card overview </a>

Card is located in the following class:

- __Java__: _com.epam.jdi.light.material.elements.surfaces.Card_

SimpleCard subclass is located in the following class:
- __Java__: _io.github.com.custom.elements.cards.SimpleCard_

ComplexInteractionCard subclass is located in the following class:
- __Java__: _io.github.com.custom.elements.cards.ComplexInteractionCard_

__Card__ - element that contains content and actions about a single subject.

![Сard](../../images/material-ui/Card.png)

Here is an example with provided Material-UI v4.12.3 code:

```html
<div class="MuiPaper-root MuiCard-root jss160 MuiPaper-elevation1 
    MuiPaper-rounded" id="simpleCard">
  <div class="MuiCardContent-root">
    <p class="MuiTypography-root jss162 MuiTypography-body1 MuiTypography-colorTextSecondary MuiTypography-gutterBottom">
      Word of the Day
    </p>
    <h2 class="MuiTypography-root MuiTypography-h5">
      be
      <span class="jss161">•</span>
      nev
      <span class="jss161">•</span>
      o
      <span class="jss161">•</span>
      lent
    </h2>
    <p class="MuiTypography-root jss163 MuiTypography-body1 MuiTypography-colorTextSecondary">
      adjective
    </p>
    <p class="MuiTypography-root MuiTypography-body2">
      well meaning and kindly.<br>a benevolent smile
    </p>
  </div>
  <div class="MuiCardActions-root MuiCardActions-spacing">
    <button class="MuiButtonBase-root MuiButton-root MuiButton-text MuiButton-textSizeSmall MuiButton-sizeSmall" tabindex="0" type="button">
      <span class="MuiButton-label">Learn More</span>
      <span class="MuiTouchRipple-root"></span>
    </button>
  </div>
</div>
```

Available methods in Java JDI Light for Card:

|Method | Description | Return Type
--- | --- | ---
**is()** | Returns object for work with assertions | CardAssert
**actions()** | Returns element's part with action buttons | UIElement
**title()** | Returns element's title | UIElement
**subHeader()** | Returns element's sub header | UIElement

Available methods in Java JDI Light for SimpleCard:

|Method | Description | Return Type
--- | --- | ---
**primaryText()** | Returns element's primary body | UIElement
**learnMoreButton()** | Returns element's 'Learn More' button | Button

Available methods in Java JDI Light for ComplexInteractionCard:

|Method | Description | Return Type
--- | --- | ---
**textUnderImage()** | Returns element's text under image | Text
**addToFavoritesButton()** | Returns element's 'Add to Favorites' button | Button
**addToFavoritesSvgIcon()** | Returns element's 'Add to Favorites' icon | Icon
**shareButton()** | Returns element's 'Share' button | Button
**expandButton()** | Returns element's 'Expand' button | Button

##### <a href="https://github.com/jdi-testing/jdi-light/blob/master_material_ui/jdi-light-material-ui-tests/src/test/java/io/github/epam/material/tests/surfaces/CardTests.java" target="_blank">Here you can find Card tests</a>

<br></br>

### 4.8 Radio

```java
    // @FindBy(css = "#simpleRadio .MuiRadio-root")
    @UI("#simpleRadio .MuiRadio-root")
    public static RadioButtons simpleRadioButtons;

    @Test
    public void simpleRadioTest() {
        simpleRadioButtons.has().values("First", "Second", "Third", "Disabled");
        simpleRadioButtons.has().enabled("First", "Second", "Third");
        simpleRadioButtons.has().disabled("Disabled");
        asList("First", "Second", "Third").forEach(label -> {
            simpleRadioButtons.select(label);
            simpleRadioButtons.has().selected(label);
            lastRadioText.has().text(containsString(label));
        });
    }
```

##### <a href="https://v4.mui.com/components/radio-buttons/" target="_blank"> Radio overview </a>

Radio is located in the following class:

- __Java__: _com.epam.jdi.light.material.elements.inputs.RadioButtons_

__Radio buttons__ - elements that allow the user to select one option from a set.

![Radio](../../images/material-ui/Radio.png)

Here is an example with provided Material-UI v4.12.3 code:

```html
<fieldset class="MuiFormControl-root">
  <div class="MuiFormGroup-root" role="radiogroup" aria-label="gender">
    <label class="MuiFormControlLabel-root">
            <span class="MuiButtonBase-root MuiIconButton-root jss215 MuiRadio-root MuiRadio-colorSecondary MuiIconButton-colorSecondary" aria-disabled="false">
                <span class="MuiIconButton-label">
                    <input class="jss218" name="position" type="radio" value="female" checked="" />
                </span>
                <span class="MuiTouchRipple-root"></span>
            </span>
      <span class="MuiTypography-root MuiFormControlLabel-label MuiTypography-body1">First</span>
    </label>
    <label class="MuiFormControlLabel-root">
            <span class="MuiButtonBase-root MuiIconButton-root jss215 MuiRadio-root MuiRadio-colorSecondary jss216 Mui-checked MuiIconButton-colorSecondary" aria-disabled="false">
                <span class="MuiIconButton-label">
                    <input class="jss218" name="position" type="radio" value="male" />
                </span>
                <span class="MuiTouchRipple-root"></span>
            </span>
      <span class="MuiTypography-root MuiFormControlLabel-label MuiTypography-body1">Second</span>
    </label>
    <label class="MuiFormControlLabel-root">
            <span class="MuiButtonBase-root MuiIconButton-root jss215 MuiRadio-root MuiRadio-colorSecondary MuiIconButton-colorSecondary" aria-disabled="false">
                <span class="MuiIconButton-label">
                    <input class="jss218" name="position" type="radio" value="other" />
                </span>
                <span class="MuiTouchRipple-root"></span>
            </span>
      <span class="MuiTypography-root MuiFormControlLabel-label MuiTypography-body1">Third</span>
    </label>
    <label class="MuiFormControlLabel-root Mui-disabled">
            <span class="MuiButtonBase-root MuiIconButton-root jss215 MuiRadio-root MuiRadio-colorSecondary jss217 Mui-disabled MuiIconButton-colorSecondary Mui-disabled Mui-disabled" tabindex="-1" aria-disabled="true">
                <span class="MuiIconButton-label">
                    <input class="jss218" disabled="" name="position" type="radio" value="disabled" />
                </span>
            </span>
      <span class="MuiTypography-root MuiFormControlLabel-label Mui-disabled MuiTypography-body1">Disabled</span>
    </label>
  </div>
</fieldset>
```

Available methods in Java JDI Light:

|Method | Description | Return Type
--- | --- | ---
**is()** | Returns object for work with assertions | RadioAssert
**label(String)** | Get label of radiobutton by value | UIElement
**labels()** | Returns list of labels | List<Label>
**values()** | Returns list of values | List<String>
**get(String)** | Returns radio button by value | UIElement
**select(String)** | Select radiobutton by value  | void
**selected()** | Get selected radiobutton value | String
**selected(String/int)** | Check whether specified radio button is selected | boolean
**listEnabled()** | Returns list of enabled values | List<String>
**listDisabled()** | Returns list of disabled values | List<String>

##### <a href="https://github.com/jdi-testing/jdi-light/blob/master_material_ui/jdi-light-material-ui-tests/src/test/java/io/github/epam/material/tests/inputs/RadioButtonsTests.java" target="_blank">Here you can find Radio tests</a>

<br></br>

### 4.9 App Bar

```java
    // @FindBy(css = ".MuiAppBar-root[1]")
    @UI(".MuiAppBar-root[1]")
    public static AppBar simpleAppBar;

    @Test
    public void simpleAppBarTest() {
        simpleAppBar.is().displayed();
        simpleAppBar.title().has().text("News");
        simpleAppBar.buttonGroup().is().displayed().and().has().buttons(2);
    }
```

##### <a href="https://v4.mui.com/components/app-bar/" target="_blank"> App Bar overview </a>

App Bar is located in the following class:

- __Java__: _com.epam.jdi.light.material.elements.surfaces.AppBar_

__App Bar__ - element that displays information and actions relating to the current screen.

![AppBar](../../images/material-ui/AppBar.png)

Here is an example with provided Material-UI v4.12.3 code:

```html
<header class="MuiPaper-root MuiAppBar-root MuiAppBar-positionStatic MuiAppBar-colorPrimary MuiPaper-elevation4">
  <div class="MuiToolbar-root MuiToolbar-regular MuiToolbar-gutters">
    <button class="MuiButtonBase-root MuiIconButton-root jss172 MuiIconButton-colorInherit MuiIconButton-edgeStart" tabindex="0" type="button" aria-label="menu">
         <span class="MuiIconButton-label">
            <svg class="MuiSvgIcon-root" focusable="false" viewBox="0 0 24 24" aria-hidden="true">
               <path d="M3 18h18v-2H3v2zm0-5h18v-2H3v2zm0-7v2h18V6H3z"></path>
            </svg>
         </span>
      <span class="MuiTouchRipple-root"></span>
    </button>
    <h6 class="MuiTypography-root jss173 MuiTypography-h6">News</h6>
    <button class="MuiButtonBase-root MuiButton-root MuiButton-text MuiButton-colorInherit" tabindex="0" type="button">
      <span class="MuiButton-label">Login</span>
      <span class="MuiTouchRipple-root"></span>
    </button>
  </div>
</header>
```

Available methods in Java JDI Light:

|Method | Description | Return Type
--- | --- | ---
**buttonGroup()** | Returns the app bar buttons | ButtonGroup
**title()** | Returns app bar title | Text
**searchField()** | Returns app bar search field | TextField
**is()** | Returns object for work with assertions | TextAssert

##### <a href="https://github.com/jdi-testing/jdi-light/blob/master_material_ui/jdi-light-material-ui-tests/src/test/java/io/github/epam/material/tests/surfaces/AppBarTests.java" target="_blank">Here you can find AppBar tests</a>

<br></br>

### 4.10 Transitions

```java
    // @FindBy(xpath = "//h2[text()='Collapse']/following::div[contains(@class,'MuiCollapse-root')]")
    @UI("//h2[text()='Collapse']/following::div[contains(@class,'MuiCollapse-root')]")
    public static List<Transition> collapseTransitions;

    // @FindBy(css = "span.MuiSwitch-root")
    @UI("span.MuiSwitch-root")
    public static List<Switch> switches;
    
    @Test
    public void collapseDisplayTest() {
        switches.get(1).check();
      
        collapseTransitions.get(1).is().displayed();
        collapseTransitions.get(2).is().displayed();
      
        switches.get(1).uncheck();
      
        collapseTransitions.get(1).is().hidden();
        collapseTransitions.get(2).is().displayed();
    }
```

##### <a href="https://v4.mui.com/components/transitions/" target="_blank"> Transitions overview </a>

Transitions is located in the following class:

- __Java__: _com.epam.jdi.light.material.elements.utils.Transition_

__Transitions__ - element that can be used to introduce some basic motion to your applications. 

It helps make a UI expressive and easy to use.

![Transitions](../../images/material-ui/Transitions.png)

Here is an example with provided Material-UI v4.12.3 code:

```html
<div class="jss257">
  <label class="MuiFormControlLabel-root">
    <span class="MuiSwitch-root">
      <span class="MuiButtonBase-root MuiIconButton-root jss262 MuiSwitch-switchBase MuiSwitch-colorSecondary" aria-disabled="false">
        <span class="MuiIconButton-label">
          <input class="jss265 MuiSwitch-input" type="checkbox" value="">
          <span class="MuiSwitch-thumb"></span></span>
        <span class="MuiTouchRipple-root"></span></span>
      <span class="MuiSwitch-track"></span></span>
    <span class="MuiTypography-root MuiFormControlLabel-label MuiTypography-body1">Show</span>
  </label>
  <div class="jss258">
    <div class="MuiCollapse-root MuiCollapse-hidden" style="min-height: 0px; height: 0px; transition-duration: 300ms;">
      <div class="MuiCollapse-wrapper">
        <div class="MuiCollapse-wrapperInner">
          <div class="MuiPaper-root jss259 MuiPaper-elevation4 MuiPaper-rounded">
            <svg class="jss260">
              <polygon points="0,100 50,00, 100,100" class="jss261"></polygon>
            </svg>
          </div>
        </div>
      </div>
    </div>
    <div class="MuiCollapse-root" style="min-height: 40px; height: 40px; transition-duration: 300ms;">
      <div class="MuiCollapse-wrapper">
        <div class="MuiCollapse-wrapperInner">
          <div class="MuiPaper-root jss259 MuiPaper-elevation4 MuiPaper-rounded">
            <svg class="jss260">
              <polygon points="0,100 50,00, 100,100" class="jss261"></polygon>
            </svg>
          </div>
        </div>
      </div>
    </div>
  </div>
</div>
```

Available methods in Java JDI Light:

|Method | Description | Return Type
--- | --- | ---
**is()** | Returns object for work with assertions | TransitionAssert
**isEntered()** | Checks whether transition is entered | boolean
**isHidden()** | Checks whether transition is hidden | boolean
**isExited()** | Checks whether transition is exited | boolean
**isDisplayed()** | Checks whether transition is displayed | boolean

##### <a href="https://github.com/jdi-testing/jdi-light/blob/master_material_ui/jdi-light-material-ui-tests/src/test/java/io/github/epam/material/tests/utils/TransitionTests.java" target="_blank">Here you can find Transitions tests</a>

<br></br>

### 4.11 Material Icons

```java
    // @FindBy(xpath = "//h2[text()='Access Alarm']/following::*[name()='svg']")
    @UI("//h2[text()='Access Alarm']/following::*[name()='svg']")
    public static List<Icon> iconsList;

    // @FindBy(id = "miconLastClick")
    @UI("#miconLastClick")
    public static Text lastClick;

    // @FindBy(id = "miconLastHover")
    @UI("#miconLastHover")
    public static Text lastHover;

    @Test(dataProvider = "defaultMaterialIconTestDataProvider")
    public void defaultMaterialIconTest(int elNum, String elType) {

        lastClick.is().text("Last click:");
        lastHover.is().text("Last hover:");

        iconsList.get(elNum).click();
        lastClick.is().text("Last click: " + elType);
        iconsList.get(elNum).hover();
        lastHover.is().text("Last hover: " + elType);
    }

    @DataProvider(name = "defaultMaterialIconTestDataProvider")
    public static Object[][] defaultMaterialIconTestData() {
        return new Object[][]{
                {1, "default"},
                {2, "large"},
                {3, "secondary"},
        };
    }
```

##### <a href="https://v4.mui.com/components/material-icons/" target="_blank"> Material Icons overview </a>

__Material Icons__ - set of icons provided by npm package, @material-ui/icons, that includes the 1,100+ official Material icons converted to SvgIcon components.

![Material Icons](../../images/material-ui/MaterialIcons.png)

Here is an example with provided Material-UI v4.12.3 code:

```html
<svg class="MuiSvgIcon-root jss225" focusable="false" viewBox="0 0 24 24" aria-hidden="true" tabindex="-1" title="AccessAlarm" data-ga-event-category="material-icons" data-ga-event-action="click" data-ga-event-label="AccessAlarm">
  <path d="M22 5.72l-4.6-3.86-1.29 1.53 4.6 3.86L22 5.72zM7.88 3.39L6.6 1.86 2 5.71l1.29 1.53 4.59-3.85zM12.5 8H11v6l4.75 2.85.75-1.23-4-2.37V8zM12 4c-4.97 0-9 4.03-9 9s4.02 9 9 9c4.97 0 9-4.03 9-9s-4.03-9-9-9zm0 16c-3.87 0-7-3.13-7-7s3.13-7 7-7 7 3.13 7 7-3.13 7-7 7z"></path>
</svg>
```

##### <a href="https://github.com/jdi-testing/jdi-light/blob/master_material_ui/jdi-light-material-ui-tests/src/test/java/io/github/epam/material/tests/displaydata/MaterialIconTests.java" target="_blank">Here you can find Material Icons tests</a>

<br></br>

### 4.12 Icons

```java
    // FindBy(xpath = "//div[contains(@class, 'MuiGrid-grid-xs-8')]/*[local-name()='svg']")
    @UI(".MuiGrid-grid-xs-8 > svg")
    public static List<Icon> simpleIcons;
    
    // @FindBy(id = "simpleLastClick")
    @UI("#simpleLastClick")
    public static Text simpleLastClick;

    // @FindBy(id = "simpleLastHover")
    @UI("#simpleLastHover")
    public static Text simpleLastHover;

    @Test
    public void simpleIconsTest() {
        simpleIcons.get(1).is().displayed();
        simpleIcons.get(1).hover();
        simpleLastHover.has().text("Last hover: DeleteIcon");
        simpleIcons.get(2).click();
        simpleLastClick.has().text("Last click: DeleteForeverIcon");
    }
```

##### <a href="https://v4.mui.com/components/icons/" target="_blank"> Icons overview </a>

Icon is located in the following class:

- __Java__: _com.epam.jdi.light.material.elements.displaydata.Icon_

__Icon__ - element that represents a small clickable  picture.

![Icons](../../images/material-ui/Icon.png)

Here is an example with provided Material-UI v4.12.3 code:

```html
<div class="MuiGrid-root MuiGrid-item MuiGrid-grid-xs-8">
  <svg class="MuiSvgIcon-root" focusable="false" viewBox="0 0 24 24" aria-hidden="true">
    <path d="M6 19c0 1.1.9 2 2 2h8c1.1 0 2-.9 2-2V7H6v12zM19 4h-3.5l-1-1h-5l-1 1H5v2h14V4z"></path>
  </svg>
  <svg class="MuiSvgIcon-root" focusable="false" viewBox="0 0 24 24" aria-hidden="true">
    <path d="M6 19c0 1.1.9 2 2 2h8c1.1 0 2-.9 2-2V7H6v12zm2.46-7.12l1.41-1.41L12 12.59l2.12-2.12 1.41 1.41L13.41 14l2.12 2.12-1.41 1.41L12 15.41l-2.12 2.12-1.41-1.41L10.59 14l-2.13-2.12zM15.5 4l-1-1h-5l-1 1H5v2h14V4z"></path>
  </svg>
</div>
<p id="simpleLastClick">Last click: DeleteOutlinedIcon</p>
<p id="simpleLastHover">Last hover: DeleteForeverIcon</p>
```

Available methods in Java JDI Light:

|Method | Description | Return Type
--- | --- | ---
**is()** | Returns object for work with assertions | IconAssert

##### <a href="https://github.com/jdi-testing/jdi-light/blob/master_material_ui/jdi-light-material-ui-tests/src/test/java/io/github/epam/material/tests/displaydata/IconsTests.java" target="_blank">Here you can find Icons tests</a>

<br></br>

### 4.13 Floating Action Button

```java
    // @FindBy(xpath = "//button[@aria-label='add']")
    @UI("//button[@aria-label='add']")
    public static Button buttonAdd;
    
    // @FindBy(xpath = "//button[@aria-label='like']")
    @UI("//button[@aria-label='like']")
    public static Button buttonLike;
    
    @Test
    public void basicButtonsTest() {
        buttonAdd.is().displayed().and().is().enabled();

        buttonLike.is().displayed().and().is().disabled();
    }
```

##### <a href="https://v4.mui.com/components/floating-action-button/" target="_blank"> Floating Action Button overview </a>

__Floating Action Button__ - element that appears in front of all screen content, typically as a circular shape with an icon in its center. 

![Floating action button](../../images/material-ui/Fab.png)

Here is an example with provided Material-UI v4.12.3 code:

```html
<div class="jss150">
  <button class="MuiButtonBase-root MuiFab-root MuiFab-primary" tabindex="0" type="button" aria-label="add">
      <span class="MuiFab-label">
         <svg class="MuiSvgIcon-root" focusable="false" viewBox="0 0 24 24" aria-hidden="true">
            <path d="M19 13h-6v6h-2v-6H5v-2h6V5h2v6h6v2z"></path>
         </svg>
      </span>
    <span class="MuiTouchRipple-root"></span>
  </button>
  <button class="MuiButtonBase-root MuiFab-root Mui-disabled Mui-disabled" tabindex="-1" type="button" disabled="" aria-label="like">
      <span class="MuiFab-label">
         <svg class="MuiSvgIcon-root" focusable="false" viewBox="0 0 24 24" aria-hidden="true">
            <path d="M12 21.35l-1.45-1.32C5.4 15.36 2 12.28 2 8.5 2 5.42 4.42 3 7.5 3c1.74 0 3.41.81 4.5 2.09C13.09 3.81 14.76 3 16.5 3 19.58 3 22 5.42 22 8.5c0 3.78-3.4 6.86-8.55 11.54L12 21.35z"></path>
         </svg>
      </span>
  </button>
</div>
```

##### <a href="https://github.com/jdi-testing/jdi-light/blob/master_material_ui/jdi-light-material-ui-tests/src/test/java/io/github/epam/material/tests/inputs/FloatingActionButtonTests.java" target="_blank">Here you can find Floating Action Button tests</a>

<br></br>

### 4.14 Hidden

```java
    // @FindBy(className = "MuiTypography-subtitle1")
    @UI(".MuiTypography-subtitle1")
    public static Text currentWidth;

    // @FindBy(className = "MuiPaper-root")
    @UI(".MuiPaper-root")
    public static WebList papers;
    
    @Test(dataProvider = "Screen Width")
    public void hiddenTestWithScreenWidthDifferentScreenWidth(int width, int size, String expectedWidth) {
        setWidth(width);
        papers.has().size(size);
        if (size > 0) {
            papers.is().displayed();
        } else {
            papers.is().hidden();
        }
        currentWidth.has().text("Current width: " + expectedWidth);
    }

    @DataProvider(name = "Screen Width")
    public Object[][] screenWidthDividers() {
        return new Object[][]{
            {599, 0, "xs"},
            {600, 1, "sm"},
            {959, 1, "sm"},
            {960, 2, "md"},
            {1279, 2, "md"},
            {1280, 3, "lg"},
            {1919, 3, "lg"},
            {1920, 4, "xl"}};
    }
```

##### <a href="https://v4.mui.com/components/hidden/" target="_blank"> Hidden overview </a>

__Hidden__ - element that allows you to quickly and responsively toggle the visibility value of components and much more.

![Hidden](../../images/material-ui/Hidden.png)

Here is an example with provided Material-UI v4.12.3 code:

```html
<div class="jss145">
  <h6 class="MuiTypography-root MuiTypography-subtitle1">Current width: lg</h6>
  <div class="jss146">
    <div class="MuiPaper-root jss147 MuiPaper-elevation1 MuiPaper-rounded">xsDown</div>
    <div class="MuiPaper-root jss147 MuiPaper-elevation1 MuiPaper-rounded">smDown</div>
    <div class="MuiPaper-root jss147 MuiPaper-elevation1 MuiPaper-rounded">mdDown</div>
  </div>
</div>
```

##### <a href="https://github.com/jdi-testing/jdi-light/blob/master_material_ui/jdi-light-material-ui-tests/src/test/java/io/github/epam/material/tests/layout/HiddenTests.java" target="_blank">Here you can find Hidden tests</a>

<br></br>

### 4.15 Stepper

```java
    // @FindBy(class = "MuiStep-root")
    @UI(".MuiStep-root")
    public static DesktopStepper nonlinearStepper;

    @Test
    public void nonlinearStepperForwardTest() {
        String[] stepsLabels = {"Step #1", "Step #2", "Step #3"};
        
        nonlinearStepper.show();
        nonlinearStepper.is().displayed().and().has().steps(stepsLabels);
        
        nonlinearStepper.step(stepsLabels[0]).is().enabled().and().incomplete();
        nonlinearStepper.step(stepsLabels[1]).is().disabled().and().incomplete();
        nonlinearStepper.step(stepsLabels[2]).is().disabled().and().incomplete();
        
        nonlinearStepper.buttonGroup().button(3).click();
        nonlinearStepper.buttonGroup().button(3).click();
        nonlinearStepper.buttonGroup().button(2).click();
        nonlinearStepper.step(stepsLabels[0]).is().enabled().and().completed();
        nonlinearStepper.step(stepsLabels[1]).is().enabled().and().completed();
        nonlinearStepper.step(stepsLabels[2]).is().enabled().and().incomplete();
        
        nonlinearStepper.step(stepsLabels[1]).click();
        nonlinearStepper.step(stepsLabels[0]).is().enabled().and().completed();
        nonlinearStepper.step(stepsLabels[1]).is().enabled().and().completed();
        nonlinearStepper.step(stepsLabels[2]).is().disabled().and().incomplete();
  }
```

##### <a href="https://v4.mui.com/components/steppers/" target="_blank"> Stepper overview </a>

Stepper is located in the following class:

- __Java__: _com.epam.jdi.light.material.elements.navigation.Stepper_

__Stepper__ - element that allows you to convey progress through numbered steps.

![Stepper](../../images/material-ui/Stepper.png)

Here is an example with provided Material-UI v4.12.3 code:

```html
<div class="jss220">
  <div class="MuiPaper-root MuiStepper-root MuiStepper-horizontal MuiPaper-elevation0">
    <div class="MuiStep-root MuiStep-horizontal">
      <button class="MuiButtonBase-root MuiStepButton-root MuiStepButton-horizontal" tabindex="0" type="button">
            <span class="MuiStepLabel-root MuiStepLabel-horizontal">
               <span class="MuiStepLabel-iconContainer">
                  <svg class="MuiSvgIcon-root MuiStepIcon-root MuiStepIcon-active" focusable="false" viewBox="0 0 24 24" aria-hidden="true">
                     <circle cx="12" cy="12" r="12"></circle>
                     <text class="MuiStepIcon-text" x="12" y="16" text-anchor="middle">1</text>
                  </svg>
               </span>
               <span class="MuiStepLabel-labelContainer"><span class="MuiTypography-root MuiStepLabel-label MuiStepLabel-active MuiTypography-body2 MuiTypography-displayBlock">Step #1</span></span>
            </span>
        <span class="MuiTouchRipple-root MuiStepButton-touchRipple"></span>
      </button>
    </div>
    <div class="MuiStepConnector-root MuiStepConnector-horizontal"><span class="MuiStepConnector-line MuiStepConnector-lineHorizontal"></span></div>
    <div class="MuiStep-root MuiStep-horizontal">
      <button class="MuiButtonBase-root MuiStepButton-root MuiStepButton-horizontal" tabindex="0" type="button">
            <span class="MuiStepLabel-root MuiStepLabel-horizontal">
               <span class="MuiStepLabel-iconContainer">
                  <svg class="MuiSvgIcon-root MuiStepIcon-root" focusable="false" viewBox="0 0 24 24" aria-hidden="true">
                     <circle cx="12" cy="12" r="12"></circle>
                     <text class="MuiStepIcon-text" x="12" y="16" text-anchor="middle">2</text>
                  </svg>
               </span>
               <span class="MuiStepLabel-labelContainer"><span class="MuiTypography-root MuiStepLabel-label MuiTypography-body2 MuiTypography-displayBlock">Step #2</span></span>
            </span>
        <span class="MuiTouchRipple-root MuiStepButton-touchRipple"></span>
      </button>
    </div>
    <div class="MuiStepConnector-root MuiStepConnector-horizontal"><span class="MuiStepConnector-line MuiStepConnector-lineHorizontal"></span></div>
    <div class="MuiStep-root MuiStep-horizontal">
      <button class="MuiButtonBase-root MuiStepButton-root MuiStepButton-horizontal" tabindex="0" type="button">
            <span class="MuiStepLabel-root MuiStepLabel-horizontal">
               <span class="MuiStepLabel-iconContainer">
                  <svg class="MuiSvgIcon-root MuiStepIcon-root" focusable="false" viewBox="0 0 24 24" aria-hidden="true">
                     <circle cx="12" cy="12" r="12"></circle>
                     <text class="MuiStepIcon-text" x="12" y="16" text-anchor="middle">3</text>
                  </svg>
               </span>
               <span class="MuiStepLabel-labelContainer"><span class="MuiTypography-root MuiStepLabel-label MuiTypography-body2 MuiTypography-displayBlock">Step #3</span></span>
            </span>
        <span class="MuiTouchRipple-root MuiStepButton-touchRipple"></span>
      </button>
    </div>
  </div>
  <div>
    <div>
      <p class="MuiTypography-root jss223 MuiTypography-body1">You are on Step #1</p>
      <div><button class="MuiButtonBase-root MuiButton-root MuiButton-text jss221 Mui-disabled Mui-disabled" tabindex="-1" type="button" disabled=""><span class="MuiButton-label">Back</span></button><button class="MuiButtonBase-root MuiButton-root MuiButton-contained jss221 MuiButton-containedPrimary" tabindex="0" type="button"><span class="MuiButton-label">Next</span><span class="MuiTouchRipple-root"></span></button><button class="MuiButtonBase-root MuiButton-root MuiButton-contained MuiButton-containedPrimary" tabindex="0" type="button"><span class="MuiButton-label">Complete Step</span><span class="MuiTouchRipple-root"></span></button></div>
    </div>
  </div>
</div>
```

Available methods in Java JDI Light for DesktopStepper:

|Method | Description | Return Type
--- | --- | ---
**currentIndex()** | Get current step index | int
**maxIndex()** | Get max steps number | int
**buttonGroup()** | Get element's buttons | ButtonGroup
**step(int)** | Get step by index | Step
**step(String)** | Get step by label | Step
**steps()** | Get all steps | List<Step>
**hasStep(int)** | Check that step with given index exists | boolean 
**hasStep(String)** | Check that step with given label exists | boolean 
**hasAllStepsCompleted()** | Check that all steps are completed | boolean 
**hasAllStepsIncomplete()** | Check that all steps are incomplete | boolean 
**hasStepCompleted(int)** | Check that step with given index is completed | boolean 
**is()** | Returns object for work with assertions | DesktopStepperAssert

Available methods in Java JDI Light for MobileStepper:

|Method | Description | Return Type
--- | --- | ---
**currentIndex()** | Get current step index | int
**maxIndex()** | Get max steps number | int
**backButton()** | Get 'Back' button | Button
**nextButton()** | Get 'Next' button | Button
**is()** | Returns object for work with assertions | MobileStepperAssert

##### <a href="https://github.com/jdi-testing/jdi-light/blob/master_material_ui/jdi-light-material-ui-tests/src/test/java/io/github/epam/material/tests/navigation/StepperTests.java" target="_blank">Here you can find Stepper tests</a>

<br></br>

### 4.16 Slider

```java
    // @FindBy(id = "continuousSlider")
    @UI("#continuousSlider")
    public static Slider continuousSlider;

    @Test
    public void continuousSliderTest() {
        continuousSlider.show();
        continuousSlider.is().enabled()
              .and().has().orientation(HORIZONTAL)
              .and().type(CONTINUOUS)
              .and().value("30");
        continuousSlider.track().is().visible();
        continuousSlider.setValue("71");
        continuousSlider.has().value("71");
    }
```

##### <a href="https://v4.mui.com/components/slider/" target="_blank"> Slider overview </a>

Slider is located in the following class:

- __Java__: _com.epam.jdi.light.material.elements.inputs.Slider_

__Slider__ - element that reflects a range of values along a bar, from which users may select a single value. 

It is ideal for adjusting settings such as volume, brightness, or applying image filters.

![Slider](../../images/material-ui/Slider.png)

Here is an example with provided Material-UI v4.12.3 code:

```html
<div class="MuiGrid-root MuiGrid-item MuiGrid-grid-xs-true">
  <span class="MuiSlider-root MuiSlider-colorPrimary" id="continuousSlider">
    <span class="MuiSlider-rail"></span>
    <span class="MuiSlider-track" style="left: 0%; width: 40%;"></span>
    <input type="hidden" value="40">
    <span class="MuiSlider-thumb MuiSlider-thumbColorPrimary" tabindex="0" role="slider" data-index="0" aria-labelledby="continuous-slider" aria-orientation="horizontal" aria-valuemax="100" aria-valuemin="0" aria-valuenow="40" style="left: 40%;"></span>
  </span>
</div>
```

Available methods in Java JDI Light:

|Method | Description | Return Type
--- | --- | ---
**thumb()** | Returns slider thumb | UIElement
**setValue(int)** | Set new value | void
**setValue(double)** | Set new value | void
**setValue(String)** | Set new value | void
**value()** | Get thumb value | String
**dragAndDropThumbTo(String)** | Perform drag and drop to given value | void
**is()** | Returns object for work with assertions | SliderAssert

##### <a href="https://github.com/jdi-testing/jdi-light/blob/master_material_ui/jdi-light-material-ui-tests/src/test/java/io/github/epam/material/tests/inputs/SliderTests.java" target="_blank">Here you can find Slider tests</a>

<br></br>

### 4.17 Tabs

```java
    // @FindBy(css = "h2+div[1] .MuiTab-root")
    @UI("h2+div[1] .MuiTab-root")
    public static Tabs simpleTabs;
    
    @Test
    public void simpleTabTest() {
        simpleTabs.has().values(equalTo(asList("ITEM ONE", "ITEM TWO", "ITEM THREE", "ITEM FOUR", "ITEM FIVE")));
        simpleTabs.has().selected(1);
        simpleTabs.select(2);
        simpleTabs.has().selected(2);
        simpleTabs.has().disabled(4);
        simpleTabs.has().size(5);
    }
```

##### <a href="https://material-ui.com/components/Tabs/" target="_blank"> Tabs overview </a>

Tabs is located in the following class:

- __Java__: _com.epam.jdi.light.material.elements.navigation.Tabs_

__Tabs__ - elements that organize and allow navigation between groups of content that are related and at the same level of hierarchy.

![Tabs](../../images/material-ui/Tabs.png)

Here is an example with provided Material-UI v4.12.3 code:

```html
<div aria-label="simple tabs example" class="MuiTabs-flexContainer" role="tablist">
  <button class="MuiButtonBase-root MuiTab-root MuiTab-textColorInherit Mui-selected" tabindex="0" type="button" role="tab" aria-selected="true" id="simple-tab-0" aria-controls="simple-tabpanel-0">
    <span class="MuiTab-wrapper">Item One</span>
    <span class="MuiTouchRipple-root"></span>
  </button>
  <button class="MuiButtonBase-root MuiTab-root MuiTab-textColorInherit" tabindex="-1" type="button" role="tab" aria-selected="false" id="simple-tab-1" aria-controls="simple-tabpanel-1">
    <span class="MuiTab-wrapper">Item Two</span>
    <span class="MuiTouchRipple-root"></span>
  </button>
  <button class="MuiButtonBase-root MuiTab-root MuiTab-textColorInherit" tabindex="-1" type="button" role="tab" aria-selected="false" id="simple-tab-2" aria-controls="simple-tabpanel-2">
    <span class="MuiTab-wrapper">Item Three</span>
    <span class="MuiTouchRipple-root"></span>
  </button>
  <button class="MuiButtonBase-root MuiTab-root MuiTab-textColorInherit Mui-disabled Mui-disabled" tabindex="-1" type="button" disabled="" role="tab" aria-selected="false" id="simple-tab-3" aria-controls="simple-tabpanel-3">
    <span class="MuiTab-wrapper">Item Four</span>
  </button>
  <button class="MuiButtonBase-root MuiTab-root MuiTab-textColorInherit" tabindex="-1" type="button" role="tab" aria-selected="false" id="simple-tab-4" aria-controls="simple-tabpanel-4">
    <span class="MuiTab-wrapper">Item Five</span>
    <span class="MuiTouchRipple-root"></span>
  </button>
</div>
```

Available methods in Java JDI Light:

|Method | Description | Return Type
--- | --- | ---
**is()** | Returns object for work with assertions | TabsAssert
**enabled(int)** | Check whether tab is enabled | boolean
**disabled(int)** | Check whether tab is disabled | boolean
**selected(int)** | Check whether tab is selected | boolean

##### <a href="https://github.com/jdi-testing/jdi-light/blob/master_material_ui/jdi-light-material-ui-tests/src/test/java/io/github/epam/material/tests/navigation/TabTests.java" target="_blank">Here you can find Tabs tests</a>

<br></br>

### 4.18 Table

```java
    // @FindBy(id = "basicTable")
    @UI("#basicTable")
    public static Table basicTable;
    
    @Test
    public void basicTableTest() {
        basicTable.has().columns(EXPECTED_TABLE_HEADERS)
                        .and().size(13);
        basicTable.getCell(1, 1).has().text("305");
    }
```

##### <a href="https://material-ui.com/components/Tables/" target="_blank"> Table overview </a>

Table is located in the following class:

- __Java__: _com.epam.jdi.light.elements.complex.table.Table_

__Table__ - element that displays sets of data.

![Tables](../../images/material-ui/Tables.png)

Here is an example with provided Material-UI v4.12.3 code:

```html
<table class="MuiTable-root jss247" aria-label="simple table" id="basicTable">
  <thead class="MuiTableHead-root">
  <tr class="MuiTableRow-root MuiTableRow-head">
    <th class="MuiTableCell-root MuiTableCell-head" scope="col">Dessert (100g serving)</th>
    <th class="MuiTableCell-root MuiTableCell-head MuiTableCell-alignRight" scope="col">Calories</th>
    <th class="MuiTableCell-root MuiTableCell-head MuiTableCell-alignRight" scope="col">Fat&nbsp;(g)</th>
    <th class="MuiTableCell-root MuiTableCell-head MuiTableCell-alignRight" scope="col">Carbs&nbsp;(g)</th>
    <th class="MuiTableCell-root MuiTableCell-head MuiTableCell-alignRight" scope="col">Protein&nbsp;(g)</th>
  </tr>
  </thead>
  <tbody class="MuiTableBody-root">
  <tr class="MuiTableRow-root">
    <th class="MuiTableCell-root MuiTableCell-body" role="cell" scope="row">Cupcake</th>
    <td class="MuiTableCell-root MuiTableCell-body MuiTableCell-alignRight">305</td>
    <td class="MuiTableCell-root MuiTableCell-body MuiTableCell-alignRight">3.7</td>
    <td class="MuiTableCell-root MuiTableCell-body MuiTableCell-alignRight">67</td>
    <td class="MuiTableCell-root MuiTableCell-body MuiTableCell-alignRight">4.3</td>
  </tr>
  ...
  </tbody>
</table>
```

Available methods in Java JDI Light:

|Method | Description | Return Type
--- | --- | ---
**is()** | Returns object for work with assertions | TableAssert
**elements(int)** | Returns rows whose number is greater than or equal to the specified number | List<String>
**get(String)** | Returns values of the specified row | String

##### <a href="https://github.com/jdi-testing/jdi-light/blob/master_material_ui/jdi-light-material-ui-tests/src/test/java/io/github/epam/material/tests/displaydata/TableTests.java" target="_blank">Here you can find Tables tests</a>

<br></br>

### 4.19 Typography

```java
    // @FindBy(css = ".MuiGrid-root[3] .MuiTypography-root")
    @UI(".MuiGrid-root[3] .MuiTypography-root")
    public static List<Typography> typographyTexts;

    @Test(dataProvider = "typographyTestData")
    public static void typographyTest(int number, String text, TypographyStyles style) {
        typographyTexts.get(number).has().text(text).and().style(style);
    }

    @DataProvider
    public Object[][] typographyTestData() {
        return new Object[][]{
                {1, "Head 1", HEAD_1}, {2, "Head 2", HEAD_2}, {3, "Head 3", HEAD_3}, {4, "Head 4", HEAD_4},
                {5, "Head 5", HEAD_5}, {6, "Head 6", HEAD_6}, {7, "Subtitle 1", SUBTITLE_1},
                {8, "Subtitle 2", SUBTITLE_2}, {9, "Body 1", BODY_1}, {10, "Body 2", BODY_2},
                {11, "BUTTON TEXT", BUTTON}, {12, "Caption text", CAPTION}, {13, "OVERLINE TEXT", OVERLINE}
        };
    }
```

##### <a href="https://material-ui.com/components/typography/" target="_blank"> Typography overview </a>

Typography is located in the following class:

- __Java__: _com.epam.jdi.light.material.elements.displaydata.Typography_

__Typography__ - element that is used to present your design and content as clearly and efficiently as possible.

![Typography](../../images/material-ui/Typography.png)

Here is an example with provided Material-UI v4.12.3 code:

```html
<div class="MuiGrid-root MuiGrid-item MuiGrid-grid-xs-10">
  <div class="MuiContainer-root MuiContainer-maxWidthXl">
    <div class="MuiBox-root jss271">
      <div class="jss272">
        <h2 class="MuiTypography-root MuiTypography-h1 MuiTypography-gutterBottom">Head 1</h2>
        <h2 class="MuiTypography-root MuiTypography-h2 MuiTypography-gutterBottom">Head 2</h2>
        <h3 class="MuiTypography-root MuiTypography-h3 MuiTypography-gutterBottom">Head 3</h3>
        <h4 class="MuiTypography-root MuiTypography-h4 MuiTypography-gutterBottom">Head 4</h4>
        <h5 class="MuiTypography-root MuiTypography-h5 MuiTypography-gutterBottom">Head 5</h5>
        <h6 class="MuiTypography-root MuiTypography-h6 MuiTypography-gutterBottom">Head 6</h6>
        <h6 class="MuiTypography-root MuiTypography-subtitle1 MuiTypography-gutterBottom">Subtitle 1</h6>
        <h6 class="MuiTypography-root MuiTypography-subtitle2 MuiTypography-gutterBottom">Subtitle 2</h6>
        <p class="MuiTypography-root MuiTypography-body1 MuiTypography-gutterBottom">Body 1</p>
        <p class="MuiTypography-root MuiTypography-body2 MuiTypography-gutterBottom">Body 2</p>
        <span class="MuiTypography-root MuiTypography-button MuiTypography-gutterBottom MuiTypography-displayBlock">Button text</span>
        <span class="MuiTypography-root MuiTypography-caption MuiTypography-gutterBottom MuiTypography-displayBlock">Caption text</span>
        <span class="MuiTypography-root MuiTypography-overline MuiTypography-gutterBottom MuiTypography-displayBlock">Overline text</span>
      </div>
    </div>
  </div>
</div>
```

Available methods in Java JDI Light:

|Method | Description | Return Type
--- | --- | ---
**is()** | Returns object for work with assertions | TypographyAssert
**getStyle()** | Returns style of component | TypographyStyles

##### <a href="https://github.com/jdi-testing/jdi-light/blob/master_material_ui/jdi-light-material-ui-tests/src/test/java/io/github/epam/material/tests/displaydata/TypographyTests.java" target="_blank">Here you can find Typography tests</a>

<br></br>

### 4.20 Badge

```java
    // @FindBy(css = "#primaryColorBadge .MuiBadge-badge")
    @UI("#primaryColorBadge .MuiBadge-badge")
    public static Badge primaryColorBadge;
    
    @Test
    public void simpleBadgeTest() {
        primaryColorBadge.is().displayed()
            .and().has().text("4")
            .and().primaryColor()
            .and().position("TopRightRectangle");
    }
```

##### <a href="https://material-ui.com/ru/components/badges/" target="_blank"> Badge overview </a>

Badge is located in the following class:

- __Java__: _com.epam.jdi.light.material.elements.displaydata.Badge_

__Badge__ - element that generates a small badge to the top-right of its children.

![Badge](../../images/material-ui/Badge.png)

Here is an example with provided Material-UI v4.12.3 code:

```html
<span class="MuiBadge-root" id="primaryColorBadge">
  <svg class="MuiSvgIcon-root" focusable="false" viewBox="0 0 24 24" aria-hidden="true">...</svg>
  <span class="MuiBadge-badge MuiBadge-anchorOriginTopRightRectangle MuiBadge-colorPrimary">
    4
  </span>
</span>
```

Available methods in Java JDI Light:

|Method | Description | Return Type
--- | --- | ---
**is()** | Returns object for work with assertions | BadgeAssert
**getPosition()** | Returns element's position | String
**isDot()** | Shows that element is a dot | boolean
**isNotVisible()** | Checks whether element is not visible | boolean

##### <a href="https://github.com/jdi-testing/jdi-light/blob/master_material_ui/jdi-light-material-ui-tests/src/test/java/io/github/epam/material/tests/displaydata/BadgeTests.java" target="_blank">Here you can find Badge tests</a>

<br></br>

### 4.21 Snackbars

```java
    // @FindBy(xpath = "//span[text()='Open simple snackbar']/parent::button")
    @UI("//span[text()='Open simple snackbar']/parent::button")
    public static Button simpleSnackbarButton;

    // @FindBy(css = "[direction='up']")
    @UI("[direction='up']")
    public static Snackbar simpleSnackbar;
    
    @Test
    public void simpleSnackbarTest() {
        simpleSnackbar.is().notVisible();
        simpleSnackbarButton.click();
        simpleSnackbar.waitFor().displayed();
        simpleSnackbar.has().text("Note archived");
        simpleSnackbar.snackbarButton(UNDO).click();
        simpleSnackbar.waitFor().hidden();
        simpleSnackbar.is().notVisible();
        simpleSnackbarButton.click();
        simpleSnackbar.waitFor().displayed();
        simpleSnackbar.close();
        simpleSnackbar.is().notVisible();
    }
```

##### <a href="https://material-ui.com/components/snackbars/" target="_blank"> Snackbars overview </a>

Snackbar is located in the following class:

- __Java__: _com.epam.jdi.light.material.elements.feedback.Snackbar_

__Snackbars__ - elements that provide brief messages about app processes. The component is also known as a toast.

![Snackbars](../../images/material-ui/Snackbars.png)

Here is an example with provided Material-UI v4.12.3 code:

```html
<button class="MuiButtonBase-root MuiButton-root MuiButton-text" tabindex="0" type="button">
  <span class="MuiButton-label">Open simple snackbar</span>
  <span class="MuiTouchRipple-root"></span>
</button>

<div class="MuiPaper-root MuiSnackbarContent-root MuiPaper-elevation6" role="alert" direction="up" style="opacity: 1; transform: none; transition: opacity 225ms cubic-bezier(0.4, 0, 0.2, 1) 0ms, transform 150ms cubic-bezier(0.4, 0, 0.2, 1) 0ms;">
  <div class="MuiSnackbarContent-message">Note archived</div>
  <div class="MuiSnackbarContent-action">
    <button class="MuiButtonBase-root MuiButton-root MuiButton-text MuiButton-textSecondary MuiButton-textSizeSmall MuiButton-sizeSmall" tabindex="0" type="button">
      <span class="MuiButton-label">UNDO</span>
      <span class="MuiTouchRipple-root"></span>
    </button>
    <button class="MuiButtonBase-root MuiIconButton-root MuiIconButton-colorInherit MuiIconButton-sizeSmall" tabindex="0" type="button" aria-label="close">
      <span class="MuiIconButton-label">...<span class="MuiTouchRipple-root"></span>
    </button>
  </div>
</div>
```

Available methods in Java JDI Light:

|Method | Description | Return Type
--- | --- | ---
**is()** | Returns object for work with assertions | SnackbarAssert
**snackbarButton(String)** | Returns element's button | UIElement
**text()** | Returns component's text| String
**close()** | Closes element| void
**messageType(String)** | Shows that element's message has required type| boolean
**position(String)** | Shows that element has required position| boolean

##### <a href="https://github.com/jdi-testing/jdi-light/blob/master_material_ui/jdi-light-material-ui-tests/src/test/java/io/github/epam/material/tests/feedback/SnackbarTests.java" target="_blank">Here you can find Snackbars tests</a>

<br></br>

### 4.22 Backdrop

```java
    // @FindBy(className = "MuiButton-root")
    @UI(".MuiButton-root")
    public static MaterialButton showBackdropButton;

    // @FindBy(className = "MuiBackdrop-root")
    @UI(".MuiBackdrop-root")
    public static Backdrop backdrop;

    @Test
    public void defaultBackdropTest() {
        showBackdropButton.click();
        backdrop.is().visible();
        backdrop.core().click();
        backdrop.is().hidden();
    }
```

##### <a href="https://material-ui.com/components/backdrop/" target="_blank"> Backdrop overview </a>

Backdrop is located in the following class:

- __Java__: _com.epam.jdi.light.material.elements.feedback.Backdrop_

__Backdrop__ - element that is used to provide emphasis on a particular element or parts of it.

![Backdrop](../../images/material-ui/Backdrop.png)

Here is an example with provided Material-UI v4.12.3 code:

```html
<div class="MuiBackdrop-root jss284" aria-hidden="true" style="opacity: 1; transition: opacity 225ms cubic-bezier(0.4, 0, 0.2, 1) 0ms;">
  <div class="MuiCircularProgress-root MuiCircularProgress-indeterminate" role="progressbar" style="width: 40px; height: 40px;">
    <svg class="MuiCircularProgress-svg" viewBox="22 22 44 44">
      <circle class="MuiCircularProgress-circle MuiCircularProgress-circleIndeterminate" cx="44" cy="44" r="20.2" fill="none" stroke-width="3.6"></circle>
    </svg>
  </div>
</div>
```

Available methods in Java JDI Light:

|Method | Description | Return Type
--- | --- | ---
**is()** | Returns object for work with assertions | BackdropAssert

##### <a href="https://github.com/jdi-testing/jdi-light/blob/master_material_ui/jdi-light-material-ui-tests/src/test/java/io/github/epam/material/tests/feedback/BackdropTests.java" target="_blank">Here you can find Backdrop tests</a>

<br></br>

### 4.23 Dialog

```java
    //Button containing dialog @FindBy(xpath = "//span[text()='Open simple dialog']/parent::button")
    //Dialog @FindBy(xpath = "//div[@aria-labelledby = 'simple-dialog-title']/parent::div[contains(@class, 'MuiDialog-container')]")
    //Text reflecting last action @FindBy(id = "simpleDialogSelection")
    @JDIButtonWithDialog(root = "//span[text()='Open simple dialog']/parent::button",
              dialog = "//div[@aria-labelledby = 'simple-dialog-title']/parent::div[contains(@class, 'MuiDialog-container')]",
              actionText = "#simpleDialogSelection")
    public static ButtonWithDialog simpleDialogButton;

    @Test(dataProvider = "simpleDialogDataProvider")
    public void simpleDialogTest(String titleText, int index, String text) {
        simpleDialogButton.click();
        simpleDialogButton.dialog().is().displayed();
        simpleDialogButton.dialog().title().has().text(titleText);
        simpleDialogButton.dialog().list().has().size(3);
        simpleDialogButton.dialog().list().items().get(index).has().text(text);
        simpleDialogButton.dialog().list().items().get(index).click();
        simpleDialogButton.dialog().is().hidden();
        simpleDialogButton.actionText().has()
                .text(equalToIgnoringCase("Selected: " + text.replaceAll(" ", "")));
    }

    @DataProvider(name = "simpleDialogDataProvider")
    public Object[][] simpleDialogData() {
        return new Object[][]{
                {"Set backup account", 0, "username@gmail.com"},
                {"Set backup account", 1, "user02@gmail.com"},
                {"Set backup account", 2, "Add account"}
        };
    }
```

##### <a href="https://material-ui.com/components/dialogs/" target="_blank"> Dialog overview </a>

Dialog is located in the following class:

- __Java__: _com.epam.jdi.light.material.elements.feedback.Dialog_

__Dialog__ - element that informs users about a task and can contain critical information, require decisions, or involve multiple tasks.

![Dialog](../../images/material-ui/Dialog.png)

Here is an example with provided Material-UI v4.12.3 code:

```html
<div class="MuiPaper-root MuiDialog-paper MuiDialog-paperScrollPaper MuiDialog-paperWidthSm MuiPaper-elevation24 MuiPaper-rounded" role="dialog" aria-labelledby="simple-dialog-title">
  <div class="MuiDialogTitle-root" id="simple-dialog-title">
    <h2 class="MuiTypography-root MuiTypography-h6">Set backup account</h2>
  </div>
  <ul class="MuiList-root MuiList-padding">
    <div class="MuiButtonBase-root MuiListItem-root MuiListItem-gutters MuiListItem-button" tabindex="0" role="button" aria-disabled="false">...</div>
    <div class="MuiButtonBase-root MuiListItem-root MuiListItem-gutters MuiListItem-button" tabindex="0" role="button" aria-disabled="false">...</div>
    <div class="MuiButtonBase-root MuiListItem-root MuiListItem-gutters MuiListItem-button" tabindex="0" role="button" aria-disabled="false">...</div>
  </ul>
</div>
```

Available methods in Java JDI Light:

|Method | Description | Return Type
--- | --- | ---
**is()** | Returns object for work with assertions | DialogAssert
**title()** | Returns element's title | Text
**list()** | Returns list of element's items | List
**textContent()** | Returns element's text content | Text
**actions()** | Returns element's action buttons | ButtonGroup
**radioButtons()** | Returns element's radio buttons | RadioButtons
**input()** | Returns element's input field | TextField
**hasScrollableContent()** | Shows that element has scrollable content | Boolean
**hasScrollableBody()** | Shows that element has scrollable body | Boolean
**close()** | Closes element | void
**confirm()** | Confirms and closes element | void
**scrollDialogBodyTo(int)** | Scrolls element to targeted position | void

##### <a href="https://github.com/jdi-testing/jdi-light/blob/master_material_ui/jdi-light-material-ui-tests/src/test/java/io/github/epam/material/tests/feedback/DialogTests.java" target="_blank">Here you can find Dialog tests</a>

<br></br>

### 4.24 Date / Time pickers

```java
    // @FindBy(xpath = "//*[@id = 'date-picker-inline-label']/parent::div")
    @UI("//*[@id = 'date-picker-inline-label']/parent::div")
    public static DateTimePicker inlineDatePicker;
    
    @Test
    public void datePickerInlineTest() {
        inlineDatePicker.has().title("Date picker inline");

        inlineDatePicker.input("10/10/2022");
        inlineDatePicker.has().text("10/10/2022");
        inlineDatePicker.selectDate("22");
        inlineDatePicker.has().text(containsString("/22/"));
    }
```

##### <a href="https://material-ui.com/components/pickers/" target="_blank"> Date / Time pickers overview </a>

DateTimePicker is located in the following class:

- __Java__: _com.epam.jdi.light.material.elements.inputs.DateTimePicker_

__Date / Time Picker__ - element that provides a simple way to select a single value from a pre-determined set.

![DateTimePickers](../../images/material-ui/DateTimePickers.png)

Here is an example with provided Material-UI v4.12.3 code:

```html
<div class="MuiInputBase-root MuiInput-root MuiInput-underline MuiInputBase-formControl MuiInput-formControl MuiInputBase-adornedEnd">
  <input aria-invalid="false" id="date-picker-inline" type="text" class="MuiInputBase-input MuiInput-input MuiInputBase-inputAdornedEnd" value="08/18/2014">
  <div class="MuiInputAdornment-root MuiInputAdornment-positionEnd">
    <button class="MuiButtonBase-root MuiIconButton-root" tabindex="0" type="button" aria-label="change date">...</button>
  </div>
</div>

<div class="MuiPickersBasePicker-container">
  <div class="MuiPickersBasePicker-pickerView">
    <div>
      <div class="MuiPickersCalendarHeader-switchHeader">...</div>
      <div class="MuiPickersCalendarHeader-daysHeader">...</div>
    </div>
    <div class="MuiPickersSlideTransition-transitionContainer MuiPickersCalendar-transitionContainer">...</div>
  </div>
</div>
```

Available methods in Java JDI Light:

|Method | Description | Return Type
--- | --- | ---
**is()** | Returns object for work with assertions | DateTimePickerAssert
**timer()** | Returns list for of hours| WebList
**selectDate(String)** | Selects required date | void
**expand()** | Expands element | void
**cancel()** | Closes element without saving changes | void
**confirm()** | Closes element with saving changes | void
**input(String)** | Sets text in element's input field | void
**title()** | Returns element's title | String
**isExpanded()** | Shows that element is expanded | boolean
**getText()** | Returns text from input field | String

##### <a href="https://github.com/jdi-testing/jdi-light/blob/master_material_ui/jdi-light-material-ui-tests/src/test/java/io/github/epam/material/tests/inputs/DateTimePickersTests.java" target="_blank">Here you can find Date/Time Pickers tests</a>

<br></br>

### 4.25 Select

```java
    // @FindBy(xpath = "//*[@id='demo-simple-select']/following-sibling::div")
    @JDropdown(root = "//*[@id='demo-simple-select']/following-sibling::div")
    public static Select simpleSelect;
  
    @Test
    public void simpleSelectTest() {
        String value = "Hansen";
        
        simpleSelect.expand();
        simpleSelect.is().expanded();
        simpleSelect.close();
        simpleSelect.is().collapsed();
        simpleSelect.select(value);
        simpleSelect.has().selected(value);
    }
```

##### <a href="https://material-ui.com/components/selects/" target="_blank"> Select overview </a>

Select is located in the following class:

- __Java__: _com.epam.jdi.light.material.elements.inputs.Select_

__Select__ - element that is used for collecting user provided information from a list of options.

![Select](../../images/material-ui/Select.png)

Here is an example with provided Material-UI v4.12.3 code:

```html
<div class="MuiFormControl-root jss304">
  <label class="MuiFormLabel-root MuiInputLabel-root MuiInputLabel-formControl MuiInputLabel-animated" data-shrink="false" id="demo-simple-select">
    Simple Select
  </label>
  <div class="MuiInputBase-root MuiInput-root MuiInput-underline MuiInputBase-formControl MuiInput-formControl">
    <div class="MuiSelect-root MuiSelect-select MuiSelect-selectMenu MuiInputBase-input MuiInput-input" tabindex="0" role="button" aria-haspopup="listbox" aria-labelledby="simple-select" id="simple-select">
      <span>​</span>
    </div>
    <input aria-hidden="true" tabindex="-1" class="MuiSelect-nativeInput" value="">
    <svg class="MuiSvgIcon-root MuiSelect-icon" focusable="false" viewBox="0 0 24 24" aria-hidden="true">...</svg>
  </div>
</div>
```

Available methods in Java JDI Light:

|Method | Description | Return Type
--- | --- | ---
**is()** | Returns object for work with assertions | SelectAssert
**list()** | Returns list of options | SelectAssert
**close()** | Closes element | void
**select(String)** | Selects required value in element | void
**selected()** | Returns value of selected element | String
**getText()** | Returns value of selected element | String
**text()** | Returns value of selected element | String

##### <a href="https://github.com/jdi-testing/jdi-light/blob/master_material_ui/jdi-light-material-ui-tests/src/test/java/io/github/epam/material/tests/inputs/SelectTests.java" target="_blank">Here you can find Select tests</a>

<br></br>

### 4.26 Switch

```java
    // @FindBy(xpath = "//fieldset//span[@class='MuiSwitch-root']")
    @UI("//fieldset//span[@class='MuiSwitch-root']")
    public static List<Switch> formGroupSwitches;

    // @FindBy(xpath = "//p[contains(@class,'MuiFormHelperText-root')]")
    @UI("//p[contains(@class,'MuiFormHelperText-root')]")
    public static Text formGroupTextForm;
  
    @Test(dataProvider = "switchesWithFormGroupTestsDataProvider")
    public void switchesWithFormGroupTest(int index, String fullName) {
        formGroupTextForm.is().text("Be careful");
        switchWithLabelTestLogic(formGroupSwitches.get(index),fullName);
    }
    
    private void switchWithLabelTestLogic(Switch muiSwitch, String labelText) {
        String firstName = Arrays.stream(labelText.split(" "))
                .collect(Collectors.toList())
                .get(0)
                .toLowerCase();
        basicSwitchTestLogic(muiSwitch);
        muiSwitch.has().label();
        muiSwitch.has().labelText(labelText);
        if (muiSwitch.isTurnedOn()) {
            muiSwitch.turnOff();
        }
        muiSwitch.turnOn();
        formGroupTextForm.is().text(String.format("Be careful with %s", firstName));
    }
```

##### <a href="https://material-ui.com/components/switches/" target="_blank"> Switch overview </a>

Switch is located in the following class:

- __Java__: _com.epam.jdi.light.material.elements.inputs.Switch_

__Switch__ - element that toggles the state of a single setting on or off.

![Switch](../../images/material-ui/Switch.png)

Here is an example with provided Material-UI v4.12.3 code:

```html
<fieldset class="MuiFormControl-root">
  <legend class="MuiFormLabel-root">Assign responsibility</legend>
  <div class="MuiFormGroup-root">
    <label class="MuiFormControlLabel-root">
      <span class="MuiSwitch-root">
        <span class="MuiButtonBase-root MuiIconButton-root jss326 MuiSwitch-switchBase MuiSwitch-colorSecondary jss327 Mui-checked" aria-disabled="false">
          <span class="MuiIconButton-label">
            <input class="jss329 MuiSwitch-input" name="gilad" type="checkbox" value="" checked="">
            <span class="MuiSwitch-thumb"></span>
          </span>
          <span class="MuiTouchRipple-root"></span>
        </span>
        <span class="MuiSwitch-track"></span>
      </span>
      <span class="MuiTypography-root MuiFormControlLabel-label MuiTypography-body1">Gilad Gray</span>
    </label>
    <label class="MuiFormControlLabel-root">
      <span class="MuiSwitch-root">...</span>
      <span class="MuiTypography-root MuiFormControlLabel-label MuiTypography-body1">Jason Killian</span>
    </label>
    <label class="MuiFormControlLabel-root">
      <span class="MuiSwitch-root">...</span>
    <span class="MuiTypography-root MuiFormControlLabel-label MuiTypography-body1">Antoine Llorca</span></label></div>
  <p class="MuiFormHelperText-root">Be careful </p>
</fieldset>
```

Available methods in Java JDI Light:

|Method | Description | Return Type
--- | --- | ---
**is()** | Returns object for work with assertions | SwitchAssert
**has()** | Returns object for work with assertions | SwitchAssert
**isTurnedOn()** | Shows that element turned on | boolean
**isTurnedOff()** | Shows that element turned off | boolean
**turnOn()** | Turns element on | void
**turnOff()** | Turns element off | void
**label()** | Returns element's label | Label
**labelText()** | Returns label's text | String

##### <a href="https://github.com/jdi-testing/jdi-light/blob/master_material_ui/jdi-light-material-ui-tests/src/test/java/io/github/epam/material/tests/inputs/SwitchTests.java" target="_blank">Here you can find Switch tests</a>

<br></br>

### 4.27 Button

```java
    // @FindBy(xpath = "//h2[text()='Contained buttons']/parent::div/div[1]/*")
    @UI("//h2[text()='Contained buttons']/parent::div/div[1]/*")
    public static List<Button> containedButtons;

    @Test
    public void defaultButtonTest() {
        containedButtons.get(1).click();
        containedButtons.get(1).is().text("DEFAULT");
        containedButtons.get(6).is().text("Last click: Default");

        containedButtons.get(2).click();
        containedButtons.get(2).is().text("PRIMARY");
        containedButtons.get(6).is().text("Last click: Primary");

        containedButtons.get(3).click();
        containedButtons.get(3).is().text("SECONDARY");
        containedButtons.get(6).is().text("Last click: Secondary");
    }
```

##### <a href="https://material-ui.com/components/buttons/" target="_blank"> Button overview </a>

Button is located in the following class:

- __Java__: _com.epam.jdi.light.ui.html.elements.common.Button_

__Button__ - element that allows users to take actions and make choices with a single tap.

![Buttons](../../images/material-ui/Buttons.png)

Here is an example with provided Material-UI v4.12.3 code:

```html
<h2>Contained buttons</h2>
<div class="jss331">
  <button class="MuiButtonBase-root MuiButton-root MuiButton-contained" tabindex="0" type="button">
    <span class="MuiButton-label">Default</span>
    <span class="MuiTouchRipple-root"></span>
  </button>
</div>
```

Available methods in Java JDI Light:

|Method | Description | Return Type
--- | --- | ---
**is()** | Returns object for work with assertions | TextAssert
**getValue()** | Returns button text | String

##### <a href="https://github.com/jdi-testing/jdi-light/blob/master_material_ui/jdi-light-material-ui-tests/src/test/java/io/github/epam/material/tests/inputs/ButtonTests.java" target="_blank">Here you can find Buttons tests</a>

<br></br>

### 4.28 ButtonGroup

```java
    //      @FindBy(xpath = "//div[@aria-label = 'outlined primary button group']")
    @UI("//div[@aria-label = 'outlined primary button group']")
    @JDIButtonGroup(list = ".MuiButtonGroup-groupedHorizontal")
    public static ButtonGroup basicButtonGroup;

    //      @FindBy(xpath = "//div[@aria-label = 'vertical contained primary button group']")
    @UI("//div[@aria-label = 'vertical contained primary button group']")
    @JDIButtonGroup(list = ".MuiButton-root")
    public static ButtonGroup verticalButtonGroup;
```

```java
    @Test
    public void basicButtonGroupTest(){

        basicButtonGroup.getButtonByIndex(1).click();
        basicButtonGroup.getButtonByIndex(2).click();
        basicButtonGroup.getButtonByIndex(3).click();

        basicButtonGroup.getButtonByText("Three").click();
        basicButtonGroup.getButtonByText("Two").click();
        basicButtonGroup.getButtonByText("One").click();

        basicButtonGroup.getButtonByIndex(1).is().enabled();
        basicButtonGroup.getButtonByIndex(1).has().text("ONE");

        basicButtonGroup.has().numberOfGroupedButtons(3);
        basicButtonGroup.has().buttonsTextsInAnyOrder(Arrays.asList("THREE","ONE","TWO"));
    }

    @Test
    public void verticalButtonGroupTest(){

        verticalButtonGroup.getButtonByIndex(2).click();
        verticalButtonGroup.getButtonByIndex(3).click();

        verticalButtonGroup.getButtonByText("Two").click();
        verticalButtonGroup.getButtonByText("One").click();

        basicButtonGroup.getButtonByIndex(2).is().enabled();
        basicButtonGroup.getButtonByIndex(2).has().text("TWO");
    }
```

##### <a href="https://material-ui.com/components/button-group/" target="_blank">ButtonGroup overview</a>

ButtonGroup is located in the following class:

- __Java__: _com.epam.jdi.light.material.elements.inputs.ButtonGroup_

__ButtonGroup__ - element that represents a group of clickable button. The ButtonGroup component can be used to group
related buttons.

![ButtonGroup](../../images/buttongroup.png)
![ButtonGroup](../../images/verticalbuttongroup.png)

Here are examples with provided MaterialUI v4.12.3 code:

```html

<div role="group" class="MuiButtonGroup-root" aria-label="outlined primary button group">
  <button
    class="MuiButtonBase-root MuiButton-root MuiButton-outlined MuiButtonGroup-grouped MuiButtonGroup-groupedHorizontal MuiButtonGroup-groupedOutlined MuiButtonGroup-groupedOutlinedHorizontal MuiButtonGroup-groupedOutlinedPrimary MuiButton-outlinedPrimary"
    tabindex="0" type="button">
    <span class="MuiButton-label">One</span>
    <span class="MuiTouchRipple-root"></span>
  </button>
  <button
    class="MuiButtonBase-root MuiButton-root MuiButton-outlined MuiButtonGroup-grouped MuiButtonGroup-groupedHorizontal MuiButtonGroup-groupedOutlined MuiButtonGroup-groupedOutlinedHorizontal MuiButtonGroup-groupedOutlinedPrimary MuiButton-outlinedPrimary"
    tabindex="0" type="button">
    <span class="MuiButton-label">Two</span>
    <span class="MuiTouchRipple-root"></span>
  </button>
  <button
    class="MuiButtonBase-root MuiButton-root MuiButton-outlined MuiButtonGroup-grouped MuiButtonGroup-groupedHorizontal MuiButtonGroup-groupedOutlined MuiButtonGroup-groupedOutlinedHorizontal MuiButtonGroup-groupedOutlinedPrimary MuiButton-outlinedPrimary"
    tabindex="0" type="button">
    <span class="MuiButton-label">Three</span>
    <span class="MuiTouchRipple-root"></span>
  </button>
</div>
```
```html
<div role="group" class="MuiButtonGroup-root MuiButtonGroup-contained MuiButtonGroup-vertical" aria-label="vertical contained primary button group">
  <button class="MuiButtonBase-root MuiButton-root MuiButton-contained MuiButtonGroup-grouped MuiButtonGroup-groupedVertical MuiButtonGroup-groupedContained MuiButtonGroup-groupedContainedVertical MuiButtonGroup-groupedContainedPrimary MuiButton-containedPrimary" tabindex="0" type="button">
    <span class="MuiButton-label">One</span>
    <span class="MuiTouchRipple-root"></span>
  </button>
  <button class="MuiButtonBase-root MuiButton-root MuiButton-contained MuiButtonGroup-grouped MuiButtonGroup-groupedVertical MuiButtonGroup-groupedContained MuiButtonGroup-groupedContainedVertical MuiButtonGroup-groupedContainedPrimary MuiButton-containedPrimary" tabindex="0" type="button">
    <span class="MuiButton-label">Two</span>
    <span class="MuiTouchRipple-root"></span>
  </button>
  <button class="MuiButtonBase-root MuiButton-root MuiButton-contained MuiButtonGroup-grouped MuiButtonGroup-groupedVertical MuiButtonGroup-groupedContained MuiButtonGroup-groupedContainedVertical MuiButtonGroup-groupedContainedPrimary MuiButton-containedPrimary" tabindex="0" type="button">
    <span class="MuiButton-label">Three</span>
    <span class="MuiTouchRipple-root"></span>
  </button>
</div>
```

Available methods in Java JDI Light:

|Method | Description | Return Type
| --- | --- | ---
**is()** | Returns object for work with assertions | ButtonGroupAssert
**getButtonByIndex(int)** | Get button by index | MaterialButton
**getButtonByText(String)** | Get button by text | MaterialButton
**getAllButtons()**        | Get all buttons in a block | Collection\<MaterialButton\>

##### <a href="https://github.com/jdi-testing/jdi-light/blob/master_material_ui/jdi-light-material-ui-tests/src/test/java/io/github/epam/material/tests/inputs/ButtonGroupTests.java" target="_blank">Here you can find Button group tests</a>

<br></br>

### 4.29 Grid

```java
    // @FindBy(id = "basicGrid")
    @UI("#basicGrid")
    public static Grid basicGrid;

    @Test(dataProvider = "basicGridItems")
    public void basicGridItemsTest(int itemIndex, String itemWidth, String itemClass) {
        rootGrid.is().displayed()
                .and().has().cssClass("MuiContainer-maxWidthXl");
        basicGrid.show();
        basicGrid.is().displayed()
                .and().has().items(7);
        
        basicGrid.items().get(itemIndex)
                .has().cssClass(itemClass)
                .and().css("max-width", itemWidth);
    }

    @DataProvider
    public Object[][] basicGridItems() {
        return new Object[][]{
                {1, "100%", "MuiGrid-grid-xs-12"},
                {2, "50%", "MuiGrid-grid-xs-6"},
                {3, "50%", "MuiGrid-grid-xs-6"},
                {4, "25%", "MuiGrid-grid-xs-3"},
                {5, "25%", "MuiGrid-grid-xs-3"},
                {6, "25%", "MuiGrid-grid-xs-3"},
                {7, "25%", "MuiGrid-grid-xs-3"},
        };
    }
```

##### <a href="https://material-ui.com/components/grid/" target="_blank"> Grid overview </a>

Grid is located in the following class:

- __Java__: _com.epam.jdi.light.material.elements.layout.Grid_

__The grid__ adapts to screen size and orientation, creates visual consistency between layouts while allowing flexibility across a wide variety of designs.

![Grid](../../images/material-ui/Grids.png)

Here is an example with provided MaterialUI v4.12.3 code:

```html
<div class="MuiGrid-root MuiGrid-container MuiGrid-spacing-xs-3" id="basicGrid">
  <div class="MuiGrid-root MuiGrid-item MuiGrid-grid-xs-12">
    <div class="MuiPaper-root jss6 MuiPaper-elevation1 MuiPaper-rounded">xs=12</div>
  </div>
  <div class="MuiGrid-root MuiGrid-item MuiGrid-grid-xs-6">
    <div class="MuiPaper-root jss6 MuiPaper-elevation1 MuiPaper-rounded">xs=6</div>
  </div>
  <div class="MuiGrid-root MuiGrid-item MuiGrid-grid-xs-6">
    <div class="MuiPaper-root jss6 MuiPaper-elevation1 MuiPaper-rounded">xs=6</div>
  </div>
  <div class="MuiGrid-root MuiGrid-item MuiGrid-grid-xs-3">
    <div class="MuiFormControl-root MuiTextField-root jss6">
      <div class="MuiInputBase-root MuiInput-root MuiInput-underline MuiInputBase-formControl MuiInput-formControl">
        <input aria-invalid="false" type="text" class="MuiInputBase-input MuiInput-input" value="xs=31">
      </div>
    </div>
  </div>
  <div class="MuiGrid-root MuiGrid-item MuiGrid-grid-xs-3">
    <div class="MuiFormControl-root MuiTextField-root jss6">
      <div class="MuiInputBase-root MuiInput-root MuiInput-underline MuiInputBase-formControl MuiInput-formControl">
        <input aria-invalid="false" type="text" class="MuiInputBase-input MuiInput-input" value="xs=32">
      </div>
    </div>
  </div>
  <div class="MuiGrid-root MuiGrid-item MuiGrid-grid-xs-3">
    <div class="MuiFormControl-root MuiTextField-root jss6">
      <div class="MuiInputBase-root MuiInput-root MuiInput-underline MuiInputBase-formControl MuiInput-formControl">
        <input aria-invalid="false" type="text" class="MuiInputBase-input MuiInput-input" value="xs=33">
      </div>
    </div>
  </div>
  <div class="MuiGrid-root MuiGrid-item MuiGrid-grid-xs-3">
    <div class="MuiFormControl-root MuiTextField-root jss6">
      <div class="MuiInputBase-root MuiInput-root MuiInput-underline MuiInputBase-formControl MuiInput-formControl">
        <input aria-invalid="false" type="text" class="MuiInputBase-input MuiInput-input" value="xs=34">
      </div>
    </div>
  </div>
</div>
```

Available methods in Java JDI Light:

|Method | Description | Return Type
--- | --- | ---
**is()** | Returns object for work with assertions | GridAssert
**items()** | Returns list of items in grid | WebList

##### <a href="https://github.com/jdi-testing/jdi-light/blob/master_material_ui/jdi-light-material-ui-tests/src/test/java/io/github/epam/material/tests/layout/GridTests.java" target="_blank">Here you can find Grid tests</a>

<br></br>

### 4.30 GridList

```java 
     // @FindBy(css = ".MuiGridList-root.jss5")
     @UI(".MuiGridList-root.jss5")
     public static GridList singleLineGridList;
    
     @Test
     public static void singleLineGridTest() {
        singleLineGridList.has().size(5);
        singleLineGridList.has().image(3).and().altImgName(3, HATS);
        singleLineGridList.has().image(4).and().altImgName(4, BIKE);
        singleLineGridList.has().title(5, CAMERA);
    }
```

##### <a href="https://v3.mui.com/demos/grid-list/" target="_blank"> GridList overview </a>

GridList is located in the following class:

- __Java__: _com.epam.jdi.light.material.elements.layout.GridList_

__The Grid List__ - list of Material UI Grid elements.

![GridList](../../images/material-ui/GridList.png)

Here is an example with provided MaterialUI v3.9.4 code:

```html
<div class="jss26">
  <ul class="MuiGridList-root jss27" style="margin: -2px;">
    <li class="MuiGridListTile-root" style="width: 40%; height: 184px; padding: 2px;">
      <div class="MuiGridListTile-tile">
        <img src="https://images.unsplash.com/photo-1444418776041-9c7e33cc5a9c?fit=crop&amp;auto=format" alt="coffee"
             class="MuiGridListTile-imgFullWidth">
        <div class="MuiGridListTileBar-root jss29 MuiGridListTileBar-titlePositionBottom">
          <div class="MuiGridListTileBar-titleWrap MuiGridListTileBar-titleWrapActionPosRight">
            <div class="MuiGridListTileBar-title jss28">coffee</div>
          </div>
          <div class="MuiGridListTileBar-actionIcon">
            <button class="MuiButtonBase-root MuiIconButton-root" tabindex="0" type="button" aria-label="star coffee">
              <span class="MuiIconButton-label"></span>
              <span class="MuiTouchRipple-root"></span>
            </button>
          </div>
        </div>
      </div>
    </li>
    <li class="MuiGridListTile-root" style="width: 40%; height: 184px; padding: 2px;">
      <div class="MuiGridListTile-tile">
        <img src="https://images.unsplash.com/photo-1518756131217-31eb79b20e8f?fit=crop&amp;auto=format" alt="fern"
             class="MuiGridListTile-imgFullWidth">
        <div class="MuiGridListTileBar-root jss29 MuiGridListTileBar-titlePositionBottom">
          <div class="MuiGridListTileBar-titleWrap MuiGridListTileBar-titleWrapActionPosRight">
            <div class="MuiGridListTileBar-title jss28">fern</div>
          </div>
          <div class="MuiGridListTileBar-actionIcon">
            <button class="MuiButtonBase-root MuiIconButton-root" tabindex="0" type="button" aria-label="star fern">
              <span class="MuiIconButton-label"></span>
              <span class="MuiTouchRipple-root"></span>
            </button>
          </div>
        </div>
      </div>
    </li>
    <li class="MuiGridListTile-root" style="width: 40%; height: 184px; padding: 2px;">
      <div class="MuiGridListTile-tile">
        <img src="https://images.unsplash.com/photo-1533827432537-70133748f5c8?fit=crop&amp;auto=format" alt="hats"
             class="MuiGridListTile-imgFullWidth">
        <div class="MuiGridListTileBar-root jss29 MuiGridListTileBar-titlePositionBottom">
          <div class="MuiGridListTileBar-titleWrap MuiGridListTileBar-titleWrapActionPosRight">
            <div class="MuiGridListTileBar-title jss28">hats</div>
          </div>
          <div class="MuiGridListTileBar-actionIcon">
            <button class="MuiButtonBase-root MuiIconButton-root" tabindex="0" type="button" aria-label="star hats">
              <span class="MuiIconButton-label"></span>
              <span class="MuiTouchRipple-root"></span>
            </button>
          </div>
        </div>
      </div>
    </li>
    <li class="MuiGridListTile-root" style="width: 40%; height: 184px; padding: 2px;">
      <div class="MuiGridListTile-tile">
        <img src="https://images.unsplash.com/photo-1589118949245-7d38baf380d6?fit=crop&amp;auto=format" alt="bike"
             class="MuiGridListTile-imgFullWidth">
        <div class="MuiGridListTileBar-root jss29 MuiGridListTileBar-titlePositionBottom">
          <div class="MuiGridListTileBar-titleWrap MuiGridListTileBar-titleWrapActionPosRight">
            <div class="MuiGridListTileBar-title jss28">bike</div>
          </div>
          <div class="MuiGridListTileBar-actionIcon">
            <button class="MuiButtonBase-root MuiIconButton-root" tabindex="0" type="button" aria-label="star bike">
              <span class="MuiIconButton-label"></span>
              <span class="MuiTouchRipple-root"></span>
            </button>
          </div>
        </div>
      </div>
    </li>
    <li class="MuiGridListTile-root" style="width: 40%; height: 184px; padding: 2px;">
      <div class="MuiGridListTile-tile">
        <img src="https://images.unsplash.com/photo-1522770179533-24471fcdba45?fit=crop&amp;auto=format" alt="camera"
             class="MuiGridListTile-imgFullWidth">
        <div class="MuiGridListTileBar-root jss29 MuiGridListTileBar-titlePositionBottom">
          <div class="MuiGridListTileBar-titleWrap MuiGridListTileBar-titleWrapActionPosRight">
            <div class="MuiGridListTileBar-title jss28">camera</div>
          </div>
          <div class="MuiGridListTileBar-actionIcon">
            <button class="MuiButtonBase-root MuiIconButton-root" tabindex="0" type="button" aria-label="star camera">
              <span class="MuiIconButton-label"></span>
              <span class="MuiTouchRipple-root"></span>
            </button>
          </div>
        </div>
      </div>
    </li>
  </ul>
</div>
```

Available methods in Java JDI Light:

|Method | Description | Return Type
--- | --- | ---
**is()** | Returns object for work with assertions| GridListAssert
**hasImage(int)** | Shows that required element has image| boolean
**getAltImgName(int)** | Returns required element's image alternative name| String
**getTitle(int)** | Returns required element's title | String

##### <a href="https://github.com/jdi-testing/jdi-light/blob/master_material_ui/jdi-light-material-ui-tests/src/test/java/io/github/epam/material/tests/layout/GridListTests.java" target="_blank">Here you can find GridList tests</a>

<br></br>

### 4.31 Drawer

```java  
    //root - @FindBy(xpath = "//span[text() = 'left']/parent::button")
    //drawer - @FindBy(css = ".MuiDrawer-paperAnchorLeft")
    @JDIButtonWithDrawer(
            root = "//span[text() = 'left']/parent::button",
            drawer = ".MuiDrawer-paperAnchorLeft"
    )
    public static ButtonWithDrawer leftDrawerButton;
    
    //@FindBy(css = ".MuiDrawer-paper")
    @UI(".MuiDrawer-paper")
    public static Drawer clippedDrawer;

    @Test
    public void leftTemporaryDrawerTest() {
        leftDrawerButton.click();
        leftDrawerButton.drawer().is().displayed();
        leftDrawerButton.drawer().has().position("left");
        leftDrawerButton.drawer().has().width(250);
        leftDrawerButton.drawer().close();
        leftDrawerButton.drawer().is().notExist();
    }
    
    @Test
    public void clippedDrawerTest() {
        clippedDrawer.is().displayed();
        clippedDrawer.has().position("left");
        clippedDrawer.has().width(240);
        clippedDrawer.has().numberOfListItems(7);
        clippedDrawer.topList().has().size(4);
        clippedDrawer.topList().items().get(1).has().text("Starred");
        clippedDrawer.topList().items().get(0).icon().is().displayed();
        clippedDrawer.bottomList().has().size(3);
        clippedDrawer.bottomList().items().get(2).has().text("Spam");
        clippedDrawer.bottomList().items().get(1).icon().is().displayed();
    }
```

##### <a href="https://material-ui.com/components/drawers/" target="_blank"> Drawer overview</a>

Drawer is located in the following class:

- __Java__: _com.epam.jdi.light.material.elements.navigation.Drawer_

Navigation __drawers__ provide access to destinations in your app. Side sheets are surfaces containing supplementary
content that are anchored to the left or right edge of the screen.

![Drawer](../../images/material-ui/Drawer.png)

Here is an example with provided MaterialUI v4.12.3 code:

```html
<div class="MuiPaper-root MuiDrawer-paper MuiDrawer-paperAnchorLeft MuiPaper-elevation16" tabindex="-1"
     style="transform: none; transition: transform 225ms cubic-bezier(0, 0, 0.2, 1) 0ms;">
  <div class="jss34" role="presentation">
    <ul class="MuiList-root MuiList-padding">
      <div class="MuiButtonBase-root MuiListItem-root MuiListItem-gutters MuiListItem-button" tabindex="0" role="button"
           aria-disabled="false">
        <div class="MuiListItemIcon-root"></div>
        <div class="MuiListItemText-root"></div>
        <span class="MuiTouchRipple-root"></span>
      </div>
      <div class="MuiButtonBase-root MuiListItem-root MuiListItem-gutters MuiListItem-button" tabindex="0" role="button"
           aria-disabled="false">
        <div class="MuiListItemIcon-root"></div>
        <div class="MuiListItemText-root"></div>
        <span class="MuiTouchRipple-root"></span>
      </div>
      <div class="MuiButtonBase-root MuiListItem-root MuiListItem-gutters MuiListItem-button" tabindex="0" role="button"
           aria-disabled="false">
        <div class="MuiListItemIcon-root"></div>
        <div class="MuiListItemText-root"></div>
        <span class="MuiTouchRipple-root"></span>
      </div>
      <div class="MuiButtonBase-root MuiListItem-root MuiListItem-gutters MuiListItem-button" tabindex="0" role="button"
           aria-disabled="false">
        <div class="MuiListItemIcon-root"></div>
        <div class="MuiListItemText-root"></div>
        <span class="MuiTouchRipple-root"></span>
      </div>
    </ul>
    <hr class="MuiDivider-root">
    <ul class="MuiList-root MuiList-padding">
      <div class="MuiButtonBase-root MuiListItem-root MuiListItem-gutters MuiListItem-button" tabindex="0" role="button"
           aria-disabled="false">
        <div class="MuiListItemIcon-root"></div>
        <div class="MuiListItemText-root"></div>
        <span class="MuiTouchRipple-root"></span>
      </div>
      <div class="MuiButtonBase-root MuiListItem-root MuiListItem-gutters MuiListItem-button" tabindex="0" role="button"
           aria-disabled="false">
        <div class="MuiListItemIcon-root"></div>
        <div class="MuiListItemText-root"></div>
        <span class="MuiTouchRipple-root"></span>
      </div>
      <div class="MuiButtonBase-root MuiListItem-root MuiListItem-gutters MuiListItem-button" tabindex="0" role="button"
           aria-disabled="false">
        <div class="MuiListItemIcon-root"></div>
        <div class="MuiListItemText-root"></div>
        <span class="MuiTouchRipple-root"></span>
      </div>
    </ul>
  </div>
</div>
```

Available methods in Java JDI Light:

|Method | Description | Return Type
--- | --- | ---
**is()** | Returns object for work with assertions | DrawerAssert
**listItems()** | Returns List of element's list items | List
**lists()** | Returns List of element's Material UI Lists | List
**topList()** | Returns Material UI List at the top of the element | List
**bottomList()** | Returns Material UI List at the bottom of the element | List
**getWidth()** | Returns element's width | String
**getPosition()** | Returns element's position | String
**isHidden()** | Shows that element is hidden | boolean
**close()** | Closes element | void

##### <a href="https://github.com/jdi-testing/jdi-light/blob/Material-UI/jdi-light-material-ui-tests/src/test/java/io/github/epam/material/tests/navigation/DrawerTests.java" target="_blank">Here you can find Drawer tests</a>

<br></br>

### 4.32 Breadcrumbs

```java 
    //       @FindBy(css = ".MuiBreadcrumbs-root")
    @JDIBreadcrumbs(root = ".MuiBreadcrumbs-root")
    public static Breadcrumbs routerBreadcrumbs;
    
```

You can specify locators for the root, items and separators
explicitly through a `JDIBreadcrumbs` annotation:

```java    
    @JDIBreadcrumbs(
          root = ".MuiBreadcrumbs-root[1]",
          items = ".MuiBreadcrumbs-li .MuiTypography-root",
          separators = ".MuiBreadcrumbs-separator"
    )
    public static Breadcrumbs simpleBreadcrumbs;
 ```

```java   
    @Test
    public void routerIntegrationBreadcrumbsTest() {
        routerBreadcrumbs.has().values("Home", "Inbox");
        mailBoxList.get("Important").click();
        routerBreadcrumbs.has().values("Home", "Inbox", "Important");
        mailBoxList.get("Trash").click();
        routerBreadcrumbs.has().values("Home", "Trash");
        mailBoxList.get("Spam").click();
        routerBreadcrumbs.has().values("Home", "Spam");
        mailBoxList.get("Inbox").click();
        routerBreadcrumbs.has().values("Home", "Inbox");
    }
    
    @Test
    public void simpleBreadcrumbsTest() {
        simpleBreadcrumbs.has().values("Material-UI", "Core", "Breadcrumb");

        simpleBreadcrumbs.get("Material-UI").has().attr("href", containsString("#materialUI"));
        simpleBreadcrumbs.get("Material-UI").click();
        jdiAssert(simpleBreadcrumbsPage.driver().getCurrentUrl(), endsWith("#materialUI"));

        simpleBreadcrumbs.get("Core").has().attr("href", endsWith("#core"));
        simpleBreadcrumbs.get("Core").click();
        jdiAssert(simpleBreadcrumbsPage.driver().getCurrentUrl(), endsWith("#core"));

        simpleBreadcrumbs.separators().foreach(separator -> separator.has().text("/"));
    }
```

##### <a href="https://material-ui.com/components/Breadcrumbs/" target="_blank"> Breadcrumbs overview </a>

Breadcrumbs is located in the following class:

- __Java__: _com.epam.jdi.light.material.elements.navigation.Breadcrumbs_

__Breadcrumbs__ allow users to make selections from a range of values.

![Breadcrumbs](../../images/material-ui/Breadcrumbs.png)

Here is an example with provided MaterialUI v4.12.3 code:

```html

<nav class="MuiTypography-root MuiBreadcrumbs-root MuiTypography-body1 MuiTypography-colorTextSecondary"
     aria-label="breadcrumb">
  <ol class="MuiBreadcrumbs-ol">
    <li class="MuiBreadcrumbs-li">
      <a class="MuiTypography-root MuiLink-root MuiLink-underlineHover MuiTypography-colorInherit" href="#materialUI">Material-UI</a>
    </li>
    <li aria-hidden="true" class="MuiBreadcrumbs-separator">/</li>
    <li class="MuiBreadcrumbs-li">
      <a class="MuiTypography-root MuiLink-root MuiLink-underlineHover MuiTypography-colorInherit" href="#core">Core</a>
    </li>
    <li aria-hidden="true" class="MuiBreadcrumbs-separator">/</li>
    <li class="MuiBreadcrumbs-li">
      <p class="MuiTypography-root MuiTypography-body1 MuiTypography-colorTextPrimary">Breadcrumb</p>
    </li>
  </ol>
</nav>
```

Available methods in Java JDI Light:

|Method | Description | Return Type
--- | --- | ---
**list()** | Returns element's list | WebList
**separators()** | Returns element's separator list | WebList

##### <a href="https://github.com/jdi-testing/jdi-light/blob/master_material_ui/jdi-light-material-ui-tests/src/test/java/io/github/epam/material/tests/navigation/SimpleBreadcrumbsTests.java" target="_blank">Here</a> and <a href="https://github.com/jdi-testing/jdi-light/blob/master_material_ui/jdi-light-material-ui-tests/src/test/java/io/github/epam/material/tests/navigation/RouterBreadcrumbsTests.java" target="_blank">here you can find Breadcrumbs tests</a>

<br></br>

### 4.33 Bottom Navigation

```java
    //    @FindBy(css = ".MuiBottomNavigationAction-root")
    @UI(".MuiBottomNavigationAction-root")
    public static BottomNavigation bottomNavigationItems;

    @Test(dataProvider = "bottomNavigationButtons")
    public void defaultBottomNavigationTest(int index, String buttonText, String positionText) {
        bottomNavigationItems.select(index);
        bottomNavigationItems.has().selected(index);
        currentPosition.has().text(containsString(positionText));
        bottomNavigationItemsText.get(index).has().text(buttonText);
    }
```

##### <a href="https://material-ui.com/components/bottom-navigation/" target="_blank"> BottomNavigation overview </a>

BottomNavigation is located in the following class:

- __Java__: _com.epam.jdi.light.material.elements.navigation.BottomNavigation_

__Bottom navigation__ bars allow movement between primary destinations in an app.

![BottomNavigation](../../images/material-ui/BottomNavigation.png)

Here is an example with provided MaterialUI v4.12.3 code:

```html
<div class="MuiBottomNavigation-root jss44">
  <button class="MuiButtonBase-root MuiBottomNavigationAction-root Mui-selected" tabindex="0" type="button">
    <span class="MuiBottomNavigationAction-wrapper">
      <span class="MuiBottomNavigationAction-label Mui-selected">Recents</span>
    </span>
    <span class="MuiTouchRipple-root"></span>
  </button>
  <button class="MuiButtonBase-root MuiBottomNavigationAction-root" tabindex="0" type="button">
    <span class="MuiBottomNavigationAction-wrapper">
      <span class="MuiBottomNavigationAction-label">Favorites</span>
    </span>
    <span class="MuiTouchRipple-root"></span>
  </button>
  <button class="MuiButtonBase-root MuiBottomNavigationAction-root" tabindex="0" type="button">
    <span class="MuiBottomNavigationAction-wrapper">
      <span class="MuiBottomNavigationAction-label">Nearby</span>
    </span>
    <span class="MuiTouchRipple-root"></span>
  </button>
</div>
```

Available methods in Java JDI Light:

|Method | Description | Return Type
--- | --- | ---
**is()** | Returns object for work with assertions | BottomNavigation Assert
**selected** | Check if item is selected | boolean

##### <a href="https://github.com/jdi-testing/jdi-light/blob/master_material_ui/jdi-light-material-ui-tests/src/test/java/io/github/epam/material/tests/navigation/BottomNavigationTests.java" target="_blank">Here you can find Bottom Navigation tests</a>

<br></br>

### 4.34 Paper

```java 
    //   @FindBy(id = "paperElevation3")
    @UI("#paperElevation3")
    public static Paper elevationThreePaper;

    @Test
    public void elevationThreePaperTest() {
        elevationThreePaper.is().displayed();
        elevationThreePaper.has().elevation(3);
        elevationThreePaper.is().rounded();
    }
```

##### <a href="https://material-ui.com/components/paper/" target="_blank"> Paper overview </a>

Paper is located in the following class:

- __Java__: _com.epam.jdi.light.material.elements.surfaces.Paper_

In Material Design, the physical properties of paper are translated to the screen.

![Paper](../../images/material-ui/Paper.png)

Here is an example with provided MaterialUI v4.12.3 code:

```html

<div class="jss46">
  <div class="MuiPaper-root MuiPaper-elevation0 MuiPaper-rounded" id="paperElevation0">Paper with elevation = 0</div>
  <div class="MuiPaper-root MuiPaper-elevation1 MuiPaper-rounded" id="paperElevationDefault">Paper with default elavation</div>
  <div class="MuiPaper-root MuiPaper-elevation3 MuiPaper-rounded" id="paperElevation3">Paper with elevation = 3</div>
  <div class="MuiPaper-root MuiPaper-outlined MuiPaper-rounded" id="paperOutlined">Outlined paper</div>
  <div class="MuiPaper-root MuiPaper-outlined" id="paperOutlinedZero">Outlined square paper</div>
  <div class="MuiPaper-root MuiPaper-elevation1 MuiPaper-rounded" id="lastClickContent">You clicked:</div>
</div>
```

Available methods in Java JDI Light:

|Method | Description | Return Type
--- | --- | ---
**is()** | Returns object for work with assertions| PaperAssert

##### <a href="https://github.com/jdi-testing/jdi-light/blob/master_material_ui/jdi-light-material-ui-tests/src/test/java/io/github/epam/material/tests/surfaces/PaperTests.java" target="_blank">Here you can find Paper tests</a>

<br></br>

### 4.35 Accordion

```java
    // UIElement @FindBy(css = ".MuiAccordion-root[1]")
    // UIElement @FindBy(css = ".MuiButtonBase-root.MuiAccordionSummary-root")
    // List<UIElement> @FindBy(className = "MuiAccordionDetails-root")
    // Button @FindBy(className = "MuiIconButton-label")
    @JDropdown(
            root = ".MuiAccordion-root[1]",
            value = ".MuiButtonBase-root.MuiAccordionSummary-root",
            list = ".MuiAccordionDetails-root",
            expand = ".MuiIconButton-label")
    public static Accordion generalSettingsAccordion;

    @Test
    public void accordionExpandTest() {
        generalSettingsAccordion.is().enabled();
        generalSettingsAccordion.list().is().hidden();
        generalSettingsAccordion.expand();
        generalSettingsAccordion.list().is().displayed();
        generalSettingsAccordion.close();
        generalSettingsAccordion.is().collapsed();
        generalSettingsAccordion.list().is().hidden();
    }
```

##### <a href="https://mui.com/components/accordion/" target="_blank"> Accordion overview</a>

Accordion is located in the following class:

- __Java__: _com.epam.jdi.light.material.elements.surfaces.Accordion_

__The Accordion__ component allows the user to show and hide sections of related content on a page.

Accordions contain creation flows and allow lightweight editing of an element.

![Accordion](../../images/material-ui/Accordion.png)

Here is an example with provided MaterialUI v4.12.3 code:

```html
<div class="MuiPaper-root MuiAccordion-root MuiAccordion-rounded MuiPaper-elevation1 MuiPaper-rounded">
  <div class="MuiButtonBase-root MuiAccordionSummary-root" tabindex="0" role="button" aria-disabled="false"
       aria-expanded="false" aria-controls="panel1a-content" id="panel1a-header">
    <div class="MuiAccordionSummary-content">
      <p class="MuiTypography-root jss49 MuiTypography-body1">General settings</p>
      <p class="MuiTypography-root jss50 MuiTypography-body1">I am an accordion</p>
    </div>
    <div class="MuiButtonBase-root MuiIconButton-root MuiAccordionSummary-expandIcon MuiIconButton-edgeEnd"
         aria-disabled="false" aria-hidden="true">
      <span class="MuiIconButton-label"></span>
      <span class="MuiTouchRipple-root"></span>
    </div>
  </div>
  <div class="MuiCollapse-container MuiCollapse-hidden" style="min-height: 0px;">
    <div class="MuiCollapse-wrapper">
      <div class="MuiCollapse-wrapperInner">
        <div aria-labelledby="panel1a-header" id="panel1a-content" role="region">
          <div class="MuiAccordionDetails-root">
            <p class="MuiTypography-root MuiTypography-body1">Nulla facilisi. Phasellus sollicitudin nulla et quam mattis feugiat. Aliquam eget maximus est, id dignissim quam.</p>
          </div>
        </div>
      </div>
    </div>
  </div>
</div>
```

Available methods in Java JDI Light:

|Method | Description | Return Type
--- | --- | ---
**is()** | Returns object for work with assertions | DropdownAssert
**isEnabled()** | Checks whether element is enabled | boolean

##### <a href="https://github.com/jdi-testing/jdi-light/blob/master_material_ui/jdi-light-material-ui-tests/src/test/java/io/github/epam/material/tests/surfaces/AccordionTests.java" target="_blank">Here you can find Accordion tests</a>

<br></br>

### 4.36 Portal

```java 
    // @FindBy(css = ".MuiBox-root")
    @UI(".MuiBox-root")
    public static Portal portal;
    
    @Test
    public void portalTest() {
        portal.button().has().text("Mount children");
        portal.field(1).has().text(FIRST_FIELD_TEXT);
        portal.field(2).has().text("");

        portal.button().click();
        portal.button().has().text("Unmount children");
        portal.field(1).has().text(FIRST_FIELD_TEXT);
        portal.field(2).has().text("But I actually render here!");

        portal.button().click(0, 1);
        portal.button().has().text("Mount children");
        portal.field(1).has().text(FIRST_FIELD_TEXT);
        portal.field(2).has().text("");
    }
```

##### <a href="https://material-ui.com/components/Portal/" target="_blank"> Portal overview </a>

Portal is located in the following class:

- __Java__: _com.epam.jdi.light.material.elements.utils.Portal_

__The Portal__ component renders its children into a new "subtree" outside of current DOM hierarchy.

![Portal](../../images/material-ui/Portal.png)

Here is an example with provided MaterialUI v4.12.3 code:

```html
<div class="MuiBox-root jss183">
  <div><h1>Portal</h1>
    <div>
      <button type="button">Unmount children</button>
      <div class="jss184">It looks like I will render here.</div>
      <div class="jss184"><span>But I actually render here!</span></div>
    </div>
  </div>
</div>
```

Available methods in Java JDI Light:

|Method | Description | Return Type
--- | --- | ---
**is()** | Returns object for work with assertions| PortalAssert
**field(int)** | Returns required element's field| UIElement
**button()** | Returns element's button| UIElement

##### <a href="https://github.com/jdi-testing/jdi-light/blob/master_material_ui/jdi-light-material-ui-tests/src/test/java/io/github/epam/material/tests/utils/PortalTests.java" target="_blank">Here you can find Portal tests</a>

<br></br>

### 4.37 Textarea Autosize

```java 
    //    @FindBy(xpath = "//textarea[@aria-label = 'empty textarea']")
    @UI("//textarea[@aria-label = 'empty textarea']")
    public static TextArea emptyTextArea;
  
    @Test
    public void emptyAreaHeightIncreasesTest() {
      initialHeight = emptyTextArea.getSize().height;
      emptyTextArea.setLines(FOUR_LINES);
      assertThat(emptyTextArea.getSize().height, greaterThan(initialHeight));
    }

    @Test
    public void emptyAreaHeightDecreasesTest() {
      emptyTextArea.setLines(FOUR_LINES);
      initialHeight = emptyTextArea.getSize().height;
      emptyTextArea.clear();
      emptyTextArea.setLines(ONE_LINE);
      assertThat(emptyTextArea.getSize().height, lessThan(initialHeight));
    }
```

##### <a href="https://material-ui.com/components/textarea-autosize/" target="_blank"> TextArea Autosize overview </a>

TextArea is located in the following class:

- __Java__: _com.epam.jdi.light.ui.html.elements.common.TextArea_

__The Textarea__ component for React which grows with content.

![TextArea](../../images/material-ui/TextareaAutosize.png)

Here is an example with provided MaterialUI v4.12.3 code:

```html
<textarea rows="1" aria-label="empty textarea" placeholder="Empty" style="height: 21px; overflow: hidden;">
</textarea>
```

Available methods in Java JDI Light you can find in html `TextArea` class.

##### <a href="https://github.com/jdi-testing/jdi-light/blob/master_material_ui/jdi-light-material-ui-tests/src/test/java/io/github/epam/material/tests/utils/TextAreaAutoSizeTests.java" target="_blank">Here you can find TextAreaAutosize tests</a>

<br></br>

### 4.38 Popover

```java 
    //    @FindBy(css = ".MuiPopover-root .MuiPaper-root")
    @UI(".MuiPopover-root .MuiPaper-root")
    public static Popover popover;
    
    @Test
    public void clickPopoverTest() {
        popover.button(CLICK_BUTTON).click();
        popover.is().text(POPOVER_CONTENT);
        popover.button(CLICK_BUTTON).click(1, 0);
        popover.is().notVisible();
    }

    @Test
    public void hoverPopoverTest() {
        popover.button(HOVER_BUTTON).hover();
        popover.button(HOVER_BUTTON).has().attr("aria-owns", "mouse-over-popover");
        popover.is().text(POPOVER_CONTENT);
        popover.button(CLICK_BUTTON).hover();
        popover.is().notVisible();
    }
```

##### <a href="https://material-ui.com/components/popover/" target="_blank"> Popover overview </a>

Popover is located in the following class:

- __Java__: _com.epam.jdi.light.material.elements.utils.Popover_

__The Popover__ can be used to display some content on top of another.

![Popover](../../images/material-ui/Popover.png)

Here is an example with provided MaterialUI v4.12.3 code:

```html
<div class="MuiPaper-root MuiPopover-paper MuiPaper-elevation8 MuiPaper-rounded" tabindex="-1" style="opacity: 1; transform: none; transition: opacity 207ms cubic-bezier(0.4, 0, 0.2, 1) 0ms, transform 138ms cubic-bezier(0.4, 0, 0.2, 1) 0ms; top: 175px; left: 261px; transform-origin: 68.5px 0px;">
  <div class="jss55">Popover content</div>
</div>
```

Available methods in Java JDI Light:

|Method | Description | Return Type
--- | --- | ---
**is()** | Returns object for work with assertions| PopoverAssert
**button(String)** | Returns required element's button| UIElement

##### <a href="https://github.com/jdi-testing/jdi-light/blob/master_material_ui/jdi-light-material-ui-tests/src/test/java/io/github/epam/material/tests/utils/PopoverTests.java" target="_blank">Here you can find Popover tests</a>

<br></br>

### 4.39 Modal

```java 
    //    @FindBy(xpath = "//*[@role='presentation' and not(@aria-hidden='true')]")
    @UI("//*[@role='presentation' and not(@aria-hidden='true')]")
    public static Modal modal;

    //    @FindBy(css = "button")
    @UI("button")
    public static MaterialButton buttonModal;
    
    @Test
    public void modalTests() {
    
        buttonModal.click();
        for (int i = 0; i <= 3; i++) {
            modal.is().visible();
            modal.title().has().text("Text in a modal");
            modal.has().text(EXPECTED_TEXT);
            modal.find("button").click();
        }

        for (int i = 0; i <= 4; i++) {
            modal.close();
        }
        modal.is().notVisible();
    }
```

##### <a href="https://material-ui.com/components/modal/" target="_blank"> Modal overview </a>

Modal is located in the following class:

- __Java__: _com.epam.jdi.light.material.elements.utils.Modal_

__The Modal__ component provides a solid foundation for creating dialogs, popovers, lightboxes, or whatever else.

![Modal](../../images/material-ui/Modal.png)

Here is an example with provided MaterialUI v4.12.3 code:

```html
<div class="jss58" tabindex="-1" style="top: 53%; left: 59%; transform: translate(-53%, -59%);">
  <h2 id="simple-modal-title1">Text in a modal</h2>
  <p id="simple-modal-description1">Duis mollis, est non commodo luctus, nisi erat porttitor ligula.</p>
  <div>
    <h1>Modal windows</h1>
    <div>
      <button type="button">Open Modal</button>
    </div>
  </div>
</div>
<div role="presentation" aria-labelledby="simple-modal-title" aria-describedby="simple-modal-description" style="position: fixed; z-index: 1300; inset: 0px;">
  <div aria-hidden="true" style="z-index: -1; position: fixed; inset: 0px; background-color: rgba(0, 0, 0, 0.5); -webkit-tap-highlight-color: transparent;"></div>
  <div tabindex="0" data-test="sentinelStart"></div>
  <div class="jss178" tabindex="-1" style="top: 46%; left: 51%; transform: translate(-46%, -51%);">
    <h2 id="simple-modal-title2">Text in a modal</h2>
    <p id="simple-modal-description2">Duis mollis, est non commodo luctus, nisi erat porttitor ligula.</p>
    <div>
      <h1>Modal windows</h1>
      <div>
        <button type="button">Open Modal</button>
      </div>
    </div>
  </div>
  <div tabindex="0" data-test="sentinelEnd"></div>
</div>
```

Available methods in Java JDI Light:

|Method | Description | Return Type
--- | --- | ---
**is()** | Returns object for work with assertions| ModalAssert
**getText()** | Returns element's text| String
**title()** | Returns element's title| UIElement
**close()** | Closes element| void

##### <a href="https://github.com/jdi-testing/jdi-light/blob/master_material_ui/jdi-light-material-ui-tests/src/test/java/io/github/epam/material/tests/utils/ModalTests.java" target="_blank">Here you can find Modal tests</a>

<br></br>

### 4.40 Popper

```java
    // @FindBy(css = "[type=button]")
    @UI("[type=button]")
    public static List<TooltipButton> popperButton;
    
    @Test(dataProvider = "positionedPopperDataProvider")
    public void positionedPoppersTest(int number, String buttonText, Position position) {
        
        popperButton.get(number).has().text(buttonText);
        popperButton.get(number).click();
        popperButton.get(number).popper().assertThat().displayed();
        popperButton.get(number).popper().assertThat().text("The content of the Popper.");
        popperButton.get(number).popper().assertThat().position(position);
        popperButton.get(number).click();
        popperButton.get(number).popper().assertThat().notVisible();
    }
    
    @DataProvider
    public Object[][] positionedPopperDataProvider() {
        return new Object[][]{
                {1, "TOP", Position.TOP}, 
                {2, "LEFT", Position.LEFT}, 
                {3, "RIGHT", Position.RIGHT}, 
                {4, "BOTTOM", Position.BOTTOM}
        };
    }
```

##### <a href="https://material-ui.com/components/popper/" target="_blank"> Popper overview </a>

Popper is located in the following class:

- __Java__: _com.epam.jdi.light.material.elements.utils.Popper_

__A Popper__ can be used to display some content on top of another. It's an alternative to react-popper.

![Popper](../../images/material-ui/Popper.png)

Here is an example with provided MaterialUI v4.12.3 code:

```html
<div role="tooltip" id="positionedPopper" style="position: absolute; will-change: transform; top: 0px; left: 0px; transform: translate3d(415px, 82px, 0px);" x-placement="top">
  <div class="MuiPaper-root MuiPaper-elevation1 MuiPaper-rounded" style="opacity: 1; transition: opacity 350ms cubic-bezier(0.4, 0, 0.2, 1) 0ms;">
    <p class="MuiTypography-root jss61 MuiTypography-body1">The content of the Popper.</p>
  </div>
</div>
```

Available methods in Java JDI Light:

|Method | Description | Return Type
--- | --- | ---
**is()** | Returns object for work with assertions| PopperAssert
**position()** | Returns popper's position| String

##### <a href="https://github.com/jdi-testing/jdi-light/blob/master_material_ui/jdi-light-material-ui-tests/src/test/java/io/github/epam/material/tests/utils/PopperTests.java" target="_blank">Here you can find Popper tests</a>

<br></br>

### 4.41 Progress

```java
    //    @FindBy(xpath = "(//div[@aria-valuenow='100']/following-sibling::div)[1]")
    @JProgress(root = "(//div[@aria-valuenow='100']/following-sibling::div)[1]")
    public static CircularProgress circularDeterminateProgress;

    @Test
    public void circularDeterminateTest() {
        circularDeterminateProgress.is().displayed().and().determinate()
                .and().has().primaryColor();
        int valueNow = circularDeterminateProgress.getValueNow();
        timer.wait(() -> circularDeterminateProgress.has().value(valueNow + 10));
    }
```

##### <a href="https://material-ui.com/components/progress/" target="_blank"> Progress overview </a>

Abstract Progress and its descendants are located in the following classes:

- __Java__: 
  - _com.epam.jdi.light.material.elements.feedback.progress.Progress_
  - _com.epam.jdi.light.material.elements.feedback.progress.CircularProgress_
  - _com.epam.jdi.light.material.elements.feedback.progress.LinearProgress_

__Progress__ indicators commonly known as spinners, express an unspecified wait time or display the length of a process. The
animation works with CSS, not JavaScript.

![Progress](../../images/material-ui/Progress.png)

Here is an example with provided MaterialUI v4.12.3 code:

```html
<div class="MuiCircularProgress-root MuiCircularProgress-colorPrimary MuiCircularProgress-determinate" role="progressbar" aria-valuenow="30" style="width: 40px; height: 40px; transform: rotate(-90deg);">
  <svg class="MuiCircularProgress-svg" viewBox="22 22 44 44">
    <circle class="MuiCircularProgress-circle MuiCircularProgress-circleDeterminate" cx="44" cy="44" r="20.2" fill="none" stroke-width="3.6" style="stroke-dasharray: 126.92; stroke-dashoffset: 88.844px;"></circle>
  </svg>
</div>
```

Available methods in Java JDI Light:

- __Progress__

|Method | Description | Return Type
--- | --- | ---
**is()** | Returns object for work with assertions | ProgressAssert
**label()** | Returns progress label | Label
**getValueNow()** | Returns current element's value | int
**maxValue()** | Returns element's max limit | int
**minValue()** | Returns element's min limit | int
**getColor()** | Returns element's color | String
**isDisplayed()** | Checks whether the element is displayed | boolean
**isIndeterminate()** | Shows that element is indeterminate | boolean
**isDeterminate()** | Shows that element is determinate | boolean

- additional methods of __Circular Progress__

|Method | Description | Return Type
--- | --- | ---
**circle()** | Returns progress circle | UIElement

- additional methods of __Linear Progress__

|Method | Description | Return Type
--- | --- | ---
**is()** | Returns object for work with assertions | LinearProgressAssert
**bar1()** | Returns progress first bar | UIElement
**bar2()** | Returns progress second bar | UIElement
**firstBarColor()** | Returns first bar color | String
**secondBarColor()** | Returns second bar color | String
**isBuffer()** | Checks whether the progress is buffer | boolean

##### <a href="https://github.com/jdi-testing/jdi-light/blob/master_material_ui/jdi-light-material-ui-tests/src/test/java/io/github/epam/material/tests/feedback/ProgressTests.java" target="_blank">Here you can find Progress tests</a>

<br></br>

### 4.42 Link

```java 
    //    @FindBy(xpath = "//a[text()='Link']")
    @UI("//a[text()='Link']")
    public static Link link;

    //    @FindBy(css = "div a[href='#link2']")
    @Css("div a[href='#link2']")
    public static Link inheritColorLink;
    
    @Test
    public void defaultLinkTest() {
        link.is().displayed().and().enabled()
                .and().has().text("Link");

        link.has().cssClass("MuiLink-underlineHover");
        link.hover();
        link.is().underlined();

        inheritColorLink.hover();
        link.is().notUnderlined();

        link.click();
    }

    @Test
    public void colorInheritLinkTest() {
        inheritColorLink.is().displayed().and().enabled()
                .and().has().text(containsString("inherit"));

        inheritColorLink.has().cssClass("MuiTypography-colorInherit");
        inheritColorLink.has().color("rgba(0, 0, 0, 0.87)");

        inheritColorLink.click();
    }
```

##### <a href="https://material-ui.com/components/links/" target="_blank"> Link overview </a>

Link is located in the following class:

- __Java__: _com.epam.jdi.light.material.elements.navigation.Link_

__The Link__ component allows you to easily customize anchor elements with your theme colors and typography styles

![Links](../../images/material-ui/links.png)

Here is an example with provided MaterialUI v4.12.3 code:

```html
<a class="MuiTypography-root MuiLink-root MuiLink-underlineHover MuiTypography-colorPrimary" href="#link1">Link</a>
<a class="MuiTypography-root MuiLink-root MuiLink-underlineHover MuiTypography-colorInherit" href="#link2">color="inherit"</a>
```

Available methods in Java JDI Light:

|Method | Description | Return type
| --- | --- | --- 
**is()** | Returns object for work with assertions | LinkAssert
**isUnderlined()** | Checks that link is underlined | boolean
**isNotUnderlined()** | Checks that link is not underlined| boolean

##### <a href="https://github.com/jdi-testing/jdi-light/blob/master_material_ui/jdi-light-material-ui-tests/src/test/java/io/github/epam/material/tests/navigation/LinkTests.java" target="_blank">Here you can find Link tests</a>

<br></br>

### 4.43 Menus

```java 
    //  @FindBy(css = "span.MuiButton-label")
    @UI("span.MuiButton-label")
    public static Menu menu;

    //  @FindBy(css = "ul.MuiList-root.MuiMenu-list.MuiList-padding")
    @UI("ul.MuiList-root.MuiMenu-list.MuiList-padding")
    public static List simpleMenuList;

    //  @FindBy(xpath = "//*/p[starts-with(@class, 'MuiTypography')]")
    @UI("//*/p[starts-with(@class, 'MuiTypography')]")
    public static Menu contextMenu;

    //  @FindBy(css = "ul.MuiList-root.MuiMenu-list.MuiList-padding")
    @UI("ul.MuiList-root.MuiMenu-list.MuiList-padding")
    public static List contextMenuList;

    @Test
    public void simpleMenuTest() {
        menu.has().text("OPEN MENU");
        menu.click();
        simpleMenuList.is().displayed();
        menu.has().properMenuItems(simpleMenuList, SIMPLE_AND_SELECTED_MENU_ITEMS);
        simpleMenuList.selectItemByText("Profile");
        menu.is().displayed();
    }

    @Test
    public void contextMenuTest() {
        contextMenuPage.open();
        contextMenu.rightClick();
        menu.has().properMenuItems(contextMenuList, CONTEXT_MENU_ITEMS);
        contextMenuList.selectItemByText("Print");
        contextMenu.isDisplayed();
    }
```

##### <a href="https://material-ui.com/ru/components/menus/" target="_blank"> Menus overview </a>

Menu is located in the following class:

- __Java__: _com.epam.jdi.light.material.elements.navigation.Menu_

__Menus__ display a list of choices on temporary surfaces.

![SimpleMenu](../../images/material-ui/simpleMenu.png)
![Menu](../../images/material-ui/contextMenu.png)

Here is an example with provided MaterialUI v4.12.3 code:

```html
<div class="MuiPaper-root MuiMenu-paper MuiPopover-paper MuiPaper-elevation8 MuiPaper-rounded" tabindex="-1" style="opacity: 1; transform: none; transition: opacity 251ms cubic-bezier(0.4, 0, 0.2, 1) 0ms, transform 167ms cubic-bezier(0.4, 0, 0.2, 1) 0ms; top: 130px; left: 227px; transform-origin: 0px 26px;">
  <ul class="MuiList-root MuiMenu-list MuiList-padding" role="menu" tabindex="-1">
    <li class="MuiButtonBase-root MuiListItem-root MuiMenuItem-root MuiMenuItem-gutters MuiListItem-gutters MuiListItem-button" tabindex="0" role="menuitem" aria-disabled="false">Profile
      <span class="MuiTouchRipple-root"></span>
    </li>
    <li class="MuiButtonBase-root MuiListItem-root MuiMenuItem-root MuiMenuItem-gutters MuiListItem-gutters MuiListItem-button" tabindex="-1" role="menuitem" aria-disabled="false">My account
      <span class="MuiTouchRipple-root"></span>
    </li>
    <li class="MuiButtonBase-root MuiListItem-root MuiMenuItem-root MuiMenuItem-gutters MuiListItem-gutters MuiListItem-button" tabindex="-1" role="menuitem" aria-disabled="false">Logout
      <span class="MuiTouchRipple-root"></span>
    </li>
  </ul>
</div>
```

Available methods in Java JDI Light:

|Method | Description | Return type
| --- | --- | --- 
**has()** | Returns object for work with assertions  | MenuAssert
**is()** | Returns object for work with assertions | MenuAssert
**click()** | click | void
**rightClick()** | right-click | void
**scrollToMenuItem(List, String)** | scroll to menu item | void
**isDisplayed()** | return answer is displayed | boolean
**getText()** | return text | String
**getMenuItems(List)** | return list of menu items | List<String>

##### <a href="https://github.com/jdi-testing/jdi-light/blob/master_material_ui/jdi-light-material-ui-tests/src/test/java/io/github/epam/material/tests/navigation/MenuTests.java" target="_blank">Here you can find Menu tests</a>

<br></br>

### 4.44 Lists

```java
    // @FindBy(id = "simpleList")
    @UI("#simpleList")
    public static List simpleList;

    // @FindBy(id = "lastClickInfo")
    @UI("#lastClickInfo")
    public static Text simpleListLastClickInfo;

    @Test
    public void simpleListTests() {
        simpleList.items().get(0).click();
        String firstItemText = simpleList.items().get(0).getText();
        simpleListLastClickInfo.has().text(format("You clicked on: %s", firstItemText));

        simpleList.items().get(1).click();
        String secondItemText = simpleList.items().get(1).getText();
        simpleListLastClickInfo.has().text(format("You clicked on: %s", secondItemText));
    }
```

##### <a href="https://material-ui.com/components/lists/" target="_blank"> Lists overview </a>

List is located in the following class:

- __Java__: _com.epam.jdi.light.material.elements.displaydata.List_

__Lists__ are continuous groups of text or images. They are composed of items containing primary and supplemental actions,
which are represented by icons and text.

![simpleList](../../images/material-ui/simpleList.png)

Here are examples with provided MaterialUI v4.12.3 code:

```html
<nav class="MuiList-root MuiList-padding" aria-label="List items" id="simpleList">
  <div class="MuiButtonBase-root MuiListItem-root MuiListItem-gutters MuiListItem-button" tabindex="0" role="button" aria-disabled="false">
    <div class="MuiListItemText-root">
      <span class="MuiTypography-root MuiListItemText-primary MuiTypography-body1 MuiTypography-displayBlock">List item 1</span>
    </div>
    <span class="MuiTouchRipple-root"></span>
  </div>
  <a class="MuiButtonBase-root MuiListItem-root MuiListItem-gutters MuiListItem-button" tabindex="0" role="button" aria-disabled="false">
    <div class="MuiListItemText-root">
      <span class="MuiTypography-root MuiListItemText-primary MuiTypography-body1 MuiTypography-displayBlock">List item 2</span>
    </div>
    <span class="MuiTouchRipple-root"></span>
  </a>
</nav>
<p id="lastClickInfo">You clicked on: </p>
```

Available methods in Java JDI Light:

|Method | Description | Return type
| --- | --- | --- 
**is()** | Returns object for work with assertions | ListAssert
**items()** | Returns a Java list of list items | List\<ListItem>
**getItemByText(String)** | Returns first list item with specified text | ListItem
**selectItemByText(String)** | Clicks first list item with specified text | void
**nestedLists()** | Returns a Java list of Material UI lists nested directly within the list | List\<List>
**size()** | Returns list size | int
**isEmpty()** | Checks if a list does not contain any elements | boolean
**isDense()** | Checks if a list is dense | boolean
**subheaders()** | Returns list sub-headers as Java list of UIElements | List\<UIElement>

##### <a href="https://github.com/jdi-testing/jdi-light/blob/master_material_ui/jdi-light-material-ui-tests/src/test/java/io/github/epam/material/tests/displaydata/ListTests.java" target="_blank">Here you can find List tests</a>

#### 4.44.1 List Items

List Item is located in the following class:

- __Java__: _com.epam.jdi.light.material.elements.displaydata.ListItem_

**List Items** represent elements collected in a Material UI List. 

List item has a "primary area" which may contain an icon/avatar/checkbox, primary and secondary text. It can also support a primary action invoked by clicking on this area, like selecting the item.

List item also might have a "secondary area" containing a switch or button used to invoke a distinct secondary action.

Available methods in Java JDI Light:

|Method | Description | Return type
| --- | --- | --- 
**is()** | Returns object for work with assertions | ListItemAssert
**getText()** | Returns primary text of list item as string | String
**getPrimaryText()** | Returns properly marked primary text of list item as Text | Text
**getSecondaryText()** | Returns secondary text of list item | Text
**icon()** | Returns icon of list item | Icon
**avatar()** | Returns avatar of list item | Avatar
**checkbox()** | Returns checkbox of list item | Checkbox
**isSelected()** | Checks if a list item is selected | boolean
**secondaryActionButton()** | Returns secondary action button of list item | Button
**secondaryActionSwitch()** | Returns secondary action switch of list item | Switch

<br></br>

### 4.45 Transfer List

```java
    // @FindBy(css = ".MuiGrid-justify-xs-center")
    // @UI(".MuiGrid-justify-xs-center")
    @JDITransferList(root = "#root", allItemsLeftCheckbox = "(//span[./input[@aria-label='all items selected']])[1]",
      allItemsRightCheckbox = "(//span[./input[@aria-label='all items selected']])[2]")
    public static EnhancedTransferList enhancedTransferList;
    
    @Test
    public void enhancedTransferListTest() {
        enhancedTransferListPage.open();
        enhancedTransferList.assertThat().isMoveRightButtonDisable().and().isMoveLeftButtonDisable();

        enhancedTransferList.check(items.get(0));
        enhancedTransferList.is().checked(items.get(0));
        enhancedTransferList.is().isMoveRightButtonEnable();

        enhancedTransferList.uncheck(items.get(0));
        enhancedTransferList.is().unchecked(items.get(0));

        checkMoveElementsFunction(enhancedTransferList, items.toArray(new String[0]));
    }

    private static void checkMoveElementsFunction(TransferList transferList, String... checkingItems) {
        transferList.moveAllElementsRight();
        transferList.has().itemsMovedRight(checkingItems);
        transferList.moveAllElementsLeft();
        transferList.has().itemsMovedLeft(checkingItems);
    }
```

##### <a href="https://material-ui.com/components/transfer-list/" target="_blank"> Transfer List overview</a>

Abstract TransferList and its descendants are located in the following classes:

- __Java__:
_com.epam.jdi.light.material.elements.inputs.transferlist.TransferList_
_com.epam.jdi.light.material.elements.inputs.transferlist.SimpleTransferList_
_com.epam.jdi.light.material.elements.inputs.transferlist.EnhancedTransferList_

A **transfer list** (or "shuttle") enables the user to move one or more list items between lists.

Inner lists of a transfer list have the same methods as a regular List. 

![Enhanced Transfer Lists](../../images/material-ui/EnhancedTransferList.png)

Here is an example with provided MaterialUI v4.12.3 code:

```html

<div class="MuiGrid-root jss124 MuiGrid-container MuiGrid-spacing-xs-2 MuiGrid-align-items-xs-center MuiGrid-justify-xs-center">
  <div class="MuiGrid-root MuiGrid-item">
    <div class="MuiPaper-root MuiCard-root MuiPaper-elevation1 MuiPaper-rounded">
      <div class="MuiCardHeader-root jss125">
        <div class="MuiCardHeader-avatar">
          <span class="MuiButtonBase-root MuiIconButton-root jss106 MuiCheckbox-root MuiCheckbox-colorSecondary MuiIconButton-colorSecondary" aria-disabled="false">...</span>
        </div>
        <div class="MuiCardHeader-content">
          <span class="MuiTypography-root MuiCardHeader-title MuiTypography-body2 MuiTypography-displayBlock">Choices</span>
          <span class="MuiTypography-root MuiCardHeader-subheader MuiTypography-body2 MuiTypography-colorTextSecondary MuiTypography-displayBlock">0/4 selected</span>
        </div>
      </div>
      <hr class="MuiDivider-root">
      <div class="MuiList-root jss126 MuiList-dense MuiList-padding" role="list">
        <div class="MuiButtonBase-root MuiListItem-root MuiListItem-dense MuiListItem-gutters MuiListItem-button" tabindex="0" role="listitem" aria-disabled="false">
          <div class="MuiListItemIcon-root">
            <span class="MuiButtonBase-root MuiIconButton-root jss106 MuiCheckbox-root MuiCheckbox-colorSecondary MuiIconButton-colorSecondary" aria-disabled="false">...</span>
          </div>
          <div class="MuiListItemText-root MuiListItemText-dense" id="transfer-list-all-item-0-label">
            <span class="MuiTypography-root MuiListItemText-primary MuiTypography-body2 MuiTypography-displayBlock">List item 1</span>
          </div>
          <span class="MuiTouchRipple-root"></span>
        </div>
        <div class="MuiButtonBase-root MuiListItem-root MuiListItem-dense MuiListItem-gutters MuiListItem-button" tabindex="0" role="listitem" aria-disabled="false">
          <div class="MuiListItemIcon-root">
            <span class="MuiButtonBase-root MuiIconButton-root jss106 MuiCheckbox-root MuiCheckbox-colorSecondary MuiIconButton-colorSecondary" aria-disabled="false">...</span>
          </div>
          <div class="MuiListItemText-root MuiListItemText-dense" id="transfer-list-all-item-1-label">
            <span class="MuiTypography-root MuiListItemText-primary MuiTypography-body2 MuiTypography-displayBlock">List item 2</span>
          </div>
          <span class="MuiTouchRipple-root"></span>
        </div>
        <div class="MuiButtonBase-root MuiListItem-root MuiListItem-dense MuiListItem-gutters MuiListItem-button" tabindex="0" role="listitem" aria-disabled="false">
          <div class="MuiListItemIcon-root">
            <span class="MuiButtonBase-root MuiIconButton-root jss106 MuiCheckbox-root MuiCheckbox-colorSecondary MuiIconButton-colorSecondary" aria-disabled="false">...</span>
          </div>
          <div class="MuiListItemText-root MuiListItemText-dense" id="transfer-list-all-item-2-label">
            <span class="MuiTypography-root MuiListItemText-primary MuiTypography-body2 MuiTypography-displayBlock">List item 3</span>
          </div>
          <span class="MuiTouchRipple-root"></span>
        </div>
        <div class="MuiButtonBase-root MuiListItem-root MuiListItem-dense MuiListItem-gutters MuiListItem-button" tabindex="0" role="listitem" aria-disabled="false">
          <div class="MuiListItemIcon-root">
            <span class="MuiButtonBase-root MuiIconButton-root jss106 MuiCheckbox-root MuiCheckbox-colorSecondary MuiIconButton-colorSecondary" aria-disabled="false">...</span>
          </div>
          <div class="MuiListItemText-root MuiListItemText-dense" id="transfer-list-all-item-3-label">
            <span class="MuiTypography-root MuiListItemText-primary MuiTypography-body2 MuiTypography-displayBlock">List item 4</span>
          </div>
          <span class="MuiTouchRipple-root"></span>
        </div><li class="MuiListItem-root MuiListItem-dense MuiListItem-gutters"></li>
      </div>
    </div>
  </div>
  <div class="MuiGrid-root MuiGrid-item">
    <div class="MuiGrid-root MuiGrid-container MuiGrid-direction-xs-column MuiGrid-align-items-xs-center">
      <button class="MuiButtonBase-root MuiButton-root MuiButton-outlined jss127 MuiButton-outlinedSizeSmall MuiButton-sizeSmall Mui-disabled Mui-disabled" tabindex="-1" type="button" aria-label="move selected right" disabled="">...</button>
      <button class="MuiButtonBase-root MuiButton-root MuiButton-outlined jss127 MuiButton-outlinedSizeSmall MuiButton-sizeSmall Mui-disabled Mui-disabled" tabindex="-1" type="button" disabled="" aria-label="move selected left">...</button>
    </div>
  </div>
  <div class="MuiGrid-root MuiGrid-item">
    <div class="MuiPaper-root MuiCard-root MuiPaper-elevation1 MuiPaper-rounded">
      <div class="MuiCardHeader-root jss125">
        <div class="MuiCardHeader-avatar">
          <span class="MuiButtonBase-root MuiIconButton-root jss106 MuiCheckbox-root MuiCheckbox-colorSecondary MuiIconButton-colorSecondary" aria-disabled="false">...</span>
        </div>
        <div class="MuiCardHeader-content">
          <span class="MuiTypography-root MuiCardHeader-title MuiTypography-body2 MuiTypography-displayBlock">Chosen</span>
          <span class="MuiTypography-root MuiCardHeader-subheader MuiTypography-body2 MuiTypography-colorTextSecondary MuiTypography-displayBlock">0/4 selected</span>
        </div>
      </div><hr class="MuiDivider-root">
      <div class="MuiList-root jss126 MuiList-dense MuiList-padding" role="list">
        <div class="MuiButtonBase-root MuiListItem-root MuiListItem-dense MuiListItem-gutters MuiListItem-button" tabindex="0" role="listitem" aria-disabled="false">
          <div class="MuiListItemIcon-root">
            <span class="MuiButtonBase-root MuiIconButton-root jss106 MuiCheckbox-root MuiCheckbox-colorSecondary MuiIconButton-colorSecondary" aria-disabled="false">...</span>
          </div>
          <div class="MuiListItemText-root MuiListItemText-dense" id="transfer-list-all-item-4-label">
            <span class="MuiTypography-root MuiListItemText-primary MuiTypography-body2 MuiTypography-displayBlock">List item 5</span>
          </div>
          <span class="MuiTouchRipple-root"></span>
        </div>
        <div class="MuiButtonBase-root MuiListItem-root MuiListItem-dense MuiListItem-gutters MuiListItem-button" tabindex="0" role="listitem" aria-disabled="false">
          <div class="MuiListItemIcon-root">
            <span class="MuiButtonBase-root MuiIconButton-root jss106 MuiCheckbox-root MuiCheckbox-colorSecondary MuiIconButton-colorSecondary" aria-disabled="false">...</span>
          </div>
          <div class="MuiListItemText-root MuiListItemText-dense" id="transfer-list-all-item-5-label">
            <span class="MuiTypography-root MuiListItemText-primary MuiTypography-body2 MuiTypography-displayBlock">List item 6</span>
          </div>
          <span class="MuiTouchRipple-root"></span>
        </div>
        <div class="MuiButtonBase-root MuiListItem-root MuiListItem-dense MuiListItem-gutters MuiListItem-button" tabindex="0" role="listitem" aria-disabled="false">
          <div class="MuiListItemIcon-root">
            <span class="MuiButtonBase-root MuiIconButton-root jss106 MuiCheckbox-root MuiCheckbox-colorSecondary MuiIconButton-colorSecondary" aria-disabled="false">...</span>
          </div>
          <div class="MuiListItemText-root MuiListItemText-dense" id="transfer-list-all-item-6-label">
            <span class="MuiTypography-root MuiListItemText-primary MuiTypography-body2 MuiTypography-displayBlock">List item 7</span>
          </div>
          <span class="MuiTouchRipple-root"></span>
        </div>
        <div class="MuiButtonBase-root MuiListItem-root MuiListItem-dense MuiListItem-gutters MuiListItem-button" tabindex="0" role="listitem" aria-disabled="false">
          <div class="MuiListItemIcon-root">
            <span class="MuiButtonBase-root MuiIconButton-root jss106 MuiCheckbox-root MuiCheckbox-colorSecondary MuiIconButton-colorSecondary" aria-disabled="false">...</span>
          </div>
          <div class="MuiListItemText-root MuiListItemText-dense" id="transfer-list-all-item-7-label">
            <span class="MuiTypography-root MuiListItemText-primary MuiTypography-body2 MuiTypography-displayBlock">List item 8</span>
          </div>
          <span class="MuiTouchRipple-root"></span>
        </div>
        <li class="MuiListItem-root MuiListItem-dense MuiListItem-gutters"></li>
      </div>
    </div>
  </div>
</div>
```

Available methods in Java JDI Light:

- **Transfer List**

|Method | Description | Return Type
--- | --- | ---
**is()** | Returns object for work with assertions | TransferListAssert
**check(String)** | Checks required item | void
**isChecked(String)** | Shows that required item is checked | boolean
**uncheck(String)** | Unchecks required item | void
**isUnchecked(String)** | Shows that required item is unchecked | boolean
**isMoveRightButtonEnable()** | Shows that list's move right button is enable | boolean
**isMoveRightButtonDisable()** | Shows that list's move right button is disable | boolean
**isMoveLeftButtonEnable()** | Shows that list's move left button is enable | boolean
**isMoveLeftButtonDisable()** | Shows that list's move left button is disable | boolean
**isMoveLeftButtonDisable()** | Shows that list's move left button is disable | boolean

- additional methods of **Simple Transfer List**

|Method | Description | Return Type
--- | --- | ---
**moveAllElementsRight()** | Clicks "move all items to right inner list" button | void
**moveAllElementsLeft()** | Clicks "move all items to left inner list" button | void

- additional methods of **Enhanced Transfer List**

|Method | Description | Return Type
--- | --- | ---
**moveAllElementsRight()** | Clicks "move all items to right inner list" button | void
**moveAllElementsLeft()** | Clicks "move all items to left inner list" button | void

##### <a href="https://github.com/jdi-testing/jdi-light/blob/master_material_ui/jdi-light-material-ui-tests/src/test/java/io/github/epam/material/tests/inputs/TransferListTests.java" target="_blank">Here you can find Transfer List tests</a>

<br></br>

### 4.46 Text Field

```java 
    //    @FindBy(xpath = "//form[@id='formProps']/div[2]/div[contains(@class, 'MuiTextField-root')]")
    @UI("//form[@id='formProps']/div[2]/div[contains(@class, 'MuiTextField-root')]")
    public static List<TextField> validationTextFields;
    
    @Test
    public void validateTextFieldTests() {
        validationTextFields.get(1).has().text(HELLO_WORLD);
        validationTextFields.get(1).is().validationError();
        validationTextFields.get(1).click();
        validationTextFields.get(1).is().focused();
        validationTextFields.get(1).clear();
        validationTextFields.get(1).is().empty();
        validationTextFields.get(2).click();
        validationTextFields.get(1).has().placeholder();
        validationTextFields.get(1).has().placeholderText("Error");
        validationTextFields.get(1).sendKeys(randomString);
        validationTextFields.get(1).has().text(randomString);
        validationTextFields.get(1).label().has().text("Error");
    }
```
```java 
    //    @FindBy(xpath = "//form[@id='formProps']/div[5]/div[contains(@class, 'MuiFormControl-root')]")
    @UI("//form[@id='formProps']/div[5]/div[contains(@class, 'MuiFormControl-root')]")
    public static List<TextField> inputAdornmentsTextFields;
    
    @Test
    public void standardAdornmentTextFieldTests() {
        inputAdornmentsTextFields.get(1).adornment().has().position("start");
        inputAdornmentsTextFields.get(1).adornment().has().text("Kg");
        inputAdornmentsTextFields.get(1).click();
        inputAdornmentsTextFields.get(1).is().focused();
        inputAdornmentsTextFields.get(1).is().empty();
        inputAdornmentsTextFields.get(1).sendKeys(randomString);
        inputAdornmentsTextFields.get(1).has().text(randomString);
        inputAdornmentsTextFields.get(1).label().has().text("With normal TextField");
    }
```

##### <a href="https://material-ui.com/components/text-fields/" target="_blank"> Text Fields overview</a>

Text Field is located in the following class:

- __Java__: _com.epam.jdi.light.material.elements.inputs.TextField_

__The TextField__ wrapper component is a complete form control including a label, input and help text.
It supports standard, outlined and filled styling.

![Validation](../../images/material-ui/Validation.png)
![Input Adornments](../../images/material-ui/InputAdornments.png)

Here are examples with provided MaterialUI v4.12.3 code:

```html
<div>
  <div class="MuiFormControl-root MuiTextField-root">
    <label class="MuiFormLabel-root MuiInputLabel-root MuiInputLabel-formControl MuiInputLabel-animated MuiInputLabel-shrink MuiInputLabel-filled Mui-error Mui-error MuiFormLabel-filled" data-shrink="true" for="filled-error" id="filled-error-label">Error</label>
    <div class="MuiInputBase-root MuiFilledInput-root MuiFilledInput-underline Mui-error Mui-error MuiInputBase-formControl">
      <input aria-invalid="true" id="filled-error" type="text" class="MuiInputBase-input MuiFilledInput-input" value="Hello World">
    </div>
  </div>
  <div class="MuiFormControl-root MuiTextField-root">
    <label class="MuiFormLabel-root MuiInputLabel-root MuiInputLabel-formControl MuiInputLabel-animated MuiInputLabel-shrink MuiInputLabel-filled Mui-error Mui-error MuiFormLabel-filled" data-shrink="true" for="filled-error-helper-text" id="filled-error-helper-text-label">Error</label>
    <div class="MuiInputBase-root MuiFilledInput-root MuiFilledInput-underline Mui-error Mui-error MuiInputBase-formControl">
      <input aria-invalid="true" aria-describedby="filled-error-helper-text-helper-text" id="filled-error-helper-text" type="text" class="MuiInputBase-input MuiFilledInput-input" value="Hello World">
    </div>
    <p class="MuiFormHelperText-root MuiFormHelperText-contained Mui-error MuiFormHelperText-filled" id="filled-error-helper-text-helper-text">Incorrect entry.</p>
  </div>
</div>
```
```html
<div>
  <div class="MuiFormControl-root MuiTextField-root">
    <label class="MuiFormLabel-root MuiInputLabel-root MuiInputLabel-formControl MuiInputLabel-animated MuiInputLabel-shrink" data-shrink="true" for="standard-start-adornment" id="standard-start-adornment-label">With normal TextField</label>
    <div class="MuiInputBase-root MuiInput-root MuiInput-underline MuiInputBase-formControl MuiInput-formControl MuiInputBase-adornedStart">
      <div class="MuiInputAdornment-root MuiInputAdornment-positionStart">...</div>
      <input aria-invalid="false" id="standard-start-adornment" type="text" class="MuiInputBase-input MuiInput-input MuiInputBase-inputAdornedStart" value="">
    </div>
  </div>
  <div class="MuiFormControl-root">
    <div class="MuiInputBase-root MuiInput-root MuiInput-underline MuiInputBase-formControl MuiInput-formControl MuiInputBase-adornedEnd">
      <input aria-invalid="false" aria-describedby="standard-weight-helper-text" id="standard-adornment-weight" type="text" aria-label="weight" class="MuiInputBase-input MuiInput-input MuiInputBase-inputAdornedEnd" value="">
      <div class="MuiInputAdornment-root MuiInputAdornment-positionEnd">...</div>
    </div>
    <p class="MuiFormHelperText-root" id="standard-weight-helper-text">Weight</p>
  </div>
  <div class="MuiFormControl-root">
    <label class="MuiFormLabel-root MuiInputLabel-root MuiInputLabel-formControl MuiInputLabel-animated" data-shrink="false" for="standard-adornment-password">Password</label>
    <div class="MuiInputBase-root MuiInput-root MuiInput-underline MuiInputBase-formControl MuiInput-formControl MuiInputBase-adornedEnd">
      <input aria-invalid="false" id="standard-adornment-password" type="password" class="MuiInputBase-input MuiInput-input MuiInputBase-inputAdornedEnd" value="">
      <div class="MuiInputAdornment-root MuiInputAdornment-positionEnd">
        <button class="MuiButtonBase-root MuiIconButton-root" tabindex="0" type="button" aria-label="toggle password visibility">...</button>
      </div>
    </div>
  </div>
  <div class="MuiFormControl-root MuiFormControl-fullWidth">
    <label class="MuiFormLabel-root MuiInputLabel-root MuiInputLabel-formControl MuiInputLabel-animated MuiInputLabel-shrink" data-shrink="true" for="standard-adornment-amount">Amount</label>
    <div class="MuiInputBase-root MuiInput-root MuiInput-underline MuiInputBase-formControl MuiInput-formControl MuiInputBase-adornedStart">
      <div class="MuiInputAdornment-root MuiInputAdornment-positionStart">...</div>
      <input aria-invalid="false" id="standard-adornment-amount" type="text" class="MuiInputBase-input MuiInput-input MuiInputBase-inputAdornedStart" value="">
    </div>
  </div>
</div>
```

Available methods in Java JDI Light:

|Method | Description | Return Type
--- | --- | ---
|**is()** |Returns object for work with assertions| TextFieldAssert
|**setValue(String text)**|Input text| void
|**Clear()**|Clear data in Text Field| void
|**Click()**|Click on Text Field| void
|**GetText()**|Get current Text from Text Field| String

##### <a href="https://github.com/jdi-testing/jdi-light/blob/master_material_ui/jdi-light-material-ui-tests/src/test/java/io/github/epam/material/tests/inputs/TextFieldTests.java"  target="_blank">Here you can find Text Fields tests</a>

<br></br>

### 4.47 UseMediaQuery

```java
    //    @FindBy(xpath = "//span[contains(.,'min-width')]")
    @UI("//span[contains(.,'min-width')]")
    public static Text useMediaQueryText;
    
    @Test
    public void useMediaQueryTestWithDifferentScreenWidth() {
        useMediaQueryText.has().value(containsString("true"));
        useMediaQueryPage.driver().manage().window().setSize(new Dimension(500, 1000));
        useMediaQueryText.has().value(containsString("false"));
        useMediaQueryPage.driver().manage().window().setSize(new Dimension(700, 1000));
        useMediaQueryText.has().value(containsString("true"));
    }
```

##### <a href="https://material-ui.com/components/use-media-query/#usemediaquery" target="_blank"> useMediaQuery overview </a>

This is a CSS media query hook for React. It listens for matches to a CSS media query. It allows the rendering of
components based on whether the query matches or not.

![useMediaQuery](../../images/material-ui/useMediaQuery.png)

```html
<span>(min-width:600px) matches: true</span>
```

##### <a href="https://github.com/jdi-testing/jdi-light/blob/master_material_ui/jdi-light-material-ui-tests/src/test/java/io/github/epam/material/tests/utils/UseMediaQueryTests.java"  target="_blank">Here you can find useMediaQuery tests</a>

<br></br>

### 4.48 Alert

```java
    // @FindBy(xpath = "//div[contains(@class, 'MuiTypography-root')]/ancestor::*[contains(@class, 'MuiAlert-root')]")
    @UI("//div[contains(@class, 'MuiTypography-root')]/ancestor::*[contains(@class, 'MuiAlert-root')]")
    public static List<Alert> alertsWithDescription;
    
    @Test(dataProvider = "alertsWithDescriptionTestData", dataProviderClass = AlertDataProvider.class)
    public void alertsWithDescriptionTest(int alertIndex, String titleText, String messageText) {
        Alert alert = alertsWithDescription.get(alertIndex);
        alert.show();
        alert.is().displayed();
        alert.icon.is().displayed();
        alert.title.is().displayed().and().has().text(titleText);
        alert.has().text(Matchers.containsString(messageText));
    }
```

##### <a href="https://mui.com/components/alert/" target="_blank"> Alert overview</a>

Alert is located in the following class:

- __Java__: _com.epam.jdi.light.material.elements.feedback_

An __Alert__ displays a short, important message in a way that attracts the user's attention without interrupting the user's task.

![Alert](../../images/material-ui/Alert.png)

Here are examples with provided MaterialUI v4.12.3 code:

```html
<div class="MuiPaper-root MuiPaper-elevation MuiPaper-rounded MuiPaper-elevation0 MuiAlert-root MuiAlert-standardError MuiAlert-standard css-17y7f73" role="alert">
  <div class="MuiAlert-icon css-1l54tgj">
    <svg class="MuiSvgIcon-root MuiSvgIcon-fontSizeInherit css-1cw4hi4" focusable="false" aria-hidden="true" viewBox="0 0 24 24" data-testid="ErrorOutlineIcon">
      <path d="M11 15h2v2h-2zm0-8h2v6h-2zm.99-5C6.47 2 2 6.48 2 12s4.47 10 9.99 10C17.52 22 22 17.52 22 12S17.52 2 11.99 2zM12 20c-4.42 0-8-3.58-8-8s3.58-8 8-8 8 3.58 8 8-3.58 8-8 8z"></path>
    </svg>
  </div>
  <div class="MuiAlert-message css-1w0ym84">
    <div class="MuiTypography-root MuiTypography-body1 MuiTypography-gutterBottom MuiAlertTitle-root css-1jvvlz4">Error</div>
    This is an error alert — <strong>check it out!</strong>
  </div>
</div>
```

Available methods in Java JDI Light:

|Method | Description | Return Type
--- | --- | ---
|**is()** |Returns object for work with assertions| TextAssert
|**Icon()** |Returns alert's icon| Icon
|**Title()** |Returns alert's title| Text

##### <a href="https://github.com/jdi-testing/jdi-light/blob/master_material_ui/jdi-light-material-ui-tests/src/test/java/io/github/epam/material/tests/feedback/AlertTests.java"  target="_blank">Here you can find Alert tests</a>

<br></br><br></br>
