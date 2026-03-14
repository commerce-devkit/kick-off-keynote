---
theme: apple-basic
title: Modern Systems Architecture
info: |
  Clean keynote-style presentation
background: https://source.unsplash.com/1920x1080/?dark,gradient
highlighter: shiki
class: text-center
colorSchema: dark
drawings:
  persist: false
transition: fade
mdc: true
---

# Building Modern Systems

### Simplicity scales better than complexity

<div class="opacity-60 text-sm mt-10">
Johannes Huber · Conference 2026
</div>

---

# The Problem

### Systems become harder to evolve over time

---

## Why This Happens

- tightly coupled services
- slow deployments
- limited observability

---

# The Shift

### Automation + small services

---

```ts
async function deploy(service) {
  await build(service);
  await test(service);
  await release(service);
}
```

<style>
:root {
  --slidev-theme-primary: #6366f1;
}

.slidev-layout {
  background: #0f172a;
}
</style>
