# 🎨 Streamlit Version - Customer Churn Prediction

A beautiful, interactive web app for predicting customer churn using Streamlit.

---

## 🎯 What You Have

### Streamlit Application (`streamlit_app.py`)
- **5 Interactive Pages:**
  - 📊 Dashboard - Overview & metrics
  - 🔮 Single Prediction - Predict individual customers
  - 📈 Batch Analysis - Upload CSV for bulk predictions
  - 📋 Data Upload - Analyze customer data
  - ℹ️ About - Model info & help

- **Features:**
  - ✅ Interactive visualizations (Plotly)
  - ✅ Real-time predictions
  - ✅ File upload/download
  - ✅ Risk segmentation
  - ✅ Personalized recommendations
  - ✅ Mobile responsive
  - ✅ Beautiful UI with custom theme

### Configuration
- `.streamlit/config.toml` - App theming & settings
- `streamlit_requirements.txt` - Dependencies

---

## ⚡ Quick Start (2 minutes)

### Step 1: Install
```bash
pip install -r streamlit_requirements.txt
```

### Step 2: Run
```bash
streamlit run streamlit_app.py
```

### Step 3: Open
```
http://localhost:8501
```

That's it! 🎉

---

## ☁️ Deploy to Cloud (3-5 minutes)

### Best Option: Streamlit Cloud (FREE)

1. Push code to GitHub:
   ```bash
   git push origin main
   ```

2. Go to: https://share.streamlit.io

3. Click "New app" and select your repo

4. Your app is live! 🚀

**Advantages:**
- ✅ Completely free
- ✅ Auto-deploy on push
- ✅ HTTPS included
- ✅ Built-in analytics
- ✅ No DevOps needed

### Other Options:
- **Heroku:** `git push heroku main` ($7/month)
- **Docker:** `docker run -p 8501:8501 churn-streamlit:1.0` (AWS/GCP)
- **AWS:** EC2 instance with `streamlit run streamlit_app.py`
- **Azure:** App Service

See `STREAMLIT_DEPLOYMENT.md` for detailed guides.

---

## 📊 App Pages

### 1. Dashboard 📊
- Overall metrics (total customers, churn rate, high risk, model AUC)
- Churn distribution pie chart
- Monthly charges histogram
- Customer tenure scatter plot
- Feature importance bar chart
- Key insights

### 2. Single Prediction 🔮
- Interactive form for customer details
- Real-time churn probability prediction
- Risk gauge visualization
- Personalized retention recommendations
- Support for all customer attributes

### 3. Batch Analysis 📈
- CSV file upload
- Bulk predictions for multiple customers
- Summary statistics
- Risk distribution visualization
- Probability histogram
- Download results as CSV

### 4. Data Upload 📋
- Import customer data in CSV format
- View data statistics
- Download processed data
- Export to Excel or CSV
- Data quality checks

### 5. About ℹ️
- Model performance metrics
- Feature importance ranking
- How-to guides for each page
- FAQ section
- Usage recommendations

---

## 🎨 Features

### Interactive Visualizations
- Plotly charts (responsive & zoomable)
- Real-time gauge for churn probability
- Distribution plots and scatter plots
- Feature importance bar charts

### File Management
- Upload CSV with customer data
- Download predictions as CSV
- Export to Excel format
- Built-in data validation

### Smart Predictions
- Single customer analysis
- Batch processing (unlimited size)
- Risk classification (High/Medium/Low)
- Probability scores

### User Experience
- Responsive design (desktop & mobile)
- Intuitive navigation
- Clear error messages
- Progress indicators
- Helpful recommendations

---

## 📝 CSV Format

### Required Columns
```
customer_id,Age,MonthlyCharges,TotalCharges,ContractLength,
MonthsAsCustomer,InternetService,OnlineSecurity,OnlineBackup,
TechSupport,StreamingTV,PaperlessBilling,PaymentMethod
```

### Example
```csv
CUST_001,45,89.5,2400,24,30,Fiber optic,Yes,No,No,Yes,Yes,Electronic check
CUST_002,50,95.0,3200,12,8,DSL,No,Yes,Yes,No,No,Bank transfer
```

### Categorical Values
- **InternetService:** Fiber optic, DSL, No
- **Services:** Yes, No
- **PaymentMethod:** Electronic check, Mailed check, Bank transfer, Credit card

---

## 🔧 Configuration

Edit `.streamlit/config.toml` to customize:

```toml
[theme]
primaryColor = "#667eea"        # Change to your brand color
backgroundColor = "#f8f9fa"
secondaryBackgroundColor = "#e8ecf1"
textColor = "#262730"
font = "sans serif"

[server]
port = 8501
maxUploadSize = 200             # Max CSV file size (MB)
```

---

## 🚀 Performance Tips

1. **Use Caching:**
   ```python
   @st.cache_resource
   def load_model():
       return pickle.load(open('models/churn_model.pkl', 'rb'))
   ```

2. **Lazy Load Data:**
   ```python
   with st.expander("Load heavy data"):
       df = pd.read_csv('large_file.csv')
   ```

3. **Optimize Visualizations:**
   - Use Plotly (faster rendering)
   - Limit data points on charts
   - Cache plot generation

