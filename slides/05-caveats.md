## Caveats?

## Issue: Prop Drilling

Fix: A state boundary. A component that does the fetching deeper within a tree but still passes data to pure components. eg: React Context

## Issue: Shallow checking

Fix: Be aware of creating new references that cause rerenders. (new arrays, anonymous functions)

Could be a premature optimization to care to much about this.

---
