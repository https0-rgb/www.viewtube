# ViewTube Quick Start Guide

Get ViewTube running in 5 minutes!

## Prerequisites
- Node.js 16+ installed
- A Supabase account (free)

## Quick Setup (5 steps)

### 1. Install Dependencies
\`\`\`bash
npm install
\`\`\`

### 2. Create Supabase Project
1. Go to [supabase.com](https://supabase.com) and create a new project
2. Wait for it to finish setting up (2-3 minutes)

### 3. Set Up Database
1. In Supabase, go to **SQL Editor**
2. Copy everything from `supabase-schema.sql`
3. Paste and click **Run**

### 4. Create Storage Buckets
1. Go to **Storage** in Supabase
2. Create bucket named `videos` (public)
3. Create bucket named `thumbnails` (public)

### 5. Configure Environment
1. In Supabase, go to **Settings** → **API**
2. Copy your **Project URL** and **anon public key**
3. Rename `.env.example` to `.env`
4. Paste your credentials:
\`\`\`env
VITE_SUPABASE_URL=your_project_url
VITE_SUPABASE_ANON_KEY=your_anon_key
\`\`\`

## Start the App

\`\`\`bash
npm run dev
\`\`\`

Open [http://localhost:5173](http://localhost:5173)

## Create Admin Account

1. Click **Sign Up** and create an account
2. Go to Supabase **Table Editor** → **users** table
3. Find your user and set `is_admin` to `true`
4. Access admin panel at `/admin`

## Test Features

✅ Upload a video  
✅ Search for videos  
✅ Comment on a video  
✅ Create a playlist  
✅ Subscribe to a channel  
✅ Access admin dashboard  

## Need Help?

- Check `SETUP_GUIDE.md` for detailed instructions
- See `FEATURES.md` for complete feature list
- Review `README.md` for technical documentation

## Production Build

\`\`\`bash
npm run build
\`\`\`

Deploy the `dist` folder to Netlify, Vercel, or any static host.

---

**That's it! You're ready to go! 🚀**
