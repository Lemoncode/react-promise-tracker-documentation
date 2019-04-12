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


## usePromiseTracker

React Promise Tracker custom hook, this hook will expose a promiseInProgress boolean flag.

**Typescript definition**

```typescript 
export function usePromiseTracker(outerConfig? : Config) : { promiseInProgress : boolean };
```

## promiseTrackerHoc

 It wraps a given React component into a new component that adds properties to watch pending promises (HOC).

Parameters:
 - Component: component to wrap.

Booelan property added to wrapped component: _promiseInProgress_

**Typescript definition**

```typescript
export function promiseTrackerHoc<P>(component: React.ComponentType<P & ComponentToWrapProps>): React.ComponentType<P & TrackerHocProps>;
```

## Config

Configuration contract: user can setup areas (display more than one spinner) or delay when the spinner is shown (this is useful when a user has a fast connection, to avoid unneccessary flickering)

**Typescript definition**

```typescript
interface Config {
   area: string;
   delay: number;
}
```