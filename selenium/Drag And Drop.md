Drag And Drop with Selenium
==============================

## 1. Usage

Selenium supports drag and drop action. In java client, it is like:
```java
public static void dragAndDrop(WebDriver driver, WebElement source, WebElement target) {
        Actions builder = new Actions(driver);
        Actions dragAndDrop = builder.dragAndDrop(source, target);
        dragAndDrop.perform();
}
```


And dragAndDrop method actually is:
```java
 /**
   * A convenience method that performs click-and-hold at the location of the source element,
   * moves to the location of the target element, then releases the mouse.
   *
   * @param source element to emulate button down at.
   * @param target element to move to and release the mouse at.
   * @return A self reference.
   */
  public Actions dragAndDrop(WebElement source, WebElement target) {
    if (isBuildingActions()) {
      action.addAction(new ClickAndHoldAction(jsonMouse, (Locatable) source));
      action.addAction(new MoveMouseAction(jsonMouse, (Locatable) target));
      action.addAction(new ButtonReleaseAction(jsonMouse, (Locatable) target));
    }

    return moveInTicks(source, 0, 0)
        .tick(defaultMouse.createPointerDown(LEFT.asArg()))
        .moveInTicks(target, 0, 0)
        .tick(defaultMouse.createPointerUp(LEFT.asArg()));
  }
```


So dragAndDrop method is exactly same as 'clickAndHold'+'moveToElement'+'release'.  
It means, you **don't** need to do this. It is exactly same as 'dragAndDrop' method.
```java
public static void dragAndDrop2(WebDriver driver, WebElement source, WebElement target) {
        Actions builder = new Actions(driver);
        Action dragAndDrop = builder.clickAndHold(source)
                .moveToElement(target)
                .release(target)
                .build();
        dragAndDrop.perform();
}
```

## 2. PainPoints

Drag and drop action is very sensitive action. It might be fail sometimes unfortunatly.  
To make drag and drop stable, you should care about your testing environment. Such as...  

- Window should be maximize/fullscreen. *Window/Linux: maximize, Mac: fullscreen
- Actual mouse point should be inside the browser.

Using selenium moveTo action, actual mouse doesn't move. Only virtual position will be moved.  
If you want real mouse movement you should use another library such as **java.awt.Robot**.  
All of these happened becuase drag and drop action depends on x/y position.  
And selenium driver need to calculate positions and it needs to window maximize for its accuracy.  
