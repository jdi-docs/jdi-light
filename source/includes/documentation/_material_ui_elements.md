## Material UI elements

### Checkbox

#### <a href="https://material-ui.com/components/checkboxes/" target="_blank"> https://material-ui.com/components/checkboxes/ </a>

```java 
    @UI("//h2[text()='Basic checkboxes']/following-sibling::div[1]/span")
    public List<Checkbox> basicCheckbox;

    @Test
    public void basicCheckboxTest() {
        for (int i = 1; i < 3; i++)
            checkboxTestLogic(
                    checkboxPage.basicCheckbox.get(i),
                    i != 2 && i != 7 ? "MuiCheckbox-colorSecondary" :
                            i == 2 ? "MuiCheckbox-colorPrimary" : "jss3");
    }
    
    private void checkboxTestLogic(Checkbox checkbox, String className) {
        if (checkbox.isEnabled()) {
            checkbox.check();
            checkbox.is().checked();
            checkbox.uncheck();
            checkbox.is().unChecked();
        } else
            checkbox.is().disabled();
        checkbox.is().hasClass(className);
    }
```

Checkbox is located in the following class:

- __Java__: _com.epam.jdi.light.material.elements.inputs.Checkbox_

![Checkbox](../images/material-ui/Checkbox.png)

Checkboxes allow the user to select one or more items from a set.

|Method | Description | Return Type
--- | --- | ---
**is()** | Returns Assert class | Assert
**isDisabled()** | Verify state | boolean
**hasClassName(String className)** | Checks class| void
**checked()** | Assert that Checkbox selected | Assert
**uncheck()** | Assert that Checkbox not selected | Assert
**check()** | select Checkbox | void
**uncheck()** | unselect Checkbox | void


#### <a href="https://github.com/jdi-testing/jdi-light/blob/Material-UI/jdi-light-material-ui-tests/src/test/java/io/github/epam/material/tests/inputs/CheckboxTests.java" target="_blank">Here you can find Checkbox tests</a>

### Chips

#### <a href="https://material-ui.com/components/chips/" target="_blank"> https://material-ui.com/components/chips/ </a>

```java 
@JDIChip
@UI("//h2[text() = 'Chip']/following-sibling::*[1]")
public static Chip defaultChips;

@JDIChip
@UI("//h2[text() = 'Outlined Chips']/following-sibling::*[1]")
public static Chip outlinedChips;

@JDIChip
@UI("//h2[text() = 'Chip array']/following-sibling::*[1]")
public static Chip chipArrays;

@BeforeMethod
public void beforeTest() {
    chipsPage.open();
}

@Test
public void defaultChipTest(){
    basicCheck(defaultChips);
    disabledCheck(defaultChips);// first variant of class value
    clickableCheck(defaultChips,3);
    clickableLinkCheck(defaultChips,7);
}

@Test
public void outlinedChipTest(){
    basicCheck(outlinedChips);
    disabledCheck(outlinedChips); // second variant of class value
    clickableCheck(outlinedChips, 3);
    clickableLinkCheck(outlinedChips, 7);
}

@Test
public void chipArrayTest(){
    chipArrays.is().displayed(1);
    chipArrays.is().text(1, hasToString("Angular"));
    chipArrays.is().displayed(2);
    chipArrays.is().text(2, hasToString("jQuery"));
    chipArrays.getChipIcon(1).click();
    chipArrays.is().text(1, hasToString("jQuery")); // "jQuery" became first element as "Angular" element was deleted
}

public void basicCheck(Chip chips){
    chips.is().displayed(1);
    chips.is().text(1, hasToString("Basic"));
}
```

Chip is located in the following class:

- __Java__: _com.epam.jdi.light.material.elements.displaydata.Chip_

![Chip](../images/material-ui/Chip.png)

Chips are compact elements that represent an input, attribute, or action.

|Method | Description | Return Type
--- | --- | ---
**is()** | Returns Assert class | ChipAssert
**click(int index)** | Clicks on chip | void
**getChipLabel(int index)** | Gets label| UIElement
**getChipRoot(int index)** | Gets root| UIElement
**getChipIcon(int index)** | Gets Icon|UIElement

#### <a href="https://github.com/jdi-testing/jdi-light/blob/Material-UI/jdi-light-material-ui-tests/src/test/java/io/github/epam/material/tests/displaydata/ChipTests.java" target="_blank">Here you can find Chips tests</a>

### Tooltip

#### <a href="https://material-ui.com/components/tooltips/" target="_blank"> https://material-ui.com/components/tooltips/ </a>

```java 
@UI("//*[contains(@class, 'MuiIconButton-root')]")
public ButtonWithTooltip buttonWithTooltip;

@Test
public void defaultTooltipTest() {
    tooltipPage.open();
    tooltipPage.buttonWithTooltip.hover();
    tooltipPage.buttonWithTooltip.tooltip().is().visible();
    tooltipPage.buttonWithTooltip.tooltip().has().text("Delete");
}
```

Tooltip is located in the following class:

- __Java__: _com.epam.jdi.light.material.elements.displaydata.Tooltip_

![Tooltip](../images/material-ui/Tooltip.png)

Tooltips display informative text when users hover over, focus on, or tap an element.

|Method | Description | Return Type
--- | --- | ---
**is()** | Returns Assert class | TooltipAssert
**has()** | Returns Assert class | TooltipAssert
**isVisible()** | Checks element is displayed| boolean
**isInteractive()** | Checks element is interactive| boolean
**getValue()** | Gets value| String

#### <a href="https://github.com/jdi-testing/jdi-light/blob/Material-UI/jdi-light-material-ui-tests/src/test/java/io/github/epam/material/tests/displaydata/TooltipTests.java" target="_blank">Here you can find Tooltip tests</a>

### Container

#### <a href="https://material-ui.com/components/container/" target="_blank"> https://material-ui.com/components/container/ </a>

```java 
    @UI("//div[contains(@Class, 'MuiTypography-body1')]")
    public static UIElement container;

    @Test
    public void defaultContainerTest(){
        Timer timer = new Timer(1000L);
        timer.wait(() -> container.isDisplayed());
        container.is().text("Example text");
        container.is().attr("style", "background-color: rgb(207, 232, 252); height: 100vh;");
    }
```

![Container](../images/material-ui/Container.png)

The container centers your content horizontally. It's the most basic layout element.

|Method | Description | Return Type
--- | --- | ---
**is()** | Verify state | boolean
**isDisplayed()** | Verify state | boolean


#### <a href="https://github.com/jdi-testing/jdi-light/blob/Material-UI/jdi-light-material-ui-tests/src/test/java/io/github/epam/material/tests/layout/ContainerTests.java" target="_blank">Here you can find Container tests</a>


### Avatar

#### <a href="https://material-ui.com/ru/components/avatars/" target="_blank"> https://material-ui.com/ru/components/avatars/ </a>

```java 
    @UI("//span[@class='MuiBadge-root']/span")
    public static List<UIElement> onlineStatus;
    
    @UI("//span[@class='MuiBadge-root']/following-sibling::div")
    public static List<UIElement> avatarWithoutPhoto;
    
    @UI("//span[@class='MuiBadge-root']/div")
    public static List<UIElement> avatarWithPhoto;

    @Test
    public void avatarTests() {
        Timer timer = new Timer(1000L);
        timer.wait(() -> onlineStatus.get(1).is().displayed());
        basicAvatarChecks(avatarWithoutPhoto, true);
        basicAvatarChecks(avatarWithPhoto, false);
        onlineStatus.get(1).has().classValue(Matchers.containsString("MuiBadge-dot"));
        onlineStatus.get(2).has().text("R");
        onlineStatus.get(2).has().classValue(Matchers.containsString("MuiBadge-anchorOriginBottomRightCircle"));
    }
```

![Avatar](../images/material-ui/Avatar.png)

Avatars are found throughout material design with uses in everything from tables to dialog menus.

|Method | Description | Return Type
--- | --- | ---
**hasImage()** | Checks image | boolean
**classValue()** | Checks class | boolean
**isDisplayed()** | Verify state | void
**text()** | Asserts text | Assert
**has()** | Verify state | boolean

#### <a href="https://github.com/jdi-testing/jdi-light/blob/Material-UI/jdi-light-material-ui-tests/src/test/java/io/github/epam/material/tests/displaydata/AvatarTests.java" target="_blank">Here you can find Avatar tests</a>

### Click Away Listener

#### <a href="https://material-ui.com/ru/components/click-away-listener/" target="_blank"> https://material-ui.com/ru/components/click-away-listener/ </a>

```java     
    @UI("//h2[text()='Example']/following-sibling::div[1]/div/button")
    public static Button exampleButton;

    @UI("//h2[text()='Portal']/following-sibling::div[1]/div/button")
    public static Button portalButton;

    @UI("//div[text()='Click me, I will stay visible until you click outside.']")
    public static TextArea text;

    @Test
    public void exampleClickAwayListenerTest() {
        textFieldTest(1);
    }

    @Test
    public void portalExampleClickAwayListenerTest() {
        textFieldTest(2);
    }

    private void textFieldTest(int buttonId) {
        clickAwayListenerPage.clickButton(buttonId);
        text.is().displayed();
        clickAwayListenerPage.clickButton(buttonId);
        text.is().hidden();
        clickAwayListenerPage.clickButton(buttonId);
        text.is().displayed();
        clickAwayListenerPage.clickAroundTextPopup(text.getSize().width + 1, -1);
        text.is().hidden();
        clickAwayListenerPage.clickButton(buttonId);
        clickAwayListenerPage.clickAroundButton(exampleButton.getSize().width + 1,0, buttonId);
        text.is().hidden();
    }
```

![ClickAwayListener](../images/material-ui/ClickAwayListener.png)

Detect if a click event happened outside of an element. It listens for clicks that occur somewhere in the document.

|Method | Description | Return Type
--- | --- | ---
**click()** | Clicks on box | void
**click(int x, int y)** | Clicks on point in box | void
**is()** | Returns Assert class | Assert
**displayed()** | Assert state | Assert
**hidden()** | Assert state | Assert

#### <a href="https://github.com/jdi-testing/jdi-light/blob/Material-UI/jdi-light-material-ui-tests/src/test/java/io/github/epam/material/tests/utils/ClickAwayListenerTests.java" target="_blank">Here you can find ClickAwayListener tests</a>

### Divider

#### <a href="https://material-ui.com/components/dividers/" target="_blank"> https://material-ui.com/components/dividers/ </a>

```java 
    @UI("(//li[contains(@class, 'MuiDivider-root')])")
    public static List<Divider> insetDividers;
    
    @UI(".MuiDivider-root")
    public static Divider verticalDivider;

    @Test
    public void insetDividerTest() {
        insetDividers.forEach(
            d-> d.is().inset()
        );
    }
    
    @Test
    public void verticalDividerTest() {
        verticalDivider.is().vertical();
    }
```

Divider is located in the following class:

- __Java__: _com.epam.jdi.light.material.elements.displaydata.Divider_

![InsetDivider](../images/material-ui/InsetDivider.png)
![VerticalDivider](../images/material-ui/VerticalDivider.png)

