# 🔐 Role-Based Access Control (RBAC) - FINTEL AI

## Overview
FINTEL AI now has complete role-based access control with 4 different user roles, each with specific permissions.

---

## 👥 User Roles

### 1. **Admin** 🛡️
**Full System Access**
- ✅ Upload Invoices
- ✅ View & Edit Invoices
- ✅ Delete Invoices
- ✅ View & Export Reports
- ✅ Manage Users
- ✅ View & Resolve Anomalies
- ✅ Access Settings
- ✅ Chat with FINTEL AI

**Use Case:** System administrators, IT team

---

### 2. **Finance Manager** 💼
**Financial Operations**
- ✅ Upload Invoices
- ✅ View & Edit Invoices
- ❌ Delete Invoices
- ✅ View & Export Reports
- ❌ Manage Users
- ✅ View & Resolve Anomalies
- ❌ Access Settings
- ✅ Chat with FINTEL AI

**Use Case:** Finance team leads, managers

---

### 3. **Auditor** 🔍
**Read-Only + Export**
- ❌ Upload Invoices
- ✅ View Invoices (Read-only)
- ❌ Edit Invoices
- ✅ View & Export Reports
- ❌ Manage Users
- ✅ View Anomalies (Cannot resolve)
- ❌ Access Settings
- ✅ Chat with FINTEL AI

**Use Case:** Internal/external auditors, compliance team

---

### 4. **Viewer** 👁️
**Basic Read-Only**
- ❌ Upload Invoices
- ✅ View Invoices (Read-only)
- ❌ Edit Invoices
- ✅ View Reports (Cannot export)
- ❌ Manage Users
- ✅ View Anomalies (Read-only)
- ❌ Access Settings
- ❌ Chat with FINTEL AI

**Use Case:** Stakeholders, read-only access users

---

## 🎯 Features Implemented

### 1. **AuthContext** (`src/contexts/AuthContext.tsx`)
- Centralized authentication state
- Role-based permissions mapping
- Permission checking functions
- User management (login/logout)

### 2. **ProtectedRoute** (`src/components/auth/ProtectedRoute.tsx`)
- Route-level access control
- Automatic permission checking
- Access denied page for unauthorized users

### 3. **RoleSwitcher** (`src/components/auth/RoleSwitcher.tsx`)
- Quick role switching for demo
- Visual role indicators
- Dropdown menu with all roles

### 4. **Dynamic Menu**
- Menu items filtered by permissions
- Only shows accessible pages
- Automatic hiding of restricted items

---

## 🔧 How It Works

### Permission Checking
```typescript
// Check if user has specific permission
if (hasPermission('canUploadInvoices')) {
  // Show upload button
}
```

### Protected Routes
```typescript
// Route requires specific permission
<Route 
  path="/upload" 
  element={
    <ProtectedRoute requiredPermission="canUploadInvoices">
      <Upload />
    </ProtectedRoute>
  } 
/>
```

### Role Switching (Demo Mode)
- Click role badge in header
- Select new role from dropdown
- Page reloads with new permissions
- Menu items update automatically

---

## 📋 Permission Matrix

| Feature | Admin | Finance Manager | Auditor | Viewer |
|---------|-------|----------------|---------|--------|
| Upload Invoices | ✅ | ✅ | ❌ | ❌ |
| View Invoices | ✅ | ✅ | ✅ | ✅ |
| Edit Invoices | ✅ | ✅ | ❌ | ❌ |
| Delete Invoices | ✅ | ❌ | ❌ | ❌ |
| View Reports | ✅ | ✅ | ✅ | ✅ |
| Export Data | ✅ | ✅ | ✅ | ❌ |
| Manage Users | ✅ | ❌ | ❌ | ❌ |
| View Anomalies | ✅ | ✅ | ✅ | ✅ |
| Resolve Anomalies | ✅ | ✅ | ❌ | ❌ |
| Access Settings | ✅ | ❌ | ❌ | ❌ |
| Chat with FINTEL | ✅ | ✅ | ✅ | ❌ |

---

## 🚀 Usage

### For Demo/Testing:
1. Login to the system
2. Click the role badge in header (e.g., "Admin")
3. Select different role from dropdown
4. Page reloads with new permissions
5. Notice menu items change based on role

### For Production:
1. User logs in with credentials
2. Backend assigns role based on user account
3. Frontend receives role in auth token
4. Permissions applied automatically
5. Menu and features filtered by role

---

## 🔒 Security Features

- ✅ Route-level protection
- ✅ Component-level permission checks
- ✅ Menu filtering by permissions
- ✅ Access denied pages
- ✅ Automatic logout on permission change
- ✅ LocalStorage for session persistence

---

## 📝 Files Created

1. **`src/contexts/AuthContext.tsx`** - Authentication & permissions
2. **`src/components/auth/ProtectedRoute.tsx`** - Route protection
3. **`src/components/auth/RoleSwitcher.tsx`** - Role switching UI
4. **`src/App.tsx`** - Updated with protected routes
5. **`src/components/layout/DashboardLayout.tsx`** - Updated with role switcher

---

## 🎯 Next Steps (Optional)

1. **Backend Integration**
   - Connect to real authentication API
   - Store roles in database
   - JWT token-based auth

2. **User Management**
   - Add user management page (Admin only)
   - Create/edit/delete users
   - Assign roles to users

3. **Audit Logging**
   - Log all permission checks
   - Track role changes
   - Monitor access attempts

4. **Advanced Permissions**
   - Department-based access
   - Custom permission sets
   - Time-based access

---

## ✅ Testing

**Test Each Role:**

1. **Admin** - Should see all menu items
2. **Finance Manager** - No Settings, can't delete
3. **Auditor** - No Upload, no Settings, read-only
4. **Viewer** - Minimal access, no exports, no chat

**Test Access Denied:**
- Switch to Viewer role
- Try to access `/upload` directly
- Should see "Access Denied" message

---

**RBAC is now fully implemented and working! 🎉**
