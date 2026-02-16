# 🚀 Streamlit Deployment Guide

Deploy your Churn Prediction app with Streamlit - the easiest way!

---

## ⚡ Quick Start (Local)

### 1. Install Dependencies
```bash
pip install -r streamlit_requirements.txt
```

### 2. Run Streamlit App
```bash
streamlit run streamlit_app.py
```

### 3. Access in Browser
```
http://localhost:8501
```

Done! Your app is running locally.

---

## 📊 Streamlit Features

✓ **Interactive Dashboard** - Real-time visualizations  
✓ **Single Predictions** - Get instant churn probability  
✓ **Batch Analysis** - Upload CSV for bulk predictions  
✓ **Data Upload** - Analyze your own customer data  
✓ **Auto-reload** - Changes update instantly  
✓ **Mobile Responsive** - Works on any device  
✓ **No Backend Needed** - Pure Python frontend  

---

## 🌐 Deploy to Streamlit Cloud (Easiest)

### Step 1: Push Code to GitHub
```bash
git init
git add streamlit_app.py streamlit_requirements.txt
git commit -m "Add Streamlit churn prediction app"
git push origin main
```

### Step 2: Deploy to Streamlit Cloud
1. Go to: https://share.streamlit.io
2. Click "New app"
3. Connect your GitHub repo
4. Select: Repository → Branch → File path (`streamlit_app.py`)
5. Deploy!

**Your app is live at:** `https://share.streamlit.io/your-username/your-repo/streamlit_app.py`

**FREE FOREVER** with generous usage limits!

---

## 🐳 Deploy with Docker

### Dockerfile for Streamlit
```dockerfile
FROM python:3.10-slim

WORKDIR /app

COPY streamlit_requirements.txt .
RUN pip install -r streamlit_requirements.txt

COPY streamlit_app.py .
COPY models/ ./models/

EXPOSE 8501

HEALTHCHECK CMD curl --fail http://localhost:8501/_stcore/health

CMD ["streamlit", "run", "streamlit_app.py", "--server.port=8501", "--server.address=0.0.0.0"]
```

### Build & Run
```bash
docker build -t churn-streamlit:1.0 .
docker run -d -p 8501:8501 churn-streamlit:1.0
```

Access at: http://localhost:8501

---

## ☁️ Deploy to Heroku

### 1. Create `Procfile`
```
web: streamlit run streamlit_app.py --server.port=$PORT --server.address=0.0.0.0
```

### 2. Create `.streamlit/config.toml`
```toml
[client]
showErrorDetails = true

[logger]
level = "info"

[theme]
primaryColor = "#667eea"
backgroundColor = "#f0f2f6"
secondaryBackgroundColor = "#e0e3f1"
textColor = "#262730"
font = "sans serif"
```

### 3. Deploy
```bash
heroku login
heroku create your-app-name
git push heroku main
heroku open
```

**Cost:** $7-50/month (free tier available)

---

## 🌥️ Deploy to Streamlit Cloud (Recommended)

**Easiest & Free option!**

1. Push code to GitHub (public repo)
2. Visit https://share.streamlit.io
3. Click "New app"
4. Select your repo, branch, and file
5. Deploy in seconds!

**Features:**
- ✓ Free hosting
- ✓ Auto-scaling
- ✓ HTTPS included
- ✓ GitHub auto-deploy
- ✓ Community apps

---

## 🌐 Deploy to AWS

### Option 1: EC2
```bash
# SSH into instance
ssh -i key.pem ubuntu@instance-ip

# Install dependencies
sudo apt update
sudo apt install python3-pip -y
pip3 install -r streamlit_requirements.txt

# Run app
streamlit run streamlit_app.py
```

### Option 2: Lambda + API Gateway
Use the FastAPI wrapper with Lambda (more complex)

### Option 3: ECS (Container)
```bash
# Push image to ECR
aws ecr get-login-password | docker login --username AWS --password-stdin $AWS_ACCOUNT.dkr.ecr.$REGION.amazonaws.com

docker tag churn-streamlit:1.0 $AWS_ACCOUNT.dkr.ecr.$REGION.amazonaws.com/churn-streamlit:latest
docker push $AWS_ACCOUNT.dkr.ecr.$REGION.amazonaws.com/churn-streamlit:latest

# Create ECS service pointing to image
```

---

## 🌐 Deploy to Google Cloud Run

```bash
# Build image
gcloud builds submit --tag gcr.io/$PROJECT_ID/churn-streamlit

# Deploy
gcloud run deploy churn-streamlit \
  --image gcr.io/$PROJECT_ID/churn-streamlit \
  --platform managed \
  --region us-central1 \
  --allow-unauthenticated \
  --memory 1Gi
```

---

## 🌐 Deploy to Azure App Service

```bash
# Create resource group
az group create --name churn-rg --location eastus

# Create App Service plan
az appservice plan create \
  --name churn-plan \
  --resource-group churn-rg \
  --sku B1 --is-linux

# Create web app
az webapp create \
  --resource-group churn-rg \
  --plan churn-plan \
  --name churn-app \
  --runtime "PYTHON|3.10"

# Deploy code
az webapp up --resource-group churn-rg --name churn-app
```

