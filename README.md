# ITViec Clone — Frontend Client & Admin Portal (React + TypeScript)

Frontend web application for the **ITViec Clone** recruitment platform, built with **React 18**, **TypeScript**, **Vite**, **Redux Toolkit**, and **Ant Design (AntD & ProComponents)**. Includes both the candidate-facing job portal and the Admin/HR management dashboard with dynamic permission-based UI rendering.

- **Live Demo:** [https://itviec-fe-gslm.vercel.app](https://itviec-fe-gslm.vercel.app)
- **Demo Admin Account:** `admin@gmail.com` | **Password:** `123456`
- **Backend Repository:** [github.com/doquochuy2106/itviec-Be](https://github.com/doquochuy2106/itviec-Be)

---

## Key Features

- **Candidate Portal (Client View):**
  - Search and filter IT jobs by skills, location (Ho Chi Minh, Ha Noi, Da Nang), and salary range.
  - Browse top IT companies, company profiles, and active job openings.
  - Submit job applications with online CV/Resume upload (`PDF`/`DOCX`).
  - Manage personal account: view applied CV history & status, update user profile, and subscribe to skill-based weekly job alert emails.
- **Admin & HR Dashboard:**
  - **Dynamic RBAC UI (`<Access />` wrapper & Protected Routes):** Automatically hides/disables pages, tables, and action buttons (`Create`, `Update`, `Delete`) based on the logged-in user's assigned permissions.
  - **Company & Job Management:** Rich-text descriptions (`React Quill`), skill tags, salary formatting, and pagination via Ant Design `ProTable`.
  - **Resume Review Workflow:** Filter submitted CVs and update application statuses (`PENDING`, `REVIEWING`, `APPROVED`, `REJECTED`).
  - **User, Role & Permission Management:** Visual grouped permission matrix by API module for configuring HR and Admin roles.
- **API & State Management Architecture:**
  - Centralized `Axios` instance with request/response interceptors and `async-mutex` to handle automatic JWT Access Token refresh without race conditions when multiple requests fail with `401 Unauthorized`.
  - Global state management with **Redux Toolkit** slices (`account`, `company`, `job`, `resume`, `role`, `permission`, `user`).

---

## Tech Stack

| Category | Technologies |
| :--- | :--- |
| **Core** | React 18, TypeScript, Vite |
| **State Management** | Redux Toolkit (`@reduxjs/toolkit`), React-Redux |
| **UI & Styling** | Ant Design 5 (`antd`), `@ant-design/pro-components`, SASS/SCSS Modules, React Quill |
| **Networking & Routing** | Axios, `async-mutex` (Token Refresh Lock), React Router v6, `query-string` |
| **Deployment** | Vercel |

---

## Project Structure

```text
src/
├── components/
│   ├── admin/      # Modals, forms, and views for Company, Job, Resume, Role, Permission, User
│   ├── client/     # Header, Footer, Search bar, Job/Company cards, Apply CV & Account modals
│   └── share/      # Protected routes, <Access /> RBAC wrapper, Layout & Loading states
├── config/         # Axios interceptors (with async-mutex refresh token), API endpoints, Permission constants
├── pages/          # Route pages (Home, Job list/detail, Company list/detail, Auth, Admin pages)
├── redux/          # Redux store & slices for server/auth state synchronization
├── styles/         # Modular SCSS stylesheets
└── types/          # Strict TypeScript interfaces for API requests/responses (backend.d.ts)
```

---

## Getting Started

### 1. Prerequisites
- **Node.js** >= 16.20.0 (or v18+)

### 2. Installation

```bash
npm install
```

### 3. Environment Configuration

Create or update `.env.development`:

```env
NODE_ENV=development
PORT=3000
VITE_BACKEND_URL=http://localhost:8080
```

### 4. Run the Application

```bash
# Start development server
npm run dev

# Build for production
npm run build
```
