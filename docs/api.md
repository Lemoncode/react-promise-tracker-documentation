---
id: api
title: Api
---

## TrackPromise

It tracks a promise while in pending state. @param promise Input promise to be tracked. @returns It returns the same promise as input.

**Typescript definition**

```typescript
export function trackPromise(promise: Promise<any>): Promise<any>;
```

**Paramaters:**
  - promise: promise to be tracked.

**Returns:**
  - The same promise that was passed as argument (chain pattern).

## usePromiseTracker

React Promise Tracker custom hook, this hook will expose a promiseInProgress boolean flag.

**Typescript definition**

```typescript 
export function usePromiseTracker(outerConfig? : Config) : { promiseInProgress : boolean };
```

**Parameters:**

- outerConfig: optional configuration parameters (area and delay), see _Config_
section on this api for more information.

**Returns:**

- _promiseInProgress_ boolean flag.

## promiseTrackerHoc

 It wraps a given React component into a new component that adds properties to watch pending promises (HOC).

**Typescript definition**

```typescript
export function promiseTrackerHoc<P>(component: React.ComponentType<P & ComponentToWrapProps>): React.ComponentType<P & TrackerHocProps>;
```

**Parameters:**
 - Component: component to wrap.

Boolean property added to wrapped component: _promiseInProgress_

## Config

Configuration contract: user can setup areas (display more than one spinner) or delay when the spinner is shown (this is useful when a user has a fast connection, to avoid unneccessary flickering)

**Typescript definition**

```typescript
interface Config {
   area: string;
   delay: number;
}
```

**Fields:**

- _area_:
    - Accepted values: true / false (boolean)-
    - Optional parameter.
    - You can define named areas and display multiple spinners (e.g. block just certain part of the screen).
-_delay_:
    - Accepted values 1..99999 (milliseconds)
    - Optional parameter.
    - Whenever a promise is getting fired, wait X milliseconds to display the spinner
    (on fast internet connections likely after that amount of time the ajax
    request is already fullfille.)