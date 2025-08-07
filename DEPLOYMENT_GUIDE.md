# 🚀 Railway + Render Deployment Guide

## 📋 Overview

- **API Server**: Railway (Python Flask)
- **Admin Dashboard**: Render (React)
- **Database**: SQLite (Railway)
- **Real-time**: Socket.IO

## 🚂 Railway Deployment (API)

### Step 1: Railway Account Setup
1. Go to [Railway.app](https://railway.app)
2. Sign up with GitHub
3. Create new project

### Step 2: Connect Repository
1. Click "Deploy from GitHub repo"
2. Select your repository: `moonbd0529/autojionbot`
3. Railway will auto-detect Python project

### Step 3: Environment Variables
Add these environment variables in Railway dashboard:

```bash
BOT_TOKEN=7408341592:AAHE_Ba4_Tn5qM_qTaui5E8DFSZDB86hys0
ADMIN_USER_ID=6251161332
DASHBOARD_PASSWORD=cpode
CHANNEL_ID=-1002286109418
CHANNEL_URL=https://t.me/+mEcMgPqw3xphODM1
GROUP_INVITE_LINK=https://t.me/+mEcMgPqw3xphODM1
API_ID=25842851
API_HASH=4fcbc414da34a43d86eca15e1235d2ae
CHAT_ID=-1002286109418
FLASK_ENV=production
```

### Step 4: Deploy
1. Railway will auto-deploy
2. Get your Railway URL: `https://your-app.railway.app`

## 🌐 Render Deployment (Admin Dashboard)

### Step 1: Render Account Setup
1. Go to [Render.com](https://render.com)
2. Sign up with GitHub
3. Create new Static Site

### Step 2: Connect Repository
1. Connect your GitHub repository
2. Select branch: `main`
3. Set root directory: `admin`

### Step 3: Build Configuration
- **Build Command**: `npm install && npm run build`
- **Publish Directory**: `build`
- **Environment**: `Node`

### Step 4: Environment Variables
Add these in Render dashboard:

```bash
REACT_APP_API_URL=https://your-railway-app.railway.app
REACT_APP_SOCKET_URL=https://your-railway-app.railway.app
NODE_ENV=production
```

### Step 5: Deploy
1. Render will auto-deploy
2. Get your Render URL: `https://your-app.onrender.com`

## 🔧 Configuration Updates

### Update API URLs
After getting your Railway URL, update these files:

1. **admin/src/environment.js**:
```javascript
production: {
  API_BASE_URL: 'https://your-railway-app.railway.app',
  SOCKET_URL: 'https://your-railway-app.railway.app',
  MEDIA_BASE_URL: 'https://your-railway-app.railway.app/media',
  FRONTEND_URL: 'https://your-render-app.onrender.com'
}
```

2. **api.py** CORS settings:
```python
CORS(app, origins=[
    "https://your-render-app.onrender.com",
    "http://localhost:3000"
], supports_credentials=True)
```

## 📊 Monitoring

### Railway Monitoring
- **Logs**: View in Railway dashboard
- **Metrics**: CPU, Memory usage
- **Deployments**: Auto-deploy on push

### Render Monitoring
- **Logs**: View in Render dashboard
- **Build Status**: Check build logs
- **Performance**: Static site metrics

## 🔒 Security

### Environment Variables
- Never commit sensitive data
- Use Railway/Render environment variables
- Keep bot tokens secure

### CORS Configuration
- Update CORS origins for production
- Allow only your Render domain
- Enable credentials for Socket.IO

## 🚀 Post-Deployment

### 1. Test API Endpoints
```bash
curl https://your-railway-app.railway.app/dashboard-stats
```

### 2. Test Admin Dashboard
- Visit your Render URL
- Login with admin credentials
- Test all features

### 3. Test Bot
- Send message to your bot
- Check auto-approval
- Test media uploads

## 🐛 Troubleshooting

### Railway Issues
- Check environment variables
- View deployment logs
- Verify Python version

### Render Issues
- Check build logs
- Verify Node.js version
- Check environment variables

### Common Problems
1. **CORS Errors**: Update CORS origins
2. **Socket.IO Issues**: Check WebSocket support
3. **Database Issues**: SQLite file permissions

## 📈 Scaling

### Railway Scaling
- Upgrade to paid plan for more resources
- Add custom domain
- Enable auto-scaling

### Render Scaling
- Static sites are automatically scaled
- Add custom domain
- Enable CDN

## 🔄 Updates

### Deploy Updates
1. Push changes to GitHub
2. Railway auto-deploys API
3. Render auto-deploys admin dashboard

### Manual Deploy
```bash
# Railway
railway up

# Render
# Automatic from GitHub
```

---

## 🎯 Quick Deploy Commands

```bash
# 1. Push to GitHub
git add .
git commit -m "Deploy to Railway and Render"
git push origin main

# 2. Railway auto-deploys
# 3. Render auto-deploys
# 4. Update URLs in environment.js
# 5. Test everything
```

Your AutoJOIN Telegram Bot will be live on Railway + Render! 🚀 