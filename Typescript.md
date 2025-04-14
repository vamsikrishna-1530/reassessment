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
