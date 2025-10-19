# ViewTube Mobile - Progressive Web App

A comprehensive YouTube-like video streaming platform optimized for mobile devices built with React, TypeScript, and Supabase.

> **👉 New here? Start with [START_HERE.md](START_HERE.md) or [QUICKSTART.md](QUICKSTART.md)**

## Features

### User Features
- 🔐 User authentication (login/register)
- 🎥 Video browsing with categories
- 🔍 Advanced search with filters
- ▶️ Full-featured video player
- 👤 User profiles and channels
- 📤 Video upload with metadata
- 💬 Comments with replies
- 👍 Like/dislike system
- 📺 Channel subscriptions
- 📜 Watch history
- 📋 Playlist management
- 📱 Progressive Web App support
- 🔔 Notifications

### Admin Features
- 📊 Analytics dashboard
- 👥 User management
- 🎬 Content moderation
- ✅ Video approval workflow
- 🛡️ Comment moderation
- ⚙️ Platform settings

## Tech Stack

- **Frontend:** React 18, TypeScript, Tailwind CSS
- **Build Tool:** Vite
- **Backend:** Supabase (PostgreSQL, Auth, Storage, Real-time)
- **Routing:** React Router v6
- **Icons:** Lucide React
- **PWA:** Vite PWA Plugin

## Setup Instructions

### 1. Install Dependencies

\`\`\`bash
npm install
\`\`\`

### 2. Set Up Supabase

1. Create a new project at [supabase.com](https://supabase.com)
2. Go to Project Settings > API to get your credentials
3. Run the SQL schema provided in `supabase-schema.sql` in the SQL Editor
4. Set up Storage buckets:
   - Create a `videos` bucket (public)
   - Create a `thumbnails` bucket (public)

### 3. Configure Environment Variables

Create a `.env` file in the root directory:

\`\`\`env
VITE_SUPABASE_URL=your_supabase_project_url
VITE_SUPABASE_ANON_KEY=your_supabase_anon_key
\`\`\`

### 4. Run Development Server

\`\`\`bash
npm run dev
\`\`\`

The app will open at `http://localhost:5173`

### 5. Build for Production

\`\`\`bash
npm run build
npm run preview
\`\`\`

## Project Structure

\`\`\`
src/
├── components/          # Reusable UI components
│   ├── BottomNav.tsx
│   ├── Header.tsx
│   ├── VideoCard.tsx
│   └── ...
├── contexts/           # React contexts (Auth, etc.)
├── lib/                # Utilities and Supabase client
├── pages/              # Page components
│   ├── Home.tsx
│   ├── Search.tsx
│   ├── VideoPlayer.tsx
│   ├── admin/          # Admin pages
│   └── ...
├── App.tsx             # Main app component
└── main.tsx            # Entry point
\`\`\`

## Key Features Implementation

### Authentication
- Uses Supabase Auth for user management
- Protected routes for authenticated users
- Admin role-based access control

### Video Management
- Video upload to Supabase Storage
- Thumbnail support
- Video metadata (title, description, category, tags)
- Status workflow (draft → processing → published/rejected)

### Social Features
- Subscribe to channels
- Like/dislike videos
- Comment with nested replies
- Watch history tracking

### Admin Panel
- Separate admin layout and routes
- Content approval workflow
- User verification system
- Analytics dashboard

## Database Schema

The app uses the following main tables:
- `users` - User profiles and authentication
- `videos` - Video metadata and status
- `comments` - Video comments and replies
- `subscriptions` - Channel subscriptions
- `playlists` - User playlists
- `watch_history` - Video watch tracking
- `video_likes` - Like/dislike records

See `supabase-schema.sql` for the complete schema.

## PWA Features

- Installable on mobile devices
- Offline support with service workers
- App manifest for native-like experience
- Optimized for mobile touch interactions

## Color Palette

- Primary: `#FF6B35` (vibrant orange)
- Secondary: `#1A1A1A` (dark charcoal)
- Accent: `#00D9FF` (bright cyan)
- Background: `#F8F9FA` (light gray)
- Text: `#2D3748` (dark gray)

## Typography

- Headings: Inter (bold, semi-bold)
- Body: Inter (regular, medium)
- Monospace: JetBrains Mono

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## License

This project is open source and available under the MIT License.
