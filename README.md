# Selector not updating when slice data is udpdated

### Bug Description

1. There is a `Counter` RTK Query Service which has a `getCounter` endpoint that gets the `counter` value from an API (Next.js API for this example repo).

2. There is a slice `counterSlice` that has an async thunk that calls the above query using `counterAPI.endpoints.getCounter.initiate()`

3. `extraReducers` - `builder.addMatcher` are used to update `loading`, `error` and `fulfilled` states in the slice.

4. `AnotherComponent` calls this async thunk using `store.dispatch(fetchCounterDataThunk())`.

5. There is a selector which gets the counter value from the slice defined in `counterSlice` file and used on the `index` page like so `const data = useSelector(getCounter)`.

6. The data updates in the store that can seen via the Redux DevTools, but the selector in the index page does not receive the updated data.
