# RTK-QUERY-CRUD
RTK Query is a powerful data fetching and caching tool. It is designed to simplify common cases for loading data in a web application, eliminating the need to hand-write data fetching &amp; caching logic yourself.

RTK Query takes inspiration from other tools that have pioneered solutions for data fetching, like Apollo Client, React Query, Urql, and SWR, but adds a unique approach to its API design:

1) The data fetching and caching logic is built on top of Redux Toolkit's createSlice and createAsyncThunk APIs
2) Because Redux Toolkit is UI-agnostic, RTK Query's functionality can be used with any UI layer
3) API endpoints are defined ahead of time, including how to generate query parameters from arguments and transform responses for caching
4) RTK Query can also generate React hooks that encapsulate the entire data fetching process, provide data and isLoading fields to components, and manage the lifetime of cached data as components mount and unmount
5) RTK Query provides "cache entry lifecycle" options that enable use cases like streaming cache updates via websocket messages after fetching the initial data
6) We have early working examples of code generation of API slices from OpenAPI and GraphQL schemas
7) Finally, RTK Query is completely written in TypeScript, and is designed to provide an excellent TS usage experience

  RTK Query includes these APIs:

1) createApi(): The core of RTK Query's functionality. It allows you to define a set of "endpoints" that describe how to retrieve data from backend APIs and other async sources, including the configuration of how to fetch and transform that data. In most cases, you should use this once per app, with "one API slice per base URL" as a rule of thumb
2)  fetchBaseQuery(): A small wrapper around fetch that aims to simplify requests. Intended as the recommended baseQuery to be used in createApi for the majority of users.
3)  <ApiProvider />: Can be used as a Provider if you do not already have a Redux store.
4)  etupListeners(): A utility used to enable refetchOnMount and refetchOnReconnect behaviors
