# ApexHRMS: Modern Payroll & Attendance Management System

A full-stack, enterprise-grade **Payroll and Attendance Management System** built with **React 19**, **Tailwind CSS v4**, **Node.js / Express**, and high-performance **native SQLite** (`node:sqlite` in WAL mode).

---

## 🌟 Key Features

### ⏱️ 1. Attendance Management
- **Interactive Punch In/Out**: Real-time ticking clock, live session duration timer, and one-click clock-in and clock-out with optional location notes.
- **Smart Shift Rules & Late Detection**: Automatically compares clock-in timestamps against assigned shift timings (e.g. 09:00 AM) and grace periods (15 minutes).
- **Working Hours & Overtime Engine**: Automatically categorizes punches into `Present`, `Half Day`, or `Overtime` based on shift thresholds.
- **Master Attendance Dashboard (HR/Admin)**:
  - Filter by date, department, and status (`Present`, `Late`, `Half Day`, `Absent`, `On Leave`).
  - **Bulk Mark Present**: 1-click attendance marking for all or filtered active staff.
  - **Manual Punch Override**: Easily add or adjust clock-in/out times, status, and remarks for any employee.
- **Interactive Attendance Calendar**: Visual color-coded month grid (Present, Late, Half Day, Leave, Absent) with click-to-view day details.

### 🌴 2. Leave Management Workflow
- **Multi-Type Quota Tracking**: Pre-configured with Paid/Annual Leave, Sick Leave, Casual Leave, and Unpaid Leave (Loss of Pay).
- **Employee Leave Application**: Date-range picker, automated working-days calculation (excluding weekends), and real-time balance check.
- **HR Review & Approval Workflow**: HR managers can approve or reject pending requests with review notes.
- **Cross-Module Synchronization**: Approved leaves automatically populate attendance logs as `On Leave` and link with payroll calculations.

### 💰 3. Automated Payroll Engine
- **Monthly Payroll Batches**: Create and simulate payroll runs (e.g., October 2026) for all active employees.
- **Smart Proration & Deductions**:
  - Automatically factors in attendance records, unpaid leaves (Loss of Pay), and overtime hours.
  - Computes Gross Earnings = Base Salary + HRA + Conveyance + Medical + Special Allowance + Overtime Pay + Performance Bonus.
  - Computes Deductions = Provident Fund (PF) + Professional Tax + Health Insurance (ESI) + Income Tax (TDS) + LOP Deductions + Custom Deductions.
  - Computes Net Salary Payable.
- **Disbursement & Payment Tracking**: Review calculations, adjust spot bonuses or deductions, and commit batches with disbarment dates.

### 📄 4. Vectorized PDF Payslip Generation
- **Official Printable Payslips**: Generated on-the-fly using `PDFKit`.
- Features company header, employee summary, two-column itemized Earnings vs Deductions table, amount in numbers and words, and confidential digital stamp.
- Instant 1-click download from both employee portal and HR records.

### 📊 5. Reports & Analytics
- **Attendance Audit Report**: Monthly workforce metrics (Present days, Half days, Late marks, Leaves, Total hours, Overtime, Attendance Rate %).
- **Payroll Expenditure Report**: Annual and monthly payroll expenditure trends with interactive bar charts.
- **CSV Data Export**: One-click download of attendance and payroll reports in CSV format.

### 👑 6. Multi-Tenant SaaS & White-Label Client Co-Branding
- **Platform Owner (SaaS Vendor)**:
  - Complete control over onboarding client businesses (e.g., Microsoft, Acme, TechCorp).
  - Automatically provisions the client's **Administrator Account** with isolated workspace, departments, shifts, and leave quotas.
  - Generates instant copyable login credentials to send directly to the client owner.
- **Client Co-Branding & Customization**:
  - **Custom Client Logo**: Upload or link any client logo (e.g. Microsoft corporate logo).
  - **Brand Accent Color**: Tailored brand color (e.g. Microsoft Blue `#0078d4`) reflected across UI highlights and reports.
  - **"Powered By" Co-Branding Badge**: Display `"Powered by [Your Platform / Company Name]"` on the Sidebar header, Navbar, Login portal, and Payslips.
  - **Pre-Configured Microsoft Showcase**: Switch to `admin@microsoft.com` with 1 click to view the live Microsoft-branded portal with "Powered by ApexHRMS" co-branding.

### 🛡️ 7. Role-Based Access Control (RBAC) & Demo Switcher
- **SaaS Platform Owner**: Manage client subscriptions, provision administrator accounts, configure global white-labeling.
- **Client Administrator**: Full control over their company's workforce directory, user accounts, shifts, and payroll batches.
- **HR Specialist**: Manage employee records, review leaves, master attendance, and execute monthly payroll runs.
- **Employee**: Self-service portal for clocking in/out, viewing attendance history, applying for leaves, and accessing payslips.
- **Built-in Quick Switcher**: Top banner with one-click instant login between Platform Owner, Microsoft Admin, Apex Admin, HR, and Employee.

