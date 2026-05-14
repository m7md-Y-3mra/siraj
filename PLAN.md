Step 2: Authentication & Route Protection
The goal is to ensure only your specific account can access the management tools.

Auth Implementation: Set up a login page using Supabase Auth (Email/Password) to obtain a session.

Next.js Middleware: Create a middleware.ts file to intercept requests to /dashboard. It must check if the auth.uid() exists in your newly created admins table before allowing access.

Admin Verification Utility: Write a server-side helper function to re-verify admin status within Server Actions to prevent unauthorized API calls.

Step 3: Folder & Container Management
This establishes the "Many-to-Many" organization system for your resources.

Folder CRUD UI: Build the /dashboard/folders view to manage your containers (e.g., "Ibn Qayyim Books").

Junction Logic: Prepare the frontend to handle the folder_resources table, allowing a single resource to be linked to multiple folder IDs.

Server Actions: Create actions to create, update, and delete folders, ensuring revalidatePath is called to update the public site.

Step 4: Resource Dashboard (Books & Playlists)
This is the core management hub for uploading files and links.

Dynamic Resource Form: Build a form that toggles fields based on whether the user is adding a BOOK or a PLAYLIST.

File Upload Service:

For Books: Implement a client-side upload to the library_files bucket.

For Playlists: Simply capture the URL.

Mapping UI: Integrate a multi-select component in the form to assign the resource to one or more folders simultaneously.

Step 5: Public Library & Unified Search
Creating the interface for students of knowledge.

Unified Resource Fetching: Use a Server Component to fetch the resources table.

Advanced Filtering:

Implement Search by title or author.

Implement Filters by type (Book vs. Playlist) and by Folder name.

Responsive Grid: Use React 19 features to render a performant grid of resource cards.

Step 6: Viewing Experience & Summaries
Dynamic Routing: Setup /resource/[id] to display individual items.

Media Rendering:

For Books: Use an iframe or react-pdf to display the PDF from the url stored in the database.

For Playlists: Embed the video player and fetch associated data from the summaries table to display beneath it.

Download Logic: Ensure the url for books triggers a download using the Supabase Storage public link.

Step 7: Optimization & Deployment
ISR & PPR: Apply Incremental Static Regeneration to the library and folder pages to ensure high performance.

SEO: Add dynamic metadata for each book and folder to make links social-media friendly.

Final Review: Verify all RLS policies are active on the library_files bucket and all tables to maintain strict admin-only write access.
