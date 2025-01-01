## useLog

`useLog` is a hook that provides the functions given in `createLogger` config. It also provides the function to get and set the context.

```tsx
import { useLog } from "@loggists/logger";

const { init, send, setContext, getContext, DOMevents, onImpression, onPageView } = useLog();
```

### Return Value

- `init: (params: unknown) => void`
- `send: (params: unknown) => void`
- `setContext: (params: unknown) => void`
- `getContext: () => unknown`
- `events: Record<keyof EventNames, (params: unknown) => void>`