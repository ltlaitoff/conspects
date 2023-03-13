Angular applications are modular and Angular has its own modularity system called NgModules. NgModules are containers fgor a cohesive block(связанный блок) of code dedicated to an application domain, a workflow, or a closely related set of capabilities. They can contain components, service providers, and other code files whose scope is defined by the containing NgModule. They can import functionality that is exported from other NgModules, and export selected functionality for use by other NgModules.

Every Angular application has at least one NgModule class, the root module, which is conventionally named `AppModule` ans resides in a file named `app.module.ts`. You launch your application by boostrapping the root NgModule.

While a small application might have only one NgModule, most applications have many more feature modules. The root NgModule for an application is so named because it can include child NgModules in a hierarchy of any depth.

## NgModule metadata

An NgModule is defined by a class decorated with `@NgModule()`. The `@NgModule()` decorator is a function that takes a single metadata object, whose properties describe the module. The most important properties are as follows.

|Properties | Details | 
|------------ | ------------| 
| `declarations` | The components, directives, and pipes that belong to this NgModule |
| `exports` | The subset of declarations that should be visible and usable in the component templates of other NgModules. |
| `imports` | Other modules whise exported classes are needed by component templates declared in this NgModule |
| `providers` | Creators of services that this NgModule contributes to the global collection of services; they become accessible in all parts of the application|
| `bootstrap` | The main application view, called the root component, which hosts all other application views. Only the root NgModule should set the `bootstrap` property |

Here's a simple root NgModule definition.

```ts
import { NgModule } from '@angular/core';
import { BrowserModule } from '@angular/platform-browser';

@NgModule({
  imports:      [ BrowserModule ],
  providers:    [ Logger ],
  declarations: [ AppComponent ],
  exports:      [ AppComponent ], // Not need in root component
  bootstrap:    [ AppComponent ]
})
export class AppModule { }
```


## NgModules and components

NgModules provide a compolation context for their components. A root NgModule always has a root component that is created during bootstap but any NgModule can include any number of additional components, which can be loaded throught the router   or created throught the template. The components that belong to an NgModule share a compilation context.

![[Introduction to modules A.png]]

A component ant its template together define a view. A component can contain a view hierarchy, which allows you to define arbitrarily complex areas of the screen that can be created, modified, and destroyes as a unit. A view hierarchy can mix views defined in components that belong to different NgModules. This is often the case, especially for UI libraries.

![[Introduction to modules B.png]]

When you create a component, it's associated directly with a single view, called the host view. The host view can be the root of a view hierarchy, which can contain embedded views, which are in turn the host views of other components. Those components can be in the same NgModule, or can be imported from other NgModules. Views in the tree can be nested to any depth.

