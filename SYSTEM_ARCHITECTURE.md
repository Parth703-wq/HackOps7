# 🏗️ FINTEL AI - SYSTEM ARCHITECTURE & WORKFLOW

## 📋 TABLE OF CONTENTS
1. [System Overview](#system-overview)
2. [Architecture Diagram](#architecture-diagram)
3. [Technology Stack](#technology-stack)
4. [System Components](#system-components)
5. [Complete Workflow](#complete-workflow)
6. [Data Flow](#data-flow)
7. [API Endpoints](#api-endpoints)
8. [Database Schema](#database-schema)

---

## 🎯 SYSTEM OVERVIEW

**FINTEL AI** is an autonomous finance and compliance agent that automates invoice processing, anomaly detection, and compliance checking using AI/ML technologies.

### **Core Capabilities:**
- 📄 **Invoice OCR** - Extract data from PDF invoices using Gemini Vision
- 🔍 **Anomaly Detection** - Detect duplicates, GST issues, price deviations
- ✅ **GST Verification** - Real-time verification with Government API
- 🤖 **AI Agent** - LangChain-powered intelligent analysis
- 📊 **Analytics** - Real-time dashboards and reports
- 📧 **Automated Reporting** - Scheduled email reports

---

## 🏗️ ARCHITECTURE DIAGRAM

```
┌─────────────────────────────────────────────────────────────────┐
│                         USER INTERFACE                          │
│                    (React + TypeScript)                         │
│                    http://localhost:8080                        │
└────────────────────────┬────────────────────────────────────────┘
                         │
                         │ HTTP/REST API
                         │
┌────────────────────────┴────────────────────────────────────────┐
│                      BACKEND SERVICES                           │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  ┌─────────────────┐      ┌──────────────────┐                │
│  │  Node.js Server │      │  Python AI Agent │                │
│  │  (Port 5000)    │      │  (Port 8000)     │                │
│  │                 │      │                  │                │
│  │ - Auth Routes   │      │ - Gemini Vision  │                │
│  │ - Email Service │      │ - LangChain AI   │                │
│  │ - Reports       │      │ - GST Verifier   │                │
│  └────────┬────────┘      └────────┬─────────┘                │
│           │                        │                           │
└───────────┼────────────────────────┼───────────────────────────┘
            │                        │
            │                        │
            └────────┬───────────────┘
                     │
                     │ MongoDB Driver
                     │
┌────────────────────┴────────────────────────────────────────────┐
│                      DATABASE LAYER                             │
│                    MongoDB (Port 27017)                         │
│                                                                 │
│  Collections:                                                   │
│  - users          (Authentication)                              │
│  - invoices       (Invoice data)                                │
│  - anomalies      (Detected issues)                             │
│  - vendors        (Vendor information)                          │
└─────────────────────────────────────────────────────────────────┘
            │
            │ External APIs
            │
┌───────────┴─────────────────────────────────────────────────────┐
│                      EXTERNAL SERVICES                          │
│                                                                 │
│  - Gemini AI API (Google)     - Invoice OCR & Analysis         │
│  - RapidAPI GST Verification  - Government GST validation       │
│  - Gmail SMTP                 - Email notifications             │
└─────────────────────────────────────────────────────────────────┘
```

---

## 💻 TECHNOLOGY STACK

### **Frontend:**
```
Framework:     React 18 + TypeScript
Build Tool:    Vite
UI Library:    shadcn/ui + Tailwind CSS
State:         React Hooks + Context API
Routing:       React Router v6
Charts:        Recharts
HTTP Client:   Fetch API
Icons:         Lucide React
```

### **Backend - Node.js Server:**
```
Runtime:       Node.js
Framework:     Express.js
Database:      MongoDB + Mongoose
Auth:          JWT + bcrypt
Email:         Nodemailer
Scheduler:     node-cron
File Upload:   Multer
```

### **Backend - Python AI Agent:**
```
Framework:     FastAPI
AI/ML:         Google Gemini AI
Agent:         LangChain + LangGraph
OCR:           Gemini Vision
Database:      PyMongo
GST API:       RapidAPI
PDF:           PyPDF2
```

### **Database:**
```
Database:      MongoDB 7.0
Driver:        Mongoose (Node.js), PyMongo (Python)
```

### **External APIs:**
```
Gemini AI:     gemini-2.0-flash-exp
GST API:       RapidAPI GST Verification
Email:         Gmail SMTP
```

---

## 🧩 SYSTEM COMPONENTS

### **1. Frontend (React App)**

**Location:** `Frontend/`

**Pages:**
- `Login.tsx` - User authentication
- `Signup.tsx` - User registration
- `Dashboard.tsx` - Analytics overview
- `Upload.tsx` - Invoice upload
- `Explorer.tsx` - Invoice browser
- `Anomalies.tsx` - Anomaly management
- `Vendors.tsx` - Vendor analytics
- `Reports.tsx` - Report generation
- `Chat.tsx` - AI chat interface
- `Settings.tsx` - System settings

**Key Features:**
- Role-based access (Admin/User)
- Real-time data updates
- Interactive charts
- Dark mode support
- Responsive design

---

### **2. Backend - Node.js Server**

**Location:** `Backend/`

**Main File:** `server.js`

**Routes:**
```javascript
/api/auth          - Authentication (login, signup, verify)
/api/invoices      - Invoice CRUD operations
/api/anomalies     - Anomaly management
/api/chat          - Chat with FINTEL AI
/api/email         - Email services
/api/vendors       - Vendor analytics
```

**Services:**
- **Authentication:** JWT-based user auth
- **Email Service:** Automated report emails
- **Scheduled Reports:** Daily/Weekly reports
- **File Management:** Invoice storage

---

### **3. Backend - Python AI Agent**

**Location:** `AI-Agent/`

**Main File:** `fintel_api_fixed.py`

**Core Modules:**

**a) Gemini Vision OCR (`gemini_vision_ocr.py`):**
```python
- Extract invoice data from PDF
- Multi-page support
- Structured data extraction
- Confidence scoring
```

**b) GST Verifier (`gst_verifier.py`):**
```python
- Real-time GST verification
- Government API integration
- Vendor name matching
- Active status check
```

**c) LangChain Agent (`langchain_agent.py`):**
```python
- Intelligent invoice analysis
- Natural language processing
- Anomaly reasoning
- Recommendation generation
```

**d) Database Manager (`database.py`):**
```python
- MongoDB operations
- Anomaly detection logic
- Historical comparison
- Trend analysis
```

**Features:**
- Multi-model AI (Gemini 2.0, 1.5)
- Hybrid detection (Rule-based + AI)
- Real-time processing
- Batch operations

---

## 🔄 COMPLETE WORKFLOW

### **📤 INVOICE UPLOAD & PROCESSING**

```
┌──────────────────────────────────────────────────────────────┐
│ STEP 1: USER UPLOADS INVOICE                                │
└────────────────────┬─────────────────────────────────────────┘
                     │
                     ▼
┌──────────────────────────────────────────────────────────────┐
│ Frontend (Upload.tsx)                                        │
│ - User selects PDF file                                      │
│ - Validates file type/size                                   │
│ - Sends to backend via POST /api/upload                      │
└────────────────────┬─────────────────────────────────────────┘
                     │
                     ▼
┌──────────────────────────────────────────────────────────────┐
│ STEP 2: BACKEND RECEIVES FILE                               │
└────────────────────┬─────────────────────────────────────────┘
                     │
                     ▼
┌──────────────────────────────────────────────────────────────┐
│ Python AI Agent (fintel_api_fixed.py)                       │
│ - Receives PDF file                                          │
│ - Saves to uploads/ directory                                │
│ - Starts processing pipeline                                 │
└────────────────────┬─────────────────────────────────────────┘
                     │
                     ▼
┌──────────────────────────────────────────────────────────────┐
│ STEP 3: GEMINI VISION OCR                                   │
└────────────────────┬─────────────────────────────────────────┘
                     │
                     ▼
┌──────────────────────────────────────────────────────────────┐
│ Gemini Vision OCR (gemini_vision_ocr.py)                    │
│                                                              │
│ 1. Convert PDF to images (per page)                         │
│ 2. Send to Gemini Vision API                                │
│ 3. Extract structured data:                                 │
│    - Invoice Number                                          │
│    - Vendor Name                                             │
│    - GST Number(s)                                           │
│    - Total Amount                                            │
│    - Invoice Date                                            │
│    - HSN/SAC Codes                                           │
│    - Line Items                                              │
│    - GST Rates (CGST, SGST, IGST)                           │
│ 4. Calculate OCR confidence score                           │
│ 5. Extract raw text                                          │
└────────────────────┬─────────────────────────────────────────┘
                     │
                     ▼
┌──────────────────────────────────────────────────────────────┐
│ STEP 4: GST VERIFICATION                                    │
└────────────────────┬─────────────────────────────────────────┘
                     │
                     ▼
┌──────────────────────────────────────────────────────────────┐
│ GST Verifier (gst_verifier.py)                              │
│                                                              │
│ 1. Extract GST number from invoice                          │
│ 2. Call RapidAPI GST Verification                           │
│ 3. Verify with Government database                          │
│ 4. Check:                                                    │
│    - GST is valid                                            │
│    - GST is active                                           │
│    - Vendor name matches                                     │
│ 5. Store verification result                                │
└────────────────────┬─────────────────────────────────────────┘
                     │
                     ▼
┌──────────────────────────────────────────────────────────────┐
│ STEP 5: COMPLIANCE CHECKING                                 │
└────────────────────┬─────────────────────────────────────────┘
                     │
                     ▼
┌──────────────────────────────────────────────────────────────┐
│ Compliance Engine                                            │
│                                                              │
│ 1. Validate invoice format                                  │
│ 2. Check mandatory fields                                   │
│ 3. Verify GST calculations                                  │
│ 4. Validate HSN codes                                       │
│ 5. Check date formats                                       │
│ 6. Calculate compliance score                               │
│ 7. Assign risk level (LOW/MEDIUM/HIGH)                      │
└────────────────────┬─────────────────────────────────────────┘
                     │
                     ▼
┌──────────────────────────────────────────────────────────────┐
│ STEP 6: STORE IN MONGODB                                    │
└────────────────────┬─────────────────────────────────────────┘
                     │
                     ▼
┌──────────────────────────────────────────────────────────────┐
│ Database (MongoDB)                                           │
│                                                              │
│ Store invoice with:                                          │
│ - All extracted data                                         │
│ - OCR confidence                                             │
│ - GST verification results                                   │
│ - Compliance results                                         │
│ - Upload timestamp                                           │
│ - File reference                                             │
└────────────────────┬─────────────────────────────────────────┘
                     │
                     ▼
┌──────────────────────────────────────────────────────────────┐
│ STEP 7: ANOMALY DETECTION                                   │
└────────────────────┬─────────────────────────────────────────┘
                     │
                     ▼
┌──────────────────────────────────────────────────────────────┐
│ Anomaly Detector (database.py)                              │
│                                                              │
│ Rule-Based Detection:                                        │
│ 1. DUPLICATE_INVOICE                                         │
│    - Check invoice number exists                             │
│    - Same vendor + amount                                    │
│                                                              │
│ 2. INVALID_GST                                               │
│    - GST verification failed                                 │
│    - GST not active                                          │
│                                                              │
│ 3. MISSING_GST                                               │
│    - No GST number found                                     │
│                                                              │
│ 4. GST_VENDOR_MISMATCH                                       │
│    - GST used by different vendor                            │
│                                                              │
│ 5. UNUSUAL_AMOUNT                                            │
│    - Amount > 3x vendor average                              │
│                                                              │
│ 6. HSN_PRICE_DEVIATION                                       │
│    - Price differs from HSN history                          │
│                                                              │
│ Store detected anomalies in MongoDB                          │
└────────────────────┬─────────────────────────────────────────┘
                     │
                     ▼
┌──────────────────────────────────────────────────────────────┐
│ STEP 8: AI AGENT ANALYSIS (Optional)                        │
└────────────────────┬─────────────────────────────────────────┘
                     │
                     ▼
┌──────────────────────────────────────────────────────────────┐
│ LangChain AI Agent (langchain_agent.py)                     │
│                                                              │
│ 1. Analyze invoice with LangChain                           │
│ 2. Use Gemini AI for reasoning                              │
│ 3. Generate insights:                                        │
│    - Risk assessment                                         │
│    - Anomaly explanations                                    │
│    - Recommendations                                         │
│ 4. Natural language summary                                 │
└────────────────────┬─────────────────────────────────────────┘
                     │
                     ▼
┌──────────────────────────────────────────────────────────────┐
│ STEP 9: RETURN RESPONSE                                     │
└────────────────────┬─────────────────────────────────────────┘
                     │
                     ▼
┌──────────────────────────────────────────────────────────────┐
│ Response to Frontend                                         │
│                                                              │
│ {                                                            │
│   "success": true,                                           │
│   "invoiceNumber": "INV-001",                                │
│   "vendorName": "ABC Corp",                                  │
│   "totalAmount": 50000,                                      │
│   "gstNumber": "27XXXXX",                                    │
│   "ocrConfidence": 95,                                       │
│   "complianceScore": 87,                                     │
│   "riskLevel": "LOW",                                        │
│   "anomaliesDetected": 0,                                    │
│   "gstVerification": { "valid": true }                       │
│ }                                                            │
└────────────────────┬─────────────────────────────────────────┘
                     │
                     ▼
┌──────────────────────────────────────────────────────────────┐
│ STEP 10: DISPLAY TO USER                                    │
└──────────────────────────────────────────────────────────────┘
│ Frontend shows:                                              │
│ - Success message                                            │
│ - Extracted data                                             │
│ - Compliance status                                          │
│ - Any anomalies detected                                     │
│ - Redirect to Explorer/Dashboard                             │
└──────────────────────────────────────────────────────────────┘
```

---

## 📊 DATA FLOW

### **Invoice Data Structure:**

```javascript
{
  // Basic Information
  "_id": "ObjectId",
  "filename": "invoice.pdf",
  "uploadDate": "2025-11-08T00:00:00Z",
  
  // Extracted Data (from Gemini Vision)
  "invoiceNumber": "INV-001",
  "vendorName": "ABC Corporation",
  "gstNumber": "27AADCC8181EIZN",
  "allGstNumbers": ["27AADCC8181EIZN"],
  "totalAmount": 50000.00,
  "invoiceDate": "2025-11-01",
  
  // GST Details
  "gst_rate": "18%",
  "cgst_rate": "9%",
  "sgst_rate": "9%",
  "igst_rate": "0%",
  
  // Line Items
  "hsnCodes": ["8517", "8471"],
  "itemDescriptions": ["Mobile Phone", "Laptop"],
  "quantities": [10, 5],
  
  // OCR Quality
  "ocrConfidence": 95.5,
  "rawText": "Full extracted text...",
  
  // GST Verification (NEW!)
  "gst_verification": [{
    "success": true,
    "is_valid": true,
    "is_active": true,
    "legal_name": "ABC CORPORATION",
    "trade_name": "ABC Corp",
    "registration_date": "2020-01-01"
  }],
  "gst_missing": false,
  
  // Compliance Results
  "complianceResults": {
    "score": 87,
    "risk_level": "LOW",
    "checks_passed": 8,
    "checks_failed": 1,
    "issues": []
  },
  
  // ML Prediction
  "mlPrediction": null
}
```

### **Anomaly Data Structure:**

```javascript
{
  "_id": "ObjectId",
  "invoiceId": "ObjectId (reference)",
  "invoiceNumber": "INV-001",
  "vendorName": "ABC Corp",
  "anomalyType": "DUPLICATE_INVOICE",
  "severity": "HIGH",
  "description": "Duplicate invoice detected",
  "amount": 50000.00,
  "detectedAt": "2025-11-08T00:00:00Z",
  "resolved": false
}
```

---

## 🔌 API ENDPOINTS

### **Authentication APIs:**

```
POST   /api/auth/signup       - Register new user
POST   /api/auth/login        - User login
GET    /api/auth/verify       - Verify JWT token
GET    /api/auth/me           - Get current user
```

### **Invoice APIs:**

```
POST   /api/upload            - Upload invoice (Python AI Agent)
GET    /api/invoices/history  - Get all invoices
GET    /api/invoices/:id      - Get single invoice
DELETE /api/invoices/:id      - Delete invoice
```

### **Anomaly APIs:**

```
GET    /api/anomalies         - Get all anomalies
GET    /api/anomalies/:id     - Get single anomaly
PUT    /api/anomalies/:id     - Update anomaly status
```

### **Dashboard APIs:**

```
GET    /api/dashboard/stats   - Get dashboard statistics
GET    /api/dashboard/trends  - Get anomaly trends
```

### **Vendor APIs:**

```
GET    /api/vendors           - Get all vendors
GET    /api/vendors/:id       - Get vendor details
```

### **Chat APIs:**

```
POST   /api/chat              - Chat with FINTEL AI
GET    /api/chat/suggestions  - Get chat suggestions
```

### **Email APIs:**

```
POST   /api/email/send-report - Send email report
```

---

## 🗄️ DATABASE SCHEMA

### **MongoDB Collections:**

**1. users**
```javascript
{
  _id: ObjectId,
  username: String,
  email: String (unique),
  password: String (hashed),
  role: String (enum: 'user', 'admin'),
  createdAt: Date,
  lastLogin: Date
}
```

**2. invoices**
```javascript
{
  _id: ObjectId,
  filename: String,
  uploadDate: Date,
  invoiceNumber: String,
  vendorName: String,
  gstNumber: String,
  allGstNumbers: [String],
  totalAmount: Number,
  invoiceDate: String,
  hsnCodes: [String],
  itemDescriptions: [String],
  quantities: [Number],
  ocrConfidence: Number,
  gst_verification: [Object],
  gst_missing: Boolean,
  complianceResults: Object,
  mlPrediction: Object,
  rawText: String
}
```

**3. anomalies**
```javascript
{
  _id: ObjectId,
  invoiceId: ObjectId,
  invoiceNumber: String,
  vendorName: String,
  anomalyType: String,
  severity: String,
  description: String,
  amount: Number,
  detectedAt: Date,
  resolved: Boolean
}
```

**4. vendors**
```javascript
{
  _id: ObjectId,
  name: String,
  gstNumber: String,
  totalInvoices: Number,
  totalAmount: Number,
  averageAmount: Number,
  riskScore: Number,
  lastInvoiceDate: Date
}
```

---

## 🔐 SECURITY FEATURES

### **Authentication:**
- JWT tokens (7-day expiry)
- Password hashing (bcrypt, 10 rounds)
- Role-based access control
- Protected routes

### **Data Security:**
- MongoDB authentication
- Environment variables for secrets
- CORS configuration
- Input validation

### **API Security:**
- Rate limiting (planned)
- Request validation
- Error handling
- Secure file uploads

---

## 📈 PERFORMANCE OPTIMIZATION

### **Frontend:**
- Code splitting
- Lazy loading
- React.memo for components
- Debounced search

### **Backend:**
- Connection pooling
- Async/await operations
- Batch processing
- Caching (planned)

### **Database:**
- Indexed fields
- Query optimization
- Aggregation pipelines

---

## 🚀 DEPLOYMENT ARCHITECTURE

```
Production Setup:

Frontend:
- Vercel / Netlify
- CDN distribution
- Environment variables

Backend (Node.js):
- AWS EC2 / Heroku
- PM2 process manager
- Nginx reverse proxy

Backend (Python):
- AWS EC2 / Google Cloud Run
- Gunicorn + Uvicorn
- Docker container

Database:
- MongoDB Atlas
- Automated backups
- Replica sets

External Services:
- Gemini AI API
- RapidAPI GST
- Gmail SMTP
```

---

## 📊 MONITORING & LOGGING

### **Logs:**
- Console logging
- Error tracking
- API request logs
- Performance metrics

### **Monitoring:**
- Uptime monitoring
- API response times
- Error rates
- Database performance

---

## 🎯 KEY FEATURES SUMMARY

1. **AI-Powered OCR** - Gemini Vision for accurate data extraction
2. **Real-time GST Verification** - Government API integration
3. **Intelligent Anomaly Detection** - Rule-based + AI hybrid
4. **LangChain AI Agent** - Natural language analysis
5. **Role-Based Access** - Admin and User roles
6. **Automated Reporting** - Scheduled email reports
7. **Interactive Dashboard** - Real-time analytics
8. **Chat Interface** - Ask questions about invoices
9. **Export Functionality** - PDF and Excel reports
10. **Responsive Design** - Works on all devices

---

## 📝 NOTES

- **Gemini API Quota:** 1,500 requests/day (free tier)
- **Processing Time:** 5-10 seconds per invoice
- **Supported Formats:** PDF only
- **Max File Size:** 10MB
- **Multi-page Support:** Yes
- **Languages:** English (primary)

---

**🎉 FINTEL AI - Autonomous Finance & Compliance Agent**

**Version:** 1.0.0  
**Last Updated:** November 8, 2025  
**Status:** Production Ready ✅
