Great! Here are some common and strong **TypeScript interview questions** with well-structured answers from a **candidate’s perspective**:

---

### ✅ **1. What is TypeScript and why do you prefer it over JavaScript?**

> TypeScript is a statically typed superset of JavaScript that compiles to plain JS. I prefer it because it adds type safety, autocompletion, and better tooling support. In larger codebases, especially with teams, it prevents a lot of runtime errors by catching issues during development. It also improves refactoring, which I find extremely useful when maintaining or scaling React/Next.js projects.

---

### ✅ **2. What is the difference between `any` and `unknown` in TypeScript?**

> Both `any` and `unknown` are top types, meaning they can hold any value. But `unknown` is safer.
>
> When you use `any`, TypeScript disables type checking — so it could lead to runtime errors. But with `unknown`, you’re forced to narrow the type before using it. For example:
>
> ```ts
> function handle(value: unknown) {
>   if (typeof value === "string") {
>     console.log(value.toUpperCase());
>   }
> }
> ```
> This protects the code from unexpected operations on unknown data, which I find useful when working with dynamic APIs or third-party inputs.

---

### ✅ **3. What's the difference between `interface` and `type`? When do you use each?**

> Both can be used to define object shapes. But:
>
> - `interface` is extendable via `extends` and is more suited for class-based or component props structures.
> - `type` is more flexible — you can use unions, intersections, mapped types, etc.
>
> In my projects:
> - I use `interface` for React props and when building reusable components.
> - I use `type` when I need advanced types like unions or when modeling API responses.

---

### ✅ **4. What are Generics in TypeScript? How have you used them?**

> Generics let us write reusable and flexible components or functions while maintaining type safety. I use them often when building utility functions or custom hooks.
>
> For example, I created a `useFetch<T>()` hook where `T` can be the shape of the data being fetched:
>
> ```ts
> function useFetch<T>(url: string): Promise<T> { ... }
> const data = await useFetch<User>('api/user');
> ```
>
> This way, the return type is always strongly typed based on the generic passed in.

---

### ✅ **5. Can you explain some commonly used Utility Types in TypeScript?**

> Yes, I regularly use built-in utility types like:
>
> - `Partial<T>` – makes all properties optional. Useful for forms.
> - `Pick<T, K>` – picks only specific keys.
> - `Omit<T, K>` – removes certain keys.
> - `Record<K, T>` – great for mapping keys to types.
>
> Example:
> ```ts
> type User = { id: number; name: string; email: string };
> type UserPreview = Pick<User, 'id' | 'name'>;
> ```

---

### ✅ **6. What are Union and Intersection types?**

> - **Union types (`|`)** allow values to be one of several types:
>   ```ts
>   type Status = 'loading' | 'success' | 'error';
>   ```
>
> - **Intersection types (`&`)** combine multiple types:
>   ```ts
>   type Address = { city: string };
>   type Contact = { phone: string };
>   type User = Address & Contact;
>   ```
>
> I use unions for status enums, and intersections to merge props or API models.

---

### ✅ **7. How does Type Inference work in TypeScript?**

> TypeScript can infer types based on values or return statements. For instance:
>
> ```ts
> const name = "John"; // inferred as string
> ```
>
> I rely on type inference to reduce verbosity but still annotate complex types explicitly—especially when sharing APIs across teams to avoid misinterpretation.

---

### ✅ **8. What are Discriminated Unions and how are they useful?**

> Discriminated unions combine union types with a common discriminant property. I use them to model complex states or API responses:
>
> ```ts
> type Success = { status: "success"; data: User };
> type Error = { status: "error"; message: string };
> type Result = Success | Error;
> ```
>
> Then I use type narrowing via `switch` or `if` to safely access the correct data:
> ```ts
> if (res.status === "success") {
>   console.log(res.data);
> }
> ```

# **Pros & Cons**

Certainly! Here's a well-balanced, **interview-style answer** to:

**"What are the pros and cons of using TypeScript?"**

---

**Answer (as a candidate):**

I’ve worked extensively with TypeScript in frontend projects, and I find it offers many advantages, especially for larger, collaborative codebases. Here's how I look at its pros and cons:

---

### ✅ **Pros of TypeScript**

1. **Static Typing:**
   TypeScript catches type-related bugs at compile time, which improves reliability and reduces runtime errors.

2. **Improved Developer Experience:**
   With strong IntelliSense support in IDEs like VSCode, I get autocomplete, type hints, and inline documentation, which speeds up development and reduces cognitive load.

3. **Better Code Maintenance:**
   Explicit types make the codebase easier to read, refactor, and maintain—especially in large teams or projects with frequent onboarding.

4. **Enhanced Collaboration:**
   Types serve as documentation. When working in teams, TypeScript makes API contracts and function expectations much clearer.

5. **Integration with Modern Tooling:**
   TypeScript integrates seamlessly with modern frameworks like Next.js, React, and Node.js. It also works well with tools like ESLint, Prettier, and testing libraries.

6. **Early Error Detection:**
   It helps identify edge cases or missing fields that JavaScript might overlook, especially when dealing with API responses or complex objects.

---

### ⚠️ **Cons of TypeScript**

1. **Initial Learning Curve:**
   Developers coming from plain JavaScript need time to learn TypeScript concepts like generics, union types, and advanced type guards.

2. **Increased Complexity:**
   For small projects or MVPs, TypeScript might feel like overkill, and setting up types can slow down rapid prototyping.

3. **Build Overhead:**
   TypeScript requires a compilation step, which slightly increases build time and complexity in CI/CD pipelines.

4. **Verbosity:**
   Some developers find it verbose, especially when defining complex types or working with third-party libraries that have poor or missing type definitions.

5. **Type Definition Maintenance:**
   When external APIs change or when libraries lack up-to-date type support, we may need to write or maintain our own `*.d.ts` files, which can be tedious.

---

### Summary:
So overall, I see TypeScript as a strong asset for long-term, scalable projects. While it introduces some upfront complexity, the benefits in terms of stability, tooling, and collaboration typically outweigh the drawbacks.

---

Let me know if you’d like me to tailor this to a specific use case, like React or backend development!