A divider is a thin line that groups content in lists and layouts.

|Method | Description | Return Type
--- | --- | ---
**is()** | Returns DividerAssert class | DividerAssert
**isInset()** | Assert inset divider | boolean
**isVertical()** | Assert vertical divider| boolean


#### <a href="https://github.com/jdi-testing/jdi-light/blob/Material-UI/jdi-light-material-ui-tests/src/test/java/io/github/epam/material/tests/displaydata/DividerTests.java" target="_blank">Here you can find Divider tests</a>

### Card

#### <a href="https://material-ui.com/components/cards/" target="_blank"> https://material-ui.com/components/cards/ </a>

```java    
    @UI("//div[@class='MuiCardContent-root']/p[1]")
    public static List<Text> pTagTexts;

    @UI("//div[@class='MuiCardContent-root']/h2[1]")
    public static List<Text> h2TagTexts;

    @UI("//div[@class='MuiCardActions-root']/button[1]")
    public static Button complexCardHeartIconButton;

    @UI("//div[@class='MuiCardActions-root']/button[1]/span[1]/*")
    public static Icon complexCardHeartIcon;

    @UI("//div[@class='MuiCardActions-root']/button[3]")
    public static Button complexCardSliderDownButton;

    @UI("//div[@class='MuiCardActions-root']/preceding-sibling::div[2]")
    public static Image complexCardImage;

    @UI("//div[@class='MuiCardActions-root']/following-sibling::div[1]")
    public static TextArea complexCardHiddenTextArea;

    @UI("//div[@class='MuiCardActions-root']/following-sibling::div[1]/div/div/div/p[1]")
    public static Text complexCardHiddenText;

    private void textCheck(int index) {
        pTagTexts.get(index).has().text(Matchers.is("Word of the Day"));
        h2TagTexts.get(index).has().text(Matchers.is("be•nev•o•lent"));
    }

    @Test
    public void complexCardTest() {
        String expectedText = "This impressive paella is a perfect party dish and a fun meal to cook together with your guests. Add 1 cup of frozen peas along with the mussels, if you like.";
        pTagTexts.get(3).has().text(Matchers.is(expectedText));
        complexCardImage.is().displayed();

        complexCardHeartIconButton.click();
        new Timer(1000L)
                .wait(() -> complexCardHeartIcon.has().classValue(Matchers.containsString("jss")));

        complexCardHeartIconButton.click();
        new Timer(1000L)
                .wait(() -> complexCardHeartIcon.has().classValue(Matchers.not("jss")));

        complexCardSliderDownButton.click();
        complexCardHiddenTextArea.is().displayed();
        complexCardHiddenText.has().text(Matchers.containsString("Method:"));
    }
```

![Сard](../images/material-ui/Card.png)

Cards contain content and actions about a single subject.

|Method | Description | Return Type
--- | --- | ---
**click()** | Clicks on box | void
**is()** | Returns Assert class | Assert
**displayed()** | Assert state | Assert
**hidden()** | Assert state | Assert
**classValue()** | Assert state | Assert

#### <a href="https://github.com/jdi-testing/jdi-light/blob/Material-UI/jdi-light-material-ui-tests/src/test/java/io/github/epam/material/tests/surfaces/CardTests.java" target="_blank">Here you can find Card tests</a>

### Radio

#### <a href="https://material-ui.com/components/radio-buttons/" target="_blank"> https://material-ui.com/components/radio-buttons/ </a>

```java 
    @UI("//fieldset[@id='simpleRadio']//span[contains(@Class,'MuiRadio-root')]")
    public static List<Button> simpleRadioButtons;

    @UI("//fieldset[@id='simpleRadio']//span[contains(@Class,'MuiFormControlLabel-label')]")
    public static List<Button> simpleRadioButtonsLabel;

    static private final List<String> labels = Arrays.asList("First", "Second", "Third", "Disabled");
    static private final List<String> classes = Arrays.asList("Top", "Start", "Bottom");
    static private final List<String> messages = Arrays.asList("You got it!", "Sorry, wrong answer!");
    static private final Timer timer = new Timer(2000L);

    @Test
    public void simpleRadioTest() {
        for (int i = 1; i <= 4; i++) {
            Button currentRadioButton = simpleRadioButtons.get(i);
            Button currentRadioButtonLabel = simpleRadioButtonsLabel.get(i);
            if (i != 4) {
                currentRadioButton.click();
                timer.wait(() -> currentRadioButton.has().classValue(containsString("Mui-checked")));
                lastRadioText.has().text(containsString(currentRadioButton.text()));
            }
            else
                timer.wait(() -> currentRadioButton.has().classValue(containsString("Mui-disabled")));
            currentRadioButtonLabel.has().text(labels.get(i - 1));
        }
    }
```

![Radio](../images/material-ui/Radio.png)

Radio buttons allow the user to select one option from a set.

|Method | Description | Return Type
--- | --- | ---
**click()** | Clicks on box | void
**click(int x, int y)** | Clicks on point in box | void
**is()** | Returns Assert class | Assert
**displayed()** | Assert state | Assert
**hidden()** | Assert state | Assert

#### <a href="https://github.com/jdi-testing/jdi-light/blob/Material-UI/jdi-light-material-ui-tests/src/test/java/io/github/epam/material/tests/inputs/RadioButtonTests.java" target="_blank">Here you can find Radio tests</a>

### App Bar

#### <a href="https://material-ui.com/components/app-bar/" target="_blank"> https://material-ui.com/components/app-bar/ </a>

```java 
    @UI("//*[text()='App Bar with menu']/preceding::button[@aria-label='menu']")
    public static UIElement simpleMenu;

    @UI("//*[text()='Prominent App Bar']/preceding::button[@aria-label='menu'][1]")
    public static UIElement appBarMenu;

    @UI("//*[text()='Prominent App Bar']/following::button[@aria-label='open drawer']")
    public static UIElement prominentMenu;

    @UI("//*[text()='Simple App bar']/following::h6[1]")
    public static Text simpleText;

    @UI("//*[text()='App Bar with menu']/following::h6")
    public static Text appBarText;

    @UI("//*[text()='Prominent App Bar']/following::h5")
    public static Text prominentText;

    @UI("//*[text()='Simple App bar']/following::button[2]")
    public static Button simpleButton;

    @Test
    public void simpleAppBarTest() {
        simpleAppBarPage.open();
        simpleAppBarPage.shouldBeOpened();
        simpleMenu.isDisplayed();
        appBarMenu.isDisplayed();
        prominentMenu.isDisplayed();
        simpleText.has().text("News");
        appBarText.has().text("Photos");
        prominentText.has().text("Material-UI");
        simpleButton.is().displayed();
        appBarIcon.is().displayed();
        prominentSearch.is().displayed();
        prominentSecondMenu.is().displayed();
        logoutSwitchButton.click();
        timer.wait(() -> appBarIcon.isNotVisible());
        logoutSwitchButton.click();
        timer.wait(() -> appBarIcon.isDisplayed());
        appBarIcon.click();
        timer.wait(() -> appBarIconOptions.get(1).isDisplayed());
        appBarIconOptions.get(1).click();
        timer.wait(() -> {
            appBarIconOptions.get(1).isNotVisible();
            appBarIcon.isVisible();
        });
    }
```

![AppBar](../images/material-ui/AppBar.png)

The App Bar displays information and actions relating to the current screen.

|Method | Description | Return Type
--- | --- | ---
**click()** | Clicks on element | void
**click(int x, int y)** | Clicks on point in element | void
**is()** | Returns Assert class | Assert
**has()** | Returns Assert class | Assert
**displayed()** | Assert state | Assert
**hidden()** | Assert state | Assert

#### <a href="https://github.com/jdi-testing/jdi-light/blob/Material-UI/jdi-light-material-ui-tests/src/test/java/io/github/epam/material/tests/surfaces/AppBarTests.java" target="_blank">Here you can find AppBar tests</a>

### Box

#### <a href="https://material-ui.com/components/box/" target="_blank"> https://material-ui.com/components/box/ </a>

```java     
    @UI("//button[contains(@class,'MuiButton-outlined')]")
    public static Button outlinedBox;

    @Test
    public void outlinedBoxTest() {
        outlinedBox.is().displayed();
        outlinedBox.click();
        outlinedBox.is().text("SECOND BUTTON");
        lastClickContent.is().text("You clicked Second button");
    }
```

The Box component serves as a wrapper component for most of the CSS utility needs.
Java example code for the Button box:

![Box](../images/material-ui/Box.png)

|Method | Description | Return Type
--- | --- | ---
**is()** | Verify state | boolean
**click()** | Clicks on box | void
**displayed()** | Verify state | void
**text()** | Verify text | void

#### <a href="https://github.com/jdi-testing/jdi-light/blob/Material-UI/jdi-light-material-ui-tests/src/test/java/io/github/epam/material/tests/layout/BoxTests.java" target="_blank">Here you can find Box tests</a>

### Transitions

#### <a href="https://material-ui.com/components/transitions/" target="_blank"> https://material-ui.com/components/transitions/ </a>

```java     
    @UI("//h1[text()='Transitions']/following::div[contains(@class,'MuiCollapse-container')]")
    public static List<UIElement> collapseFadeTransitions;

    @UI("//span[@class='MuiSwitch-root']")
    public static List<Checkbox> checkboxes;
    
    @Test
    public void collapseDisplayTest() {
      Timer timer = new Timer(2000L);

      collapseFadeTransitions.get(1).has().classValue(not(containsString("MuiCollapse-entered")));
      collapseFadeTransitions.get(2).has().classValue(not(containsString("MuiCollapse-entered")));

      checkboxes.get(1).check();

      timer.wait(() -> collapseFadeTransitions.get(1).hasClass(containsString("MuiCollapse-entered").toString()));
      collapseFadeTransitions.get(1).has().classValue(containsString("MuiCollapse-entered"));
      collapseFadeTransitions.get(2).has().classValue(containsString("MuiCollapse-entered"));
    }
```

Transition helps make a UI expressive and easy to use.

![Transitions](../images/material-ui/Transitions.png)

|Method | Description | Return Type
--- | --- | ---
**has()** | Verify state | boolean
**hasClass()** | Verify state | boolean
**classValue()** | Verify state | boolean
**check()** | Checkbox selected | void

#### <a href="https://github.com/jdi-testing/jdi-light/blob/Material-UI/jdi-light-material-ui-tests/src/test/java/io/github/epam/material/tests/utils/TransitionTests.java" target="_blank">Here you can find Transitions tests</a>

### Material Icons

