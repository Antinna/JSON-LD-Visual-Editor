# JSON-LD Visual Editor 🎨

> **A Visual Foundation for an Offline-First, Schema.org-Native Platform**

Build structured data visually. Work offline after loading Schema.org definitions.

---

## 🌟 Key Features

### Key capabilities and design goals

* **Visual Editing:** Create and modify structured data without manually writing every JSON object.
* **Schema-Aware Modeling:** Work with Schema.org types and properties in a structured editing environment.
* **Type & Subtype Selection:** Choose suitable entity types and precise, specific subtypes.
* **Nested Objects:** Represent complex relationships and values without losing the underlying structure.
* **Multiple Values:** Easily handle properties containing arrays or multiple items.
* **JSON-LD Keywords:** Native support for constructs such as `@context`, `@type`, `@id`, `@value`, and `@language`.
* **Language-Tagged Values:** Represent multilingual text seamlessly using JSON-LD value objects.
* **Linked Entities:** Reuse entity identifiers and references instead of duplicating data across records.
* **Local Persistence:** Powered by **Drift** for robust local storage in the standalone implementation.
* **JSON-LD Interoperability:** Work with a format standard designed specifically for web-wide structured data.

---

## 🚀 Explore the Prototype

| Resource | Link |
| :--- | :--- |
| **Demo** | 🌐 [Live Web Editor](https://antinna.github.io/JSON-LD-Visual-Editor/) |
| **Code** | 📁 [GitHub Repository](https://github.com/Antinna/JSON-LD-Visual-Editor) |

> [!IMPORTANT]
> ### Preview Scope, Serverpod Usage related Disclaimer & Proprietary Code Notice
>
> This repository and its live demo are provided as a limited preview (extracted using some Agentic AI from actual code) of the broader project concept. **The current live preview (`no-pod`) does not use Serverpod as its backend, and our actual proprietary production implementation has not been published or hosted publicly. But You can Guess it just Like `Google's Blogger™` but with JSON-LD only Posts and Blog**
>
> The code shared here is a small, selectively extracted sample of usable components and implementation ideas intended to demonstrate the concept. It is not the complete source code of the original platform, nor should it be treated as a representation of the full production architecture (I will share my full MVP below).
>
> I understand that this limited preview may not be sufficient to demonstrate the complete technical implementation or meet every evaluation criterion. If this affects my participation or eligibility, I respect the decision. However, I intend to share an MVP demonstration showing how the actual implementation works so the broader architecture and its capabilities can be evaluated accurately.
>
> **Please evaluate the current repository as a conceptual and technical preview, not as the complete proprietary product.** The distinction between the publicly shared sample and the actual implementation is intentional. The goal is to share the idea, demonstrate selected implementations, and help developers explore what can be built on top of it.

---

# 💡 Architecture & MVP

> *The full idea is discussed here and can be used freely.*

### The Shift to the Agentic Era
We are entering the **Agentic Era**. With the rapid rise of AI agents, frameworks like Genkit, and declarative UI paradigms like A2UI, the foundation of how apps interact with data is changing forever.

However, an undeniable truth remains: **End-users do not care what programming language or backend framework powers your application.** They only care about two things:
1. An uncompromised User Experience
2. Instant, reliable problem-solving

To deliver that, our applications must evolve. They shouldn't just display static pages; they need to speak a **universal, structured data language** that both human UIs and autonomous AI agents can fluently understand (`A2UI`).

---

### Rethinking Content Nodes
For years, I was inspired by the sheer flexibility of platforms like **Google’s Blogger™**. The idea of treating posts as dynamic content nodes was brilliant. However, modern enterprise needs hit hard walls on traditional blogging platforms—you can't deploy native custom Service Workers, configure edge `.well-known` discovery files, and many more (the con's of Blogger™).

While proxying through edge networks like Cloudflare solves some routing bottlenecks, I wanted a **truly universal, local-first solution**. That led to a fundamental question:

> *Why are we still treating application data as unstructured text or rigid, proprietary database schemas?*

Instead of traditional blog posts, what if every single post, record, or entity was a universally typed, machine-readable **Schema.org Linked Data (JSON-LD)** object?

> **Note:** In our proprietary implementation, we made this possible by using **Typed Schemas** to store all blogs and posts.

---

### Leveraging Schema.org at Scale
Schema.org defines nearly 1,000 standardized types covering virtually every real-world domain—from e-commerce and local services to events and social graphs.

By leveraging Dart tools like `schemantic` along with `json_serializable`, we brought these global web schemas directly into type-safe mobile and web code. Every "blog post" in our architecture is actually a strongly-typed JSON-LD object.

#### The Power of `@base` and `@id` Interlinking
To prevent data bloat and duplicate payloads, we leverage Schema’s `@base` and `@id` properties:

* **`@base`**: Automatically scopes entities to your domain or dynamic post route (`blogId/blogPostId`). *(Assigned automatically in our platform for blog posts, or `blogId` for standalone blogs).*
* **`@id`**: Acts as a global pointer. Instead of repeating vendor details, product specs, or author profiles across hundreds of records, you simply reference the entity's `@id` URL path or something like `blogId/postId` or if just blog homepage then `blogId`.

Need to modify a linked entity for a specific post? You can reference its `@id` and apply localized overrides on the fly without breaking the global reference—creating a lightweight, modular, and highly scalable **Knowledge Graph**.

---

### Solving AI Hallucinations in JSON-LD
While AI models are great at generating code, developers quickly realize that AI frequently hallucinates deeply nested JSON-LD structures and invalid property types.

To solve this, I built the **JSON-LD Visual Editor**—a dedicated, type-safe developer tool that lets anyone visually build, inspect, and export syntactically perfect Schema.org Linked Data without memorizing specs or guessing fields. *(Designed using Agentic tools; available freely in the repository links given above `no-pod`).*

It bridges the gap for developers, content creators, and AI pipelines alike.

---

### Implementations

To prove this data-driven architecture under real-world conditions, I am making two open implementations available to the community:

1. **The Local-First Utility (`no-pod`):** Built for standalone tools and offline-first client applications. It uses local SQLite storage via `drift` so developers can create, query, and store interlinked schemas entirely on-device without running a server.
2. **The Cloud-Synced Ecosystem (`pod`):** Built using `serverpod_offline_sync` for cloud-synced workflows (just an extract not an actual code,), 
> **Please Note:** Neither the server-side nor the complete client-side code is included in this preview. A similar implementation can be developed using Agentic AI to generate a complete project tailored to the user's specific use case. But I am here to showcase this `JSON-LD Visual Editor` and what i made using that, `MVP`.

