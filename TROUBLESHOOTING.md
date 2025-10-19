# ViewTube Troubleshooting Guide

## Common Issues and Solutions

### TypeScript/Import Errors Before Installation

**Symptoms:**
- "Cannot find module 'react'" errors
- "JSX element implicitly has type 'any'" errors
- Red underlines in TypeScript files

**Solution:**
These are expected BEFORE running `npm install`. Simply run:
```bash
npm install
```

All TypeScript errors will disappear once dependencies are installed.

---

### Build Errors

#### Issue: "Cannot find module 'path'"
**Solution:** 
Already included `@types/node` in devDependencies. Run:
```bash
npm install
```

#### Issue: Vite config errors
**Solution:**
The `vite.config.ts` is properly configured with path alias support. Ensure you've run `npm install`.

---

### Database/Supabase Issues

#### Issue: "Invalid API key" or "Failed to fetch"
**Solution:**
1. Check your `.env` file has correct credentials
2. Ensure no extra spaces or quotes around values
3. Verify URL format: `https://xxxxx.supabase.co`
4. Restart dev server after changing `.env`

#### Issue: "Row Level Security policy violation"
**Solution:**
1. Ensure you ran the complete `supabase-schema.sql`
2. Check RLS is enabled on all tables
3. Verify policies are created (check in Supabase Table Editor → Policies)

#### Issue: "relation does not exist"
**Solution:**
Database tables not created. Run `supabase-schema.sql` in SQL Editor.

---

### Authentication Issues

#### Issue: Can't login after signup
**Solution:**
1. Check Supabase email confirmation settings
2. In Supabase: Authentication → Settings → Enable "Confirm email" OFF for testing
3. Or check your email for confirmation link

#### Issue: Admin panel shows "Access Denied"
**Solution:**
1. Go to Supabase Table Editor → `users` table
2. Find your user row
3. Set `is_admin` column to `true`
4. Logout and login again

---

### Upload Issues

#### Issue: Video upload fails
**Solution:**
1. Verify storage buckets exist: `videos` and `thumbnails`
2. Ensure buckets are PUBLIC (in Supabase Storage settings)
3. Check file size is under 500MB
4. Verify file format (MP4, WebM, OGG)

#### Issue: "Failed to upload to storage"
**Solution:**
1. Check bucket names are exactly `videos` and `thumbnails` (lowercase)
2. Verify bucket policies allow public uploads
3. Check Supabase project is not paused (free tier)

---

### Development Server Issues

#### Issue: Port 5173 already in use
**Solution:**
```bash
# Kill the process or use different port
npm run dev -- --port 3000
```

#### Issue: Hot reload not working
**Solution:**
1. Restart dev server
2. Clear browser cache (Ctrl+Shift+R)
3. Check firewall isn't blocking WebSocket connections

---

### Build/Production Issues

#### Issue: Build fails with "out of memory"
**Solution:**
```bash
# Increase Node memory
set NODE_OPTIONS=--max-old-space-size=4096
npm run build
```

#### Issue: Environment variables not working in production
**Solution:**
- Ensure all `VITE_` prefixed variables are set in your hosting platform
- Rebuild after changing environment variables
- Variables must start with `VITE_` to be exposed to frontend

---

### PWA Issues

#### Issue: PWA not installing
**Solution:**
1. Must use HTTPS (localhost is OK for testing)
2. Check manifest.json is served correctly
3. Verify service worker registered (DevTools → Application → Service Workers)

#### Issue: Service worker caching old content
**Solution:**
1. Unregister service worker in DevTools
2. Clear cache
3. Hard refresh (Ctrl+Shift+R)

---

### Performance Issues

#### Issue: Slow video loading
**Solution:**
1. Videos are served directly from Supabase Storage
2. Consider adding CDN for production
3. Use smaller video files for testing
4. Enable compression in Supabase

#### Issue: Slow page loads
**Solution:**
1. Check network tab for slow requests
2. Verify database indexes are created (they're in schema)
3. Limit query results (already implemented with `.limit()`)

---

### TypeScript Strict Mode Errors

If you see type errors in development:

**"Parameter 'e' implicitly has 'any' type"**
These are already typed correctly in the onChange handlers. If you see them:
```typescript
onChange={(e: React.ChangeEvent<HTMLInputElement>) => ...}
```

**"Property does not exist on type"**
Check your TypeScript version matches package.json (5.2.2)

---

## Verification Checklist

Before reporting issues, verify:

- [ ] Ran `npm install`
- [ ] Created `.env` file with correct credentials  
- [ ] Ran `supabase-schema.sql` in Supabase
- [ ] Created storage buckets (`videos`, `thumbnails`)
- [ ] Buckets are set to PUBLIC
- [ ] Restarted dev server after changing `.env`
- [ ] Using Node.js 16 or higher
- [ ] Browser is modern (Chrome 90+, Firefox 88+, Safari 14+)

---

## Getting Additional Help

1. **Check Browser Console** - Most errors show here with details
2. **Check Supabase Logs** - Go to Supabase Dashboard → Logs
3. **Verify Network Requests** - Use browser DevTools → Network tab
4. **Check File Structure** - Ensure all files are in correct locations

---

## Known Limitations

- Video transcoding is not implemented (videos play in uploaded format)
- Email notifications require additional setup
- Free Supabase tier has limits: 500MB database, 1GB storage, 50MB file uploads
- Search is basic (full-text, not AI-powered)

---

## Reset Everything (Nuclear Option)

If all else fails:

```bash
# Delete node_modules and reinstall
rm -rf node_modules package-lock.json
npm install

# In Supabase, drop all tables and re-run schema
# WARNING: This deletes all data!
DROP SCHEMA public CASCADE;
CREATE SCHEMA public;
# Then run supabase-schema.sql again
```

---

## Report Issues

If problems persist after trying solutions above, gather:
1. Error message (full text)
2. Browser console output
3. Node.js version (`node --version`)
4. Operating system
5. Steps to reproduce

The more details you provide, the easier to diagnose!
