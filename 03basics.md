
### Sub-navigation in routes :-

* Each slot of your dashboard can essentially function as a mini-application , with its own navigation and state management .

* This is especially useful in a complex application such as our dashboard where different sections serve distinct purposes .

### Sub-navigation in routes contd. :-

### Sub-navigation :-


* localhost:3000/dashboard

```css
___________________________________________

            Header
-------------------------------------------

DashBoard

|---------------|    |------------------|
|User analytics |    |                  |
|---------------|    |  Default         |
                     | Notifications    |
|---------------|    |                  |
|revenue metrics|    |                  |
|---------------|    |------------------|


__________________________________________

        Footer
--------------------------------------------

```


* localhost:3000/dashboard/archived

```css
___________________________________________

            Header
-------------------------------------------

DashBoard

|---------------|    |------------------|
|User analytics |    |                  |
|---------------|    | Archived         |
                     | Notifications    |
|---------------|    |                  |
|revenue metrics|    |                  |
|---------------|    |------------------|


__________________________________________

        Footer
--------------------------------------------

```

### Unmatched Routes :-

* Navigation from the UI :-

* In the case of navigation within the UI , Next.js  retains the previously active state of a slot regardless of changes in the URL .


### Page reload :-

* Next.js immediately searches for a default.tsx file within each unmatched slot .

* The presence of this file is critical , as it provides the default content that Next.js will render in the user interface .

* If this default.tsx file is critical , as it provides the default.tsx file is missing in any of the unmatched slots for the current route , Next.js will render a 404 error .

### default.tsx :-

* The `deault.tsx` file in Next.js serves as a fallback to render content when the framework cannot retrive a slot's active state from the current URL .

* You have complete freedom to define the UI for unmatched routes : you can either mirror the content found in page.tsx or craft an entirely custom view .


### Tutorial - 31 - Intercepting Routes :-

### Advanced Routing Patterns :-

* Parallel routes 

* Intercepting routes 

### Intercepting Routes :-

* Intercepting routes allow you to intercept or stop the default routing behavior to present an alternate view or component when navigating through the UI , while still preserving the intended route for scenarios like page reloads 

* This can be useful if you want to show a route while keeping the context of the current page .

### Intercepting Routes Conventions :-

* (.) to match segments on the same level .

* (..) to match segments one level above .

* (..)(..) to match segments two level above .

* (...) to match segments from the root app directory .

## Advanced Routing Patterns :-

* Parallel routes

* Intercepting routes 