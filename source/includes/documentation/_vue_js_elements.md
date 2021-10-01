## Vue.js elements

### Alerts

[Vuetify documentation page](https://vuetifyjs.com/en/components/alerts/)

```java
  @Test
  public void alertsWithPropsHaveProperCssProps(){
      redAlert.has().text("I'm an alert with a top border and red color");
      redAlert.has().css("background-color", Colors.RED_LIGHTEN_2.value());
      redAlert.has().cssClass("v-alert--border-top");
  }
```

- __Java__: _com.epam.jdi.light.vuetify.elements.common.Alert.java_

![Alerts example](../../images/vuetify/alerts.png)

For examples of usage see: [Custom vuetify alert example](https://github.com/jdi-testing/jdi-light/blob/3118-implement-alerts/jdi-light-vuetify-tests/src/main/java/io/github/com/custom/CustomAlert.java)
and [JDI vuetify page tests for alerts](https://github.com/jdi-testing/jdi-light/blob/3118-implement-alerts/jdi-light-vuetify-tests/src/test/java/io/github/epam/vuetify/tests/common/AlertsTests.java).


### Avatars

[Vuetify documentation page](https://vuetifyjs.com/en/components/avatars/)

- __Java__: _com.epam.jdi.light.vuetify.elements.common.Avatar.java_

```java
    @Test
    public void avatarsWithSizeTests() {
        for(Avatar avatar: avatarsWithSize) {
        avatar.is().displayed();
        }
        avatarsWithSize.get(1).is().text("36");
        avatarsWithSize.get(2).is().text("48");
        avatarsWithSize.get(3).is().text("62");
        avatarsWithSize.get(1).has().size("36");
        avatarsWithSize.get(2).has().size("48");
        avatarsWithSize.get(3).has().size("62");
    }
```

![Avatars example](../../images/vuetify/avatars.png)

For examples of usage see: [Custom vuetify avatar example (profile card)](https://github.com/jdi-testing/jdi-light/blob/vuetify-develop/jdi-light-vuetify-tests/src/main/java/io/github/com/custom/ProfileCard.java)
and [JDI vuetify page tests for avatars](https://github.com/jdi-testing/jdi-light/blob/vuetify-develop/jdi-light-vuetify-tests/src/test/java/io/github/epam/vuetify/tests/common/AvatarsTests.java).


### Banners

[Vuetify documentation page](https://vuetifyjs.com/en/components/banners/)

- __Java__: _com.epam.jdi.light.vuetify.elements.complex.Banner.java_

```java
    @Test
    public void singleBannerTests() {
        singleBanner.is().displayed();
        singleBanner.has().properTitle("My Document");
        singleBanner.has().properText("We can't save your edits");
        singleBanner.has().button();
        singleBanner.has().checker();
        singleBanner.is().checkerUnchecked();
        singleBanner.getChecker().click();
        singleBanner.is().checkerChecked();
    }
```

![Banners example](../../images/vuetify/banners.png)

Banners may contain anything, you can inherit the `Banner` class and customize it
the way you want.

Basically, you have methods that can return you elements containing in banner (buttons, checkers, icons, etc.).

For examples of usage see: [JDI vuetify page tests for banners](https://github.com/jdi-testing/jdi-light/blob/vuetify-develop/jdi-light-vuetify-tests/src/test/java/io/github/epam/vuetify/tests/complex/BannersTests.java).


### Breadcrumbs

[Vuetify documentation page](https://vuetifyjs.com/en/components/breadcrumbs/)

- __Java__: _com.epam.jdi.light.vuetify.elements.complex.Breadcrumbs.java_

```java
    @JDIBreadcrumbs(
            root = "#differentDividersBreadcrumbs > ul:nth-child(2)",
            items = ".v-breadcrumbs__item",
            dividers = ".v-breadcrumbs__divider"
    )
    public static Breadcrumbs forwardSlashedBreadcrumbs;
```

You can specify locators for the root, links and dividers
explicitly through a `JDIBreadcrumbs` annotation:

```java
    @JDIBreadcrumbs(root = "#largeBreadcrumbs > ul")
    public static Breadcrumbs largeBreadcrumbs;
```

```java
    @Test
    public void itemSlotBreadcrumbsTest() {
        itemSlotsBreadcrumbs.is().displayed();
        itemSlotsBreadcrumbs.has().size(3);
        itemSlotsBreadcrumbs.dividers().has().size(2);
        itemSlotsBreadcrumbs.items().has().values("DASHBOARD", "LINK 1", "LINK 2");
        jdiAssert(itemSlotsBreadcrumbs.selected("DASHBOARD"), Matchers.is(false));
        jdiAssert(itemSlotsBreadcrumbs.selected("LINK 2"), Matchers.is(true));
    }
```


It is **necessary** to specify **the root** of an element



For examples of usage see: [Vuetify Breadcrumbs tests](https://github.com/jdi-testing/jdi-light/blob/vuetify-develop/jdi-light-vuetify-tests/src/test/java/io/github/epam/vuetify/tests/complex/BreadcrumbsTests.java).


### Cards

[Vuetify documentation page](https://vuetifyjs.com/en/components/cards/)

- __Java__: _com.epam.jdi.light.vuetify.elements.complex.Card.java_

```java
public class MediaTextCard extends Card {
    @UI(".v-image__image")
    protected Image image;
    public Image image() {
        return image;
    }
    public Button shareButton() {
        return new Button().setCore(Button.class, actions().find("//button[./span[contains(text(), 'Share')]]"));
    }
    public Button exploreButton() {
        return new Button().setCore(Button.class, actions().find("//button[./span[contains(text(), 'Explore')]]"));
    }
}
```

```java
    @Test
    public void mediaTextCardTest() {
        mediaTextCard.is().displayed();
        mediaTextCard.image().has().css("background-size", "cover");
        mediaTextCard.has().title("Top 10 Australian beaches");
        mediaTextCard.has().subtitle(containsString("Number 10"));
        mediaTextCard.content().has().text(containsString("Whitehaven Beach"));
        mediaTextCard.shareButton().click();
        mediaTextCard.exploreButton().click();
    }
```

![Cards example](../../images/vuetify/cards.png)

Cards may contain anything, you can inherit the `Card` class and customize it
the way you want.


Basically, you have 4 methods: `title`, `subtitle`, `content` and `actions`.
They return the parts of a card described [here](https://vuetifyjs.com/en/components/cards/#api).
The `content` method returns a
card `text` element, but the `text` method is inherited from `UIBaseElement` that why it has a different name.

For examples of usage see: [Custom vuetify card examples](https://github.com/jdi-testing/jdi-light/tree/vuetify-develop/jdi-light-vuetify-tests/src/main/java/io/github/com/custom/cards)
and [JDI vuetify page tests for cards](https://github.com/jdi-testing/jdi-light/blob/vuetify-develop/jdi-light-vuetify-tests/src/test/java/io/github/epam/vuetify/tests/complex/CardsTests.java).

### Expansion Panels

[Vuetify documentation page](https://vuetifyjs.com/en/components/expansion-panels/)

- __Java__: _com.epam.jdi.light.vuetify.elements.complex.panels.ExpansionPanels.java_
- __Java__: _com.epam.jdi.light.vuetify.elements.complex.panels.ExpansionPanel.java_

```java
    @JDIExpansionPanels(
        root = "#ModelExpansionPanel .v-expansion-panels",
        panels = ".v-expansion-panel",
        header = ".v-expansion-panel-header",
        icon = ".v-expansion-panel-header__icon",
        content = ".v-expansion-panel-content",
        wrapper = ".v-expansion-panel-content__wrap"
    )
    public static ExpansionPanels modelExpansionPanels;
```

You can specify locators for the root and panels to find panels in root. 
Also, you can specify header, content, icon and wrapper locators for all panels. All of it you can do
explicitly through a `JDIExpansionPanels` annotation. 

It is **necessary** to specify **the root** of an element.

```java
    @JDIExpansionPanels(
        root = "#CustomIconExpansionPanel .v-expansion-panels:nth-child(1)",
        icon = ".v-expansion-panel-header__icon .v-icon"
    )
    public static ExpansionPanels customIconExpansionPanelsSameIcons;
```

```java
    @Test
    public void customIconExpansionPanelTest() {
        customIconExpansionPanelsSameIcons.has().size(5);
        for (ExpansionPanel expansionPanel : customIconExpansionPanelsSameIcons.panels()) {
            expansionPanel.header().has().text("Item");
            expansionPanel.wrapper().has().text(LOREM_IPSUM_TEXT);
            expansionPanel.is().expanded();
            expansionPanel.expander().is().displayed();
            expansionPanel.expander().has().cssClass("mdi-menu-down");
        }
    }
```

![Expansion panels example](../../images/vuetify/expansionPanels.png)

ExpansionPanels is a list of ExpansionPanel.

Expansion panel may contain anything, so you can inherit the `ExpansionPanel` class and customize it
the way you need. This class has 4 base methods: `header`, `expander`, `content` and `wrapper`. 
They return the parts of an expansion panel. 

Also, you can inherit the `ExpansionPanels`.

For examples of usage see: [Custom vuetify expansion panels examples](https://github.com/jdi-testing/jdi-light/tree/vuetify-develop/jdi-light-vuetify-tests/src/main/java/io/github/com/custom/panels)
and [JDI vuetify page tests for expansion panels](https://github.com/jdi-testing/jdi-light/blob/vuetify-develop/jdi-light-vuetify-tests/src/test/java/io/github/epam/vuetify/tests/complex/ExpansionPanelsTest.java).

### Pagination

[Vuetify documentation page](https://vuetifyjs.com/en/components/paginations/)

- __Java__: _com.epam.jdi.light.vuetify.elements.complex.Pagination.java_

```java
    @JDIPagination(
        root = "#CirclePagination .v-pagination",
        items = ".v-pagination__item",
        left = ".v-pagination__navigation[1]",
        right = ".v-pagination__navigation[2]",
        more = ".v-pagination__more"
    )
    public static Pagination circlePagination;
```

You can specify locators for the root and items to find page buttons in the root.
Also, you can specify locators of left and right navigation buttons, locators of button with 'more' value like '...'. All of it you can do
explicitly through a `JDIPagination` annotation.

It is **necessary** to specify **the root** of an element.

```java
    @JDIPagination(root = "#TotalVisiblePagination .v-pagination")
    public static Pagination totalVisiblePagination;

    @Test
    public void totalVisiblePaginationTest() {
        totalVisiblePagination.has().size(6);
        totalVisiblePagination.has().hiddenButtons();
        totalVisiblePagination.is().enabled();
        totalVisiblePagination.is().started();

        totalVisiblePagination.select("15");
        totalVisiblePagination.is().ended();
        totalVisiblePagination.has().values("1", "2", "3", "13", "14", "15");
        totalVisiblePagination.has().selected("15");
        totalVisiblePagination.has().selected(6);

        List<String> actualButtonsFromEndToStart = new ArrayList<>();
        ListIterator<String> it = totalVisiblePagination.listIterator();
        while (it.hasPrevious()) {
            actualButtonsFromEndToStart.add(it.previous());
        }
        totalVisiblePagination.is().started();
        assertThat(actualButtonsFromEndToStart, equalTo(Arrays.asList(
            "15", "14", "13", "12", "11", "10", "9", "8", "7", "6", "5", "4", "3", "2", "1"
        )));
  }
```

![Expansion panels example](../../images/vuetify/pagination.png)

For examples of usage see: [JDI vuetify page tests for pagination](https://github.com/jdi-testing/jdi-light).

### Tabs

[Vuetify documentation page](https://vuetifyjs.com/en/components/tabs/)

- __Java__: _com.epam.jdi.light.ui.html.elements.complex.Tabs.java_

```java
    @Test
    public static void iconsTextTabsTest() {
        iconAndTextTabs.select(1);
        iconAndTextTabs.get(1).is().text("RECENTS");
        iconAndTextTabsIcon.get(1).is().visible();

        iconAndTextTabs.select(2);
        iconAndTextTabs.get(2).is().text("FAVORITES");
        iconAndTextTabsIcon.get(2).is().visible();

        iconAndTextTabs.select(3);
        iconAndTextTabs.get(3).is().text("NEARBY");
        iconAndTextTabsIcon.get(3).is().visible();
    }
```

![Cards example](../../images/vuetify/tabs.png)

Tabs - a list of tabs which may be implemented as buttons, links, icons etc. You can inherit the `Tabs` class and customize it the way you want.

For examples of usage see: [JDI vuetify page tests for tabs](https://github.com/jdi-testing/jdi-light/blob/vuetify-develop/jdi-light-vuetify-tests/src/test/java/io/github/epam/vuetify/tests/complex/TabsTests.java).
