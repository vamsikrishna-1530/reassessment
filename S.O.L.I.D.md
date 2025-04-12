
# **“Can you explain the SOLID principles and how you’ve applied them in your frontend projects?”**


> Absolutely. The **SOLID principles** are a set of five object-oriented design principles that help write maintainable, scalable, and testable code. Even in frontend projects—especially with **TypeScript** and component-based architectures like **React/Next.js**—they’re very applicable. Let me briefly go through them and share where I've applied them:
>
> ---
> #### 🔸 **S – Single Responsibility Principle**
> > A class or module should have only one reason to change.
>
> In my insurance form project, I split form components by responsibility. For example, I had a `FormInput.tsx` component that only handled rendering a field, and a separate `useFormValidation` hook for logic. This kept rendering and business logic separate and easier to test or modify.
>
> ---
> #### 🔸 **O – Open/Closed Principle**
> > Components should be open for extension but closed for modification.
>
> I often use this when creating reusable components. For instance, instead of modifying the `Button` component every time I needed a new style, I passed a `variant` prop and extended styles using Tailwind. This way, the component is extensible without touching its core.
>
> ```tsx
> <Button variant="primary" /> or <Button variant="outline" />
> ```
>
> ---
> #### 🔸 **L – Liskov Substitution Principle**
> > Subtypes should be substitutable for their base types.
>
> In TypeScript, I follow this when working with interfaces or types. If I create a base `FormFieldProps`, I ensure that components accepting those props also work when I extend them, like `TextFieldProps`, without breaking behavior.
>
> ```ts
> interface FormFieldProps { label: string; }
> interface TextFieldProps extends FormFieldProps { maxLength?: number; }
> ```
>
> ---
> #### 🔸 **I – Interface Segregation Principle**
> > Don't force components to depend on things they don’t use.
>
> I avoid bloated prop interfaces. If a component doesn’t need certain props, I break down interfaces into smaller, focused ones. This helps reduce coupling and makes components easier to reason about.
>
> ---
> #### 🔸 **D – Dependency Inversion Principle**
> > Depend on abstractions, not on concretions.
>
> In frontend, I apply this by passing dependencies like API functions or configuration into components via props or context, instead of hardcoding them. For instance, I passed an abstract `submitForm` function into a `FormContainer`, so I could mock it easily during tests.
>
> ```tsx
> <FormContainer onSubmit={handleSubmit} />
> ```
>
> ---
>
> So overall, SOLID principles help me write cleaner, testable, and more maintainable frontend code—even in a component-driven framework like React or Next.js.
