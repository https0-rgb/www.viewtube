# ViewTube Installation Instructions

## Prerequisites

Before you begin, ensure you have:
- **Node.js 16 or higher** - [Download here](https://nodejs.org/)
- **npm** (comes with Node.js)
- A **Supabase account** - [Sign up free](https://supabase.com)

Check your versions:
```bash
node --version  # Should be v16.0.0 or higher
npm --version   # Should be 7.0.0 or higher
```

---

## Installation Steps

### Step 1: Install Dependencies

Open terminal in the project directory:

```bash
npm install
```

This installs:
- React & React DOM
- TypeScript
- Vite (build tool)
- Tailwind CSS
- Supabase client
- All other dependencies

**Expected time:** 2-3 minutes

**Note:** TypeScript errors are normal before this step!

---

### Step 2: Set Up Supabase

#### 2.1 Create Project

1. Go to [supabase.com](https://supabase.com)
2. Sign in with GitHub or email
3. Click "New Project"
4. Fill in:
   - **Name:** viewtube
   - **Database Password:** (generate and save it)
   - **Region:** Choose nearest to you
5. Click "Create new project"
6. Wait 2-3 minutes for setup

#### 2.2 Create Database Schema

1. In Supabase Dashboard, click **SQL Editor** (left sidebar)
2. Click **New query**
3. Open `supabase-schema.sql` from project root
4. Copy ALL contents (Ctrl+A, Ctrl+C)
5. Paste into SQL Editor
6. Click **Run** (or press Ctrl+Enter)
7. Should see: ✅ "Success. No rows returned"

This creates:
- 9 tables (users, videos, comments, etc.)
- Indexes for performance
- Row Level Security policies
- Database triggers

#### 2.3 Create Storage Buckets

1. Go to **Storage** (left sidebar)
2. Click **New bucket**

Create first bucket:
- Name: `videos`
- Public bucket: ✅ **YES** (checked)
- Click **Create bucket**

Create second bucket:
- Name: `thumbnails`  
- Public bucket: ✅ **YES** (checked)
- Click **Create bucket**

**Important:** Bucket names must be exact (lowercase)!

---

### Step 3: Configure Environment Variables

#### 3.1 Get Supabase Credentials

1. In Supabase, go to **Settings** (gear icon, bottom left)
2. Click **API** in settings menu
3. You'll need two values:

**Project URL:**
```
https://xxxxxxxxxxxxx.supabase.co
```

**anon public key:**
```
eyJhbGc....(long string)....xyz
```

Copy these values!

#### 3.2 Create .env File

1. In project root, find `.env.example`
2. **Rename it** to `.env` (remove .example)
3. Open `.env` in text editor
4. Paste your values:

```env
VITE_SUPABASE_URL=https://your-project-ref.supabase.co
VITE_SUPABASE_ANON_KEY=your-anon-key-here
```

**Important:** 
- No quotes around values
- No spaces before/after =
- Must start with `VITE_`

---

### Step 4: Start Development Server

```bash
npm run dev
```

You should see:
```
VITE v5.0.8  ready in 500 ms

➜  Local:   http://localhost:5173/
➜  Network: use --host to expose
```

**Open browser:** [http://localhost:5173](http://localhost:5173)

You should see ViewTube home page! 🎉

---

### Step 5: Create Your Account

1. Click **Sign Up** (top right)
2. Fill in:
   - Username: (your choice)
   - Email: (your email)
   - Password: (at least 6 characters)
3. Check "I agree to Terms"
4. Click **Sign Up**

You're now logged in!

---

### Step 6: Grant Admin Access (Optional)

To access the admin panel:

1. Go back to **Supabase Dashboard**
2. Click **Table Editor** (left sidebar)
3. Select **users** table
4. Find your user row (by email)
5. Click the **is_admin** cell
6. Change from `false` to `true`
7. Click checkmark to save

Now visit: [http://localhost:5173/admin](http://localhost:5173/admin)

You have admin access! 🎊

---

## Verification

Test these features to ensure everything works:

### Basic Features
- [x] Home page loads with video grid
- [x] Can navigate using bottom bar
- [x] Search page works
- [x] Login/logout works

### User Features (when logged in)
- [x] Upload a video (try small test file)
- [x] View your channel at /my-channel
- [x] Create a playlist
- [x] Edit your profile in settings

### Admin Features (if admin enabled)
- [x] Access /admin dashboard
- [x] See statistics
- [x] View content management
- [x] Check user management

---

## Next Steps

### Customize Your App

1. **Change colors** - Edit `tailwind.config.js`
2. **Update logo** - Replace files in `public/` folder
3. **Modify metadata** - Edit `index.html`

### Production Deployment

When ready to deploy:

```bash
npm run build
```

This creates `dist/` folder ready for deployment.

**Recommended hosts:**
- [Netlify](https://netlify.com) - Easiest
- [Vercel](https://vercel.com) - Fast
- [Firebase Hosting](https://firebase.google.com) - Google
- Any static host

Remember to set environment variables in hosting platform!

---

## Troubleshooting

### "Cannot find module 'react'"
**Solution:** Run `npm install`

### "Invalid API key"  
**Solution:** Check `.env` file has correct credentials

### Videos won't upload
**Solution:** Verify storage buckets are created and PUBLIC

### Can't access admin panel
**Solution:** Set `is_admin = true` in users table

**For more issues:** See `TROUBLESHOOTING.md`

---

## File Structure After Installation

```
ViewTube/
├── node_modules/       # ✅ Created after npm install
├── src/                # React source code
├── public/             # Static assets
├── dist/              # ✅ Created after npm run build
├── .env               # ✅ Your credentials (created by you)
├── package.json        # Dependencies
└── README.md          # Documentation
```

---

## Important Notes

⚠️ **Never commit `.env` file** - It's in `.gitignore` for security

⚠️ **Supabase Free Tier Limits:**
- 500MB database storage
- 1GB file storage
- 50MB max file upload
- Good for development and small projects

✅ **Security:** Row Level Security is enabled by default

✅ **TypeScript:** Full type safety throughout the app

---

## Quick Reference

```bash
# Install dependencies
npm install

# Start dev server
npm run dev

# Build for production
npm run build

# Preview production build
npm run preview

# Run linter
npm run lint
```

---

## Support

- **Setup issues:** Check `TROUBLESHOOTING.md`
- **Feature docs:** See `FEATURES.md`
- **Quick start:** Read `QUICKSTART.md`
- **Database:** Review `supabase-schema.sql`

---

## Success! 🎉

If you see the ViewTube home page and can sign up/login, you're all set!

Start uploading videos and exploring features.

**Enjoy building with ViewTube!** 🚀
