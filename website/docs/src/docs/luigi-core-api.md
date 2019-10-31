# Luigi Core API

## Luigi Config

<!-- Generated by documentation.js. Update this documentation by updating the source code. -->

### Configuration

#### setConfig

Sets the configuration for Luigi initially. Can also be called at a later point in time again to update the configuration.

##### Parameters

-   `configInput` **[Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)** the Luigi Core configuration object

##### Examples

```javascript
Luigi.setConfig({
  navigation: {
    nodes: () => [
      {
        pathSegment: 'home',
        label: 'Home',
        children: [
          {
            pathSegment: 'hello',
            label: 'Hello Luigi!',
            viewUrl: '/assets/basicexternal.html'
          }
        ]
      }
    ]
  },
  routing: {
    useHashRouting: true
  }
})
```

#### getConfig

Returns the current active configuration

##### Examples

```javascript
Luigi.getConfig()
```

Returns **[Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)** configuration object

#### configChanged

Tells Luigi that the configuration has been changed. Luigi will update the application or parts of it based on the specified scope.

##### Parameters

-   `scope` **...[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** one or more scope selectors specifying what parts of the configuration were changed. If no scope selector is provided, the whole configuration is considered changed.<p>
    The supported scope selectors are:
    <p>
    <ul>
      <li><code>navigation</code>: the navigation part of the configuration was changed. This includes navigation nodes, the context switcher, the product switcher and the profile menu.</li>
      <li><code>navigation.nodes</code>: navigation nodes were changed.</li>
      <li><code>navigation.contextSwitcher</code>: context switcher related data were changed.</li>
      <li><code>navigation.productSwitcher</code>: product switcher related data were changed.</li>
      <li><code>navigation.profile</code>: profile menu was changed.</li>
      <li><code>settings</code>: settings were changed.</li>
      <li><code>settings.header</code>: header settings (title, icon) were changed.</li>
      <li><code>settings.footer</code>: left navigation footer settings were changed.</li>
    </ul>

#### getConfigValue

Gets value of the given property on Luigi config object. Target can be a value or a synchronous function.

##### Parameters

-   `property` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** the object traversal path

##### Examples

```javascript
Luigi.getConfigValue('auth.use')
Luigi.getConfigValue('settings.sideNavFooterText')
```

#### getConfigBooleanValue

Gets boolean value of the given property on Luigi config object.
Function return true if the property value is equal true or 'true'. Otherwise the function returns false.

##### Parameters

-   `property` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** the object traversal path

##### Examples

```javascript
Luigi.getConfigBooleanValue('settings.hideNavigation')
```

#### getConfigValueAsync

Gets value of the given property on the Luigi config object.
If the value is a Function it is called (with the given parameters) and the result of that call is the value.
If the value is not a Promise it is wrapped to a Promise so that the returned value is definitely a Promise.

##### Parameters

-   `property` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** the object traversal path
-   `parameters` **any** optional parameters that are used if the target is a function

##### Examples

```javascript
Luigi.getConfigValueAsync('navigation.nodes')
Luigi.getConfigValueAsync('navigation.profile.items')
Luigi.getConfigValueAsync('navigation.contextSwitcher.options')
```

#### isAuthorizationEnabled

Detects if authorization is enabled via configuration.

Returns **[boolean](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Boolean)** returns true if authorization is enabled. Otherwise returns false.

**Meta**

-   **deprecated**: now located in Luigi.auth() instead of Luigi

## Luigi.elements()

<!-- Generated by documentation.js. Update this documentation by updating the source code. -->

### Elements

Use these functions to get DOM elements.

#### getLuigiContainer

Returns the container of the Luigi content.

##### Examples

```javascript
Luigi.elements().getLuigiContainer();
```

Returns **[HTMLElement](https://developer.mozilla.org/docs/Web/HTML/Element)** the DOM element that wraps the Luigi content.

**Meta**

-   **since**: 0.6.0

#### getShellbar

Returns the shellbar component.

##### Examples

```javascript
Luigi.elements().getShellbar();
```

Returns **[HTMLElement](https://developer.mozilla.org/docs/Web/HTML/Element)** the shellbar DOM element.

**Meta**

-   **since**: 0.4.12

#### getShellbarActions

Returns the shellbar actions component.

##### Examples

```javascript
Luigi.elements().getShellbarActions();
```

Returns **[HTMLElement](https://developer.mozilla.org/docs/Web/HTML/Element)** the shellbar actions DOM element.

**Meta**

-   **since**: 0.4.12

#### getMicrofrontends

Returns a list of all available micro frontends.

##### Examples

```javascript
Luigi.elements().getMicrofrontends();
```

Returns **[Array](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Array)&lt;{id: [string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String), active: [boolean](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Boolean), container: [HTMLElement](https://developer.mozilla.org/docs/Web/HTML/Element), type: (`"main"` \| `"split-view"` \| `"modal"`)}>** list of objects defining all micro frontends from the DOM

**Meta**

-   **since**: 0.6.2

#### getMicrofrontendIframes

Returns all micro frontend iframes including the iframe from the modal if it exists.

##### Examples

```javascript
Luigi.elements().getMicrofrontendIframes();
```

Returns **[Array](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Array)&lt;[HTMLElement](https://developer.mozilla.org/docs/Web/HTML/Element)>** an array of all micro frontend iframes from the DOM.

**Meta**

-   **since**: 0.4.12

#### getCurrentMicrofrontendIframe

Returns the active micro frontend iframe.
If there is a modal, which includes the micro frontend iframe, the function returns this iframe.

##### Examples

```javascript
Luigi.elements().getCurrentMicrofrontendIframe();
```

Returns **[HTMLElement](https://developer.mozilla.org/docs/Web/HTML/Element)** the active micro frontend iframe DOM element.

**Meta**

-   **since**: 0.4.12

## Luigi.auth()

<!-- Generated by documentation.js. Update this documentation by updating the source code. -->

### Authorization

Authorization helpers

#### isAuthorizationEnabled

Detects if authorization is enabled via configuration.

##### Examples

```javascript
Luigi.auth().isAuthorizationEnabled();
```

Returns **[boolean](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Boolean)** true if authorization is enabled. Otherwise returns false.

## Luigi.navigation()

<!-- Generated by documentation.js. Update this documentation by updating the source code. -->

### LuigiNavigation

Use these functions for navigation-related features.

#### updateTopNavigation

Refreshes top navigation badge counters by rendering the navigation again.

##### Examples

```javascript
Luigi.navigation().updateTopNavigation();
```

## Luigi.i18n()

<!-- Generated by documentation.js. Update this documentation by updating the source code. -->

### LuigiI18N

Localization-related functions.

#### getCurrentLocale

Gets the current locale.

Returns **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** current locale

**Meta**

-   **since**: 0.5.3

#### setCurrentLocale

Sets current locale to the specified one.

##### Parameters

-   `locale` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** locale to be set as the current locale

**Meta**

-   **since**: 0.5.3

#### addCurrentLocaleChangeListener

Registers a listener for locale changes.

##### Parameters

-   `listener` **[Function](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/function)** function called on every locale change with the new locale as argument

Returns **[number](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Number)** listener ID associated with the given listener; use it when removing the listener

**Meta**

-   **since**: 0.5.3

#### removeCurrentLocaleChangeListener

Unregisters a listener for locale changes.

##### Parameters

-   `listenerId` **[number](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Number)** listener ID associated with the listener to be removed, returned by addCurrentLocaleChangeListener

**Meta**

-   **since**: 0.5.3

#### getTranslation

Gets translated text for the specified key in the current locale or in the specified one.
Property values for token replacement in the localization key will be taken from the specified interpolations object.

##### Parameters

-   `key` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** key to be translated
-   `interpolations` **[Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)** objects with properties that will be used for token replacements in the localization key
-   `locale` **locale** optional locale to get the translation for; default is the current locale

## Luigi.customMessages()

<!-- Generated by documentation.js. Update this documentation by updating the source code. -->

### CustomMessages

Functions related to custom messages.

#### sendToAll

Sends a custom message to all opened micro frontends.

##### Parameters

-   `message` **[Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)** an object containing data to be sent to the micro frontend to process it further. This object is set as an input parameter of the custom message listener on the micro frontend side.
    -   `message.id` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** the id of the message
    -   `message.MY_DATA_FIELD` **any** any other message data field

##### Examples

```javascript
Luigi.customMessages().sendToAll({
    id: 'myprefix.my-custom-message-for-client',
    dataField1: 'here goes some data',
    moreData: 'here goes some more'
});
```

**Meta**

-   **since**: 0.6.2

#### send

Sends a message to specific micro frontend identified with an id.
Use Luigi.elements().getMicrofrontends() to get the iframe id.

##### Parameters

-   `microfrontendId` **[number](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Number)** the id of the micro frontend
-   `message` **[Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)** an object containing data to be sent to the micro frontend to process it further. This object is set as an input parameter of the custom message listener on the micro frontend side.
    -   `message.id` **[number](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Number)** the id of the message
    -   `message.MY_DATA_FIELD` **any** any other message data field

##### Examples

```javascript
Luigi.customMessages().send(microfrontend.id, {
    id: 'myprefix.my-custom-message-for-client',
    dataField1: 'here goes some data',
    moreData: 'here goes some more'
});
```

**Meta**

-   **since**: 0.6.2

## Luigi.ux()

<!-- Generated by documentation.js. Update this documentation by updating the source code. -->

### UX

Functions to use Luigi Core UX features.

#### hideAppLoadingIndicator

Hides the app loading indicator.

**Meta**

-   **since**: 0.6.4