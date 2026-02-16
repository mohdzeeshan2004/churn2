# 🚀 Streamlit Quick Start

Get your churn prediction app live in 2 minutes!

---

## ⚡ Option 1: Local (Instant)

```bash
# 1. Install dependencies
pip install -r streamlit_requirements.txt

# 2. Run app
streamlit run streamlit_app.py

# 3. Open browser
http://localhost:8501

# Done! 🎉
```

---

## ☁️ Option 2: Streamlit Cloud (Recommended - 3 minutes)

**Best for:** Production apps, FREE hosting

### Step 1: Push to GitHub
```bash
git add streamlit_app.py streamlit_requirements.txt
git commit -m "Add Streamlit app"
git push origin main
```

### Step 2: Deploy
1. Go to https://share.streamlit.io
2. Click "New app"
3. Enter: GitHub repo → Branch (main) → File (streamlit_app.py)
4. Click Deploy!

### Step 3: Share
Your app is live at:
```
https://share.streamlit.io/YOUR-USERNAME/YOUR-REPO/streamlit_app.py
```

**That's it!** 🎉

---

## 🐳 Option 3: Docker (5 minutes)

```bash
# 1. Build image
docker build -t churn-streamlit:1.0 .

# 2. Run container
docker run -d -p 8501:8501 churn-streamlit:1.0

# 3. Access
http://localhost:8501
```

---

## 🚀 Option 4: Heroku (5 minutes)

```bash
# 1. Create Procfile
echo "web: streamlit run streamlit_app.py --server.port=\$PORT" > Procfile

# 2. Deploy
heroku create your-app-name
git push heroku main
heroku open
```

**Cost:** $7-50/month

---

## 🌐 Option 5: AWS (10 minutes)

```bash
# 1. Create EC2 instance (Ubuntu)
# 2. SSH in
ssh -i key.pem ubuntu@instance-ip

# 3. Install and run
sudo apt update
sudo apt install python3-pip -y
pip3 install -r streamlit_requirements.txt
streamlit run streamlit_app.py
```

**Cost:** $5-20/month

---

## 📊 What You Get

### Pages Included:
✅ **Dashboard** - Overview & metrics  
✅ **Single Prediction** - Predict individual customers  
✅ **Batch Analysis** - Upload CSV for bulk predictions  
✅ **Data Upload** - Analyze your customer data  
✅ **About** - Model info & how-to guide  

### Features:
✅ Interactive visualizations with Plotly  
✅ File upload & download  
✅ Real-time predictions  
✅ Risk segmentation (High/Medium/Low)  
✅ Personalized recommendations  

---

## 🎯 Which Should You Pick?

| Option | Time | Cost | Best For |
|--------|------|------|----------|
| **Local** | 1 min | Free | Testing |
| **Streamlit Cloud** | 3 min | Free | Production |
| **Docker** | 5 min | Free | Custom setup |
| **Heroku** | 5 min | $7/mo | Quick cloud |
| **AWS** | 10 min | $5/mo | Full control |

**👉 Recommended:** **Streamlit Cloud** (Free, easiest, fastest)

---

## 🔧 Troubleshooting

### App won't start
```bash
# Check dependencies
pip install -r streamlit_requirements.txt

# Run with debug info
streamlit run streamlit_app.py --logger.level=debug
```

### Models not found
```bash
# Create models directory
mkdir models

# Copy your model files
cp churn_model.pkl models/
cp scaler.pkl models/
```

### Port already in use
```bash
# Use different port
streamlit run streamlit_app.py --server.port 8502
```

### CSV upload not working
```bash
# Check file format - must have these columns:
# Age, MonthlyCharges, TotalCharges, ContractLength
# MonthsAsCustomer, InternetService, OnlineSecurity
# OnlineBackup, TechSupport, StreamingTV
# PaperlessBilling, PaymentMethod
```

---

## 💡 Tips & Tricks

### Add Custom Theme
Create `.streamlit/config.toml`:
```toml
[theme]
primaryColor = "#667eea"
backgroundColor = "#ffffff"
textColor = "#262730"
font = "sans serif"
```

### Add Password Protection
```python
import streamlit as st

password = st.text_input("Password:", type="password")
if password != "demo":
    st.stop()

# Rest of app...
```

### Speed Up Loading
```python
@st.cache_resource
def load_model():
    return pickle.load(open('models/churn_model.pkl', 'rb'))

model = load_model()
```

---

## 📱 Mobile Access

All deployment options are mobile-responsive!

Access your app from:
- ✓ Desktop browsers
- ✓ Tablets
- ✓ Mobile phones
- ✓ Any device with internet

---

## 🔒 Production Best Practices

- [ ] Test locally first
- [ ] Add password protection
- [ ] Keep model files in `models/` directory
- [ ] Use environment variables for secrets
- [ ] Monitor app usage
- [ ] Set up error logging
- [ ] Regular model retraining
- [ ] Document CSV format for users

---

## 📊 Next Steps

1. **Try Local First:**
   ```bash
   streamlit run streamlit_app.py
   ```

2. **Test All Features:**
   - Dashboard page
   - Single prediction
   - Batch analysis
   - Data upload

3. **Deploy to Cloud:**
   - Choose Streamlit Cloud (recommended)
   - Push to GitHub
   - Deploy in 1 click

4. **Share with Team:**
   - Send app URL
   - Add password if needed
   - Document CSV format

---

## 🎉 You're Ready!

Pick an option above and deploy in minutes.

**Most recommended:** Streamlit Cloud (instant, free, easy)

```bash
# 1. Push code
git push origin main

# 2. Deploy at https://share.streamlit.io
# 3. Share URL with team
# Done! ✅
```

---

## 📚 Learn More

- **Streamlit Docs:** https://docs.streamlit.io/
- **Components Gallery:** https://streamlit.io/components
- **Community Cloud:** https://share.streamlit.io/
- **Deploy Guide:** https://docs.streamlit.io/deploy/

Happy deploying! 🚀
