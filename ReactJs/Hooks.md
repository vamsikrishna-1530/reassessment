# **React Hooks (Replacing Lifecycle Methods & More)**  
React Hooks allow functional components to **use state and lifecycle-like behavior** without needing a class.  

### **Commonly Used Hooks in React:**  
| Hook | Purpose | Equivalent Class Lifecycle Method |
|------|---------|---------------------------------|
| `useState` | Manages local state | `this.state`, `setState()` |
| `useEffect` | Handles side effects | `componentDidMount`, `componentDidUpdate`, `componentWillUnmount` |
| `useContext` | Accesses context values | `Context.Consumer` |
| `useRef` | Manipulates DOM & stores values persistently | `React.createRef()` |
| `useMemo` | Optimizes performance by memoizing values | N/A (manual optimization in classes) |
| `useCallback` | Prevents unnecessary function recreation | N/A (method bindings in classes) |
| `useReducer` | Manages complex state logic | Alternative to `useState`, similar to Redux |
| `useLayoutEffect` | Runs synchronously after DOM updates | Similar to `componentDidMount`, `componentDidUpdate`, but runs earlier |
| `useImperativeHandle` | Controls how refs expose functionality | Used with `forwardRef()` |
| `useTransition` | Improves UI responsiveness for concurrent rendering | N/A |
| `useDeferredValue` | Defers a value for better UI performance | N/A |

## **Core Hooks – In-Depth Explanation**  

### **🔹 `useState` – Managing Local Component State**  
- Used to add **state** in functional components.  
- Unlike `this.state` in class components, `useState` returns an **array with the state variable and setter function**.  
- Triggers a **re-render** when the state updates.  
- Best for **simple state updates** (use `useReducer` for complex state logic).  

💡 **When to Use?**  
- Tracking form inputs, toggle switches, counters, etc.  

---

### **🔹 `useEffect` – Handling Side Effects**  
- Replaces `componentDidMount`, `componentDidUpdate`, and `componentWillUnmount`.  
- Runs **after** every render **by default** but can be controlled with dependencies.  
- Can return a cleanup function (like `componentWillUnmount`).  

💡 **When to Use?**  
- Fetching data from APIs.  
- Subscribing to WebSocket events.  
- Setting timers and intervals.  
- Listening for window resize events.  

⚠️ **Common Mistake:**  
- If used incorrectly, it can lead to **infinite re-renders**.  

---

### **🔹 `useContext` – Global State Management Without Prop Drilling**  
- Allows access to **React Context values** without `Context.Consumer`.  
- Reduces **prop drilling**, making code cleaner.  

💡 **When to Use?**  
- Managing **theme**, **authentication**, or **language preferences** globally.  

---

### **🔹 `useRef` – Persistent Value Storage & DOM Manipulation**  
- Stores a **mutable value** that persists across renders **without triggering re-renders**.  
- Can be used to **reference DOM elements** directly (like `document.querySelector`).  

💡 **When to Use?**  
- Accessing form inputs without re-rendering.  
- Storing previous state values.  
- Handling focus, animations, and scroll positions.  

---

### **🔹 `useMemo` – Performance Optimization by Memoizing Values**  
- Caches expensive calculations so they don’t recompute unnecessarily.  
- Only recalculates when dependencies change.  

💡 **When to Use?**  
- Optimizing **slow computations**.  
- Preventing unnecessary re-renders in **large lists**.  

---

### **🔹 `useCallback` – Preventing Unnecessary Function Re-Creation**  
- Returns **memoized functions** that don’t get recreated on re-renders.  
- Helps optimize performance in components receiving functions as **props**.  

💡 **When to Use?**  
- Passing event handlers to child components.  
- Preventing child components from **unnecessary re-renders**.  

---

### **🔹 `useReducer` – Managing Complex State Logic**  
- Alternative to `useState`, **similar to Redux**, but local to a component.  
- Helps **manage state transitions** in a structured way.  

💡 **When to Use?**  
- Handling **complex state** with multiple sub-values (e.g., form state).  
- Managing **state with multiple dependent updates**.  

---

### **🔹 `useLayoutEffect` – Handling Synchronous Effects (Before Paint)**  
- Works like `useEffect`, but fires **synchronously after DOM mutations**.  
- Runs **before** the browser paints the screen.  

💡 **When to Use?**  
- Measuring **DOM elements** (e.g., getting dimensions).  
- Synchronizing **animations**.  

---

### **🔹 `useImperativeHandle` – Customizing `ref` Behavior**  
- Used with `forwardRef()` to **control how parent components interact with child refs**.  
- Lets components **expose specific methods** instead of the whole DOM element.  

💡 **When to Use?**  
- Creating **custom modal dialogs, focus management, or exposing methods** from a component.  

---

### **🔹 `useTransition` – Making UI Responsive During Heavy Updates**  
- Allows React to prioritize **urgent updates** (e.g., typing) over **heavy computations**.  
- Improves **concurrent rendering performance**.  

💡 **When to Use?**  
- Keeping **UI responsive** when filtering large lists or loading data.  

---

### **🔹 `useDeferredValue` – Deferring Value Updates to Improve Performance**  
- Delays updating non-urgent values, allowing more important updates to render first.  
- Helps prevent UI flickering.  

💡 **When to Use?**  
- **Deferring input values** while users type in a search box.  

---