```java     
    @UI("#defaultAccessAlarm")
    public static UIElement defaultAlarm;

    @UI("#largeAccessAlarm")
    public static UIElement largeAlarm;

    @UI("#secondaryAccessAlarm")
    public static UIElement secondaryAlarm;

    @UI("#miconLastClick")
    public static UIElement lastClick;

    @UI("#miconLastHover")
    public static UIElement lastHover;

    @Test
    public void defaultMaterialIconTest() {
        lastClick.is().text("Last click:");
        lastHover.is().text("Last hover:");

        defaultAlarm.hover();
        lastClick.is().text("Last click:");
        lastHover.is().text("Last hover: default");

        defaultAlarm.click();
        lastClick.is().text("Last click: default");
        lastHover.is().text("Last hover: default");

        largeAlarm.hover();
        lastClick.is().text("Last click: default");
        lastHover.is().text("Last hover: large");

        largeAlarm.click();
        lastClick.is().text("Last click: large");
        lastHover.is().text("Last hover: large");

        secondaryAlarm.hover();
        lastClick.is().text("Last click: large");
        lastHover.is().text("Last hover: secondary");

        secondaryAlarm.click();
        lastClick.is().text("Last click: secondary");
        lastHover.is().text("Last hover: secondary");
    }
```

#### <a href="https://material-ui.com/components/material-icons/" target="_blank"> https://material-ui.com/components/material-icons/ </a>

The following npm package, @material-ui/icons, includes the 1,100+ official Material icons converted to SvgIcon components.

![Material Icons](../images/material-ui/MaterialIcons.png)

|Method | Description | Return Type
--- | --- | ---
**is()** | Verify state | boolean
**displayed()** | Verify state | boolean
**hasClass()** | Verify state | boolean
**text()** | Verify text | boolean
**click()** | Clicks on box | void
**hover()** | Hovers on box | void

#### <a href="https://github.com/jdi-testing/jdi-light/blob/master/jdi-light-material-ui-tests/src/test/java/io/github/epam/material/tests/displaydata/MaterialIconTests.java" target="_blank">Here you can find Material Icons tests</a>

### Icons

#### <a href="https://material-ui.com/components/icons/" target="_blank"> https://material-ui.com/components/icons/ </a>

```java     
    @UI("//h2[text()='Color']/following::*[name()='svg']")
    public static List<UIElement> color;

    @UI("#colorLastClick")
    public static Text colorLastClick;

    @UI("#colorLastHover")
    public static Text colorLastHover;

    @Test
    public void colorIconsTest() {
        color.forEach(el -> el.is().displayed());
        colorLastClick.is().text("Last click:");
        colorLastHover.is().text("Last hover:");

        Map<UIElement, List<List<String>>> allColorIcons = new LinkedHashMap<>();
        allColorIcons.put(color.get(1), Arrays.asList(Arrays.asList("", " default"), Arrays.asList(" default", " default")));
        allColorIcons.put(color.get(2), Arrays.asList(Arrays.asList(" default", " primary"), Arrays.asList(" primary", " primary")));
        allColorIcons.put(color.get(3), Arrays.asList(Arrays.asList(" primary", " secondary"), Arrays.asList(" secondary", " secondary")));
        allColorIcons.put(color.get(4), Arrays.asList(Arrays.asList(" secondary", " action"), Arrays.asList(" action", " action")));
        allColorIcons.put(color.get(5), Arrays.asList(Arrays.asList(" action", " disabled"), Arrays.asList(" disabled", " disabled")));
        allColorIcons.put(color.get(6), Arrays.asList(Arrays.asList(" disabled", " green[500]"), Arrays.asList(" green[500]", " green[500]")));

        allColorIcons.forEach(
                (k, v) -> {
                    k.hover();
                    colorLastClick.is().text(String.format("Last click:%s", v.get(0).get(0)));
                    colorLastHover.is().text(String.format("Last hover:%s", v.get(0).get(1)));
                    k.click();
                    colorLastClick.is().text(String.format("Last click:%s", v.get(1).get(0)));
                    colorLastHover.is().text(String.format("Last hover:%s", v.get(1).get(1)));
                }
        );
    }
```

Material-UI provides icons support in three ways:

1. Standardized Material Design icons exported as React components (SVG icons).
2. With the SvgIcon component, a React wrapper for custom SVG icons.
3. With the Icon component, a React wrapper for custom font icons.

![Icons](../images/material-ui/Icon.png)

|Method | Description | Return Type
--- | --- | ---
**is()** | Verify state | boolean
**displayed()** | Verify state | boolean
**text()** | Verify text | boolean
**click()** | Clicks on box | void
**hover()** | Hovers on box | void

#### <a href="https://github.com/jdi-testing/jdi-light/blob/master/jdi-light-material-ui-tests/src/test/java/io/github/epam/material/tests/displaydata/IconTests.java" target="_blank">Here you can find Icons tests</a>

### Floating Action Button

#### <a href="https://material-ui.com/components/floating-action-button/" target="_blank"> https://material-ui.com/components/floating-action-button/ </a>

```java     
    @UI("//div[@id='basicActionBtns']/button")
    public static List<Button> basicBtns;

    @UI("//button[@aria-label='add']")
    public static Button addBtn;

    @UI("//button[@aria-label='edit']")
    public static Button editBtn;

    @UI("//button[contains(@class,'MuiFab-extended')]")
    public static Button extendedBtn;

    @UI("//button[@aria-label='like']")
    public static Button disabledBtn;

    @UI("#basicActionBtnsLastClick")
    public static Text basicBtnsLastClick;

    @Test
    public void basicButtonsTest() {
        basicBtns.forEach(el -> el.is().displayed());
        basicBtnsLastClick.is().text("Last click:");

        addBtn.is().enabled();
        addBtn.click();
        basicBtnsLastClick.is().text("Last click: Add");

        editBtn.is().enabled();
        editBtn.click();
        basicBtnsLastClick.is().text("Last click: Edit");

        extendedBtn.is().enabled();
        extendedBtn.click();
        basicBtnsLastClick.is().text("Last click: Navigate");

        disabledBtn.is().disabled();
    }
```

A floating action button appears in front of all screen content, typically as a circular shape with an icon in its center. FABs come in two types: regular, and extended.

![Floating action button](../images/material-ui/Fab.png)

|Method | Description | Return Type
--- | --- | ---
**is()** | Verify state | boolean
**displayed()** | Verify state | boolean
**enabled()** | Verify state | boolean
**disabled()** | Verify state | boolean
**text()** | Verify text | boolean
**click()** | Clicks on box | void

#### <a href="https://github.com/jdi-testing/jdi-light/blob/master/jdi-light-material-ui-tests/src/test/java/io/github/epam/material/tests/inputs/FabTests.java" target="_blank">Here you can find Floating Action Button tests</a>

### Hidden

#### <a href="https://material-ui.com/components/hidden/" target="_blank"> https://material-ui.com/components/hidden/ </a>

```java     
    @UI(".MuiTypography-subtitle1")
    public static Text currentWidth;

    @UI("//div[contains(text(),'xsDown')]")
    public static Button xsDown;

    @UI("//div[text()='smDown']")
    public static Button smDown;

    @UI("//div[text()='mdDown']")
    public static Button mdDown;

    @UI("//div[text()='lgDown']")
    public static Button lgDown;

    @UI("//div[text()='xlDown']")
    public static Button xlDown;

    @Test
        public void defaultHiddenTest() {
            currentWidth.is().displayed();
            xsDown.is().displayed();
            smDown.is().displayed();
            mdDown.is().displayed();
    
            String width = getWidth(currentWidth);
            checkWidth(width);
    
            setHalfScreenWidthSize();
            width = getWidth(currentWidth);
            checkWidth(width);
        }
```

Quickly and responsively toggle the visibility value of components and more with the hidden utilities.

![Hidden](../images/material-ui/Hidden.png)

|Method | Description | Return Type
--- | --- | ---
**is()** | Verify state | boolean
**displayed()** | Verify state | boolean
**text()** | Verify text | boolean

#### <a href="https://github.com/jdi-testing/jdi-light/blob/Material-UI/jdi-light-material-ui-tests/src/test/java/io/github/epam/material/tests/layout/HiddenTests.java" target="_blank">Here you can find Hidden tests</a>

### Stepper

#### <a href="https://material-ui.com/components/steppers/" target="_blank"> https://material-ui.com/components/steppers/ </a>

![Stepper](../images/material-ui/Stepper.png)

```java
    @UI("//*[@id='simpleStepper']//following-sibling::div//*[@class='MuiTypography-root MuiTypography-body1']")
    public static Text simpleLinearStepperTitle;

    @UI("//*[@id='simpleStepper']//following-sibling::div//button[contains(@class, 'MuiButtonBase-root')]")
    public static WebList simpleLinearStepperButton;

    @Test
    public void simpleLinearStepperTest(){
        simpleLinearStepperTitle.is().text("You are on Step #1");
        simpleLinearStepperButton.get(2).click();
        simpleLinearStepperTitle.is().text("You are on Step #2");
        simpleLinearStepperButton.get(1).click();
        simpleLinearStepperTitle.is().text("You are on Step #1");
        simpleLinearStepperButton.get(2).click();
        simpleLinearStepperTitle.is().text("You are on Step #2");
        simpleLinearStepperButton.get(2).click();
        simpleLinearStepperTitle.is().text("You are on Step #3");
        simpleLinearStepperButton.get(2).click();
        simpleLinearStepperTitle.is().text("All steps completed");
        simpleLinearStepperButton.get(1).click();
        simpleLinearStepperTitle.is().text("You are on Step #1");
    }
```

Steppers convey progress through numbered steps. It provides a wizard-like workflow.
You can use for testing Text and Button classes, implemented in JDI-html section.

|Method | Description | Return Type
--- | --- | ---
**is()** | Verify state | boolean
**text()** | After is() allows to check state of text element | boolean
**click()** | Click on button | void

#### <a href="https://github.com/jdi-testing/jdi-light/blob/Material-UI/jdi-light-material-ui-tests/src/test/java/io/github/epam/material/tests/navigation/StepperTests.java" target="_blank">Here you can find Stepper tests</a>

### Slider

#### <a href="https://material-ui.com/components/slider/" target="_blank"> https://material-ui.com/components/slider/ </a>

```java
    @UI("//*[@id=\"continuous-slider\"]/following-sibling::div//span[contains(@class, \"MuiSlider-root\")]")
    public static Slider continuousSlider;
    
    @Test
    public void continuousSliderTest(){
        continuousSlider.is().enabled();
        continuousSlider.is().orientation("horizontal");
        continuousSlider.is().value(30);
        continuousSlider.setValue(15);
        continuousSlider.is().value(15);
        continuousSlider.moveLeft();
        continuousSlider.is().value(14);
        continuousSlider.moveRight();
        continuousSlider.is().value(15);
        continuousSlider.slideHorizontalTo(10);
        continuousSlider.is().value(10);
    }
```

Sliders reflect a range of values along a bar, from which users may select a single value. They are ideal for adjusting settings such as volume, brightness, or applying image filters.

![Slider](../images/material-ui/Slider.png)

|Method | Description | Return Type
--- | --- | ---
**value()** | Get current value | int
**setValue(int)** | Set new value | void
**orientation()** | Get orientation value | String
**slideVerticalTo(int)** | Set new value using drag-and-drop action for vertical slider | void
**slideHorizontalTo(int)** | Set new value using drag-and-drop action for horizontal slider | void
**moveRight()** | Move right to one unit using arrow key on keyboard | void
**moveLeft()** | Move left to one unit using arrow key on keyboard | void
**is()** | Verify state | boolean

