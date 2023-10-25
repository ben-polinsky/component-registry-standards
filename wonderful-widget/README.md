# Fake Saved Views Widget

The Saved Views Widget for iTwin Viewers enables retrieving and saving [iTwin saved views](https://developer.bentley.com/apis/savedviews/overview/) - a feature that enable applications to persist display information like camera angles, views, and element visibility, among other things. The widget connects to either new iTwin Saved Views API or the legacy Product Setting Service. This is a fake widget for the purposes of demonstrating what a good README.md looks like in the [iTwin Component Registry](https://component-registry.itwin.dev/).

![Preview of Saved Views Widget](saved-views.gif)

## Basic Usage

Add the [`@bentley/itwin-saved-views`](https://bentleycs.visualstudio.com/beconnect/_git/TCDEAppService?path=/packages/modules/itwin-saved-views) package to your app via your nodejs package manager of choice. The widget code exports a `SavedViewsWidget` and a `SavedViewsUiProivder`, both which are needed to initialize the widget:

```ts
import {
  SavedViewsWidget,
  SavedViewsUiProvider,
} from "@bentley/itwin-saved-views";
```

Add a new instance of the `SavedViewUiProvider` viewer's `uiProviders` prop array:

```tsx
<Viewer uiProviders={[...otherUiProviders, new SavedViewUiProvider()]} />
```

Initialize the widget:

```ts
const onIModelAppInit = useCallback(async () => {
  await SavedViewsWidget.initialize();
});
```

Finally, ensure that the application you are using is configured to use the following scopes:

- `itwins:read`
- `product-settings-service`

### Customize the Fake Widget

The widget can be customized by passing in a `SavedViewsWidgetProps` object to the `SavedViewsWidget.initialize` method. The following optional properties are supported:

| Property               | Description                                                |
| ---------------------- | ---------------------------------------------------------- |
| `uiProvider`           | The `SavedViewsUiProvider` instance to use.                |
| `uiSettingsStorage`    | The `UiSettingsStorage` instance to use.                   |
| `uiSettingsNamespace`  | The namespace to use for storing the widget's UI settings. |
| `uiSettingsStorageId`  | The ID to use for storing the widget's UI settings.        |
| `uiSettingsOptions`    | The options to use for storing the widget's UI settings.   |
| `savedViewsApi`        | The `SavedViewsApi` instance to use.                       |
| `savedViewsApiOptions` | The options to use for the `SavedViewsApi` instance.       |

In addition, the widget can be customized by passing in a `SavedViewsUiProviderProps` object to the `SavedViewsUiProvider` constructor. The following optional properties are supported:

| Property              | Description                                                |
| --------------------- | ---------------------------------------------------------- |
| `settingOne`          | The `settingOne` to use. 0                                 |
| `uiSettingsNamespace` | The namespace to use for storing the widget's UI settings. |
| `uiSettingsStorageId` | The ID to use for storing the widget's UI settings.        |

## Related

- [iTwin Saved Views API](https://developer.bentley.com/apis/savedviews/overview/)
- [iTwin Viewer](https://github.com/iTwin/viewer)
- [Product Settings Service](https://developer.bentley.com/apis/ps/overview/)