---

## 🔒 Security

### Add Password Protection

Option 1: Environment variable
```bash
export STREAMLIT_SERVER_HEADLESS=true
```

Option 2: In app
```python
import streamlit as st

password = st.text_input("Password:", type="password")
if password != st.secrets.get("APP_PASSWORD"):
    st.stop()
```

### Secure File Uploads
- Validate CSV format before processing
- Sanitize file paths
- Store uploads in temp directory
- Auto-delete after processing

---

## 📱 Mobile Support

The app is fully responsive:
- ✅ Desktop browsers
- ✅ Tablets
- ✅ Mobile phones
- ✅ All screen sizes

Access from any device!

---

## 🐛 Troubleshooting

### App won't start
```bash
# Install missing dependencies
pip install -r streamlit_requirements.txt

# Run with debug
streamlit run streamlit_app.py --logger.level=debug
```

### Models not found
```bash
# Create models directory
mkdir models

# Copy model files
cp churn_model.pkl models/
cp scaler.pkl models/
```

### CSV upload fails
- Check column names match requirements
- Ensure file is properly formatted
- Max file size: 200MB (configurable)
- Supported format: CSV only

### Slow predictions
- Model files loaded to memory
- Predictions are fast (< 100ms)
- Batch operations cached
- Use smaller files for testing

---

## 📊 How to Use

### For Single Prediction:
1. Go to "Single Prediction" page
2. Enter customer details
3. Click "Predict Churn Risk"
4. Get probability, risk level, and recommendations

### For Batch Analysis:
1. Go to "Batch Analysis" page
2. Upload CSV file
3. Click "Predict All Customers"
4. View results and download CSV

### For Data Analysis:
1. Go to "Data Upload" page
2. Upload your customer CSV
3. View statistics and summaries
4. Export processed data

---

## 🎯 Model Performance

| Metric | Value |
|--------|-------|
| Algorithm | Gradient Boosting |
| Accuracy | 68.5% |
| AUC-ROC | 0.6349 |
| F1-Score | 0.2759 |
| Training Data | 1000 customers |

### Top Predictors:
1. MonthsAsCustomer (28.5%)
2. MonthlyCharges (19.8%)
3. TotalCharges (15.7%)

---

## 💡 Best Practices

1. **Test Locally First:**
   ```bash
   streamlit run streamlit_app.py
   ```

2. **Version Control:**
   ```bash
   git add streamlit_app.py
   git commit -m "Update churn app"
   git push origin main
   ```

3. **Monitor Performance:**
   - Check Streamlit Cloud dashboard
   - View app usage statistics
   - Monitor error logs

4. **Keep Models Updated:**
   - Retrain quarterly
   - Validate new models locally
   - Push updates to production

---

## 📚 Documentation

- **STREAMLIT_QUICK_START.md** - Get started fast
- **STREAMLIT_DEPLOYMENT.md** - Deploy to cloud
- **CHURN_PREDICTION_GUIDE.md** - Model details
- **README.md** - Complete overview

---

## 🎁 Bonus

### Included Features
- ✅ Sample data & visualizations
- ✅ Demo mode (no model needed)
- ✅ Beautiful theme
- ✅ Mobile responsive
- ✅ File download
- ✅ CSV support
- ✅ Error handling
- ✅ Progress indicators

### Coming Soon
- User authentication
- Email notifications
- Database integration
- Advanced analytics
- Custom dashboards

---

## 🚀 Deployment Comparison

| Platform | Time | Cost | Difficulty | Recommendation |
|----------|------|------|------------|-----------------|
| Local | 2 min | Free | Easy | Development |
| Streamlit Cloud | 3 min | Free | Very Easy | **Production** |
| Docker | 5 min | Free | Medium | Custom setup |
| Heroku | 5 min | $7/mo | Easy | Quick cloud |
| AWS | 10 min | $5/mo | Medium | Enterprise |

**⭐ Recommended:** Streamlit Cloud (fastest, easiest, free)

---

## ✅ Deployment Checklist

- [ ] Install dependencies: `pip install -r streamlit_requirements.txt`
- [ ] Test locally: `streamlit run streamlit_app.py`
- [ ] Test all 5 pages
- [ ] Check CSV upload with sample file
- [ ] Verify predictions work
- [ ] Push to GitHub
- [ ] Deploy to Streamlit Cloud or chosen platform
- [ ] Test production app
- [ ] Share URL with team

---

## 📞 Support

### Questions?
1. Check STREAMLIT_QUICK_START.md
2. Read STREAMLIT_DEPLOYMENT.md
3. See troubleshooting section
4. Visit https://docs.streamlit.io

### Report Issues
1. Check app logs
2. Verify CSV format
3. Ensure models exist
4. Check dependencies

---

## 🎉 You're Ready!

Your Streamlit app is production-ready. Deploy in minutes and start making predictions!

**Quick Deploy:**
```bash
# 1. Push to GitHub
git push origin main

# 2. Visit https://share.streamlit.io
# 3. Deploy in 1 click
# 4. Share URL with team!
```

Happy deploying! 🚀