#### <a href="https://github.com/jdi-testing/jdi-light/blob/Material-UI/jdi-light-material-ui-tests/src/test/java/io/github/epam/material/tests/inputs/SliderTests.java" target="_blank">Here you can find Slider tests</a>

### Tabs

#### <a href="https://material-ui.com/components/Tabs/" target="_blank"> https://material-ui.com/components/Tabs/ </a>

```java
    private List<List<Button>> tableLocators;
    private List<String> itemList = Arrays.asList("", "One", "Two", "Three", "Four", "Five", "Six", "Seven", "Eight", "Nine", "Ten", "Eleven");
    private int tableIndex;
    private Timer timer = new Timer(5000L);

    public void clickButton(int indexRow) { tableLocators.get(tableIndex).get(indexRow).click(); }
    
    public void checkLastItemText(String name) {lastItemText.get(tableIndex).has().text(containsString(name)); }
    
    @BeforeTest()
    public void beforeTest() {
        tabPage.open();
        tabPage.isOpened();
        tableLocators = Arrays.asList(null, simpleTabs, scrollableTabs, preventScrollTabs, verticalTabs);
    }

    @Test
    public void simpleTabTest() {
        tableIndex = 1;
        clickButton(1);
        checkLastItemText(itemList.get(1));
        tableLocators.get(tableIndex).get(4).has().classValue(containsString("Mui-disabled"));
        clickButton(5);
        checkLastItemText(itemList.get(5));
    }

    @Test
    public void scrollableTabTest(){
        tableIndex = 2;
        clickButton(9);
        checkLastItemText(itemList.get(9));
        timer.wait(() -> scrollButtons.get(2).click());
        clickButton(11);
        checkLastItemText(itemList.get(11));
        timer.wait(() -> scrollButtons.get(1).click());
        clickButton(1);
        checkLastItemText(itemList.get(1));
    }
```

Tabs organize and allow navigation between groups of content that are related and at the same level of hierarchy.

![Tabs](../images/material-ui/Tabs.png)

|Method | Description | Return Type
--- | --- | ---
**click()** | Clicks on button | void
**has()** | Returns Assert class | Assert
**text()** | Assert text | Assert

#### <a href="https://github.com/jdi-testing/jdi-light/blob/Material-UI/jdi-light-material-ui-tests/src/test/java/io/github/epam/material/tests/navigation/TabTests.java" target="_blank">Here you can find Tabs tests</a>

### Table

#### <a href="https://material-ui.com/components/Tables/" target="_blank"> https://material-ui.com/components/Tables/ </a>

```java
  @UI(".MuiDataGrid-main div[role='row'] div[tabindex]")
  public static List<Button> tableCells;

  @UI(".MuiDataGrid-selectedRowCount")
  public static Text selectedRowCounter;

  @UI(".MuiTablePagination-actions button")
  public static List<Button> scrollButtons;

  private final Timer timer = new Timer(2000L);
  private Button getCell(int row, int coll) {
      return tableCells.get((row - 1) * 6 + coll);
  }

  @BeforeTest
  public void beforeTest() {
    tablePage.open();
    tablePage.isOpened();
  }

  @Test
  public void dataTableTest() {
    getCell( 1, 1).click();
    selectedRowCounter.has().text(containsString("9"));
    getCell(3, 1).click();
    getCell(5, 1).click();
    selectedRowCounter.has().text(containsString("7"));
    scrollButtons.get(2).click();
    getCell(2, 1).click();
    selectedRowCounter.has().text(containsString("6"));
    getCell(1, 5).click();
    timer.wait(() -> getCell(4, 5).has().text(containsString("150")));
  }
```

Tables display sets of data. They can be fully customized.

![Tables](../images/material-ui/Tables.png)

|Method | Description | Return Type
--- | --- | ---
**click()** | Clicks on button | void
**has()** | Returns Assert class | Assert
**text()** | Assert text | Assert

#### <a href="https://github.com/jdi-testing/jdi-light/blob/Material-UI/jdi-light-material-ui-tests/src/test/java/io/github/epam/material/tests/displaydata/TableTests.java" target="_blank">Here you can find Tables tests</a>

### Typography

#### <a href="https://material-ui.com/ru/components/typography/" target="_blank"> https://material-ui.com/ru/components/typography/ </a>

```java
  @UI("//*[contains(@class,'MuiTypography-gutterBottom')]")
  public static List<Text> typographyTexts;

  @BeforeMethod
  public void before() {
  typographyPage.open();
  }

  @Test
  public void typographyTextTest() {

  List<String> expectedTextFields = Arrays.asList("Head 1", "Head 2", "Head 3", "Head 4", "Head 5", "Head 6",
  "Subtitle 1", "Subtitle 2", "Body 1", "Body 2", "BUTTON TEXT", "Caption text", "OVERLINE TEXT");

  List<String> expectedTypographyClasses = Arrays.asList("MuiTypography-h1", "MuiTypography-h2",
  "MuiTypography-h3", "MuiTypography-h4", "MuiTypography-h5", "MuiTypography-h6",
  "MuiTypography-subtitle1", "MuiTypography-subtitle2", "MuiTypography-body1", "MuiTypography-body2",
  "MuiTypography-button", "MuiTypography-caption", "MuiTypography-overline");

  List<String> actualTextFields = new ArrayList<>();

  for (Text typographyText : typographyTexts) {
  actualTextFields.add(typographyText.getText());
  }

  for (int i = 0; i < typographyTexts.size(); i++) {
  assertEquals(expectedTextFields.get(i), actualTextFields.get(i));
  typographyTexts.get(i + 1).has().classValue(containsString(expectedTypographyClasses.get(i)));
  }
  }
```

Use typography to present your design and content as clearly and efficiently as possible.

![Typography](../images/material-ui/Typography.png)

#### <a href="https://github.com/jdi-testing/jdi-light/blob/Material-UI/jdi-light-material-ui-tests/src/test/java/io/github/epam/material/tests/displaydata/TypographyTests.java" target="_blank">Here you can find Typography tests</a>

### Badge

#### <a href="https://material-ui.com/ru/components/badges/" target="_blank"> https://material-ui.com/ru/components/badges/ </a>

```java
  @UI("//span[@class='MuiBadge-root']")
  public static List<Badge> badge;

  @UI("//span[contains(@class,'MuiBadge-badge')]")
  public static List<Text> badgeCounter;
  
  @BeforeMethod
  public void before() {
  badgePage.open();
  }

  @Test
  public void simpleBadgeTest() {

  badge.get(1).is().displayed();
  badge.get(1).is().displayedSvg();
  badgeCounter.get(1).is().text("4");
  badgeCounter.get(1).has().classValue(containsString("MuiBadge-anchorOriginTopRightRectangle MuiBadge-colorPrimary"));

  badge.get(2).is().displayed();
  badge.get(2).is().displayedSvg();
  badgeCounter.get(2).is().text("4");
  badgeCounter.get(2).has().classValue(containsString("MuiBadge-anchorOriginTopRightRectangle MuiBadge-colorError"));
  }
  
```

Badge generates a small badge to the top-right of its child(ren).

![Badge](../images/material-ui/Badge.png)

#### <a href="https://github.com/jdi-testing/jdi-light/blob/Material-UI/jdi-light-material-ui-tests/src/test/java/io/github/epam/material/tests/displaydata/BadgeTests.java" target="_blank">Here you can find Badge tests</a>

### Snackbars

#### <a href="https://material-ui.com/components/snackbars/" target="_blank"> https://material-ui.com/components/snackbars/ </a>

```java
  @UI("//div[@class='MuiAlert-message']")
  public static List<Text> customizedSnackbarPopUpTitles;

  @UI("//div[@class='MuiAlert-message']/parent::div")
  public static List<Text> customizedSnackbarPopUpStyles;

  @UI("//div[@direction]/div[@class='MuiAlert-message']/parent::div")
  public static Text successSnackbarPopUp;
  
  @Test
  public void customizedSnackbarTest() {
  customizedSnackbarPopUpTitles.get(1).is().text("This is an error message!");
  customizedSnackbarPopUpStyles.get(1).has().classValue(containsString("MuiAlert-filledError"));
  customizedSnackbarPopUpTitles.get(2).is().text("This is a warning message!");
  customizedSnackbarPopUpStyles.get(2).has().classValue(containsString("MuiAlert-filledWarning"));
  customizedSnackbarPopUpTitles.get(3).is().text("This is an information message!");
  customizedSnackbarPopUpStyles.get(3).has().classValue(containsString("MuiAlert-filledInfo"));
  customizedSnackbarPopUpTitles.get(4).is().text("This is a success message!");
  customizedSnackbarPopUpStyles.get(4).has().classValue(containsString("MuiAlert-filledSuccess"));
  }
```

Snackbars provide brief messages about app processes. The component is also known as a toast.

![Snackbars](../images/material-ui/Snackbars.png)

#### <a href="https://github.com/jdi-testing/jdi-light/blob/Material-UI/jdi-light-material-ui-tests/src/test/java/io/github/epam/material/tests/feedback/SnackbarTests.java" target="_blank">Here you can find Snackbars tests</a>

### Backdrop

#### <a href="https://material-ui.com/components/backdrop/" target="_blank"> https://material-ui.com/components/backdrop/ </a>

```java
  @UI(".MuiButton-root")
  public static Button showBackdropButton;

  @UI(".MuiBackdrop-root")
  public static UIElement backdrop;

  @Test
  public void defaultBackdropTest() {
  showBackdropButton.click();
  timer.wait(() -> backdrop.is().visible());
  backdrop.click();
  timer.wait(() -> backdrop.is().hidden());
  }
```

The backdrop component is used to provide emphasis on a particular element or parts of it.
![Backdrop](../images/material-ui/Backdrop.png)

#### <a href="https://github.com/jdi-testing/jdi-light/blob/Material-UI/jdi-light-material-ui-tests/src/test/java/io/github/epam/material/tests/feedback/BackdropTests.java" target="_blank">Here you can find Backdrop tests</a>

### Dialog

#### <a href="https://material-ui.com/components/dialogs/" target="_blank"> https://material-ui.com/components/dialogs/ </a>

```java
  @UI("//span[text()='Open simple dialog']/parent::*[contains(@class,'MuiButtonBase-root')]")
  public static Button simpleDialogButton;
  
  @UI("//div[@id='simple-dialog-title']/following::div[@class='MuiListItemText-root'][1]")
  public static Button simpleDialogListButton;
  
  @UI("#simpleDialogSelection")
  public static Text simpleDialogField;

  @Test
  public void simpleDialogTest() {
    simpleDialogButton.click();
    dialogTitle.is().text("Set backup account");
    simpleDialogListButton.click();
    simpleDialogField.is().text("Selected: username@gmail.com");
    }
  
  @Test
  public void alertDialogTest() {
  
    alertDialogButton.click();
    dialogTitle.is().text("Alert dialog question?");
    dialogContent.is().text(dialogTextContent);
    dialogOkButton.click();
    timer.wait(() -> dialogContent.is().notVisible());
    alertDialogField.is().text("Selected: ok");
    alertDialogButton.click();
    dialogCloseButton.click();
    timer.wait(() -> dialogContent.is().notVisible());
    alertDialogField.is().text("Selected: close");
    }
```

