# flapjack 🥞

https://hyperwave.codes/

flapjack is a server-side framework for building web applications.

- fast: Bun and Hono for best-in-class performance
- lightweight: ~20kb payload. Demo loads in a couple seconds even while throttled to 2G.
- productive: use the best tools for the job: Tailwind, HTMX, and TypeScript
- portable: compile a binary to deploy anywhere

### Setup

`bun install && bun run src/db.ts && bun dev`

Visit port 3000 and edit `server.tsx`

---

### Demo

https://github.com/tireymorris/hyperwave/assets/3528600/ade1b785-c1b9-4bf8-be2b-3b07f2ae17f7

---

### Example

This is the endpoint serving our initial landing page:

```typescript
app.get("/", ({ html }) =>
  html(
    <Layout title="flapjack 🥞">
      <section class="flex flex-col gap-8">
        <div>
          <button
            class="bg-blue-100 p-4 text-sm font-bold rounded-md shadow-sm"
            hx-get="/instructions"
            hx-target="closest div"
          >
            fetch instructions from <code>/instructions</code>
          </button>
        </div>
      </section>
    </Layout>,
  ),
);
```

- The API serves a full HTML document to the client, which includes Tailwind classes and HTMX attributes
- The response is wrapped in a `<Layout />` tag, a server-rendered functional component, which takes a `title` prop
- The button, when clicked, will issue a `GET` request to `/instructions` and replace the content of its parent div with the response.

---

### Deployment

Build an executable for your current architecture with `bun run build`

`PORT` environment variable is available if needed (default 3000)

Note: deploy `public/` with the executable, it contains the generated UnoCSS build.

---

### Components

- [Bun](https://bun.sh/) provides the bundler, runtime, test runner, and package manager.
- [SQLite](https://bun.sh/docs/api/sqlite) is production-ready and built into Bun.
- [Hono](https://hono.dev) is a robust web framework with great DX and performance
- [UnoCSS](https://unocss.dev/integrations/cli) is Tailwind-compatible and generates only the styles used in application code.
- [HTMX](https://htmx.org/reference/) gives 99% of the client-side interactivity most apps need.

---
