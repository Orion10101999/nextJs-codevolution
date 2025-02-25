## Tutorial - 11 - File Colocation :-

## Tutorial - 12 - Private Folders :-

* A private folder indicates that it is a private implementation detail and should not be considered by the routing system . 

* The folder and all its subfolders are excluded from routing .

* Prefix the folder name with an underscore 


```css

app - |
      |
      | - _lib
            |
            | - format-date.tsx
            | - page.tsx

```

### Private Folders contd. :-

* For separating UI logic from routing logic .

* For consistently organizing internal files across a project .

* For sorting and grouping files in code editors .

* And finally , for avoiding potential naming conflicts with future Next.js file conventions .

*  If you want to include an underscore in URL segments , you can prefix the folder name with "%5F" , which is the URL-encoded form of an underscore .

## Tutorial - 13 - Route Groups :-

* Allows us to logically group our routes and project files without affecting the URL path structure .

* Let's implement authentication routes .

- Register 

- Login

```css

localhost:3000/auth/register
localhost:3000/auth/login

src - |
      | - app
           |
           | - auth
                |
                | - register
                |      | 
                |      | - page.tsx 
                |
                |
                | - login
                |      | 
                |      | - page.tsx 

                
```

```css

localhost:3000/register
localhost:3000/login

src - |
      | - app
           |
           | - (auth)
                 |
                 | - register
                 |       | 
                 |       | - page.tsx 
                 |
                 |
                 | - login
                 |      | 
                 |      | - page.tsx 


```

### Layouts :-

* A page is UI that is unique to a route .

* A Layout is UI that is shared between multiple pages in the app .

```css

________________________________________________

                    Header
_________________________________________________



                    Content


_________________________________________________

                    Footer

_________________________________________________

```

## How to Create Layouts :-

* You can define a layout by default exporting a React component from a layout.js or layout.tsx file .

* That component should accept children prop that will be be populated with child page during rendering .

```tsx

import type { Metadata } from "next";
import { Inter } from "next/font/google";
import "./globals.css";

const inter = Inter({ subsets: ["latin"] });

export const metadata: Metadata = {
  title: "Create Next App",
  description: "Generated by create next app",
};

export default function RootLayout({
  children,
}: Readonly<{
  children: React.ReactNode;
}>) {
  return (
    <html lang="en">
      <body className={inter.className}>{children}</body>
    </html>
  );
}


```

### Example :-1

```css

app 
 |
 | - layout.tsx
 |
 | - about
 |    |
 |    | - page.tsx
 |    
 | - profile
 |      |
 |      | - page.tsx
 |      
 | - page.tsx

```


```css

______________________________________________
    localhost:3000
_______________________________________________
_______________________________________________
                    Header
_________________________________________________


                    Home

_________________________________________________
                    Footer
_________________________________________________

```

```css

______________________________________________
    localhost:3000/about
_______________________________________________

________________________________________________

                    Header
_________________________________________________



                    About

_________________________________________________

                    Footer

_________________________________________________

```

```css

______________________________________________
    localhost:3000/profile
_______________________________________________

________________________________________________

                    Header
_________________________________________________



                    Profile

_________________________________________________

                    Footer

_________________________________________________

```

### Example :- 2

```css

app 
 |
 | - layout.tsx
 |
 | - products
 |    |
 |    | - [productId]
 |    |         |    
 |    |         | - layout.tsx
 |    |         |    
 |    |         | - page.tsx
 |    |         |    
 |    |
 |    | - page.tsx
 |      
 | - page.tsx

```
______________________________________________
*    localhost:3000
______________________________________________

```css
_______________________________________________
                    Header
_________________________________________________


                    Layout

_________________________________________________
                    Footer
_________________________________________________

```

______________________________________________
*    localhost:3000/products
_______________________________________________
```css
_______________________________________________
                    Header
_________________________________________________


            List Of Products

_________________________________________________
                    Footer
_________________________________________________

```

______________________________________________
*    localhost:3000/products/1
_______________________________________________

```css
_______________________________________________
                    Header
_________________________________________________

    |--------------------------------------|
    |                                      |
    |               Product 1              |
    |                                      |
    ________________________________________

                Featured products
_________________________________________________
                    Footer
_________________________________________________

```
______________________________________________
*    localhost:3000/products/2
_______________________________________________

```css
_______________________________________________
                    Header
_________________________________________________

    |--------------------------------------|
    |                                      |
    |               Product 2              |
    |                                      |
    ________________________________________

                Featured products
_________________________________________________
                    Footer
_________________________________________________

```


###  Tutorial - 16 - Route Group Layout :-

### Route Group Layout :-

### route Group uses :-

* To organise your project in a manner that doesn't affect the URL 

* To selectively apply a layout to certain while leaving others unchanged .


### Tutorial - 17 - Routing Metadata

### Routing Metadata :-

* Ensuring proper search engine optimization (SEO) is crucial for increasing visibility and atttracting users .

* Next.js introduces the Metadata API which allows you to define metadata for each page .

* Metadata ensures accurate and relevent information is displayed when your pages are shared or indexed .

### Configuring Metadata :-

* Export a static metadata object .

* Export a dynmic generateMetadata function .

### metadata rules :-

* Both layout.tsx and page.tsx files can export metadata . If defined in a page , it applies only to that page .

* Metadata is read in order , from the root level down to the final page level .

* when there's metadata in multiple places for the same route , they get combined , but page metadata will replace layout metadata if they have the same properties .

