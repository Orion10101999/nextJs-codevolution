## What is Next.js ?

* Next.js is a React framework for building web applications .

### React :-

* It's not feasible to create a fully-featured application for production

* React is a library for building user interfaces .

* You need to make decisions about other features such as routing , data fetching and more 

### Next.js :-

* It uses React for building user interfaces .

* Provides additional features that enable you to build production-ready applications 

* These features include routing , optimized rendering , data fetching , bundling , compling , and more .

* You don't need to install additional packages as Next.js provides everything you need 

* Opinions and conventions should be followed these features .


## What is Next.js ?

### Next.js is a react framework for building web applications .


## Why learn Next.js ?

* Next.js simplifies the process of building a web application for production .

1. Routing
2. API routes
3. Rendering
4. Data fetching
5. Styling
6. Optimization 
7. Dev and prod build system .

## Prerequisities :-

* HTML , CSS and JavaScript fundamentals .

* ES6 + features 

* React fundamentals 

## React Server Component (RSC) :-

* React Server Components is a new architecture introduced by the React team in version 18 which was quickly embraced by Next.js .

* The architecture introduces a new way of creating React components , splitting them into two types .

- Server components .

- Client components .

### Server Components :-

* In Next.js , all components are Server components by default .

* They have the ability to run tasks like reading files or fetching data from a database .

* However , they don't have the ability to use hooks or handle user interactions 

### Client Components :-

* To Create a Client component , it's necessary to add "use client" at the top of the component file .

* Client components can't perform tasks like reading files , but they have the ability to use hooks and manage interactions .

### React Server Components and Routing :-

* We'll explore examples where we use server components that await certain actions to finalize before rendering content on the screen .

* We'll also see examples where we use client components to leverage hooks from the routing module .

## Routing :-

* Next.js has a file-system based routing mechanism .

* URL has a file-System based routing mechanism .

* URL paths that users can access in the browser are defined by files and folders in your codebase .

## Routing Conventions :-

* All routes must be placed inside the app folder .

* Every file that corresponds to a route must be named page.js or page.tsx 

* Every folder corresponds to a path segment in the browser URL .

## File Based Routing :-

### Scenario 1 

```css
|------------------------------------------------|
|   localhost:3000                               |
|________________________________________________|
|                                                |
|                                                |
|                                                |
|                                                |
|                                                |
|               Home Page                        |
|                                                |
|                                                |
|                                                |
|                                                |
|________________________________________________|



src - |
      |
      | - app
          |
          | - page.tsx , page.js
   
   
```


### Scenario 2 

```css
|------------------------------------------------|
|   localhost:3000/about                         |
|________________________________________________|
|                                                |
|                                                |
|                                                |
|                                                |
|                                                |
|               About Page                       |
|                                                |
|                                                |
|                                                |
|                                                |
|________________________________________________|

src - |
      |
      | - app
          |
          | - about
                |
                |
                | - page.tsx , page.js
   
```


### Scenario 2

```css
|------------------------------------------------|
|   localhost:3000/profile                       |
|________________________________________________|
|                                                |
|                                                |
|                                                |
|                                                |
|                                                |
|               Profile Page                     |
|                                                |
|                                                |
|                                                |
|                                                |
|________________________________________________|


src - |
      |
      | - app
          |
          | - profile
                |
                |
                | - page.tsx , page.js
   


```

## Nested routes :-

### Scenario 3

```css
|------------------------------------------------|
|   localhost:3000/blog                          |
|________________________________________________|
|                                                |
|                                                |
|                                                |
|                                                |
|                                                |
|               Blog Page                        |
|                                                |
|                                                |
|                                                |
|                                                |
|________________________________________________|

src - |
      |
      | - app
          |
          | - blog
                |
                |
                | - page.tsx , page.js
   


```

```css
|------------------------------------------------|
|   localhost:3000/blog/first                    |
|________________________________________________|
|                                                |
|                                                |
|                                                |
|                                                |
|                                                |
|               First Blog Page                  |
|                                                |
|                                                |
|                                                |
|                                                |
|________________________________________________|

src - |
      |
      | - app
          |
          | - blog
                |
                | - first
                      |
                      | - page.tsx , page.js
   

```

```css
|------------------------------------------------|
|   localhost:3000/blog/second                   |
|________________________________________________|
|                                                |
|                                                |
|                                                |
|                                                |
|                                                |
|               Second Blog Page                 |
|                                                |
|                                                |
|                                                |
|                                                |
|________________________________________________|


src - |
      |
      | - app
          |
          | - blog
                |
                | - second
                      |
                      | - page.tsx , page.js
   



```

