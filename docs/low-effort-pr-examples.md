# Low-Effort PR Examples & Quality Expectations

This document outlines common examples of "low-effort" pull requests in the aegis-dashboard repository. PRs exhibiting these anti-patterns will typically fail maintainer evaluation and be closed. 

To ensure your contributions are valuable, thoroughly reviewed, and merged, study the contrast between unacceptable submissions and their expected alternatives.

---

## 1. Superficial or Cosmetic Changes

**The Anti-Pattern:** Submitting a PR that solely fixes a minor typo in a comment, reorders imports without a structural reason, or tweaks markdown formatting, while claiming a feature or substantial bounty.

**Unacceptable Example:**
```tsx
// Changes:
// - // Check if the wallet is connected
// + // Checks if the wallet is connected
```

**Expected Alternative:** 
If you notice typos, batch them together across the entire codebase or include them as a secondary commit in a PR that delivers meaningful, tested UI changes.

---

## 2. Under-Tested Logic (Missing Coverage)

**The Anti-Pattern:** Adding or modifying core components, custom hooks, or state transitions in the React frontend without providing corresponding unit tests or visual regression fixtures.

**Unacceptable Example:**
```tsx
// Adding a new compliance check hook without testing it
export function useComplianceCheck(address: string) {
    // Implementation added...
    // But no .test.ts file created!
}
```

**Expected Alternative:**
Every new hook or major component must include robust Vitest tests covering both happy and failure paths.

---

## 3. Unsafe State Mutations or Suppressed Errors

**The Anti-Pattern:** Using `@ts-ignore`, `any`, or suppressing ESLint rules to bypass type safety, or swallowing errors silently in catch blocks.

**Unacceptable Example:**
```tsx
catch (err) {
  // @ts-ignore
  console.log(err); // Swallows the error silently, breaking the UI state
}
```

**Expected Alternative:**
```tsx
catch (err) {
  const wrappedErr = err instanceof Error ? err : new Error(String(err));
  setError(wrappedErr.message); // Properly surfaces the error to the user
}
```

---

## 4. Failing CI / Ignored Checks

**The Anti-Pattern:** Opening a PR, noticing the GitHub Actions CI pipeline fails, and requesting a maintainer review anyway.

**Expected Alternative:**
Before requesting review, ensure your local build and tests pass. If CI fails after pushing, inspect the logs, fix the formatting, linter warnings, or broken tests, and push the corrections.

---

## Summary of a "High-Effort" PR

1. **Meaningful:** Solves a documented issue.
2. **Tested:** Includes robust positive and negative Vitest tests.
3. **Safe:** Uses strict TypeScript typing.
4. **Green CI:** Passes all local and remote checks.
5. **Descriptive:** Explains what changed and why.