### Tutorial - 18 - title Metadata :-

* The title field's primary purpose is to define the document title .

* It can either a string or an object .

### Tutorial - 19 - Link Component Navigation :-

### Navigation :-

* File based routing :-

* We manually entered the URLs in the browser's address bar to navigate different routes .

* Users rely on UI elements like links to navigate 

* Clicking on them or 

* Through programmatic navigation after completing an action .

### Link component Navigation :-

* To enable client-side navigation Next.js provides us with the Link component .

* The `<Link>` component is a React component that extends the Html `<a>` element , and it's the primary way to navigate between routes in Next.js 

* To use it , we need to import it from "next/link".

* replace

* usePathname()

### Navigating Programmatically :-

* useRouter()

* router.push("/")
* router.replace("/")
* router.back()
* router.forward()

### Tutorial - 22 - Templates :-

* Templates are similar to layouts in that they wrap each child layout or page .

* But , with templates , when a user navigates between routes that share a template , a new instance of the component is mounted , DOM elements are recreated , state is not preserved , and effects are re-synchronized .

* A templete can be defined by exporting a default React component from a template.js or template.tsx file 

* Similar to layouts , templates also should accept a children prop which will render the nested  segments in the route .


```css

                layout.tsx
______________________________________________
|                                             |
|               template.tsx                  |
|        |---------------------------|        |
|        |                           |        |
|        |                           |        |
|        |        page.tsx           |        |
|        |                           |        |
|        |---------------------------|        |
|                                             |
|                                             |
|                                             |
|                                             |
_______________________________________________

```

### Special Files :-

1. page.tsx

2. layout.tsx

3. template.tsx

4. not-found.tsx

5. loading.tsx

### loading.tsx

* This file allows us to create loading states that are displayed to users while a specific route segment's content is loading .


* the loading state appears immediately upon navigation , giving users the assurance that the application is responsive and actively loading content .

### loading.tsx Benefits :-

1. You can display the loading state as soon as a user navigates to a new route .

2. Next.js allows the creation of shared layouts that remain interactive while new route segments are loading 

* Users can continue interacting with certain parts of the application , such as a navigation menu or sidebar , even if the main content is still being fetched .

### Special Files :-

1. page.tsx

2. layout.tsx

3. template.tsx

4. not-found.tsx

5. loading.tsx

6. error.tsx

### error.tsx :-

* Automatically wrap a route segment and its nested children in a React Error Boundary .

* Create error UI tailored to specific segments using the file-system hierarchy to adjust granularity .

* Isolate errors to affects segments while keeping the rest of the applicationfunctional .

* And functionaly to attemt to recover from an error without a full page reload .

### Component Hierarchy :-

* layout.js

* template.js

* error.js

* loading.js

* not-found.js

* page.js

### Handling Errors in Nested Routes :-

* Errors bubble up to the closest parent error boundary .

* An error.tsx file will cater to errors for all its nested segments .

* By positioning error.tsx files at different levels in the nested folders of a route , you can achieve a more granular level of error handling .

### Hndling Errors in Layouts :-

* An error.tsx file will handle errors for all its nested child segments .

* The error boundary does not catch errors thrown here because it's nested inside the layouts component .

### Component Hierarchy :-

* layout.js

* template.js

* error.js

* loading.js

* not-found.js

* page.js

### Parallel Routes :-

* Parallel routes are an advanced routing mechanism that allows for the simultaneous rendering of multiple pages  within the same layout .

### Parallel Routes :-

### Scenario 7 :-

* localhost:3000/dashboard

```css
___________________________________________

            Header
-------------------------------------------

DashBoard

|---------------|    |------------------|
|User analytics |    |                  |
|---------------|    |                  |
                     | Notifications    |
|---------------|    |                  |
|revenue metrics|    |                  |
|---------------|    |------------------|


__________________________________________

        Footer
--------------------------------------------

```

### Parallel Routes contd. 

* Parallel routes in Next.js are defined using a feature known as slots

* Slots help structure our content in a modular fashion .

* To define a slot , we use the `@folder` naming convention

* Each slot is then passed as a prop to its corresponding `layout.tsx` file .

```css

app
 |
 | - dashboard 
        |
        | - @notifications
        |         |
        |         | - page.tsx
        |         
        | - @revenue
        |         |
        |         | - page.tsx
        |         
        | - @users
        |      |
        |      | - page.tsx
        |         


```

### Parallel Routes Benefits :-

* A clear benefits of parallel routes is their ability to split a single layout into various slots , making the code more manageble .

### Independent Route Handling :-

* Each slot of your layout , such as user analytics or revenue metrics , can have its own loading and error states.

* This granular control is particularly beneficial in scenarios where different sections of the page load at varying speeds or encounter unique errors .


### Loading :-

* localhost:3000/dashboard

```css
___________________________________________

            Header
-------------------------------------------

DashBoard

|---------------|    |------------------|
|  Loading...   |    |                  |
|---------------|    |                  |
                     | Notifications    |
|---------------|    |                  |
|revenue metrics|    |                  |
|---------------|    |------------------|


__________________________________________

        Footer
--------------------------------------------
```

### Error :-

* localhost:3000/dashboard


```css
___________________________________________

            Header
-------------------------------------------

DashBoard

|---------------|    |------------------|
|User analytics |    |                  |
|---------------|    |                  |
                     | Notifications    |
|---------------|    |                  |
|   Error..     |    |                  |
|---------------|    |------------------|


__________________________________________

        Footer
--------------------------------------------

```

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