---

## 🏗️ Technology Stack

| Component | Technology |
|---|---|
| **Frontend** | React 19, Vite 8, Tailwind CSS v4, Lucide React, Recharts |
| **Backend API** | Node.js (ES Modules), Express.js |
| **Database** | Native SQLite (`node:sqlite`) in WAL mode (Zero external binaries needed) |
| **Document Generation** | PDFKit (Pure JavaScript vector PDF generation) |
| **Authentication** | JWT (JSON Web Tokens) & BCrypt password hashing |

---

## 🚀 Quick Start Guide

### 1. Prerequisites
- **Node.js** v20+ or v24+ (Recommended)
- **npm** v10+

### 2. Installation
Navigate to the project root directory:
```bash
cd payroll-attendance-system
```

Install root, backend, and frontend dependencies:
```bash
# Install backend dependencies
cd server
npm install

# Install frontend dependencies
cd ../client
npm install

cd ..
```

### 3. Seed Database
Run the pre-configured seed script to create departments, shifts, leave types, sample staff, 20+ days of attendance logs, and previous/current payroll batches:
```bash
cd server
npm run seed
cd ..
```

### 4. Start the Application
Run both backend API and React client concurrently:
```bash
node start.js
```
Or start them individually in separate terminals:
- **Backend API**: `cd server && npm run dev` (Runs on `http://localhost:5000`)
- **Frontend App**: `cd client && npm run dev` (Runs on `http://localhost:3000`)

Open your browser at: **`http://localhost:3000`**

---

## 🔑 Demo Login Credentials

You can log in manually using the credentials below, or click any role in the **One-Click Demo Switcher** banner at the top of the screen:

| Role | Email | Password | Organization | Co-Branding / Access Scope |
|---|---|---|---|---|
| **👑 Platform Owner (You)** | `owner@platform.com` | `owner123` | Platform Provider | Sell service, onboard clients, provision Admins, system stats |
| **🌐 Client Administrator (Microsoft)** | `admin@microsoft.com` | `msft123` | Microsoft Corporation | **Microsoft Logo + "Powered by ApexHRMS"** showcase |
| **🏢 Client Administrator (Apex)** | `admin@company.com` | `admin123` | ApexGlobal Tech | Client 1 administration, staff, payroll, shifts |
| **💼 HR Specialist** | `hr@company.com` | `hr123` | ApexGlobal Tech | Workforce attendance, leave review & approvals, payroll |
| **👤 Employee (John Doe)** | `john.doe@company.com` | `employee123` | ApexGlobal Tech | Personal clock-in/out, leave requests, personal payslips |
| **🏢 Client Administrator (Nexus)** | `admin@nexus.io` | `nexus123` | Nexus Cloud Solutions | Client 2 isolated organization administration |

---

## 📁 Project Structure

```
payroll-attendance-system/
├── client/                     # React 19 + Tailwind CSS Frontend
│   ├── src/
│   │   ├── components/
│   │   │   ├── Attendance/     # PunchCard, AttendanceCalendar
│   │   │   ├── Common/         # Badge, Modal, StatsCard, QuickRoleBanner
│   │   │   └── Layout/         # Sidebar, Navbar, Shell Layout
│   │   ├── context/            # AuthContext (JWT, user state, quick switch)
│   │   ├── pages/              # Dashboard, Employees, Detail, Attendance, Leaves, Payroll, Payslips, Reports, Settings
│   │   ├── services/           # API fetch wrapper
│   │   ├── App.jsx             # React Router v7 configuration
│   │   └── main.jsx
│   ├── vite.config.js          # Vite configuration with API proxy to port 5000
│   └── package.json
├── server/                     # Express REST API Backend
│   ├── src/
│   │   ├── config/             # SQLite connection & schema migrations
│   │   ├── controllers/        # Auth, Employee, Attendance, Leave, Payroll, Report, Dashboard
│   │   ├── middleware/         # JWT authentication & RBAC authorization
│   │   ├── routes/             # Express API route modules
│   │   ├── seeds/              # Initial seed script with realistic staff & history
│   │   ├── services/           # Payroll engine calculations & PDFKit payslip renderer
│   │   └── index.js            # Express app entry point
│   ├── data/                   # SQLite database storage (payroll.db)
│   └── package.json
├── start.js                    # Cross-platform concurrent startup script
├── package.json                # Project root script orchestrator
└── README.md                   # System documentation
```
