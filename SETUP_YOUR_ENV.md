# 🔑 Setup Your Environment File

## Quick Setup (2 steps)

Your Supabase credentials are ready! Follow these simple steps:

### Step 1: Create .env File

In the project root, create a new file named **`.env`** (exactly, with the dot at the beginning)

**Option A: Using File Explorer**
1. Open File Explorer to this folder
2. Right-click → New → Text Document
3. Name it `.env` (delete the .txt extension)

**Option B: Using VS Code**
1. In VS Code, click File → New File
2. Save as `.env` in the project root

**Option C: Using Terminal**
```powershell
New-Item -Path .env -ItemType File
```

### Step 2: Copy Your Credentials

Open the `.env` file you just created and paste these EXACT lines:

```
VITE_SUPABASE_URL=https://ebsvgvffgkuplciyqqah.supabase.co
VITE_SUPABASE_ANON_KEY=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJzdXBhYmFzZSIsInJlZiI6ImVic3ZndmZmZ2t1cGxjaXlxcWFoIiwicm9sZSI6ImFub24iLCJpYXQiOjE3NjA4MjY1NDcsImV4cCI6MjA3NjQwMjU0N30.KiNLSzJFQUlfK5fsgni3XpqoC7NK5h2NkA9Bj74sy9I
```

**Or simply:**
1. Open `YOUR_ENV_FILE.txt` (in this folder)
2. Copy all contents
3. Paste into your new `.env` file
4. Save

### Step 3: Verify

Your `.env` file should look exactly like this:
- Line 1: `VITE_SUPABASE_URL=https://ebsvgvffgkuplciyqqah.supabase.co`
- Line 2: `VITE_SUPABASE_ANON_KEY=eyJhbGc...` (long key)
- No extra spaces
- No quotes around values
- No blank lines at the start

---

## ✅ That's It!

Once you save the `.env` file, you're ready to start the app:

```bash
npm run dev
```

The app will now connect to your Supabase project!

---

## 🔒 Security Note

The `.env` file is automatically ignored by Git (listed in `.gitignore`), so your credentials won't be committed to version control. This is why I can't create it automatically - it's protected for security!

---

## 🎯 Next Steps

1. ✅ Create `.env` file with your credentials (above)
2. ✅ Run `npm run dev`
3. ✅ Open http://localhost:5173
4. ✅ Set up database (run `supabase-schema.sql` in Supabase)
5. ✅ Create storage buckets (`videos`, `thumbnails`)
6. ✅ Sign up and start using ViewTube!

---

## 📞 Need Help?

If you see errors like "Invalid API key":
- Check `.env` file has NO spaces around the `=` sign
- Check the file is named exactly `.env` (not `.env.txt`)
- Restart the dev server after creating `.env`

**Your Supabase Project:** https://ebsvgvffgkuplciyqqah.supabase.co
