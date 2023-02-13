Angular is a platform and framework for building  single-page applications( #SPA ) using #HTML and #TypeScript. Angular is written in TypeScript. It implements core and optional functionality as a set of TypeScript libraries that you import into your applications.

The architectore of an Angualr application relies of certain fundamental concepts. 

The basic building block of the Angular framework are Angular components that be organized into  `NgModules`.

`NgModules` collect related code into functional sets; an Angular application is defined by a set of `NgModules`.

An application always has at least a `root module` that enables bootstrapping, and typically has many `feature modules`

- `Components` define `views`, which are sets of screen elements that Angular can choose among and modify according to your program logic and data
- `Components` use `services`, which provide specific functionality not directly related to views. Service providers can be `injected` into componetns as `dependencies`, making your code modular, reusable and efficient.

`Modules`, `components` and `services` are classes that use `decorators`. These `decorators` mark their type and provide metadata that tells Angular how to use them.

- The metadata for a `component` class associates it with a `template` that defines a view. A template combines ordinary HTML and Angular directives and binding markup that allows Angular modify the HTML before rendering it for display
- The metadata for a `service` class provides the information Angular needs to make it avalible to components through #Dependency-Injection (DI).

An application's components typically define many view, arraged hierarchically.

## Modules

Angular `NgModules` differ from and coplement `JavaScript` (ES2015) modules. An `NgModule` declares a copilation context for a set of components that is dedicated to an application domain, a workflow, or a closely related set of capabilities. An `NgModule` can associate its components with related code, such as services, to form functional units.

Every Angular application has a `root module`, conventionally names `AppModule`, which provides the bootstap mechanism that launches the application. An application typically contains many functional modules.

Like `JavaScript` modules, `NgModules` can import functionality from other `NgModules`, and allow their own functionality to be exported and used by other `NgModules`. For example, to use the router service in your App, you import the `Router` `NgModule`.

Organizing your code distinct functional modules helps in managing development of complex application and in designing for reusability. In addition, this technique lets you  take advantage of `lazy-loading` - that is, loading modules on demand - to minimize the amount of code that needs to be loaded on startup.

## Components

Every Angular application has at least one component, root component that connect a component hierarchy with the page document object model ( #DOM ). Each component defines a class that contains application data and logic, and is assiciated with as HTML template that defines a view to be displayed in a target environment.

The `@Component()` decorator identifies the class immediatelly below it as a component, and provides the template and related component-specific metadata.

## Template, directives, and data binding

A template combines HTML with Angular markup that can modify HTML elements before they are displayed. Template directives provide program logic, and binding markup connects your application data and the DOM. 
Two types of data bindings:

|Data bindings | Details| 
|------------ | ------------| 
| Event binding | Lets your application respond to user input in the target environment by updating your application data. |
| Property binding | Lets you interpolate values that are computed from your application data into the HTML. |

Before a view is displayed, Angular evaluates the directives and resolves the binding syntax in the template to modify the HTML elements and the DOM, according to your program data and logic. Angular supports two-way data binding, meaning that changes in the DOM, such as user choices, are also reflected in your program data.

You templates can use pipes to improve the user experience by transforming values for diplay. For example, use pipes to display dates and currency values that are appripriate for a user's locale. Angular provides predefined pipes for common transformations, and you can also define your own pipes.

## Services and dependency injection

For data or logic that isn't associated with a specific view, and that you want to shate across components, you create a service class. A service class definition is immediately  preceded by the `@Injectable()` decorator. The decorator provides the metadata that allows other provides to be injected as dependencies into your class.

Dependency injection (DI) lets you keep your component classes lean and efficient. They don't fetch data from the server, validate user input, or log directly to the console; they delegate such tasks to services.

## Routing

The Angular `Router` NgModule provides a service that lets you define a navigation path among the different application states and view hierarchies in your application. It is modeled on the familiar browser navigation conventions:

- Enter a URL in the address bar and the browser navigates to a corresponding page
- Click links on the page and the browser navigates to a new page
- Click the browser's back and forward buttons and the browser navigates backward and forward through the history of pages you've seen

The router maps URL-like paths to views instead of pages. When a user performs an action, such as clicking a link, that would load a new page in the browser, the router intercepts the browser's behavior, and shows or hides view hierarchies.

If the router determines that the current application state requires particular functionality, and the module that defines it hasn't been loaded, the router can lazy-load the module on demand.

The router interprets a link URL according to your application's view navigation rules and data state. You can navigate to new views when the user clicks a button or select from a drop box, or in response to some other stimulus from any source. The router log activity in the browser's history, so the back and forward buttons work as well.

TO define navigation rules, you assosiate navigation paths with your components. A path uses a URL-like syntax that integrates your program data, in much the same way that template syntax integrates your views with your program data. You cat then apply program logic to choose which views to show or to hide, in response to user input and your own access rules
