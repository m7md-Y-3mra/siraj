# Siraj Project Context

This project is a modern web application built with Next.js 16, React 19, Tailwind CSS v4, and Supabase.

## ⚠️ Critical Warning (Next.js 16)

This project uses **Next.js 16**. According to `AGENTS.md`:
> This version has breaking changes — APIs, conventions, and file structure may all differ from your training data. Read the relevant guide in `node_modules/next/dist/docs/` before writing any code. Heed deprecation notices.

Always verify Next.js APIs against the local documentation or by inspecting types, as standard knowledge of Next.js 13/14/15 may be outdated.

## Tech Stack

- **Framework:** Next.js 16.2.6 (App Router)
- **Library:** React 19.2.4
- **Styling:** Tailwind CSS v4 (using OKLCH colors and `@theme` syntax in `app/globals.css`)
- **UI Components:** shadcn/ui (configured in `components.json`)
- **Database & Auth:** Supabase (using `@supabase/ssr`)
- **Fonts:** Geist Sans & Geist Mono

## Project Structure

- `app/`: Next.js App Router directory.
    - `layout.tsx`: Root layout with font and style initialization.
    - `page.tsx`: Main entry point (currently fetches `todos` from Supabase).
    - `globals.css`: Tailwind v4 configuration and global styles.
- `components/ui/`: shadcn/ui components.
- `lib/`: Utility functions (e.g., `cn` in `utils.ts`).
- `utils/supabase/`: Supabase client initialization for different environments:
    - `server.ts`: For Server Components and Server Actions.
    - `client.ts`: For Client Components.
    - `middleware.ts`: For Next.js Middleware.
- `.agents/`: Local agent configurations and skills (includes a `supabase` skill).

## Building and Running

- **Development:** `npm run dev`
- **Build:** `npm run build`
- **Start:** `npm run start`
- **Lint:** `npm run lint`

## Development Conventions

- **Supabase:** Always use the appropriate client from `@/utils/supabase/` based on the context (Server vs. Client).
- **Styling:** Use Tailwind CSS v4 utility classes. Note the use of OKLCH colors in `globals.css`.
- **TypeScript:** The project is strictly typed. Ensure new components and functions are properly typed.
- **Components:** Prefer functional components with hooks. Use shadcn/ui for consistent UI elements.

## Key Files to Reference

- `package.json`: Dependency versions and scripts.
- `app/globals.css`: Tailwind v4 theme and color variables.
- `utils/supabase/server.ts`: Supabase server-side client setup.
- `AGENTS.md`: Important notice about Next.js 16 changes.

Project Identity: A library for Muslim students built with Next.js and Supabase.
Core Feature (The Container): A Many-to-Many relationship between resources and folders. A single book or playlist can exist in multiple folders (e.g., "General" and "Ibn Qayyim").
Schema Details:

resources: Holds both BOOKS (files) and PLAYLISTS (links) via a unified url column.

folders: Containers for grouping resources.

folder_resources: Junction table connecting the two.

summaries: Linked to Playlists for extra study notes.
Auth: Admin-only access to /dashboard verified via an admins table in public schema./

<!-- SPECKIT START -->
For additional context about technologies to be used, project structure,
shell commands, and other important information, read the current plan
<!-- SPECKIT END -->