---

## 📋 Streamlit Configuration

Create `.streamlit/config.toml`:

```toml
[theme]
primaryColor = "#667eea"
backgroundColor = "#ffffff"
secondaryBackgroundColor = "#f0f2f6"
textColor = "#262730"
font = "sans serif"

[client]
showErrorDetails = true

[logger]
level = "info"

[server]
port = 8501
headless = true
runOnSave = true
```

---

## 🔒 Secure Deployment

### Add Password Protection

```python
import streamlit as st

# In streamlit_app.py, add at the top:
if 'authenticated' not in st.session_state:
    st.session_state.authenticated = False

def check_password():
    if st.session_state.authenticated:
        return True
    
    password = st.text_input("Enter password:", type="password")
    if password == st.secrets.get("APP_PASSWORD", "demo"):
        st.session_state.authenticated = True
        st.rerun()
        return True
    return False

if not check_password():
    st.stop()

# Rest of app continues...
```

### Use Environment Secrets

Create `.streamlit/secrets.toml`:
```toml
APP_PASSWORD = "your-secure-password"
API_KEY = "your-api-key"
```

---

## 📊 Streamlit Sharing Features

### Session State
```python
if 'counter' not in st.session_state:
    st.session_state.counter = 0

st.session_state.counter += 1
st.write(f"Count: {st.session_state.counter}")
```

### Caching
```python
@st.cache_resource
def load_model():
    return pickle.load(open('model.pkl', 'rb'))

model = load_model()
```

### File Download
```python
csv_data = df.to_csv(index=False)
st.download_button(
    label="Download CSV",
    data=csv_data,
    file_name="predictions.csv",
    mime="text/csv"
)
```

---

## ⚡ Performance Tips

1. **Use Caching**
   ```python
   @st.cache_resource
   def load_model():
       # Load once, reuse many times
       return model
   ```

2. **Lazy Load Heavy Data**
   ```python
   with st.expander("Load detailed data"):
       df = pd.read_csv('large_file.csv')
   ```

3. **Use Columns for Layout**
   ```python
   col1, col2 = st.columns(2)
   with col1:
       st.write("Left")
   with col2:
       st.write("Right")
   ```

4. **Minimize Recomputation**
   ```python
   @st.cache_data
   def process_data(file_path):
       return expensive_computation(file_path)
   ```

---

## 🐛 Debugging

### Run with Logging
```bash
streamlit run streamlit_app.py --logger.level=debug
```

### View Logs
```bash
# Streamlit Cloud
streamlit run streamlit_app.py --logger.level=debug 2>&1 | tail -100
```

### Terminal Output
```python
import sys
print("Debug message", file=sys.stderr)
```

---

## 📈 Monitoring

### Streamlit Cloud Analytics
- View app usage stats
- Check error logs
- Monitor performance
- Set environment variables

### Custom Analytics
```python
import datetime
import streamlit as st

# Track usage
if 'session_start' not in st.session_state:
    st.session_state.session_start = datetime.datetime.now()

if st.button("Log Event"):
    with open('usage.log', 'a') as f:
        f.write(f"Event at {datetime.datetime.now()}\n")
```

---

## 🎯 Recommended Deployment Path

### For Quick Demo (2 minutes)
→ **Streamlit Cloud** (just push to GitHub!)

### For Production (5 minutes)
→ **Streamlit Cloud** + Custom domain

### For Enterprise (more control)
→ **Docker + AWS/GCP/Azure**

### For Maximum Simplicity (no DevOps)
→ **Streamlit Cloud** (100% recommended)

---

## 📚 Useful Links

- **Streamlit Docs:** https://docs.streamlit.io/
- **Streamlit Cloud:** https://share.streamlit.io/
- **Deployment Guide:** https://docs.streamlit.io/deploy/streamlit-community-cloud
- **Components:** https://streamlit.io/components
- **Theming:** https://docs.streamlit.io/library/get-started/installation
- **Secrets Mgmt:** https://docs.streamlit.io/deploy/streamlit-community-cloud/deploy-your-app#secrets-management

---

## ✅ Deployment Checklist

- [ ] Test app locally: `streamlit run streamlit_app.py`
- [ ] Push code to GitHub
- [ ] Deploy to Streamlit Cloud OR Docker/Cloud provider
- [ ] Test all pages and features
- [ ] Check data privacy (CSV uploads)
- [ ] Set up password protection if needed
- [ ] Configure custom domain (optional)
- [ ] Monitor usage and performance
- [ ] Document for team

---

## 🎉 You're Ready!

Your Streamlit app is production-ready. Choose a deployment method and launch in minutes!

**Most Recommended:** Streamlit Cloud (free, easy, fast)

**Command:**
```bash
# Push to GitHub
git push origin main

# Deploy at: https://share.streamlit.io
# Choose repo → deploy → done!
```

Happy deploying! 🚀
