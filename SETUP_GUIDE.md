# ViewTube Setup Guide

This guide will walk you through setting up ViewTube from scratch.

## Prerequisites

- Node.js 16+ installed
- A Supabase account (free tier works fine)
- Git (optional)

## Step-by-Step Setup

### 1. Install Dependencies

Open your terminal in the project directory and run:

\`\`\`bash
npm install
\`\`\`

This will install all necessary packages including React, TypeScript, Tailwind CSS, and Supabase.

### 2. Set Up Supabase Backend

#### 2.1 Create Supabase Project

1. Go to [supabase.com](https://supabase.com)
2. Click "Start your project"
3. Sign in with GitHub or email
4. Click "New Project"
5. Fill in:
   - Project name: `viewtube`
   - Database password: (generate a strong password and save it)
   - Region: Choose closest to you
6. Click "Create new project" and wait for setup (2-3 minutes)

#### 2.2 Run Database Schema

1. In your Supabase project, go to **SQL Editor** (left sidebar)
2. Click "New query"
3. Copy the entire contents of `supabase-schema.sql`
4. Paste into the SQL editor
5. Click "Run" (or press Ctrl+Enter)
6. You should see "Success. No rows returned"

This creates all necessary tables, indexes, and security policies.

#### 2.3 Set Up Storage Buckets

1. Go to **Storage** (left sidebar)
2. Click "Create a new bucket"
3. Create first bucket:
   - Name: `videos`
   - Public bucket: ✓ Yes
   - Click "Create bucket"
4. Create second bucket:
   - Name: `thumbnails`
   - Public bucket: ✓ Yes
   - Click "Create bucket"

#### 2.4 Get Your API Credentials

1. Go to **Project Settings** (gear icon, bottom left)
2. Click **API** in the left sidebar
3. Copy these values:
   - **Project URL** (e.g., `https://xxxxx.supabase.co`)
   - **anon public** key (long string under "Project API keys")

### 3. Configure Environment Variables

1. In the project root, rename `.env.example` to `.env`
2. Open `.env` and paste your credentials:

\`\`\`env
VITE_SUPABASE_URL=https://your-project.supabase.co
VITE_SUPABASE_ANON_KEY=your-anon-key-here
\`\`\`

**Important:** Never commit the `.env` file to version control!

### 4. Start Development Server

\`\`\`bash
npm run dev
\`\`\`

The app will open at `http://localhost:5173`

You should see the ViewTube home page!

### 5. Create Your First Admin Account

1. Click "Sign Up" in the top right
2. Create an account with:
   - Username: `admin`
   - Email: your email
   - Password: strong password
3. After signing up, go back to Supabase
4. Go to **Table Editor** → **users** table
5. Find your user row
6. Click to edit the `is_admin` column
7. Change from `false` to `true`
8. Click the checkmark to save

Now you can access the admin panel at `/admin`

### 6. Test the Application

#### As a Regular User:
- ✓ Browse videos on the home page
- ✓ Search for videos
- ✓ Upload a video (small test file)
- ✓ Comment on videos
- ✓ Subscribe to channels
- ✓ Create playlists

#### As an Admin:
- ✓ Visit `/admin` to access admin panel
- ✓ Approve/reject uploaded videos
- ✓ Manage users
- ✓ View analytics
- ✓ Moderate comments

## Common Issues

### Issue: "Invalid API key"
**Solution:** Double-check your `.env` file has the correct credentials from Supabase.

### Issue: Videos won't upload
**Solution:** 
1. Verify storage buckets are created and public
2. Check bucket names are exactly `videos` and `thumbnails`
3. Ensure file size is under 500MB

### Issue: Can't see admin panel
**Solution:** 
1. Make sure you set `is_admin = true` in the users table
2. Log out and log back in
3. Navigate directly to `/admin`

### Issue: Database errors
**Solution:** 
1. Re-run the `supabase-schema.sql` script
2. Check all tables were created in Table Editor
3. Verify Row Level Security policies are enabled

## Building for Production

\`\`\`bash
npm run build
\`\`\`

This creates an optimized build in the `dist/` folder.

### Deploy to Netlify (Recommended)

1. Push code to GitHub
2. Go to [netlify.com](https://netlify.com)
3. Click "Add new site" → "Import an existing project"
4. Connect to GitHub and select your repo
5. Build settings:
   - Build command: `npm run build`
   - Publish directory: `dist`
6. Add environment variables (VITE_SUPABASE_URL, VITE_SUPABASE_ANON_KEY)
7. Click "Deploy site"

## Next Steps

- Customize colors in `tailwind.config.js`
- Add your logo images in `public/` folder
- Update site metadata in `index.html`
- Configure video processing (optional)
- Set up email notifications (optional)
- Add payment integration for monetization (optional)

## Support

If you encounter any issues:
1. Check the browser console for errors
2. Review Supabase logs in the Logs section
3. Verify all setup steps were completed
4. Check that RLS policies are enabled

## Security Notes

- Never expose your `VITE_SUPABASE_ANON_KEY` is safe for frontend use
- The service role key should NEVER be in frontend code
- Row Level Security (RLS) protects your data
- Always validate user input on the backend

Enjoy building with ViewTube! 🎥✨
