## **4. Lifecycle Methods vs. Hooks – One-to-One Comparison**  

| Class Lifecycle Method | Equivalent Hook |
|------------------------|----------------|
| `constructor()` | `useState()` |
| `componentDidMount()` | `useEffect(() => {}, [])` |
| `componentDidUpdate()` | `useEffect(() => {...}, [dependencies])` |
| `componentWillUnmount()` | `useEffect(() => { return cleanup }, [])` |
| `shouldComponentUpdate()` | `React.memo()`, `useMemo()`, `useCallback()` |
| `getDerivedStateFromProps()` | `useEffect()` (with dependency tracking) |
| `getSnapshotBeforeUpdate()` | `useRef()` |
| `componentWillReceiveProps()` | `useEffect()` (with props as dependencies) |
