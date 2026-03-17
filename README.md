<div align="center">

<img src="https://skillicons.dev/icons?i=github" />

<br/>

![GitHub last commit](https://img.shields.io/github/last-commit/Tristan-DW/Skedadel-fleet-system?style=for-the-badge&color=6e40c9)
![GitHub stars](https://img.shields.io/github/stars/Tristan-DW/Skedadel-fleet-system?style=for-the-badge&color=f0883e)
![GitHub issues](https://img.shields.io/github/issues/Tristan-DW/Skedadel-fleet-system?style=for-the-badge&color=da3633)
![License](https://img.shields.io/badge/license-MIT-238636?style=for-the-badge)

# Skedadel-fleet-system

> **Skedadel fleet system**

</div>

---

A comprehensive fleet management platform built with React and Express, optimized for Vercel deployment.

##  Quick Deploy to Vercel

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

Click "Deploy" and wait ~2 minutes. Done! 

##  Full Setup Guide

See [VERCEL-SETUP.md](./VERCEL-SETUP.md) for detailed deployment instructions, troubleshooting, and optimization tips.

## ️ Architecture

- **Frontend**: React + Vite → Static files on Vercel CDN
- **Backend**: Express → Serverless functions on Vercel
- **Database**: MySQL on Hostinger

##  Local Development

```bash
npm install

# Start development (frontend + backend)
npm start

# Frontend only (port 3000)
npm run dev

# Backend only (port 5000)
npm run server
```

##  Project Structure

```
 api/                  # Serverless functions
    index.js         # API handler
 components/          # React components
 views/              # React views
 server/             # Express backend
    routes/         # API routes
    models/         # Database models
    config/         # Configuration
 services/           # Business logic
 dist/              # Build output
```

##  Key Features

- Real-time order tracking
- Driver management
- Fleet analytics
- Geofencing
- Invoice generation
- Challenge system

##  License

MIT

---

Built with ️ for modern fleet management

---

<div align="center">

**Made with love by [Tristan Wentzel](https://github.com/Tristan-DW)**

</div>

---

<div align="center">

<sub>Built by <a href="https://github.com/Tristan-DW">Tristan Wentzel</a></sub>

</div>

---

<div align="center">

<sub>Architected by <a href="https://github.com/Tristan-DW">Tristan</a> &mdash; Head Architect</sub>

</div>
