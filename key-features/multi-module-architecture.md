---
order: 90
---

# Multi-module architecture

## Monolithic beginnings
When we started developing Agni, the project was relatively simple, with a few key features, like patient registration and list view. Everything resided under a single module—`app/`. This single-module structure had all UI components, networking code, view models, repositories, and utility classes bundled together. While this made initial development fast and straightforward, it soon began to show cracks as new features were added.

### Challenges faced
As Agni matured, we ran into several pain points:

* **Longer build times**: With everything in one module, even a small change triggered a full build of the entire project.
* **Poor separation of concerns**: Features and layers (UI, domain, data) were interdependent, leading to tightly coupled code.
* **Merge conflicts**: Multiple developers working on different features in the same module led to frequent conflicts.
* **Difficult testing and debugging**: Isolating bugs became harder, especially when multiple features depended on the same shared codebase.
* **Codebase bloat**: As features like patient registration, multiple assessments, and authentication were added, navigating the code became cumbersome.

## Why We Migrated to Multi-Module Architecture
We needed a way to:

* Speed up our build times.
* Clearly separate different features for better maintainability.
* Enable parallel development by multiple team members.
* Make code reusable and testable in isolation.

The multi-module architecture addressed all of these issues and offered even more advantages. It was the logical next step for Agni's growing complexity.

### New project structure
In a multi-module architecture, instead of having a single codebase, we break the app down into independent, self-contained modules. Each module can represent a feature, a layer (like data or domain), or shared utilities.

Here is an overview of our refactored project structure:
```
AGNI/
├── app/ # Main entry point
├── core/
| ├── theme/ # colors and typography
| ├── model/ # data classes
| ├── data/ # repositories
| ├── database/ # daos, entities
│ ├── ui/ # Common UI components
│ ├── network/ # Retrofit, interceptors, API clients
│ └── utils/ # Shared utilities
├── features
│ ├── auth/ # authentication module
│ ├── patient/ # patient module
│ ├── household/ # household member module
| ├── many other features
```

### Benefits we gained
1. **Faster Build Times**: Gradle builds only the changed modules, reducing overall build time.
2. **Better Code Separation**: Features and layers (UI, domain, data) are cleanly separated and encapsulated.
3. **Scalable Team Collaboration**: Multiple developers can safely work on different modules simultaneously.
5. **Reusability**: Shared components live in core modules and are reused across features.

### Migration strategy
We migrated feature-by-feature using a phased approach:

1. **Extracted least dependent features** (e.g., authentication)
2. **Created a `core/` layer** for shared code (network, UI, utils)
3. **Introduced Hilt** for dependency injection across modules
4. **Used interface-based abstractions** to decouple dependencies
5. **Ensured no circular dependencies** between modules