Dialogs inform users about a task and can contain critical information, require decisions, or involve multiple tasks.
![Dialog](../images/material-ui/Dialog.png)

#### <a href="https://github.com/jdi-testing/jdi-light/blob/Material-UI/jdi-light-material-ui-tests/src/test/java/io/github/epam/material/tests/feedback/DialogTests.java" target="_blank">Here you can find Dialog tests</a>

### Date / Time pickers

#### <a href="https://material-ui.com/components/pickers/" target="_blank"> https://material-ui.com/components/pickers/ </a>

```java
  @JDropdown(
    root = "//*[@id = 'date-picker-dialog-label']/parent::div",
    value = "//*[@id ='date-picker-dialog']",
    list = "//*[@id = 'date-picker-dialog-label']/parent::div /ancestor::body " +
      "//div[@class = 'MuiPickersBasePicker-pickerView']//p",
    expand = "//span[@class = 'MuiIconButton-label']")
  public static Dropdown dialogPicker;
  
  @Test
  public void datePickerDialogTest() {
    dialogPicker.iCore().label().has().text("Date picker dialog");
    dialogPicker.expand();
    dialogPicker.select("12");
    dialogPicker.command("ENTER");
    timer.wait(() -> dialogPicker.has().text(containsString("/12/")));
  
    dialogPicker.expand();
    dialogPicker.select("11");
    dialogPicker.command("ESCAPE");
    timer.wait(() -> dialogPicker.has().text("08/12/2014"));
  
    dialogPicker.value().setText("10/10/2021");
    dialogPicker.has().text("10/10/2021");
    }
```

Dropdown is located in the following class:

- __Java__: _com.epam.jdi.light.elements.complex.dropdown.Dropdown_

Date pickers and Time pickers provide a simple way to select a single value from a pre-determined set.
![Dialog](../images/material-ui/DateTimePickers.png)

#### <a href="https://github.com/jdi-testing/jdi-light/blob/Material-UI/jdi-light-material-ui-tests/src/test/java/io/github/epam/material/tests/inputs/DateTimePickersTests.java" target="_blank">Here you can find Date/Time Pickers tests</a>

### Select

#### <a href="https://material-ui.com/components/selects/" target="_blank"> https://material-ui.com/components/selects/ </a>

```java
  @UI("//div[@id='simple-select']")
  public static Button simpleSelectExpand;
  
  @UI("//input")
  public static List<TextField> simpleSelectField;
  
  @UI("//ul")
  public static Select selectList;
  
  @UI("//div[@id='disabled-select']")
  public static Button disabledSelectExpand;

  @Test
  public void simpleSelectTest() {
    simpleSelectExpand.click();
    selectList.selectItemByText("Henry");
    simpleSelectField.get(1).is().attr("value", "Henry");
  }
  
  @Test
  public void disabledSelectTest() {
    disabledSelectExpand.is().classValue(containsString("Mui-disabled"));
    disabledSelectExpand.has().attr("aria-disabled", "true");
    disabledSelectExpand.has().attr("aria-labelledby", "disabled-select");
  }
```

Select components are used for collecting user provided information from a list of options.
![Select](../images/material-ui/Select.png)

#### <a href="https://github.com/jdi-testing/jdi-light/blob/Material-UI/jdi-light-material-ui-tests/src/test/java/io/github/epam/material/tests/inputs/SelectTests.java" target="_blank">Here you can find Select tests</a>

### Switch

#### <a href="https://material-ui.com/components/switches/" target="_blank"> https://material-ui.com/components/switches/ </a>

```java
  @UI("//span[contains(@class,'MuiSwitch-switchBase')]")
  public static List<Checkbox> switches;
  
  @UI("//p[contains(@class,'MuiFormHelperText-root')]")
  public static Text formGroupTextForm;
  
  @Test
  public void basicSwitchesTest() {
    switches.get(1).is().classValue(containsString("MuiSwitch-colorSecondary"));
    switches.get(1).is().classValue(containsString("Mui-checked"));
    switches.get(1).click();
    switches.get(1).is().classValue(not(containsString("Mui-checked")));
    }
```

Switches toggle the state of a single setting on or off.
![Switch](../images/material-ui/Switch.png)

#### <a href="https://github.com/jdi-testing/jdi-light/blob/Material-UI/jdi-light-material-ui-tests/src/test/java/io/github/epam/material/tests/inputs/SwitchTests.java" target="_blank">Here you can find Switch tests</a>

### Button

#### <a href="https://material-ui.com/components/buttons/" target="_blank"> https://material-ui.com/components/buttons/ </a>

```java
  @UI("//h2[text()='Contained buttons']/parent::div/div[1]/*")
  public static List<Button> containedButtons;
  
  @UI("//h2[text()='Text buttons']/parent::div/div[2]/*")
  public static List<Button> textButtons;
  
  @UI("//h2[text()='Buttons with icons and label']/parent::div/div[3]/*")
  public static List<Button> iconLabelButtons;
  
  @UI("//span[contains(@class,'MuiButton-icon')]")
  public static List<Icon> iconLabelIcons;
  
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
  
    containedButtons.get(4).is().text("DISABLED");
    containedButtons.get(4).is().attr("disabled");
    containedButtons.get(4).is().disabled();
  
    containedButtons.get(5).click();
    containedButtons.get(5).is().text("LINK");
    containedButtons.get(6).is().text("Last click: Link");
    containedButtons.get(5).is().notVisible();
  }
```

Buttons allow users to take actions, and make choices, with a single tap.

![Buttons](../images/material-ui/Buttons.png)

#### <a href="https://github.com/jdi-testing/jdi-light/blob/Material-UI/jdi-light-material-ui-tests/src/test/java/io/github/epam/material/tests/inputs/ButtonTests.java" target="_blank">Here you can find Buttons tests</a>

<br></br><br></br>

### ButtonGroup

#### <a href="https://jdi-testing.github.io/jdi-light/material/button_groups" target="_blank">Link to the site "Material UI test component"</a>

#### Basic and Vertical button group

**ButtonGroup** - element that represents a group of clickable button.

![ButtonGroup](../images/buttongroup.png)
![ButtonGroup](../images/verticalbuttongroup.png)

The ButtonGroup component can be used to group related buttons.

<br></br>

#### Split button
ButtonGroup can also be used to create a split button. The dropdown can change the button action (as in this example), or be used to immediately trigger a related action.

![ButtonGroup](../images/splitbutton.png)


#### <a href="https://material-ui.com/ru/components/button-group/" target="_blank">Here you can find specification of Button Group</a>

<br></br>

ButtonGroup is located in the following class:

- __Java__: _com.epam.jdi.light.material.elements.inputs.ButtonGroup_

Available methods in Java JDI Light:

|Method | Description | Return Type
  --- | --- | ---
**getButtonByIndex()** | Get button index | int
**select()** | Select the button | void
**getMainButton()** | Get main button | String
**getButtonByText()** | Get button text | String


<br></br>

#### ButtonGroupPage

ButtonGroupPage class has been extended from WebPage. This class contains variables that are used in tests:
- basicButtonGroup
- verticalButtonGroup
- splitButtonGroup

```java
public class ButtonGroupPage extends WebPage {

    //FindBy(xpath = "//*[@id=\"__next\"]/div/div/div[2]/div/div/div/div[1]/div")
    @UI("//*[@id=\"__next\"]/div/div/div[2]/div/div/div/div[1]/div")
    public ButtonGroup basicButtonGroup;

    //FindBy(xpath = "//*[@id=\"__next\"]/div/div/div[2]/div/div/div/div[2]/div")
    @UI("//*[@id=\"__next\"]/div/div/div[2]/div/div/div/div[2]/div")
    public ButtonGroup verticalButtonGroup;

    //FindBy(xpath = "//*[@id=\"__next\"]/div/div/div[2]/div/div/div/div[3]/div)
    @UI("//*[@id=\"__next\"]/div/div/div[2]/div/div/div/div[3]/div")
    @JDIButtonGroup(
            root = "#root",
            mainButton = ".MuiButton-root[1]",
            expand = ".MuiButton-root[2]",
            list = ".MuiPaper-root #split-button-menu")
    public ButtonGroup splitButtonGroup;
```

<br></br>

#### ButtonGroupTests

ButtonGroupTests is located in the following class:

- __Java__: _io.github.epam.material.tests.inputs.ButtonGroupTests_

Most applicable methods:

|Method | Description | Return Type
    --- | --- | ---
**click()** | Click the button  | void
**enabled()** | Assert that button is enabled | ButtonAssert
**is()**  | Assert action | ButtonAssert
**text()** | Assert text | ButtonAssert

```java
public class ButtonGroupTests extends TestsInit {

    @BeforeMethod
    public void before(){

        buttonGroupPage.open();
        buttonGroupPage.isOpened();
    }

    @Test
    public void basicButtonGroupTest() {

        buttonGroupPage.basicButtonGroup.getButtonByIndex(1).click();
        buttonGroupPage.basicButtonGroup.getButtonByIndex(2).click();
        buttonGroupPage.basicButtonGroup.getButtonByIndex(3).click();

        buttonGroupPage.basicButtonGroup.getButtonByText("Three").click();
        buttonGroupPage.basicButtonGroup.getButtonByText("Two").click();
        buttonGroupPage.basicButtonGroup.getButtonByText("One").click();

        buttonGroupPage.basicButtonGroup.getButtonByIndex(1).is().enabled();
        buttonGroupPage.basicButtonGroup.getButtonByIndex(1).has().text("ONE");
    }

    @Test
    public void verticalButtonGroupTest() {

        buttonGroupPage.verticalButtonGroup.getButtonByIndex(2).click();
        buttonGroupPage.verticalButtonGroup.getButtonByIndex(3).click();

        buttonGroupPage.verticalButtonGroup.getButtonByText("Two").click();
        buttonGroupPage.verticalButtonGroup.getButtonByText("One").click();

        buttonGroupPage.basicButtonGroup.getButtonByIndex(1).is().enabled();
        buttonGroupPage.basicButtonGroup.getButtonByIndex(1).has().text("ONE");
    }

    @Test
    public void splitButtonGroupTest() {

        buttonGroupPage.splitButtonGroup.getMainButton().click();
        buttonGroupPage.splitButtonGroup.getMainButton()
                .has().text("SQUASH AND MERGE");
        buttonGroupPage.splitButtonGroup.select("Create a merge commit");
        buttonGroupPage.splitButtonGroup.getMainButton()
            .has().text("CREATE A MERGE COMMIT");
    }

```

#### <a href="https://github.com/jdi-testing/jdi-light/blob/Material-UI/jdi-light-material-ui-tests/src/test/java/io/github/epam/material/tests/inputs/ButtonGroupTests.java" target="_blank">Here you can find Button group tests</a>

<br></br><br></br>

### Grid

#### <a href="https://material-ui.com/components/grid/" target="_blank"> https://material-ui.com/components/grid/ </a>

