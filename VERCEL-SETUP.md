# Vercel Deployment Guide - Skedadel Fleet Management

This guide walks you through deploying both your frontend and backend to Vercel using serverless functions.

## 📋 Prerequisites

- Vercel account (free tier works)
- Git repository connected to Vercel
- Database credentials (MySQL on Hostinger)
- Gemini API key

## 🚀 Quick Deployment Steps

### 1. Install Vercel CLI (Optional)

```bash
npm install -g vercel
```

### 2. Deploy via GitHub (Recommended)

1. **Push your code to GitHub**
   ```bash
   git add .
   git commit -m "Configure Vercel deployment"
   git push origin main
   ```

2. **Import to Vercel**
   - Go to [vercel.com/new](https://vercel.com/new)
   - Click "Import Project"
   - Select your GitHub repository
   - Vercel will auto-detect the configuration

3. **Configure Environment Variables**
   
   In your Vercel project settings → Environment Variables, add:

   ```
   NODE_ENV=production
   USE_SQL_DATABASE=true
   
   # Database Configuration
   DB_HOST=195.35.53.7
   DB_PORT=3306
   DB_NAME=u682067506_fleet_system
   DB_USER=u682067506_fleet_system
   DB_PASSWORD=your_database_password_here
   
   # JWT Secret
   JWT_SECRET=your_jwt_secret_here
   
   # Gemini API Key (for AI features)
   VITE_GEMINI_API_KEY=your_gemini_api_key_here
   
   # Vercel environment variable (auto-set by Vercel)
   VERCEL=1
   ```

4. **Deploy**
   - Click "Deploy"
   - Wait for build to complete (~2-3 minutes)

### 3. Deploy via CLI (Alternative)

```bash
# Login to Vercel
vercel login

# Deploy to preview
vercel

# Deploy to production
vercel --prod
```

## 🔧 What Was Changed

### New Files
- **`api/index.js`** - Serverless function handler that wraps your Express backend

### Modified Files
- **`vercel.json`** - Routes API calls to serverless function, serves frontend from `/dist`
- **`package.json`** - Added `vercel-build` script
- **`vite.config.ts`** - Configured for production (no proxy needed on Vercel)
- **`server/config/database.js`** - Optimized connection pooling for serverless

## 📊 How It Works

```
User Request → Vercel Edge Network
                    ↓
              Is it /api/* ?
               ↙        ↘
            YES         NO
             ↓           ↓
    api/index.js    dist/index.html
    (Serverless)    (Static Files)
         ↓
    MySQL Database
    (Hostinger)
```

- **Frontend**: Built static files served from global CDN
- **Backend**: Serverless function runs on-demand
- **Database**: Connects to your existing Hostinger MySQL database

## ⚙️ Environment Variables Explained

| Variable | Purpose | Example |
|----------|---------|---------|
| `NODE_ENV` | Environment mode | `production` |
| `USE_SQL_DATABASE` | Use MySQL vs MongoDB | `true` |
| `DB_HOST` | Database host IP | `195.35.53.7` |
| `DB_PORT` | Database port | `3306` |
| `DB_NAME` | Database name | `u682067506_fleet_system` |
| `DB_USER` | Database username | `u682067506_fleet_system` |
| `DB_PASSWORD` | Database password | Your password |
| `JWT_SECRET` | JWT signing secret | Random string |
| `VITE_GEMINI_API_KEY` | Google AI API key | Your Gemini key |
| `VERCEL` | Auto-set by Vercel | `1` |

> **Note**: The `VERCEL` environment variable is automatically set by Vercel and triggers serverless-optimized database pooling.

## ✅ Post-Deployment Verification

1. **Check Health Endpoint**
   ```
   https://your-app.vercel.app/api/health
   ```
   Should return:
   ```json
   {
     "status": "ok",
     "message": "Fleet Management API is running on Vercel",
     "environment": "production",
     "database": "MySQL",
     "dbInitialized": true
   }
   ```

2. **Test Frontend**
   - Visit `https://your-app.vercel.app`
   - Verify the app loads
   - Check browser console for errors

3. **Test Authentication**
   - Try logging in
   - Create a test order
   - Verify data persistence

## 🐛 Troubleshooting

### Build Fails

**Issue**: Build fails during deployment  
**Solution**: 
- Check build logs in Vercel dashboard
- Ensure all dependencies are in `dependencies` (not `devDependencies`)
- Verify Node.js version compatibility (use 18.x)

### API Returns 500 Error

**Issue**: `/api/*` endpoints return 500 errors  
**Solution**:
- Check Vercel function logs
- Verify database credentials in environment variables
- Ensure database allows connections from Vercel IPs
- Check serverless function timeout (10s on free tier)

### Database Connection Fails

**Issue**: "Unable to connect to database" errors  
**Solution**:
- Verify database host IP is correct
- Check database allows remote connections
- Confirm username/password are correct
- Test connection from another tool (MySQL Workbench)

### Environment Variables Not Working

**Issue**: API can't access environment variables  
**Solution**:
- Verify variables are set in Vercel dashboard
- Redeploy after adding new variables
- Use `VITE_` prefix for frontend variables only
- Backend variables don't need prefix

### Serverless Function Timeout

**Issue**: Requests timeout after 10 seconds  
**Solution**:
- Optimize slow database queries
- Add indexes to frequently queried columns
- Consider upgrading to Vercel Pro (60s timeout)
- For very long operations, consider keeping backend on VPS

## 🔄 Redeployment

To redeploy after making changes:

```bash
git add .
git commit -m "Your changes"
git push origin main
```

Vercel will automatically redeploy when you push to your main branch.

Or use CLI:
```bash
vercel --prod
```

## 📈 Performance Tips

1. **Database Optimization**
   - Add indexes to frequently queried columns
   - Use `SELECT` with specific columns instead of `SELECT *`
   - Implement caching for frequently accessed data

2. **Serverless Best Practices**
   - Keep functions small and focused
   - Minimize cold start time
   - Use connection pooling wisely (already configured)

3. **Frontend Optimization**
   - Images are cached for 1 year
   - Code splitting is automatic with Vite
   - Consider lazy loading for views

## 🆘 Support Resources

- [Vercel Documentation](https://vercel.com/docs)
- [Vercel Serverless Functions](https://vercel.com/docs/concepts/functions/serverless-functions)
- [Troubleshooting Guide](https://vercel.com/docs/concepts/deployments/troubleshoot-a-build)

## 🎯 Custom Domain (Optional)

1. Go to your Vercel project → Settings → Domains
2. Add your custom domain
3. Update DNS records as instructed
4. SSL certificate is automatically provisioned

## 📊 Monitoring

- **Analytics**: Enable Vercel Analytics in project settings
- **Logs**: View real-time logs in Vercel dashboard → Deployments → Your deployment → Runtime Logs
- **Performance**: Check Core Web Vitals in Vercel Analytics

---

**Your app is now deployed!** Visit your Vercel URL to see it live. 🎉
