# 🚀 Setup Guide - Run Streamlit Locally

Since this is a cloud environment without network access, here's how to run everything on **YOUR LOCAL MACHINE**.

---

## ⚡ Quick Setup (5 minutes)

### Step 1: Download Your Files

All files are in `/outputs/` folder:
- `streamlit_app.py` - Main application
- `streamlit_requirements.txt` - Dependencies
- `.streamlit/config.toml` - Configuration

**Download these to your computer.**

---

### Step 2: Create Virtual Environment

```bash
# Navigate to your project folder
cd /path/to/churn-prediction

# Create virtual environment
python -m venv venv

# Activate it
# On Windows:
venv\Scripts\activate
# On Mac/Linux:
source venv/bin/activate
```

---

### Step 3: Install Dependencies

```bash
# Install all required packages
pip install -r streamlit_requirements.txt
```

**Expected output:**
```
Successfully installed streamlit pandas numpy scikit-learn plotly openpyxl
```

---

### Step 4: Run the App

```bash
streamlit run streamlit_app.py
```

**Expected output:**
```
  You can now view your Streamlit app in your browser.

  Local URL: http://localhost:8501
  Network URL: http://192.168.x.x:8501
```

---

### Step 5: Open in Browser

Click the link or visit:
```
http://localhost:8501
```

Done! 🎉 Your app is running!

---

## 📋 What's Inside `streamlit_requirements.txt`

```
streamlit==1.28.0          # Streamlit framework
pandas==2.1.3              # Data manipulation
numpy==1.24.3              # Numerical computing
scikit-learn==1.3.2        # ML models
plotly==5.17.0             # Interactive charts
openpyxl==3.11.0           # Excel export
```

---

## 🔧 Troubleshooting

### "streamlit command not found"
Make sure you activated your virtual environment:
```bash
# Windows
venv\Scripts\activate

# Mac/Linux
source venv/bin/activate
```

### "No module named plotly"
Reinstall dependencies:
```bash
pip install -r streamlit_requirements.txt
```

### "Port 8501 already in use"
Use a different port:
```bash
streamlit run streamlit_app.py --server.port 8502
```

### "ImportError: No module named 'sklearn'"
Reinstall scikit-learn:
```bash
pip install scikit-learn
```

---

## 📁 Folder Structure

Your project should look like this:

```
churn-prediction/
├── venv/                          # Virtual environment (auto-created)
├── streamlit_app.py               # Main app
├── streamlit_requirements.txt      # Dependencies
├── .streamlit/
│   └── config.toml                # Configuration
├── models/                        # Model files (optional)
│   ├── churn_model.pkl
│   └── scaler.pkl
└── data/                          # Data files (optional)
    └── sample.csv
```

---

## ✅ Testing the App

Once running at http://localhost:8501:

1. **Dashboard Page** - Check visualizations load
2. **Single Prediction** - Enter customer data, click "Predict"
3. **Batch Analysis** - Try uploading a CSV file
4. **Data Upload** - View data statistics
5. **About** - Read model info and FAQ

All pages should work smoothly!

---

## 🚀 Deploy to Streamlit Cloud (After Testing Locally)

Once you've tested locally and everything works:

### Step 1: Push to GitHub
```bash
git add .
git commit -m "Add Streamlit churn prediction app"
git push origin main
```

### Step 2: Deploy to Streamlit Cloud
1. Go to: https://share.streamlit.io
2. Click "New app"
3. Enter your GitHub repo details
4. Click "Deploy"

Your app will be live in a few minutes! 🚀

---

## 💡 Tips

### Run in Development Mode
```bash
streamlit run streamlit_app.py --logger.level=debug
```

### Change Theme Colors
Edit `.streamlit/config.toml`:
```toml
[theme]
primaryColor = "#667eea"          # Change color
backgroundColor = "#ffffff"
```

### Add CSV Sample Data
Create `sample.csv`:
```csv
customer_id,Age,MonthlyCharges,TotalCharges,ContractLength,MonthsAsCustomer,InternetService,OnlineSecurity,OnlineBackup,TechSupport,StreamingTV,PaperlessBilling,PaymentMethod
CUST_001,45,89.5,2400,24,30,Fiber optic,Yes,No,No,Yes,Yes,Electronic check
CUST_002,50,95.0,3200,12,8,DSL,No,Yes,Yes,No,No,Bank transfer
```

Then upload on "Batch Analysis" page!

---

## 📚 Commands Reference

| Task | Command |
|------|---------|
| Create venv | `python -m venv venv` |
| Activate venv (Windows) | `venv\Scripts\activate` |
| Activate venv (Mac/Linux) | `source venv/bin/activate` |
| Install dependencies | `pip install -r streamlit_requirements.txt` |
| Run app | `streamlit run streamlit_app.py` |
| Stop app | `Ctrl + C` |
| Deactivate venv | `deactivate` |

---

## 🎯 Next Steps

1. ✅ Download files from `/outputs/`
2. ✅ Create virtual environment
3. ✅ Install dependencies
4. ✅ Run `streamlit run streamlit_app.py`
5. ✅ Test in browser
6. ✅ Deploy to Streamlit Cloud (optional)

---

## 🆘 Still Having Issues?

### Check Python Version
```bash
python --version
# Should be 3.8 or higher
```

### Reinstall Everything
```bash
# Remove venv
rm -rf venv

# Create fresh venv
python -m venv venv

# Activate
source venv/bin/activate  # or venv\Scripts\activate on Windows

# Install fresh
pip install -r streamlit_requirements.txt
```

### Check Internet Connection
Some packages need to download:
```bash
pip install --upgrade pip
pip install streamlit
```

---

## 📞 Common Issues & Solutions

| Issue | Solution |
|-------|----------|
| "No module named X" | `pip install X` |
| Port already in use | `streamlit run streamlit_app.py --server.port 8502` |
| Slow startup | First run downloads dependencies, be patient |
| App crashes | Check console for error messages, see troubleshooting |
| CSV upload fails | Ensure column names match requirements |

---

## ✨ You're All Set!

Your Streamlit Churn Prediction app is ready to run locally!

**Quick start (copy-paste ready):**
```bash
# 1. Create & activate venv
python -m venv venv
source venv/bin/activate

# 2. Install dependencies
pip install -r streamlit_requirements.txt

# 3. Run the app
streamlit run streamlit_app.py

# 4. Open browser
# Visit: http://localhost:8501
```

Done! 🎉

---

## 🚀 Ready to Deploy?

See **STREAMLIT_DEPLOYMENT.md** for:
- Streamlit Cloud (FREE!)
- Docker deployment
- Heroku deployment
- AWS deployment

Happy coding! 🎨