```java
  @UI(".MuiContainer-root")
  public static UIElement rootGrid;
  
  @UI("//h2[text()='Complex grid']/preceding::div[contains(@class,'MuiGrid-spacing')]")
  public static UIElement basicGrid;
  
  @UI("//h2[text()='Complex grid']/following::div[contains(@class,'MuiPaper-rounded')]/div[contains(@class,'MuiGrid-spacing')]")
  public static UIElement complexGrid;
  
  @UI("//div[contains(@class,'MuiPaper-rounded')]")
  public static List<Button> listButton;
  
  @Test
  public void gridTest() {
    rootGrid.is().displayed();
    rootGrid.attr("class").contains("MuiContainer-maxWidthXl");
    basicGrid.is().displayed();
    complexGrid.is().displayed();
    }
  
  @Test
  public void buttonsTest() {
    listButton.forEach(button -> button.is().displayed());
    listButton.forEach(button -> button.click());
    }
```

The Material Design responsive layout grid adapts to screen size and orientation, ensuring consistency across layouts.

![Grid](../images/material-ui/Grids.png)

#### <a href="https://github.com/jdi-testing/jdi-light/blob/Material-UI/jdi-light-material-ui-tests/src/test/java/io/github/epam/material/tests/layout/GridTests.java" target="_blank">Here you can find Grid tests</a>

### Drawer

#### <a href="https://material-ui.com/components/drawers/" target="_blank"> https://material-ui.com/components/drawers/ </a>

```java
  @UI("//*[text()='left']")
  public static Button leftButton;
  
  @UI("//*[text()='right']")
  public static Button rightButton;
  
  @UI("//*[text()='top']")
  public static Button topButton;
  
  @UI("//*[text()='bottom']")
  public static Button bottomButton;
  
  @UI("//div[contains(@class,'MuiPaper-root')]")
  public static Drawer drawer;

  @Test(priority = 1)
  public void temporaryDrawerTest() {
    temporaryDrawerPage.open();
    List<Button> buttons = Arrays.asList(leftButton, rightButton, topButton, bottomButton);
    buttons.forEach(
      button -> {
        button.click();
        drawer.is().displayed();
        String currentButtonName = button.getName();
        drawer.has().classValue(containsString(String.format("MuiDrawer-paperAnchor%s", currentButtonName.substring(0,currentButtonName.lastIndexOf(" ") + 1))));
        drawerElementsIcon.forEach(
          icon -> icon.is().displayedSvg()
        );
        drawerElementsText.forEach(
            text -> actualDrawerTexts.add(text.getText())
        );
        assertEquals(actualDrawerTexts, expectedDrawerTexts);
        actualDrawerTexts.clear();
        drawerElementsText.get(1).click();
      }
    );
    }
```

Navigation drawers provide access to destinations in your app. Side sheets are surfaces containing supplementary content that are anchored to the left or right edge of the screen.

![Drawer](../images/material-ui/Drawer.png)

#### <a href="https://github.com/jdi-testing/jdi-light/blob/Material-UI/jdi-light-material-ui-tests/src/test/java/io/github/epam/material/tests/navigation/DrawerTests.java" target="_blank">Here you can find Drawer tests</a>

### Breadcrumbs

#### <a href="https://material-ui.com/components/Breadcrumbs/" target="_blank"> https://material-ui.com/components/Breadcrumbs/ </a>

```java
  @UI(".MuiBreadcrumbs-li")
  public static List<UIElement> breadcrumbs;
  
  @UI("//h3[text()='Material UI']")
  public static UIElement materialElement;
  
  @UI("//h3[text()='Core']")
  public static UIElement coreElement;
  
  private static Timer timer = new Timer(3000L);

  @Test
  public void simpleBreadcrumbsTest() {
    simpleBreadcrumbsPage.open();
    breadcrumbs.get(1).is().text("Material-UI");
    breadcrumbs.get(1).click();
    timer.wait(() -> materialElement.is().visible());
    breadcrumbs.get(2).is().text("Core");
    breadcrumbs.get(2).click();
    timer.wait(() -> materialElement.is().notVisible());
    timer.wait(()->coreElement.is().visible());
    }
```

Breadcrumbs allow users to make selections from a range of values.

![Breadcrumbs](../images/material-ui/Breadcrumbs.png)

#### <a href="https://github.com/jdi-testing/jdi-light/blob/Material-UI/jdi-light-material-ui-tests/src/test/java/io/github/epam/material/tests/navigation/BreadcrumbsTests.java" target="_blank">Here you can find Breadcrumbs tests</a>

### Bottom Navigation

#### <a href="https://material-ui.com/components/bottom-navigation/" target="_blank"> https://material-ui.com/components/bottom-navigation/ </a>

```java
  @UI(".MuiBottomNavigationAction-root[2]")
  public static BottomNavigation favorites;
  
  @UI("#currentPosition")
  public static Text currentPosition;
  
  @Test
  public void defaultBottomNavigationTest(){
    favorites.is().enabled();
    assertTrue(favorites.core().text().contains("Favorites"));
    assertFalse(favorites.isSelected());
    favorites.core().click();
    assertTrue(currentPosition.getText().contains("Favorites"));
    favorites.is().selected();
  }
```

Bottom navigation bars allow movement between primary destinations in an app.


![BottomNavigation](../images/material-ui/BottomNavigation.png)

#### <a href="https://github.com/jdi-testing/jdi-light/blob/Material-UI/jdi-light-material-ui-tests/src/test/java/io/github/epam/material/tests/navigation/BottomNavigationTests.java" target="_blank">Here you can find Bottom Navigation tests</a>

### Paper

#### <a href="https://material-ui.com/components/paper/" target="_blank"> https://material-ui.com/components/paper/ </a>

```java
  @UI(".MuiPaper-root")
  public static List<UIElement> paper;

  private final String WITH_ZERO_ELEVATION = "Paper with elevation = 0";
  private final String WITH_DEFAULT_ELEVATION = "Paper with default elavation";
  private final String YOU_CLICKED = "You clicked: %s";
  public void defaultPaperTest() {
  
    paper.get(1).is().text(WITH_ZERO_ELEVATION);
    paper.get(1).click();
    paper.get(6).is().text(String.format(YOU_CLICKED, WITH_ZERO_ELEVATION));
  
    paper.get(2).is().text(WITH_DEFAULT_ELEVATION);
    paper.get(2).click();
    paper.get(6).is().text(String.format(YOU_CLICKED, WITH_DEFAULT_ELEVATION)); 
  }
```

In Material Design, the physical properties of paper are translated to the screen.


![Paper](../images/material-ui/Paper.png)

#### <a href="https://github.com/jdi-testing/jdi-light/blob/Material-UI/jdi-light-material-ui-tests/src/test/java/io/github/epam/material/tests/surfaces/PaperTests.java" target="_blank">Here you can find Paper tests</a>

### Accordion

#### <a href="https://material-ui.com/components/Accordion/" target="_blank"> https://material-ui.com/components/Accordion/ </a>

```java
  @UI(".MuiBreadcrumbs-li")
  public static List<UIElement> breadcrumbs;
  
  @UI("//h3[text()='Material UI']")
  public static UIElement materialElement;
  
  @UI("//h3[text()='Core']")
  public static UIElement coreElement;
  
  private static Timer timer = new Timer(3000L);

  @Test
  public void simpleBreadcrumbsTest() {
    simpleBreadcrumbsPage.open();
    breadcrumbs.get(1).is().text("Material-UI");
    breadcrumbs.get(1).click();
    timer.wait(() -> materialElement.is().visible());
    breadcrumbs.get(2).is().text("Core");
    breadcrumbs.get(2).click();
    timer.wait(() -> materialElement.is().notVisible());
    timer.wait(()->coreElement.is().visible());
    }
```

Accordions contain creation flows and allow lightweight editing of an element.

![Accordion](../images/material-ui/Accordion.png)

#### <a href="https://github.com/jdi-testing/jdi-light/blob/Material-UI/jdi-light-material-ui-tests/src/test/java/io/github/epam/material/tests/surfaces/AccordionTests.java" target="_blank">Here you can find Accordion tests</a>

### Portal

#### <a href="https://material-ui.com/components/Portal/" target="_blank"> https://material-ui.com/components/Portal/ </a>

```java
  @UI("//button")
  public static Button button;
  
  @UI("//button/following::div[1]")
  public static Text field1;
  
  @UI("//button/following::div[2]")
  public static Text field2;
  
  @Test
  public void portalTest() {
    button.has().text("Mount children");
    field1.has().text("It looks like I will render here.");
    field2.has().text("");
  
    button.click();
    button.has().text("Unmount children");
    field1.has().text("It looks like I will render here.");
    field2.has().text("But I actually render here!");
  
    button.click();
    button.has().text("Mount children");
    field1.has().text("It looks like I will render here.");
    field2.has().text("");
  }
```

The portal component renders its children into a new "subtree" outside of current DOM hierarchy.

![Portal](../images/material-ui/Portal.png)

#### <a href="https://github.com/jdi-testing/jdi-light/blob/Material-UI/jdi-light-material-ui-tests/src/test/java/io/github/epam/material/tests/utils/PortalTests.java" target="_blank">Here you can find Portal tests</a>

### Textarea Autosize

#### <a href="https://material-ui.com/components/textarea-autosize/" target="_blank"> https://material-ui.com/components/textarea-autosize/ </a>

```java
  @UI("//textarea[@aria-label = 'empty textarea']")
  public static TextArea emptyTextArea;
  
  @UI("//textarea[@aria-label = 'minimum height']")
  public static TextArea minArea;
  
  @UI("//textarea[@aria-label = 'maximum height']")
  public static TextArea maxArea;
  
  private int initialHeight;
  private static final String ONE_LINE = "1";
  private static final String THREE_LINES = "1\n2\n3";
  private static final String FOUR_LINES = "1\n2\n3\n4";
  
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

A textarea component for React which grows with content.


![TextArea](../images/material-ui/TextareaAutosize.png)

#### <a href="https://github.com/jdi-testing/jdi-light/blob/Material-UI/jdi-light-material-ui-tests/src/test/java/io/github/epam/material/tests/utils/TextAreaAutoSizeTests.java" target="_blank">Here you can find TextAreaAutosize tests</a>

### Popover

#### <a href="https://material-ui.com/components/popover/" target="_blank"> https://material-ui.com/components/popover/ </a>

```java
  @UI("//button[contains(@class,'MuiButtonBase-root')]/span[@class='MuiButton-label']")
  public static Button buttonToClick;
  
  @UI("//div[contains(@class,'MuiPaper-root')]/div")
  public static Button popoverContent;
  
  @UI("//span[@class='MuiTypography-root']")
  public static Text popoverHoverField;
  
  @Test
  public void clickPopoverTest() {
    buttonToClick.is().text("CLICK TO OPEN POPOVER");
    buttonToClick.click();
    popoverContent.is().text("Popover content");
  }
  
  @Test
  public void hoverPopoverTest() {
    popoverHoverField.is().text("[Hover to open Popover]");
    popoverHoverField.hover();
    popoverHoverField.has().attr("aria-owns", "mouse-over-popover");
    popoverContent.is().text("Popover content");
  }
