## **Custom Hooks in React**  

### **1️⃣ What is a Custom Hook?**  
A **Custom Hook** is a reusable JavaScript function in React that encapsulates logic inside a hook-like function. It allows you to **reuse stateful logic** across multiple components **without repeating code**.

---

### **2️⃣ Why Create a Custom Hook?**  
✅ **Reusability** → Avoid duplicating logic in multiple components.  
✅ **Separation of Concerns** → Keeps components clean by moving logic elsewhere.  
✅ **Code Maintainability** → Easier to manage and debug.  
✅ **Encapsulation** → Abstracts complex logic, improving readability.  

---

### **3️⃣ When to Create a Custom Hook?**  
You should create a **Custom Hook** when:  
🔹 Multiple components **share the same logic** (e.g., fetching data, form handling).  
🔹 You need to **simplify complex logic** in a component.  
🔹 You want to **encapsulate side effects** (e.g., API calls, event listeners).  

---

### **4️⃣ How to Create a Custom Hook?**  
🔹 A **Custom Hook is just a function** that starts with `use` (e.g., `useFetch`, `useLocalStorage`).  
🔹 It can **use other hooks** (`useState`, `useEffect`, `useRef`, etc.).  
🔹 It should **return values** (state, functions, or computed values) for the component to use.  

---

### **5️⃣ Example Use Cases for Custom Hooks**  

| Use Case | Example Custom Hook | Purpose |
|----------|---------------------|---------|
| Fetching API data | `useFetch()` | Handles API calls and loading states. |
| Local Storage | `useLocalStorage()` | Saves and retrieves values from `localStorage`. |
| Form Handling | `useForm()` | Manages form state and validation. |
| Window Resize | `useWindowSize()` | Tracks window size dynamically. |
| Dark Mode | `useDarkMode()` | Manages dark/light mode toggling. |

---

### **6️⃣ Best Practices for Custom Hooks**  
✅ **Use the `use` prefix** → Helps React identify it as a hook.  
✅ **Encapsulate only related logic** → Keep it focused on a single concern.  
✅ **Return necessary values/functions** → Components should use them easily.  
✅ **Follow React’s Hook Rules** → Don’t call hooks inside loops, conditions, or nested functions.  

Would you like an **example of a real-world Custom Hook** and how to use it? 🚀
