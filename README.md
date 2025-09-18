# Secure File Management System

This repository contains a secure **client–server file management system** that allows users to upload, download, and delete files on a server.  
It is built with **Node.js + Express (backend)** and **Next.js + Tailwind (frontend)**.

---

## 🚀 Features
- Upload multiple files per user with unique ID prefixes.
- Download or delete files via secure REST endpoints.
- Separate storage directories per user (example: `username`, or generic `files/`).
- Logging middleware saves all requests in `logs/reqLog.txt`.
- CORS configured for local frontend (`http://localhost:3000`).
- Client built with **Next.js** for easy UI access.

---

## 📦 Project Structure
```
secure-file-management/
├─ server.js              # Express backend
├─ middleware/            # Custom middleware
│  ├─ corsConfig.js
│  ├─ logEvents.js
│  ├─ fileExtLimiter.js
│  └─ filesPayloadExist.js
├─ files/                 # Default file storage (ignored in git)
├─ client/ (Next.js app)
│  ├─ app/
│  ├─ tailwind.config.ts
│  ├─ tsconfig.json
│  └─ README.md
├─ package.json
└─ package-lock.json
```

---

## ⚙️ Installation

### 1. Prerequisites
- [Node.js 18+](https://nodejs.org/) and npm
- (Optional) Git & Docker

### 2. Clone repository
```bash
git clone https://github.com/<your-username>/secure-file-management.git
cd secure-file-management
```

### 3. Install dependencies

#### Backend (Express)
```bash
cd server
npm install
```

#### Frontend (Next.js)
```bash
cd client
npm install
```

---

## ▶️ Running the App

### Start Backend
```bash
cd server
npm run dev   # or: node server.js
```
Server runs on [http://localhost:5500](http://localhost:5500).

### Start Frontend
```bash
cd client
npm run dev
```
Frontend runs on [http://localhost:3000](http://localhost:3000).

---

## 🌐 API Endpoints

### Login / Logout
- `POST /login/:username` – logs in user  
- `POST /logout/:username` – logs out user  

### Upload File(s)
```http
POST /upload/:username/:fileName
Form-Data: files[] (one or more files)
```

### Download File
```http
GET /download/:username/:fileName
```

### Delete File
```http
DELETE /delete/:username/:fileName
```

---

## 📝 Logs
- All requests are logged in `logs/reqLog.txt` with timestamp and origin.

---

## 🎨 Frontend (Next.js)
- Run client: `npm run dev` in `/client`
- Open [http://localhost:3000](http://localhost:3000)
- UI connects to backend for file upload/download/delete.

---

## 🛠 Development Notes
- Configure CORS in `middleware/corsConfig.js` (default: `http://localhost:3000`).
- User folders: `username` created automatically.
- Middleware handles payload validation and extension limits.

---

## 🤝 Contributing
1. Fork the project
2. Create feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit changes (`git commit -m 'Add some feature'`)
4. Push to branch (`git push origin feature/AmazingFeature`)
5. Open Pull Request

