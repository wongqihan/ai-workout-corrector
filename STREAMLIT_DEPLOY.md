# 🚀 Deploy to Streamlit Cloud - Step by Step

Your AI Workout Form Corrector is ready to deploy! Follow these steps:

## Step 1: Create GitHub Repository

1. Go to https://github.com/new
2. Repository name: `ai-workout-corrector`
3. Description: `AI-powered workout form analyzer with live camera tracking`
4. Make it **Public** (required for Streamlit Cloud free tier)
5. **DO NOT** initialize with README (we already have files)
6. Click "Create repository"

## Step 2: Push Your Code to GitHub

After creating the repository, GitHub will show you commands. Run these in your terminal:

```bash
cd /Users/qihanw/Documents/ai_workout_corrector

# Add the remote (replace YOUR_USERNAME with your GitHub username)
git remote add origin https://github.com/YOUR_USERNAME/ai-workout-corrector.git

# Push the code
git branch -M main
git push -u origin main
```

## Step 3: Deploy to Streamlit Cloud

1. Go to https://share.streamlit.io/
2. Click **"New app"** button
3. Fill in the form:
   - **Repository:** Select `YOUR_USERNAME/ai-workout-corrector`
   - **Branch:** `main`
   - **Main file path:** `app.py`
4. Click **"Deploy!"**

## Step 4: Wait for Deployment

- Initial deployment takes 3-5 minutes
- Streamlit will install all dependencies from `requirements.txt`
- You'll see a build log - this is normal

## Step 5: Test Your App

Once deployed, you'll get a URL like: `https://YOUR_USERNAME-ai-workout-corrector.streamlit.app`

**Test these features:**
1. ✅ Click "START" to enable camera
2. ✅ Grant camera permissions in browser
3. ✅ Camera feed should appear with pose tracking
4. ✅ Switch between Squat and Push-up modes
5. ✅ Click "▶️ Start Workout" to begin tracking
6. ✅ Verify rep counting works
7. ✅ Check that form feedback appears

## Why Streamlit Cloud?

✅ **Free tier available**
✅ **WebRTC works out of the box** (no TURN server needed)
✅ **Easy deployment** (just push to GitHub)
✅ **Auto-redeploy** on git push
✅ **Built-in SSL/HTTPS** (required for camera access)

## Troubleshooting

### Camera not working?
- Make sure you're using **HTTPS** (Streamlit Cloud provides this automatically)
- Grant camera permissions when prompted
- Try Chrome or Edge browser (best WebRTC support)

### Build failing?
- Check the build logs in Streamlit Cloud dashboard
- Verify all files are committed to GitHub
- Make sure `requirements.txt` and `packages.txt` are in the root directory

### App is slow?
- First load takes time (cold start)
- MediaPipe initialization can take 5-10 seconds
- Subsequent loads will be faster

## Next Steps After Deployment

1. **Share your app** - Send the URL to friends to try it out!
2. **Monitor usage** - Check Streamlit Cloud dashboard for analytics
3. **Update your app** - Just push to GitHub, it auto-redeploys

---

## Quick Command Reference

```bash
# If you need to make changes and redeploy:
cd /Users/qihanw/Documents/ai_workout_corrector
git add .
git commit -m "Update: description of changes"
git push

# Streamlit Cloud will automatically redeploy!
```

---

**Need help?** The Streamlit Community is very active: https://discuss.streamlit.io/