```

A Popover can be used to display some content on top of another.

![Popover](../images/material-ui/Popover.png)

#### <a href="https://github.com/jdi-testing/jdi-light/blob/Material-UI/jdi-light-material-ui-tests/src/test/java/io/github/epam/material/tests/utils/PopoverTests.java" target="_blank">Here you can find Popover tests</a>

### Modal

#### <a href="https://material-ui.com/components/modal/" target="_blank"> https://material-ui.com/components/modal/ </a>

```java
  @UI("[id='simple-modal-description']")
  public static List<Text> modalTexts;

  @UI("button")
  public static List<Button> buttonModal;

  private static final String EXPECTED_TEXT = "Duis mollis, est non commodo luctus, nisi erat porttitor ligula.";
  
  @Test
  public void modalTests() {
    for (int modalCounter = 1; modalCounter < 3; modalCounter++) {
    buttonModal.get(modalCounter).click();
    modalTexts.get(modalCounter).has().text(EXPECTED_TEXT);
    }
    for (int modalCounter = 3; modalCounter > 1; modalCounter--) {
    buttonModal.get(modalCounter).core().click(-200, -100);
    }
  }
```

The modal component provides a solid foundation for creating dialogs, popovers, lightboxes, or whatever else.

![Modal](../images/material-ui/Modal.png)

#### <a href="https://github.com/jdi-testing/jdi-light/blob/Material-UI/jdi-light-material-ui-tests/src/test/java/io/github/epam/material/tests/utils/ModalTests.java" target="_blank">Here you can find Modal tests</a>

### Popper

#### <a href="https://material-ui.com/components/popper/" target="_blank"> https://material-ui.com/components/popper/ </a>

```java
  @UI("button")
  public static List<com.epam.jdi.light.ui.html.elements.common.Button> buttons;
  
  @UI("[role='tooltip']")
  public static UIElement tooltip;
  
  private final static List<String> POPPER_TEXTS = Arrays.asList("", "TOP", "LEFT", "RIGHT", "BOTTOM");
  private final static List<String> TOOLTIP_CLASSES = Arrays.asList("", "top", "left", "right", "bottom");
  
  @Test
  public void positionedPoppersTest() {
    for (int i = 1; i <= 4; i++) {
    buttons.get(i).click();
    buttons.get(i).has().text(POPPER_TEXTS.get(i));
    tooltip.has().attr("x-placement", TOOLTIP_CLASSES.get(i));
    }
  }
```

A Popper can be used to display some content on top of another. It's an alternative to react-popper.

![Popper](../images/material-ui/Popper.png)

#### <a href="https://github.com/jdi-testing/jdi-light/blob/Material-UI/jdi-light-material-ui-tests/src/test/java/io/github/epam/material/tests/utils/PopperTests.java" target="_blank">Here you can find Popper tests</a>

### Progress

#### <a href="https://material-ui.com/components/progress/" target="_blank"> https://material-ui.com/components/progress/ </a>

```java
  @JDIProgressBar(root ="(//*[contains(@class, 'MuiCircularProgress-root')])[1]")
  public static ProgressBar circularDefault;
  
  @JDIProgressBar(root ="(//*[contains(@class, 'MuiCircularProgress-root')])[6]")
  public static ProgressBar circularIndeterminate;
  
  @UI("//*[contains(@class, 'MuiFab-primary')]")
  public static Button interactiveIntegrationCircularButton;
  
  private Timer timer = new Timer(5000L);

  @Test
  public void progressTest() {
    circularDefault.is().indeterminate();
    int valueNow = circularIndeterminate.getValueNow();
    timer.wait(() ->circularIndeterminate.is().value(valueNow + 10));
    circularDefault.is().indeterminate();
    interactiveIntegrationCircularButton.click();
    interactiveIntegrationCircularIndeterminate.is().indeterminate();
    startLoadingButton.click();
    loadingCircularIndeterminate.is().indeterminate();
    simulateLoadButton.click();
    simulateLoadCircularIndeterminate.is().indeterminate();
    timer.wait(() -> successMessage.is().displayed());
  }
```
ProgressBar is located in the following class:
- __Java__: _com.epam.jdi.light.material.elements.feedback.ProgressBar_

Progress indicators commonly known as spinners, express an unspecified wait time or display the length of a process. The animation works with CSS, not JavaScript.

![Progress](../images/material-ui/Progress.png)

#### <a href="https://github.com/jdi-testing/jdi-light/blob/Material-UI/jdi-light-material-ui-tests/src/test/java/io/github/epam/material/tests/feedback/ProgressTests.java" target="_blank">Here you can find Progress tests</a>

### Menu

#### <a href="https://material-ui.com/ru/components/menus/" target="_blank"> https://material-ui.com/ru/components/menus/ </a>

```java
  @Url("/simple_menu")
  public static SimpleMenuPage simpleMenuPage;
  //@FindBy(css = "div[class^=MuiBox-root]>div div:nth-of-type(1) svg")
  @UI("div[class^=MuiBox-root]>div div:nth-of-type(1) svg")
  public static Menu iconMenu;
  //@FindBy(css = "div[class*=MuiPaper-root][style*='opacity: 1']")
  @UI("div[class*=MuiPaper-root][style*='opacity: 1']")
  public static Menu paddingMenuList;
  //@FindBy(css = "li.MuiListItem-button:first-child")
  @UI("li.MuiListItem-button:first-child")
  public static Menu menuListFirstButton;
  
  @BeforeMethod
  public void before() {
    simpleMenuPage.open();
    simpleMenuPage.isOpened();
  }

  @Test
  public void menuWithIconsTest() {
    iconMenu.is().displayedSvg();
    iconMenu.click();
    paddingMenuList.is().displayed();
    menuListFirstButton.is().displayedSvg();
    menuListFirstButton.has().text("Text with send icon");
    menuListFirstButton.click();
    iconMenu.is().displayed();
  }
```
Menu is located in the following class:
- __Java__: _com.epam.jdi.light.material.elements.navigation.Menu_

Menus display a list of choices on temporary surfaces.
![Menu](../images/material-ui/MenuWithIcons.png)
##### <a href="https://github.com/jdi-testing/jdi-light/blob/Material-UI/jdi-light-material-ui-tests/src/test/java/io/github/epam/material/tests/navigation/MenuTests.java" target="_blank">Here you can find Menu tests</a>
#### ContextMenu
#### <a href="https://material-ui.com/ru/components/menus/#context-menu" target="_blank"> https://material-ui.com/ru/components/menus/#context-menu </a>
 ```java
package io.github.com.pages.navigation;

import com.epam.jdi.light.elements.composite.WebPage;
import com.epam.jdi.light.elements.pageobjects.annotations.locators.UI;
import com.epam.jdi.light.material.elements.navigation.Menu;

public class ContextMenuPage extends WebPage {
//@FindBy(css = "li.MuiListItem-button:first-child")
    @UI("li.MuiListItem-button:first-child")
    public static Menu menuContextListFirstButton;
//@FindBy(css = "li.MuiListItem-button:last-child")
    @UI("li.MuiListItem-button:last-child")
    public static Menu menuContextListLastButton;
//@FindBy(css = "li.MuiListItem-button:last-child")
    @UI("//*/p[starts-with(@class, 'MuiTypography')]")
    public static Menu contextMenu;
}
@Url("/context_menu")
    public static ContextMenuPage contextMenuPage; 
