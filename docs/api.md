# API

## createLogger(config)

```tsx
const [{ Provider, DOMEvent, Click, Impression, PageView, SetContext }, useLog] = createLogger({
  init,
  send,
  DOMEvents,
  impression: {
    onImpression,
    options,
  },
  pageView: {
    onPageView,
  },
  batch,
});
```

### Parameter1 (Config)

- `init: (initialContext: Context) => void | Promise<void>`
  - **optional**
  - The function that should be executed before any events happen.
  - If it returns a promise, the events will be delayed until the promise is resolved.
- `send: (params: Params, context: Context) => TaskReturnType`
  - **optional**
  - A standard function to send events.
  - If it returns a promise, the events will be delayed until the promise is resolved.
- `DOMEvents: DOMEvents`
  - **optional**
  - A collection of DOM event handlers.
  - Supports standard React DOM events (`onClick`, `onMouseEnter`, etc.).
  - Each event handler is executed when that event occurs on a child for `<Log.DOMEvent type=[event type]>`.
  - If it returns a promise, the events will be delayed until the promise is resolved.
- `impression`
  - `onImpression: (params: P, context: C) => TaskReturnType`
    - **optional**
    - A function that is executed when impression occurs on a child for `<Log.Impression>`.
    - If it returns a promise, the events will be delayed until the promise is resolved.
  - `options: ImpressionOptions`
    - **optional**
    - `threshold: number`
      - **optional**
      - defaults to `0.2`.
      - A value indicating the percentage of the target's visibility needed to trigger `onImpression`.
    - `freezeOnceVisible: boolean`
      - **optional**
      - defaults to `true`.
      - If `true`, freezes the intersection state once the target becomes visible.
    - `initialIsIntersecting: boolean`
      - **optional**
      - defaults to `false`.
      - The initial state of the intersection.
- `pageView`
  - `onPageView: (params: P, context: C) => TaskReturnType`
    - **optional**
    - The function that is executed when `<Log.PageView>`is mounted.
    - If it returns a promise, the events will be delayed until the promise is resolved.
- `batch: SchedulerConfig["batch"]`
  - **optional**
  - `enable: boolean`
    - **optional**
    - defaults to `false`.
    - Whether batching is enabled.
  - `interval: number`
    - **optional**
    - defaults to `3000`.
    - The interval(ms) to flush event results.
  - `thresholdSize: number`
    - **optional**
    - defaults to `25`.
    - The max size of the batch until it is flushed.
  - `onFlush: (results: EventResults[], isBrowserClosing: boolean) => void | Promise<void>`
    - **required when `enable` is `true`**
    - The function to flush the event results.
    - The second parameter can be used to correctly handle situations when the browser is not visible or closing.
  - `onError: (error: Error) => void | Promise<void>`
    - **optional**
    - The function to handle the error.

### Return Array Value1

- [`Provider`](./components.md##Provider)
- [`DOMEvent`](./components.md##DOMEvent)
- [`Click`](./components.md##Click)
- [`Impression`](./components.md##Impression)
- [`PageView`](./components.md##PageView)
- [`SetContext`](./components.md##SetContext)

### Return Array Value2

- [`useLog`](./hook.md)