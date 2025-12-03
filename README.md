# Skedadel Fleet Management System

A comprehensive fleet management platform built with React and Express, optimized for Vercel deployment.

## 🚀 Quick Deploy to Vercel

[![Deploy with Vercel](https://vercel.com/button)](https://vercel.com/new/clone)

### 1. Deploy via GitHub

```bash
git add .
git commit -m "Deploy to Vercel"
git push origin main
```

Then import your repository at [vercel.com/new](https://vercel.com/new)

### 2. Configure Environment Variables

Add these in Vercel Dashboard → Settings → Environment Variables:

```env
NODE_ENV=production
USE_SQL_DATABASE=true
DB_HOST=195.35.53.7
DB_PORT=3306
DB_NAME=u682067506_fleet_system
DB_USER=u682067506_fleet_system
DB_PASSWORD=your_password
JWT_SECRET=your_jwt_secret
VITE_GEMINI_API_KEY=your_gemini_key
```

### 3. Deploy

Click "Deploy" and wait ~2 minutes. Done! 🎉

## 📖 Full Setup Guide

See [VERCEL-SETUP.md](./VERCEL-SETUP.md) for detailed deployment instructions, troubleshooting, and optimization tips.

## 🏗️ Architecture

- **Frontend**: React + Vite → Static files on Vercel CDN
- **Backend**: Express → Serverless functions on Vercel
- **Database**: MySQL on Hostinger

## 💻 Local Development

```bash
# Install dependencies
npm install

# Start development (frontend + backend)
npm start

# Frontend only (port 3000)
npm run dev

# Backend only (port 5000)
npm run server
```

## 📁 Project Structure

```
├── api/                  # Serverless functions
│   └── index.js         # API handler
├── components/          # React components
├── views/              # React views
├── server/             # Express backend
│   ├── routes/         # API routes
│   ├── models/         # Database models
│   └── config/         # Configuration
├── services/           # Business logic
└── dist/              # Build output
```

## 🔑 Key Features

- Real-time order tracking
- Driver management
- Fleet analytics
- Geofencing
- Invoice generation
- Challenge system

## 📝 License

MIT

---

Built with ❤️ for modern fleet management
