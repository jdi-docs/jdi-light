# Theory
## UI Objects Pattern (Extend your PageObjects with UI elements)
TBD

## Entity Driven Testing
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

//If Smart locator rule is id:
    SmartSearchLocator = "#{0}";
    
//and the conversion rule is 'hyphen-to-csharp-name':
    SmartSearchName(string name) => StringExtensions.SplitHyphen(name);
    
//So you can write:

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

//If Smart locator rule is id:
    WebSettings.SMART_SEARCH_LOCATORS = asList("#%s");
    
//and the conversion rule is 'hyphen-to-java-name':
    WebSettings.SMART_SEARCH_NAME = StringUtils::splitHyphen;

//So you can write:
public class UserCard extends Form<User> {
    TextField name;
    TextField lastName;
    Button submitButton; 
}

```


If you have your developers following some standard way of marking UI elements or you have an agreement to add special attributes, you can even avoid writing locators for elements, thus making your page objects much more compact.

You can manage locator creation from field name using:

### Settings interface ISmartLocators contains:
  
- **SmartSearch** - method invoked if you have an element with no locator

- **SmartSearchLocator** - locator that can be used to try to find an element

- **SmartSearchName** -  method to create locator name from field name (this value will be passed as parameter to SmartSearchLocator)



## JDI Locators (simple as css powerful as xpath)
TBD