@Test
    public void contextMenuTest() {
        contextMenuPage.open();
        contextMenu.rightClick();
        menuContextListLastButton.has().text("Email");
        menuContextListLastButton.click();
        contextMenu.isDisplayed()
 ```
Menu is located in the following class:
- __Java__: _com.epam.jdi.light.material.elements.navigation.Menu_
  Menus display a list of choices on temporary surfaces.
  ![Menu](../images/material-ui/ContextMenu.png)

### Lists

#### <a href="https://material-ui.com/components/lists/" target="_blank"> https://material-ui.com/components/lists/ </a>

```java
  @Url("/simple_list")
  public static ListPage ListPage;
  @Test
  public void pinnedSubHeaderList(){
  ListPage.open();

  ListPage.stickyZero.is().enabled();
  ListPage.stickyZero.is().text(hasToString("I'm sticky 0"));
  ListPage.stickyOne.is().enabled();
  ListPage.stickyOne.is().text(hasToString("I'm sticky 1"));
  }
```
Lists is located in the following class:
- __Java__: _com.epam.jdi.light.material.elements.displaydata.Lists_

Lists are continuous, vertical indexes of text or images.

![Lists](../images/material-ui/ListsSubheader.png)

#### <a href="https://github.com/jdi-testing/jdi-light/blob/Material-UI/jdi-light-material-ui-tests/src/test/java/io/github/epam/material/tests/displaydata/ListsTests.java" target="_blank">Here you can find Lists tests</a>

### Transfer List

Available methods in Java JDI Light:

|Method | Description | Return Type
--- | --- | ---
**isMoveRightButtonDisable()** | Assert > button is disabled | TransferListAssert
**isMoveLeftButtonDisable()** | Assert < button is disabled | TransferListAssert
**check()** | Click on checkbox to check | void
**uncheck()** | Click on checkbox to uncheck | void
**isMoveRightButtonEnable()** | Assert > button is enabled | TransferListAssert
**isMoveLeftButtonEnable()** | Assert < button is enabled | TransferListAssert
**moveItemsRight()** | Click on > button | void
**moveItemsLeft()** | Click on < button | void
**is()** | Various assert action for Transfer List | TransferListAssert
**itemsMovedRight()** | Assert items are existed on Right List | TransferListAssert
**itemsMovedLeft()** | Assert items are existed on Right List | TransferListAssert
**checked()** | Assert items is selected | TransferListAssert

### Simple Transfer List

#### <a href="https://material-ui.com/components/transfer-list/#simple-transfer-list" target="_blank"> https://material-ui.com/components/transfer-list/#simple-transfer-list </a>

```java
  @Test
  public void simpleTransferListTest() {
    simpleTransferListPage.open();
    simpleTransferListPage.simpleTransferList.is().isMoveRightButtonDisable();
    simpleTransferListPage.simpleTransferList.is().isMoveLeftButtonDisable();

    simpleTransferListPage.simpleTransferList.check("List item 1");
    simpleTransferListPage.simpleTransferList.is().checked("List item 1");

    simpleTransferListPage.simpleTransferList.is().isMoveRightButtonEnable();
    simpleTransferListPage.simpleTransferList.moveItemsRight();
    simpleTransferListPage.simpleTransferList.is().itemsMovedRight("List item 1");

    simpleTransferListPage.simpleTransferList.check("List item 5");
    simpleTransferListPage.simpleTransferList.check("List item 6");
    simpleTransferListPage.simpleTransferList.is().checked("List item 5");
    simpleTransferListPage.simpleTransferList.is().checked("List item 6");
    simpleTransferListPage.simpleTransferList.is().isMoveLeftButtonEnable();
    simpleTransferListPage.simpleTransferList.moveItemsLeft();
    simpleTransferListPage.simpleTransferList.is().itemsMovedLeft("List item 5", "List item 6");

    simpleTransferListPage.simpleTransferList.moveAllElementsRight();
    simpleTransferListPage.simpleTransferList.is().itemsMovedRight("List item 1", "List item 2",
        "List item 3", "List item 4", "List item 5", "List item 6", "List item 7", "List item 8");

    simpleTransferListPage.simpleTransferList.moveAllElementsLeft();
    simpleTransferListPage.simpleTransferList.is().itemsMovedLeft("List item 1", "List item 2",
      "List item 3", "List item 4", "List item 5", "List item 6", "List item 7", "List item 8");
 }
```

Available methods in Java JDI Light:

![Simple Transfer Lists](../images/material-ui/SimpleTransferList.png)

|Method | Description | Return Type
--- | --- | ---
**moveAllElementsRight()** | Click on >> button | void
**moveAllElementsLeft()** | Click on << button | void

#### <a href="https://github.com/jdi-testing/jdi-light/blob/Material-UI/jdi-light-material-ui-tests/src/test/java/io/github/epam/material/tests/inputs/TransferListTests.java" target="_blank">Here you can find Simple Transfer List tests</a>

### Enhanced Transfer List

#### <a href="https://material-ui.com/components/transfer-list/#enhanced-transfer-list" target="_blank"> https://material-ui.com/components/transfer-list/#enhanced-transfer-list </a>

```java
    @Test
    public void enhancedTransferListTest() {
        enhancedTransferListPage.open();
        enhancedTransferListPage.enhancedTransferList.is().isMoveRightButtonDisable();
        enhancedTransferListPage.enhancedTransferList.is().isMoveLeftButtonDisable();

        enhancedTransferListPage.enhancedTransferList.check("List item 1");
        enhancedTransferListPage.enhancedTransferList.is().checked("List item 1");
        enhancedTransferListPage.enhancedTransferList.is().isMoveRightButtonEnable();

        enhancedTransferListPage.enhancedTransferList.uncheck("List item 1");
        enhancedTransferListPage.enhancedTransferList.is().unchecked("List item 1");

        enhancedTransferListPage.enhancedTransferList.moveAllElementsRight();
        enhancedTransferListPage.enhancedTransferList.is().itemsMovedRight("List item 1", "List item 2",
            "List item 3", "List item 4", "List item 5", "List item 6", "List item 7", "List item 8");

        enhancedTransferListPage.enhancedTransferList.moveAllElementsLeft();
        enhancedTransferListPage.enhancedTransferList.is().itemsMovedLeft("List item 1", "List item 2",
            "List item 3", "List item 4", "List item 5", "List item 6", "List item 7", "List item 8");
    }
```

Available methods in Java JDI Light:

![Enhanced Transfer Lists](../images/material-ui/EnhancedTransferList.png)

|Method | Description | Return Type
--- | --- | ---
**moveAllElementsRight()** | Select all elements on left list then click on > button | void
**moveAllElementsLeft()** | Select all elements on right list then click on < button | void

#### <a href="https://github.com/jdi-testing/jdi-light/blob/Material-UI/jdi-light-material-ui/src/main/java/com/epam/jdi/light/material/elements/inputs/TextField.java">Here you can find Text Fields tests</a>

### Text Field

Available methods in Java JDI Light:

|Method | Description | Return Type
--- | --- | ---
|**setValue(String text)**|Input text| void
|**Clear()**|Clear data in Text Field| void
|**Click()**|Click on Text Field| void
|**GetText()**|Get current Text from Text Field| String
|**is()** |Various assert action for Text Field| TextFieldAssert
|**has()**|Various assert action for data of Text Field|TextFieldAssert

### Form Props

#### <a href="https://material-ui.com/components/text-fields/#form-props" target="_blank"> https://material-ui.com/components/text-fields/#form-props </a>

```java
    @Test
  public void formPropsTextFieldTest() {
  
    Random random = new Random();
    int intNumber = random.nextInt();
    double doubleNumber = random.nextDouble();
    float floatNumber = random.nextFloat();
  
    String randomString = generateRandomString();
  
    textFieldPage.textFieldRequired.is().enabled();
    textFieldPage.textFieldRequired.setValue(randomString);
    textFieldPage.textFieldRequired.has().text(randomString);
    textFieldPage.textFieldRequired.clear();
    textFieldPage.textFieldRequired.has().text("");
  
    textFieldPage.textFieldDisabled.is().disabled();
  
    textFieldPage.textFieldPassword.is().enabled();
    textFieldPage.textFieldPassword.setValue(randomString);
    textFieldPage.textFieldPassword.clear();
    textFieldPage.textFieldPassword.has().text("");
  
    textFieldPage.textFieldReadOnly.is().enabled();
    textFieldPage.textFieldReadOnly.is().readOnly();
  
    textFieldPage.textFieldNumber.is().enabled();
    textFieldPage.textFieldNumber.setValue(String.valueOf(intNumber));
    textFieldPage.textFieldNumber.has().text(String.valueOf(intNumber));
    textFieldPage.textFieldNumber.setValue(String.valueOf(floatNumber));
    textFieldPage.textFieldNumber.has().text(String.valueOf(floatNumber));
    textFieldPage.textFieldNumber.setValue(String.valueOf(doubleNumber));
    textFieldPage.textFieldNumber.has().text(String.valueOf(doubleNumber));
    textFieldPage.textFieldNumber.clear();
    textFieldPage.textFieldNumber.has().text("");
  
    textFieldPage.textFieldSearch.is().enabled();
    textFieldPage.textFieldSearch.setValue(randomString);
    textFieldPage.textFieldSearch.has().text(randomString);
    textFieldPage.textFieldSearch.clear();
    textFieldPage.textFieldSearch.has().text("");
  
    textFieldPage.textFieldHelper.is().enabled();
    textFieldPage.textFieldHelper.has().text(DEFAULT_VALUE);
    textFieldPage.textFieldHelper.setValue(randomString);
    textFieldPage.textFieldHelper.has().text(randomString);
    textFieldPage.textFieldHelper.clear();
    textFieldPage.textFieldHelper.has().text("");
    }
```

![Form Props](../images/material-ui/FormProps.png)

### Validation

#### <a href="https://material-ui.com/components/text-fields/#validation" target="_blank"> https://material-ui.com/components/text-fields/#validation </a>

```java
    @Test
  public void validateTextFieldTest() {
  
    String randomString = generateRandomString();
    textFieldPage.textFieldFilledError.is().enabled();
    textFieldPage.textFieldFilledError.setValue(randomString);
    textFieldPage.textFieldFilledError.has().text(randomString);
    textFieldPage.textFieldFilledError.clear();
    textFieldPage.textFieldFilledError.has().text("");
  
    textFieldPage.textFieldFilledErrorHelperText.is().enabled();
    textFieldPage.textFieldFilledErrorHelperText.setValue(randomString);
    textFieldPage.textFieldFilledErrorHelperText.has().text(randomString);
    textFieldPage.textFieldFilledErrorHelperText.clear();
    textFieldPage.textFieldFilledErrorHelperText.has().text("");
    textFieldPage.labelErrorHelperText.has().text("Incorrect entry.");
  }
```

![Validation](../images/material-ui/Validation.png)

### Multiline

#### <a href="https://material-ui.com/components/text-fields/#multiline" target="_blank"> https://material-ui.com/components/text-fields/#multiline </a>

```java
    @Test
  public void multilineTextFieldTest() {
  
    String randomString = generateRandomString();
    textFieldPage.textFieldMultiLine.is().enabled();
    textFieldPage.textFieldMultiLine.has().text("EUR");
    textFieldPage.textFieldMultiLine.clearAndSetValue(randomString);
    textFieldPage.textFieldMultiLine.has().text(randomString);
    textFieldPage.textFieldMultiLine.clear();
    textFieldPage.textFieldMultiLine.has().text("");
  
    textFieldPage.textFieldMultiLinePlaceHolder.is().enabled();
    textFieldPage.textFieldMultiLinePlaceHolder.setValue(randomString);
    textFieldPage.textFieldMultiLinePlaceHolder.has().text(randomString);
    textFieldPage.textFieldMultiLinePlaceHolder.clear();
    textFieldPage.textFieldMultiLinePlaceHolder.has().text("");
  
    textFieldPage.textFieldMultiLineStatic.is().enabled();
    textFieldPage.textFieldMultiLineStatic.has().text(DEFAULT_VALUE);
    textFieldPage.textFieldMultiLineStatic.clearAndSetValue(randomString);
    textFieldPage.textFieldMultiLineStatic.has().text(randomString);
    textFieldPage.textFieldMultiLineStatic.clear();
    textFieldPage.textFieldMultiLineStatic.has().text("");
  }
```

![Multiline](../images/material-ui/Multiline.png)

### Select

#### <a href="https://material-ui.com/components/text-fields/#select" target="_blank"> https://material-ui.com/components/text-fields/#select </a>

```java
    @Test
    public void selectTest() {
    
      for(CurrencyItems currency : CurrencyItems.values()){
      textFieldPage.selectElementField.click();
      textFieldPage.selectElement.selectItemByText(currency.currencyItemText);
      jdiAssert(textFieldPage.selectElementField.getText().equals(currency.currencyItemText), Matchers.is(true));
    
      textFieldPage.selectNativeSelect.select(currency.currencyItemText);
      textFieldPage.selectNativeSelect.has().text(currency.currencyItemText);
  }
```

![TextFieldSelect](../images/material-ui/TextFieldSelect.png)

Available methods in Java JDI Light:

|Method | Description | Return Type
--- | --- | ---
|**selectItemByText**|Select item by text| void

### Input Adornments

#### <a href="https://material-ui.com/components/text-fields/#input-adornments" target="_blank"> https://material-ui.com/components/text-fields/#input-adornments </a>

```java
    @Test
    public void inputAdornmentsTest() {
    
      String randomString = generateRandomString();
      textFieldPage.textFieldNormal.is().enabled();
      textFieldPage.textFieldNormal.setValue(randomString);
      textFieldPage.textFieldNormal.has().text(randomString);
      textFieldPage.textFieldNormal.clear();
      textFieldPage.textFieldNormal.has().text("");
    
      textFieldPage.textFieldWeight.is().enabled();
      textFieldPage.textFieldWeight.setValue(randomString);
      textFieldPage.textFieldWeight.has().text(randomString);
      textFieldPage.textFieldWeight.clear();
      textFieldPage.textFieldWeight.has().text("");
    
      textFieldPage.textFieldAdornmentPassword.is().enabled();
      textFieldPage.textFieldAdornmentPassword.setValue(randomString);
      textFieldPage.textFieldAdornmentPassword.has().text(randomString);
      textFieldPage.textFieldAdornmentPassword.clear();
      textFieldPage.textFieldAdornmentPassword.has().text("");
    
      textFieldPage.textFieldAmount.is().enabled();
      textFieldPage.textFieldAmount.setValue(randomString);
      textFieldPage.textFieldAmount.has().text(randomString);
      textFieldPage.textFieldAmount.clear();
      textFieldPage.textFieldAmount.has().text("");
    }
```

![Input Adornments](../images/material-ui/InputAdornments.png)

<br></br><br></br>
