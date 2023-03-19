<p align="left">
  <a href="https://badge.fury.io/js/bang-button">
    <img src="https://badge.fury.io/js/bang-button.svg" alt="npm version">
  </a>
    <img src="https://img.shields.io/badge/Licence-MIT-success" alt="Jest is released under the MIT license." />
  <a href="https://github.com/Ashish-simplecoder/bang-button/actions/workflows/main.yml">
    <img src="https://img.shields.io/github/actions/workflow/status/Ashish-simpleCoder/bang-button/main.yml?label=CI&logo=GitHub" alt="Jest is released under the MIT license." />
  </a>
</p>

# awesome-react-components

An Awesome React Library for **Utility** **Components** and **Hooks**

## Installation

For npm users

```bash
$ npm install awesome-react-components
```

For pnpm users

```bash
$ pnpm install awesome-react-components
```

For yarn users

```bash
$ yarn add awesome-react-components
```

## Components

-  [If](#if)
-  [Then](#then)
-  [Else](#else)

## If

| Prop      |   Type    | Required | Default  | Description                                                                           |
| --------- | :-------: | :------: | :------: | ------------------------------------------------------------------------------------- |
| condition |    any    |    ❌    |  false   | Based on evaluation of the condition flag the component will return null or children  |
| children  | ReactNode |    ❌    |   null   | To render the children                                                                |
| suspense  |  boolean  |    ❌    |  false   | To lazy load the component or not                                                     |
| fallback  | ReactNode |    ❌    | Fragment | Fallback needed to show unless the component is loaded fully for suspensed components |

### Working

-  If you pass only one children and condition is false then it will return null otherwise the childen will be rendered.
-  If you pass two or more childs and condition is false then it will return all of the children except first child otherwise the first child will be rendered.

### Example

```tsx
import { If } from 'awesome-react-components';

// For react lazy loading
import { lazy } from 'react';
const SomeLazyComponent = lazy(() => import('./some-lazy-component'));

// For nextjs lazy loading
import dynamic from 'next/dynamic';
const SomeLazyComponent = dynamic(() => import('./some-lazy-component'), { ssr: false });

export default function YourComponent() {
   return (
      <div>
         {/* Passing only one children and a condition prop */}
         <If codition={true}>
            <h1>this will render.</h1>
         </If>

         {/* Passing more than one children and a truthy condition prop */}
         <If codition={true}>
            <h1>this is will render</h1>
            <h2>this is will not render. As condition it truthy, the first children will render</h2>
         </If>

         {/* Passing more than one children and a falsy condition prop */}
         <If codition={falsy}>
            <h1>this is will not render</h1>
            <h2>this is will render. As condition it falsy, then second children will render</h2>
            <h2>this is will also render</h2>
         </If>

         {/* Passing two childrens, condition and suspense prop */}
         <If codition={false} suspense>
            {/* this component code file will only download when the condition will be true.
             In this case, codition is falsy then it will not be downloaded. */}
            <SomeLazyComponent />
            <h2>this is will render</h2>
         </If>
      </div>
   );
}
```

## Then

| Prop     |   Type    | Required | Default | Description                 |
| -------- | :-------: | :------: | :-----: | --------------------------- |
| children | ReactNode |    ❌    |  null   | Renders the passed children |

### Example

```tsx
import { If, Then } from 'awesome-react-components';

export default function YourComponent() {
   return (
      <div>
         <If codition={true}>
            <Then>
               <h1>this will render.</h1>
            </Then>
         </If>
      </div>
   );
}
```

## Else

| Prop     |   Type    | Required | Default | Description                 |
| -------- | :-------: | :------: | :-----: | --------------------------- |
| children | ReactNode |    ❌    |  null   | Renders the passed children |

### Example

```tsx
import { lazy } from 'react';
import { If, Then, Else } from 'awesome-react-components';

export default function YourComponent() {
   return (
      <div>
         <If codition={true}>
            <Then>
               <h1>this will render.</h1>
            </Then>
         </If>

         <If codition={true}>
            <Then>
               <h1>this will render.</h1>
            </Then>
            <Else>
               <h1>this will not render.</h1>
            </Else>
         </If>
      </div>
   );
}
```