```css
app
 | - blog
 |     | - first
 |     |     | - page.tsx    
 |     |
 |     | - second
 |     |      | - page.tsx
 |     |
 |     | - page.tsx
 |     |
 |
 | - layout.tsx
 |
 | - page.tsx
 |

 ```

## Dynamic Routes :-

### Scenario 4 

```css

|------------------------------------------------|
|   localhost:3000/products                      |
|________________________________________________|
|                                                |
|                                                |
|                                                |
|                                                |
|                                                |
|               Product 1                        |
|               Product 2                        |
|               Product 3                        |
|                                                |
|                                                |
|                                                |
|                                                |
|________________________________________________|


src - |
      |
      | - app
          |
          | - products
                |
                |
                | - page.tsx , page.js


   
```

```css

|------------------------------------------------|
|   localhost:3000/products/id                   |
|________________________________________________|
|                                                |
|                                                |
|                                                |
|                                                |
|                                                |
|               Product Details                  |
|                                                |
|                                                |
|                                                |
|                                                |
|________________________________________________|

src - |
      |
      | - app
          |
          | - products
                |
                |
                | - [productId]
                        |
                        |
                        | - page.tsx , page.js


```

```css

|------------------------------------------------|
|   localhost:3000/products/1                    |
|________________________________________________|
|                                                |
|                                                |
|                                                |
|                                                |
|                                                |
|               Product 1 Details                |
|                                                |
|                                                |
|                                                |
|                                                |
|________________________________________________|


```

```css

|------------------------------------------------|
|   localhost:3000/products/50                   |
|________________________________________________|
|                                                |
|                                                |
|                                                |
|                                                |
|                                                |
|               Product 50 Details               |
|                                                |
|                                                |
|                                                |
|                                                |
|________________________________________________|


```

```css

|------------------------------------------------|
|   localhost:3000/products/100                  |
|________________________________________________|
|                                                |
|                                                |
|                                                |
|                                                |
|                                                |
|               Product 100 Details              |
|                                                |
|                                                |
|                                                |
|                                                |
|________________________________________________|


```
```css

|------------------------------------------------|
|   localhost:3000/products/1/reviews/1          |
|________________________________________________|
|                                                |
|                                                |
|                                                |
|                                                |
|                                                |
|               Product 1 Details                |
|               reviews 1 Details                |
|                                                |
|                                                |
|                                                |
|                                                |
|________________________________________________|


src - |
      |
      | - app
          |
          | - products
                |
                |
                | - [productId]
                        |
                        |
                        | - reviews
                                |
                                |
                                | - [reviewId]
                                       |
                                       |
                                       | - page.tsx 
                                       | - page.js

```


```tsx

import React from 'react'

const ReviewId = ({ params } : { params : { reviewId : string , productId : string}}) => {
    return (
        <div>Review Details Id: { params.reviewId } <span>
        Product Id : {params. productId}
        </span></div>
  )
}

export default ReviewId


```

## Catch - all Segments :-

### Scenario - 6 :-
```css

      
      |------------------------------------------------|
      |   localhost:3000/docs/feature1/concept1        |
      |________________________________________________|
      |                                                |
      |                                                |
      |                                                |
      |                                                |
      |                                                |
      |                                                |
      |                                                |
      |                                                |
      |________________________________________________|

                        |
Feature 1               |
                        |
    Concept 1           |
    Concept 2           |
    Concept 3           |
    Concept 4           |
    Concept 5           |
                        |   Docs for F1 C1
Feature 2               |        
Feature 3               |
Feature 4               |
Feature 5               |
                        |


localhost:3000/docs/feature1/concept1
localhost:3000/docs/feature2/concept2
localhost:3000/docs/feature3/concept3
localhost:3000/docs/feature4/concept4

```

```
* 20 Features X 20 Concepts = 400

* 20 Features X 1 [ConceptId] = 20

* 1 [featureId] X 1 [conceptId] = 1

localhost:3000/docs/feature1/concept1/example1

```


```css

localhost:3000/docs/routing/catch-all-segments

| - app
|    |
|    | - docs
|    |    | - [...slugs]
|    |              | 
|    |              | - page.tsx
|    | - page.tsx
|
| - page.tsx
|
| - layout.tsx

```
* No need make page.tsx for docs if we use [[...slugs]]

```css

localhost:3000/docs/routing/catch-all-segments

| - app
|    |
|    | - docs
|    |    | - [[...slugs]]
|    |               | 
|    |               | - page.tsx
|    
|
| - layout.tsx
|
| - page.tsx

```

## For Making Not Found Page :-

### not-found.tsx


