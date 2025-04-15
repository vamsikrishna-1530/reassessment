Got it! Here's a refined **interview-style answer**, as if you're the candidate responding in a **clear, concise, and confident** manner during a live interview:

---

**Q: How do you handle accessibility (a11y) issues in a Next.js project according to WCAG standards?**

**A (Candidate):**  
In my projects, accessibility is something I address from the beginning — not just at the end. In a Next.js project, I follow WCAG guidelines to make sure the app is usable for everyone, including users with disabilities.

The first thing I focus on is **semantic HTML**. I use elements like `<button>`, `<nav>`, and `<label>` properly so that screen readers can interpret the UI structure clearly.

Next, I ensure all **interactive components** — like modals, dropdowns, or custom toggles — are fully accessible using the keyboard. That includes setting proper `tabindex`, handling key events, and managing focus traps.

I also make use of **ARIA attributes** like `aria-label`, `aria-expanded`, and `aria-live` where needed — but I prefer to rely on semantic HTML first, and only use ARIA when necessary.

For **visual accessibility**, I follow WCAG contrast ratio requirements — typically 4.5:1 for text. Since we use Tailwind in our stack, I often customize the color palette to ensure all design tokens meet that contrast.

Images always have descriptive `alt` text, and for purely decorative icons, I use `aria-hidden="true"` or empty alt text.

Finally, I integrate automated tools like **Lighthouse**, **axe-core**, and **eslint-plugin-jsx-a11y** during development. But I also do **manual testing** using screen readers like VoiceOver, and keyboard-only navigation, to catch real-world accessibility issues.

Whenever I find accessibility bugs — whether it's missing labels, improper focus handling, or poor contrast — I treat them with the same priority as functional bugs, especially because we often work with US clients where a11y compliance is a legal and UX standard.

So overall, I treat accessibility as a first-class concern in the dev process — and it’s something I’m actively improving in every sprint.

---

Let me know if you want a **Tailwind-specific example** or a scenario like “how did you fix a real a11y bug on a project”!


Perfect! Here's how you can **answer as a candidate** when asked to describe a **real-world scenario where you fixed an accessibility (a11y) issue** — tailored to your stack (Next.js + TypeScript + Tailwind) and a US client-facing project:

---

### 🧑‍💻 **Q: Can you share an example where you fixed an accessibility issue in a real project?**

**A (Candidate):**  
Yes, definitely. In one of my previous projects — a customer-facing dashboard for a US-based client — we got feedback from a screen reader user that the **custom dropdown components weren’t accessible**. They couldn’t tell when the dropdown opened, or navigate through the options using the keyboard.

After inspecting the code, I realized we had used a plain `<div>` with `onClick` to toggle the menu and absolutely no ARIA attributes or keyboard support.

To fix it, I refactored the component by:

1. **Changing the trigger element** from `<div>` to a real `<button>`, and added:
   ```tsx
   aria-haspopup="listbox"
   aria-expanded={isOpen}
   aria-controls="dropdown-menu"
   ```

2. **Adding keyboard navigation**:
   I handled `Enter`, `ArrowDown`, `ArrowUp`, and `Escape` keys so users could open, navigate, and close the menu entirely by keyboard.

3. **Ensuring focus management**:
   When the dropdown opened, I focused the first item using a `ref`, and when it closed, I returned focus to the toggle button.

4. **Improving screen reader support**:
   I wrapped the options list with `role="listbox"` and each option with `role="option"` and `aria-selected`.

5. **Styling the focus**:
   With Tailwind, I used `focus:outline-none` and `focus-visible:ring-2 ring-blue-500` to clearly show which element is in focus — which helps both keyboard and low-vision users.

Here’s a snippet from that fix:

```tsx
<button
  onClick={toggleDropdown}
  aria-haspopup="listbox"
  aria-expanded={isOpen}
  aria-controls="dropdown-menu"
  className="focus-visible:ring-2 ring-blue-500"
>
  Select Option
</button>
<ul
  id="dropdown-menu"
  role="listbox"
  className={`absolute mt-2 ${isOpen ? 'block' : 'hidden'}`}
>
  {options.map((opt, idx) => (
    <li
      key={opt.value}
      role="option"
      aria-selected={selected === opt.value}
      tabIndex={0}
      onKeyDown={e => handleOptionKeyDown(e, idx)}
      onClick={() => selectOption(opt)}
      className="p-2 hover:bg-gray-100 focus:bg-gray-200"
    >
      {opt.label}
    </li>
  ))}
</ul>
```

After the fix, we re-tested with VoiceOver and NVDA, and the dropdown was fully navigable and screen-reader friendly. That update also helped us pass an internal WCAG 2.1 audit before demoing to the client.

---

Would you like a breakdown of a similar fix for **form inputs, modals**, or **error messages** too?
