# 🚀 FINTEL AI - Quick Start Guide

## ⚡ EASIEST WAY - Double Click!

### **START ALL SERVICES:**
```
Just double-click: start-all-services.bat
```

**What it does:**
1. ✅ Starts Backend (Node.js) - Port 5000
2. ✅ Starts AI Agent (Python) - Port 8000
3. ✅ Starts Frontend (React) - Port 8080
4. ✅ Opens browser automatically
5. ✅ Opens 3 terminal windows

**Wait 10-15 seconds for everything to load!**

---

### **STOP ALL SERVICES:**
```
Just double-click: stop-all-services.bat
```

**What it does:**
1. ✅ Stops all Node.js processes
2. ✅ Stops all Python processes
3. ✅ Closes all services

---

## 📋 MANUAL START (If batch file doesn't work)

### **Terminal 1: Backend**
```bash
cd d:\IIT_GANDHINAGAR\Backend
node server.js
```

### **Terminal 2: AI Agent**
```bash
cd d:\IIT_GANDHINAGAR\AI-Agent
python fintel_api_fixed.py
```

### **Terminal 3: Frontend**
```bash
cd d:\IIT_GANDHINAGAR\Frontend
npm run dev
```

---

## 🌐 ACCESS URLS:

Once all services are running:

- **Main Application:** http://localhost:8080
- **Backend API:** http://localhost:5000
- **AI Agent API:** http://localhost:8000

---

## ✅ HOW TO KNOW IT'S WORKING:

### **You should see 3 terminal windows:**

**Window 1: FINTEL Backend - Port 5000**
```
✅ MongoDB Connected
📧 Email Service: Active
✅ Daily Report scheduled: 9:00 AM IST
```

**Window 2: FINTEL AI Agent - Port 8000**
```
✅ Gemini Vision OCR initialized!
✅ MongoDB connected
✅ Server running on port 8000
```

**Window 3: FINTEL Frontend - Port 8080**
```
✅ VITE ready
➜ Local: http://localhost:8080/
```

---

## 🔧 TROUBLESHOOTING:

### **Port already in use?**
```bash
# Run stop-all-services.bat first
# Then run start-all-services.bat again
```

### **MongoDB not running?**
```bash
# Start MongoDB service
net start MongoDB
```

### **Browser doesn't open automatically?**
```
Manually open: http://localhost:8080
```

---

## 📧 EMAIL FEATURES:

**Automatic Emails:**
- ✅ Daily at 9:00 AM IST
- ✅ Daily at 6:00 PM IST
- ✅ Weekly Monday 10:00 AM IST

**Manual Emails:**
- ✅ Go to Reports page
- ✅ Click "Send Report"
- ✅ Email sent to: parth.hindiya@gmail.com

---

## 🎯 QUICK CHECKLIST:

- [ ] Double-click `start-all-services.bat`
- [ ] Wait 10-15 seconds
- [ ] See 3 terminal windows open
- [ ] Browser opens automatically
- [ ] Login to system
- [ ] Start using FINTEL AI!

---

## 💡 TIPS:

**Keep terminals open:**
- Don't close the 3 terminal windows
- Minimize them if needed
- All 3 must run together

**To stop everything:**
- Double-click `stop-all-services.bat`
- Or close all 3 terminal windows

**Daily use:**
- Start: Double-click `start-all-services.bat`
- Use: http://localhost:8080
- Stop: Double-click `stop-all-services.bat`

---

## 🎉 THAT'S IT!

**Just double-click `start-all-services.bat` and you're ready to go!**

**Everything starts automatically!** 🚀✨
