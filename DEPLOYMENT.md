# Deployment Guide for AI Workout Form Corrector

## Files Created for Deployment

1. **`.streamlit/config.toml`** - Streamlit configuration
2. **`packages.txt`** - System dependencies for Streamlit Cloud
3. **`.python-version`** - Python version specification
4. **`requirements.txt`** - Updated with flexible version requirements

## Deployment Options

### Option 1: Streamlit Cloud (Recommended for Quick Deploy)

1. **Push to GitHub:**
   ```bash
   cd /Users/qihanw/Documents/ai_workout_corrector
   git init
   git add .
   git commit -m "Initial commit: AI Workout Form Corrector"
   git branch -M main
   git remote add origin YOUR_GITHUB_REPO_URL
   git push -u origin main
   ```

2. **Deploy on Streamlit Cloud:**
   - Go to https://share.streamlit.io/
   - Click "New app"
   - Select your repository
   - Set main file path: `app.py`
   - Click "Deploy"

### Option 2: Docker Deployment (Cloud Run, Railway, Render)

The Dockerfile is already configured. To deploy:

**Google Cloud Run:**
```bash
# Build and push
gcloud builds submit --tag gcr.io/YOUR_PROJECT_ID/workout-corrector
gcloud run deploy workout-corrector --image gcr.io/YOUR_PROJECT_ID/workout-corrector --platform managed --port 8080 --allow-unauthenticated
```

**Railway:**
```bash
# Install Railway CLI
npm i -g @railway/cli
# Login and deploy
railway login
railway init
railway up
```

**Render:**
- Connect your GitHub repo
- Select "Web Service"
- Use Dockerfile for deployment
- Set port to 8080

## Important Notes

### WebRTC Considerations
⚠️ **streamlit-webrtc** requires proper STUN/TURN server configuration for production:

- The app currently uses Google's public STUN server
- For production, consider using a dedicated TURN server (Twilio, Xirsys, etc.)
- Some cloud platforms may have firewall restrictions

### Known Deployment Challenges

1. **MediaPipe on ARM architectures**: May require platform-specific builds
2. **WebRTC peer connections**: Requires proper network configuration
3. **Camera permissions**: Users must grant browser camera access

### Testing Deployment

After deployment, test:
1. ✅ App loads without errors
2. ✅ Camera permission prompt appears
3. ✅ Video feed displays
4. ✅ Pose detection overlay appears
5. ✅ Rep counting works
6. ✅ Mode switching works

## Troubleshooting

### If MediaPipe fails to install:
Try using a pre-built wheel or switch to Python 3.10:
```bash
pip install mediapipe --no-deps
pip install -r requirements.txt
```

### If WebRTC doesn't connect:
Check browser console for ICE connection errors. May need to configure TURN servers.

### If deployment times out:
The initial build can take 5-10 minutes due to MediaPipe and OpenCV. This is normal.

## Alternative: Upload Video Mode

If real-time WebRTC proves problematic, consider adding a video upload mode:
- Users upload pre-recorded workout videos
- Process frame-by-frame
- Return analyzed video with feedback

This would work more reliably across all deployment platforms.
