# 🤖 GEMINI API USAGE IN YOUR SYSTEM

## ✅ YES! WE'RE USING GEMINI API A LOT!

### **📊 TOTAL GEMINI API USAGE:**

```
1. Gemini Vision OCR (Main OCR)
2. Gemini for Chat/Q&A
3. LangChain AI Agent (Gemini-powered)
4. LangGraph Workflow (Gemini-powered)
```

---

## 🎯 WHERE WE USE GEMINI:

### **1. Gemini Vision OCR** 📄
**File:** `gemini_vision_ocr.py`
**Model:** `gemini-2.5-flash`
**Usage:** EVERY invoice upload

```python
genai.configure(api_key="AIzaSyB7zJbF7Nx_KP4oIOZCGc5P84WN4RHO14M")
self.model = genai.GenerativeModel('gemini-2.5-flash')
```

**What it does:**
```
✅ Extracts invoice data from PDF/images
✅ OCR for all text
✅ Intelligent data extraction
✅ Multi-page processing
✅ CGST/SGST/IGST calculation
✅ Line items extraction
```

**API Calls:**
```
Every invoice upload = 1 API call per page
Multi-page invoice (3 pages) = 3 API calls
```

---

### **2. Gemini for Chat** 💬
**File:** `fintel_api_fixed.py`
**Model:** `gemini-2.5-flash`
**Usage:** Chat with FINTEL AI endpoint

```python
genai.configure(api_key=GEMINI_API_KEY)
gemini_model = genai.GenerativeModel('gemini-2.5-flash')
```

**What it does:**
```
✅ Answers user questions
✅ Explains anomalies
✅ Provides insights
✅ Invoice analysis queries
```

**API Calls:**
```
Every chat message = 1 API call
```

---

### **3. LangChain AI Agent** 🤖
**File:** `langchain_agent.py`
**Model:** `gemini-2.0-flash-exp`
**Usage:** Intelligent invoice analysis

```python
llm = ChatGoogleGenerativeAI(
    model="models/gemini-2.0-flash-exp",
    temperature=0,
    google_api_key=api_key
)
```

**What it does:**
```
✅ Decides which tools to use
✅ Check duplicates
✅ Validate GST
✅ Analyze amounts
✅ Check GST-vendor consistency
✅ Provides reasoning
✅ Confidence scores
```

**API Calls:**
```
Every invoice with AI analysis = 3-5 API calls
(Agent makes multiple tool calls)
```

---

### **4. LangGraph Workflow** 🔄
**File:** `langgraph_workflow.py`
**Model:** `gemini-1.5-flash`
**Usage:** Multi-step invoice processing

```python
llm = ChatGoogleGenerativeAI(
    model="gemini-1.5-flash",
    temperature=0,
    google_api_key=os.getenv("GEMINI_API_KEY")
)
```

**What it does:**
```
✅ Deep anomaly analysis
✅ Multi-step reasoning
✅ Conditional branching
✅ Report generation
```

**API Calls:**
```
If used = 2-3 API calls per invoice
```

---

## 📊 TOTAL API CALLS PER INVOICE:

### **Basic Upload (No AI Agent):**
```
1. Gemini Vision OCR = 1 call (single page)
                     = 3 calls (3-page invoice)
Total: 1-3 calls
```

### **With AI Agent (Current Setup):**
```
1. Gemini Vision OCR = 1-3 calls (per page)
2. LangChain AI Agent = 3-5 calls (tool usage)
Total: 4-8 calls per invoice
```

### **With Full LangGraph:**
```
1. Gemini Vision OCR = 1-3 calls
2. LangChain AI Agent = 3-5 calls
3. LangGraph Workflow = 2-3 calls
Total: 6-11 calls per invoice
```

---

## 💰 COST ESTIMATION:

### **Gemini API Pricing (Approximate):**
```
Gemini 2.5 Flash:
- Input: $0.075 per 1M tokens
- Output: $0.30 per 1M tokens

Gemini 2.0 Flash Exp:
- Input: $0.075 per 1M tokens
- Output: $0.30 per 1M tokens

Gemini 1.5 Flash:
- Input: $0.075 per 1M tokens
- Output: $0.30 per 1M tokens
```

### **Per Invoice Cost:**
```
Average tokens per call: ~1000 input + 500 output
Cost per call: ~$0.0002

Basic upload (1-3 calls): ~$0.0002 - $0.0006
With AI Agent (4-8 calls): ~$0.0008 - $0.0016
With LangGraph (6-11 calls): ~$0.0012 - $0.0022
```

### **Monthly Cost (Example):**
```
100 invoices/month with AI Agent:
100 × $0.0012 = $0.12/month

1000 invoices/month with AI Agent:
1000 × $0.0012 = $1.20/month

10,000 invoices/month with AI Agent:
10,000 × $0.0012 = $12/month
```

---

## 🎯 API USAGE BREAKDOWN:

### **Current System:**
```
Every Invoice Upload:
├─ Gemini Vision OCR (1-3 calls)
│  └─ Extract all invoice data
│
└─ LangChain AI Agent (3-5 calls)
   ├─ Check duplicates
   ├─ Validate GST
   ├─ Analyze amount
   └─ Check consistency

Total: 4-8 Gemini API calls per invoice
```

### **Chat Feature:**
```
Every Chat Message:
└─ Gemini Chat (1 call)
   └─ Answer user question

Total: 1 Gemini API call per message
```

---

## 🔑 API KEY USED:

```
GEMINI_API_KEY = AIzaSyB7zJbF7Nx_KP4oIOZCGc5P84WN4RHO14M
```

**Used in:**
```
✅ gemini_vision_ocr.py
✅ fintel_api_fixed.py
✅ langchain_agent.py
✅ langgraph_workflow.py
✅ .env file
```

---

## 📈 USAGE OPTIMIZATION:

### **To Reduce API Calls:**

**Option 1: Disable AI Agent**
```python
# In fintel_api_fixed.py
use_ai=False  # Only use rule-based detection
```
**Saves:** 3-5 calls per invoice

**Option 2: Conditional AI**
```python
# Only run AI for high-value invoices
if invoice_amount > 10000:
    run_ai_analysis()
```
**Saves:** ~50% of AI calls

**Option 3: Batch Processing**
```python
# Process multiple invoices in one call
# (Not currently implemented)
```

---

## ✅ SUMMARY:

**Gemini API Usage:**
```
✅ Gemini Vision OCR: EVERY invoice
✅ Gemini Chat: EVERY chat message
✅ LangChain Agent: EVERY invoice (if enabled)
✅ LangGraph: Optional (not always used)
```

**Total API Calls:**
```
Per Invoice: 4-8 calls (with AI Agent)
Per Chat: 1 call
Monthly (100 invoices): ~400-800 calls
```

**Cost:**
```
Very affordable!
~$0.0012 per invoice
~$1-2 per month for 1000 invoices
```

**Benefits:**
```
✅ Highly accurate OCR
✅ Intelligent fraud detection
✅ Automated reasoning
✅ Multi-language support
✅ Multi-page processing
✅ Real-time analysis
```

---

**🎉 YES, WE USE GEMINI A LOT - BUT IT'S VERY COST-EFFECTIVE!**

**For 1000 invoices/month: Only ~$1-2!** 💰✨
